# ANNEXE ENRICHIE : PROCESSUS MÉTIER, GESTION ET INDICATEURS DE PERFORMANCE

## Introduction

Ce document détaille l'ensemble des processus métier couverts par la plateforme Waajal Ëlëk. Chaque module est décrit du point de vue de sa finalité stratégique, des règles de gestion qu'il applique, des mécanismes de contrôle qu'il intègre, et des **indicateurs de performance (KPIs)** qu'il permet de piloter. L'objectif est de fournir une vision exhaustive de la richesse fonctionnelle de la solution et de sa capacité à être un véritable outil de pilotage pour la Mutuelle.

---
## **PÔLE 1 : GESTION DU CYCLE DE VIE DE L'ADHÉRENT**
---

### **Module 1 : Gestion du Personnel Militaire (Référentiel Central)**

*   **Finalité Stratégique :**
    Ce module est le socle de la plateforme. Il a pour vocation de constituer le dossier individuel unique pour chaque militaire, garantissant ainsi l'unicité et la fiabilité des informations fondamentales. La constitution de ce référentiel centralisé est un prérequis indispensable à la justesse des calculs de droits, à la personnalisation de la communication et à la conformité réglementaire. Il s'agit de la "carte d'identité" de l'adhérent au sein du régime, sur laquelle reposeront toutes les opérations futures.

