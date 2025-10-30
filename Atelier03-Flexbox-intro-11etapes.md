# Atelier 03 : Mise en page en utilisant les Flexbox

### **Objectif du TP : Maîtriser Flexbox **

**Projet :** Vous allez créer la mise en page d'un site e-commerce, incluant un **header**, une **sidebar de filtres**, le **contenu principal**, et un **pied de page**.

-----

### **Fichiers de Départ **

Commencez par créer deux fichiers : `index.html` et `style.css`.

#### `index.html` (Nouveau)

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TP Flexbox - Sneakers</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <header class="main-header">
        <div class="logo">SNEAKERS</div>
        <nav class="main-nav">
            <ul>
                <li><a href="#">Nouveautés</a></li>
                <li><a href="#">Hommes</a></li>
                <li><a href="#">Femmes</a></li>
                <li><a href="#">Contact</a></li>
            </ul>
        </nav>
    </header>

    <div class="page-content">
        
        <aside class="sidebar-left">
            <h3>Filtres</h3>
            <ul>
                <li><a href="#">Taille</a></li>
                <li><a href="#">Couleur</a></li>
                <li><a href="#">Marque</a></li>
                <li><a href="#">Prix</a></li>
            </ul>
        </aside>

        <main class="main-content">
            <div class="container">
                <h1>Nos Nouveautés</h1>
                
                <div class="product-gallery">
                    <div class="card">
                        <img src="https://via.placeholder.com/300x200?text=Sneaker+1" alt="Sneaker 1">
                        <h3 class="card-title">Modèle Air Max</h3>
                        <p class="card-description">Confort et style, le classique revisité pour 2025.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>
                    <div class="card">
                        <img src="https://via.placeholder.com/300x200?text=Sneaker+2" alt="Sneaker 2">
                        <h3 class="card-title">Modèle Runner</h3>
                        <p class="card-description">Parfaite pour vos sessions de course, légère et durable.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>
                    <div class="card">
                        <img src="https://via.placeholder.com/300x200?text=Sneaker+3" alt="Sneaker 3">
                        <h3 class="card-title">Modèle Urbain</h3>
                        <p class="card-description">Le style de rue à l'état pur. Stock limité.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>
                    <div class="card">
                        <img src="https://via.placeholder.com/300x200?text=Sneaker+4" alt="Sneaker 4">
                        <h3 class="card-title">Modèle Classique</h3>
                        <p class="card-description">Simple, efficace, indémodable.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>
                </div>
            </div>
        </main>

    </div> <footer class="main-footer">
        <p>&copy; 2025 Sneakers Inc. Tous droits réservés.</p>
    </footer>

</body>
</html>
```

#### `style.css` (Nouveau style de départ)

Copiez ce code. Il inclut des styles de base pour la sidebar et le footer, pour qu'ils soient visibles.

```css
/* Réinitialisation et styles de base */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    background-color: #f4f4f4;
}

.main-header {
    background-color: #fff;
    border-bottom: 2px solid #eee;
    padding: 20px;
}
.logo {
    font-size: 24px;
    font-weight: bold;
}
.main-nav ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
}
.main-nav li {
    margin-left: 15px;
}
.main-nav a {
    text-decoration: none;
    color: #555;
    font-weight: bold;
}

/* NOUVEAU : Styles de base pour la sidebar */
.sidebar-left {
    background-color: #fff;
    padding: 20px;
    border-right: 2px solid #eee;
}
.sidebar-left h3 {
    margin-top: 0;
}
.sidebar-left ul {
    list-style-type: none;
    padding: 0;
}
.sidebar-left li {
    margin-bottom: 10px;
}

