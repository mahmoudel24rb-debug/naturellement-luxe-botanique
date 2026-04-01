# Plan Version B — Redesign Organique / Botanique

## Contexte
Ce projet est une **copie du site Naturellement Luxe** avec un **redesign complet** de la charte graphique. On garde le même contenu (textes, structure des pages, prestations, tarifs, etc.) mais on transforme entièrement l'identité visuelle vers un style organique et botanique. Les fichiers sont déjà en local.

---

## Direction artistique

**Mots-clés :** Nature, organique, douceur, vivant, botanique, artisanal, chaleureux, terreux.

L'idée est de passer d'un style "luxe classique noir & or" à un style "luxe naturel" — comme un spa niché dans une forêt ou un jardin botanique. Des formes douces, des couleurs terreuses, des courbes partout, zéro angle agressif.

---

## 1. Nouvelle palette de couleurs

| Rôle | Hex | Description |
|---|---|---|
| Fond principal | `#F7F3ED` | Blanc crème chaud (lin naturel) |
| Fond secondaire | `#EDE7DC` | Beige sable doux |
| Couleur primaire | `#4A6741` | Vert forêt / sauge foncé |
| Couleur secondaire | `#C17C4E` | Terracotta chaud |
| Accent | `#D4A574` | Caramel / miel doré |
| Texte principal | `#2C2418` | Brun très foncé (quasi noir mais chaud) |
| Texte secondaire | `#6B5D4F` | Brun moyen |
| Fond sections sombres | `#2C2418` | Brun nuit |
| Fond cartes / éléments accent | `#4A6741` | Vert forêt |
| Bordures | `#C8BBA8` | Beige moyen |
| Hover | `#5C7D52` | Vert plus lumineux |

---

## 2. Nouvelles typographies

Remplacer les polices actuelles par :

- **Titres :** `"Playfair Display"` en italic — élégant, organique, avec du caractère. Import Google Fonts.
- **Sous-titres / accents :** `"Cormorant Garamond"` — serif raffiné et léger.
- **Corps de texte :** `"DM Sans"` — sans-serif lisible, moderne et doux.

```css
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=DM+Sans:wght@300;400;500;700&display=swap');
```

---

## 3. Formes et mise en page — Style organique

### Border-radius généreux partout
- Cartes de prestations : `border-radius: 24px` au lieu de coins droits ou légèrement arrondis
- Images dans les cartes : `border-radius: 20px`
- Boutons : `border-radius: 50px` (pill) — garder le style arrondi mais avec les nouvelles couleurs
- Sections : ajouter des coins arrondis aux conteneurs principaux

### Séparateurs de sections en vague (wave dividers)
Entre les grandes sections de chaque page, ajouter des séparateurs SVG en forme de vague organique au lieu de lignes droites. Exemple :

```html
<div class="wave-divider">
  <svg viewBox="0 0 1440 100" preserveAspectRatio="none">
    <path d="M0,40 C360,100 720,0 1080,60 C1260,80 1380,20 1440,40 L1440,100 L0,100 Z" fill="currentColor"/>
  </svg>
</div>
```

Utiliser ces vagues pour faire la transition entre les sections à fond clair et fond sombre (et inversement). La couleur du SVG doit correspondre au fond de la section suivante.

### Éléments décoratifs botaniques
Ajouter des SVG décoratifs discrets de feuilles ou branches dans certaines sections (en `position: absolute`, `opacity: 0.08-0.12`, en arrière-plan). Par exemple :
- Une feuille stylisée en haut à droite de la section hero
- Une branche fine en bas à gauche de la section prestations
- Ce sont des éléments purement décoratifs, subtils, pas envahissants

### Ombres douces
Remplacer les ombres actuelles (si existantes) par des ombres très douces et chaudes :
```css
box-shadow: 0 8px 32px rgba(44, 36, 24, 0.08);
```

---

## 4. Boutons — Style organique

Tous les boutons gardent le style pill arrondi mais avec l'identité botanique :

