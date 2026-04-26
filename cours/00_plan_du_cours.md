# Plan de cours complet – SVG & Canvas (Graphiques Web avancés)

**Public cible** : Développeurs web débutants ou ayant des bases HTML/CSS/JS  
**Prérequis** : Notions de base de JavaScript (variables, fonctions, événements)  
**Environnement** : VS Code (ou tout éditeur) + navigateur moderne (Chrome/Firefox)  
**Objectif final** : Maîtriser le dessin vectoriel (SVG) et bitmap (Canvas) pour des applications web interactives, accessibles et performantes

---

## Module 1 – Introduction, mise en place et accessibilité
**Objectif** : Installer l’environnement, comprendre les bases et intégrer l’accessibilité dès le départ.

1. SVG vs Canvas (vectoriel vs bitmap, cas d’usage)
   1.1. SVG : scalable, DOM accessible, idéal pour icônes, graphiques, cartes
   1.2. Canvas : pixels, haute performance, idéal pour jeux, filtres, animations
   1.3. Quand choisir l’un ou l’autre
2. Structure HTML de base et intégration
   2.1. Balise `<svg>` : attributs `width`, `height`, `viewBox`
   2.2. Balise `<canvas>` : attributs `width`, `height` (taille réelle vs CSS)
   2.3. Accès au contexte 2D : `canvas.getContext('2d')`
3. Premier rectangle (SVG/Canvas)
   3.1. `<rect x="10" y="10" width="100" height="50" fill="red" />`
   3.2. `ctx.fillRect(10, 10, 100, 50)`
4. Accessibilité minimale
   4.1. SVG : `role="img"`, `<title>`, `<desc>`, `aria-label`
   4.2. Canvas : `aria-label` sur l’élément, gestion focus manuelle avec `tabindex`
   4.3. Fournir des descriptions alternatives dans le DOM

**TP final** :
> Crée une page HTML avec un carré rouge (SVG accessible avec titre et description) et un carré bleu (Canvas avec `aria-label`). Teste la navigation au clavier (tabulation et focus). Vérifie avec un lecteur d’écran (NVDA/VoiceOver).

---

## Module 2 – Bases du SVG + Responsive
**Objectif** : Maîtriser les formes, attributs et le rendu fluide.

1. Formes SVG
   1.1. `<rect>` : x, y, width, height, rx, ry
   1.2. `<circle>` : cx, cy, r
   1.3. `<ellipse>` : cx, cy, rx, ry
   1.4. `<line>` : x1, y1, x2, y2
   1.5. `<polygon>` : points="x1,y1 x2,y2 ..."
2. Styles et apparence
   2.1. Attributs : `fill`, `stroke`, `stroke-width`, `opacity`
   2.2. Styles CSS : `.ma-classe { fill: red; }`
3. **Système de coordonnées et responsive**
   3.1. `viewBox="minX minY width height"` – système de coordonnées interne
   3.2. `preserveAspectRatio` : comment l’image s’adapte (meet, slice, none)
   3.3. Largeur/hauteur en % pour l’adaptation au conteneur
4. Positionnement (x, y, cx, cy)

**TP final** :
> Dessine une maison SVG (toit triangulaire, corps rectangulaire, porte, fenêtre) qui s’adapte à n’importe quelle taille d’écran en utilisant `viewBox="0 0 100 100"`. Teste en redimensionnant la fenêtre.

---

## Module 3 – SVG avancé, dégradés et réutilisation
**Objectif** : Créer des graphiques complexes et optimisés.

1. Chemins (`<path>`)
   1.1. Commandes : `M` (move), `L` (ligne), `H` (horizontal), `V` (vertical)
   1.2. Courbes : `C` (cubic bezier), `Q` (quadratic), `A` (arc)
   1.3. Fermeture : `Z`
2. Groupes et transformations
   2.1. `<g>` – groupe logique
   2.2. `transform="translate(x,y) rotate(deg) scale(s)"`
   2.3. Application aux groupes
3. Dégradés et motifs
   3.1. `<linearGradient>` : `x1, y1, x2, y2`, `<stop>`
   3.2. `<radialGradient>` : `cx, cy, r`
   3.3. `<pattern>` – motifs répétés
