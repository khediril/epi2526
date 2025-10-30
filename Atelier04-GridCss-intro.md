
#  Travaux Pratiques : Maîtriser la Disposition avec CSS Grid

## Objectif du TP : De Zéro à une Mise en Page Complète

Ce TP vous guidera pour transformer la même page HTML de "Sneakers" en une mise en page complète, en utilisant cette fois **CSS Grid** pour la structure principale et la galerie.

**Projet :** Créer la structure d'une page produit (Header, Sidebar, Contenu, Footer) en définissant une "grille" pour l'ensemble de votre page.

---

## 1. Fichiers de Départ (Exactement les mêmes)

Utilisez exactement les mêmes fichiers `index.html` et `style.css` que pour le TP Flexbox. L'objectif est de montrer que l'on peut changer radicalement la mise en page **sans jamais toucher au HTML**.

### 1.1. Fichier `index.html` (La Structure)
*(Utilisez le même fichier que l'exercice précédent. Vous n'avez rien à y changer.)*

### 1.2. Fichier `style.css` (Styles de Base)
*(Utilisez le même fichier de départ que l'exercice précédent. Assurez-vous qu'il ne contient aucune propriété Flexbox ou Grid pour l'instant.)*

---

## 2. Les Étapes du TP : Penser en Grilles

La philosophie de Grid est de concevoir la "structure" d'abord. Nous allons donc commencer par définir la grille globale de notre page.

### Étape 1 : Définir la "Grille Maîtresse" de la Page

**Constat :** Notre `<body>` contient trois enfants directs : `<header>`, `.page-content` et `<footer>`. Ils sont empilés. Nous voulons qu'ils s'organisent verticalement et que la page prenne au moins 100% de la hauteur de l'écran.

**Question :** Comment transformer le `<body>` en un conteneur Grid qui définit 3 **lignes** :
1.  Une ligne pour le header (`.main-header`) qui prend sa hauteur de contenu (`auto`).
2.  Une ligne pour le `.page-content` qui prend **tout l'espace vertical restant** (`1fr`).
3.  Une ligne pour le footer (`.main-footer`) qui prend sa hauteur de contenu (`auto`).

> ###  Concepts Traités :
> * `display: grid` : Transforme un élément en conteneur de grille.
> * `min-height: 100vh` : Force l'élément (`body`) à prendre au moins 100% de la hauteur de la fenêtre (viewport height).
> * `grid-template-rows` : Définit les pistes (lignes) de notre grille.
> * `auto` : La piste s'adapte à la hauteur de son contenu.
> * `1fr` : L'unité de fraction. Signifie "1 fraction de l'espace *disponible*". C'est ce qui permet à la ligne du milieu de s'étendre.
>
> **Tâche :** Appliquez ces styles au sélecteur `body`.

### Étape 2 : Définir la Structure du Contenu Principal

**Constat :** La structure verticale de la page est bonne ! Maintenant, concentrons-nous sur `.page-content`. À l'intérieur, la sidebar (`.sidebar-left`) et le contenu (`.main-content`) sont toujours empilés.

**Question :** Comment transformer le `.page-content` en un conteneur Grid qui définit 2 **colonnes** :
1.  Une colonne pour la sidebar, d'une largeur **fixe** de **200px**.
2.  Une colonne pour le contenu principal, qui prend **tout l'espace horizontal restant** (`1fr`).

> ###  Concepts Traités :
> * `display: grid` (imbriqué) : Un item de la grille (`.page-content`) devient lui-même un conteneur de grille.
> * `grid-template-columns` : Définit les pistes (colonnes) de notre grille.
>
> **Tâche :** Appliquez ces styles au sélecteur `.page-content`.

### Étape 3 : Créer la Galerie de Produits (La Magie de Grid)

**Constat :** Les cartes de produits (`.card`) sont empilées dans la zone de contenu.

**Question :** C'est ici que Grid est très puissant. Comment transformer le `.product-gallery` en une grille **automatiquement responsive** qui :
1.  Crée autant de colonnes que possible (`auto-fit`).
2.  S'assure que chaque colonne a une taille **minimale de 300px** (`minmax(300px, ...)`).
3.  Partage l'espace restant équitablement entre les colonnes (`... 1fr`).
4.  Ajoute un espace (`gap`) entre les cartes ?

> ###  Concepts Traités :
> * `display: grid`
> * `gap` : Raccourci pour `grid-gap`. C'est l'espace entre les cellules de la grille.
> * `repeat()` : Une fonction pour répéter une définition de piste.
> * `auto-fit` : Crée autant de pistes (colonnes) que possible sans déborder, en se basant sur la taille définie.
> * `minmax(min, max)` : Définit une plage de taille. Ici, `minmax(300px, 1fr)` signifie : "Chaque colonne doit faire *au moins* 300px, mais si tu as de la place en plus, partage-la équitablement (1fr)".
>
> **Tâche :** Appliquez ces styles au `.product-gallery` en utilisant `grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));`.

### Étape 4 : Aligner le Contenu des Cartes (Bonus Grid)

**Constat :** Les boutons des cartes ne sont pas alignés, car le texte a une hauteur variable. L'astuce `margin-top: auto` est spécifique à Flexbox.

**Question :** Comment pouvons-nous utiliser **Grid à l'intérieur de la carte** pour résoudre ce problème ? Nous voulons que la `.card` ait 3 lignes :
1.  L'image (`auto`).
2.  Le texte (qui doit **grandir** pour remplir l'espace vide, `1fr`).
3.  Le bouton (`auto`).

> ###  Concepts Traités :
> * `display: grid` (encore une grille imbriquée !)
> * `grid-template-rows: auto 1fr auto` : Nous définissons 3 lignes. La première et la dernière s'adaptent à leur contenu, et celle du milieu (`1fr`) prend tout l'espace restant, poussant le bouton vers le bas.
>
> **Tâche :** Appliquez ces styles à l'élément `.card`.

### Étape 5 : Finaliser le Header et le Footer (Le Bon Outil pour le Bon Travail)

**Constat 1 (Header) :** Le logo et la navigation sont toujours empilés. C'est un simple alignement sur une ligne.
**Constat 2 (Footer) :** Le texte du pied de page est collé à gauche.

**Question A (Header) :** Pour un simple alignement 1D (logo à gauche, nav à droite), **Flexbox** reste souvent l'outil le plus simple et le plus direct. Comment utiliser Flexbox *à l'intérieur* de notre header (qui est un item Grid) pour aligner le logo et la navigation ?
> ** Concepts Traités :** `display: flex`, `justify-content: space-between`, `align-items: center`.
> *Note : C'est une leçon importante. Grid et Flexbox ne sont pas ennemis, ils sont complémentaires !*
>
> **Tâche :** Appliquez ces styles au `.main-header`. (N'oubliez pas d'appliquer aussi `display: flex` au `.main-nav ul`).

**Question B (Footer) :** Quelle est la commande CSS Grid la plus **simple et la plus courte** pour centrer parfaitement un item (le `<p>`) à la fois horizontalement et verticalement à l'intérieur de son conteneur (`.main-footer`) ?
> ###  Concepts Traités :
> * `display: grid`
> * `place-items: center` : C'est le raccourci magique qui combine `align-items: center` et `justify-items: center`.
>
> **Tâche :** Appliquez ces styles au `.main-footer`.
