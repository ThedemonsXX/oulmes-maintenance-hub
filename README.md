# oulmes-maintenance-hub

> Interface web de gestion des pannes et solutions pour les machines de la ligne de production du site Oulmes.

---

## Aperçu

**oulmes-maintenance-hub** est une page web responsive, entièrement en français, conçue pour les techniciens et agents de maintenance du site Oulmes. Elle centralise, pour chaque machine de la ligne, la liste des pannes répertoriées, leurs causes possibles et les actions correctives à appliquer — le tout accessible en quelques clics, sans connexion à une base de données ni framework JavaScript.

---

## Machines couvertes

| Machine | Pannes répertoriées |
|---|---|
| Souffleuse & Soutireuse | 7 |
| Big Buffer | 7 |
| Poigneteuse | 7 |
| Étiqueteuse | 7 |
| Fardeleuse | 7 |

---

## Fonctionnalités

- **Navigation fixe** en haut de page avec liens d'ancrage vers chaque machine et surlignage actif au scroll
- **Logo Oulmes** en haut à gauche, configurable via l'attribut `src`
- **Cartes machines** avec image, métadonnées et bouton d'action
- **Panneau de pannes dépliable** — cliquer sur *Afficher les problèmes* révèle la liste des pannes numérotées
- **Popup de solution** — chaque panne dispose d'un bouton *Afficher solution* qui ouvre une modale avec les causes (fond rouge) et l'action corrective (fond vert)
- **Fermeture modale** par clic en dehors, bouton ✕ ou touche `Échap`
- **Images uniformes** — même taille pour toutes les machines, avec placeholder automatique si l'image est absente
- **Entièrement responsive** — mobile, tablette et desktop

---

## Structure du projet

```
oulmes-maintenance-hub/
├── index.html           # Page principale (tout-en-un : HTML + CSS + JS)
├── README.md
└── images/
    ├── oulmes-logo.png  # Logo Oulmes (à fournir)
    ├── souffleuse.jpg
    ├── bigbuffer.jpg
    ├── poigneteuse.jpg
    ├── etiqueteuse.jpg
    └── fardeleuse.jpg
```

> Le projet est un fichier HTML unique sans dépendance externe à installer. Seule la police Google Fonts (Inter + DM Sans) est chargée via CDN.

---

## Installation & utilisation

### 1. Cloner le dépôt

```bash
git clone https://github.com/votre-org/oulmes-maintenance-hub.git
cd oulmes-maintenance-hub
```

### 2. Ajouter les images

Placez vos images dans le dossier `images/` en respectant les noms suivants, ou modifiez directement les attributs `src` dans `index.html` :

| Fichier attendu | Machine |
|---|---|
| `images/oulmes-logo.png` | Logo dans la navbar |
| `images/souffleuse.jpg` | Souffleuse & Soutireuse |
| `images/bigbuffer.jpg` | Big Buffer |
| `images/poigneteuse.jpg` | Poigneteuse |
| `images/etiqueteuse.jpg` | Étiqueteuse |
| `images/fardeleuse.jpg` | Fardeleuse |

Si une image est absente, un placeholder gris s'affiche automatiquement — aucune erreur visible.

### 3. Configurer le logo

Dans `index.html`, localisez la ligne suivante et remplacez la valeur de `src` :

```html
<img src="YOUR_OULMES_LOGO_SRC_HERE" alt="Oulmes" ... />
```

Par exemple :

```html
<img src="images/oulmes-logo.png" alt="Oulmes" ... />
```

### 4. Ouvrir dans le navigateur

Aucun serveur requis pour un usage local :

```bash
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Pour un déploiement en réseau interne ou sur un serveur web, copiez simplement le dossier sur votre serveur (Apache, Nginx, IIS, etc.).

---

## Personnalisation

### Ajouter une panne

Dans `index.html`, repérez le panneau de la machine concernée (`id="panel-nomMachine"`) et ajoutez un bloc `.problem-row` :

```html
<div class="problem-row">
  <div class="problem-num">8</div>
  <div class="problem-text">Intitulé de la nouvelle panne</div>
  <button class="btn-solution" onclick="openModal(
    'Nom Machine',
    'Intitulé de la nouvelle panne',
    'Cause possible ici',
    'Action corrective ici'
  )">
    <svg>...</svg>
    Afficher solution
  </button>
</div>
```

### Ajouter une machine

1. Créer une nouvelle `<section class="machine-section" id="nomMachine">` en suivant le même patron que les sections existantes
2. Ajouter un lien dans la `<ul class="nav-links">` de la navbar :

```html
<li><a href="#nomMachine"><span class="nav-dot"></span>Nom Machine</a></li>
```

### Modifier les couleurs

Les couleurs sont centralisées dans les variables CSS en haut du `<style>` :

```css
:root {
  --blue-deep:   #0a2540;
  --blue-accent: #2770c8;
  --teal:        #0eb5a0;
  /* ... */
}
```

---

## Technologies

- HTML5 / CSS3 (variables CSS, Flexbox, Grid, media queries)
- JavaScript vanilla (aucune dépendance)
- [Google Fonts](https://fonts.google.com/) — Inter & DM Sans

---

## Compatibilité navigateurs

| Navigateur | Support |
|---|---|
| Chrome / Edge 90+ | ✅ |
| Firefox 88+ | ✅ |
| Safari 14+ | ✅ |
| Mobile Chrome / Safari | ✅ |

---

## Licence

Usage interne Oulmes — tous droits réservés.
