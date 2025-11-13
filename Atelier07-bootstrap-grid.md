
#  Atelier 04 : Maîtriser le Système de Grille Bootstrap (3 Heures)

Cet atelier est conçu pour vous faire passer de la théorie à la pratique, en vous permettant de construire des mises en page professionnelles et réactives.

| Durée Totale | Public Cible | Objectif Principal | Prérequis |
| :---: | :---: | :---: | :---: |
| 3h00 | Étudiants en Informatique/Web | Maîtriser la grille 12 colonnes et la réactivité (**RWD**) de Bootstrap. | HTML de base, CSS de base, Compréhension du **Box Model**. |

-----

## Module 1 : Fondations et Concepts de Base 

### 1.1. Introduction et Setup 

  * **Qu'est-ce que Bootstrap ?** C'est un *framework* CSS/JavaScript front-end qui fournit des outils prêts à l'emploi (composants, styles et **système de grille**).
  * **Le Rôle de la Grille :** Elle est la fondation de toute mise en page. Elle divise l'espace horizontal en 12 colonnes virtuelles, permettant un alignement précis sur tous les appareils.
  * **Setup :** Créez un fichier `index.html` et intégrez Bootstrap (via CDN) pour commencer.

<!-- end list -->

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TP Grille Bootstrap</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        /* CSS personnalisé pour visualiser les colonnes */
        .col, .col-md-6 { 
            border: 1px solid #0d6efd; 
            background-color: rgba(13, 110, 253, 0.1); 
            padding: 10px; 
            text-align: center;
        }
        .row {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Atelier Bootstrap Grid</h1>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

### 1.2. Concepts Clés : Conteneurs, Lignes et Colonnes 

**Construisons notre première grille.**

| Composant | Classe Bootstrap | Rôle | Explication |
| :---: | :---: | :---: | :---: |
| **Conteneur** | `container` ou `container-fluid` | **Contient tout.** Définit la largeur maximale de la mise en page. | `container` : Largeur fixe, centrée. `container-fluid` : Prend 100% de la largeur de la fenêtre. |
| **Ligne** | `row` | **Bloc horizontal.** Doit toujours être placé *dans* un conteneur. Annule les marges horizontales du conteneur. | C'est le conteneur Flexbox qui aligne horizontalement les colonnes. |
| **Colonne** | `col-*-*` | **Élément de contenu.** Doit toujours être placé *dans* une ligne. | C'est l'élément que vous remplissez de contenu. La somme des largeurs de colonne doit faire **12**. |

####  Exercice 1 : Les 12 Colonnes (Implicite et Explicite)

1.  **Répartition Égale (Implied)** : Créez une ligne (`row`) avec trois colonnes (`div` ayant la classe `col`). Observez comment elles se partagent les 12 colonnes.
2.  **Répartition Explicite (Fixed)** : Créez une nouvelle ligne. Placez une colonne de 4, une de 6, et une de 2. Vérifiez que la somme fait 12.

<!-- end list -->

```html
<div class="container">
    <h2>1. Répartition Implicite (Égale)</h2>
    <div class="row">
        <div class="col">1/3</div>
        <div class="col">2/3</div>
        <div class="col">3/3</div>
    </div>

    <h2>2. Répartition Explicite (Totale = 12)</h2>
    <div class="row">
        <div class="col-4">4 colonnes</div>
        <div class="col-6">6 colonnes</div>
        <div class="col-2">2 colonnes</div>
    </div>
</div>
```

-----

## Module 2 : La Réactivité (RWD) et les Points de Rupture 

### 2.1. Les Points de Rupture (Breakpoints) 

Le secret de Bootstrap réside dans les classes préfixées qui changent la mise en page en fonction de la taille de l'écran.

| Préfixe | Point de Rupture | Description | Utilisation |
| :---: | :---: | :---: | :---: |
| **`col-`** | \< 576px (Extra Small) | **Mobile par défaut.** | S'applique de XS jusqu'à l'infini. |
| **`col-sm-`** | ≥ 576px (Small) | Petits écrans. | S'applique de SM jusqu'à l'infini. |
| **`col-md-`** | ≥ 768px (Medium) | Tablettes (format portrait). | S'applique de MD jusqu'à l'infini. |
| **`col-lg-`** | ≥ 992px (Large) | Ordinateurs portables. | S'applique de LG jusqu'à l'infini. |
| **`col-xl-`** | ≥ 1200px (Extra Large) | Grands écrans. | S'applique de XL jusqu'à l'infini. |

### 2.2. L'Empilement et la Combinaison

####  Exercice 2 : Empilement Mobile par Défaut

**Principe :** Si aucune classe n'est spécifiée (sauf `col` sans préfixe), les éléments s'empilent naturellement sur les petits écrans.

1.  Créez une ligne avec trois colonnes. Donnez à chaque colonne la classe **`col-md-4`**.
2.  Affichez la page et redimensionnez la fenêtre.
      * **Sur ordinateur (MD et plus) :** Chaque colonne prend 4/12 de la largeur.
      * **Sur mobile (moins de 768px) :** Les colonnes reprennent leur comportement par défaut et s'empilent, prenant **100%** de la largeur.

####  Exercice 3 : La Mise en Page "Magazine" (Combinaison)

**Principe :** Il faut définir le comportement pour le mobile *avant* de le définir pour le bureau. Le comportement d'une classe *coule* vers les classes plus grandes, sauf s'il est écrasé.

1.  **Mobile (XS/SM) :** Nous voulons que tous les éléments s'empilent (prennent 12/12). *Solution :* N'utilisez pas de classe `col` sur ces tailles, ou utilisez `col-12`.
2.  **Tablette (MD) :** Nous voulons une disposition 6-6 (deux colonnes).
3.  **Bureau (LG) :** Nous voulons une disposition 4-8 (une petite sidebar, un grand contenu).

| Éléments | Comportement XS | Comportement MD | Comportement LG |
| :---: | :---: | :---: | :---: |
| Colonne 1 | 12 (Empilement) | 6/12 | 4/12 |
| Colonne 2 | 12 (Empilement) | 6/12 | 8/12 |

**Tâche :** Implémentez la structure ci-dessous en utilisant les classes combinées. Testez en redimensionnant.

```html
<h2>3. Mise en Page Magazine (Responsive)</h2>
<div class="row">
    <div class="col-md-6 col-lg-4">Sidebar (4/12 sur grand écran)</div> 
    
    <div class="col-md-6 col-lg-8">Contenu Principal (8/12 sur grand écran)</div>
</div>
```

-----

## Module 3 : Techniques Avancées 

### 3.1. Les Gouttières (Gutters) et les Décalages (Offsets) 

  * **Les Gouttières (`g` classes) :** Les gouttières sont les marges horizontales et les paddings verticaux entre les colonnes et les lignes.

      * `g-0` : Supprime les gouttières.
      * `g-5` : Gouttières maximales.
      * `gx-3` : Contrôle les gouttières **horizontales** (x-axis).
      * `gy-4` : Contrôle les gouttières **verticales** (y-axis).

  * **Les Décalages (`offset`) :** Permettent de pousser une colonne vers la droite en utilisant l'espace de colonnes vides.

#### 📝 Exercice 4 : Décalage et Centrage

1.  Créez une ligne. Nous voulons une colonne qui prenne 4/12 de la largeur, mais qui soit parfaitement **centrée** sur la ligne.
2.  **Tâche :**
      * La colonne doit prendre 4/12 (`col-4`).
      * L'espace vide restant est de (12 - 4) = 8. Nous voulons 4 colonnes de vide de chaque côté.
      * Utilisez la classe `offset-md-4` sur la colonne pour la décaler de 4.

<!-- end list -->

```html
<h2>4. Centrage par Décalage (Offset)</h2>
<div class="row">
    <div class="col-md-4 offset-md-4">Contenu Centré (col-4)</div> 
</div>
```

### 3.2. Alignement Flexbox et Ordonnancement 

Les lignes Bootstrap (`.row`) sont des conteneurs Flexbox. Vous pouvez utiliser les utilitaires Flexbox de Bootstrap pour aligner le contenu.

  * **`justify-content-*`** : Aligne les colonnes sur l'axe horizontal.
  * **`align-items-*`** : Aligne les colonnes sur l'axe vertical.
  * **`order-*`** : Change l'ordre d'affichage des colonnes indépendamment du code HTML.

####  Exercice 5 : Ordre et Alignement Vertical

1.  Créez une ligne (`row`) avec une grande hauteur (utilisez CSS personnalisé si nécessaire : `min-height: 200px;`).
2.  Placez trois colonnes (`col-4`) à l'intérieur.
3.  **Tâche A (Alignement) :** Forcez toutes les colonnes à s'aligner **en bas** de la ligne.
4.  **Tâche B (Ordre) :** La première colonne dans le HTML doit s'afficher **en dernier**.

<!-- end list -->

```html
<h2>5. Alignement et Ordonnancement</h2>
<div class="row align-items-end" style="min-height: 200px; border: 2px solid green;">
    
    <div class="col-4 order-3">Premier (mais affiché dernier)</div> 
    
    <div class="col-4 order-2">Deuxième (affiché au milieu)</div>
    
    <div class="col-4 order-1">Troisième (affiché premier)</div>
</div>
```

### 3.3. Mise en Pratique Finale

####  Exercice 6 : Le Layout 

**Tâche :** Créez une mise en page d'application complète avec les contraintes suivantes :

1.  Un **Header** et un **Footer** qui prennent toujours 100% de la largeur.
2.  Une zone de contenu avec deux éléments :
      * Une **Sidebar** à gauche (2/12) qui est fixe à partir de la taille **MD**.
      * Un **Contenu Principal** à droite (10/12) qui prend le reste de l'espace.
3.  **Réactivité :** Sur les petits écrans (SM et moins), la Sidebar doit s'empiler sous le Header, et le Contenu Principal doit prendre toute la largeur.

| Zone | Contraintes | Classes |
| :---: | :---: | :---: |
| Header | 12/12 | `col-12` |
| Sidebar | 12/12 (XS) → 2/12 (MD) | `col-12 col-md-2` |
| Contenu | 12/12 (XS) → 10/12 (MD) | `col-12 col-md-10` |

-----

##  Conclusion et Q\&R (15 min)

  * **Récapitulatif :** La grille Bootstrap repose sur la division par 12 et la logique des **points de rupture** (`-sm-`, `-md-`, etc.). Le principe est de définir le comportement du mobile d'abord, puis d'écraser ce comportement pour les écrans plus grands.
  * **Prochaines étapes :** Exploration des utilitaires de marge/padding (classes `m-*` et `p-*`) et des composants de Bootstrap (Cards, Navbar, etc.).

-----