# OFFRE TECHNIQUE STRATÉGIQUE - WAAJAL ËLËK

## Proposition pour la Conception, le Développement et le Déploiement de la Plateforme de Gestion du Régime de Retraite Complémentaire des Armées

**Soumissionnaire :** [Votre Nom/Nom de l'Entreprise]
**Date :** 11 septembre 2025
**Référence :** TDR_plateforme_waajalelek

---

## 1. Résumé Exécutif (Executive Summary)

La présente offre technique détaille notre proposition pour la réalisation de la plateforme **Waajal Ëlëk**. Notre solution n'est pas seulement une réponse aux exigences du TDR, mais une vision stratégique pour doter la Mutuelle des Armées d'un système de gestion de retraite **robuste, pérenne, sécurisé et à la pointe de la technologie**.

Nous avons analysé en profondeur le contexte et les offres concurrentes pour synthétiser une solution qui capitalise sur les meilleures approches :
*   **Fiabilité Actuarielle :** Un moteur de calcul actuariel puissant et transparent, garantissant la justesse des prestations et la viabilité à long terme du régime.
*   **Architecture Technique Moderne :** Une stack technologique éprouvée, combinant performance, sécurité et maintenabilité. Nous avons opté pour **Ruby on Rails 8** pour sa maturité dans le secteur financier et sa productivité, couplé à **React/TypeScript** pour une expérience utilisateur fluide et dynamique.
*   **Couverture Fonctionnelle Exhaustive :** Une décomposition en 20 modules qui couvrent, et dépassent, l'ensemble des spécifications du TDR, garantissant qu'aucun aspect de la gestion du régime ne soit laissé pour compte.
*   **Sécurité "Zero Trust" :** Une approche de la sécurité intégrée à chaque niveau de l'application, du code à l'infrastructure (DevSecOps).

Notre engagement est de livrer un **Produit Minimum Viable (MVP) opérationnel pour le 1er novembre 2025**, et de finaliser l'ensemble des modules avancés pour le **1er janvier 2026**, en respectant scrupuleusement le budget et les délais.

---

## 2. Architecture Technique Détaillée

Notre philosophie est de construire sur des fondations solides. L'architecture proposée est conçue pour la performance, la scalabilité et une sécurité sans compromis.

*   **Backend (Ruby on Rails 8) :**
    *   **Justification :** Ruby on Rails (RoR) est un framework mature, reconnu pour sa productivité et son écosystème robuste. Des plateformes comme GitHub, Shopify et Stripe lui font confiance pour des opérations critiques. Sa convention "Convention over Configuration" assure une base de code propre et maintenable.
    *   **Composants clés :** Nous utiliserons **Solid Queue** pour la gestion asynchrone des tâches (calculs de cotisations, envois de notifications), garantissant une interface utilisateur toujours réactive. L'intégration de la gemme **PaperTrail** offrira un audit log immuable de chaque modification de donnée, répondant à l'exigence de traçabilité totale.

*   **Frontend (React 18 + TypeScript) :**
    *   **Justification :** React est le leader incontesté pour la création d'interfaces utilisateur dynamiques. L'utilisation de **TypeScript** ajoute un typage statique, ce qui réduit drastiquement les erreurs au runtime et facilite la maintenance à long terme, un point crucial pour une application de cette envergure.
    *   **Librairies et Design System :** Nous construirons un **Design System** sur mesure basé sur **Tailwind CSS**, garantissant une cohérence visuelle parfaite et une expérience utilisateur (UX) intuitive, inspirée des meilleures applications bancaires modernes.

*   **Base de Données (PostgreSQL 16) :**
    *   **Justification :** PostgreSQL est réputé pour sa robustesse, son extensibilité et sa conformité aux standards SQL. Ses fonctionnalités avancées comme les transactions ACID, la réplication native et la gestion fine des rôles sont indispensables pour une application financière. Nous mettrons en place une stratégie de **réplication Primaire-Secondaire** pour la haute disponibilité et des sauvegardes journalières automatisées et testées.

*   **Application Mobile (React Native) :**
    *   **Justification :** Pour offrir une expérience mobile optimale, nous développerons une application native pour iOS et Android en utilisant **React Native**. Cela permet de partager une grande partie du code avec l'application web (logique métier, services API) tout en offrant des performances natives et un accès aux fonctionnalités du téléphone (biométrie, notifications push).
    *   **Mode Hors-Ligne :** L'application intégrera une base de données locale (WatermelonDB) pour permettre la consultation et la saisie de certaines données en mode déconnecté, avec une synchronisation intelligente et automatique dès le retour de la connexion.

*   **Infrastructure & DevOps (Cloud Souverain + Kubernetes) :**
    *   **Hébergement :** Déploiement sur une infrastructure de **Cloud Souverain** pour garantir la confidentialité et la souveraineté des données.
    *   **Orchestration :** L'application sera entièrement conteneurisée avec **Docker** et orchestrée par **Kubernetes (K8s)**. K8s nous permettra d'assurer une haute disponibilité (auto-healing), une scalabilité horizontale automatique en cas de pic de charge, et des déploiements "zero-downtime".
    *   **CI/CD & Monitoring :** Nous mettrons en place une pipeline d'intégration et de déploiement continus (CI/CD) avec **GitLab CI**. Le monitoring sera assuré par **Prometheus** et **Grafana** pour la performance, et une stack **ELK (Elasticsearch, Logstash, Kibana)** pour la centralisation et l'analyse des logs.

---

## 3. Fonctionnalités Détaillées

Notre proposition couvre 20 modules fonctionnels, conçus pour adresser chaque exigence du TDR avec une précision et une profondeur technique maximales.

**Le détail complet de chaque fonctionnalité, incluant les processus métier et les notes d'implémentation technique, est disponible dans le document annexe : `fonctionnalite.md`.**

Ce document a été spécifiquement enrichi pour servir de référence technique tout au long du projet. Il détaille, par exemple, comment les appels aux API de paiement mobile money seront sécurisés, comment le moteur actuariel effectuera les simulations Monte Carlo, ou encore comment le journal d'audit garantira son intégrité.

---

## 4. Planning de Livraison Accéléré

Notre planning est à la fois ambitieux et réaliste, conçu pour mettre la plateforme entre les mains des utilisateurs le plus rapidement possible tout en maîtrisant les risques.

*   **Phase 1 : MVP Opérationnel (Livraison le 1er novembre 2025)**
    *   **Objectif :** Permettre l'enrôlement et la gestion des cotisations dès la date cible.
    *   **Modules :** Gestion du Personnel, Adhésions, Cotisations, Paiements, Portail Adhérent (consultation), Administration & Sécurité.

*   **Phase 2 : Prestations & Comptabilité (Livraison le 1er décembre 2025)**
    *   **Objectif :** Activer la gestion complète des prestations de retraite.
    *   **Modules :** Gestion des Pensions, Gestion des Retraités, Démissions & Rachats, Comptabilité & Comptes, Rapports & Analyses.

*   **Phase 3 : Modules Experts & Mobilité (Livraison le 1er janvier 2026)**
    *   **Objectif :** Doter la plateforme de ses capacités d'analyse et d'une expérience mobile complète.
    *   **Modules :** Simulateur Actuariel, Avances sur Capital, Gestion des Investissements, Application Mobile (iOS/Android), Centre d'Aide.

---

## 5. Conclusion

Choisir notre solution, c'est investir dans un partenariat stratégique pour l'avenir de la Mutuelle des Armées. Nous apportons non seulement une réponse complète au TDR, mais aussi une expertise technique approfondie, une méthodologie de projet éprouvée et un engagement total pour la réussite de **Waajal Ëlëk**.

Nous sommes convaincus que notre proposition représente la meilleure synthèse de technologie, d'expertise métier et de vision à long terme.

---
