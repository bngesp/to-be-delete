# ANNEXE TECHNIQUE : SPÉCIFICATIONS FONCTIONNELLES DÉTAILLÉES

## Introduction

Ce document fournit une description exhaustive des 20 modules qui composent la plateforme **Waajal Ëlëk**. Chaque module est présenté avec ses fonctionnalités métier et des **notes d'implémentation technique** pour garantir une transparence totale sur l'architecture et les choix de développement. Cette approche a pour but de servir de fondation solide pour les équipes de développement et d'assurer un alignement parfait avec les besoins de la Mutuelle des Armées.

---

## PHASE 1 : FONDATIONS ET ENRÔLEMENT (Livraison : 1er novembre 2025)

### Module 1 : Gestion du Personnel Militaire

*   **Objectif :** Constituer le référentiel central et unique pour toutes les données personnelles, administratives et de carrière des militaires.

*   **Fonctionnalités :**
    *   Gestion complète des dossiers : état civil, contacts, situation familiale, informations bancaires (RIB).
    *   Profil militaire détaillé : matricule, grade, échelon, corps, unité, date d'incorporation, limite d'âge.
    *   Historique de carrière : suivi des promotions, affectations, formations et décorations.
    *   Gestion de la rémunération de référence servant de base au calcul des cotisations.
    *   Import massif et synchronisation depuis des fichiers Excel/CSV ou via une future API du système de paie.
    *   Moteur de recherche multicritères (nom, matricule, unité, etc.).
    *   Gestion documentaire sécurisée associée à chaque profil (ex: CNI, attestations).

*   **Notes d'implémentation technique :**
    *   **Modèles de données :**
        *   `MilitaryPersonnel(id, first_name, last_name, matricule, birth_date, rank, unit, base_salary, status, ...)`
        *   `CareerHistory(id, personnel_id, event_type, event_date, description)`
        *   `PersonnelDocument(id, personnel_id, document_type, file_path, encrypted_dek)`
    *   **API Endpoints :**
        *   `GET /api/v1/military_personnel` : Liste paginée du personnel.
        *   `POST /api/v1/military_personnel/import` : Endpoint pour l'import de fichiers CSV/Excel, traité par un background job.
        *   `GET /api/v1/military_personnel/{id}` : Détails complets d'un militaire.
    *   **Sécurité :** Les documents personnels seront chiffrés au repos (AES-256). L'accès aux données sera régi par une politique de contrôle d'accès basée sur les rôles (RBAC).

### Module 2 : Adhésions et Contrats

*   **Objectif :** Gérer l'ensemble du cycle de vie de l'adhésion d'un militaire au régime de retraite.

*   **Fonctionnalités :**
    *   Processus d'enrôlement en ligne avec workflow de validation (Saisie → Vérification → Approbation → Activation).
    *   Création automatique du contrat d'adhésion à partir d'un enrôlement validé.
    *   Gestion des différents statuts d'adhésion : `Actif`, `Suspendu`, `Résilié`, `En attente`.
    *   Paramétrage des contrats : taux de cotisation (salariale, patronale), plafonds, options spécifiques.
    *   Génération et archivage des bulletins d'adhésion au format PDF.

*   **Notes d'implémentation technique :**
    *   **Modèles de données :**
        *   `Membership(id, personnel_id, contract_type, status, effective_date)`
        *   `Contract(id, membership_id, contribution_rate, ceiling, ...)`
    *   **Processus Asynchrones :** Un `State Machine` (ex: gemme AASM) sera utilisé pour gérer les transitions de statut de l'adhésion, garantissant l'intégrité du processus et déclenchant des notifications.
    *   **API Endpoints :**
        *   `POST /api/v1/enrollments` : Soumission d'une nouvelle demande d'enrôlement.
        *   `POST /api/v1/memberships/{id}/approve` : Endpoint sécurisé pour l'approbation par un gestionnaire.

### Module 3 : Cotisations et Points

