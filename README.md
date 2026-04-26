# 🎨 Formation SVG & Canvas - Cours complet des graphiques web

[![SVG Version](https://img.shields.io/badge/SVG-1.1-FF6600?style=flat&logo=svg)](https://www.w3.org/TR/SVG2/)
[![Canvas Version](https://img.shields.io/badge/Canvas-2D-00ADD8?style=flat&logo=html5)](https://developer.mozilla.org/fr/docs/Web/API/Canvas_API)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Complet-brightgreen)]()

Bienvenue dans ce cours complet d'apprentissage des graphiques web avec **SVG** (Scalable Vector Graphics) et **Canvas**. Ce dépôt contient un plan de cours structuré, des modules progressifs et des travaux pratiques pour maîtriser les deux technologies, de zéro à un niveau avancé, avec un accent particulier sur **l'accessibilité**, le **responsive design** et les **performances**.

---

## 📋 Table des matières

- [À propos](#-à-propos)
- [Prérequis](#-prérequis)
- [Structure du cours](#-structure-du-cours)
- [Modules (1 à 12)](#-modules-1-à-12)
- [Modules suivants (aperçu)](#-modules-suivants-aperçu)
- [Projet final](#-projet-final)
- [Installation](#-installation)
- [Comment utiliser ce cours](#-comment-utiliser-ce-cours)
- [TP par module](#-tp-par-module)
- [Ressources complémentaires](#-ressources-complémentaires)

---

## 🎯 À propos

Ce cours est conçu pour vous apprendre **SVG** et **Canvas** de manière progressive et pratique, en vous permettant de choisir la bonne technologie selon vos besoins. Chaque module combine :

- **Concepts théoriques** expliqués simplement
- **Exemples concrets** et bonnes pratiques
- **Travaux pratiques (TP)** avec corrigés
- **Pièges à éviter** et astuces
- **Accessibilité** intégrée dès le début (a11y)
- **Responsive design** pour tous les écrans

**Contenu actuel :** Modules 1 à 12 (fondamentaux SVG, Canvas, interactivité, animations, performances, tactile, architecture)
**À venir :** Modules 13 à 16

---

## 📚 Prérequis

- Connaissances de base en HTML et CSS
- Notions élémentaires en JavaScript (variables, fonctions, événements)
- Un navigateur moderne (Chrome, Firefox, Edge, Safari)
- Un éditeur de code (VS Code recommandé)

---

## 🏗️ Structure du cours

Le cours est découpé en **16 modules progressifs** + un **projet final intégrateur** :

```
formation_svg_canvas/
├── README.md                              # Ce fichier
├── 01_introduction_et_mise_en_place.md
├── 02_bases_svg_et_responsive.md
├── 03_svg_avance_degrades_et_reutilisation.md
├── 04_interactivite_svg_evenements_tactiles.md
├── 05_introduction_canvas_et_pixels.md
├── 06_canvas_avance_transformations_images_texte.md
├── 07_animations_et_performances_canvas.md
├── 08_interaction_complete_canvas.md
├── 09_architecture_et_performances_avancees.md
├── 10_svg_vs_canvas_webgl_intro.md
├── 11_projet_final_integrateur.md
├── 12_integration_framework_react_vue.md
├── 13_svg_avance_filtres_masques.md        📝 À venir
├── 14_canvas_patterns_complexes.md          📝 À venir
├── 15_webgl_avec_threejs.md                 📝 À venir
└── 16_performance_extreme.md                📝 À venir
```

---

## 📖 Modules (1 à 12)

### Module 1 – Introduction, mise en place et accessibilité
**Objectif** : Installer l'environnement, comprendre les bases et intégrer l'accessibilité dès le départ.

| Sous-partie | Description |
|-------------|-------------|
| 1.1 | SVG vs Canvas (vectoriel vs bitmap, cas d'usage) |
| 1.2 | Structure HTML et intégration (`<svg>`, `<canvas>`) |
| 1.3 | Premier rectangle (SVG/Canvas) |
| 1.4 | Accessibilité minimale (`role="img"`, `aria-label`, `tabindex`) |

**TP** : Page avec carré rouge (SVG accessible) + carré bleu (Canvas) + focus clavier testé

---

### Module 2 – Bases du SVG + Responsive
**Objectif** : Maîtriser les formes, attributs et le rendu fluide.

| Sous-partie | Description |
|-------------|-------------|
| 1 | Formes : `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polygon>` |
| 2 | Styles : fill, stroke, stroke-width, opacity |
| 3 | Système de coordonnées et responsive : `viewBox`, `preserveAspectRatio` |
| 4 | Positionnement (x, y, cx, cy) |

**TP** : Maison SVG qui s'adapte à n'importe quelle taille d'écran

---

### Module 3 – SVG avancé, dégradés et réutilisation
**Objectif** : Créer des graphiques complexes et optimisés.

| Sous-partie | Description |
|-------------|-------------|
| 1 | Chemins (`<path>` : M, L, H, V, C, Q, A) |
| 2 | Groupes et transformations (`<g>`, translate, rotate, scale) |
| 3 | Dégradés (linearGradient, radialGradient) et motifs |
| 4 | Optimisation SVG : `<defs>` + `<use>` pour réduire le DOM |

**TP** : Logo stylisé avec chemin personnalisé, rotation, dégradé

---

### Module 4 – Interactivité SVG + Événements tactiles
**Objectif** : Rendre le SVG dynamique (souris, clavier, tactile).

| Sous-partie | Description |
|-------------|-------------|
| 1 | Accès DOM et modification d'attributs (`setAttribute`) |
| 2 | Événements : click, mouseover, drag (simulé) |
| 3 | Événements tactiles : touchstart, touchmove, touchend |
| 4 | Prévention du scroll et du zoom par défaut |

**TP** : Bouton SVG tactile et souris qui change de couleur au hover

---

### Module 5 – Introduction au Canvas + Manipulation de pixels
**Objectif** : Comprendre le contexte 2D et accéder aux pixels.

| Sous-partie | Description |
|-------------|-------------|
| 1 | Contexte "2d" : fillRect, strokeRect |
| 2 | Dessin vectoriel : beginPath, moveTo, lineTo, arc |
| 3 | Styles : fillStyle, strokeStyle, lineWidth |
| 4 | Manipulation de pixels : getImageData, putImageData |

**TP** : Smiley Canvas + bouton « inverser couleurs »

---

### Module 6 – Canvas avancé : transformations, images, texte
**Objectif** : Maîtriser les transformations et la composition.

| Sous-partie | Description |
|-------------|-------------|
| 1 | Transformations : translate, rotate, scale, setTransform |
| 2 | Images : drawImage, chargement, CORS |
| 3 | Texte : fillText, strokeText, police |
| 4 | Export : toDataURL (PNG) – sauvegarde/capture |

**TP** : Scène complexe (image + texte + formes) avec rotation

---

### Module 7 – Animations et performances Canvas
**Objectif** : Produire des animations fluides et économes.

| Sous-partie | Description |
|-------------|-------------|
| 1 | requestAnimationFrame : principe et boucle |
| 2 | Mouvement : position, vitesse, gravité simple |
| 3 | Collisions : bounding box, rebonds |
| 4 | Optimisation : OffscreenCanvas + Web Worker (intro) |

**TP** : Balle qui rebondit dans l'écran

---

### Module 8 – Interaction utilisateur complète (souris, clavier, tactile) pour Canvas
**Objectif** : Gérer les entrées et la détection de collision.

| Sous-partie | Description |
|-------------|-------------|
| 1 | Événements souris : click, mousemove, mousedown/up |
| 2 | Coordonnées Canvas transformées (ratio, décalage) |
| 3 | Clavier : keydown, keyup |
| 4 | Hit detection sur objets (formes simples) |

**TP** : Mini jeu : déplacer un carré au clavier

---

### Module 9 – Architecture et performances avancées
**Objectif** : Structurer une app graphique maintenable et rapide.

| Sous-partie | Description |
|-------------|-------------|
| 1 | Organisation du code : séparation logique/rendu, classes JS |
| 2 | Optimisation des redraws : dirty rectangles, mise en cache |
| 3 | OffscreenCanvas avec Worker (exemple simple) |
| 4 | Outils de débogage : inspecteur SVG, performance Canvas |

**TP** : Refactoriser le mini jeu avec une architecture propre

---

### Module 10 – SVG vs Canvas en situation réelle + WebGL intro
**Objectif** : Choisir la bonne technologie et ouvrir vers la 3D.

| Sous-partie | Description |
|-------------|-------------|
| 1 | Comparaison concrète : performance, accessibilité |
| 2 | Cas d'usage : dashboard (SVG), jeu (Canvas) |
| 3 | WebGL : introduction, différence avec Canvas 2D |
| 4 | Sécurité : CORS dans Canvas, sandbox SVG |

**TP** : Grille de sièges en SVG vs Canvas (comparaison performance)

---

### Module 11 – Projet final intégrateur
**Objectif** : Réaliser un système complet de réservation de sièges accessible.

**Énoncé** : Plan de salle avec :
- Choix technologique justifié (SVG ou Canvas)
- Accessibilité : navigation clavier, annonces lecteurs d'écran
- Responsive : adaptation au redimensionnement
- États : disponible / réservé / sélectionné
- Export PNG de la sélection

---

### Module 12 – Intégration avec un framework (React/Vue)
**Objectif** : Transférer les compétences vers un framework moderne.

| Sous-partie | Description |
|-------------|-------------|
| 1 | React : SVG dans JSX, useRef pour Canvas |
| 2 | Vue : ref, réactivité sur attributs SVG |
| 3 | Patterns : composants réutilisables, hooks |

**TP** : Mini seat map dans React ou Vue

---

## 📖 Modules suivants (aperçu)

| Module | Titre | Description |
|--------|-------|-------------|
| 13 | SVG avancé – Filtres et masques | `<filter>` (blur, shadow), `<mask>` |
| 14 | Canvas – Patterns complexes | globalCompositeOperation, gradients avancés |
| 15 | WebGL avec Three.js | Scène 3D, lumière, textures |
| 16 | Performance extrême | WebGPU, optimisation GPU |

---

## 🎓 Projet final

**Système de réservation de salle de spectacle**

À la fin du cours (module 11), vous développerez une application complète qui combine toutes les compétences acquises :

- ✅ Plan de salle interactif (SVG ou Canvas justifié)
- ✅ Accessibilité complète (clavier, lecteurs d'écran)
- ✅ Responsive design (viewBox ou redessin)
- ✅ États des sièges (disponible/réservé/sélectionné)
- ✅ Animation simple (feedback utilisateur)
- ✅ Export PNG de la sélection
- ✅ Persistance locale (`localStorage`)
- ✅ Code commenté et documentation

---

## 🔧 Installation

### Prérequis

Aucune installation spécifique n'est requise ! Un simple navigateur et un éditeur de texte suffisent.

### Environnement recommandé

**VS Code** avec extensions :
- Live Server (pour serveur local)
- SVG Viewer
- Prettier (formatage)

```bash
# Cloner ce dépôt
git clone https://github.com/votre-compte/formation-svg-canvas.git
cd formation-svg-canvas

# Démarrer un serveur local (si Live Server installé)
# Ou ouvrir index.html directement
```

### Structure d'un TP type

```bash
module-1-tp/
├── index.html
├── style.css
└── script.js
```

---

## 💡 Comment utiliser ce cours

1. **Par module** : Suivez l'ordre recommandé (Module 1 → 12)
2. **Pratiquez** : Faites chaque TP **sans regarder la correction** d'abord
3. **Expérimentez** : Modifiez les exemples, testez vos idées
4. **Testez l'accessibilité** : Navigation clavier + lecteur d'écran

### Commandes utiles

```bash
# Ouvrir le navigateur avec live-reload (VS Code Live Server)
Clique droit sur index.html → "Open with Live Server"

# Vérifier l'accessibilité (Chrome DevTools)
F12 → Onglet "Lighthouse" → Catégorie "Accessibility"

# Debug Canvas
console.log(ctx) # Vérifier le contexte
```

### Test d'accessibilité

| Outil | Usage |
|-------|-------|
| **Tab** | Navigation clavier |
| **NVDA/VoiceOver** | Lecteur d'écran |
| **Lighthouse** | Audit automatique |
| **axe DevTools** | Extension Chrome |

---

## 📚 TP par module (Modules 1 à 12)

| Module | TP | Concepts clés |
|--------|-----|----------------|
| **1** | Carrés SVG et Canvas accessibles | `viewBox`, `role="img"`, `tabindex` |
| **2** | Maison SVG responsive | `viewBox`, `preserveAspectRatio` |
| **3** | Logo stylisé | `<path>`, `<g>`, `<defs>`, `<use>` |
| **4** | Bouton SVG tactile | Événements tactiles, `setAttribute` |
| **5** | Smiley Canvas + filtre pixels | `getImageData`, `putImageData` |
| **6** | Scène avec image + texte | Transformations, `drawImage`, `toDataURL` |
| **7** | Balle rebondissante | `requestAnimationFrame`, collisions |
| **8** | Mini jeu déplacement | Hit detection, clavier, tactile |
| **9** | Refactorisation jeu | Classes, OffscreenCanvas |
| **10** | Comparaison SVG vs Canvas | Performance, cas d'usage |
| **11** | Plan de salle réservation | Projet complet |
| **12** | Seat map React/Vue | Framework moderne |

### Exemple de réalisation (Module 1)

```svg
<svg viewBox="0 0 100 100" role="img" aria-labelledby="title">
    <title id="title">Carré Rouge</title>
    <rect x="10" y="10" width="80" height="80" fill="red" />
</svg>
```

```javascript
// Canvas avec gestion focus
const canvas = document.getElementById('monCanvas');
canvas.tabIndex = 0;
canvas.addEventListener('keydown', (e) => {
    if (e.key === 'Enter') {
        // Action
    }
});
```

---

## 🔗 Ressources complémentaires

### Documentation officielle
- [MDN - SVG](https://developer.mozilla.org/fr/docs/Web/SVG)
- [MDN - Canvas API](https://developer.mozilla.org/fr/docs/Web/API/Canvas_API)
- [W3C - SVG 2.0](https://www.w3.org/TR/SVG2/)
- [WCAG - Accessibilité](https://www.w3.org/WAI/WCAG22/quickref/)

### Outils recommandés
- **VS Code** + Live Server
- **Inkscape** (éditeur SVG)
- **Chrome DevTools** (débogage)
- **Lighthouse** (audit accessibilité)
- **axe DevTools** (tests a11y)

### Bibliographie
- "SVG Essentials" - J. David Eisenberg
- "HTML5 Canvas" - Steve Fulton & Jeff Fulton
- "Inclusive Design Patterns" - Heydon Pickering

### Communauté
- [MDN Web Docs](https://developer.mozilla.org/)
- [Stack Overflow - SVG](https://stackoverflow.com/questions/tagged/svg)
- [Stack Overflow - Canvas](https://stackoverflow.com/questions/tagged/html5-canvas)
- [Web Almanac](https://almanac.httparchive.org/)

---

## 📈 Progression recommandée

```
Semaine 1   : Module 1 (Introduction + accessibilité)
Semaine 2   : Modules 2-3 (Bases SVG + avancé)
Semaine 3   : Module 4 (Interactivité SVG + tactile)
Semaine 4   : Modules 5-6 (Bases Canvas + avancé)
Semaine 5   : Module 7 (Animations Canvas)
Semaine 6   : Module 8 (Interaction Canvas)
Semaine 7   : Module 9 (Architecture + performances)
Semaine 8   : Module 10 (SVG vs Canvas + WebGL)
Semaine 9   : Module 11 (Projet final)
Semaine 10  : Module 12 (Framework) + perfectionnement
```

---

## 🤝 Contribution

Les corrections, suggestions et améliorations sont les bienvenues !

1. Forkez le projet
2. Créez votre branche (`git checkout -b amelioration/ma-modification`)
3. Committez vos changements (`git commit -m 'feat: ajout de quelque chose'`)
4. Poussez vers la branche (`git push origin amelioration/ma-modification`)
5. Ouvrez une Pull Request

---

## 📝 Licence

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## ✨ Remerciements

- Le W3C pour les spécifications SVG
- La communauté MDN pour la documentation Canvas
- Les experts en accessibilité web (WCAG)
- Tous les contributeurs et apprenants

---

**Bon apprentissage ! 🎨♿**

N'hésitez pas à ouvrir une issue si vous avez des questions ou des suggestions.

*Dernière mise à jour : Avril 2026*
