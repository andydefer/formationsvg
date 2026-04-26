# Module 1 – Introduction, mise en place et accessibilité

**Objectif** : Installer l'environnement, comprendre les bases et intégrer l'accessibilité dès le départ.

---

## 1. SVG vs Canvas (vectoriel vs bitmap, cas d'usage)

### 1.1. SVG : scalable, DOM accessible, idéal pour icônes, graphiques, cartes

**SVG** (Scalable Vector Graphics) est un format d'image vectoriel basé sur XML.

```svg
<svg width="200" height="200" viewBox="0 0 200 200">
    <circle cx="100" cy="100" r="50" fill="blue" />
</svg>
```

**Caractéristiques :**
- **Vectoriel** : les formes sont définies par des équations mathématiques
- **DOM accessible** : chaque élément devient un nœud HTML manipulable
- **Redimensionnement infini** : pas de perte de qualité
- **Accessible** : peut contenir des titres et descriptions

**Cas d'usage :**
- Icônes et logos
- Graphiques et diagrammes
- Cartes vectorielles
- Plans de salle interactifs

### 1.2. Canvas : pixels, haute performance, idéal pour jeux, filtres, animations

**Canvas** est une zone de dessin bitmap pilotée par JavaScript.

```html
<canvas id="monCanvas" width="200" height="200"></canvas>
<script>
    const ctx = document.getElementById('monCanvas').getContext('2d');
    ctx.fillStyle = 'red';
    ctx.fillRect(0, 0, 200, 200);
</script>
```

**Caractéristiques :**
- **Bitmap** : grille de pixels
- **Performant** : idéal pour des milliers d'objets
- **Manipulation pixels** : accès direct via `getImageData()`
- **Non accessible** : le DOM ne connaît pas les formes

**Cas d'usage :**
- Jeux vidéo
- Filtres d'images
- Animations complexes
- Visualisations de données volumineuses

### 1.3. Quand choisir l'un ou l'autre

| Critère | SVG | Canvas |
|---------|-----|--------|
| Accessibilité | ✅ Excellente | ❌ Mauvaise |
| Scalabilité | ✅ Parfaite | ❌ Flou si agrandi |
| Performance (1000+ éléments) | ❌ Lente | ✅ Rapide |
| Manipulation pixels | ❌ Impossible | ✅ Possible |
| SEO / Indexation | ✅ Oui | ❌ Non |

**Règle simple :**
- Accessibilité + interactivité → **SVG**
- Performance + animations → **Canvas**

---

## 2. Structure HTML de base et intégration

### 2.1. Balise `<svg>` : attributs `width`, `height`, `viewBox`

La balise `<svg>` est le conteneur de tout graphique SVG.

```html
<svg 
    width="300" 
    height="200" 
    viewBox="0 0 300 200"
    xmlns="http://www.w3.org/2000/svg"
>
    <!-- Contenu SVG -->
</svg>
```

#### `width` et `height` – Dimensions d'affichage

| Unité | Exemple | Effet |
|-------|---------|-------|
| Pixels | `width="300"` | Taille fixe |
| Pourcentage | `width="100%"` | S'adapte au parent |
| Auto | `height="auto"` | Maintient les proportions |

#### `viewBox` – Le système de coordonnées interne (À MAÎTRISER ABSOLUMENT)

`viewBox` est le concept le plus important de SVG. Il crée un **système de coordonnées virtuel** indépendant de la taille d'affichage.

**Syntaxe :** `viewBox="minX minY largeur hauteur"`

| Paramètre | Rôle | Exemple |
|-----------|------|---------|
| `minX` | Coin supérieur gauche (X) | `0` |
| `minY` | Coin supérieur gauche (Y) | `0` |
| `largeur` | Largeur du système virtuel | `100` |
| `hauteur` | Hauteur du système virtuel | `100` |

---

## 📐 viewBox – Explication détaillée

### Problème sans `viewBox`

```svg
<!-- Sans viewBox : coordonnées = pixels -->
<svg width="200" height="100">
    <!-- Ce rectangle apparaît à x=10, y=10 pixels -->
    <rect x="10" y="10" width="80" height="40" fill="red" />
</svg>
```

**Problème :** Si je change `width="400" height="200"`, le rectangle devient plus grand car les coordonnées sont en pixels absolus.

### Solution avec `viewBox`

```svg
<!-- Avec viewBox : système de coordonnées virtuel -->
<svg width="200" height="100" viewBox="0 0 100 50">
    <!-- Dans le monde virtuel : x=10, y=10, largeur=80, hauteur=40 -->
    <!-- Ce monde mesure 100x50 unités virtuelles -->
    <rect x="10" y="10" width="80" height="40" fill="red" />
</svg>
```

