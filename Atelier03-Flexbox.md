
# Atelier Guidé : Maîtriser la Mise en Page avec CSS Flexbox

  * **Objectif Principal :** Comprendre et savoir utiliser le modèle de boîte flexible (Flexbox) pour créer des mises en page modernes et responsives.
  * **Prérequis :** Connaissances de base en HTML (structure) et CSS (sélecteurs, propriétés `color`, `background`, `width`, `height`, et le **Box Model**).

-----

## Déroulé de l'Atelier

### Module 1 : Le "Pourquoi" ?

**Le Concept Fondamental de Flexbox**

  * **La Révolution :** Flexbox introduit l'idée d'un **conteneur** qui contrôle ses **enfants**.

  * **Les Deux Axes :** L'idée la plus importante. Il y a toujours un **Axe Principal** (Main Axis) et un **Axe Secondaire** (Cross Axis).

  * Le conteneur "dit" aux enfants comment se comporter sur ces axes.

**Activation de Flexbox**

  * On applique `display: flex;` au **conteneur parent**.
  * Démonstration en direct : 4 `div` dans un conteneur. Par défaut, ils sont en `display: block` (l'un sous l'autre).
  * Ajout de `display: flex;` -\> Ils se mettent instantanément en ligne. C'est le point de départ.

-----

### Module 2 : Le Conteneur Flex (Partie 1) - L'Axe Principal

  * **Objectif :** Maîtriser la distribution des éléments sur l'axe principal.

**Changer de Direction : `flex-direction`**

  * `row` (défaut) : L'axe principal est horizontal (gauche à droite).
  * `row-reverse` : L'axe principal est horizontal (droite à gauche).
  * `column` : L'axe principal devient vertical (haut en bas).
  * `column-reverse` : L'axe principal est vertical (bas en haut).

**La Propriété Reine : `justify-content`**

  * C'est la propriété qui gère l'alignement et la distribution sur l'**Axe Principal**.
  * Explication visuelle :
      * `flex-start` (défaut) : Tout au début.
      * `flex-end` : Tout à la fin.
      * `center` : Tout au centre.
      * `space-between` : Espace *entre* les éléments (le premier au début, le dernier à la fin).
      * `space-around` : Espace *autour* de chaque élément (demi-espace aux extrémités).
      * `space-evenly` : Espace *égal* partout.

**🛠️ EXERCICE 1 : Construire une Barre de Navigation**

  * **But :** Créer un header avec un logo à gauche et des liens de navigation groupés à droite.
  * **HTML fourni :**
    ```html
    <nav class="main-nav">
      <div class="logo">MonLogo</div>
      <ul>
        <li><a href="#">Accueil</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </nav>
    ```
  * **Instructions guidées :**
    1.  "Commencez par styliser la nav (ex: fond noir, couleur blanche)."
    2.  "Le `<ul>` a des puces et des marges. Enlevez-les."
    3.  "Les `<li>` sont en `block`. Comment les mettre en ligne ?" -\> `display: flex;` sur le `<ul>` \!
    4.  "Le logo et la liste `<ul>` sont l'un sous l'autre. Comment les aligner ?" -\> `display: flex;` sur le parent `.main-nav`.
    5.  "Maintenant, comment pousser le logo à gauche et la liste à droite ?" -\> `justify-content: space-between;` sur `.main-nav`.
    6.  "Le logo et les liens ne sont pas centrés verticalement. On verra ça au module 3..."

-----

### Module 3 : Le Conteneur Flex (Partie 2) - L'Axe Secondaire et l'Enroulement

  * **Objectif :** Maîtriser l'alignement sur l'axe secondaire et la gestion du responsive.

**L'Alignement : `align-items`**

  * C'est la propriété qui gère l'alignement sur l'**Axe Secondaire**.
  * `stretch` (défaut) : Les enfants s'étirent pour remplir le conteneur.
  * `flex-start` : Les enfants en haut (si `flex-direction: row`).
  * `flex-end` : Les enfants en bas.
  * `center` : **LA solution pour le centrage vertical \!**

**Le Responsive : `flex-wrap`**

  * Par défaut, Flexbox essaie de tout garder sur une seule ligne (`nowrap`).
  * `wrap` : Permet aux éléments de passer à la ligne s'ils n'ont plus de place. C'est la base du responsive avec Flexbox.

**🛠️ EXERCICE 2 : Une Galerie de Cartes**

  * **But :** Créer une galerie de "cartes produits" qui s'adapte à la largeur de l'écran.
  * **HTML fourni :**
    ```html
    <div class="gallery-container">
      <div class="card">Produit 1</div>
      <div class="card">Produit 2</div>
      <div class="card">Produit 3</div>
      <div class="card">Produit 4</div>
      <div class="card">Produit 5</div>
    </div>
    ```
  * **Instructions guidées :**
    1.  "Donnez une taille fixe à vos cartes (ex: `width: 200px; height: 150px;`) et un fond."
    2.  "Activez Flexbox sur `.gallery-container`."
    3.  "Observez ce qui se passe si vous réduisez la fenêtre... Les cartes rétrécissent \! Pourquoi ?" -\> `flex-shrink` (on verra ça après).
    4.  "Comment forcer les cartes à passer à la ligne ?" -\> `flex-wrap: wrap;`.
    5.  "Maintenant, les cartes sont collées à gauche. Comment les centrer ?" -\> `justify-content: center;` (ou `space-around`).
    6.  **(Bonus)** "Reprenez l'exercice 1 et ajoutez `align-items: center;` sur `.main-nav`. Magique, non ?"

-----

**PAUSE**

-----

### Module 4 : Les Enfants Flex

  * **Objectif :** Comprendre comment un enfant peut modifier son propre comportement.

**La Flexibilité : `flex-grow`, `flex-shrink`, `flex-basis`**

  * Ces propriétés s'appliquent aux **enfants**, pas au conteneur.
  * `flex-basis` : La taille "idéale" ou de base de l'élément (remplace `width` dans un contexte flex).
  * `flex-grow` : Un nombre. Définit la capacité d'un élément à "grandir" s'il y a de l'espace en trop. `0` = ne grandit pas. `1` = grandit.
  * `flex-shrink` : Un nombre. Définit la capacité à rétrécir. `1` = rétrécit. `0` = ne rétrécit pas.
  * **Le Raccourci Magique :** `flex: 1;` (équivaut à `flex-grow: 1; flex-shrink: 1; flex-basis: 0%;`). Signifie : "Prends tout l'espace disponible et partage-le équitablement".

**🛠️ EXERCICE 3 : Le Layout "Saint-Graal" (simplifié)**

  * **But :** Créer un layout classique (sidebar, contenu principal) qui remplit 100% de la hauteur.
  * **HTML fourni :**
    ```html
    <div class="page-container">
      <aside class="sidebar">Sidebar</aside>
      <main class="main-content">Contenu principal</main>
    </div>
    ```
  * **Instructions guidées :**
    1.  "Donnez au `.page-container` une hauteur de `100vh` (100% de la hauteur de la fenêtre) et activez Flexbox."
    2.  "Donnez une largeur de base à la sidebar (ex: `flex-basis: 250px;` ou juste `width: 250px;`)."
    3.  "Le contenu principal ne prend pas le reste de la place. Comment lui dire de 'grandir' pour remplir l'espace vide ?" -\> `flex-grow: 1;` (ou `flex: 1;`) sur `.main-content`.