*   **Objectif :** Assurer le calcul, la collecte et la conversion des cotisations en points de retraite.

*   **Fonctionnalités :**
    *   Calcul automatique des cotisations mensuelles basé sur la rémunération de référence et le taux défini au contrat.
    *   Gestion des échéanciers de paiement avec suivi des statuts (`Payé`, `En retard`, `En attente`).
    *   Conversion automatique des cotisations versées en points, selon la valeur d'achat du point en vigueur.
    *   Gestion des points gratuits et bonifications (attribués par les administrateurs).
    *   Historique complet et transparent de toutes les transactions de cotisations et d'acquisition de points pour chaque adhérent.

*   **Notes d'implémentation technique :**
    *   **Processus Asynchrones :** Un job récurrent (via Solid Queue) s'exécutera en début de mois pour calculer et générer toutes les cotisations dues.
    *   **Modèles de données :**
        *   `Contribution(id, membership_id, amount_due, amount_paid, status, due_date, payment_date)`
        *   `PointTransaction(id, membership_id, points_acquired, value_per_point, transaction_date, source_contribution_id)`
    *   **Calculs :** La logique de calcul sera isolée dans des `Service Objects` Ruby dédiés, facilitant les tests unitaires et la maintenance. La valeur d'achat du point sera stockée dans une table `SystemParameter` pour être modifiable sans déploiement.

### Module 4 : Intégration des Paiements

*   **Objectif :** Offrir des moyens de paiement modernes et sécurisés pour les cotisations et les prestations.

*   **Fonctionnalités :**
    *   Intégration avec les API de Mobile Money (Wave, Orange Money, Free Money).
    *   Paiement par virement bancaire avec génération de références uniques pour le rapprochement.
    *   Réconciliation automatique des transactions.
    *   Journal d'audit de toutes les transactions financières.

*   **Notes d'implémentation technique :**
    *   **API & Webhooks :** L'interaction avec les plateformes de paiement se fera via des appels API sécurisés. Nous implémenterons des endpoints de `webhooks` pour recevoir les confirmations de paiement de manière asynchrone, garantissant qu'une interruption de service momentanée ne cause pas de perte de données.
    *   **Sécurité :** Toutes les clés d'API et secrets seront stockés de manière chiffrée via le système de `credentials` de Rails. Aucune information sensible ne sera versionnée dans le code.

### Module 5 : Portail Adhérent (Consultation)

*   **Objectif :** Fournir aux adhérents un accès sécurisé à leurs informations de retraite.

