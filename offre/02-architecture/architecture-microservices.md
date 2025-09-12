# Architecture Microservices Cloud-Native

## Une Architecture de Nouvelle Génération pour la Gestion de Retraite Moderne

L'architecture de la plateforme Waajal Ëlëk constitue le fondement technologique sur lequel repose l'ensemble de notre proposition de valeur. Notre choix d'une architecture microservices cloud-native répond aux exigences spécifiques d'un système de gestion de retraite moderne : scalabilité, résilience, sécurité, évolutivité et performance conformément aux spécifications du TDR.

Cette architecture représente un investissement dans l'avenir technologique de la Mutuelle des Armées. Elle garantit que la plateforme pourra évoluer et s'adapter aux changements réglementaires, aux évolutions démographiques et aux innovations technologiques des deux prochaines décennies, tout en maintenant un niveau de service exemplaire.

## Vue d'Ensemble Architecturale - Diagramme ASCII

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           WAAJAL ËLËK ECOSYSTEM                            │
│                        Architecture Microservices                           │
└─────────────────────────────────────────────────────────────────────────────┘

                         ┌─────────────────────────┐
                         │      LOAD BALANCER      │
                         │     (HAProxy/NGINX)     │
                         │   SSL Termination TLS   │
                         └───────────┬─────────────┘
                                     │
                         ┌───────────▼─────────────┐
                         │     API GATEWAY         │
                         │   (Spring Cloud GW)     │
                         │ Rate Limiting/Routing   │
                         └───────────┬─────────────┘
                                     │
        ┌────────────────────────────┼────────────────────────────┐
        │                            │                            │
        ▼                            ▼                            ▼
┌──────────────┐            ┌──────────────┐            ┌──────────────┐
│ FRONTEND     │            │   MOBILE     │            │  ADMIN       │
│ WEB CLIENT   │            │   CLIENTS    │            │  PORTAL      │
│ (React 18)   │            │ iOS/Android  │            │ (React 18)   │
└──────────────┘            └──────────────┘            └──────────────┘

═══════════════════════════════════════════════════════════════════════════════
                            SECURITY LAYER
═══════════════════════════════════════════════════════════════════════════════

            ┌─────────────────────┐    ┌─────────────────────┐
            │    KEYCLOAK         │    │   VAULT SECRETS     │
            │  Identity Provider  │    │   Management       │
            │  OAuth2/OIDC       │    │   AES-256 Keys     │
            └─────────────────────┘    └─────────────────────┘

═══════════════════════════════════════════════════════════════════════════════
                         MICROSERVICES LAYER
═══════════════════════════════════════════════════════════════════════════════

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ USER-MANAGEMENT │ │ PERSONNEL-SVC   │ │ ADHESION-SVC    │ │ COTISATION-SVC  │
│                 │ │                 │ │                 │ │                 │
│ • Authentication│ │ • Military Data │ │ • Registration  │ │ • Contribution  │
│ • Authorization │ │ • Career Track  │ │ • Simulation    │ │ • Calculation   │
│ • Session Mgmt  │ │ • Hierarchy     │ │ • Validation    │ │ • Collection    │
│ • RBAC Rules    │ │ • Promotions    │ │ • Document Gen  │ │ • Reconciliation│
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ POINTS-SVC      │ │ ACCOUNT-SVC     │ │ PENSION-SVC     │ │ FINANCIAL-SVC   │
│                 │ │                 │ │                 │ │                 │
│ • Conversion    │ │ • Individual    │ │ • Calculation   │ │ • Investment    │
│ • Point Value   │ │ • Account       │ │ • Liquidation   │ │ • Portfolio Mgmt│
│ • History       │ │ • Balance       │ │ • Payout        │ │ • Performance   │
│ • Attestations  │ │ • Transactions  │ │ • Options       │ │ • Asset Alloc   │
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ ACCOUNTING-SVC  │ │ ACTUARIAL-SVC   │ │ SIMULATION-SVC  │ │ AI-FRAUD-SVC    │
│                 │ │                 │ │                 │ │                 │
│ • OHADA Rules   │ │ • Calculations  │ │ • Monte Carlo   │ │ • ML Detection  │
│ • General Ledger│ │ • Provisions    │ │ • Projections   │ │ • Behavioral    │
│ • Financial Rep │ │ • Mortality Tbl │ │ • Scenarios     │ │ • Anomaly Det   │
│ • Audit Trail   │ │ • Stress Tests  │ │ • Risk Models   │ │ • Alert System │
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ ROBO-ADVISOR    │ │ BUSINESS-INTEL  │ │ NOTIFICATION    │ │ INTEGRATION     │
│                 │ │                 │ │                 │ │                 │
│ • ML Recommend  │ │ • Analytics     │ │ • Multi-channel │ │ • Mobile Money  │
│ • Portfolio Opt │ │ • Dashboards    │ │ • Push/SMS/Mail │ │ • External APIs │
│ • Risk Profiling│ │ • Predictive    │ │ • Personalized  │ │ • ERP Systems   │
│ • Personalizatn │ │ • Real-time KPI │ │ • Intelligent   │ │ • Data Sync     │
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘

═══════════════════════════════════════════════════════════════════════════════
                          MESSAGING LAYER
═══════════════════════════════════════════════════════════════════════════════

            ┌─────────────────────────────────────────────────────┐
            │                  RABBITMQ CLUSTER                  │
            │                                                     │
            │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  │
            │  │   Exchange  │  │   Exchange  │  │   Exchange  │  │
            │  │   Direct    │  │   Topic     │  │   Fanout    │  │
            │  └─────────────┘  └─────────────┘  └─────────────┘  │
            │                                                     │
            │  Queues: user.events, payment.events, audit.logs   │
            │  Dead Letter Queues, Message Persistence, HA       │
            └─────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════════════════════════
                           DATA LAYER
═══════════════════════════════════════════════════════════════════════════════

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ POSTGRESQL      │ │ POSTGRESQL      │ │ POSTGRESQL      │ │ REDIS CLUSTER   │
│ USER-DB         │ │ FINANCIAL-DB    │ │ AUDIT-DB        │ │                 │
│                 │ │                 │ │                 │ │ • Session Store │
│ • Users/Roles   │ │ • Transactions  │ │ • Audit Logs    │ │ • Cache Layer   │
│ • Permissions   │ │ • Accounts      │ │ • Security Evts │ │ • Temp Data     │
│ • Sessions      │ │ • Investments   │ │ • Compliance    │ │ • Pub/Sub       │
│ • Master/Slave  │ │ • Master/Slave  │ │ • Write-Only    │ │ • High Perf     │
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘

═══════════════════════════════════════════════════════════════════════════════
                        OBSERVABILITY LAYER
═══════════════════════════════════════════════════════════════════════════════

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ ELASTICSEARCH   │ │ PROMETHEUS      │ │ GRAFANA         │ │ JAEGER TRACING  │
│                 │ │                 │ │                 │ │                 │
│ • Log Aggreg    │ │ • Metrics Coll  │ │ • Visualization │ │ • Distributed   │
│ • Full-text Srch│ │ • Time Series   │ │ • Dashboards    │ │ • Request Track │
│ • Kibana UI     │ │ • Alerting      │ │ • Real-time     │ │ • Performance   │
│ • ELK Stack     │ │ • Service Mon   │ │ • Custom Views  │ │ • Bottleneck ID │
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘

═══════════════════════════════════════════════════════════════════════════════
                      KUBERNETES ORCHESTRATION
═══════════════════════════════════════════════════════════════════════════════

    ┌─────────────────────────────────────────────────────────────────────┐
    │                        K8S CLUSTER                                 │
    │                                                                     │
    │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐                 │
    │  │  MASTER     │  │  MASTER     │  │  MASTER     │                 │
    │  │  NODE-1     │  │  NODE-2     │  │  NODE-3     │                 │
    │  └─────────────┘  └─────────────┘  └─────────────┘                 │
    │                                                                     │
    │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐                 │
    │  │  WORKER     │  │  WORKER     │  │  WORKER     │                 │
    │  │  NODE-1     │  │  NODE-2     │  │  NODE-3     │                 │
    │  └─────────────┘  └─────────────┘  └─────────────┘                 │
    │                                                                     │
    │  Features: HPA, VPA, Network Policies, Resource Quotas            │
    │  Storage: Persistent Volumes, StorageClasses                       │
    │  Security: Pod Security Standards, RBAC                           │
    └─────────────────────────────────────────────────────────────────────┘