**Maintenant :** Si je change `width="400" height="200"`, le rectangle occupe toujours 80% de la largeur et 80% de la hauteur.

---

### Fonctionnement interne de `viewBox`

```
viewBox = "0 0 100 50"

Monde virtuel (viewBox)         Monde réel (affichage)
┌─────────────────────┐         ┌─────────────────────────┐
│ (0,0)               │         │ (0,0)                   │
│  ┌────────┐         │  ────→  │   ┌──────────────┐      │
│  │ 80x40  │         │         │   │    (zoom     │      │
│  └────────┘         │         │   │   automatique)│      │
│               (100) │         │               (width) │
└─────────────────────┘         └─────────────────────────┘
    100 unités virtuelles             200 pixels (par exemple)
```

**Ce qui se passe :**
1. SVG crée un monde virtuel de `100x50` unités
2. Le rectangle fait `80x40` dans ce monde (donc 80% de la largeur)
3. Le navigateur **zoome automatiquement** ce monde pour remplir `200x100` pixels
4. Le rectangle occupe toujours 80% de l'espace, quelle que soit la taille d'affichage

---

### Exemples concrets de `viewBox`

#### Exemple 1 : viewBox carré dans un rectangle

```svg
<!-- viewBox carré 100x100 affiché dans un rectangle 200x100 -->
<svg width="200" height="100" viewBox="0 0 100 100">
    <!-- Le cercle utilise les coordonnées 100x100 -->
    <circle cx="50" cy="50" r="40" fill="blue" />
</svg>
```

**Résultat :** Le cercle est déformé horizontalement car le monde 100x100 est étiré en 200x100.

#### Exemple 2 : Même viewBox, tailles différentes

```svg
<!-- Affichage 100x100 -->
<svg width="100" height="100" viewBox="0 0 100 100">
    <rect x="25" y="25" width="50" height="50" fill="red" />
</svg>

<!-- Affichage 200x200 -->
<svg width="200" height="200" viewBox="0 0 100 100">
    <rect x="25" y="25" width="50" height="50" fill="red" />
</svg>
```

**Résultat :** Les deux rectangles ont les mêmes proportions. Le deuxième est simplement deux fois plus grand.

#### Exemple 3 : viewBox décalée

```svg
<!-- viewBox qui commence à (-50,-50) -->
<svg width="200" height="200" viewBox="-50 -50 100 100">
    <!-- L'origine (0,0) est maintenant au centre -->
    <circle cx="0" cy="0" r="40" fill="green" />
    <rect x="-25" y="-25" width="50" height="50" fill="orange" />
</svg>
```

**Utilité :** Permet de centrer le système de coordonnées.

#### Exemple 4 : viewBox plus grande que l'affichage

```svg
<!-- viewBox 200x200 dans un affichage 100x100 -->
<svg width="100" height="100" viewBox="0 0 200 200">
    <!-- Le rectangle fait 100x100 dans un monde 200x200 (donc 50% de la largeur) -->
    <rect x="50" y="50" width="100" height="100" fill="purple" />
</svg>
```

**Résultat :** Le rectangle prend 50% de l'espace (car 100/200 = 0.5), affiché sur 100x100 pixels → 50x50 pixels.

---

### Résumé visuel des transformations

| viewBox | width/height | Effet |
|---------|--------------|-------|
| `0 0 100 100` | `200 200` | Zoom ×2 |
| `0 0 100 100` | `50 50` | Zoom ×0.5 |
| `0 0 200 100` | `100 100` | Étirement horizontal |
| `-50 -50 100 100` | `100 100` | Décalage (centre à 0,0) |

---

### `preserveAspectRatio` – Contrôler l'adaptation

`preserveAspectRatio` contrôle comment l'image s'adapte quand les proportions viewBox ≠ proportions d'affichage.

**Syntaxe :** `preserveAspectRatio="[alignement] [meet|slice]"`

| Valeur | Effet |
|--------|-------|
| `meet` (défaut) | L'image tient entièrement, peut laisser des bandes |
| `slice` | L'image remplit tout, peut être coupée |
| `none` | L'image se déforme pour remplir |

**Alignements possibles :**
- `xMinYMin` : coin supérieur gauche
- `xMidYMid` : centré (défaut)
- `xMaxYMax` : coin inférieur droit

```svg
<!-- Centré, bandes possibles -->
<svg viewBox="0 0 100 100" width="200" height="100" preserveAspectRatio="xMidYMid meet">

<!-- Remplit tout, même coupé -->
<svg viewBox="0 0 100 100" width="200" height="100" preserveAspectRatio="xMidYMid slice">

<!-- Déformation autorisée -->
<svg viewBox="0 0 100 100" width="200" height="100" preserveAspectRatio="none">
```

---

### Bonnes pratiques `viewBox`