*   **Fonctionnalités :**
    *   Tableau de bord personnel : solde de points, total des cotisations, valeur estimée du capital.
    *   Consultation de l'historique des cotisations et des points acquis.
    *   Téléchargement des documents personnels (bulletin d'adhésion, relevés annuels).
    *   Interface 100% responsive (mobile-first).

*   **Notes d'implémentation technique :**
    *   **Frontend :** Développé en React/TypeScript, le portail communiquera avec le backend via une API RESTful sécurisée par token (JWT).
    *   **Performance :** Les données agrégées du tableau de bord (total de points, etc.) seront mises en cache (côté serveur avec Redis) pour un affichage quasi-instantané.

### Module 6 : Administration & Sécurité

*   **Objectif :** Permettre aux administrateurs de gérer les utilisateurs, les droits et de superviser la sécurité de la plateforme.

*   **Fonctionnalités :**
    *   Gestion des utilisateurs (administrateurs, gestionnaires).
    *   Gestion des rôles et permissions granulaires (RBAC).
    *   Journal d'audit complet de toutes les actions effectuées sur la plateforme.
    *   Paramétrage global du système (valeur du point, taux, etc.).

*   **Notes d'implémentation technique :**
    *   **Modèles de données :**
        *   `User(id, email, encrypted_password, role_id)`
        *   `Role(id, name)`
        *   `Permission(id, action, subject_class)`
    *   **Sécurité :** L'authentification multi-facteurs (2FA) via TOTP (ex: Google Authenticator) sera obligatoire pour tous les comptes administrateurs. La gemme `Pundit` sera utilisée pour gérer les autorisations de manière centralisée et testable.

---

## PHASE 2 : GESTION DES PRESTATIONS (Livraison : 1er décembre 2025)

### Module 7 : Gestion des Pensions de Retraite

*   **Objectif :** Gérer la liquidation des droits à la retraite et le versement des pensions.

*   **Fonctionnalités :**
    *   Calcul des droits à la liquidation basé sur le total des points acquis multiplié par la valeur de service du point.
    *   Gestion des différentes options de sortie : rente viagère, capital unique, ou une combinaison des deux.
    *   Gestion des bénéficiaires et des taux de réversion.
    *   Génération des ordres de paiement mensuels pour les rentes.

*   **Notes d'implémentation technique :**
    *   **Moteur de calcul :** La logique de liquidation sera encapsulée dans un service dédié. Les calculs de rente viagère utiliseront des tables de mortalité réglementaires qui seront importées et stockées dans la base de données.
    *   **Processus Asynchrones :** La génération mensuelle des ordres de paiement de pension sera effectuée par un background job.

### Module 8 : Gestion des Retraités

*   **Objectif :** Assurer le suivi des militaires une fois leur statut passé à "Retraité".

*   **Fonctionnalités :**
    *   Transition automatique du statut "Actif" à "Retraité" à la date de liquidation.
    *   Historique complet des versements de pension.
    *   Gestion des certificats de vie avec rappels automatiques.

*   **Notes d'implémentation technique :**
    *   **Modèles de données :** Le modèle `MilitaryPersonnel` aura un statut qui passera à `retired`. Un nouveau modèle `PensionPayment(id, retiree_id, amount, payment_date, status)` suivra les versements.

### Module 9 : Démissions & Rachats

*   **Objectif :** Gérer les cas de sortie anticipée du régime.

*   **Fonctionnalités :**
    *   Gestion des demandes de rachat partiel ou total.
    *   Calcul automatique des montants rachetables en fonction des conditions (ancienneté, pénalités, etc.).
    *   Workflow de validation pour les demandes de rachat.

*   **Notes d'implémentation technique :**
    *   **API Endpoints :** `POST /api/v1/redemptions` pour initier une demande, qui sera ensuite traitée via un workflow de validation interne.

### Module 10 : Comptabilité & Comptes

*   **Objectif :** Assurer un suivi financier et comptable rigoureux de toutes les opérations.

*   **Fonctionnalités :**
    *   Enregistrement automatique de tous les flux financiers (cotisations, pensions, rachats, investissements).
    *   Plan comptable adapté au régime.
    *   Rapprochement bancaire facilité par l'import de relevés.
    *   Génération de journaux comptables.

*   **Notes d'implémentation technique :**
    *   **Double entrée :** Nous implémenterons un système de comptabilité en partie double à l'aide de la gemme `DoubleEntry` pour garantir l'intégrité des écritures comptables.
    *   **Modèles de données :** `Account(id, name, type)`, `JournalEntry(id, date, description)`, `Transaction(id, journal_entry_id, account_id, direction, amount)`.

### Module 11 : Rapports & Analyses

*   **Objectif :** Fournir des outils de pilotage stratégique à la direction de la Mutuelle.

*   **Fonctionnalités :**
    *   Tableaux de bord avec les indicateurs clés (KPIs) en temps réel : ratio actifs/retraités, taux de couverture, etc.
    *   Génération de rapports réglementaires et d'activité (PDF, Excel).
    *   Outils d'analyse ad-hoc pour explorer les données.

*   **Notes d'implémentation technique :**
    *   **Data Warehousing :** Pour les analyses complexes, les données opérationnelles de PostgreSQL seront répliquées vers une base de données optimisée pour l'analytique (Data Warehouse), afin de ne pas impacter les performances de l'application principale.

---

## PHASE 3 : MODULES EXPERTS & MOBILITÉ (Livraison : 1er janvier 2026)

### Module 12 : Simulateur Actuariel Global

*   **Objectif :** Doter la Mutuelle d'un outil puissant pour les projections à long terme et l'analyse de risques.

*   **Fonctionnalités :**
    *   Projections actuarielles de l'équilibre du régime sur 10, 20, 30 ans.
    *   Simulations de type "stress test" (ex: impact d'une crise économique, d'un changement démographique).
    *   Analyses de sensibilité et simulations Monte Carlo.

*   **Notes d'implémentation technique :**
    *   **Moteur Python :** Ce module sera développé en **Python** avec des librairies comme **Pandas, NumPy, et SciPy**, et communiquera avec l'application Rails via une API interne. Ce choix technologique donne accès à l'écosystème le plus mature pour l'analyse de données et la modélisation actuarielle.

### Module 13 : Avances sur Capital

*   **Objectif :** Permettre aux adhérents de demander une avance sur leur capital retraite.

*   **Fonctionnalités :**
    *   Demande en ligne avec vérification automatique de l'éligibilité.
    *   Simulation de l'impact de l'avance sur la pension future.
    *   Gestion de l'échéancier de remboursement.

### Module 14 : Gestion des Investissements

*   **Objectif :** Suivre les performances du portefeuille d'investissements du régime.

*   **Fonctionnalités :**
    *   Gestion du portefeuille multi-classes d'actifs.
    *   Suivi des performances (gains/pertes, rendement).
    *   Reporting consolidé du portefeuille.

### Module 15 : Intérêts & Rendements

*   **Objectif :** Calculer et attribuer les rendements financiers aux comptes des adhérents.

*   **Fonctionnalités :**
    *   Calcul périodique des rendements générés par les investissements.
    *   Répartition des gains au prorata des points de chaque adhérent.

### Module 16 : Gestion des Assurances

*   **Objectif :** Intégrer la gestion de produits d'assurance complémentaires.

*   **Fonctionnalités :**
    *   Gestion des contrats d'assurance (décès, invalidité).
    *   Suivi des primes et gestion des sinistres.

### Module 17 : Centre d'Aide

*   **Objectif :** Fournir une documentation et un support intégrés.

*   **Fonctionnalités :**
    *   Base de connaissances avec moteur de recherche.
    *   FAQ dynamique.
    *   Système de ticketing pour les demandes de support.

### Module 18 : Simulations Personnalisées (Portail Adhérent)

*   **Objectif :** Permettre aux adhérents de simuler leur propre avenir à la retraite.

*   **Fonctionnalités :**
    *   Simulation de la pension future en fonction de divers scénarios (départ anticipé, augmentation des cotisations, etc.).
    *   Visualisations graphiques des projections.

### Module 19 : Application Mobile Complète (iOS/Android)

*   **Objectif :** Offrir une expérience mobile riche et transactionnelle.

*   **Fonctionnalités :**
    *   Toutes les fonctionnalités du portail adhérent.
    *   Paiement des cotisations via Mobile Money directement depuis l'application.
    *   Demandes de rachat ou d'avance.
    *   Notifications push pour les échéances et les événements importants.
    *   Accès sécurisé par biométrie (empreinte digitale, reconnaissance faciale).

### Module 20 : Moteur de Calcul Actuariel Avancé

*   **Objectif :** Raffiner les calculs actuariels avec des hypothèses multiples.

*   **Fonctionnalités :**
    *   Intégration d'hypothèses multiples (optimiste, réaliste, pessimiste) dans les calculs.
    *   API interne pour que les autres modules (Simulations, Pensions) puissent consommer ces calculs complexes.

---

Ce document sera mis à jour continuellement durant le projet pour refléter les décisions d'architecture et de conception.

---