```

## Les Fondements Conceptuels de Notre Architecture

### Le Paradigme Microservices : Agilité et Résilience par Design

Notre architecture s'appuie sur le pattern microservices, une approche architecturale qui décompose l'application en un ensemble de services autonomes et spécialisés. Chaque microservice encapsule une logique métier cohérente et communique avec les autres services via des APIs bien définies.

Cette approche présente des avantages décisifs pour un système critique comme Waajal Ëlëk. Elle permet d'abord une évolutivité granulaire : chaque service peut être développé, testé, déployé et mis à l'échelle indépendamment des autres. Cette autonomie se traduit par une agilité opérationnelle remarquable, permettant d'adapter rapidement la plateforme aux évolutions métier sans impacter l'ensemble du système.

La résilience constitue le second avantage majeur. Dans une architecture microservices bien conçue, la défaillance d'un service n'entraîne pas l'arrêt de l'ensemble du système. Les services critiques peuvent continuer à fonctionner même si des services périphériques rencontrent des difficultés, garantissant ainsi une continuité de service optimale.

### Cloud-Native : Performance et Élasticité

Notre plateforme est conçue selon les principes cloud-native, c'est-à-dire optimisée pour tirer pleinement parti des capacités des environnements cloud modernes. Cette conception native permet une élasticité automatique : la plateforme peut adapter ses ressources en temps réel aux variations de charge, garantissant des performances optimales même lors des pics d'utilisation.

L'approche cloud-native facilite également la mise en œuvre des meilleures pratiques en matière de déploiement continu, de monitoring et de gestion des incidents. Elle permet une observabilité complète du système et une capacité de diagnostic rapide en cas de problème.

## La Stack Technologique : Excellence et Maturité

### Socle Applicatif : Spring Boot 3 et Java 17

Notre choix de Spring Boot 3 comme framework principal s'appuie sur plusieurs considérations techniques et stratégiques. Spring Boot représente aujourd'hui la référence absolue pour le développement d'applications d'entreprise en Java, avec une communauté active de plusieurs millions de développeurs et un écosystème riche et mature.

La version 3 de Spring Boot, basée sur Java 17 LTS (Long Term Support), apporte des améliorations significatives en termes de performances, de sécurité et de productivité développeur. Java 17 étant une version LTS, elle bénéficie d'un support étendu (8 ans minimum) qui garantit la pérennité de notre choix technologique.

L'écosystème Spring offre une intégration native avec l'ensemble des technologies que nous utilisons : Spring Security pour la sécurisation, Spring Data pour l'accès aux données, Spring Cloud pour les fonctionnalités de microservices (service discovery, configuration centralisée, circuit breakers), Spring Batch pour les traitements par lots.

### Communication Inter-Services : Synchrone et Asynchrone

Notre architecture intègre deux modes de communication complémentaires entre les microservices. Pour les interactions nécessitant une réponse immédiate, nous utilisons des APIs REST sécurisées avec le protocole HTTPS et l'authentification JWT. Ces APIs sont documentées automatiquement via OpenAPI/Swagger et bénéficient de mécanismes de versioning pour garantir la compatibilité ascendante.

Pour les communications asynchrones, nous nous appuyons sur RabbitMQ, un message broker robuste et performant. Ce système de messagerie permet de découpler les services dans le temps et gère automatiquement la persistance, le routage et la livraison garantie des messages. En cas de défaillance temporaire d'un service, les messages sont automatiquement mis en attente et retraités dès que le service redevient disponible.

### Orchestration et Déploiement : Kubernetes

Kubernetes constitue le socle d'orchestration de notre plateforme. Cette technologie, devenue le standard de facto de l'orchestration de conteneurs, offre des capacités avancées de déploiement, de mise à l'échelle et de gestion du cycle de vie des applications.

Notre utilisation de Kubernetes s'accompagne de Helm Charts pour standardiser et automatiser les déploiements. Ces charts permettent de définir de manière déclarative l'ensemble des ressources nécessaires au fonctionnement de chaque microservice et de leurs dépendances.

L'auto-scaling horizontal et vertical est configuré pour chaque service selon ses caractéristiques de charge. Le système peut ainsi adapter automatiquement le nombre d'instances et les ressources allouées en fonction de métriques prédéfinies (utilisation CPU, mémoire, nombre de requêtes, temps de réponse).

## Sécurité Zero Trust : Protection Multicouches

### Authentification et Autorisation Centralisées

Notre architecture de sécurité s'appuie sur le principe "Zero Trust" : aucune requête, qu'elle provienne de l'extérieur ou de l'intérieur du système, n'est considérée comme fiable par défaut. Chaque interaction doit être authentifiée, autorisée et auditée.

L'authentification centralisée est gérée par Keycloak, une solution open source mature qui implémente les standards OAuth 2.0 et OpenID Connect. Keycloak gère l'ensemble du cycle de vie des identités : création de comptes, authentification multi-facteurs, gestion des sessions, intégration avec les annuaires d'entreprise.

L'autorisation s'appuie sur un modèle RBAC (Role-Based Access Control) granulaire. Chaque utilisateur se voit attribuer un ou plusieurs rôles, et chaque rôle définit un ensemble précis de permissions. Cette approche permet une gestion fine des droits d'accès et facilite l'audit des autorisations.

### Chiffrement et Protection des Données

Toutes les communications entre les services et avec les clients sont chiffrées via TLS 1.3, la version la plus récente et la plus sécurisée du protocole. Les clés de chiffrement font l'objet d'une rotation automatique périodique pour minimiser les risques de compromission.

Les données sensibles stockées en base sont chiffrées au niveau champ avec AES-256. Les clés de chiffrement sont gérées par HashiCorp Vault, une solution spécialisée dans la gestion sécurisée des secrets. Cette approche garantit que même en cas de compromission de la base de données, les données sensibles restent protégées.

### Monitoring de Sécurité et Détection d'Intrusion

Notre solution intègre un système de monitoring de sécurité en temps réel qui analyse en permanence les logs d'application, les métriques système et les patterns de trafic pour détecter toute activité suspecte. Ce système utilise des algorithmes d'apprentissage automatique pour identifier les anomalies comportementales et générer des alertes proactives.

Chaque action sensible (authentification, accès à des données personnelles, modification de paramètres) génère un événement d'audit horodaté et signé cryptographiquement. Cette piste d'audit, stockée dans un système immutable, permet de retracer a posteriori toutes les opérations réalisées sur la plateforme.

## Observabilité 360° : Visibilité Complète et Proactive

### Stack de Monitoring : ELK, Prometheus et Grafana

Notre architecture intègre une stack d'observabilité complète qui offre une visibilité totale sur le comportement et les performances de la plateforme. Cette stack s'articule autour de trois piliers complémentaires : logs, métriques et tracing distribué.

La gestion des logs s'appuie sur la stack ELK (Elasticsearch, Logstash, Kibana) complétée par Fluentd pour la collecte. Chaque microservice génère des logs structurés en JSON qui sont automatiquement collectés, indexés et rendus searchables via Kibana. Cette approche permet un diagnostic rapide des incidents et une analyse fine des comportements applicatifs.

Les métriques applicatives et système sont collectées par Prometheus et visualisées via Grafana. Prometheus collecte automatiquement les métriques exposées par chaque service (temps de réponse, throughput, taux d'erreur, utilisation ressources) et stocke ces données dans une base de données optimisée pour les séries temporelles.

### Tracing Distribué et Analyse de Performance

Le tracing distribué, implémenté via Zipkin, permet de suivre une requête utilisateur à travers l'ensemble des microservices qu'elle traverse. Cette visibilité est cruciale pour identifier les goulots d'étranglement et optimiser les performances de bout en bout.

Chaque requête entrante génère un identifiant de trace unique qui est propagé à travers tous les services impliqués. Cette approche permet de reconstituer le parcours complet d'une transaction et d'identifier précisément les services ou les interactions responsables de latences.

### Alerting Intelligent et Proactif

Notre système d'alerting s'appuie sur des règles sophistiquées qui combinent métriques techniques et métriques métier. Les alertes sont classifiées par niveau de criticité et routées automatiquement vers les équipes compétentes via multiple canaux (email, SMS, intégration Slack, webhooks).

L'intelligence artificielle est utilisée pour réduire les faux positifs en apprenant les patterns normaux de comportement du système et en adaptant automatiquement les seuils d'alerte. Cette approche permet une détection précoce des problèmes tout en évitant la fatigue d'alerte qui peut conduire à ignorer de véritables incidents.

## Résilience et Haute Disponibilité : Tolérance aux Pannes

### Circuit Breakers et Patterns de Résilience

Chaque interaction entre microservices est protégée par un circuit breaker implémenté via la librairie Resilience4j. Ce mécanisme surveille en permanence le taux d'échec et les temps de réponse des appels distants. En cas de détérioration des performances d'un service, le circuit breaker s'ouvre automatiquement et redirige le trafic vers des mécanismes de fallback.

Ces fallbacks sont conçus spécifiquement pour chaque interaction : retour de données en cache pour les consultations, mode dégradé pour les fonctionnalités non critiques, mise en file d'attente pour les opérations différables. Cette approche garantit que les utilisateurs continuent à bénéficier d'un service, même si certaines fonctionnalités sont temporairement indisponibles.

### Déploiement Blue-Green et Rollback Automatique

Notre stratégie de déploiement s'appuie sur le pattern blue-green qui permet de déployer une nouvelle version de l'application en parallèle de la version actuelle. Cette approche élimine les interruptions de service et permet un rollback instantané en cas de problème avec la nouvelle version.

Le processus de déploiement intègre des tests automatisés de fumée qui vérifient la santé de la nouvelle version avant de basculer le trafic. En cas d'échec de ces tests ou de détection d'anomalies post-déploiement, un rollback automatique est déclenché pour restaurer la version précédente.

### Backup et Recovery : Protection des Données

Notre stratégie de sauvegarde implémente le principe 3-2-1 : 3 copies des données, sur 2 supports différents, avec 1 copie externe. Les sauvegardes de base de données sont automatisées et incluent à la fois des snapshots complets et la réplication continue des logs de transaction.

La stratégie de recovery est testée mensuellement via des exercices de restauration sur un environnement dédié. Ces tests permettent de valider les procédures et de mesurer les RTO (Recovery Time Objective) et RPO (Recovery Point Objective) effectifs.

## Architecture des Données : Cohérence et Performance

### Database per Service et Gestion de la Cohérence

Conformément aux principes des microservices, chaque service dispose de sa propre base de données, garantissant un découplage complet au niveau des données. Cette approche présente l'avantage de permettre à chaque service de choisir la technologie de stockage la plus adaptée à ses besoins spécifiques.

La cohérence entre services est gérée via le pattern Saga, qui décompose les transactions distribuées en une séquence d'opérations locales coordonnées par des événements. En cas d'échec, des transactions de compensation sont automatiquement exécutées pour maintenir la cohérence globale du système.

### Optimisation des Performances et Mise en Cache

Notre architecture intègre plusieurs niveaux de cache pour optimiser les performances. Le cache applicatif (Redis) stocke les données fréquemment consultées et les résultats de calculs complexes. Le cache de requêtes optimise l'accès aux bases de données, et le CDN accélère la livraison des assets statiques.

La stratégie de cache est intelligente et adaptative : les données critiques bénéficient d'une invalidation immédiate, tandis que les données moins sensibles utilisent des stratégies TTL (Time To Live) optimisées selon leurs patterns d'utilisation.

## Documentation Technique Détaillée des Microservices

### Core Services Layer - Services Fondamentaux

#### USER-MANAGEMENT-SERVICE
**Port** : 8081 | **Instances** : 3-6 (HPA) | **Base de données** : PostgreSQL

```yaml
Responsabilités techniques :
├── Authentication Engine (Spring Security 6)
│   ├── JWT Token Management (RS256 Algorithm)
│   ├── Refresh Token Rotation Strategy  
│   ├── Multi-Factor Authentication (TOTP/SMS)
│   └── Password Policy Enforcement (OWASP Standards)
├── Authorization Framework
│   ├── RBAC Implementation (Role-Based Access Control)
│   ├── Permission Matrix Management
│   ├── Resource-Level Security Annotations
│   └── Dynamic Permission Evaluation
├── Session Management
│   ├── Distributed Session Store (Redis)
│   ├── Session Timeout Policies
│   ├── Concurrent Session Control
│   └── Session Hijacking Prevention
└── Identity Federation
    ├── LDAP/Active Directory Integration
    ├── SAML 2.0 Support
    ├── OAuth2 Provider Implementation
    └── OpenID Connect Compliance
