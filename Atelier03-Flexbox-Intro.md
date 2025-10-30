#  Travaux Pratiques : Maîtriser la Disposition avec CSS Flexbox

## Objectif du TP : De Zéro à une Mise en Page Complète

Ce TP vous guidera, étape par étape, pour transformer une page HTML simple en une mise en page de site e-commerce complète, en utilisant exclusivement **CSS Flexbox**.

**Projet :** Créer la structure d'une page produit de "Sneakers" avec un Header, une Sidebar latérale, le Contenu Principal (Galerie de Produits) et un Footer.

-----

## 1\. Fichiers de Départ (Structure HTML et Styles Initiaux)

Créez deux fichiers : `index.html` et `style.css`.

### 1.1. Fichier `index.html` (La Structure)

Copiez cette structure HTML de départ. Elle contient toutes les balises nécessaires, mais n'est pas encore agencée.

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
                        <img src="https://placehold.co/300x200?text=Sneaker+1" alt="Sneaker 1">
                        <h3 class="card-title">Modèle Air Max</h3>
                        <p class="card-description">Confort et style, le classique revisité pour 2025.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>
                    
                    <div class="card">
                        <img src="https://placehold.co/300x200?text=Sneaker+2" alt="Sneaker 2">
                        <h3 class="card-title">Modèle Runner</h3>
                        <p class="card-description">Parfaite pour vos sessions de course, légère et durable.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>
                    
                    <div class="card">
                        <img src="https://placehold.co/300x200?text=Sneaker+3" alt="Sneaker 3">
                        <h3 class="card-title">Modèle Urbain</h3>
                        <p class="card-description">Le style de rue à l'état pur. Stock limité.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>
                    
                    <div class="card">
                        <img src="https://placehold.co/300x200?text=Sneaker+4" alt="Sneaker 4">
                        <h3 class="card-title">Modèle Classique</h3>
                        <p class="card-description">Simple, efficace, indémodable.</p>
                        <a href="#" class="card-button">Voir le produit</a>
                    </div>

                </div>
            </div>
        </main>

    </div> 

    <footer class="main-footer">
        <p>&copy; 2025 Sneakers Inc. Tous droits réservés.</p>
    </footer>

</body>
</html>
```

### 1.2. Fichier `style.css` (Styles de Base)

Copiez ces styles initiaux. Ils donnent une apparence minimale aux éléments mais ne contiennent **aucune** propriété Flexbox.

```css
/* Styles de base et réinitialisation */
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
.main-nav ul, .sidebar-left ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
}
.main-nav a, .sidebar-left a {
    text-decoration: none;
    color: #555;
    font-weight: bold;
}
.sidebar-left {
    background-color: #fff;
    padding: 20px;
    border-right: 2px solid #eee;
}
.sidebar-left li {
    margin-bottom: 10px;
}
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
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
.card img {
    width: 100%;
    border-radius: 4px;
}
.card-title {
    font-size: 1.2em;
    margin: 10px 0;
}
.card-description {
    font-size: 0.9em;
    color: #666;
    line-height: 1.4;
}
.card-button {
    display: block;
    background-color: #007bff;
    color: #fff;
    text-align: center;
    padding: 10px;
    border-radius: 4px;
    margin-top: 15px;
}
.main-footer {
    background-color: #333;
    color: #fff;
    padding: 20px;
    margin-top: 30px;
}
/* Ajoutez votre code Flexbox ci-dessous */
```

-----

## 2\. Les Étapes du TP : Application Incrémentale de Flexbox

### Étape 1 : Aligner les Éléments du Header

**Constat :** Dans la page, le logo (`.logo`) et la navigation (`.main-nav`) s'empilent verticalement. Les liens de navigation eux-mêmes (`li`) s'empilent également.

**Question A :** Comment placer le logo et la navigation sur la même ligne ?

> ** Concept Traité :** `display: flex`
> Appliquez-le au conteneur parent du logo et de la navigation.

**Question B :** Comment faire en sorte que les éléments de navigation (`li`) s'affichent les uns à côté des autres ?

> ** Concept Traité :** `display: flex` (imbrication)
> Appliquez-le au parent des `li`.

### Étape 2 : Distribuer l'Espace du Header

**Constat :** Les éléments du header sont alignés mais collés à gauche.

**Question A :** Comment positionner le logo à l'extrême gauche et la navigation à l'extrême droite ?

> ** Concept Traité :** `justify-content` (sur l'Axe Principal)
> Trouvez la bonne valeur pour créer un espace entre les deux blocs.

**Question B :** Le logo et les liens peuvent ne pas être parfaitement alignés verticalement. Comment les centrer précisément l'un par rapport à l'autre ?

> ** Concept Traité :** `align-items` (sur l'Axe Secondaire)
> Utilisez la propriété qui centre les items sur la hauteur du conteneur.

### Étape 3 : Structurer la Mise en Page Globale (Sidebar)

**Constat :** En dessous du header, la sidebar (`.sidebar-left`) et le contenu principal (`.main-content`) s'affichent l'un sous l'autre.

**Question A :** Comment placer la sidebar et le contenu principal côte à côte ?

> ** Concept Traité :** `display: flex`
> Appliquez-le au conteneur `.page-content`.

**Question B :** Comment garantir que la sidebar ait une largeur fixe de **200px** et que le contenu principal prenne tout l'espace restant ?

> ** Concepts Traités :** `flex-basis` et `flex-grow`
> Appliquez `flex-basis` et `flex-shrink: 0` à la sidebar. Appliquez `flex-grow` au `.main-content`.

### Étape 4 : Créer la Galerie de Produits Responsive

**Constat :** Les cartes de produits (`.card`) sont toujours empilées verticalement à l'intérieur du `.product-gallery`.

**Question A :** Comment faire en sorte que les cartes s'alignent horizontalement et passent à la ligne si l'espace manque ?

> ** Concepts Traités :** `display: flex` et `flex-wrap`
> Ces deux propriétés doivent être appliquées au conteneur de la galerie (`.product-gallery`).

**Question B :** Comment donner une taille de base de **300px** à chaque carte, tout en leur permettant de grandir et de rétrécir pour remplir la grille ?

> ** Concept Traité :** La propriété raccourcie `flex`
> Utilisez la forme `flex: <grow> <shrink> <basis>` sur les éléments `.card`.

### Étape 5 : Finaliser le Design des Cartes et du Footer

**Constat :** En raison de la quantité de texte (description), les boutons "Voir le produit" ne sont pas alignés en bas des cartes, ce qui est visuellement désordonné.

**Question A (Bouton en Bas) :** Comment forcer le bouton (`.card-button`) à s'aligner toujours en bas de la carte, quelle que soit la hauteur du texte au-dessus ?

> ** Concepts Traités :** `flex-direction: column` et `margin: auto`
>
> 1.  Transformez la `.card` en un conteneur flex vertical.
> 2.  Appliquez la propriété magique `margin-top: auto` sur le `.card-button`.

**Question B (Footer) :** Comment centrer le texte du pied de page (`<p>`) horizontalement et verticalement à l'intérieur du `.main-footer` ?

> ** Concepts Traités :** `display: flex`, `justify-content` et `align-items`
> Appliquez les trois propriétés au `.main-footer`.
