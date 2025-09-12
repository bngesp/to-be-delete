# Application Mobile - Consultation Compte

## Description de l'Interface

L'écran de consultation de compte mobile offre une vue détaillée et interactive du solde de retraite, de l'historique des cotisations et des projections personnalisées. Interface optimisée pour la consultation de données avec navigation tactile fluide.

## Spécifications Techniques

### Structure de l'Écran

**Header avec Navigation (100px)**
- Bouton retour (chevron gauche)
- Titre "Mon Compte Retraite"
- Menu contextuel (3 points, droite)
- Sous-header avec dernier refresh : "Mis à jour il y a 2 min"

**Résumé Principal** (240px)
- Card principale avec background légèrement coloré
- Avatar + Grade : "Sergent-Chef DIALLO"
- Matricule : "SN-ARM-2019-0847"
- Solde actuel : "2,847 POINTS" (très prominent)
- Équivalent : "2,403,429 FCFA" 
- Évolution mensuelle avec graphique sparkline
- Badge statut : "Compte Actif" (vert)

**Onglets de Navigation** (50px)
- Tabs scrollables horizontalement :
  - "Vue d'ensemble" (actif)
  - "Historique" 
  - "Projections"
  - "Documents"
- Indicateur de tab actif avec ligne verte

**Section Vue d'Ensemble** (scrollable)

1. **Graphique d'Évolution** (280px)
   - Graphique interactif des 12 derniers mois
   - Possibilité de toucher les points pour détails
   - Zoom pinch-to-zoom activé
   - Légendes : Points acquis (vert), Valeur (orange)

2. **Métriques Clés** (grille 2x2, 180px)
   - "Points ce mois" : "+47" (vert avec flèche up)
   - "Cotisation moyenne" : "28,500 FCFA"
   - "Années cotisées" : "5.2 ans"
   - "Âge retraite projeté" : "55 ans"

3. **Dernières Cotisations** (liste, 300px)
   - 5 dernières cotisations visibles
   - Format card par cotisation :
     - Date (left) | Montant cotisé | Points acquis | Status badge
   - Swipe left pour voir détails
   - "Voir plus" sticky button en bas

4. **Projections Rapides** (200px)
   - "Votre retraite projetée" (titre)
   - Slider âge de départ (50-60 ans)
   - Mise à jour temps réel de la pension estimée
   - "Simuler en détail" (bouton CTA)

### Interactions Avancées

**Touch et Gestures**
- Swipe horizontal entre onglets
- Pull-to-refresh sur toute la page
- Long press sur montants pour copier
- Swipe gauche sur cotisations pour actions

**Animations**
- Counter animation pour les montants
- Chart animation lors du chargement
- Skeleton loading pour les données
- Smooth transitions entre tabs

**États Interactifs**
- Pressed states sur tous boutons
- Loading states avec spinners contextuels
- Empty states si pas de données
- Error states avec retry

### Fonctionnalités Offline

**Données en Cache**
- Dernier solde consulté disponible offline
- Historique des 3 derniers mois en cache
- Message "Données hors ligne" si pas de réseau
- Sync automatique à la reconnexion

**Indicateurs de Statut**
- Icône wifi pour statut connexion
- Timestamp dernière synchronisation
- Badge "Hors ligne" si applicable

---

## Prompt IA pour Génération

```
Design a detailed mobile account view screen for "Waajal Ëlëk" military pension app - showing comprehensive account information and transaction history.

DEVICE & LAYOUT:
- iPhone format (393x852px) 
- Scrollable content with fixed header
- Tab-based navigation within the screen

COLOR PALETTE:
- Primary Green: #0B5345
- Success Green: #27AE60  
- Accent Orange: #E67E22
- Background: #F8F9FA
- Cards: #FFFFFF
- Text: #2C3E50, #7F8C8D

HEADER SECTION (100px):
- Back arrow (left) + "Mon Compte Retraite" title + menu dots (right)
- Subtitle: "Mis à jour il y a 2 min" in small gray text

MAIN ACCOUNT CARD (240px):
- Prominent white card with subtle green accent
- Military avatar with rank insignia
- "Sergent-Chef DIALLO Mamadou"
- "Matricule: SN-ARM-2019-0847"
- Large balance display: "2,847 POINTS"
- Equivalent value: "2,403,429 FCFA"
- Small sparkline chart showing trend
- Green status badge: "Compte Actif"

HORIZONTAL TABS (50px):
- Scrollable tab bar: "Vue d'ensemble | Historique | Projections | Documents"
- Active tab "Vue d'ensemble" with green underline indicator

CONTENT SECTIONS (scrollable):

1. EVOLUTION CHART (280px):
   - Interactive line chart showing 12 months progression
   - Touch points show detailed tooltips
   - Dual axis: Points (green line) and Value (orange line)
   - Grid background with month labels

2. KEY METRICS GRID (180px):
   - 2x2 grid of metric cards:
   - "Points ce mois: +47" (green arrow up)
   - "Cotisation moyenne: 28,500 FCFA"
   - "Années cotisées: 5.2 ans"  
   - "Âge retraite: 55 ans"

3. RECENT CONTRIBUTIONS LIST (300px):
   - "Dernières cotisations" section title
   - Card-based list of 5 recent contributions
   - Each card shows: Date | Amount contributed | Points earned | Status
   - Swipe indicators on cards
   - "Voir plus" button at bottom

4. QUICK PROJECTIONS TOOL (200px):
   - "Votre retraite projetée" title
   - Interactive slider for retirement age (50-60)
   - Real-time pension estimate updates
   - "Simuler en détail" CTA button

DESIGN CHARACTERISTICS:
- Clean, data-focused interface
- Touch-optimized with large interactive elements
- French language throughout
- Military professional aesthetic
- Chart.js or similar chart styling
- Card-based information architecture
- Clear visual hierarchy
- Loading states and skeleton screens
- Interactive elements with haptic feedback indicators
- Accessible touch targets (44px+)

MOBILE-SPECIFIC FEATURES:
- Pull-to-refresh at top
- Smooth scrolling and transitions  
- Touch-friendly chart interactions
- Swipe gestures for navigation
- Responsive typography scaling

OUTPUT: High-resolution mobile account screen mockup showing detailed financial information in a clean, professional interface
```