```

**APIs Exposées** :
- `POST /auth/login` - Authentication endpoint avec rate limiting
- `POST /auth/refresh` - Token refresh avec sliding expiration
- `GET /users/{id}/permissions` - Permission resolution avec cache
- `PUT /users/{id}/roles` - Role assignment avec audit logging

**Technologies Clés** : Spring Security 6, JWT (jjwt), BCrypt, Redis Session, Hibernate Envers

---

#### PERSONNEL-SVC (Personnel Management Service)
**Port** : 8082 | **Instances** : 2-4 (HPA) | **Base de données** : PostgreSQL

```yaml
Domain Model & Business Logic :
├── Military Hierarchy Management
│   ├── Grade Progression Rules Engine
│   ├── Career Path Validation Algorithms
│   ├── Promotion Eligibility Calculator
│   └── Service Branch Classification System
├── Personnel Data Management
│   ├── Personal Information CRUD Operations
│   ├── Career Timeline Event Sourcing
│   ├── Document Management Integration
│   └── Data Validation & Consistency Checks
├── Integration Interfaces
│   ├── HR System Synchronization (REST/SOAP)
│   ├── Payroll System Integration (ESB Pattern)
│   ├── Identity Provider User Provisioning
│   └── External Military Database Connectors
└── Event Publishing
    ├── Career Change Events (RabbitMQ)
    ├── Personnel Status Updates
    ├── Promotion Notification Events
    └── Retirement Eligibility Alerts
