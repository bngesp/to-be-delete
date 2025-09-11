# Architecture Technique de Référence - Plateforme Waajal Ëlëk

## 1. Vision et Principes Directeurs

Pour répondre aux exigences de performance, de sécurité et d'évolutivité du projet Waajal Ëlëk, nous avons opté pour une **architecture microservices native au cloud (Cloud-Native)**. Ce choix n'est pas une simple tendance technologique ; il est motivé par la nécessité de construire un système qui puisse évoluer indépendamment, module par module, sans jamais compromettre la stabilité de l'ensemble.

Nos principes directeurs sont :
*   **Haute Cohésion, Faible Couplage :** Chaque microservice aura une responsabilité métier unique et bien définie. Ils communiqueront via des contrats d'API clairs, mais leurs logiques internes et leurs cycles de vie resteront indépendants.
*   **Résilience et Tolérance aux Pannes :** L'architecture est conçue pour qu'une défaillance sur un service non critique (ex: le service de reporting) n'entraîne jamais une interruption des services essentiels (ex: la collecte des cotisations).
*   **Scalabilité Horizontale :** Chaque service pourra être dupliqué (scalé) indépendamment des autres pour répondre à une charge spécifique, optimisant ainsi l'utilisation des ressources.
*   **Autonomie des Équipes :** Cette architecture permettra à terme à des équipes dédiées de travailler sur des périmètres fonctionnels distincts, accélérant ainsi les développements futurs.

## 2. Vue d'Ensemble de l'Architecture

L'écosystème s'articulera autour des composants centraux suivants, qui forment l'épine dorsale de notre plateforme :

*   **Clients :** Une application web monopage (SPA) développée en **React/TypeScript** et une application mobile native pour iOS/Android en **React Native**.
*   **API Gateway (Spring Cloud Gateway) :** Le point d'entrée unique et sécurisé pour toutes les requêtes externes. Il se chargera du routage vers les services appropriés, de l'authentification, de la limitation de débit (rate limiting) et de l'agrégation de certaines réponses.
*   **Service Registry (Eureka) :** Un annuaire dynamique où chaque instance de microservice s'enregistre à son démarrage. Cela permet aux services de se découvrir mutuellement sans avoir à connaître leurs adresses IP.
*   **Configuration Server (Spring Cloud Config) :** Un serveur centralisé pour gérer la configuration de tous les microservices (paramètres de base de données, clés d'API, etc.), permettant de modifier des configurations à chaud sans redéploiement.
*   **Communication Asynchrone (RabbitMQ) :** Un message broker sera utilisé pour la communication événementielle entre les services. Lorsqu'une action métier importante se produit (ex: une adhésion est validée), le service concerné publiera un événement. Les autres services intéressés par cet événement pourront y souscrire, garantissant un découplage total.
*   **Observability Stack (ELK + Prometheus + Grafana + Zipkin) :** Une suite d'outils intégrés pour garantir une traçabilité et une supervision sans faille.

## 3. Description des Microservices

Chaque service est un projet Spring Boot 3 (utilisant Java 17) autonome, avec sa propre base de données (principe "Database per Service").

1.  **Service `user-service` (Personnel & Accès) :**
    *   **Responsabilités :** Gère le référentiel des militaires (dossiers, carrière), l'authentification (via Keycloak), les rôles et les permissions. C'est le garant de l'identité.
    *   **Base de données :** PostgreSQL.
    *   **Exemple d'API :** `GET /api/users/{matricule}`

2.  **Service `membership-service` (Adhésions) :**
    *   **Responsabilités :** Gère le cycle de vie des adhésions et des contrats. Publie des événements comme `Membership.Created` ou `Membership.Terminated`.
    *   **Base de données :** PostgreSQL.
    *   **Exemple d'API :** `POST /api/memberships`

3.  **Service `contribution-service` (Cotisations) :**
    *   **Responsabilités :** Calcule les cotisations, gère les échéanciers, traite les paiements via l'intégration avec les plateformes de Mobile Money et convertit les cotisations en points.
    *   **Base de données :** PostgreSQL.
    *   **Exemple d'API :** `POST /api/contributions/payments/webhook`

4.  **Service `pension-service` (Prestations) :**
    *   **Responsabilités :** Gère la liquidation des droits, les demandes de rachat et d'avance, et la génération des ordres de paiement des pensions.
    *   **Base de données :** PostgreSQL.
    *   **Exemple d'API :** `POST /api/pensions/liquidate`

5.  **Service `actuarial-engine-service` (Moteur Actuariel) :**
    *   **Responsabilités :** Fournit des endpoints pour les calculs complexes : projections, simulations Monte Carlo, calculs de rentes viagères. Il expose des API internes consommées par les autres services.
    *   **Base de données :** Pas de base de données propre, il est purement calculatoire.
    *   **Exemple d'API (interne) :** `POST /api/internal/actuarial/project-pension`

6.  **Service `accounting-service` (Comptabilité) :**
    *   **Responsabilités :** Tient le grand livre comptable de toutes les opérations financières en partie double. Il souscrit aux événements financiers publiés par les autres services (cotisations, pensions, etc.) pour garantir une cohérence comptable.
    *   **Base de données :** PostgreSQL.
    *   **Exemple d'API :** `GET /api/accounting/journal`

7.  **Service `notification-service` (Notifications) :**
    *   **Responsabilités :** Centralise l'envoi de tous les emails, SMS et notifications push. Il expose une API simple (`POST /api/notifications/send`) et souscrit à divers événements métier.
    *   **Base de données :** Pas de base de données principale, mais un cache Redis pour la gestion des templates.

8.  **Service `document-service` (Gestion Documentaire) :**
    *   **Responsabilités :** Gère le stockage, le chiffrement et la récupération sécurisée des documents.
    *   **Base de données :** MongoDB (GridFS), optimisé pour le stockage de fichiers et de métadonnées.

## 4. Résilience, Disponibilité et Traçabilité

*   **Résilience :** Nous utiliserons la librairie **Resilience4j** dans chaque service. Les appels synchrones entre services seront systématiquement encapsulés dans un **Circuit Breaker**. En cas de défaillance d'un service distant, le disjoncteur s'ouvrira et une réponse par défaut (fallback) sera fournie, évitant ainsi les défaillances en cascade.

*   **Haute Disponibilité :** L'ensemble de l'infrastructure sera déployé sur Kubernetes. Chaque microservice tournera avec un minimum de **3 répliques** réparties sur des nœuds physiques différents. Kubernetes, couplé au Service Registry, assurera la répartition de charge (load balancing) et le redémarrage automatique des instances défaillantes. La disponibilité de la base de données sera assurée par une configuration en cluster avec basculement automatique (failover).

*   **Traçabilité (Observability) :**
    *   **Logs :** Chaque service produira des logs structurés (JSON) qui seront collectés par **Fluentd**, puis envoyés vers **Elasticsearch** pour indexation et analyse via **Kibana** (Stack EFK).
    *   **Métriques :** Chaque service exposera des métriques détaillées (temps de réponse, utilisation mémoire, etc.) via **Spring Boot Actuator**. Ces métriques seront collectées par **Prometheus** et visualisées dans **Grafana**.
    *   **Tracing Distribué :** Pour suivre une requête à travers plusieurs microservices, nous utiliserons **Micrometer Tracing** avec **Zipkin**. L'API Gateway générera un `traceId` unique pour chaque requête entrante, qui sera propagé à tous les services en aval, permettant de reconstituer le parcours complet d'une opération.

---