*   **Processus Métier & Parcours Utilisateur :**
    Le processus débute par l'intégration des données du personnel existant, via des imports sécurisés et contrôlés de fichiers provenant de la DRH. Pour tout nouveau militaire, un dossier est créé par un gestionnaire habilité. L'interface lui permet de saisir l'ensemble des informations requises : état civil complet, données administratives (matricule, grade, corps, date d'incorporation), et informations de contact. Le gestionnaire peut ensuite joindre au dossier les pièces justificatives numérisées (carte d'identité, acte de service). Le module permet également de tracer l'évolution de la carrière : chaque promotion, chaque changement d'affectation est historisé, créant une chronologie complète du parcours du militaire.

*   **Règles de Gestion & Paramétrage :**
    Le système impose des contrôles de cohérence stricts à la saisie pour garantir la qualité des données (ex: une date d'incorporation ne peut être postérieure à la date de naissance). La structure du dossier est paramétrable pour pouvoir intégrer de nouveaux champs d'information si la réglementation ou les besoins de gestion évoluent. Les nomenclatures (grades, corps, unités) sont gérées dans des référentiels centraux, assurant l'homogénéité des données sur toute la plateforme. La notion de "rémunération de référence", assiette de calcul des cotisations, est également gérée ici, avec la possibilité de définir sa composition (solde de base, primes, indemnités).

*   **Contrôles, Audit & Conformité :**
    Toute création ou modification d'un dossier est tracée dans une piste d'audit détaillée : qui a fait la modification, quand, et quelle était la valeur précédente. L'accès à la consultation et à la modification des dossiers est strictement encadré par le système de gestion des habilitations. Des rapports de qualité de données peuvent être générés périodiquement pour identifier les dossiers incomplets ou présentant des anomalies, permettant ainsi de lancer des campagnes de mise à jour et de garantir en permanence la fiabilité du référentiel.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux de complétude des dossiers :** Pourcentage de dossiers ayant tous les champs obligatoires et pièces justificatives renseignés.
    *   **Taux d'anomalies de données :** Nombre de dossiers présentant des incohérences détectées par les contrôles automatiques.
    *   **Délai moyen de mise à jour :** Temps écoulé entre un changement de situation (ex: promotion) et sa répercussion dans la plateforme.
    *   **Nombre de consultations vs. modifications :** Ratio permettant de suivre l'activité de gestion sur le référentiel.

### **Module 2 : Adhésions et Contrats**

*   **Finalité Stratégique :**
    Ce module formalise la relation contractuelle entre le militaire et la Mutuelle. Il matérialise l'entrée de l'adhérent dans le régime et garantit que les conditions de son adhésion (taux de cotisation, options choisies) sont clairement définies et archivées. Une gestion rigoureuse des contrats est la clé de la sécurité juridique du régime et de la confiance des adhérents.

*   **Processus Métier & Parcours Utilisateur :**
    Lorsqu'un militaire souhaite adhérer, un gestionnaire initie une "demande d'enrôlement" dans le système. Cette demande passe par un workflow de validation : elle est d'abord instruite (vérification de l'éligibilité et des pièces), puis soumise à approbation. Une fois la demande approuvée, le système génère automatiquement le contrat d'adhésion et le bulletin d'adhésion correspondant au format PDF, qui est archivé dans le dossier du membre. Le statut de l'adhérent passe alors à "Actif", déclenchant son entrée dans le processus de cotisation.

*   **Règles de Gestion & Paramétrage :**
    Le système gère plusieurs types de contrats (ex: adhésion de base obligatoire, adhésion volontaire complémentaire). Les paramètres clés de chaque contrat, comme le taux de cotisation salariale ou les plafonds, sont configurables. Le workflow de validation est également paramétrable pour s'adapter à l'organisation de la Mutuelle (ex: validation à un ou deux niveaux). Le système gère également le cycle de vie du contrat : suspension (en cas de congé sans solde par exemple), réactivation et résiliation, chaque changement de statut étant soumis à des règles de gestion strictes.

*   **Contrôles, Audit & Conformité :**
    Chaque étape du workflow de validation est horodatée et tracée. Le bulletin d'adhésion généré constitue une preuve juridique de l'accord de l'adhérent. Le système garantit qu'un militaire ne peut avoir qu'un seul contrat actif à un instant T pour un même régime, évitant ainsi les doublons. Toute modification ultérieure du contrat (un avenant) fait l'objet d'un nouveau processus de validation et d'archivage, préservant l'historique complet de la relation contractuelle.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Délai moyen de traitement d'une adhésion :** Temps entre la soumission de la demande et l'activation du contrat.
    *   **Taux de conversion :** Pourcentage de demandes d'enrôlement qui aboutissent à une adhésion active.
    *   **Nombre d'avenants par contrat :** Indicateur de la fréquence des modifications contractuelles.
    *   **Taux de suspension/résiliation :** Suivi des sorties du régime, qui peut être analysé par grade, corps ou ancienneté.

### **Module 3 : Gestion des Retraités**

*   **Finalité Stratégique :**
    Assurer un suivi rigoureux et humain des militaires retraités, en garantissant la continuité des paiements et en maintenant le lien avec la Mutuelle. Ce module est essentiel pour la satisfaction à long terme des bénéficiaires et pour la réputation de l'institution, car il gère la phase où la promesse de la retraite se concrétise.

*   **Processus Métier & Parcours Utilisateur :**
    Lorsqu'un adhérent liquide ses droits, son dossier bascule automatiquement dans ce module. Les gestionnaires disposent alors d'une interface dédiée au suivi des retraités, leur permettant de consulter l'historique des paiements de pension, de gérer les coordonnées bancaires et de suivre les événements de vie importants. Le module intègre un processus de gestion des certificats de vie, envoyant des rappels automatiques aux retraités et offrant une interface simple pour le téléchargement du document validé.

*   **Règles de Gestion & Paramétrage :**
    Les règles de gestion de la réversion en cas de décès du retraité principal sont un élément clé de ce module. Le système permet de pré-enregistrer les bénéficiaires (conjoint, enfants) et les taux de réversion applicables. En cas de décès déclaré et validé, le système peut automatiquement initier le calcul et le versement de la pension de réversion aux ayants droit, selon les règles statutaires. Les périodicités et les dates de rappels pour les certificats de vie sont entièrement paramétrables.

*   **Contrôles, Audit & Conformité :**
    La modification des coordonnées bancaires d'un retraité est une opération à haut risque et est donc soumise à un contrôle renforcé (validation par un second utilisateur, notification automatique au retraité). Chaque versement de pension est tracé et rapproché d'un ordre de paiement. Le système bloque automatiquement les paiements pour les retraités dont le certificat de vie n'a pas été fourni dans les délais impartis, prévenant ainsi les versements indus.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux de conformité des certificats de vie :** Pourcentage de retraités ayant fourni un certificat de vie valide pour la période en cours.
    *   **Délai moyen de traitement d'un changement de RIB :** Mesure de la réactivité des services de gestion.
    *   **Nombre d'incidents de paiement :** Suivi des rejets bancaires ou autres problèmes liés au versement des pensions.
    *   **Taux de réversion :** Suivi du nombre de pensions principales qui se transforment en pensions de réversion.

---
## **PÔLE 2 : GESTION FINANCIÈRE ET PRESTATIONS**
---

### **Module 4 : Gestion des Cotisations**

*   **Finalité Stratégique :**
    Assurer la collecte régulière et exhaustive des cotisations, qui constituent le flux financier principal alimentant les réserves du régime. La performance et la rigueur de ce module sont directement liées à la capacité du régime à générer des produits financiers et, à terme, à honorer ses engagements envers les retraités.

*   **Processus Métier & Parcours Utilisateur :**
    Au début de chaque période (généralement mensuelle), le système identifie tous les adhérents actifs et calcule automatiquement le montant de la cotisation due pour chacun, en appliquant le taux de son contrat à son assiette de rémunération. Un "appel de cotisations" global est alors généré. Au fur et à mesure de la réception des paiements (via prélèvement sur la paie ou paiement direct), les gestionnaires effectuent le lettrage des cotisations. L'interface de suivi offre une vue en temps réel du taux de recouvrement et met en évidence les cotisations en attente ou en retard.

*   **Règles de Gestion & Paramétrage :**
    La complexité de ce module réside dans la finesse de ses règles de calcul. Le système permet de paramétrer précisément le calcul de l'assiette (quels éléments de la rémunération sont inclus), les règles de proratisation pour les mois d'entrée ou de sortie, et les conditions de suspension des prélèvements. Les règles de gestion des retards (délai de grâce, calcul des pénalités) sont également entièrement configurables pour s'adapter à la politique de la Mutuelle.

*   **Contrôles, Audit & Conformité :**
    Un contrôle de cohérence est effectué avant chaque appel de cotisations pour s'assurer que tous les adhérents actifs ont un contrat valide et une assiette de rémunération renseignée. Chaque paiement est tracé et rapproché d'une cotisation due. Le système génère des journaux de cotisations détaillés qui servent de base aux écritures comptables et permettent un audit complet des flux entrants. Des alertes automatiques peuvent être configurées pour notifier les gestionnaires en cas de retard de paiement significatif.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux de recouvrement global :** Pourcentage des cotisations appelées qui ont été encaissées sur la période.
    *   **Délai moyen de paiement (DSO) :** Nombre de jours moyen entre la date d'échéance de la cotisation et son paiement effectif.
    *   **Taux de cotisations en retard (> 30 jours) :** Pourcentage des cotisations non réglées plus de 30 jours après leur échéance.
    *   **Efficacité du lettrage automatique :** Pourcentage des paiements rapprochés automatiquement sans intervention manuelle.

### **Module 5 : Conversion en Points**

*   **Finalité Stratégique :**
    Traduire l'effort financier de l'adhérent en une unité de compte de retraite : le point. Ce mécanisme est le cœur du régime par points. La transparence et l'intégrité de ce module sont essentielles, car il matérialise l'accumulation des droits futurs de l'adhérent.

*   **Processus Métier & Parcours Utilisateur :**
    Ce processus est entièrement automatisé et se déclenche dès qu'une cotisation est marquée comme "payée". Le système récupère le montant versé et le divise par la "valeur d'achat du point" en vigueur à la date du paiement pour déterminer le nombre de points à créditer au compte de l'adhérent. L'adhérent peut consulter sur son portail personnel le détail de chaque acquisition de points, lui permettant de suivre en toute transparence la constitution de son futur capital retraite.

*   **Règles de Gestion & Paramétrage :**
    La "valeur d'achat du point" est le paramètre central de ce module. Elle est fixée par les instances de gouvernance de la Mutuelle et peut évoluer dans le temps. Le système historise chaque changement de cette valeur pour garantir que les calculs utilisent toujours la valeur correcte en fonction de la date de la transaction. Le module permet également aux administrateurs d'effectuer des attributions de points exceptionnelles (points gratuits, bonifications pour ancienneté, etc.), soumises à un processus de validation spécifique.

*   **Contrôles, Audit & Conformité :**
    Chaque opération d'acquisition de points est une transaction indivisible et tracée. Le système garantit qu'une même cotisation ne peut être convertie en points qu'une seule fois. Un rapport de rapprochement "Cotisations / Points" peut être généré à tout moment pour vérifier que le total des points attribués correspond bien au total des cotisations encaissées, divisé par la valeur du point. Ceci constitue un contrôle fondamental de la cohérence du régime.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre de points moyens acquis par an :** Indicateur de la dynamique d'accumulation de droits.
    *   **Évolution de la valeur d'achat du point :** Suivi historique d'un des paramètres clés du régime.
    *   **Nombre et montant des points gratuits attribués :** Suivi des politiques de bonification.
    *   **Délai de conversion :** Temps entre le paiement de la cotisation et l'attribution effective des points.

### **Module 6 : Gestion des Pensions de Retraite**

*   **Finalité Stratégique :**
    Concrétiser la promesse du régime de retraite en transformant les droits accumulés (les points) en une prestation financière (rente ou capital). La rigueur, la conformité réglementaire et l'exactitude des calculs de ce module sont absolues, car elles garantissent le respect des engagements pris envers chaque militaire.

*   **Processus Métier & Parcours Utilisateur :**
    Lorsqu'un adhérent atteint l'âge de la retraite ou remplit les conditions de départ, un gestionnaire initie le processus de "liquidation". L'interface le guide à travers les étapes : vérification des conditions, calcul du capital de points, présentation des options de sortie. Le système calcule le montant de la rente viagère, du capital unique ou des options mixtes, en présentant clairement l'impact de chaque choix. Une fois l'option choisie par l'adhérent et validée, le système génère la "notification de concession de pension" et prépare le premier versement.

*   **Règles de Gestion & Paramétrage :**
    La "valeur de service du point" est le paramètre clé pour la conversion des points en prestation. Comme la valeur d'achat, elle est fixée par la gouvernance et historisée. Le module intègre les règles de calcul pour les différentes options de sortie, y compris les paramètres fiscaux applicables. Les conditions d'éligibilité à la liquidation (âge, nombre de points minimum, etc.) sont entièrement paramétrables.

*   **Contrôles, Audit & Conformité :**
    Le processus de liquidation est soumis à un workflow de validation strict, impliquant potentiellement plusieurs niveaux de contrôle (calculateur, vérificateur, approbateur) pour garantir l'exactitude des montants. Un dossier de liquidation complet est archivé, contenant toutes les données et paramètres utilisés pour le calcul (total de points, valeur de service, table de mortalité utilisée, etc.), assurant une auditabilité parfaite même des années plus tard.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Délai moyen de liquidation d'une pension :** Temps entre la demande de l'adhérent et le premier versement.
    *   **Taux de remplacement moyen :** Ratio entre le montant de la première pension et la dernière rémunération de référence.
    *   **Répartition des options de sortie :** Pourcentage d'adhérents choisissant la rente, le capital ou une option mixte.
    *   **Montant moyen de la pension liquidée :** Suivi de l'évolution du niveau des prestations.

### **Module 7 : Démissions & Rachats**

*   **Finalité Stratégique :**
    Offrir une flexibilité encadrée aux adhérents souhaitant quitter le régime de manière anticipée. Ce module doit appliquer de manière stricte les règles statutaires tout en offrant un processus clair et transparent à l'adhérent, protégeant ainsi les intérêts financiers du régime (en appliquant des pénalités) et ceux de l'individu.

*   **Processus Métier & Parcours Utilisateur :**
    Un adhérent peut, depuis son portail, initier une demande de rachat (partiel ou total). Le système vérifie en temps réel son éligibilité en fonction des règles d'ancienneté et du capital accumulé. Il calcule ensuite le montant rachetable, en déduisant les pénalités de sortie anticipée, et présente une simulation claire à l'adhérent. Si l'adhérent confirme, la demande est transmise à un gestionnaire pour validation finale avant le paiement.

*   **Règles de Gestion & Paramétrage :**
    Toutes les conditions de rachat sont paramétrables : durée de cotisation minimale requise, pourcentage du capital rachetable, formule de calcul des pénalités en fonction de l'ancienneté, etc. Le système peut gérer différents types de rachats (ex: rachat pour cas de force majeure avec des conditions plus favorables) dont les règles sont également configurables.

*   **Contrôles, Audit & Conformité :**
    Le module garantit qu'un rachat ne peut excéder les limites autorisées par les statuts du régime. Chaque demande, simulation et validation est journalisée. Le paiement faisant suite à un rachat est tracé et automatiquement enregistré dans le module de comptabilité. Le système met également à jour le solde de points de l'adhérent pour refléter l'impact du rachat sur ses droits futurs.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre de demandes de rachat par mois/an :** Suivi de la tendance des sorties anticipées.
    *   **Montant moyen des rachats :** Analyse de l'impact financier des sorties.
    *   **Motifs de rachat les plus fréquents :** Permet de comprendre les raisons des départs.
    *   **Délai moyen de traitement d'une demande de rachat.**

### **Module 8 : Avances sur Capital**

*   **Finalité Stratégique :**
    Fournir une aide financière ponctuelle aux adhérents en difficulté, en utilisant leur capital retraite comme garantie. Ce module renforce la proposition de valeur de la Mutuelle en agissant comme un filet de sécurité pour ses membres, tout en assurant un remboursement structuré qui préserve l'intégrité de leurs droits futurs à la retraite.

*   **Processus Métier & Parcours Utilisateur :**
    Le processus est similaire à celui du rachat. L'adhérent fait une demande d'avance depuis son portail. Le système évalue son éligibilité et calcule le montant maximum de l'avance autorisée (généralement un pourcentage du capital déjà constitué). Si la demande est approuvée, un échéancier de remboursement est automatiquement généré. Le suivi des remboursements est accessible à la fois par le gestionnaire et l'adhérent.

*   **Règles de Gestion & Paramétrage :**
    Les conditions des avances sont entièrement configurables : taux d'intérêt applicable à l'avance, durée maximale de remboursement, nombre maximal d'avances autorisées, etc. Le système peut gérer différentes modalités de remboursement : prélèvement sur les cotisations futures, paiements directs par l'adhérent, ou déduction du salaire via une interface avec la paie.

*   **Contrôles, Audit & Conformité :**
    Avant d'approuver une avance, le système présente une simulation claire de l'impact des remboursements sur le revenu de l'adhérent et de l'impact potentiel sur sa pension future. Chaque remboursement est suivi et lettré par rapport à l'échéancier. En cas de défaut de paiement, le système peut déclencher des alertes et appliquer des procédures de recouvrement prédéfinies.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux d'utilisation du dispositif d'avance :** Pourcentage d'adhérents ayant une avance en cours.
    *   **Montant moyen des avances accordées.**
    *   **Taux de défaut sur les remboursements.**
    *   **Durée moyenne de remboursement d'une avance.**

### **Module 9 : Comptabilité & Comptes**

*   **Finalité Stratégique :**
    Garantir l'intégrité, la conformité et l'auditabilité de toutes les transactions financières du régime. Ce service centralise la logique comptable pour fournir une vue financière fiable, produire les états réglementaires et offrir une vision claire de la santé financière de la Mutuelle aux instances de gouvernance.

*   **Processus Métier & Parcours Utilisateur :**
    Ce module est principalement utilisé par les services comptables. Il enregistre automatiquement toutes les opérations financières (cotisations, paiements de pension, rachats, investissements, etc.) dans un système en partie double. Il permet de gérer le plan comptable, de générer des journaux comptables, des balances générales et auxiliaires, et de produire les états financiers périodiques (bilan, compte de résultat). Il intègre également des outils pour faciliter le rapprochement bancaire.

*   **Règles de Gestion & Paramétrage :**
    Le plan comptable est entièrement personnalisable pour s'adapter aux spécificités du régime. Le système de lettrage automatique peut être configuré avec des règles précises pour rapprocher les transactions bancaires des opérations de gestion. Les schémas d'écritures comptables (quels comptes débiter/créditer pour chaque type d'opération) sont prédéfinis mais peuvent être ajustés par les administrateurs comptables.

*   **Contrôles, Audit & Conformité :**
    La méthodologie en partie double garantit par nature l'équilibre de la comptabilité. Le système assure une piste d'audit complète, où chaque écriture comptable est directement liée à l'opération de gestion qui l'a générée. La clôture des périodes comptables est un processus sécurisé qui "gèle" les écritures pour garantir leur inaltérabilité. Le module est conçu pour produire des exports conformes aux exigences des auditeurs et des commissaires aux comptes.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Délai de clôture comptable mensuelle/annuelle.**
    *   **Nombre d'écritures manuelles vs. automatiques :** Mesure du niveau d'automatisation.
    *   **Taux de rapprochement bancaire automatique.**
    *   **Temps de génération des états financiers.**

### **Module 10 : Gestion des Investissements**

*   **Finalité Stratégique :**
    Permettre un suivi financier rigoureux et une analyse de la performance des actifs du régime de retraite. La valorisation du capital étant un pilier du régime, ce module offre une vue consolidée du portefeuille d'investissements, de sa performance et des risques associés, des informations cruciales pour le pilotage financier et la stratégie d'allocation d'actifs de la Mutuelle.

*   **Processus Métier & Parcours Utilisateur :**
    Les gestionnaires de portefeuille utilisent ce module pour enregistrer chaque opération d'investissement (achats/ventes d'actions, d'obligations, investissements immobiliers, etc.). Le système permet de classer les actifs par type, par secteur ou par niveau de risque. Il calcule et affiche en temps réel la valeur du portefeuille, les plus ou moins-values latentes et réalisées, et le rendement global et par classe d'actifs.

*   **Règles de Gestion & Paramétrage :**
    Le module permet de définir des seuils d'alerte sur les performances ou les niveaux de risque. Il peut s'interfacer avec des flux de données de marché (si disponible) pour valoriser automatiquement certains actifs. Les différentes méthodes de calcul de rendement (TWR, MWR) peuvent être paramétrées.

*   **Contrôles, Audit & Conformité :**
    Chaque opération d'investissement est tracée et doit être validée. Le module permet de générer des rapports de performance détaillés pour les comités d'investissement. Il aide à vérifier la conformité avec la politique de placement du régime (respect des ratios d'allocation, des limites de risque, etc.).

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Rendement global du portefeuille (annualisé).**
    *   **Volatilité du portefeuille (écart-type des rendements).**
    *   **Ratio de Sharpe :** Mesure du rendement ajusté au risque.
    *   **Suivi de l'allocation d'actifs vs. l'allocation cible.**

### **Module 11 : Intérêts & Rendements**

*   **Finalité Stratégique :**
    Assurer la redistribution équitable et transparente des gains financiers du régime aux adhérents. Ce processus est au cœur du principe de capitalisation et constitue un levier majeur de la performance des pensions individuelles. Il matérialise pour l'adhérent le fruit de la bonne gestion financière de ses cotisations.

*   **Processus Métier & Parcours Utilisateur :**
    Périodiquement (généralement une fois par an), après la clôture des comptes et la validation de la performance financière du régime, les administrateurs lancent le processus de distribution des rendements. Le système calcule le montant global à distribuer et le répartit entre les adhérents au prorata de leurs droits (nombre de points ou capital accumulé).

*   **Règles de Gestion & Paramétrage :**
    La règle de répartition est un paramètre crucial. Le système peut supporter plusieurs méthodes (ex: au prorata du nombre de points, au prorata du capital moyen sur la période, etc.). Le taux de rendement distribué peut être plafonné, et une partie des gains peut être affectée à une réserve de prévoyance, selon les statuts du régime. Toutes ces règles sont configurables.

*   **Contrôles, Audit & Conformité :**
    Le processus de distribution est une opération critique qui fait l'objet d'un workflow de validation renforcé. Avant l'attribution définitive, le système génère un rapport de simulation complet qui doit être validé par les instances de gouvernance. Une fois l'opération effectuée, chaque attribution est tracée et apparaît clairement sur le relevé de points de l'adhérent.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux de rendement net distribué aux adhérents.**
    *   **Montant total des rendements distribués.**
    *   **Comparaison du taux distribué vs. le rendement du portefeuille.**
    *   **Montant mis en réserve (si applicable).**

---
## **PÔLE 3 : PILOTAGE, COMMUNICATION & MODULES AVANCÉS**
---

### **Module 12 : Portail Personnel Militaire**

*   **Finalité Stratégique :**
    Offrir à chaque adhérent un accès direct, sécurisé et transparent à l'ensemble de ses informations de retraite. Ce portail est l'outil principal de communication et de confiance entre la Mutuelle et ses membres. Il vise à responsabiliser l'adhérent en lui donnant de l'autonomie et une vision claire de ses droits.

*   **Processus Métier & Parcours Utilisateur :**
    Après son adhésion, le militaire reçoit ses identifiants pour se connecter à son espace personnel. Il y trouve un tableau de bord synthétique : son solde de points, la valeur estimée de son capital, l'historique de ses cotisations. Il peut consulter et télécharger ses documents (relevés annuels, bulletin d'adhésion), mettre à jour ses informations personnelles (adresse, contact) et utiliser les outils de simulation.

*   **Règles de Gestion & Paramétrage :**
    Les informations affichées sur le portail sont en lecture seule pour la plupart, garantissant que l'adhérent ne peut pas modifier de données sensibles. Les demandes de modification (ex: changement de situation familiale) passent par des formulaires qui initient un processus de validation côté gestionnaire. Le contenu informationnel du portail (actualités, FAQ) est gérable par les administrateurs.

*   **Contrôles, Audit & Conformité :**
    L'accès au portail est sécurisé par mot de passe et peut être renforcé par une authentification à deux facteurs (2FA). Toutes les connexions et les actions importantes (téléchargement de document, demande de modification) sont journalisées. Le portail est conçu pour être conforme aux normes d'accessibilité (WCAG) pour garantir son utilisation par tous.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux d'activation du portail :** Pourcentage d'adhérents s'étant connectés au moins une fois.
    *   **Fréquence de connexion par adhérent.**
    *   **Taux d'utilisation des fonctionnalités clés (simulation, consultation de relevé).**
    *   **Nombre de demandes de support initiées depuis le portail.**

### **Module 13 : Rapports & Analyses**

*   **Finalité Stratégique :**
    Transformer les données brutes de la plateforme en informations exploitables pour le pilotage opérationnel et la prise de décision stratégique. Ce service fournit les rapports d'activité, les statistiques et les tableaux de bord nécessaires à la gestion quotidienne et stratégique de la Mutuelle.

*   **Processus Métier & Parcours Utilisateur :**
    Les gestionnaires et dirigeants accèdent à une bibliothèque de rapports prédéfinis (rapports d'activité, statistiques démographiques, indicateurs de performance). Un outil de reporting ad-hoc leur permet de créer leurs propres rapports en sélectionnant des champs, en appliquant des filtres et en choisissant le format de sortie (Excel, PDF, CSV). Ils peuvent également programmer la génération et l'envoi automatique de rapports par email.

*   **Règles de Gestion & Paramétrage :**
    La bibliothèque de rapports est entièrement configurable. De nouveaux rapports peuvent être conçus et ajoutés sans développement. Les droits d'accès aux rapports sont gérés de manière fine : un gestionnaire de cotisations n'aura pas accès aux mêmes rapports qu'un membre de la direction.

*   **Contrôles, Audit & Conformité :**
    L'accès à des données agrégées et statistiques est moins sensible que l'accès aux dossiers individuels, mais il est tout de même tracé. Le module permet de générer les rapports réglementaires requis par les autorités de tutelle, dans le format attendu. La cohérence des chiffres entre les différents rapports est garantie par l'utilisation du référentiel de données unique.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre de rapports générés par mois.**
    *   **Taux d'utilisation des rapports ad-hoc vs. standards.**
    *   **Temps moyen de génération d'un rapport complexe.**
    *   **Satisfaction des utilisateurs sur la pertinence des rapports.**

### **Module 14 : Simulateur Actuariel Global**

*   **Finalité Stratégique :**
    Fournir à la direction de la Mutuelle un outil de pilotage stratégique pour assurer la pérennité du régime. Ce module permet de répondre à des questions complexes comme : "Quel sera notre besoin de financement dans 20 ans si la pyramide des âges évolue de telle manière ?" ou "Quel est l'impact d'une crise économique sur notre capacité à honorer nos engagements ?".

*   **Processus Métier & Parcours Utilisateur :**
    Via une interface dédiée et sécurisée, les actuaires et dirigeants peuvent modéliser l'avenir du régime. Ils peuvent définir des scénarios en ajustant les hypothèses macroéconomiques (inflation, rendement des investissements) et démographiques (évolution des effectifs, tables de mortalité). Le système projette alors l'évolution des actifs et des passifs du régime sur des décennies, et présente les résultats sous forme de graphiques (évolution du taux de couverture, etc.).

*   **Règles de Gestion & Paramétrage :**
    Le module intègre plusieurs modèles de projection actuarielle. Les tables de mortalité réglementaires sont incluses, mais il est possible d'importer et d'utiliser des tables prospectives. Toutes les hypothèses d'un scénario peuvent être sauvegardées pour être rejouées ou comparées ultérieurement.

*   **Contrôles, Audit & Conformité :**
    Ce module est un outil d'aide à la décision. Les résultats qu'il produit sont clairement identifiés comme des projections basées sur des hypothèses. Chaque simulation est tracée (qui l'a lancée, avec quelles hypothèses) pour garantir la transparence du processus de décision stratégique. L'accès à ce module est réservé à un très petit nombre d'utilisateurs habilités.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre de scénarios de stress-test réalisés par trimestre.**
    *   **Écart entre les projections et le réalisé (analysé a posteriori).**
    *   **Sensibilité du taux de couverture à une variation de 1% du rendement des actifs.**
    *   **Âge moyen d'équilibre du régime (moment où les prestations versées dépassent les cotisations perçues).**

### **Module 15 : Simulations Personnalisées (Portail Adhérent)**

*   **Finalité Stratégique :**
    Responsabiliser et engager l'adhérent en lui donnant les outils pour comprendre et optimiser sa propre retraite. En lui permettant de visualiser l'impact de ses décisions (cotiser plus, partir plus tard), ce module transforme l'adhérent d'un spectateur passif en un acteur éclairé de sa sécurité financière future.

*   **Processus Métier & Parcours Utilisateur :**
    Depuis son portail, l'adhérent accède au simulateur. Le formulaire est pré-rempli avec ses données réelles (âge, points déjà acquis, etc.). Il peut ensuite créer des scénarios personnels : "Que se passe-t-il si je suis promu dans 2 ans ?", "Et si je cotise 2% de plus ?", "Quel serait le montant de ma pension si je pars à 55 ans au lieu de 58 ?". Les résultats sont présentés de manière simple et graphique, comparant l'impact de chaque scénario sur le montant de sa future pension.

*   **Règles de Gestion & Paramétrage :**
    Le moteur de simulation utilise les mêmes paramètres actuariels que le reste de la plateforme (valeur de service du point, hypothèses de rendement) pour garantir la cohérence. Cependant, les résultats sont clairement présentés comme des estimations non contractuelles. Les scénarios "types" (ex: "carrière accélérée") peuvent être pré-configurés par les administrateurs pour guider l'adhérent.

*   **Contrôles, Audit & Conformité :**
    L'utilisation du simulateur est anonyme dans le sens où les scénarios créés par l'adhérent ne sont pas stockés de manière nominative (sauf s'il choisit de les sauvegarder). L'objectif est de l'encourager à explorer librement les possibilités. Le système garantit que les simulations sont basées sur les règles du régime en vigueur, fournissant une information fiable, bien que non contractuelle.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux d'utilisation du simulateur par les adhérents actifs.**
    *   **Nombre moyen de scénarios créés par utilisateur.**
    *   **Scénarios les plus fréquemment testés (ex: départ anticipé).**
    *   **Corrélation entre l'utilisation du simulateur et les cotisations volontaires.**

### **Module 16 : Application Mobile & Notifications Push**

*   **Finalité Stratégique :**
    Ancrer la Mutuelle dans le quotidien du militaire en lui offrant un accès à son régime de retraite directement depuis son téléphone. L'application mobile est un canal de communication privilégié pour envoyer des informations importantes et renforcer le lien de proximité avec les adhérents, où qu'ils soient.

*   **Processus Métier & Parcours Utilisateur :**
    L'adhérent télécharge l'application sur les stores iOS ou Android. Après une première authentification sécurisée, il peut accéder à son tableau de bord, consulter son solde de points, et recevoir des notifications push pour les événements importants (confirmation de paiement, alerte, etc.). L'application offre une expérience utilisateur optimisée pour le mobile, avec une navigation simple et un accès rapide aux informations clés.

*   **Règles de Gestion & Paramétrage :**
    L'application mobile se concentre sur les fonctionnalités de consultation et de notification. Les opérations plus complexes (comme la modification de données personnelles) renvoient vers le portail web pour des raisons de sécurité et d'ergonomie. Le contenu et la fréquence des notifications push sont paramétrables par les administrateurs pour éviter de surcharger l'utilisateur.

*   **Contrôles, Audit & Conformité :**
    L'accès à l'application peut être protégé par les fonctionnalités biométriques du téléphone (empreinte digitale, reconnaissance faciale), ajoutant une couche de sécurité. La communication entre l'application et les serveurs est entièrement chiffrée. Les sessions sont gérées avec des jetons à durée de vie limitée pour se prémunir contre le vol de session.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux de téléchargement et d'installation de l'application.**
    *   **Nombre d'utilisateurs actifs mensuels (MAU) sur l'application.**
    *   **Taux d'ouverture des notifications push.**
    *   **Note moyenne de l'application sur les stores.**

### **Module 17 : Gestion des Assurances Complémentaires**

*   **Finalité Stratégique :**
    Enrichir l'offre de la Mutuelle en intégrant des produits de prévoyance complémentaires (assurance décès, invalidité, etc.). Cela permet de proposer une couverture de risque complète aux militaires et à leurs familles, renforçant le rôle social de l'institution et créant des synergies de gestion.

*   **Processus Métier & Parcours Utilisateur :**
    Ce module permet aux gestionnaires de créer et gérer des contrats d'assurance liés aux adhérents du régime de retraite. Il gère la collecte des primes (qui peut être couplée à celle des cotisations retraite), le suivi des garanties, et le processus de déclaration et de gestion des sinistres. En cas de sinistre (ex: invalidité), le module peut interagir avec le module de retraite pour déclencher des prestations spécifiques (ex: majoration de la pension, exonération des cotisations).

*   **Règles de Gestion & Paramétrage :**
    Chaque produit d'assurance est entièrement paramétrable : garanties, calcul des primes, conditions d'éligibilité, etc. Le workflow de gestion des sinistres, de la déclaration à l'indemnisation, est également configurable pour s'adapter aux procédures de la Mutuelle.

*   **Contrôles, Audit & Conformité :**
    Le module assure une séparation claire entre la gestion des fonds du régime de retraite et ceux des produits d'assurance. Chaque opération est tracée et fait l'objet d'écritures comptables distinctes. Les contrats et les déclarations de sinistres sont archivés numériquement pour garantir leur auditabilité.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux de souscription aux produits d'assurance complémentaires.**
    *   **Ratio Sinistres/Primes (S/P) par produit.**
    *   **Délai moyen d'indemnisation d'un sinistre.**
    *   **Chiffre d'affaires généré par les produits d'assurance.**

### **Module 18 : Centre d'Aide et Support**

*   **Finalité Stratégique :**
    Augmenter l'autonomie des utilisateurs (adhérents et gestionnaires) en leur fournissant une information accessible, pertinente et centralisée. Un bon centre d'aide réduit les coûts de support, améliore la satisfaction et facilite l'adoption et la bonne utilisation de la plateforme.

*   **Processus Métier & Parcours Utilisateur :**
    Les utilisateurs peuvent accéder à une base de connaissances contenant des articles, des guides d'utilisation et une section "Foire Aux Questions" (FAQ). Un moteur de recherche permet de trouver rapidement une réponse à une question. Si l'utilisateur ne trouve pas de réponse, il peut ouvrir un "ticket de support" via un formulaire, qui sera ensuite traité par les équipes de la Mutuelle.

*   **Règles de Gestion & Paramétrage :**
    L'ensemble du contenu du centre d'aide est gérable par les administrateurs via un éditeur de texte riche. Les articles peuvent être organisés par catégories. Le système de ticketing est configurable (catégories de demandes, niveaux de priorité, assignation automatique à des groupes de gestionnaires).

*   **Contrôles, Audit & Conformité :**
    Le module permet de suivre les statistiques de consultation des articles et les types de demandes de support les plus fréquentes. Ces informations sont précieuses pour identifier les points de friction pour les utilisateurs et pour améliorer continuellement la plateforme et sa documentation.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre de tickets de support créés par mois.**
    *   **Taux de résolution au premier contact.**
    *   **Délai moyen de résolution d'un ticket.**
    *   **Articles de la base de connaissances les plus consultés.**

### **Module 19 : Administration & Sécurité**

*   **Finalité Stratégique :**
    Fournir aux administrateurs les outils pour configurer, superviser et sécuriser l'ensemble de la plateforme. Ce module est le "poste de pilotage" du système, essentiel pour garantir son bon fonctionnement, sa sécurité et son adaptabilité dans le temps.

*   **Processus Métier & Parcours Utilisateur :**
    Les administrateurs accèdent à un panneau de configuration centralisé où ils peuvent gérer les utilisateurs et leurs droits (via le module de rôles), modifier les paramètres généraux du système (valeur du point, etc.), superviser l'état de la plateforme (monitoring), et consulter le journal d'audit de toutes les opérations.

*   **Règles de Gestion & Paramétrage :**
    La quasi-totalité des règles de gestion de la plateforme est centralisée et paramétrable depuis ce module. Cela inclut les paramètres actuariels, les règles de calcul des cotisations, les conditions de rachat, etc. Ce haut niveau de paramétrage garantit que la plateforme pourra s'adapter aux futures évolutions réglementaires ou statutaires sans nécessiter de développements informatiques.

*   **Contrôles, Audit & Conformité :**
    L'accès à ce module est le plus sécurisé de tous. Chaque action effectuée dans le panneau d'administration est une opération à haute sensibilité, qui est donc enregistrée dans le journal d'audit avec un niveau de criticité maximal. La modification de paramètres financiers ou actuariels clés peut être soumise à un principe de double validation.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre de modifications de paramètres critiques par mois.**
    *   **Historique des accès au panneau d'administration.**
    *   **Temps de réponse moyen de la plateforme (monitoring de performance).**
    *   **Nombre d'alertes de sécurité générées et traitées.**

### **Module 20 : Moteur de Calcul Actuariel Avancé**

*   **Finalité Stratégique :**
    Raffiner la précision des calculs actuariels en intégrant des hypothèses multiples et des modèles prospectifs. Ce module permet de passer d'une vision déterministe à une vision probabiliste des engagements, offrant ainsi une gestion des risques plus fine et plus sophistiquée.

*   **Processus Métier & Parcours Utilisateur :**
    Utilisé par les actuaires, ce module leur permet de définir plusieurs jeux d'hypothèses (optimiste, réaliste, pessimiste) pour les paramètres clés comme le rendement des actifs ou l'inflation. Les autres modules (simulation, liquidation) peuvent alors utiliser ces différents jeux d'hypothèses pour présenter des fourchettes de résultats (ex: "votre pension sera comprise entre X et Y selon le scénario économique").

*   **Règles de Gestion & Paramétrage :**
    Le module permet d'importer et de gérer différentes tables de mortalité (tables réglementaires, tables prospectives, etc.). Il intègre des modèles stochastiques pour les simulations Monte Carlo, permettant d'estimer la probabilité d'atteindre certains objectifs ou de faire face à un déficit.

*   **Contrôles, Audit & Conformité :**
    Les calculs produits par ce moteur avancé sont clairement identifiés comme étant le résultat de modèles probabilistes. Les hypothèses utilisées pour chaque calcul sont systématiquement enregistrées et présentées avec les résultats, garantissant une transparence totale sur la manière dont les chiffres ont été obtenus.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Écart-type des résultats de simulation Monte Carlo.**
    *   **Probabilité de financement du régime à horizon 30 ans.**
    *   **Impact sur le passif social d'un changement de table de mortalité.**
    *   **Nombre de modèles d'hypothèses gérés.**

### **Module 21 : Moteur de Détection de Fraude par IA**

*   **Finalité Stratégique :**
    Protéger activement le régime et ses adhérents contre les activités malveillantes ou anormales. Ce module de sécurité proactif utilise l'intelligence artificielle pour identifier les transactions suspectes en temps réel, passant d'une sécurité réactive (constater la fraude) à une sécurité prédictive (la bloquer avant qu'elle n'aboutisse). C'est un différenciateur majeur qui démontre un engagement maximal pour la sécurité des fonds du régime.

*   **Processus Métier & Parcours Utilisateur :**
    Ce module fonctionne en arrière-plan, sans interface directe pour la majorité des utilisateurs. Il analyse en continu le flux des opérations (demandes de rachat, changements de RIB, connexions, etc.). Lorsqu'il détecte un comportement jugé anormal (ex: un adhérent se connecte depuis un pays inhabituel et demande immédiatement un rachat total), il peut automatiquement bloquer l'opération et créer une alerte de haute priorité pour l'équipe de sécurité.

*   **Règles de Gestion & Paramétrage :**
    Le moteur s'appuie sur des modèles de "machine learning" qui apprennent le comportement "normal" de chaque adhérent. Les administrateurs peuvent ajuster la sensibilité du moteur pour trouver le bon équilibre entre la détection de la fraude et le risque de "faux positifs". Ils peuvent également définir des règles manuelles (ex: "bloquer toute demande de rachat supérieure à X montant initiée moins de 24h après un changement de mot de passe").

*   **Contrôles, Audit & Conformité :**
    Chaque alerte générée par le moteur est enregistrée avec tout le contexte qui a mené à la décision (les données analysées, le score de risque calculé). Ce journal est essentiel pour l'analyse post-incident et pour l'amélioration continue des modèles de détection. L'utilisation de l'IA pour la sécurité est une pratique de plus en plus recommandée par les régulateurs du secteur financier.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre de transactions suspectes bloquées par mois.**
    *   **Taux de faux positifs (alertes légitimes).**
    *   **Montant de la fraude potentielle évitée.**
    *   **Délai moyen de traitement d'une alerte par l'équipe de sécurité.**

### **Module 22 : Conseil Financier Personnalisé (Robo-Advisor)**

*   **Finalité Stratégique :**
    Fournir un service à haute valeur ajoutée en guidant les adhérents dans leurs décisions d'épargne. Ce "Robo-Advisor" agit comme un conseiller financier virtuel, démocratisant l'accès à une expertise financière et renforçant l'engagement de l'adhérent avec la plateforme en lui montrant des voies concrètes pour améliorer sa situation future.

*   **Processus Métier & Parcours Utilisateur :**
    Intégré au portail personnel, ce module analyse la situation de l'adhérent (âge, capital, carrière) et ses objectifs (via un court questionnaire). Il lui fournit ensuite des recommandations personnalisées : "Nous avons constaté que vous pourriez augmenter votre pension de 15% en effectuant une cotisation volontaire de X FCFA par mois." ou "Votre taux de remplacement projeté est de 40%. Pour atteindre l'objectif de 50%, nous vous suggérons d'envisager de repousser votre départ de 18 mois."

*   **Règles de Gestion & Paramétrage :**
    Le moteur de recommandation est basé sur un ensemble de règles expertes définies par les conseillers financiers de la Mutuelle. Ces règles peuvent être ajustées via une interface d'administration. Par exemple, les conseils peuvent être plus prudents pour les adhérents proches de la retraite et plus axés sur la croissance pour les plus jeunes.

*   **Contrôles, Audit & Conformité :**
    Toutes les recommandations sont accompagnées d'un avertissement clair indiquant qu'il ne s'agit pas d'un conseil en investissement contractuel, mais d'une aide à la décision basée sur des simulations. Le système garde une trace des recommandations proposées à chaque adhérent, ce qui peut être utile pour l'analyse du comportement des utilisateurs et l'amélioration des stratégies de conseil.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Taux d'adoption du service de conseil par les adhérents.**
    *   **Taux de conversion :** Pourcentage d'adhérents qui suivent une recommandation (ex: augmenter leurs cotisations).
    *   **Satisfaction des utilisateurs vis-à-vis de la pertinence des conseils.**
    *   **Impact mesuré des recommandations sur le niveau d'épargne global.**

### **Module 23 : Business Intelligence & Data Analytics**

*   **Finalité Stratégique :**
    Offrir à la direction un outil décisionnel ultime pour l'exploration de données. Au-delà des rapports statiques, ce module permet une navigation interactive et multidimensionnelle dans les données du régime, pour découvrir des tendances cachées, comprendre les corrélations et prendre des décisions stratégiques éclairées basées sur des faits et non des intuitions.

*   **Processus Métier & Parcours Utilisateur :**
    Les dirigeants et analystes accèdent à des tableaux de bord dynamiques (dashboards). Contrairement aux rapports figés, ils peuvent ici interagir avec les graphiques : zoomer sur une période, filtrer par grade ou par région, passer d'une vue macro (la démographie de tous les corps d'armée) à une vue micro (la démographie d'un bataillon spécifique) en quelques clics. Ils peuvent croiser des données financières et démographiques pour répondre à des questions complexes.

*   **Règles de Gestion & Paramétrage :**
    La plateforme intègre un outil de BI (comme Metabase ou Apache Superset, en open source) qui permet aux utilisateurs habilités de créer leurs propres tableaux de bord par "drag-and-drop", sans avoir besoin de connaissances techniques. Les administrateurs peuvent préparer des "modèles de données" certifiés pour garantir que les utilisateurs manipulent des indicateurs corrects et bien définis.

*   **Contrôles, Audit & Conformité :**
    L'accès aux données est sécurisé et conforme aux habilitations de l'utilisateur. Un analyste du service financier ne verra pas les mêmes données qu'un analyste RH. L'outil de BI se connecte à une base de données répliquée et anonymisée pour les données les plus sensibles, garantissant que l'exploration de données ne met jamais en péril la confidentialité des informations personnelles.

*   **Indicateurs de Performance Clés (KPIs) :**
    *   **Nombre d'utilisateurs actifs sur l'outil de BI.**
    *   **Nombre de tableaux de bord personnalisés créés par les utilisateurs.**
    *   **Temps moyen passé sur la plateforme par session d'analyse.**
    *   **Nombre de décisions stratégiques documentées comme ayant été éclairées par l'outil de BI.**

---
Ce document sera mis à jour continuellement durant le projet pour refléter les décisions d'architecture et de conception.

---
