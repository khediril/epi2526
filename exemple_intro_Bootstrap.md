
# 🚀 TP introduction : Mon Premier Portfolio avec Bootstrap 5

**Objectif :** Construire une page "responsive" (qui s'adapte aux mobiles) sans écrire une seule ligne de CSS personnalisé, en comprenant la "philosophie" Bootstrap.

**Outils :** Un simple éditeur de code (comme VS Code) et un navigateur.



### Étape 0 : La Préparation (Le "Starter Template")

Avant de construire, il nous faut les fondations. Bootstrap s'ajoute à n'importe quel fichier HTML.

> **💡 Concept : L'installation (CDN)**
> Nous n'allons rien télécharger. Nous allons utiliser le **CDN** (Content Delivery Network) : Bootstrap nous "prête" ses fichiers CSS et JS depuis ses serveurs rapides.

**Action :**

1.  Créez un fichier `index.html`.
2.  Copiez-collez ce "Starter Template" officiel. C'est votre point de départ pour **tous** vos projets Bootstrap.

<!-- end list -->

```html
<!doctype html>
<html lang="fr">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

    <title>Mon Portfolio</title>
  </head>
  <body>
    <h1>Bonjour, le monde !</h1>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  </body>
</html>
```

Ouvrez `index.html` dans votre navigateur. Vous devriez voir "Bonjour, le monde \!" avec une police déjà un peu différente. C'est la preuve que Bootstrap est activé \!

-----

### Étape 1 : Le Conteneur (La "Boîte" Principale)

**Constat :** Notre "Bonjour, le monde \!" est collé au bord gauche de l'écran. C'est inesthétique.

> **💡 Concept : `.container`**
> Bootstrap fonctionne en "enveloppant" votre contenu dans des conteneurs. La classe `.container` centre votre contenu et lui donne des marges latérales automatiques.

**Action :**
Remplacez le `<h1>` de l'étape 0 par ce code :

```html
<div class="container">
  <h1>Bonjour, le monde !</h1>
  <p>Ceci est ma première page Bootstrap.</p>
</div>
```

**Résultat :** Actualisez votre page. Le texte est maintenant centré, avec de l'espace sur les côtés. C'est plus propre \!

-----

### Étape 2 : Les Utilitaires (La Magie Instantanée)

Commençons à "peindre" avec Bootstrap, sans écrire de CSS.

> **💡 Concept : Les Classes Utilitaires (Utilities)**
> Bootstrap vous donne des milliers de classes "d'aide" pour faire une seule chose. `p-*` pour le `padding`, `m-*` pour la `margin`, `bg-*` pour le `background-color`, `text-*` pour le `color`.

**Action :**
Transformons notre simple `<h1>` en une jolie section d'introduction (un "jumbotron" simple). Modifiez votre `.container` comme suit :

```html
<div class="container">
  <div class="p-5 my-5 bg-light text-center">
    <h1>Jean Dupont</h1>
    <p>Développeur Web Novice, passionné par Bootstrap.</p>
  </div>
</div>
```

**Résultat :** En ajoutant 4 classes, nous avons créé une section d'en-tête stylisée.

-----

### Étape 3 : Les Composants (Les Pièces LEGO)

Bootstrap fournit des "composants" pré-fabriqués. Le plus simple est le bouton.

> **💡 Concept : Les Composants (`.btn`)**
> Pour faire un bouton, il suffit d'ajouter la classe `.btn` à un lien `<a>` ou un bouton `<button>`. On ajoute une couleur avec `.btn-*` (ex: `.btn-primary` pour le bleu).

**Action :**
Ajoutons un bouton "Contactez-moi" dans notre section d'en-tête.

```html
<div class="container">
  <div class="p-5 my-5 bg-light text-center">
    <h1>Jean Dupont</h1>
    <p>Développeur Web Novice, passionné par Bootstrap.</p>
    
    <a href="#" class="btn btn-primary">Me Contacter</a>
  </div>
</div>
```

**Résultat :** Nous avons un bouton bleu professionnel sans écrire une ligne de CSS.

-----

### Étape 4 : La Grille (Le Concept Fondamental)

C'est le pilier de Bootstrap. **La grille divise l'espace en 12 colonnes virtuelles.**

> **💡 Concept : `.row` et `.col-`**
>
> 1.  On crée une "ligne" (`<div class="row">`).
> 2.  On remplit cette ligne avec des "colonnes" (`<div class="col-...">`).
> 3.  La somme des colonnes dans une `row` doit faire **12**.

**Action :**
Nous voulons créer une section "Mes Compétences" avec 3 colonnes de largeur égale. Si on a 12 colonnes au total, 12 / 3 = 4. Chaque colonne aura la classe `.col-4`.

Ajoutez ce bloc *après* votre section d'en-tête (mais toujours *dans* le `.container`).

```html
<div class="row">
  <div class="col-4">
    <h4>HTML 5</h4>
    <p>Structure sémantique.</p>
  </div>
  
  <div class="col-4">
    <h4>CSS 3</h4>
    <p>Styles et animations.</p>
  </div>
  
  <div class="col-4">
    <h4>Bootstrap 5</h4>
    <p>Grilles et composants.</p>
  </div>
</div>
```

**Résultat :** Vous avez 3 colonnes parfaitement alignées.

-----

### Étape 5 : La Réactivité (Le "Mobile-First")

**Constat :** Redimensionnez votre fenêtre pour la rendre très étroite (comme un téléphone). Les 3 colonnes deviennent écrasées et illisibles.

> **💡 Concept : Les Points de Rupture (Breakpoints)**
> On dit à Bootstrap comment se comporter sur différentes tailles d'écran. Le préfixe le plus courant est `md` (medium, pour les tablettes et plus).
>
>   * `col-4` signifie "sois 4/12 **tout le temps** (même sur mobile)".
>   * `col-md-4` signifie "sois 4/12 **seulement** sur les écrans `md` (medium) ou plus grands. Sur les écrans plus petits (mobile), prends 100% de la largeur."

**Action :**
Modifions simplement nos classes de `col-4` à `col-md-4`.

```html
<div class="row">
  <div class="col-md-4">
    <h4>HTML 5</h4>
    <p>Structure sémantique.</p>
  </div>
  
  <div class="col-md-4">
    <h4>CSS 3</h4>
    <p>Styles et animations.</p>
  </div>
  
  <div class="col-md-4">
    <h4>Bootstrap 5</h4>
    <p>Grilles et composants.</p>
  </div>
</div>
```

**Résultat :** Actualisez. Sur un grand écran, rien ne change. Mais si vous réduisez la fenêtre, les 3 colonnes vont "s'empiler" proprement les unes sous les autres. Magique, non ?

-----

### Étape 6 : Combiner Grille et Composants

Les colonnes vides, c'est bien, mais mettons-y du contenu. Le composant `.card` (carte) est parfait pour cela.

> **💡 Concept : Imbrication**
> On peut mettre des composants (comme les `.card`) à l'intérieur des colonnes de la grille.

**Action :**
Remplaçons le texte simple de nos 3 colonnes par des "cartes".

```html
<div class="row">
  
  <div class="col-md-4">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">HTML 5</h5>
        <p class="card-text">Structure sémantique.</p>
      </div>
    </div>
  </div>
  
  <div class="col-md-4">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">CSS 3</h5>
        <p class="card-text">Styles et animations.</p>
      </div>
    </div>
  </div>
  
  <div class="col-md-4">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">Bootstrap 5</h5>
        <p class="card-text">Grilles et composants.</p>
      </div>
    </div>
  </div>
  
</div>
```

**Résultat :** Vous avez une page de profil propre, responsive, avec une section d'en-tête et une grille de cartes.

-----

### ✨ TP Terminé \!

Vous venez de maîtriser les 4 concepts fondamentaux de Bootstrap :

1.  **L'Installation** (CDN)
2.  **Les Conteneurs** (`.container`)
3.  **Les Utilitaires** (`.p-5`, `.bg-light`, `.text-center`)
4.  **La Grille Responsive** (`.row`, `.col-md-4`)
5.  **Les Composants** (`.btn`, `.card`)