```

**APIs Exposées** :
- `GET /personnel/{id}/career-timeline` - Career progression avec pagination
- `POST /personnel/bulk-import` - Batch personnel import avec validation
- `PUT /personnel/{id}/promotion` - Grade promotion avec workflow
- `GET /personnel/search` - Advanced search avec filters et sorting

**Technologies Clés** : Spring Data JPA, MapStruct, Apache Kafka, Spring Batch, Flyway Migration

---

#### ADHESION-SVC (Membership Service)  
**Port** : 8083 | **Instances** : 3-5 (HPA) | **Base de données** : PostgreSQL

```yaml
Business Process Management :
├── Registration Workflow Engine
│   ├── Multi-Step Form Validation (JSR-303)
│   ├── Document Upload & Verification Service
│   ├── Eligibility Rules Engine (Drools)
│   └── Approval Workflow State Machine
├── Simulation Engine
│   ├── Contribution Scenario Calculator
│   ├── Pension Projection Algorithms
│   ├── Tax Optimization Calculator  
│   └── Risk Assessment Models
├── Contract Generation System
│   ├── Document Template Engine (Thymeleaf)
│   ├── Digital Signature Integration (DocuSign API)
│   ├── PDF Generation Service (iText)
│   └── Version Control & Audit Trail
└── Integration Services
    ├── Payment Gateway Integration
    ├── Identity Verification Services
    ├── Credit Check API Integration
    └── Notification Service Connectors