4. **Optimisation SVG**
   4.1. `<defs>` – définitions réutilisables
   4.2. `<use href="#id" x="..." y="..." />` – réduit le DOM
   4.3. Accessibilité avancée : focus management pour éléments réutilisés (`tabindex`, `aria-labelledby`)

**TP final** :
> Crée un logo stylisé avec : un chemin personnalisé (forme libre), une transformation rotation sur un élément imbriqué, un dégradé linéaire, et une instance `<use>` pour réutiliser le motif. Ajoute un titre accessible et teste la navigation clavier sur chaque partie.

---

## Module 4 – Interactivité SVG + Événements tactiles
**Objectif** : Rendre le SVG dynamique (souris, clavier, tactile).

1. Accès DOM et modification dynamique
   1.1. `document.querySelector()` et `document.getElementById()`
   1.2. Modifier attributs : `element.setAttribute('fill', 'blue')`
   1.3. Modifier styles : `element.style.fill = 'blue'`
2. Événements souris
   2.1. `click`, `mouseover`, `mouseout`, `mousedown`, `mouseup`
   2.2. `target` et `currentTarget`
3. **Événements tactiles**
   3.1. `touchstart`, `touchmove`, `touchend`
   3.2. Coordonnées relatives au SVG : conversion avec `getBoundingClientRect()`
   3.3. Prévention du scroll par défaut : `preventDefault()` sur `touchmove`
4. **Animations SVG**
   4.1. CSS transitions sur attributs SVG (ex: `transition: fill 0.3s`)
   4.2. SMIL basique : `<animate attributeName="r" from="10" to="20" dur="1s" repeatCount="indefinite" />`
   4.3. JavaScript avec `requestAnimationFrame`

**TP final** :
> Crée un bouton SVG tactile et souris : cercle cliquable qui change de couleur au hover, se déplace légèrement au clic (modifier `cx`/`cy`), et reste utilisable au clavier (avec `tabindex` et événements `Enter`/`Espace`).

---

## Module 5 – Introduction au Canvas + Manipulation de pixels
**Objectif** : Comprendre le contexte 2D et accéder aux pixels.

1. Contexte "2d"
   1.1. `canvas.getContext('2d')` – unique point d’entrée
   1.2. `fillRect(x, y, w, h)`, `strokeRect(x, y, w, h)`, `clearRect(x, y, w, h)`
2. Dessin vectoriel Canvas
   2.1. `beginPath()`, `moveTo(x, y)`, `lineTo(x, y)`, `closePath()`
   2.2. `arc(x, y, radius, startAngle, endAngle)` (angles en radians)
   2.3. `stroke()` et `fill()`
3. Styles Canvas
   3.1. `fillStyle`, `strokeStyle`, `lineWidth`, `globalAlpha`
   3.2. Couleurs : chaînes CSS (`"red"`, `"#ff0000"`, `"rgb(255,0,0)"`)
4. **Manipulation de pixels**
   4.1. `getImageData(x, y, w, h)` → retourne `ImageData` avec `data` (Uint8ClampedArray)
   4.2. `putImageData(imageData, x, y)`
   4.3. Structure : `data` = [R, G, B, A, R, G, B, A, ...]
5. Filtres simples
   5.1. Niveau de gris : `(R+G+B)/3`
   5.2. Seuil (noir/blanc) : `valeur > 128 ? 255 : 0`

**TP final** :
> Dessine un smiley Canvas (cercle jaune, yeux noirs, sourire). Ajoute un bouton "Niveau de gris" qui applique un filtre gris sur tout le canvas (parcours pixels). Ajoute un bouton "Réinitialiser".

---

## Module 6 – Canvas avancé : transformations, images, texte
**Objectif** : Maîtriser les transformations et la composition.

1. Transformations
   1.1. `translate(x, y)` – déplace l’origine
   1.2. `rotate(angle)` – rotation en radians
   1.3. `scale(x, y)` – mise à l’échelle
   1.4. `setTransform(a, b, c, d, e, f)` – matrice complète
   1.5. `save()` et `restore()` – sauvegarde/restauration du contexte