```svg
<!-- ✅ BON : viewBox carré pour icônes réutilisables -->
<svg viewBox="0 0 24 24" width="24" height="24">
    <path d="M12 2L2 7l10 5 10-5-10-5z"/>
</svg>

<!-- ✅ BON : viewBox adaptée au contenu -->
<svg viewBox="0 0 800 600">
    <!-- Dessin au format 4:3 -->
</svg>

<!-- ❌ MAUVAIS : pas de viewBox = pas responsive -->
<svg width="100%">
    <!-- Les coordonnées sont en pixels -->
</svg>

<!-- ❌ MAUVAIS : viewBox trop grande -->
<svg viewBox="0 0 10000 10000">
    <!-- Coordonnées gigantesques = mauvaise performance -->
</svg>
```

**Règle d'or :** Toujours définir `viewBox`. C'est ce qui rend le SVG responsive.

---

### 2.2. Balise `<canvas>` : attributs `width`, `height` (taille réelle vs CSS)

```html
<canvas id="monCanvas" width="500" height="400"></canvas>
```

#### Différence cruciale

| Attribut | Rôle | Unité |
|----------|------|-------|
| `width`/`height` HTML | Résolution réelle (buffer de pixels) | pixels |
| `width`/`height` CSS | Taille d'affichage | pixels ou % |

```html
<!-- ⚠️ MAUVAIS : déformation -->
<canvas width="100" height="100" style="width: 400px; height: 400px"></canvas>

<!-- ✅ BON : dimensions identiques -->
<canvas width="400" height="400" style="width: 400px; height: 400px"></canvas>

<!-- ✅ BON : responsive sans déformation -->
<canvas width="800" height="600" style="width: 100%; height: auto"></canvas>
```

**Vérification en JavaScript :**
```javascript
const canvas = document.getElementById('monCanvas');
console.log('Résolution réelle :', canvas.width, canvas.height);
console.log('Taille affichée :', canvas.clientWidth, canvas.clientHeight);
```

### 2.3. Accès au contexte 2D : `canvas.getContext('2d')`

```javascript
const canvas = document.getElementById('monCanvas');
const ctx = canvas.getContext('2d');

if (!ctx) {
    console.error('Canvas 2D non supporté');
}
```

`ctx` est l'objet qui contient toutes les méthodes de dessin.

---

## 3. Premier rectangle (SVG/Canvas)

### 3.1. `<rect x="10" y="10" width="100" height="50" fill="red" />`

**Attributs de `<rect>` :**

| Attribut | Description | Exemple |
|----------|-------------|---------|
| `x` | Position horizontale | `x="10"` |
| `y` | Position verticale | `y="10"` |
| `width` | Largeur | `width="100"` |
| `height` | Hauteur | `height="50"` |
| `fill` | Couleur de remplissage | `fill="red"` |
| `stroke` | Couleur de bordure | `stroke="black"` |
| `stroke-width` | Épaisseur de bordure | `stroke-width="2"` |
| `rx`/`ry` | Coins arrondis | `rx="5"` |

**Exemple complet :**
```svg
<svg viewBox="0 0 200 100">
    <rect x="10" y="10" width="100" height="50" fill="red" stroke="black" stroke-width="2" rx="5"/>
</svg>
```

### 3.2. `ctx.fillRect(10, 10, 100, 50)`

**Méthodes rectangle Canvas :**

| Méthode | Description |
|---------|-------------|
| `fillRect(x, y, w, h)` | Rectangle rempli |
| `strokeRect(x, y, w, h)` | Rectangle avec bordure |
| `clearRect(x, y, w, h)` | Efface une zone |

**Exemple complet :**
```javascript
const canvas = document.getElementById('monCanvas');
canvas.width = 200;
canvas.height = 100;
const ctx = canvas.getContext('2d');

ctx.fillStyle = 'red';
ctx.fillRect(10, 10, 100, 50);

ctx.strokeStyle = 'black';
ctx.strokeRect(10, 10, 100, 50);
```

---

## 4. Accessibilité minimale

### 4.1. SVG : `role="img"`, `<title>`, `<desc>`, `aria-label`

```svg
<svg 
    width="200" 
    height="200" 
    viewBox="0 0 200 200"
    role="img"
    aria-labelledby="titre description"
>
    <title id="titre">Graphique des ventes</title>
    <desc id="description">Barres montrant une augmentation des ventes</desc>
    
    <rect x="10" y="100" width="40" height="80" fill="blue" />
    <rect x="60" y="50" width="40" height="130" fill="green" />
    <rect x="110" y="20" width="40" height="160" fill="red" />
</svg>
```