```

**APIs Exposées** :
- `POST /adhesion/registration` - Start registration workflow
- `GET /adhesion/{id}/simulation` - Pension projection calculation  
- `POST /adhesion/{id}/documents` - Document upload avec antivirus scan
- `PUT /adhesion/{id}/approve` - Approval workflow avec digital signature

**Technologies Clés** : Spring State Machine, Drools, iText PDF, Apache Tika, Spring Cloud OpenFeign

---

#### COTISATION-SVC (Contribution Service)
**Port** : 8084 | **Instances** : 4-8 (HPA) | **Base de données** : PostgreSQL

```yaml
Financial Calculation Engine :
├── Contribution Calculator
│   ├── Multi-Variable Formula Engine
│   ├── Tax Bracket Optimization Logic
│   ├── Voluntary Contribution Handler
│   └── Retroactive Calculation Processor
├── Collection Management
│   ├── Payment Schedule Generator
│   ├── Direct Debit Integration (SEPA)
│   ├── Mobile Money API Integration
│   └── Payment Failure Recovery System
├── Reconciliation Engine
│   ├── Bank Statement Parser (MT940/CAMT)
│   ├── Payment Matching Algorithms
│   ├── Discrepancy Detection & Resolution
│   └── Automated Clearing System Interface
└── Compliance & Reporting
    ├── Regulatory Reporting Generator
    ├── Tax Authority Data Export
    ├── Audit Trail Management
    └── Financial Control Validation
```

**APIs Exposées** :
- `POST /cotisation/calculate` - Contribution calculation avec caching
- `GET /cotisation/{id}/schedule` - Payment schedule generation
- `POST /cotisation/payment` - Payment processing avec idempotency
- `GET /cotisation/reconciliation` - Payment reconciliation status

**Technologies Clés** : Spring Boot Actuator, Micrometer Metrics, Apache Camel, Jackson JSON, Resilience4j

---

### Business Logic Layer - Services Métier Avancés

#### POINTS-SVC (Points Management Service)
**Port** : 8085 | **Instances** : 3-6 (HPA) | **Base de données** : PostgreSQL

```yaml
Actuarial Computation Engine :
├── Point Conversion System
│   ├── Real-Time Conversion Calculator
│   ├── Point Value Management (Time-Series)  
│   ├── Rounding Strategy Implementation
│   └── Historical Exchange Rate Tracking
├── Balance Management
│   ├── Account Balance Calculator  
│   ├── Point Transfer Processing
│   ├── Bonus Point Allocation System
│   └── Point Expiry Management
├── Attestation Service
│   ├── Digital Certificate Generator
│   ├── Blockchain-Based Verification
│   ├── QR Code Generation Service
│   └── Multi-Language Document Support
└── Analytics & Reporting
    ├── Point Accumulation Analytics
    ├── Value Trend Analysis
    ├── Performance Benchmarking
    └── Predictive Point Modeling
```

**Technologies Clés** : Spring Data R2DBC, WebFlux Reactive, Apache Commons Math, BouncyCastle Crypto

---

#### FINANCIAL-SVC (Investment Management Service)
**Port** : 8086 | **Instances** : 2-4 (HPA) | **Base de données** : PostgreSQL + TimescaleDB

```yaml
Portfolio Management System :
├── Asset Allocation Engine
│   ├── Modern Portfolio Theory Implementation
│   ├── Risk-Return Optimization (Markowitz Model)
│   ├── Rebalancing Algorithm (Calendar/Threshold-based)
│   └── ESG Scoring Integration
├── Performance Analytics
│   ├── Return Calculation Engine (IRR, TWRR)
│   ├── Risk Metrics Calculator (VaR, CVaR, Sharpe Ratio)
│   ├── Benchmark Comparison System
│   └── Attribution Analysis Framework
├── Trading Interface
│   ├── Order Management System (OMS)
│   ├── Execution Algorithms (TWAP, VWAP)
│   ├── Market Data Integration (Bloomberg/Reuters)
│   └── Settlement & Custody Interface
└── Compliance Framework  
    ├── Investment Policy Compliance
    ├── Regulatory Reporting (AIFMD)
    ├── Risk Limit Monitoring
    └── Audit Trail Management
