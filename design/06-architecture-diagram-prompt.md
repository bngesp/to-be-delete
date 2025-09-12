# Architecture Diagram - Prompt IA

## Description

Prompt pour générer le diagramme d'architecture technique complet de la plateforme Waajal Ëlëk avec tous les logos et technologies.

---

## Prompt IA pour Architecture Visuelle

```
Create a comprehensive technical architecture diagram for "WAAJAL ËLËK" - a cloud-native microservices platform for military pension management.

DIAGRAM SPECIFICATIONS:
- Professional enterprise architecture diagram style
- High-resolution output suitable for technical presentations
- Include official technology logos and brand colors
- Clean, modern layout with proper visual hierarchy
- Color-coded layers for easy understanding

TITLE & HEADER:
- Main title: "WAAJAL ËLËK - Architecture Microservices Cloud-Native"
- Subtitle: "Système de Gestion de Retraite Militaire - 23 Modules Fonctionnels"
- Senegalese flag colors integration (green, yellow, red)

ARCHITECTURE LAYERS (top to bottom):

1. CLIENT LAYER:
   - React.js logo + "Web Portal" (desktop browser mockup)
   - iOS logo + Android logo + "Mobile Apps" (phone mockups)
   - PWA icon + "Progressive Web App"

2. LOAD BALANCER & GATEWAY:
   - HAProxy logo or NGINX logo
   - Spring Cloud Gateway logo
   - SSL/TLS certificate icons
   - Rate limiting indicators

3. SECURITY LAYER (prominent security section):
   - Keycloak logo + "Identity Provider"
   - HashiCorp Vault logo + "Secrets Management" 
   - OAuth2 + OpenID Connect badges
   - Zero Trust architecture indicators

4. MICROSERVICES LAYER (16 services in organized grid):
   Row 1: USER-MANAGEMENT, PERSONNEL-SVC, ADHESION-SVC, COTISATION-SVC
   Row 2: POINTS-SVC, ACCOUNT-SVC, PENSION-SVC, FINANCIAL-SVC
   Row 3: ACCOUNTING-SVC, ACTUARIAL-SVC, SIMULATION-SVC, AI-FRAUD-SVC
   Row 4: ROBO-ADVISOR, BUSINESS-INTEL, NOTIFICATION-SVC, INTEGRATION-SVC
   - Each service with Spring Boot logo
   - Java 17 LTS badges
   - Port numbers displayed (8081-8092)

5. AI/ML SERVICES (highlighted section):
   - TensorFlow logo (AI-FRAUD-SVC)
   - Apache Mahout logo (ROBO-ADVISOR)  
   - scikit-learn logo (ML components)
   - GPU computing indicators (CUDA)

6. MESSAGING LAYER:
   - RabbitMQ logo with cluster representation
   - Apache Kafka logo with streaming indicators
   - Dead letter queue visualizations
   - Message routing patterns

7. DATA PERSISTENCE LAYER:
   - PostgreSQL logo (multiple instances with master/slave)
   - Redis logo (cluster configuration)
   - MongoDB logo (document store)
   - InfluxDB logo (time series)
   - Neo4j logo (graph database)
   - ClickHouse logo (analytics)

8. OBSERVABILITY & MONITORING:
   - ELK Stack: Elasticsearch + Logstash + Kibana logos
   - Prometheus logo + Grafana logo
   - Jaeger logo (distributed tracing)
   - APM indicators

9. INFRASTRUCTURE LAYER:
   - Kubernetes logo (orchestration)
   - Docker logo (containerization)
   - Helm logo (package management)
   - Istio logo (service mesh)
   - Cloud provider indicators

CONNECTION FLOWS:
- Arrows showing request flow from clients to services
- Database connection lines from services to data stores
- Message queue connections with routing patterns
- Monitoring data flow indicators
- Security checkpoint arrows
- Load balancing distribution patterns

VISUAL ELEMENTS:
- Technology logos in their official brand colors
- Consistent icon sizing and spacing
- Professional enterprise diagram styling
- Legend explaining symbols and connection types
- Performance metrics callouts where relevant
- Security indicators (locks, shields, certificates)
- Scalability indicators (horizontal scaling arrows)

ANNOTATIONS:
- "23 Modules Fonctionnels" prominently displayed
- Technology stack summary in sidebar
- Key architectural patterns labeled
- Performance specifications noted
- Security compliance badges (OHADA, BCEAO)

STYLE REQUIREMENTS:
- Clean, professional technical diagram
- Proper spacing and alignment
- Readable fonts and labels
- Official technology colors maintained
- Enterprise architecture best practices
- Print-ready resolution (300 DPI)
- Suitable for technical documentation

OUTPUT FORMAT:
- Landscape orientation (16:9 or similar)
- High-resolution PNG or SVG
- Professional presentation quality
- Technical documentation suitable
```