### Bouton principal (remplace `.btn-dark` et `.btn-primary`)
```css
background: #4A6741;
color: #F7F3ED;
border-radius: 50px;
border: none;
padding: 14px 36px;
font-family: 'DM Sans', sans-serif;
font-weight: 500;
letter-spacing: 1.5px;
text-transform: uppercase;
transition: all 0.3s ease;
```
Hover : `background: #5C7D52;` avec un léger `transform: translateY(-2px)` et `box-shadow: 0 6px 20px rgba(74, 103, 65, 0.25);`

### Bouton secondaire / outline (remplace `.btn-ghost`, `.btn-outline`)
```css
background: transparent;
color: #4A6741;
border: 1.5px solid #4A6741;
border-radius: 50px;
```
Hover : fond `#4A6741`, texte `#F7F3ED`

### Bouton sur fond sombre
```css
background: #D4A574;
color: #2C2418;
border-radius: 50px;
```
Hover : `background: #C17C4E;`

---

## 5. Header

- Fond : `#F7F3ED` (crème) ou semi-transparent avec `backdrop-filter: blur(10px)`
- Logo "Naturellement Luxe" : utiliser `Playfair Display` italic, couleur vert forêt `#4A6741`
- Liens navigation : `DM Sans`, couleur brun foncé `#2C2418`, hover en vert `#4A6741`
- Bouton "Réserver" : style pill vert forêt (bouton principal ci-dessus)

---

## 6. Cartes de prestations (page prestations)

- Fond des cartes : `#FFFFFF` ou `#F7F3ED` avec ombres douces
- Bordure : `1px solid #C8BBA8` avec `border-radius: 24px`
- Images : `border-radius: 20px 20px 0 0` (arrondies en haut)
- Titres des cartes : `Cormorant Garamond`, couleur brun foncé
- Badge "POPULAIRE" : fond terracotta `#C17C4E`, texte crème, `border-radius: 20px`

---

## 7. Page tarifs

- Tableaux sur fond sombre : fond `#2C2418` (brun nuit) au lieu de noir pur
- Prix : couleur terracotta `#C17C4E` ou accent caramel `#D4A574`
- Cartes packages : bordures arrondies `24px`, carte "Populaire" avec fond vert forêt `#4A6741`
- Boutons "Réserver" : style pill adapté au fond

---

## 8. Section CTA ("Prêt pour votre moment de détente ?")

- Fond : dégradé doux du vert forêt vers un vert plus clair, ou fond terracotta doux
- Texte : crème `#F7F3ED`
- Bouton : pill crème sur fond vert, ou pill terracotta

---

## 9. Page carte cadeau

- Cartes des formules : fond crème avec bordure verte, `border-radius: 24px`
- Carte "Populaire" : fond vert forêt, texte crème
- Icônes : couleur vert forêt ou terracotta
- Formulaire : inputs avec `border-radius: 12px`, bordures beige, focus en vert

---

## 10. Page contact

- Section "Comment venir" : conteneur compact et arrondi (`border-radius: 20px`), fond brun nuit `#2C2418` ou simplement une bordure verte avec fond crème
- Formulaire de contact : même style que carte cadeau, inputs arrondis et doux

---

## 11. Footer

- Fond : brun nuit `#2C2418`
- Texte : beige `#C8BBA8`
- Liens : hover en vert sauge ou terracotta
- Ajouter un wave divider au-dessus du footer

---

## Fichiers à modifier

| Fichier | Modifications |
|---|---|
| CSS global | Palette complète, typographies, border-radius, ombres, boutons, wave dividers |
| Toutes les pages HTML | Ajouter les imports Google Fonts, les wave dividers SVG entre sections, les éléments décoratifs botaniques |
| `index.html` | Header, hero, sections |
| `prestations.html` | Cartes, boutons |
| `tarifs.html` | Tableaux, packages, boutons |
| `carte-cadeau.html` | Formules, formulaire |
| `contact.html` | Map/fallback, formulaire |

---

## Règles importantes

- **Garder tout le contenu textuel identique** (textes, prix, descriptions, adresses)
- **Garder la même structure de pages** et navigation
- **Ne pas changer les images** (elles fonctionnent avec n'importe quelle palette naturelle)
- **Tester chaque page visuellement** pour s'assurer qu'il n'y a aucun résidu de l'ancien style noir/doré
- Le résultat doit donner l'impression d'un site designé de zéro avec cette identité organique, pas d'un simple recoloriage