2. **Images**
   2.1. `drawImage(image, x, y, width, height)`
   2.2. Chargement asynchrone : `new Image()` + événement `load`
   2.3. CORS : images cross-origin nécessitent `crossOrigin="anonymous"` et serveur autorisant
3. Texte
   3.1. `fillText(text, x, y)`, `strokeText(text, x, y)`
   3.2. `font` (ex: `"20px Arial"`), `textAlign`, `textBaseline`
   3.3. `measureText()` – largeur du texte
4. Effacement et redessin
   4.1. `clearRect(0, 0, canvas.width, canvas.height)`
   4.2. Pattern de redessin : tout redessiner à chaque frame
5. **Export**
   5.1. `canvas.toDataURL('image/png')` – obtient une URL base64
   5.2. Créer un lien téléchargeable : `<a download="capture.png" href="...">`

**TP final** :
> Crée une scène complexe : image d’arrière-plan (chargée depuis une URL), texte "Bonjour !" en superposition, et une forme géométrique tournante. Ajoute un bouton qui applique une rotation de 45° sur le texte uniquement (utilise `save`/`restore`). Ajoute un bouton "Exporter en PNG" qui télécharge la scène.

---

## Module 7 – Animations et performances Canvas
**Objectif** : Produire des animations fluides et économes.

1. **`requestAnimationFrame`**
   1.1. Principe : synchronisation avec le taux de rafraîchissement de l’écran (60 FPS)
   1.2. Structure de base : fonction `animate()` qui appelle `requestAnimationFrame(animate)`
   1.3. Avantages : pauvre en CPU quand onglet inactif
2. Mouvement
   2.1. Variables de position (x, y) et vitesse (vx, vy)
   2.2. Gravité simple : `vy += gravity`
3. **Collisions**
   3.1. Bounding box : `if (x > canvas.width - radius) { x = canvas.width - radius; vx = -vx }`
   3.2. Collision cercle-cercle : distance entre centres < somme des rayons
4. Optimisations
   4.1. Batching des dessins : éviter les appels redondants
   4.2. **OffscreenCanvas** + Web Worker (introduction)
      - Créer un `OffscreenCanvas`, le transférer au Worker
      - Dessiner dans le Worker pour ne pas bloquer le thread principal
   4.3. Double buffering : implicite en Canvas (le navigateur gère)
5. Problème du flickering : inexistant en Canvas bien implémenté

**TP final** :
> Crée une balle rouge qui rebondit sur les bords du canvas avec gravité. Ajoute une deuxième balle bleue avec collision entre balles. Utilise `requestAnimationFrame`. Aucun flickering visible. Bonus : passe les calculs de collision dans un Web Worker.

---

## Module 8 – Interaction utilisateur complète (souris, clavier, tactile) pour Canvas
**Objectif** : Gérer les entrées et la détection de collision avec des objets.

1. Événements souris
   1.1. `click`, `mousemove`, `mousedown`, `mouseup`
   1.2. Coordonnées Canvas : conversion par rapport à l’élément
      ```js
      const rect = canvas.getBoundingClientRect();
      const scaleX = canvas.width / rect.width;
      const scaleY = canvas.height / rect.height;
      const canvasX = (clientX - rect.left) * scaleX;
      ```
2. **Hit detection**
   2.1. Formes simples : point dans cercle (`distance < rayon`)
   2.2. Point dans rectangle (`x > rect.x && x < rect.x+rect.w`, idem y)
   2.3. Point dans polygone (algorithme du ray casting)
3. Événements clavier
   3.1. `keydown`, `keyup` sur `window` ou `canvas` (nécessite `tabindex`)
   3.2. Touches : `ArrowLeft`, `ArrowRight`, `Space`, `Enter`, etc.
4. **Événements tactiles**
   4.1. `touchstart`, `touchmove`, `touchend`
   4.2. Récupérer les touches : `event.touches[i]`
   4.3. Multi-touch basique : reconnaissance de deux doigts pour déplacement/zoom
   4.4. `preventDefault()` pour éviter le scroll

**TP final** :
> Mini jeu "Pousse le carré" : un carré rouge se déplace avec les flèches du clavier (ou avec un doigt tactile). Au clic souris (ou tap tactile) sur le carré, il change de couleur et gagne un point. Affiche le score. Gère la conversion coordonnées tactiles. Vérifie que le jeu reste jouable sans souris.

