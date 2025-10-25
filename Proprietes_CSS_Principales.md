# 🌐 Introduction au CSS

**CSS (Cascading Style Sheets)** est un langage de style utilisé pour
décrire la présentation d'un document HTML.\
Il permet de **séparer le contenu (HTML)** de **la mise en forme
(CSS)**, ce qui rend le code plus clair, maintenable et réutilisable.


------------------------------------------------------------------------

## 🎨 1. Propriétés de couleur et de texte

### 🔹 `color`

Définit la couleur du texte.

``` css
p {
  color: red;
}
```

### 🔹 `background-color`

Définit la couleur d'arrière-plan.

``` css
body {
  background-color: #f0f0f0;
}
```

### 🔹 `font-size`

Taille de la police (en px, em, rem, %, etc.).

``` css
h1 {
  font-size: 2em; /* 2 fois la taille de la police du parent */
}
```

### 🔹 `font-family`

Police d'écriture.

``` css
p {
  font-family: "Arial", sans-serif;
}
```

### 🔹 `font-weight`

Épaisseur de la police.

``` css
strong {
  font-weight: bold; /* ou 700 */
}
```

### 🔹 `text-align`

Alignement du texte.

``` css
h2 {
  text-align: center;
}
```

### 🔹 `text-decoration`

Ajoute une décoration (souvent utilisée pour souligner ou supprimer un
soulignement).

``` css
a {
  text-decoration: none;
}
```

------------------------------------------------------------------------

## 📦 2. Propriétés de boîte (Box Model)

Tout élément HTML peut être vu comme une **boîte rectangulaire**
comportant : - **content** (contenu) - **padding** (marge intérieure) -
**border** (bordure) - **margin** (marge extérieure)

``` css
div {
  width: 200px;
  height: 100px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

### Détails :

  Propriété           Description                             Exemple
  ------------------- --------------------------------------- --------------------------
  `width`, `height`   Taille du contenu                       `width: 100px;`
  `padding`           Espace entre le contenu et la bordure   `padding: 10px;`
  `border`            Bordure autour de l'élément             `border: 1px solid red;`
  `margin`            Espace autour de l'élément              `margin: 20px;`

------------------------------------------------------------------------

## 📐 3. Gestion de la disposition (Layout)

### 🔹 `display`

Contrôle la manière dont l'élément est affiché.

  Valeur           Effet
  ---------------- -----------------------------------------------
  `block`          Occupe toute la largeur (ex : `<div>`, `<p>`)
  `inline`         N'interrompt pas la ligne (ex : `<span>`)
  `inline-block`   Combine les avantages des deux
  `flex`           Active un conteneur flexible
  `grid`           Active une grille CSS

``` css
div {
  display: flex;
}
```

### 🔹 `position`

Détermine la position d'un élément.

  Valeur       Description
  ------------ ----------------------------------------------
  `static`     Par défaut
  `relative`   Positionné par rapport à sa position normale
  `absolute`   Positionné par rapport à l'élément parent
  `fixed`      Fixé dans la fenêtre du navigateur
  `sticky`     Se fixe lors du défilement

``` css
.box {
  position: absolute;
  top: 10px;
  left: 20px;
}
```

------------------------------------------------------------------------

## 🧭 4. Flexbox (mise en page moderne)

Le **Flexbox** facilite la création de dispositions flexibles.

``` css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

  Propriété           Rôle
  ------------------- ------------------------------------------
  `justify-content`   Aligne les éléments sur l'axe principal
  `align-items`       Aligne les éléments sur l'axe secondaire
  `flex-direction`    Définit la direction (`row`, `column`)
  `gap`               Espace entre les éléments

------------------------------------------------------------------------

## 🧱 5. Grilles CSS (CSS Grid)

Pour des mises en page complexes.

``` css
.grid {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 10px;
}
```

  Propriété                 Description
  ------------------------- -------------------------------
  `grid-template-columns`   Nombre et taille des colonnes
  `grid-template-rows`      Nombre et taille des lignes
  `gap`                     Espace entre les cellules

------------------------------------------------------------------------

## 🌈 6. Bordures, coins et ombres

``` css
.box {
  border: 2px solid #333;
  border-radius: 10px;
  box-shadow: 2px 2px 8px rgba(0,0,0,0.3);
}
```

  Propriété         Description
  ----------------- --------------------------
  `border`          Définit la bordure
  `border-radius`   Arrondit les coins
  `box-shadow`      Ajoute une ombre externe

------------------------------------------------------------------------

## 🪄 7. Transitions et animations

### 🔹 `transition`

Permet d'animer des changements en douceur.

``` css
button {
  background: blue;
  transition: background 0.3s;
}

button:hover {
  background: green;
}
```

### 🔹 `animation`

Permet de créer des animations plus complexes.

``` css
@keyframes bouge {
  from { left: 0; }
  to { left: 100px; }
}

div {
  position: relative;
  animation: bouge 2s infinite alternate;
}
```

------------------------------------------------------------------------

## 📱 8. Media Queries (responsive design)

Permet d'adapter le style selon la taille de l'écran.

``` css
@media (max-width: 600px) {
  body {
    background-color: lightgray;
  }
}
```

------------------------------------------------------------------------

## 💡 Bonnes pratiques

-   Utilisez des **classes** pour cibler les éléments.

-   Privilégiez les **valeurs relatives** (`em`, `%`, `rem`) pour la
    responsivité.

-   Commentez votre code :

    ``` css
    /* Mise en forme de l'en-tête */
    header { ... }
    ```