**Règles SVG :**
- `role="img"` : indique que c'est une image
- `<title>` : titre court (lu par lecteurs d'écran)
- `<desc>` : description détaillée
- `aria-labelledby` : relie le SVG aux titres

### 4.2. Canvas : `aria-label` sur l’élément, gestion focus manuelle avec `tabindex`

```html
<canvas 
    id="monCanvas"
    width="400" 
    height="300"
    role="img"
    aria-label="Graphique des ventes montrant une progression"
    tabindex="0"
>
    Texte alternatif : Ventes : janvier 10, février 15, mars 25
</canvas>
```

**Gestion du focus :**
```javascript
const canvas = document.getElementById('monCanvas');

canvas.addEventListener('keydown', (event) => {
    if (event.key === 'ArrowLeft') {
        // Action
        event.preventDefault();
    }
});
```

```css
canvas:focus {
    outline: 3px solid #0066cc;
    outline-offset: 2px;
}
```

### 4.3. Fournir des descriptions alternatives dans le DOM

```html
<figure>
    <canvas id="graphCanvas" width="500" height="300" tabindex="0">
        Texte alternatif : Graphique des performances
    </canvas>
    <figcaption>Évolution des performances sur l'année</figcaption>
</figure>
```

---

## TP final

**Énoncé :**
Créez une page HTML avec :
1. Un carré rouge SVG accessible (titre, description, focus clavier)
2. Un carré bleu Canvas accessible (aria-label, tabindex)
3. Test de navigation clavier entre les deux

**Éléments obligatoires :**
- SVG : `viewBox="0 0 100 100"`, `width="150" height="150"`, `role="img"`, `tabindex="0"`
- Canvas : `width="150" height="150"`, `role="img"`, `aria-label`, `tabindex="0"`

---

### Correction :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>TP Module 1 - SVG et Canvas accessibles</title>
    <style>
        .focusable:focus {
            outline: 3px solid #0066cc;
            outline-offset: 4px;
        }
        
        .container {
            display: flex;
            gap: 40px;
            padding: 40px;
            justify-content: center;
        }
        
        .card {
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Carré Rouge SVG -->
        <div class="card">
            <h2>SVG - Carré Rouge</h2>
            <svg 
                width="150" 
                height="150" 
                viewBox="0 0 100 100"
                role="img"
                aria-labelledby="svgTitle svgDesc"
                tabindex="0"
                class="focusable"
            >
                <title id="svgTitle">Carré Rouge SVG</title>
                <desc id="svgDesc">Un carré rouge de 80x80 unités dans un système 100x100</desc>
                <rect x="10" y="10" width="80" height="80" fill="red" stroke="darkred" stroke-width="2"/>
            </svg>
            <p>viewBox="0 0 100 100"</p>
        </div>
        
        <!-- Carré Bleu Canvas -->
        <div class="card">
            <h2>Canvas - Carré Bleu</h2>
            <canvas 
                id="blueCanvas"
                width="150" 
                height="150"
                role="img"
                aria-label="Carré bleu Canvas de 110x110 pixels"
                tabindex="0"
                class="focusable"
            >
                Texte alternatif : Carré bleu de 110x110 pixels
            </canvas>
            <p>width="150" height="150" (attributs HTML)</p>
        </div>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const canvas = document.getElementById('blueCanvas');
            const ctx = canvas.getContext('2d');
            
            // Dessiner le carré bleu
            ctx.fillStyle = '#2563eb';
            ctx.fillRect(20, 20, 110, 110);
            
            // Bordure
            ctx.strokeStyle = '#1e40af';
            ctx.strokeRect(20, 20, 110, 110);
            
            // Texte
            ctx.fillStyle = 'white';
            ctx.font = 'bold 14px Arial';
            ctx.textAlign = 'center';
            ctx.fillText('Canvas', 75, 80);
            
            // Gestion clavier
            canvas.addEventListener('keydown', function(e) {
                if (e.key === 'Enter' || e.key === ' ') {
                    alert('Canvas focalisé !');
                    e.preventDefault();
                }
            });
        });
    </script>
</body>
</html>
```

---

## Récapitulatif des acquis

À la fin de ce module, vous savez :

- ✅ Différence entre SVG (vectoriel) et Canvas (bitmap)
- ✅ Utiliser `viewBox` = système de coordonnées virtuel
- ✅ Comprendre le zoom automatique de `viewBox` vers l'affichage
- ✅ Configurer correctement `width`/`height` Canvas (attributs HTML, pas CSS)
- ✅ Rendre un SVG accessible avec `role="img"`, `<title>`, `<desc>`
- ✅ Rendre un Canvas focalisable avec `tabindex="0"`
- ✅ Gérer le focus clavier avec CSS `:focus`

---

➡️ **Module 2 :** Bases du SVG (formes, styles) et approfondissement responsive

**Félicitations !** Vous maîtrisez le concept fondamental de `viewBox` qui rend le SVG responsive. 🎨