---

## Module 9 – Architecture et performances avancées
**Objectif** : Structurer une app graphique maintenable et rapide.

1. Organisation du code
   1.1. Séparation logique métier / rendu
   1.2. Classes JavaScript (ES6) : `class Game { update() { ... } draw(ctx) { ... } }`
   1.3. Modules ES6 : `import/export`
2. **Optimisation des redraws**
   2.1. Dirty rectangles : ne redessiner que les zones modifiées
   2.2. Mise en cache : dessiner dans un `OffscreenCanvas` pour les éléments statiques
   2.3. Exemple : fond complexe dessiné une seule fois, puis copié avec `drawImage`
3. **OffscreenCanvas avec Worker** (approfondi)
   3.1. Créer un Worker, lui passer un `OffscreenCanvas`
   3.2. Le Worker dessine, le thread principal affiche
   3.3. Cas d’usage : calculs lourds + rendu
4. Outils de débogage
   4.1. Inspecteur SVG (onglet Éléments du navigateur)
   4.2. Performance Canvas : onglet Performance, paint flashing
   4.3. `console.time` / `console.timeEnd` pour mesurer les frames
5. Gestion des erreurs
   5.1. Try/catch autour des opérations de dessin
   5.2. Image cassée : événement `error` sur `new Image()`

**TP final** :
> Refactorise le mini jeu du module 8 : crée une classe `Game`, une classe `Player`, structure propre. Ajoute un fond statique dessiné dans un `OffscreenCanvas` une seule fois. Mesure le temps de rendu. Ajoute un bouton "Debug" qui affiche le nombre d’appels de `draw` par seconde.

---

## Module 10 – SVG vs Canvas en situation réelle + WebGL intro
**Objectif** : Choisir la bonne technologie et ouvrir vers la 3D.

1. Comparaison concrète
   1.1. Performance : Canvas > SVG au-delà de ~1000 éléments
   1.2. Accessibilité : SVG > Canvas (DOM accessible nativement)
   1.3. Manipulation DOM : SVG est modifiable, Canvas est une image
   1.4. Scalabilité : SVG parfait, Canvas doit être redessiné
2. Cas d’usage typiques
   2.1. Dashboard / graphiques : SVG (interaction, légèreté) ou Canvas (milliers de points)
   2.2. Jeux : Canvas
   2.3. Plan de salle (seat map) : SVG (plus accessible) ou Canvas (si très grand)
3. **WebGL**
   3.1. Qu’est-ce que WebGL ? Interface OpenGL pour le web
   3.2. Différence avec Canvas 2D : programmation shaders, GPU, 3D
   3.3. WebGL pour : milliers d’objets, filtres complexes, 3D
   3.4. Bibliothèques : Three.js (abstraction), Pixi.js (2D GPU)
4. Sécurité
   4.1. CORS dans Canvas : `toDataURL` et `getImageData` bloqués si image cross-origin non autorisée
   4.2. Sandbox SVG : limitation des scripts dans les SVG isolés

**TP final** :
> Implémente deux versions d’une grille de sièges (50x50 = 2500 sièges) : une version SVG (sièges comme `<rect>`s), une version Canvas (dessin dans une boucle). Compare les performances (temps de chargement, interaction). Mentionne comment WebGL pourrait gérer des grilles encore plus grandes.

---

## Module 11 – Projet final intégrateur (Ticketmaster-like enrichi)
**Objectif** : Réaliser un système complet de réservation de sièges accessible, responsive et performant.

**Énoncé étendu** :

Développe un plan de salle interactif pour la réservation de sièges avec :

- **Choix technologique justifié** : SVG ou Canvas (selon les critères du module 10)
- **Accessibilité** :
  - Navigation clavier (flèches / tab) sur les sièges
  - Annonces pour lecteurs d’écran (`aria-live`) lors de la sélection
  - Descriptions alternatives
- **Responsive** :
  - Adaptation au redimensionnement (viewBox pour SVG, redessin pour Canvas)
  - Utilisation de pourcentages CSS
