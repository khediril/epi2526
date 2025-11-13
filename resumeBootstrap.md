## 1\. Qu'est-ce que Bootstrap ? (L'Idée Fondamentale)

Pensez à Bootstrap comme à un **énorme kit de construction LEGO®** pour sites web.

  * **HTML** est la structure de base (les fondations).
  * **CSS** est la peinture et la décoration que vous faites vous-même (c'est long).
  * **Bootstrap** est un ensemble de **pièces préfabriquées** (boutons, menus, grilles) que vous assemblez rapidement pour construire un site web.

**Pourquoi l'utiliser ?**

1.  **Rapidité :** Vous n'avez pas à réécrire le même code CSS pour un bouton ou un menu sur chaque projet.
2.  **Responsive (Mobile-First) :** C'est le cœur de Bootstrap. Votre site s'adaptera **automatiquement** aux téléphones, tablettes et ordinateurs de bureau.
3.  **Cohérence :** Votre design sera propre et cohérent sans effort.

-----

## 2\. L'Installation (Le "Modèle de Départ")

Pour commencer, vous n'avez rien à télécharger. La façon la plus simple d'utiliser Bootstrap est d'utiliser le **CDN** (Content Delivery Network).

Copiez-collez simplement ce code dans un fichier `index.html`. C'est votre "modèle de départ" pour tout projet Bootstrap.

```html
<!doctype html>
<html lang="fr">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

    <title>Mon Site Bootstrap</title>
  </head>
  <body>
    <h1>Bonjour, le monde !</h1>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  </body>
</html>
```

**Points Clés :**

  * **`<meta name="viewport">` :** C'est la ligne **la plus importante**. Elle dit aux navigateurs mobiles de ne pas "dézoomer" votre page et de respecter le design responsive.
  * **`<link>` (CSS) :** Il va dans le `<head>`. C'est lui qui contient *tous* les styles.
  * **`<script>` (JS) :** Il va à la fin du `<body>`. Il est nécessaire pour les composants interactifs (comme les menus déroulants ou les modales).

-----

## 3\. Pilier n°1 : Le Système de Grille (Layout)

C'est le concept **le plus important** de Bootstrap. La grille vous permet de structurer votre page.

Imaginez que chaque ligne horizontale de votre site est divisée en **12 colonnes virtuelles**.

La mise en page se fait en combinant trois classes :

1.  **.container** : C'est la "boîte" principale qui enveloppe votre contenu.

      * `.container` : Largeur fixe, centrée, avec des marges.
      * `.container-fluid` : Prend 100% de la largeur de l'écran.

2.  **.row** : C'est une "ligne" horizontale. Elle doit **toujours** être à l'intérieur d'un `.container`. Une `.row` est un conteneur Flexbox.

3.  **.col-**\* : C'est une "colonne". C'est là que vous mettez votre contenu. Les colonnes doivent **toujours** être les enfants directs d'une `.row`.

**Exemple de base : 50% / 50%**

Si vous voulez deux colonnes de largeur égale, vous donnez à chacune la moitié des 12 colonnes, soit 6.

```html
<div class="container">
  <div class="row">
    <div class="col-6">
      Contenu de Gauche (50%)
    </div>
    <div class="col-6">
      Contenu de Droite (50%)
    </div>
  </div>
</div>
```

**Le "Mobile-First" (Les Points de Rupture)**

Maintenant, comment le rendre responsive ? Bootstrap utilise des **préfixes** pour différentes tailles d'écran :

  * `col-` (Très petit - \<576px) - *Mobile par défaut*
  * `col-sm-` (Small - ≥576px)
  * `col-md-` (Medium - ≥768px) - *Tablette*
  * `col-lg-` (Large - ≥992px) - *Bureau*
  * `col-xl-` (Extra Large - ≥1200px)

**Exemple "Responsive" classique :**

> "Je veux que mes colonnes soient à 50/50 sur **ordinateur (md)**, mais qu'elles s'empilent (100% de large) sur **mobile**."

```html
<div class="container">
  <div class="row">
    <div class="col-12 col-md-6">
      Colonne 1
    </div>
    <div class="col-12 col-md-6">
      Colonne 2
    </div>
  </div>
</div>
```

*(Redimensionnez votre navigateur pour voir la magie opérer \!)*

-----

## 4\. Pilier n°2 : Les Classes Utilitaires (Utilities)

C'est le deuxième pilier de Bootstrap 5. Au lieu d'écrire du CSS, vous utilisez des **classes d'aide** directement dans votre HTML.

C'est la philosophie "Utility-First".

### Espacement (Padding & Margin)

C'est le plus important. `m` = margin, `p` = padding.

  * `t` = top, `b` = bottom, `s` = start (gauche), `e` = end (droite)
  * `x` = axe horizontal (gauche et droite), `y` = axe vertical (haut et bas)
  * Tailles : `0` à `5` (ex: `mt-1` = petite marge en haut, `p-5` = gros padding partout)

<!-- end list -->

```html
<div class="p-3 mt-5">...</div>

<div class="px-5">...</div> 
```

### Couleurs (Texte & Fond)

Bootstrap vous donne une palette de couleurs sémantiques.

  * `primary` (bleu), `secondary` (gris), `success` (vert), `danger` (rouge), `warning` (jaune), `light` (clair), `dark` (foncé).

<!-- end list -->

```html
<p class="text-danger">Message d'erreur.</p>

<div class="bg-primary text-white p-3">
  Fond bleu avec texte blanc.
</div>
```

### Flexbox

La grille (`.row`) est déjà Flexbox, mais vous pouvez transformer *n'importe quel* élément en conteneur Flexbox.

```html
<div class="d-flex justify-content-center">
  <p>Je suis centré.</p>
</div>
```

-----

## 5\. Pilier n°3 : Les Composants (Components)

Ce sont les "pièces LEGO" prêtes à l'emploi. Ce sont des blocs de HTML pré-stylisés que vous copiez-collez depuis la documentation officielle.

**Les Incontournables :**

### Boutons (`.btn`)

Vous n'aurez plus jamais à styliser un bouton.

```html
<button type="button" class="btn btn-primary">Bouton Principal</button>
<button type="button" class="btn btn-outline-success">Bouton Secondaire</button>
```

### Cartes (`.card`)

Le conteneur de contenu le plus courant.

```html
<div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">Titre de la Carte</h5>
    <p class="card-text">Un peu de texte pour remplir la carte.</p>
    <a href="#" class="btn btn-primary">Voir plus</a>
  </div>
</div>
```

### Navbar (`.navbar`)

Un menu de navigation complet et responsive.

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">MonSite</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a class="nav-link" href="#">Accueil</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">À Propos</a>
        </li>
      </ul>
    </div>
  </div>
</nav>
```

-----

## 6\. Conclusion : La Philosophie

L'objectif de Bootstrap est d'écrire le moins de CSS personnalisé possible.

1.  Commencez toujours par la **structure (Grille)** : `.container` -\> `.row` -\> `.col-md-X`.
2.  Stylisez ensuite avec les **utilitaires (Utilities)** : `p-3`, `mt-2`, `bg-light`, `text-center`.
3.  Utilisez les **composants (Components)** : `.card`, `.btn`, `.navbar`.
4.  Si (et seulement si) vous ne pouvez pas faire ce que vous voulez avec les utilitaires, alors vous pouvez ouvrir votre propre fichier `style.css` pour la personnalisation.

La prochaine étape serait d'explorer la [documentation officielle de Bootstrap 5](https://getbootstrap.com/docs/5.3/getting-started/introduction/), qui est votre meilleur ami.