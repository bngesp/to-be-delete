# Portail Adhérent - Application Web

## Description de l'Interface

Le portail adhérent est l'espace personnel de chaque militaire pour consulter et gérer son compte retraite. Interface centrée sur l'utilisateur avec une approche de self-service et des outils de simulation intuitifs.

## Spécifications Techniques

### Layout et Structure

**Header Simplifié (70px de hauteur)**
- Logo Waajal Ëlëk + slogan "Votre retraite sécurisée"
- Nom/grade de l'adhérent connecté
- Menu utilisateur (Mon Profil, Paramètres, Déconnexion)
- Indicateur de sécurité et dernière connexion

**Navigation Principale (tabs horizontales)**
- Mon Compte | Mes Cotisations | Simulations | Documents | Support
- Indicateur actif avec soulignement vert

**Zone de Contenu Principal**
- Layout centré avec marges latérales
- Cards informatives avec données personnalisées
- Graphiques de progression personnelle
- Boutons d'action principaux bien visibles

### Contenu de l'Onglet "Mon Compte"

1. **Carte Résumé Personnel** (pleine largeur, prominente)
   - Photo/avatar + grade + unité
   - Solde total de points : 2,847 points
   - Valeur estimée : 2,403,429 FCFA
   - Projection pension à 55 ans : 186,500 FCFA/mois
   - Bouton "Simuler ma retraite" (call-to-action principal)

2. **Évolution de Mon Épargne** (graphique full-width)
   - Graphique en aire montrant la progression des points
   - Période de 5 ans avec marqueurs d'événements
   - Zoom sur les 12 derniers mois
   - Légende : Points acquis vs Valeur estimée

3. **Cotisations Récentes** (tableau condensé)
   - 5 dernières cotisations avec détails
   - Colonnes : Date, Montant cotisé, Points acquis, Statut
   - Lien "Voir tout l'historique"

4. **Actions Rapides** (3 cartes horizontales)
   - "Modifier mes cotisations" avec icône paramètres
   - "Télécharger attestation" avec icône document
   - "Contacter un conseiller" avec icône support

### Éléments d'Interface Spécifiques

**Indicateurs de Progression**
- Barre de progression vers l'objectif retraite
- Pourcentage d'avancement affiché
- Messages motivationnels contextuels

**Simulateur Intégré**
- Widget de simulation rapide en sidebar
- Sliders pour ajuster âge départ/montant cotisation
- Résultat en temps réel avec visualisation

**Badges et Statuts**
- Badge "Compte Sécurisé" avec icône cadenas
- Statut cotisations : "À jour" (vert) ou "En retard" (orange)
- Niveau d'épargne : "Débutant/Intermédiaire/Expert"

### Responsive et Mobile-First

- Adaptation tablette : 2 colonnes pour les cartes
- Mobile : Stack vertical avec priorité au résumé
- Menu burger sur mobile avec navigation simplifiée
- Touch-friendly buttons et zones d'interaction

---

## Prompt IA pour Génération

```
Design a personal member portal interface for "Waajal Ëlëk" - a military pension platform for Senegalese armed forces members.

INTERFACE TYPE: Personal account dashboard for individual military personnel

COLOR PALETTE:
- Military Green Primary: #0B5345
- Success Green: #138D75  
- Accent Orange: #E67E22
- Light backgrounds: #ECF0F1, #FFFFFF
- Text colors: #2C3E50, #7F8C8D

LAYOUT STRUCTURE:
- Clean header with "Waajal Ëlëk" logo and user info
- Horizontal tab navigation: "Mon Compte | Mes Cotisations | Simulations | Documents"
- Centered content area with personal dashboard cards

MAIN CONTENT SECTIONS:

1. HERO CARD (prominent, full-width):
   - Military avatar with rank insignia
   - "Sergeant-Chef DIALLO Mamadou - 3ème RIAOM"
   - Large display: "2,847 POINTS" 
   - Estimated value: "2,403,429 FCFA"
   - Pension projection: "186,500 FCFA/mois à 55 ans"
   - Prominent CTA button: "SIMULER MA RETRAITE"

2. SAVINGS EVOLUTION CHART:
   - Line/area chart showing point accumulation over 5 years
   - Green gradient fill under the curve
   - Monthly data points with tooltips
   - Y-axis: Points acquired, X-axis: Time period

3. RECENT CONTRIBUTIONS TABLE:
   - Clean, minimal table design
   - 5 latest contributions with: Date | Amount | Points | Status
   - Status badges with colors (green=processed, orange=pending)

4. QUICK ACTIONS (3 cards row):
   - "Modifier cotisations" with settings icon
   - "Attestation PDF" with download icon  
   - "Support conseiller" with chat icon

DESIGN CHARACTERISTICS:
- Personal, welcoming interface feel
- Military professional aesthetic but user-friendly
- Clear hierarchy with the most important info prominent
- French language throughout
- Security indicators (padlock icons, "Sécurisé" badges)
- Progress indicators showing retirement readiness
- Motivational design elements
- Clean typography with good readability
- Card-based layout with subtle shadows

USER EXPERIENCE ELEMENTS:
- Clear value proposition displayed prominently
- Easy access to key actions
- Visual progress towards retirement goals
- Trustworthy, secure appearance
- Personal touch with military rank/unit display

OUTPUT: Professional member portal interface mockup, desktop version
```