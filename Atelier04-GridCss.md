# TP : Maîtriser le CSS Grid Layout 🧱

**Durée :** 3 heures

**Objectif :** Comprendre le concept de grille, définir des lignes et des colonnes explicites et implicites, et positionner des éléments dans un système bi-dimensionnel.

-----

## Préparation

1.  Créez un dossier nommé `TP_CSS_Grid`.
2.  Créez deux fichiers : `index.html` et `style.css`.
3.  Liez la feuille de style CSS à la page HTML.
4.  Dans `index.html`, insérez un conteneur principal (`<div class="grid-container">`) et 9 éléments enfants (`<div class="item item-1">`, ..., `<div class="item item-9">`).
5.  Dans `style.css`, appliquez un style de base aux `.item` (bordure, padding, couleur de fond différente pour chaque item pour bien les distinguer).

## Partie 1 : Définition de la Grille (60 min)

L'objectif est d'établir la structure de base de la grille.

### Exercice 1.1 : Le Conteneur et les Colonnes

1.  Appliquez la propriété **`display: grid;`** à l'élément `.grid-container`.
2.  Définissez 3 colonnes de taille égale en utilisant la propriété **`grid-template-columns`** avec l'unité **`1fr`** :
    ```css
    /* 3 colonnes égales */
    grid-template-columns: 1fr 1fr 1fr;
    ```
3.  **Observation :** Les éléments se sont-ils automatiquement arrangés sur 3 colonnes ?
4.  Modifiez la définition des colonnes pour avoir : une colonne de **taille fixe** de `100px`, une colonne **flexible** de `2fr`, et une autre colonne **flexible** de `1fr`.
5.  Ajoutez un espacement entre les cellules de la grille en utilisant **`grid-gap: 10px;`** (ou `gap: 10px;`).

### Exercice 1.2 : Définition des Lignes

1.  Définissez explicitement les hauteurs des lignes en utilisant **`grid-template-rows`**. Définissez la première ligne à `50px`, la deuxième à `100px`, et la troisième à `150px`.
2.  Retirez les définitions de lignes et utilisez la propriété **`grid-auto-rows: 80px;`**.
3.  **Observation :** Quel est le rôle de `grid-auto-rows` par rapport à `grid-template-rows` ? (Réponse attendue : `grid-auto-rows` gère les lignes *implicites* non définies par le template).

### Exercice 1.3 : Les Fonctions Répétitives

1.  Redéfinissez la grille pour avoir 4 colonnes et 2 lignes de taille égale. Utilisez la fonction **`repeat()`** pour simplifier le code :
    ```css
    /* Remplacer 1fr 1fr 1fr 1fr par... */
    grid-template-columns: repeat(4, 1fr);
    ```

-----

## Partie 2 : Positionnement des Éléments (60 min)

L'objectif est de contrôler l'emplacement des éléments dans la grille, y compris le chevauchement et l'étirement (spanning).

### Exercice 2.1 : Étirement des Cellules (`span`)

1.  Revenez à la grille 3x3 (`grid-template-columns: repeat(3, 1fr);`).
2.  Ciblez l'élément `.item-1` et faites-le s'étendre sur **deux colonnes** en utilisant :
    ```css
    .item-1 {
        grid-column-start: 1; /* Commence à la ligne de grille 1 */
        grid-column-end: 3;   /* Finit à la ligne de grille 3 */
    }
    /* Ou, en raccourci : */
    /* grid-column: 1 / 3; */
    ```
3.  Ciblez l'élément `.item-4` et faites-le s'étendre sur **deux lignes** en utilisant le raccourci **`grid-row: 2 / span 2;`**.
4.  **Observation :** Comment les autres éléments (`.item-2`, `.item-3`, etc.) se réorganisent-ils pour remplir l'espace laissé ?

### Exercice 2.2 : Positionnement Bi-dimensionnel

1.  Ciblez l'élément `.item-7`. Positionnez-le pour qu'il commence à la 2ème ligne de colonne et à la 3ème ligne de ligne, et qu'il couvre 1 seule cellule :
      * `grid-column: 2 / 3;`
      * `grid-row: 3 / 4;`
2.  **Challenge :** Faites chevaucher deux éléments : positionnez `.item-8` pour qu'il se place exactement au même endroit que `.item-7`.
3.  Utilisez la propriété **`z-index`** sur `.item-7` et `.item-8` pour contrôler lequel des deux s'affiche au-dessus de l'autre.

### Exercice 2.3 : Alignement Local

1.  Donnez une grande hauteur à l'élément `.item-5` (`height: 200px;` - **Attention :** la hauteur doit être inférieure à celle de sa ligne de grille).
2.  À l'intérieur de `.item-5`, utilisez les propriétés **`justify-self`** et **`align-self`** avec les valeurs `start`, `end` et `center` pour positionner le contenu de l'item à l'intérieur de sa propre cellule.

-----

## Partie 3 : Mise en Page par Zones Nommées (60 min)

L'objectif est de créer une mise en page sémantique et facile à lire en nommant les zones de la grille.

### Exercice 3.1 : Définition des Zones

1.  Dans `index.html`, créez une nouvelle structure de layout (`<div class="layout-zones">`) avec les 4 enfants suivants :
      * `<header class="header">`
      * `<nav class="nav">`
      * `<main class="main-content">`
      * `<footer class="footer">`
2.  Appliquez `display: grid;` au `.layout-zones`.
3.  Définissez les zones de la grille en utilisant **`grid-template-areas`** pour créer le layout suivant (en-tête, navigation latérale, contenu principal, pied de page) :
    ```css
    .layout-zones {
        display: grid;
        grid-template-columns: 200px 1fr 200px; /* 3 colonnes: nav | contenu | vide */
        grid-template-rows: auto 1fr auto;      /* 3 lignes: header | contenu | footer */
        grid-template-areas:
            "header header header"
            "nav main ."
            "footer footer footer";
    }
    ```

### Exercice 3.2 : Affectation des Zones

1.  Affectez les éléments HTML à leurs zones correspondantes en utilisant la propriété **`grid-area`** :
    ```css
    .header { grid-area: header; }
    .nav    { grid-area: nav; }
    /* Compléter pour main-content et footer */
    ```
2.  **Observation :** La mise en page est-elle correcte ? Les éléments sont-ils positionnés selon le schéma `grid-template-areas` ?

### Exercice 3.3 : Layout Responsive (Bonus)

1.  Ajoutez une **Media Query** pour les écrans plus petits (`@media (max-width: 600px)`).
2.  Dans cette Media Query, modifiez uniquement la propriété **`grid-template-areas`** pour que les zones s'empilent verticalement :
    ```css
    grid-template-areas:
        "header"
        "nav"
        "main"
        "footer";
    grid-template-columns: 1fr; /* Une seule colonne */
    ```

-----

## Évaluation

Répondez brièvement aux questions suivantes :

1.  Quelle est la propriété utilisée pour définir le nombre et la taille des colonnes dans une grille ?
2.  Comment faites-vous pour qu'un élément s'étire sur 3 lignes de grille sans utiliser les noms des lignes (en utilisant `span`) ?
3.  Quelle est la principale différence (en termes de dimensions) entre Flexbox et Grid ?
4.  Quel est l'avantage principal d'utiliser `grid-template-areas` par rapport à la numérotation des lignes/colonnes ?