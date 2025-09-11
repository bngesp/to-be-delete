# ANNEXE TECHNIQUE : SPÉCIFICATIONS FONCTIONNELLES & TECHNIQUES

## Introduction

Ce document fournit une description exhaustive des 23 modules qui composent la plateforme **Waajal Ëlëk**, dans le cadre de l'architecture microservices retenue. Chaque module est présenté avec son objectif stratégique, ses fonctionnalités détaillées, et des notes d'implémentation technique précises (modèles de données, API, sécurité). Ce document constitue le socle de notre proposition, garantissant une transparence totale et démontrant une maîtrise approfondie des enjeux techniques et métier.

---
## Architecture Technique Globale : Microservices

L'architecture de la plateforme "Waajal Ëlëk" est conçue selon une approche **Microservices**, privilégiant la modularité, la résilience, et la scalabilité indépendante de chaque composant. Cette approche est idéale pour un système complexe, permettant des développements parallèles, des mises à jour ciblées et une isolation des fautes.

```ascii
                  +------------------------------------------------+
                  |           UTILISATEURS & CLIENTS               |
                  +------------------------------------------------+
                                |                  |
          +---------------------+                  +---------------------+
          | Navigateur Web      |                  | Application Mobile  |
          | (Portail Adhérent / |                  | (iOS / Android)     |
          |  Back-office Admin) |                  |                     |
          +---------------------+                  +---------------------+
                  |                                        |
                  |                                        |
+-----------------v----------------------------------------v-----------------+
|                 ^                                        ^                 |
|   +-------------+----------------------------------------+-------------+   |
|   |                    REQUETES HTTPS via Internet                     |   |
|   +--------------------------------------------------------------------+   |
|                                     |                                    |
|   +---------------------------------v----------------------------------+   |
|   | Pare-feu Applicatif (WAF) / Load Balancer                          |   |
|   +---------------------------------v----------------------------------+   |
|                                     |                                    |
|   +---------------------------------v----------------------------------+   |
|   |                API GATEWAY (Spring Cloud Gateway)                  |   |
|   |     (Routage, Authentification, Rate Limiting, Sécurité)           |   |
|   +---------------------------------v----------------------------------+   |
|                                     |                                    |
|   +---------------------------------v----------------------------------+   |
|   |             REGISTRE DE SERVICES (Eureka / Consul)                 |   |
|   +---------------------------------v----------------------------------+   |
|                                     |                                    |
|   +---------------------------------v----------------------------------+   |
|   |        SERVEUR DE CONFIGURATION (Spring Cloud Config)              |   |
|   +--------------------------------------------------------------------+   |
|                                                                            |
| <--------------------------- Réseau Interne de Microservices ---------------------------> |
|                                                                            |
| +------------------+ +------------------+ +------------------+ +------------------+      |
| |  `user-service`  | |`membership-svc`| |`contribution-svc`| | `pension-svc`  | ...  |
| +------------------+ +------------------+ +------------------+ +------------------+      |
| | Base Données 1   | | Base Données 2   | | Base Données 3   | | Base Données 4   |      |
| +------------------+ +------------------+ +------------------+ +------------------+      |
|                                                                            |
| <-------------------------- Bus d'Événements (RabbitMQ) ----------------------------> |
|                                                                            |
| +------------------+ +------------------+ +------------------+ +------------------+      |
| |`actuarial-engine`| |`accounting-svc`| |`notification-svc`| |  `reporting-svc` | ...  |
| +------------------+ +------------------+ +------------------+ +------------------+      |
| | Base Données 5   | | Base Données 6   | | Base Données 7   | | Base Données 8   |      |
| +------------------+ +------------------+ +------------------+ +------------------+      |
|                                                                            |
+------------------------------------------------------------------------------------------+
```

### Description de l'Architecture Microservices

1.  **Clients (Frontend)** : Les utilisateurs interagissent avec la plateforme via une application web responsive (SPA) et une application mobile native. Ces clients ne communiquent jamais directement avec les microservices.

2.  **API Gateway (Spring Cloud Gateway)** : C'est le point d'entrée unique et obligatoire pour tout le trafic externe. Son rôle est crucial :
    *   **Routage** : Il dirige les requêtes entrantes vers le microservice approprié.
    *   **Sécurité** : Il agit comme un rempart, validant les jetons d'authentification (JWT), appliquant des règles de sécurité et masquant la topologie du réseau interne.
    *   **Façade** : Il peut agréger les résultats de plusieurs microservices pour simplifier la communication avec le client.

3.  **Infrastructure de Services (Service Discovery & Configuration)** :
    *   **Registre de Services (Eureka/Consul)** : Chaque microservice s'enregistre à son démarrage, permettant à l'API Gateway et aux autres services de se trouver dynamiquement.
    *   **Serveur de Configuration (Spring Cloud Config)** : La configuration de tous les microservices (paramètres de base de données, URLs, etc.) est centralisée et versionnée dans un dépôt Git, permettant des modifications à chaud sans redéploiement.

