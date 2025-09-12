# Dashboard Principal - Application Web

## Description de l'Interface

Le dashboard principal de Waajal Ëlëk est l'interface centrale pour les gestionnaires de la Mutuelle des Armées. Il offre une vue d'ensemble complète des métriques clés du régime de retraite avec des visualisations interactives et des KPI en temps réel.

## Spécifications Techniques

### Layout et Structure

**Header (80px de hauteur)**
- Logo Waajal Ëlëk (à gauche)
- Menu de navigation horizontal (centre)
- Profil utilisateur + notifications (à droite)
- Indicateur de sécurité (badge SSL/encryption)

**Sidebar Gauche (280px de largeur)**
- Navigation principale avec icônes
- Modules : Adhérents, Finances, Pensions, Analytics, Administration
- Indicateur de statut système (vert/orange/rouge)

**Zone Principale (contenu dynamique)**
- Grille de widgets responsive (4 colonnes sur desktop)
- Graphiques interactifs avec Chart.js/D3.js
- Tableaux de données avec pagination
- Filtres temporels et critères de segmentation

### Widgets Principaux

1. **Métriques Globales** (4 cartes horizontales)
   - Nombre total d'adhérents : 12,847
   - Total des cotisations ce mois : 2.4 Mrd FCFA
   - Valeur du point actuelle : 847.32 FCFA
   - Performance portefeuille : +5.2%

2. **Graphique Évolution Adhésions** (demi-largeur)
   - Graphique en aire avec tendance croissante
   - Période : 12 derniers mois
   - Segmentation par grade militaire

3. **Répartition Investissements** (demi-largeur)
   - Graphique en camembert interactif
   - Obligations : 45%, Actions : 35%, Immobilier : 20%
   - Tooltip avec détails de performance

4. **Alertes et Notifications** (pleine largeur)
   - Liste des alertes système
   - Demandes en attente de validation
   - Incidents de sécurité

5. **Top Transactions Récentes** (pleine largeur)
   - Tableau avec les 10 dernières transactions
   - Colonnes : Date, Adhérent, Type, Montant, Statut
   - Actions rapides (voir détail, approuver)

### Éléments Visuels Spécifiques

- **Cartes métriques** : Fond blanc, ombre subtile, icône colorée à gauche
- **Graphiques** : Couleurs de la charte (vert principal, orange, rouge)
- **Badges de statut** : Couleurs sémantiques (vert=OK, orange=attention, rouge=critique)
- **Boutons d'action** : Style flat avec hover effects
- **Loading states** : Skeleton screens pour les chargements

---

## Prompt IA pour Génération

```
Create a professional financial dashboard interface for "Waajal Ëlëk" - a military pension management system in Senegal.

LAYOUT SPECIFICATIONS:
- Modern, clean enterprise dashboard design
- Header with logo "Waajal Ëlëk" (left), navigation menu (center), user profile (right)
- Left sidebar (280px) with navigation menu icons
- Main content area with responsive card grid layout

COLOR SCHEME:
- Primary Green: #0B5345 (military Senegal color)
- Secondary Green: #138D75
- Accent Orange: #E67E22 (Senegal flag reference)
- Accent Red: #E74C3C
- Neutral Grays: #2C3E50, #7F8C8D, #ECF0F1
- White backgrounds: #FFFFFF

DASHBOARD CONTENT:
1. TOP METRICS ROW (4 cards):
   - "Adhérents Actifs: 12,847" with user icon
   - "Cotisations Mois: 2.4 Mrd FCFA" with money icon
   - "Valeur Point: 847.32 FCFA" with chart icon
   - "Performance: +5.2%" with trending up icon

2. MAIN CHARTS SECTION:
   - Left: Line chart "Évolution Adhésions" (12 months trend)
   - Right: Pie chart "Répartition Investissements" (Obligations 45%, Actions 35%, Immobilier 20%)

3. ALERTS SECTION:
   - Notification cards with warning/info/success states
   - "3 demandes en attente", "Système opérationnel", "Sauvegarde OK"

4. RECENT TRANSACTIONS TABLE:
   - Clean table with columns: Date, Nom, Type, Montant, Statut
   - Action buttons for each row
   - Pagination at bottom

DESIGN STYLE:
- Clean, modern interface with subtle shadows
- Card-based layout with rounded corners
- Professional typography (Inter/Roboto fonts)
- Accessible contrast ratios (WCAG 2.1 AA)
- French language interface
- Military/financial professional aesthetic
- Responsive design elements
- Interactive elements with hover states

SPECIFIC ELEMENTS:
- Senegalese flag colors integration
- Military insignia styling
- Financial data visualization best practices
- Security indicators (SSL badges, encryption icons)
- Real-time data indicators (live dots, refresh icons)

OUTPUT: High-resolution dashboard mockup suitable for presentation
```