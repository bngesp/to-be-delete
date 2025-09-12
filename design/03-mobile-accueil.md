# Application Mobile - Écran d'Accueil

## Description de l'Interface

L'écran d'accueil mobile de Waajal Ëlëk est optimisé pour un accès rapide aux informations essentielles. Design mobile-first avec navigation tactile intuitive et informations prioritaires immédiatement visibles.

## Spécifications Techniques

### Dimensions et Layout

**Format** : iPhone 14/15 (393x852px) et Android équivalent
**Safe Areas** : Respect des zones sécurisées iOS/Android
**Orientation** : Portrait uniquement pour cette interface

### Structure de l'Écran

**Status Bar et Header (120px total)**
- Status bar système (44px)
- Header app (76px) :
  - Logo Waajal Ëlëk compact (gauche)
  - Notifications badge (droite)
  - Indicateur connexion sécurisée

**Carte de Bienvenue** (180px)
- Background dégradé vert militaire
- "Bonjour Sergent FALL" en blanc
- Dernière connexion et statut compte
- Icône avatar/grade stylisée

**Solde Principal** (160px)
- Card blanche avec ombre
- "Mon Solde Retraite" (titre)
- Montant principal : "2,847 POINTS" (grande typographie)
- Valeur estimée : "2,403,429 FCFA" (sous-texte)
- Variation du mois : "+47 points" (vert, avec flèche)

**Actions Rapides** (2x2 grille, 200px total)
- Boutons larges avec icônes et labels :
  - "Cotiser" (icône + vert)
  - "Simuler" (icône graphique orange) 
  - "Documents" (icône PDF gris)
  - "Support" (icône chat bleu)

**Activité Récente** (liste scrollable)
- "Dernières opérations" (titre section)
- 3-4 items visibles avec swipe pour plus
- Format : Date | Description | Montant/Points | Icône status

**Navigation Bottom** (80px avec safe area)
- Tab bar avec 5 icônes :
  - Accueil (actif) | Compte | Cotisations | Simulations | Plus
- Indicateur actif avec dot vert au-dessus
- Labels sous les icônes

### Éléments Interactifs

**Pull-to-Refresh**
- Indicateur de rafraîchissement en haut
- Animation de loading avec logo Waajal

**Swipe Gestures**
- Swipe horizontal sur activité récente
- Swipe pour actions rapides sur transactions

**Touch Feedback**
- Haptic feedback sur boutons principaux
- États pressed avec légère opacité
- Bounce animation sur boutons actions

### Notifications Push

**Badge de notification**
- Nombre en rouge sur l'icône notification
- Types : Nouvelles cotisations, alertes, messages

**In-App Notifications**
- Banners en haut d'écran pour infos importantes
- Auto-dismiss après 3 secondes
- Swipe pour dismisser manuellement

### States et Interactions

**Loading States**
- Skeleton screens pour chargement données
- Shimmer effect sur les cartes de contenu
- Loading spinner minimal sur actions

**Error States**  
- Messages d'erreur avec retry button
- Offline mode avec données en cache
- Indicateur de connectivité réseau

---

## Prompt IA pour Génération

```
Design a mobile app home screen for "Waajal Ëlëk" - a military pension mobile application for Senegalese armed forces.

DEVICE SPECIFICATIONS:
- iPhone 14 format (393x852px)
- iOS design patterns and safe areas
- Portrait orientation only
- Touch-optimized interface

COLOR SCHEME:
- Military Green: #0B5345 (primary brand color)
- Accent Green: #138D75
- Success Green: #27AE60
- Orange Accent: #E67E22 (Senegal flag)
- White cards: #FFFFFF
- Background: #F8F9FA
- Text: #2C3E50, #7F8C8D

SCREEN LAYOUT (top to bottom):

1. HEADER SECTION (76px):
   - "Waajal Ëlëk" logo (left)
   - Notification bell with red badge "3" (right)
   - Secure connection indicator (small padlock icon)

2. WELCOME CARD (180px):
   - Gradient green background (#0B5345 to #138D75)
   - "Bonjour Sergent FALL" in white text
   - Small avatar with military rank insignia
   - "Dernière connexion: Aujourd'hui 08:45"

3. BALANCE CARD (160px):
   - White card with subtle shadow
   - "Mon Solde Retraite" title
   - Large number: "2,847 POINTS" (prominent display)
   - Subtitle: "Valeur: 2,403,429 FCFA"
   - Change indicator: "+47 points ce mois" (green with up arrow)

4. QUICK ACTIONS GRID (200px):
   - 2x2 grid of large touch buttons
   - "Cotiser" with money icon (green background)
   - "Simuler" with chart icon (orange background)  
   - "Documents" with PDF icon (gray background)
   - "Support" with chat icon (blue background)

5. RECENT ACTIVITY (scrollable list):
   - "Dernières opérations" section title
   - 3-4 transaction items visible
   - Each item: Date | Description | Amount | Status icon
   - "Voir plus" link at bottom

6. BOTTOM TAB BAR (80px):
   - 5 tabs: Accueil | Compte | Cotisations | Simulations | Plus
   - Current tab (Accueil) highlighted with green dot above
   - Clean icons with labels underneath

DESIGN CHARACTERISTICS:
- Mobile-first, touch-friendly design
- Clean, minimal interface with clear hierarchy  
- French language interface
- Military professional but accessible
- High contrast for readability
- Large touch targets (44px minimum)
- Card-based layout with rounded corners
- Subtle shadows and modern iOS/Material design patterns
- Loading states and skeleton screens consideration

INTERACTIVE ELEMENTS:
- Pull-to-refresh indicator at top
- Haptic feedback indicators
- Smooth animations and transitions
- Status badges with semantic colors
- Progressive disclosure of information

OUTPUT: High-resolution mobile app home screen mockup optimized for presentation
```