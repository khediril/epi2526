
# TP : Maîtrise des Propriétés `display` en CSS

**Durée :** 3 heures

**Objectif :** Comprendre et appliquer les comportements des éléments HTML gérés par les propriétés CSS `display: block`, `display: inline`, et `display: flex` pour réaliser des mises en page de base.

-----

## Préparation

1.  Créez un dossier nommé `TP_Display_CSS`.
2.  À l'intérieur, créez deux fichiers : `index.html` et `style.css`.
3.  Liez la feuille de style CSS à la page HTML dans la section `<head>`.

## Partie 1 : Le Flux Normal (`block` vs `inline`) (60 min)

L'objectif de cette partie est d'observer le comportement par défaut des éléments HTML.

### Exercice 1.1 : Les éléments de type **`block`**

1.  Dans `index.html`, créez trois balises **`<div>`** consécutives. Donnez-leur la classe CSS `bloc`.
2.  Dans `style.css`, appliquez les styles suivants à la classe `.bloc` :
      * `background-color: lightblue;`
      * `border: 2px solid blue;`
      * `margin: 10px;`
      * `padding: 15px;`
3.  **Observation :** Que constatez-vous concernant la largeur de ces éléments et leur positionnement vertical ?
4.  Modifiez la largeur de ces blocs en ajoutant `width: 200px;`. Les blocs conservent-ils leur positionnement ?

### Exercice 1.2 : Les éléments de type **`inline`**

1.  Dans `index.html`, ajoutez une balise **`<p>`** contenant trois balises **`<span>`** consécutives. Donnez-leur la classe CSS `ligne`.
2.  Dans `style.css`, appliquez les styles suivants à la classe `.ligne` :
      * `background-color: lightgreen;`
      * `border: 2px solid green;`
      * `padding: 20px;` (sauf `padding-top` et `padding-bottom`)
      * `margin: 10px;`
3.  **Observation :** Que constatez-vous concernant l'espace vertical (`margin-top`/`margin-bottom`) et le dimensionnement de ces éléments ? Sont-ils côte à côte ?
4.  Tentez d'appliquer `width: 300px;` et `height: 50px;` aux éléments `.ligne`. Ces propriétés sont-elles prises en compte ?

### Exercice 1.3 : La conversion **`inline-block`**

1.  Modifiez le style de la classe `.ligne` en ajoutant la propriété : `display: inline-block;`.
2.  **Observation :** Les éléments sont-ils toujours côte à côte ? Les propriétés `width`, `height`, et les marges verticales sont-elles maintenant appliquées ?
3.  **Synthèse :** Expliquez la différence entre `block`, `inline` et `inline-block`.

-----

## Partie 2 : Le Modèle Flexbox (`display: flex`) (60 min)

L'objectif est d'utiliser Flexbox pour positionner les éléments de manière plus efficace et flexible.

### Exercice 2.1 : Configuration du Conteneur

1.  Dans `index.html`, créez un conteneur principal (`<div class="flex-container">`) et insérez-y cinq éléments enfants (`<div class="item">Item 1</div>` à `Item 5`).
2.  Dans `style.css`, donnez des dimensions et des couleurs de base aux `.item` (ex: `width: 100px; height: 50px; background-color: orange;`).
3.  Appliquez **`display: flex;`** au conteneur `.flex-container`.
4.  **Observation :** Comment les éléments `.item` se sont-ils arrangés ?

### Exercice 2.2 : Justification (Axe Principal)

Modifiez le style de `.flex-container` en changeant uniquement la propriété **`justify-content`** et observez l'effet :

1.  `justify-content: flex-end;`
2.  `justify-content: center;`
3.  `justify-content: space-between;`
4.  `justify-content: space-around;`

### Exercice 2.3 : Alignement (Axe Secondaire)

1.  Augmentez la hauteur du `.flex-container` (ex: `height: 200px;`).
2.  Modifiez le style de `.flex-container` en changeant uniquement la propriété **`align-items`** et observez l'effet :
      * `align-items: flex-end;`
      * `align-items: center;`

### Exercice 2.4 : Changement de Direction

1.  Appliquez la propriété **`flex-direction: column;`** au `.flex-container`.
2.  **Observation :** Que deviennent les propriétés `justify-content` et `align-items` ? (Elles s'inversent : `justify-content` agit maintenant verticalement).

-----

## Partie 3 : Mise en Page Pratique (60 min)

L'objectif est de construire une mise en page standard en utilisant uniquement Flexbox.

### Exercice 3.1 : Barre de Navigation Centrée

1.  Créez une barre de navigation (`<nav>`) contenant une liste (`<ul>`) de 4 liens (`<li><a>`).
2.  Appliquez **`display: flex;`** à la balise `<ul>`.
3.  Utilisez **`justify-content`** pour répartir les liens de manière égale sur toute la largeur de la barre.
4.  Appliquez **`align-items: center;`** pour centrer verticalement le texte dans la barre de navigation.

### Exercice 3.2 : Layout à Deux Colonnes

1.  Créez une structure HTML pour un layout :
    ```html
    <div class="main-layout">
        <aside class="sidebar"></aside>
        <section class="content"></section>
    </div>
    ```
2.  Appliquez **`display: flex;`** au conteneur `.main-layout`.
3.  Donnez une largeur fixe à la `sidebar` : `width: 250px;`.
4.  Appliquez la propriété **`flex-grow: 1;`** à la section `.content`.