/* Styles du contenu principal */
.container {
    max-width: 1200px;
    margin: 20px auto;
    padding: 0 20px;
}
h1 {
    text-align: center;
    color: #333;
}
.card {
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 15px;
    margin: 10px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
.card img {
    width: 100%;
    border-radius: 4px;
}
.card-title, .card-description {
    /* ... (styles identiques à avant) ... */
}
.card-button {
    display: block;
    background-color: #007bff;
    color: #fff;
    text-align: center;
    padding: 10px;
    border-radius: 4px;
    text-decoration: none;
    margin-top: 15px;
}

/* NOUVEAU : Styles de base pour le footer */
.main-footer {
    background-color: #333;
    color: #fff;
    padding: 20px;
    margin-top: 30px;
}


/* --- C'est ici que votre TP commence --- */

/* (Ajoutez les styles des étapes 1-3 de l'exercice précédent ici) */
.main-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.main-nav ul {
    display: flex; /* N'oubliez pas celui-ci ! */
}
```

-----
### **Étape 1 : Aligner le Header**

**Constat :** Ouvrez `index.html` dans votre navigateur. Le logo "SNEAKERS" et la liste de navigation sont empilés verticalement. Nous voulons qu'ils soient sur la même ligne.

**Question :** Comment utiliser Flexbox pour placer le logo et la navigation (`.main-nav`) sur la même ligne, à l'intérieur du conteneur `.main-header` ?

> ### 💡 Concept Traité : `display: flex`
>
>   * **Le Problème :** Par défaut, les `<div>` et les `<nav>` sont des éléments de type `block`. Ils prennent 100% de la largeur et se placent les uns sous les autres.
>   * **La Solution :** Appliquer `display: flex` au **conteneur parent** (ici, `.main-header`).
>   * **Effet :** Les enfants directs (ici, `.logo` et `.main-nav`) deviennent des "items flex" et se placent par défaut sur une ligne horizontale (appelée l'**Axe Principal**).

**Votre Tâche :** Ajoutez le code suivant dans `style.css`.

```css
.main-header {
    display: flex;
}
```

-----

### **Étape 2 : Distribuer l'espace du Header**

**Constat :** C'est mieux \! Le logo et la navigation sont sur la même ligne. Mais ils sont collés à gauche. Nous voulons que le logo soit à gauche et la navigation complètement à droite.

**Question :** Comment utiliser la propriété Flexbox qui gère la distribution de l'espace sur l'Axe Principal pour atteindre cet objectif ?

> ### 💡 Concept Traité : `justify-content`
>
>   * **Le Concept :** `justify-content` contrôle comment les items sont espacés le long de l'**Axe Principal** (l'axe horizontal par défaut).
>   * **Les Valeurs Utiles :**
>       * `flex-start` (défaut) : Tout au début.
>       * `flex-end` : Tout à la fin.
>       * `center` : Tout au centre.
>       * `space-between` : Espace *entre* les items. Le premier est collé au début, le dernier à la fin.
>       * `space-around` : Espace *autour* de chaque item.
>
> **Votre Tâche :** Ajoutez cette propriété au sélecteur `.main-header`.

```css
.main-header {
    display: flex;
    justify-content: space-between;
}
```

-----

### **Étape 3 : Centrer verticalement le Header**

**Constat :** Le logo et la navigation sont bien distribués. Cependant, si le logo était plus grand (ou avait un `padding` différent), ils ne seraient pas parfaitement centrés verticalement.

**Question :** Comment s'assurer que les items du header sont toujours parfaitement centrés sur l'axe vertical (l'Axe Secondaire) ?

> ### 💡 Concept Traité : `align-items`
>
>   * **Le Concept :** `align-items` contrôle comment les items sont alignés le long de l'**Axe Secondaire** (l'axe vertical, par défaut).
>   * **La Valeur Magique :** `center`. C'est la solution la plus simple et la plus robuste en CSS pour centrer des éléments verticalement à l'intérieur d'un conteneur parent.
>
> **Votre Tâche :** Ajoutez cette propriété au sélecteur `.main-header`.

```css
.main-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

*(Note : vous remarquerez aussi que les liens de navigation sont empilés. Appliquez `display: flex` à `.main-nav ul` pour les aligner aussi \!)*

-----

### **Étape 4 : Créer la Mise en Page Principale (Sidebar + Contenu)**

**Constat :** Notre header est parfait. Mais en dessous, la sidebar (`.sidebar-left`) et le contenu (`.main-content`) s'empilent verticalement. Nous voulons qu'ils soient côte à côte.

**Question :** Comment utiliser Flexbox sur le conteneur `.page-content` pour placer la sidebar à gauche et le contenu principal à droite ?

> ### 💡 Concept Traité : `display: flex` (pour la mise en page)
>
>   * **Le Concept :** Tout comme pour le header, nous allons appliquer `display: flex` au conteneur parent (`.page-content`). Ses enfants directs (`.sidebar-left` et `.main-content`) vont s'aligner horizontalement.
>
> **Votre Tâche :** Ajoutez le code suivant.

```css
.page-content {
    display: flex;
}
```

-----

### **Étape 5 : Gérer la Taille du Contenu et de la Sidebar**

**Constat :** Ils sont côte à côte \! Mais la sidebar prend beaucoup de place. Nous voulons qu'elle ait une largeur fixe (ex: 200px) et que le contenu principal prenne *tout le reste de l'espace disponible*.

**Question :** Comment assigner une taille de base fixe à la sidebar et dire au contenu principal de "grandir" pour remplir l'espace ?

> ### 💡 Concepts Traités : `flex-basis` et `flex-grow`
>
>   * **Le Concept :** Ces propriétés s'appliquent aux **enfants** flex.
>   * `flex-basis: 200px` : C'est comme `width`. Il définit la taille de base de l'élément.
>   * `flex-shrink: 0` : (0 = non) On dit à la sidebar de *ne pas* rétrécir, même si l'espace manque.
>   * `flex-grow: 1` : (1 = oui) On dit au `.main-content` de "grandir" pour occuper tout l'espace vide restant sur la ligne.
>
> **Votre Tâche :** Ajoutez ces styles pour la sidebar et le contenu.

```css
.sidebar-left {
    flex-basis: 200px;
    flex-shrink: 0; /* Important: ne pas la laisser rétrécir */
}

.main-content {
    flex-grow: 1;
    /* (Optionnel) Ajoutons un min-width pour éviter qu'il soit trop écrasé */
    min-width: 300px; 
}
```

-----

### **Étape 6 : Créer la Galerie de Produits (Responsive)**

**Constat :** La structure de notre page est bonne. Maintenant, concentrons-nous *à l'intérieur* du `.main-content`. Les 4 cartes de produits s'empilent verticalement.

**Question :** Comment transformer le `.product-gallery` en un conteneur flexible qui permet à ses enfants de "s'enrouler" (passer à la ligne) s'ils n'ont plus de place ?

> ### 💡 Concept Traité : `flex-wrap: wrap`
>
>   * **Le Problème :** Si on applique juste `display: flex`, tous les items vont essayer de tenir sur une seule ligne.
>   * **La Solution :** `flex-wrap: wrap;` dit au conteneur : "Fais tenir les items sur la ligne. Si tu n'as plus de place, passe à la ligne suivante".
>
> **Votre Tâche :** Ajoutez le code suivant.

```css
.product-gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center; /* Centrons les cartes pour un meilleur look */
}
```

-----

### **Étape 7 : Contrôler la Taille des Cartes**

**Constat :** Les cartes sont en ligne et passent à la ligne \! Mais elles sont toutes petites. Nous voulons qu'elles aient une taille de base, mais qu'elles s'adaptent.

**Question :** Comment dire à chaque `.card` : "Ta taille de base est de 300px, mais tu peux grandir ou rétrécir pour t'adapter à la grille" ?

> ### 💡 Concept Traité : `flex` (le raccourci)
>
>   * **Le Concept :** On utilise la propriété `flex` sur les **enfants** (les cartes).
>   * **La Syntaxe :** `flex: <flex-grow> <flex-shrink> <flex-basis>;`
>   * `flex: 1 1 300px;` signifie :
>       * `grow: 1` (Oui, tu peux grandir)
>       * `shrink: 1` (Oui, tu peux rétrécir)
>       * `basis: 300px` (Ta taille de base est 300px)
>
> **Votre Tâche :** Modifiez le sélecteur `.card`.

```css
.card {
    /* ... (tous les styles de carte existants) ... */
    margin: 10px;
    
    /* On remplace width par flex : */
    flex: 1 1 300px; 
    
    /* Assurons-nous qu'elle ne dépasse pas une taille max */
    max-width: 350px;
    
    /* On transforme la carte en conteneur flex vertical (pour le bonus) */
    display: flex;
    flex-direction: column;
}
```

-----

### **Étape 8 (Bonus) : Aligner le Bouton en bas de la Carte**

**Constat :** Les cartes n'ont pas la même hauteur à cause du texte. Les boutons ne sont pas alignés.

**Question :** Nous avons déjà transformé la `.card` en `flex-direction: column` à l'étape 7. Comment forcer le bouton `.card-button` à toujours être aligné en bas ?

> ### 💡 Concept Traité : `margin: auto` (dans un conteneur Flex)
>
>   * **L'Astuce :** Dans un conteneur Flex (même vertical), `margin: auto` absorbe tout l'espace disponible.
>   * **La Solution :** En appliquant `margin-top: auto;` au bouton, on lui dit : "Prends tout l'espace vide disponible *au-dessus* de toi". Cela le pousse donc en bas de la carte.
>
> **Votre Tâche :** Modifiez le sélecteur `.card-button`.

```css
.card-button {
    /* ... (tous les styles de bouton existants) ... */
    
    /* La magie est ici : */
    margin-top: auto;
}
```

-----

### **Étape 9 (Finale) : Centrer le Pied de Page**

**Constat :** Le pied de page (`.main-footer`) est là, mais le texte est collé à gauche.

**Question :** Comment utiliser Flexbox pour centrer parfaitement le paragraphe `<p>` à l'intérieur du `.main-footer`, à la fois horizontalement et verticalement ?

> ### 💡 Concept Traité : `justify-content` et `align-items` (pour les petits composants)
>
>   * **Le Concept :** Flexbox n'est pas seulement pour les grandes mises en page \! Il est parfait pour centrer des items dans un conteneur.
>   * `justify-content: center;` : Centre sur l'Axe Principal (horizontal).
>   * `align-items: center;` : Centre sur l'Axe Secondaire (vertical).
>
> **Votre Tâche :** Ajoutez ces styles au `.main-footer`.

```css
.main-footer {
    background-color: #333;
    color: #fff;
    padding: 20px;
    margin-top: 30px;

    /* On ajoute flex pour centrer le contenu */
    display: flex;
    justify-content: center;
    align-items: center;
    
    /* Donnons-lui une hauteur pour voir l'effet vertical */
    min-height: 100px;
}
```
### Étape 10 : Stylisation du Header (Menu de Navigation Principal) 🎨

**Constat :** Le header est fonctionnel (logo à gauche, liens à droite), mais les liens sont bruts.

**Question A :** Comment donner un aspect de boutons aux liens de navigation (ex: `#555` comme couleur de texte, `padding` horizontal de `15px` et vertical de `5px`, et une légère bordure de fond au survol pour indiquer une interaction) ?

> **💡 Concept Traité :** CSS de base et pseudo-classe **`:hover`**
> Ciblez les balises `<a>` à l'intérieur de `.main-nav ul li`.

**Question B :** Le header est déjà un conteneur Flexbox. Comment utiliser cette propriété pour que les liens soient bien espacés **sans utiliser de `margin`** sur les `li` ?

> **💡 Concept Alternative :** `gap`
> La propriété `gap` (ou `column-gap`) est idéale pour ajouter un espacement uniforme entre les éléments Flexbox enfants (les `li` dans `.main-nav ul`).

### Étape 11 : Stylisation du Menu Latéral (Sidebar) ✨

**Constat :** La sidebar est alignée correctement (Étape 3), mais ses liens sont basiques et la navigation n'est pas claire.

**Question A :** Comment styliser les liens de la sidebar pour qu'ils ressemblent à une liste de filtres cliquables (ex: couleur de texte bleue, taille de police `16px`, et un `padding` uniforme de `8px` pour agrandir la zone de clic) ?

> **💡 Concept Traité :** Ciblages CSS précis
> Assurez-vous de cibler les balises `<a>` dans `.sidebar-left ul li` et de les mettre en `display: block` pour que le `padding` et la couleur de fond remplissent toute la largeur.

**Question B :** Comment faire apparaître une **barre de couleur** (ex: `#007bff`) à gauche de chaque lien de la sidebar lorsque l'utilisateur le survole, pour indiquer clairement l'élément pointé ?

> **💡 Concepts Traités :** **`:hover`** et `border-left`
> Utilisez la pseudo-classe `:hover` pour appliquer une propriété `border-left` sur le lien.

-----