```

**Technologies Clés** : QuantLib Java, Apache Spark, TimescaleDB, Spring WebFlux, Apache Kafka Streams

---

### AI/ML Layer - Services d'Intelligence Artificielle

#### AI-FRAUD-SVC (AI Fraud Detection Service)
**Port** : 8087 | **Instances** : 2-3 (HPA) | **Base de données** : MongoDB + InfluxDB

```yaml
Machine Learning Pipeline :
├── Feature Engineering Pipeline
│   ├── Real-time Feature Extraction
│   ├── Behavioral Pattern Analysis  
│   ├── Geolocation Anomaly Detection
│   └── Device Fingerprinting System
├── ML Model Serving
│   ├── Isolation Forest (Anomaly Detection)
│   ├── LSTM Network (Sequential Pattern Analysis)
│   ├── Random Forest (Classification)
│   └── AutoEncoder (Dimensionality Reduction)
├── Real-time Scoring Engine
│   ├── Event Stream Processing (Apache Flink)
│   ├── Risk Score Calculation
│   ├── Alert Threshold Management
│   └── False Positive Reduction Logic
└── Model Management
    ├── A/B Testing Framework
    ├── Model Versioning & Rollback
    ├── Performance Monitoring
    └── Continuous Learning Pipeline
```

**Technologies Clés** : TensorFlow Java, Apache Flink, MLflow, MongoDB, InfluxDB, Kafka Streams

---

#### ROBO-ADVISOR-SVC (Automated Advisory Service)
**Port** : 8088 | **Instances** : 2-4 (HPA) | **Base de données** : Neo4j + PostgreSQL

```yaml
Advisory Intelligence System :
├── Risk Profiling Engine
│   ├── Questionnaire Analysis Algorithm
│   ├── Behavioral Finance Models
│   ├── Dynamic Risk Tolerance Assessment
│   └── Life Stage Classification System
├── Recommendation Engine
│   ├── Goal-Based Investment Strategy
│   ├── Tax-Loss Harvesting Optimizer
│   ├── Asset Class Recommendation System
│   └── Rebalancing Trigger Algorithm
├── Personalization Framework
│   ├── Client Preference Learning (Collaborative Filtering)
│   ├── Communication Style Adaptation
│   ├── Timing Optimization (Send-Time Optimization)
│   └── Content Personalization Engine
└── Performance Tracking
    ├── Goal Progress Monitoring
    ├── Advice Effectiveness Measurement
    ├── Client Satisfaction Scoring
    └── Recommendation Outcome Analysis
```

**Technologies Clés** : Apache Mahout, Neo4j Graph Database, Spring AI, scikit-learn via Jython

---

#### SIMULATION-SVC (Monte Carlo Simulation Service)
**Port** : 8089 | **Instances** : 2-6 (Auto-scaling) | **Base de données** : PostgreSQL + Redis

```yaml
Stochastic Modeling Framework :
├── Monte Carlo Engine
│   ├── Pseudo-Random Number Generator (Mersenne Twister)
│   ├── Variance Reduction Techniques (Antithetic Variables)
│   ├── Parallel Computation Framework
│   └── Convergence Analysis Tools
├── Economic Model Library
│   ├── Geometric Brownian Motion (Asset Prices)
│   ├── Cox-Ingersoll-Ross Model (Interest Rates)
│   ├── Jump Diffusion Models (Market Shocks)
│   └── Multi-Factor Models (Economic Scenarios)
├── Actuarial Calculation Engine
│   ├── Mortality Projection Models
│   ├── Longevity Risk Assessment
│   ├── Pension Liability Calculation
│   └── Solvency Ratio Estimation
└── Result Processing
    ├── Statistical Summary Generator
    ├── Confidence Interval Calculator  
    ├── Sensitivity Analysis Framework
    └── Visualization Data Preparation
