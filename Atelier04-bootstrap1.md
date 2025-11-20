# Atelier 4 : Le Système de Grille et le Responsive Design (Grid & RWD) 💻

**Durée :** 3 heures       

**Objectif :** Maîtriser le système de grille à 12 colonnes, utiliser les préfixes de points de rupture pour créer un design réactif, et appliquer le principe du "Mobile First".

## Préparation

1.  Créez un dossier `TP_Bootstrap_2`.
2.  Créez un fichier `layout.html` et assurez-vous d'avoir Bootstrap 5 intégré.

## Partie 1 : Maîtrise de la Grille (60 min)

### Exercice 1.1 : Grille de Base et Taille Explicite

1.  Créez une section **`.container`**.
2.  Créez une **`.row`** avec trois colonnes. Dans cette rangée, attribuez les largeurs suivantes :
    * Colonne 1 : 2 unités (`.col-2`).
    * Colonne 2 : 7 unités (`.col-7`).
    * Colonne 3 : 3 unités (`.col-3`).
3.  **Vérification :** Assurez-vous que la somme des unités est bien 12.

### Exercice 1.2 : Largeur Automatique et Espacement

1.  Créez une nouvelle **`.row`**.
2.  Insérez 4 colonnes, mais ne spécifiez de largeur que pour la troisième :
    * Colonne 1 : **`.col`** (largeur automatique).
    * Colonne 2 : **`.col`** (largeur automatique).
    * Colonne 3 : **`.col-6`** (6 unités fixes).
    * Colonne 4 : **`.col`** (largeur automatique).
3.  **Observation :** Comment Bootstrap gère-t-il la répartition des unités restantes entre les colonnes à largeur automatique ?
4.  Appliquez la classe **`g-5`** à la rangée (`.row`) pour augmenter l'espace (le *gutter*) entre toutes les colonnes.

### Exercice 1.3 : Décalage et Centrage

1.  Créez une rangée. Créez une colonne qui doit être centrée sur la page et occuper 6 unités : **`class="col-6 offset-3"`**.
2.  **Analyse :** Expliquez le rôle de la classe **`offset-3`**.

## Partie 2 : Le Responsive Design et les Breakpoints (90 min)

L'objectif est de faire varier la mise en page en fonction de la taille de l'écran.

### Exercice 2.1 : Empilement Réactif

1.  Créez une rangée avec deux colonnes :
    * Colonne **`col-12`** et **`col-md-6`**.
    * Colonne **`col-12`** et **`col-md-6`**.
2.  **Test :** Réduisez la largeur de la fenêtre du navigateur :
    * **Grand écran (`md` et plus) :** Les colonnes sont côte à côte (6+6=12).
    * **Petit écran (`sm` et moins) :** Les colonnes s'empilent verticalement (12/12).
3.  **Conclusion :** Expliquez pourquoi `col-12` est nécessaire dans ce scénario (principe du Mobile First).

### Exercice 2.2 : Layout à Trois Niveaux (Mobile First)

1.  Créez une rangée avec 4 colonnes identiques.
2.  Appliquez les classes suivantes à chaque colonne pour définir leur comportement : **`class="col-12 col-md-6 col-lg-3"`**.
3.  **Test :** Observez le layout aux différentes tailles :
    * **Très petit écran (`col-12`) :** 4 colonnes empilées (100% de la largeur).
    * **Taille Moyenne (`col-md-6`) :** 2 colonnes par ligne (50% de la largeur).
    * **Grande Taille (`col-lg-3`) :** 4 colonnes par ligne (25% de la largeur).

### Exercice 2.3 : Ordre et Visibilité

1.  Créez une rangée avec deux colonnes (A et B).
2.  Par défaut, A est à gauche et B est à droite.
3.  Utilisez les classes **`.order-md-2`** sur A et **`.order-md-1`** sur B pour inverser leur position uniquement à partir du point de rupture `md`.
4.  Utilisez les classes **`.d-none`** et **`.d-md-block`** sur un élément pour le rendre visible **uniquement** sur les écrans moyens et plus grands.

## Partie 3 : Synthèse de Composants (30 min)

### Exercice 3.1 : Footer Réactif

1.  Créez un pied de page (`<footer>`) avec une rangée.
2.  Divisez cette rangée en **trois colonnes d'information** (ex: "Contact", "Liens Rapides", "Réseaux Sociaux").
3.  Définissez leur responsive : elles doivent être côte à côte sur les grands écrans (`col-lg-4`) mais s'empiler deux par deux sur les écrans moyens (`col-md-6`), et complètement s'empiler sur mobile (`col-12`).
    * **Indice :** `class="col-12 col-md-6 col-lg-4"` pour chaque colonne.