- **États des sièges** :
  - Disponible (vert)
  - Réservé (gris, non cliquable)
  - Sélectionné par l’utilisateur (bleu)
- **Interaction** :
  - Clic souris ou tap tactile pour réserver/unréserver
  - Feedback visuel instantané
  - Animation simple (ex: légère pulsation au clic)
- **Fonctionnalités bonus** :
  - Export PNG de la sélection (capture)
  - Affichage du nombre de sièges sélectionnés
  - Version OffscreenCanvas si grille > 500 éléments
- **Contraintes techniques** :
  - Code commenté
  - Fichier `README.md` avec justification du choix SVG/Canvas
  - Page unique HTML/CSS/JS sans framework (sauf optionnel)

**Livrable attendu** :
- `index.html`, `style.css`, `script.js` (ou `app.js`)
- Documentation interne (commentaires)
- Testé sur navigateur desktop + mobile (ou émulateur tactile)

---

## Module 12 (optionnel) – Intégration avec un framework (React/Vue)
**Objectif** : Transférer les compétences vers un framework moderne.

1. **React**
   1.1. SVG dans JSX : `return <svg><rect ... /></svg>` – attributs en camelCase (`strokeWidth`)
   1.2. Canvas avec `useRef` : `const canvasRef = useRef(null); canvasRef.current.getContext('2d')`
   1.3. Gestion d’état : `useState` pour les sièges sélectionnés
   1.4. Effets : `useEffect` pour redessiner le canvas après changement d’état
2. **Vue.js**
   1.1. Template avec `<svg>` : double binding `v-bind`
   1.2. Canvas : `ref` dans `setup`, `onMounted` pour initialiser
   1.3. Réactivité : `computed` pour les états des sièges
3. Patterns réutilisables
   3.1. Hook `useCanvas` (React) : encapsule la logique canvas
   3.2. Composant `SeatMap` générique

**TP final** :
> Transpose le projet final (plan de salle) en React ou Vue. Le composant doit être réutilisable avec des props pour le nombre de sièges, la couleur, etc. Vérifie que l’accessibilité clavier est conservée.

---

## Modules suivants (aperçu – approfondissements)

| Module | Titre | Contenu principal |
|--------|-------|-------------------|
| 13 | SVG avancé – Filtres et masques | `<filter>` (blur, drop-shadow), `<mask>` (découpage) |
| 14 | Canvas – Patterns complexes | Shadow, globalCompositeOperation (mélanges), gradients avancés |
| 15 | WebGL avec Three.js | Scène 3D, lumière, textures, animations basiques |
| 16 | Performance extrême | WebGPU (future), optimisation des shaders, mémoire GPU |

---

## Projet final intégrateur complet (après module 11)

**Capacités requises** :  
Tous les modules précédents (SVG, Canvas, accessibilité, responsive, événements souris/clavier/tactile, animations, performances, pixels, export).

**Énoncé enrichi – Système de réservation de salle de spectacle** :

Développe une application web complète (sans backend) qui permet :

1. **Visualisation de la salle** (orchestre, balcon, loges) :
   - Zones de sièges avec différentes couleurs (prix différents)
   - Zoom/Pan basique (optionnel)
2. **Sélection de sièges** :
   - Clic souris, tap tactile, navigation clavier
   - Indisponibles (gris) → non sélectionnables
   - Sélection multiple (Ctrl+clic ou touche Ctrl)
3. **Récapitulatif en temps réel** :
   - Nombre de sièges, prix total
   - Mise à jour accessible (annonce vocale)
4. **Persistance locale** :
   - Sauvegarde de la sélection dans `localStorage` (rechargement page)
5. **Export** :
   - Capture PNG du plan avec les sièges sélectionnés mis en évidence
6. **Performance** :
   - Si plus de 1000 sièges, utilise `OffscreenCanvas` ou une grille SVG optimisée
7. **Documentation** :
   - Fichier `README.md` avec justification de tous les choix techniques (SVG vs Canvas, gestion d’accessibilité, stratégie de rendu)

**Livrable final** :  
Dépôt GitHub avec code source, instructions d’installation (simple `index.html`), et une démo en ligne (GitHub Pages ou équivalent).

---

**Fin du plan de cours SVG & Canvas**