```

**Technologies Clés** : Apache Commons Math, CUDA Java (GPU Computing), Apache Spark, JBlas Linear Algebra

---

#### BUSINESS-INTEL-SVC (Business Intelligence Service)
**Port** : 8090 | **Instances** : 2-4 (HPA) | **Base de données** : ClickHouse + PostgreSQL

```yaml
Analytics & Reporting Platform :
├── Data Processing Pipeline
│   ├── ETL Framework (Apache NiFi)
│   ├── Data Quality Validation
│   ├── Master Data Management
│   └── Data Lineage Tracking
├── OLAP Engine
│   ├── Dimensional Modeling (Star Schema)
│   ├── Pre-aggregated Cube Management
│   ├── Drill-down/Drill-through Operations
│   └── Dynamic Measure Calculation
├── Machine Learning Analytics
│   ├── Predictive Analytics (Time Series)
│   ├── Customer Segmentation (K-Means)
│   ├── Churn Prediction Models
│   └── Anomaly Detection in KPIs
└── Visualization Engine
    ├── Interactive Dashboard Framework
    ├── Real-time Data Streaming
    ├── Custom Chart Components
    └── Export/Sharing Capabilities
```

**Technologies Clés** : ClickHouse OLAP, Apache Superset, D3.js, Apache NiFi, Tableau Server API

---

### Communication & Integration Layer

#### NOTIFICATION-SVC (Multi-channel Notification Service)
**Port** : 8091 | **Instances** : 3-5 (HPA) | **Base de données** : MongoDB + Redis

```yaml
Omnichannel Communication Platform :
├── Message Routing Engine
│   ├── Channel Selection Algorithm
│   ├── Delivery Optimization (A/B Testing)
│   ├── Fallback Strategy Implementation
│   └── Message Queuing & Retry Logic
├── Template Management System
│   ├── Dynamic Content Generation
│   ├── Multi-language Support (i18n)
│   ├── Personalization Variables
│   └── Template Version Control
├── Channel Integrations
│   ├── SMS Gateway (Twilio/MessageBird)
│   ├── Email Service (SendGrid/AWS SES)  
│   ├── Push Notification (Firebase/APNs)
│   └── In-App Message System
└── Analytics & Optimization
    ├── Delivery Rate Tracking
    ├── Open/Click Rate Analysis
    ├── Engagement Score Calculation
    └── Campaign Performance Metrics
```

**Technologies Clés** : Apache Pulsar, MongoDB, Redis, Spring WebFlux, Apache Freemarker

---

#### INTEGRATION-SVC (Enterprise Integration Service)
**Port** : 8092 | **Instances** : 2-3 (HPA) | **Base de données** : PostgreSQL

```yaml
Enterprise Service Bus :
├── API Gateway Functions
│   ├── Protocol Translation (REST/SOAP/GraphQL)
│   ├── Message Transformation (XML/JSON/EDI)
│   ├── Request/Response Mediation
│   └── Service Orchestration
├── External System Connectors
│   ├── Mobile Money APIs (Wave/Orange Money)
│   ├── Banking System Integration (ISO 20022)
│   ├── ERP System Connectors (SAP/Oracle)
│   └── Government Portal APIs
├── Data Synchronization
│   ├── Change Data Capture (CDC)
│   ├── Event-Driven Synchronization
│   ├── Conflict Resolution Strategies
│   └── Data Consistency Validation
└── Monitoring & Management
    ├── API Performance Monitoring
    ├── SLA Management & Reporting
    ├── Error Handling & Recovery
    └── Circuit Breaker Implementation
```

**Technologies Clés** : Apache Camel, Spring Integration, Apache ActiveMQ, Debezium CDC, OpenAPI 3.0

---

## Infrastructure Services & Cross-Cutting Concerns

### Service Mesh Architecture (Istio)
```yaml
Traffic Management :
├── Load Balancing (Round Robin, Least Connection, Random)
├── Circuit Breaker (Hystrix Pattern Implementation)
├── Rate Limiting (Token Bucket Algorithm)
└── Fault Injection (Chaos Engineering)

Security Features :
├── Mutual TLS (mTLS) between services
├── Service-to-Service Authentication
├── Policy Enforcement (RBAC at service level)
└── Certificate Management & Rotation
```

### Configuration Management (Spring Cloud Config)
```yaml
Centralized Configuration :
├── Environment-specific properties
├── Feature Flags (LaunchDarkly Integration)
├── Secrets Management (HashiCorp Vault)
└── Dynamic Configuration Refresh
```

### Distributed Tracing & APM
```yaml
Observability Stack :
├── Jaeger (Distributed Tracing)
├── Prometheus (Metrics Collection)
├── Grafana (Visualization & Alerting)
└── ELK Stack (Centralized Logging)
```

Cette architecture représente l'état de l'art en matière de conception de systèmes distribués modernes pour la gestion de régimes de retraite. Elle garantit que la plateforme Waajal Ëlëk pourra accompagner la croissance de la Mutuelle des Armées et s'adapter aux défis technologiques des prochaines décennies.