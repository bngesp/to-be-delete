# ANNEXE : DESCRIPTION DES PROCESSUS MÉTIER ET FONCTIONNELS

## Introduction

Ce document détaille l'ensemble des processus métier couverts par la plateforme Waajal Ëlëk. Chaque module est décrit du point de vue de sa finalité pour la Mutuelle, des règles de gestion qu'il applique, et des mécanismes de contrôle qu'il intègre. L'objectif est de fournir une vision claire et exhaustive de la richesse fonctionnelle de la solution et de sa parfaite adéquation avec les exigences de la gestion d'un régime de retraite par capitalisation.

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

### **Module 2 : Adhésions et Contrats**

*   **Finalité Stratégique :**
    Ce module formalise la relation contractuelle entre le militaire et la Mutuelle. Il matérialise l'entrée de l'adhérent dans le régime et garantit que les conditions de son adhésion (taux de cotisation, options choisies) sont clairement définies et archivées. Une gestion rigoureuse des contrats est la clé de la sécurité juridique du régime et de la confiance des adhérents.

*   **Processus Métier & Parcours Utilisateur :**
    Lorsqu'un militaire souhaite adhérer, un gestionnaire initie une "demande d'enrôlement" dans le système. Cette demande passe par un workflow de validation : elle est d'abord instruite (vérification de l'éligibilité et des pièces), puis soumise à approbation. Une fois la demande approuvée, le système génère automatiquement le contrat d'adhésion et le bulletin d'adhésion correspondant au format PDF, qui est archivé dans le dossier du membre. Le statut de l'adhérent passe alors à "Actif", déclenchant son entrée dans le processus de cotisation.

*   **Règles de Gestion & Paramétrage :**
    Le système gère plusieurs types de contrats (ex: adhésion de base obligatoire, adhésion volontaire complémentaire). Les paramètres clés de chaque contrat, comme le taux de cotisation salariale ou les plafonds, sont configurables. Le workflow de validation est également paramétrable pour s'adapter à l'organisation de la Mutuelle (ex: validation à un ou deux niveaux). Le système gère également le cycle de vie du contrat : suspension (en cas de congé sans solde par exemple), réactivation et résiliation, chaque changement de statut étant soumis à des règles de gestion strictes.

*   **Contrôles, Audit & Conformité :**
    Chaque étape du workflow de validation est horodatée et tracée. Le bulletin d'adhésion généré constitue une preuve juridique de l'accord de l'adhérent. Le système garantit qu'un militaire ne peut avoir qu'un seul contrat actif à un instant T pour un même régime, évitant ainsi les doublons. Toute modification ultérieure du contrat (un avenant) fait l'objet d'un nouveau processus de validation et d'archivage, préservant l'historique complet de la relation contractuelle.

---
## **PÔLE 2 : GESTION FINANCIÈRE ET PRESTATIONS**
---

### **Module 3 : Gestion des Cotisations**

*   **Finalité Stratégique :**
    Assurer la collecte régulière et exhaustive des cotisations, qui constituent le flux financier principal alimentant les réserves du régime. La performance et la rigueur de ce module sont directement liées à la capacité du régime à générer des produits financiers et, à terme, à honorer ses engagements envers les retraités.

*   **Processus Métier & Parcours Utilisateur :**
    Au début de chaque période (généralement mensuelle), le système identifie tous les adhérents actifs et calcule automatiquement le montant de la cotisation due pour chacun, en appliquant le taux de son contrat à son assiette de rémunération. Un "appel de cotisations" global est alors généré. Au fur et à mesure de la réception des paiements (via prélèvement sur la paie ou paiement direct), les gestionnaires effectuent le lettrage des cotisations. L'interface de suivi offre une vue en temps réel du taux de recouvrement et met en évidence les cotisations en attente ou en retard.

*   **Règles de Gestion & Paramétrage :**
    La complexité de ce module réside dans la finesse de ses règles de calcul. Le système permet de paramétrer précisément le calcul de l'assiette (quels éléments de la rémunération sont inclus), les règles de proratisation pour les mois d'entrée ou de sortie, et les conditions de suspension des prélèvements. Les règles de gestion des retards (délai de grâce, calcul des pénalités) sont également entièrement configurables pour s'adapter à la politique de la Mutuelle.

*   **Contrôles, Audit & Conformité :**
    Un contrôle de cohérence est effectué avant chaque appel de cotisations pour s'assurer que tous les adhérents actifs ont un contrat valide et une assiette de rémunération renseignée. Chaque paiement est tracé et rapproché d'une cotisation due. Le système génère des journaux de cotisations détaillés qui servent de base aux écritures comptables et permettent un audit complet des flux entrants. Des alertes automatiques peuvent être configurées pour notifier les gestionnaires en cas de retard de paiement significatif.

### **Module 4 : Conversion en Points**

*   **Finalité Stratégique :**
    Traduire l'effort financier de l'adhérent en une unité de compte de retraite : le point. Ce mécanisme est le cœur du régime par points. La transparence et l'intégrité de ce module sont essentielles, car il matérialise l'accumulation des droits futurs de l'adhérent.

*   **Processus Métier & Parcours Utilisateur :**
    Ce processus est entièrement automatisé et se déclenche dès qu'une cotisation est marquée comme "payée". Le système récupère le montant versé et le divise par la "valeur d'achat du point" en vigueur à la date du paiement pour déterminer le nombre de points à créditer au compte de l'adhérent. L'adhérent peut consulter sur son portail personnel le détail de chaque acquisition de points, lui permettant de suivre en toute transparence la constitution de son futur capital retraite.

*   **Règles de Gestion & Paramétrage :**
    La "valeur d'achat du point" est le paramètre central de ce module. Elle est fixée par les instances de gouvernance de la Mutuelle et peut évoluer dans le temps. Le système historise chaque changement de cette valeur pour garantir que les calculs utilisent toujours la valeur correcte en fonction de la date de la transaction. Le module permet également aux administrateurs d'effectuer des attributions de points exceptionnelles (points gratuits, bonifications pour ancienneté, etc.), soumises à un processus de validation spécifique.

*   **Contrôles, Audit & Conformité :**
    Chaque opération d'acquisition de points est une transaction indivisible et tracée. Le système garantit qu'une même cotisation ne peut être convertie en points qu'une seule fois. Un rapport de rapprochement "Cotisations / Points" peut être généré à tout moment pour vérifier que le total des points attribués correspond bien au total des cotisations encaissées, divisé par la valeur du point. Ceci constitue un contrôle fondamental de la cohérence du régime.

*(... et ainsi de suite pour les 23 modules, en appliquant ce même niveau de détail métier à chaque description)*

---