4.  **Microservices Métier** :
    *   Le cœur de la logique est décomposé en services indépendants, chacun responsable d'un domaine métier spécifique (ex: `user-service`, `contribution-service`).
    *   **Déploiement Indépendant** : Chaque service peut être mis à jour, redéployé et mis à l'échelle individuellement, offrant une agilité maximale.
    *   **Base de Données par Service** : Chaque service possède sa propre base de données, garantissant un découplage complet. Aucun service n'est autorisé à accéder directement à la base de données d'un autre.

5.  **Communication Asynchrone (Bus d'Événements)** :
    *   Pour les communications inter-services qui ne nécessitent pas de réponse immédiate, un **Bus d'Événements (RabbitMQ)** est utilisé.
    *   Lorsqu'une action métier importante se produit (ex: une adhésion est validée), le service concerné publie un événement (`MembershipApprovedEvent`). D'autres services (comme le service de notification ou de comptabilité) peuvent souscrire à cet événement et réagir en conséquence. Cette approche **événementielle** garantit la résilience et le découplage.

Cette architecture microservices, orchestrée avec l'écosystème Spring Cloud, est le standard de l'industrie pour construire des applications d'entreprise complexes, distribuées et évolutives. Elle est parfaitement alignée avec l'ambition et la criticité du projet Waajal Ëlëk.

---
## **Microservice `user-service` (Personnel & Accès)**
---

### **Module 1 : Gestion du Personnel Militaire (Référentiel Central)**

*   **Objectif Stratégique & Valeur Métier :**
    Ce module constitue la pierre angulaire de la plateforme Waajal Ëlëk, en établissant une source de vérité unique et incorruptible (`Single Source of Truth`) pour l'ensemble des données des militaires. L'objectif est d'éliminer toute ambiguïté ou redondance d'information, de garantir la conformité réglementaire (KYM - Know Your Military) et de fournir une base de données fiable pour les calculs actuariels et les projections. En centralisant l'état civil, le parcours militaire et les données administratives, ce module réduit drastiquement le risque d'erreurs opérationnelles, facilite les audits et renforce la confiance des adhérents en garantissant que leurs droits sont calculés sur des informations d'une parfaite exactitude.

*   **Description Fonctionnelle Détaillée :**
    L'interface de gestion permettra aux administrateurs autorisés de consulter, créer et modifier les dossiers individuels via une IHM (Interface Homme-Machine) riche et sécurisée. Un processus d'import initial permettra d'ingérer en masse les données existantes depuis les systèmes de la DRH-AT via des fichiers CSV/Excel formatés, avec un rapport de validation détaillé signalant toute anomalie ou donnée manquante. Le moteur de recherche sera doté d'une recherche "full-text" et de filtres à facettes, permettant de segmenter la population sur des critères multiples (par grade, par corps, par année d'incorporation, etc.). Chaque dossier intégrera un coffre-fort numérique individuel pour stocker de manière sécurisée les pièces justificatives numérisées (CNI, actes de service, etc.), avec un versionnage de chaque document.

*   **Implémentation Technique & Architecture :**
    Ce service sera développé en Spring Boot 3 avec Java 17. Le modèle de données principal dans PostgreSQL sera l'entité JPA `@Entity` `MilitaryPersonnel`, liée aux entités `CareerEvent`, `FamilyMember`, `BankAccount` via des relations `@OneToMany`. Les endpoints de l'API RESTful (ex: `GET /api/v1/personnel/{matricule}`) utiliseront la pagination via des objets `Pageable`. L'upload de documents sera délégué au `document-service` (voir module dédié), mais l'association (le lien métadonnées) sera gérée ici. La logique métier sera implémentée dans des classes `@Service`, en respectant le principe de responsabilité unique et en utilisant l'injection de dépendances.

*   **Sécurité, Performance & Scalabilité :**
    L'accès à ce module sera le plus restreint de la plateforme, contrôlé via des annotations `@PreAuthorize` sur les méthodes de service, basées sur les rôles et permissions extraits du jeton JWT fourni par Keycloak. Toute modification d'un champ sensible (ex: RIB) déclenchera un événement `User.Data.Updated` vers RabbitMQ pour informer les autres services et nécessitera une validation par un second administrateur (principe des quatre yeux). Des index composites seront créés sur les colonnes fréquemment interrogées pour garantir la performance des recherches, et des DTO (Data Transfer Objects) seront utilisés pour ne pas exposer directement les entités JPA.

### **Module 2 : Administration, Rôles & Sécurité**

*   **Objectif Stratégique & Valeur Métier :**
    Ce module est le centre de contrôle de la sécurité applicative. Il permet de définir "qui a le droit de faire quoi", garantissant une application stricte du principe de moindre privilège. Une gestion fine des permissions est cruciale pour la sécurité des données personnelles et financières, la prévention des fraudes internes et la conformité avec les réglementations sur la protection des données comme la LOPD (Loi sur la Protection des Données à caractère Personnel) du Sénégal.

*   **Description Fonctionnelle Détaillée :**
    Les super-administrateurs pourront créer et configurer des rôles (ex: "Gestionnaire de Pension", "Comptable", "Auditeur"). Pour chaque rôle, ils pourront assigner des permissions granulaires (ex: "peut liquider une pension", "peut seulement consulter la comptabilité"). L'interface permettra de visualiser rapidement tous les utilisateurs associés à un rôle et l'historique des changements de permission, qui sera lui-même un événement auditable.

*   **Implémentation Technique & Architecture :**
    Ce module sera principalement une surcouche de gestion sur notre serveur d'identité **Keycloak**. Les rôles et permissions seront définis dans Keycloak. Le `user-service` interagira avec l'API d'administration de Keycloak via son client Java pour la gestion programmatique. Les permissions seront incluses dans le jeton d'accès JWT que les frontends recevront après authentification. L'API Gateway (Spring Cloud Gateway) et chaque microservice valideront ce jeton et les permissions qu'il contient à chaque requête via une configuration centralisée de Spring Security.

*   **Sécurité, Performance & Scalabilité :**
    La sécurité de ce module est critique. L'accès à ses fonctionnalités sera limité au rôle de "Super-Administrateur", dont les comptes seront protégés par une authentification multi-facteurs (MFA) obligatoire via TOTP. Toute modification de rôle ou de permission générera un événement d'audit de la plus haute criticité, envoyé au `log-service` et potentiellement à un système d'alerte en temps réel (SIEM) pour une supervision continue des activités à privilèges.

---
## **Microservice `membership-service` (Adhésions)**
---

### **Module 3 : Adhésions et Contrats**

*   **Objectif Stratégique & Valeur Métier :**
    Ce module digitalise et automatise l'entrée du militaire dans le régime de retraite, rendant le processus plus rapide, plus fiable et entièrement traçable. Il assure que chaque adhésion est conforme aux règles du régime et que les termes du contrat sont correctement enregistrés, formant la base de la relation entre l'adhérent et la Mutuelle et garantissant la solidité juridique des engagements.

*   **Description Fonctionnelle Détaillée :**
    Le module offrira un formulaire d'enrôlement en ligne, mais aussi la possibilité pour un gestionnaire de faire une saisie manuelle. Un workflow de validation à plusieurs niveaux (Saisie → Vérification → Approbation → Activation) sera mis en place, entièrement configurable. À l'activation, le contrat est automatiquement créé avec les paramètres par défaut (taux, etc.), qui peuvent ensuite être ajustés via des avenants. Le système gérera ces avenants, en conservant un historique de chaque version du contrat pour une auditabilité parfaite.

*   **Implémentation Technique & Architecture :**
    Le service utilisera une machine à états (State Machine) via la librairie **Spring Statemachine** pour modéliser le cycle de vie de l'adhésion (`MembershipLifecycle`). Chaque transition d'état (ex: `APPROVE`) sera une transaction ACID en base de données (`@Transactional`) et publiera un événement métier (`MembershipApprovedEvent`) dans un topic RabbitMQ. Le `user-service` souscrira à cet événement pour créer le compte de l'adhérent sur le portail, et le `notification-service` pour lui envoyer un email de bienvenue.

*   **Sécurité, Performance & Scalabilité :**
    Les données du contrat sont sensibles. Seuls les gestionnaires avec la permission `contract:edit` pourront initier des modifications. Chaque version du contrat sera stockée dans une table d'historique (`ContractVersion`) pour une traçabilité parfaite. Les opérations étant majoritairement unitaires, la performance n'est pas un enjeu majeur, mais le service sera tout de même déployé en plusieurs répliques pour garantir la haute disponibilité du processus d'adhésion.

---
## **Microservice `contribution-service` (Cotisations & Paiements)**
---

### **Module 4 : Gestion des Cotisations**

*   **Objectif Stratégique & Valeur Métier :**
    C'est le cœur financier transactionnel du système. Ce module assure la collecte rigoureuse et ponctuelle des fonds qui alimentent le régime de retraite. Son automatisation et sa fiabilité sont essentielles pour garantir la croissance des capitaux, la justesse des droits accumulés par les adhérents et la bonne santé financière du régime.

*   **Description Fonctionnelle Détaillée :**
    Chaque début de mois, le système calculera automatiquement les cotisations dues pour tous les adhérents actifs, en se basant sur la rémunération de référence et les termes du contrat. Il gérera les cas particuliers (congés, détachements, temps partiel) via des règles de calcul configurables. Un échéancier clair sera présenté aux gestionnaires, avec des statuts visuels (`Payé`, `En retard`, `En attente`). Le module calculera également les pénalités de retard selon les règles définies.

*   **Implémentation Technique & Architecture :**
    Un `Job` **Spring Batch** (`@Scheduled`) s'exécutera mensuellement pour la génération des cotisations. Ce job sera conçu pour être robuste, parallélisé (`multi-threaded step`) et idempotent (s'il est relancé, il ne dupliquera pas les cotisations). La logique de calcul sera isolée dans des `ItemProcessor` spécifiques. Après chaque paiement validé, le service publiera un événement `ContributionPaidEvent` contenant l'ID de l'adhérent, le montant et la période concernée.

*   **Sécurité, Performance & Scalabilité :**
    Le job de calcul mensuel sera optimisé pour traiter des dizaines de milliers d'adhérents en quelques minutes. Les transactions de paiement seront sécurisées et atomiques. En cas de pic de charge (ex: le jour du paiement), Kubernetes pourra automatiquement augmenter le nombre d'instances de ce service (Horizontal Pod Autoscaling) en se basant sur l'utilisation du CPU ou de la RAM.

### **Module 5 : Conversion en Points**

*   **Objectif Stratégique & Valeur Métier :**
    Ce module traduit l'effort de cotisation financier en droit à la retraite tangible pour l'adhérent : les points. La transparence, l'exactitude et l'instantanéité de ce processus sont fondamentales pour renforcer la confiance de l'adhérent dans le système par points et lui donner une vision claire de la valeur de son épargne.

*   **Description Fonctionnelle Détaillée :**
    Le module fonctionnera de manière entièrement automatisée. Pour chaque cotisation validée, il la convertira en points en se basant sur la "valeur d'achat du point" en vigueur à la date du paiement. Il gérera aussi l'attribution de points gratuits ou de bonifications, initiée par les administrateurs via une interface dédiée. L'adhérent pourra consulter son historique d'acquisition de points avec le détail de chaque transaction (date, montant cotisé, valeur du point, points acquis).

*   **Implémentation Technique & Architecture :**
    Ce module fonctionnera de manière événementielle. Un `Listener` RabbitMQ (`@RabbitListener`) souscrira au topic où sont publiés les événements `ContributionPaidEvent`. À la réception d'un message, il appellera un service qui, dans une transaction unique (`@Transactional`), lira la valeur du point en vigueur (via un appel REST à `actuarial-engine-service`), effectuera le calcul, et insérera une nouvelle ligne dans la table `PointTransaction`.

*   **Sécurité, Performance & Scalabilité :**
    Le traitement asynchrone garantit que même un pic de paiements n'impactera pas les performances du système. Si le calcul échoue pour une raison quelconque (ex: le service actuariel est indisponible), le message sera automatiquement placé dans une "Dead Letter Queue" (DLQ) de RabbitMQ pour une analyse et un traitement ultérieur, garantissant qu'aucune acquisition de points ne soit jamais perdue.

### **Module 6 : Intégration des Paiements**

*   **Objectif Stratégique & Valeur Métier :**
    Moderniser l'expérience de paiement en offrant des canaux digitaux (Mobile Money, virement) que les adhérents et les gestionnaires utilisent au quotidien. Une intégration fluide, sécurisée et entièrement réconciliée est un facteur clé d'efficacité pour la collecte des cotisations et le versement des prestations.

*   **Description Fonctionnelle Détaillée :**
    Le module intégrera les API des opérateurs Mobile Money (Wave, Orange Money, Free Money) pour les cotisations et le versement des prestations. Il permettra le paiement par virement avec génération de références uniques pour faciliter le rapprochement comptable. Toutes les transactions seront suivies en temps réel et les statuts mis à jour automatiquement dans l'interface de gestion.

*   **Implémentation Technique & Architecture :**
    Ce module agira comme une façade (Facade Pattern) pour les différents PSP (Payment Service Providers). Il exposera une API interne unifiée (ex: `POST /api/internal/payments/initiate`). Pour les webhooks de confirmation de paiement, un endpoint unique (`POST /api/contributions/payments/webhook/{provider}`) sera créé. Le corps de la requête sera validé avec la signature fournie par le PSP (ex: `X-Wave-Signature`) pour garantir son authenticité avant tout traitement.

*   **Sécurité, Performance & Scalabilité :**
    Les clés d'API des PSP seront stockées dans un coffre-fort de secrets comme **HashiCorp Vault**, et injectées dans le service au démarrage via Spring Cloud Vault. La communication avec les PSP sera toujours via mTLS (mutual TLS) si supporté, ou a minima TLS 1.3. Le service étant "stateless", il pourra être scalé horizontalement sans problème pour absorber un grand nombre de notifications de paiement simultanées.

---
## **Microservice `pension-service` (Prestations)**
---

### **Module 7 : Gestion des Pensions de Retraite**

*   **Objectif Stratégique & Valeur Métier :**
    Ce module concrétise la promesse du régime de retraite : transformer les points accumulés en une prestation financière. Sa rigueur et sa conformité réglementaire sont absolues pour garantir le paiement correct et ponctuel des pensions, le cœur de la mission de la Mutuelle et l'aboutissement de la carrière de l'adhérent.

*   **Description Fonctionnelle Détaillée :**
    Le module gérera le processus de liquidation des droits, initié par un gestionnaire. Il calculera le montant de la prestation en fonction du total des points et de la "valeur de service du point". Il présentera les différentes options de sortie (rente viagère, capital, mixte) et leur impact fiscal. Il gérera aussi la réversion aux ayants droit en cas de décès, selon les règles établies, en assurant une transition fluide pour les familles.

*   **Implémentation Technique & Architecture :**
    La liquidation sera un processus métier complexe orchestré par ce service, potentiellement modélisé avec un moteur de BPMN comme **Camunda**. Il appellera le `user-service` pour obtenir les données de l'adhérent, le `contribution-service` pour le solde de points final, et le `actuarial-engine-service` pour le calcul de la rente viagère. Le résultat sera une transaction unique qui changera le statut de l'adhérent et publiera un événement `Pension.Liquidated`.

*   **Sécurité, Performance & Scalabilité :**
    La liquidation est une opération critique. Elle sera soumise à un workflow de validation à plusieurs signatures (principe des quatre yeux). Toutes les données utilisées pour le calcul (solde de points, valeur de service, tables de mortalité, etc.) seront "gelées" et stockées dans un document JSON d'audit avec le dossier de liquidation pour garantir une auditabilité parfaite, même si les paramètres du régime changent plus tard.

### **Module 8 : Gestion des Retraités**

*   **Objectif Stratégique & Valeur Métier :**
    Assurer un suivi rigoureux et humain des militaires retraités, en garantissant la continuité des paiements et en maintenant le lien avec la Mutuelle. Ce module est essentiel pour la satisfaction à long terme des bénéficiaires et pour la réputation de l'institution.

*   **Description Fonctionnelle Détaillée :**
    Le module gérera le cycle de vie du retraité, incluant la gestion des certificats de vie avec des rappels automatiques par email ou SMS via le `notification-service`. Il permettra aux gestionnaires de suivre l'historique complet des versements de pension, de gérer les changements de coordonnées bancaires et de traiter les cas de suspension ou de réactivation de pension.

*   **Implémentation Technique & Architecture :**
    Ce service écoutera l'événement `Pension.Liquidated` pour créer un dossier `Retiree` dans sa propre base de données. Un `Job` Spring Batch mensuel générera les ordres de paiement qui seront ensuite envoyés au `contribution-service` (qui gère les paiements sortants) pour exécution. La gestion des certificats de vie sera également gérée par un job récurrent qui vérifiera les dates et enverra des notifications.

*   **Sécurité, Performance & Scalabilité :**
    La modification des coordonnées bancaires d'un retraité est une opération à haut risque. Elle nécessitera une authentification forte du gestionnaire et une validation par un second utilisateur. Un événement d'audit sera généré et une notification sera envoyée au retraité pour l'informer du changement. Le service est conçu pour gérer des centaines de milliers de retraités avec des performances stables.

### **Module 9 : Démissions & Rachats**

*   **Objectif Stratégique & Valeur Métier :**
    Offrir une flexibilité encadrée aux adhérents souhaitant quitter le régime de manière anticipée. Ce module doit appliquer de manière stricte les règles statutaires tout en offrant un processus clair et transparent à l'adhérent, protégeant ainsi les intérêts du régime et ceux de l'individu.

*   **Description Fonctionnelle Détaillée :**
    Les adhérents pourront initier une demande de rachat (partiel ou total) depuis leur portail. Le système vérifiera automatiquement leur éligibilité (ancienneté, etc.) et calculera le montant rachetable, en appliquant les pénalités éventuelles. La demande suivra un workflow de validation interne avant que l'ordre de paiement ne soit généré.

*   **Implémentation Technique & Architecture :**
    Une demande de rachat (`POST /api/v1/redemptions`) créera une nouvelle ressource `RedemptionRequest` avec un statut `PENDING`. Un processus de validation (manuel ou automatique) changera le statut. Si la demande est approuvée, le service publiera un événement `Redemption.Approved` qui sera consommé par le `accounting-service` et le `contribution-service` pour le décaissement.

*   **Sécurité, Performance & Scalabilité :**
    La logique de calcul des pénalités et des montants rachetables sera configurable via le `Configuration Server` pour permettre des ajustements sans redéploiement. Toutes les étapes de la demande de rachat, de l'initiation au paiement, seront journalisées pour un audit complet.

### **Module 10 : Avances sur Capital**

*   **Objectif Stratégique & Valeur Métier :**
    Fournir une aide financière ponctuelle aux adhérents en difficulté, en utilisant leur capital retraite comme garantie. Ce module renforce la proposition de valeur de la Mutuelle en agissant comme un filet de sécurité pour ses membres, tout en assurant un remboursement structuré qui préserve leurs droits futurs.

*   **Description Fonctionnelle Détaillée :**
    Similaire aux rachats, ce module permettra aux adhérents de demander une avance. Le système calculera le montant maximum autorisé (ex: un pourcentage du capital déjà constitué). Si la demande est approuvée, un échéancier de remboursement sera automatiquement généré, et les remboursements pourront être prélevés sur les cotisations futures ou payés séparément.

*   **Implémentation Technique & Architecture :**
    La gestion des avances suivra un modèle similaire à celui des rachats, avec une entité `AdvanceRequest`. L'échéancier de remboursement sera stocké dans une table `RepaymentSchedule`. Un job mensuel vérifiera les échéances et pourra automatiquement déduire les montants des salaires via une intégration avec le système de paie, ou générer une cotisation spéciale.

*   **Sécurité, Performance & Scalabilité :**
    L'impact de l'avance sur la pension future sera simulé en temps réel et présenté à l'adhérent avant qu'il ne confirme sa demande. Cette simulation fera un appel API au `actuarial-engine-service`. Toutes les conditions (taux d'intérêt de l'avance, durée maximale) seront centralisées dans le `Configuration Server`.

---
## **Microservice `actuarial-engine-service` (Moteur Actuariel)**
---

### **Module 11 : Moteur de Calcul Actuariel**

*   **Objectif Stratégique & Valeur Métier :**
    C'est le cerveau mathématique de la plateforme. Ce service centralise toute la logique de calcul complexe, garantissant que les valorisations, les projections et les calculs de rentes sont basés sur des modèles actuariels standards, fiables et auditables. Il décharge les autres services de cette complexité, leur permettant de se concentrer sur leur logique métier.

*   **Description Fonctionnelle Détaillée :**
    Ce service n'aura pas d'interface utilisateur directe. Il exposera une série d'API internes sécurisées pour : calculer la valeur d'une rente viagère à partir d'un capital et d'un profil démographique, projeter l'évolution d'un capital en fonction d'hypothèses, ou encore calculer la valeur de service et d'achat du point. Il intégrera différentes tables de mortalité qui pourront être mises à jour par les administrateurs.

*   **Implémentation Technique & Architecture :**
    Développé en Spring Boot, ce service utilisera des librairies mathématiques et statistiques robustes comme **Apache Commons Math**. Les tables de mortalité seront stockées dans sa propre base de données PostgreSQL. Les API exposées seront purement fonctionnelles (sans état), ce qui signifie que pour une même entrée, la sortie sera toujours la même, facilitant les tests et la mise en cache.

*   **Sécurité, Performance & Scalabilité :**
    L'accès à ce service sera restreint au réseau interne de microservices via des règles de pare-feu au niveau de Kubernetes. Les calculs intensifs (comme les simulations Monte Carlo) pourront être mis en cache dans Redis pour éviter de les recalculer à chaque appel avec les mêmes paramètres. Le service peut être fortement scalé horizontalement pour répondre à un grand nombre de demandes de simulation simultanées.

### **Module 12 : Simulateur Actuariel Global**

*   **Objectif Stratégique & Valeur Métier :**
    Fournir à la direction de la Mutuelle un outil de pilotage stratégique pour assurer la pérennité du régime. Ce module permet de répondre à des questions complexes comme : "Que se passe-t-il si l'espérance de vie augmente de 2 ans ?" ou "Quel est l'impact d'une crise économique sur notre capacité à payer les pensions dans 20 ans ?".

*   **Description Fonctionnelle Détaillée :**
    Via une interface dédiée, les actuaires et dirigeants pourront lancer des simulations de l'ensemble du régime sur des décennies. Ils pourront ajuster les hypothèses macroéconomiques (inflation, rendement des investissements) et démographiques (pyramide des âges, taux de départ à la retraite). Les résultats seront présentés sous forme de graphiques et de tableaux de bord prédictifs.

*   **Implémentation Technique & Architecture :**
    Cette fonctionnalité utilisera le `actuarial-engine-service` de manière intensive. Pour une simulation globale, le service lancera un `Job` Spring Batch qui orchestrera des milliers de calculs de projection individuels en parallèle. Les résultats seront agrégés et stockés dans une base de données analytique (potentiellement ClickHouse ou une autre base de données en colonnes) pour une interrogation rapide par les tableaux de bord.

*   **Sécurité, Performance & Scalabilité :**
    L'exécution de ces simulations est extrêmement gourmande en ressources. Elle sera déclenchée manuellement et s'exécutera avec une priorité basse pour ne pas impacter les services transactionnels. L'utilisation d'une base de données analytique dédiée est cruciale pour permettre une exploration interactive des résultats sans surcharger la base de données principale.

### **Module 13 : Simulations Personnalisées (Portail Adhérent)**

*   **Objectif Stratégique & Valeur Métier :**
    Responsabiliser et engager l'adhérent en lui donnant les outils pour comprendre et optimiser sa propre retraite. En lui permettant de visualiser l'impact de ses décisions (cotiser plus, partir plus tard), ce module transforme l'adhérent d'un spectateur passif en un acteur de sa sécurité financière.

*   **Description Fonctionnelle Détaillée :**
    Depuis son portail, l'adhérent pourra lancer des simulations de sa future pension. Le formulaire sera pré-rempli avec ses données actuelles. Il pourra ensuite créer des scénarios en modifiant des paramètres comme son âge de départ, le montant de ses cotisations volontaires, ou une future promotion. Les résultats compareront graphiquement les différents scénarios.

*   **Implémentation Technique & Architecture :**
    L'interface React appellera un endpoint sur le `pension-service` (ex: `POST /api/v1/simulations/personal`). Ce service agira comme un orchestrateur : il récupérera les données de l'adhérent depuis le `user-service` et appellera ensuite le `actuarial-engine-service` avec les paramètres du scénario pour obtenir les projections.

*   **Sécurité, Performance & Scalabilité :**
    Les appels à l'API de simulation seront soumis à une limitation de débit (rate limiting) au niveau de l'API Gateway pour éviter les abus. Comme mentionné précédemment, les résultats des calculs de l'engine actuariel pourront être mis en cache pour améliorer le temps de réponse pour des simulations similaires.

---
## **Autres Microservices**
---

*(Cette section regroupe les services transverses et spécialisés)*

### **Module 14 : Service de Comptabilité (`accounting-service`)**

*   **Objectif Stratégique & Valeur Métier :**
    Garantir l'intégrité, la conformité et l'auditabilité de toutes les transactions financières du régime. Ce service centralise la logique comptable pour fournir une vue financière fiable et produire les états réglementaires.

*   **Description Fonctionnelle Détaillée :**
    Ce service enregistrera toutes les opérations (cotisations, paiements de pension, rachats, investissements) dans un système comptable en partie double. Il permettra de gérer le plan comptable, de générer des journaux comptables, des balances et des états financiers (bilan, compte de résultat). Il facilitera le rapprochement bancaire en important les relevés électroniques.

*   **Implémentation Technique & Architecture :**
    Ce service sera entièrement événementiel. Il souscrira aux événements `Contribution.Paid`, `Pension.Paid`, `Investment.Executed`, etc. Pour chaque événement, il créera les écritures comptables correspondantes (débit/crédit) dans ses propres tables (`JournalEntry`, `Transaction`). Il ne possédera pas de logique métier autre que la comptabilité, garantissant un découplage parfait.

*   **Sécurité, Performance & Scalabilité :**
    L'intégrité des données est la priorité absolue. Toutes les opérations se feront dans des transactions de base de données strictes. L'accès en écriture à ce service sera interdit depuis l'extérieur ; seules les modifications via les événements RabbitMQ seront possibles, garantissant que la comptabilité est toujours le reflet fidèle des opérations métier.

### **Module 15 : Service de Reporting (`reporting-service`)**

*   **Objectif Stratégique & Valeur Métier :**
    Transformer les données brutes de la plateforme en informations exploitables pour le pilotage et la prise de décision. Ce service fournit les rapports d'activité, les statistiques et les tableaux de bord nécessaires à la gestion quotidienne et stratégique de la Mutuelle.

*   **Description Fonctionnelle Détaillée :**
    Le module permettra de générer une large gamme de rapports : rapports d'activité (adhésions, cotisations, prestations), statistiques démographiques (pyramide des âges), indicateurs de performance (taux de collecte, délais de traitement). Les utilisateurs pourront programmer la génération et l'envoi automatique de rapports par email.

*   **Implémentation Technique & Architecture :**
    Pour ne pas surcharger les bases de données transactionnelles, ce service utilisera sa propre base de données en lecture seule, qui sera une réplique de la base de données des services principaux (via la réplication logique de PostgreSQL). Pour la génération des PDF et Excel, il utilisera des librairies Java éprouvées comme **Apache POI** (pour Excel) et **iText/OpenPDF** (pour PDF). Les générations de rapports volumineux seront exécutées de manière asynchrone par un `Job` Spring Batch.

*   **Sécurité, Performance & Scalabilité :**
    L'utilisation d'une base de données répliquée est le pattern clé ici (CQRS - Command Query Responsibility Segregation), permettant d'optimiser les requêtes de lecture complexes pour le reporting sans impacter les performances des services qui gèrent les écritures. Le service peut être scalé indépendamment pour gérer un grand nombre de demandes de rapports.

### **Module 16 : Service de Notifications (`notification-service`)**

*   **Objectif Stratégique & Valeur Métier :**
    Assurer une communication proactive, opportune et personnalisée avec les adhérents et les gestionnaires. Une bonne communication est essentielle pour l'engagement, la satisfaction et la réduction de la charge de travail du support client.

*   **Description Fonctionnelle Détaillée :**
    Ce service centralisera l'envoi de toutes les communications sortantes : emails de bienvenue, notifications de paiement, rappels de certificat de vie, alertes de sécurité, etc. Il gérera des templates de messages personnalisables par les administrateurs.

*   **Implémentation Technique & Architecture :**
    Ce sera un service simple et léger. Il exposera une API REST interne (`POST /api/internal/notifications`) et souscrira à des dizaines d'événements métier (`Membership.Approved`, `Contribution.Reminder`, etc.). Il s'intégrera avec des fournisseurs externes d'envoi d'email (comme **SendGrid** ou **Mailgun**) et de SMS (via les API des opérateurs locaux).

*   **Sécurité, Performance & Scalabilité :**
    Les templates de messages seront stockés dans un cache Redis pour un accès rapide. Les envois seront placés dans une file d'attente interne pour gérer les pics de charge et les nouvelles tentatives en cas d'échec. Pour la sécurité, il nettoiera systématiquement le contenu des messages pour prévenir les injections de code (XSS).

### **Module 17 : Gestion des Investissements (`investment-service`)**
*   **Objectif Stratégique & Valeur Métier :**
    Permettre un suivi financier rigoureux des actifs du régime de retraite. Ce module offre une vue consolidée du portefeuille d'investissements, de sa performance et des risques associés, des informations cruciales pour le pilotage financier de la Mutuelle.

### **Module 18 : Intérêts & Rendements (`yield-service`)**
*   **Objectif Stratégique & Valeur Métier :**
    Assurer la redistribution équitable et transparente des gains financiers du régime aux adhérents. Ce processus est au cœur du principe de capitalisation et constitue un levier majeur de la performance des pensions individuelles.

### **Module 19 : Gestion des Assurances (`insurance-service`)**
*   **Objectif Stratégique & Valeur Métier :**
    Enrichir l'offre de la Mutuelle en intégrant des produits de prévoyance complémentaires (décès, invalidité). Cela permet de proposer une couverture de risque complète aux militaires et à leurs familles, renforçant le rôle social de l'institution.

### **Module 20 : Centre d'Aide (`help-center-service`)**
*   **Objectif Stratégique & Valeur Métier :**
    Augmenter l'autonomie des utilisateurs (adhérents et gestionnaires) en leur fournissant une information accessible et pertinente. Un bon centre d'aide réduit les coûts de support, améliore la satisfaction et facilite l'adoption de la plateforme.

### **Module 21 : Moteur de Détection de Fraude par IA (`fraud-detection-service`)**
*   **Objectif Stratégique & Valeur Métier :**
    Protéger le régime et ses adhérents contre les activités malveillantes. Ce module de sécurité proactif utilise l'intelligence artificielle pour identifier les transactions suspectes en temps réel, passant d'une sécurité réactive à une sécurité prédictive. C'est un différenciateur majeur qui démontre un engagement maximal pour la sécurité.

### **Module 22 : Conseil Financier Personnalisé (`robo-advisor-service`)**
*   **Objectif Stratégique & Valeur Métier :**
    Fournir un service à haute valeur ajoutée en guidant les adhérents dans leurs décisions d'épargne. Ce "Robo-Advisor" agit comme un conseiller financier virtuel, démocratisant l'accès à une expertise financière et renforçant l'engagement de l'adhérent avec la plateforme.

### **Module 23 : Business Intelligence & Data Analytics (`bi-service`)**
*   **Objectif Stratégique & Valeur Métier :**
    Offrir à la direction un outil décisionnel ultime pour l'exploration de données. Au-delà des rapports statiques, ce module permet une navigation interactive et multidimensionnelle dans les données du régime, pour découvrir des tendances cachées et prendre des décisions stratégiques éclairées.

---
Ce document sera mis à jour continuellement durant le projet pour refléter les décisions d'architecture et de conception.

---
