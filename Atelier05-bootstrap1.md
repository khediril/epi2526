
# TP 4 : Les Fondations et les Composants de Bootstrap 5

**Objectif :** Maîtriser l'intégration de Bootstrap, ses utilitaires d'espacement et de couleur, et savoir utiliser les composants d'interface utilisateur les plus fréquents (boutons, alertes, Navbar, Card).

## Préparation

1.  Créez un dossier `TP_Bootstrap_1`.
2.  Créez un fichier `index.html`.
3.  **Lien CDN :** Intégrez le CSS et le JavaScript de Bootstrap 5 via CDN.

## Partie 1 : Les Utilitaires

### Exercice 1.1 : Conteneurs et Marges/Padding

1.  Créez un conteneur principal avec la classe **`.container-fluid`**.
2.  À l'intérieur, créez une `div` avec les styles de couleur de fond suivants : `class="bg-dark p-5"`.
3.  À l'intérieur de cette `div`, ajoutez une autre `div` avec le fond clair et l'espacement suivant : **`class="bg-light m-4 p-3"`**.
4.  Ajoutez un texte à l'intérieur de la deuxième `div`.
5.  **Test :** Changez le `m-4` par `mx-auto` et observez comment l'élément se centre horizontalement (seulement si la `div` a une largeur définie).

### Exercice 1.2 : Couleurs et Texte

1.  Créez une série de balises `<p>` pour afficher les messages suivants :
    * Un message de succès (texte vert) : `class="text-success"`.
    * Un titre de niveau 3 formaté avec la classe de typographie Bootstrap : `class="h3"`.
    * Un paragraphe en gras avec un fond d'avertissement (jaune) : `class="fw-bold bg-warning"`.
2.  **Synthèse :** Expliquez la différence entre une classe de fond (`.bg-*`) et une classe de texte (`.text-*`).

### Exercice 1.3 : Flexbox Utilitaires

1.  Créez une `div` conteneur et donnez-lui la classe **`d-flex`** et **`bg-secondary p-5`**.
2.  Ajoutez trois `div` enfants avec une couleur de fond différente.
3.  Utilisez les classes Flexbox de Bootstrap pour :
    * **Centrer** horizontalement les trois éléments : `justify-content-center`.
    * **Aligner** les éléments en bas (axe secondaire) : `align-items-end`.
    * **Inverser** la direction des éléments (verticale) : `flex-column`.

## Partie 2 : Les Composants Essentiels

### Exercice 2.1 : Boutons et Alertes

1.  Créez un bouton principal de grande taille : **`class="btn btn-primary btn-lg"`**.
2.  Créez un bouton d'action secondaire avec un contour seulement : **`class="btn btn-outline-secondary"`**.
3.  Affichez une **Alerte** rouge (`danger`) avec un message d'erreur. Ajoutez un bouton de fermeture (`.btn-close`) à l'alerte.

### Exercice 2.2 : Barre de Navigation (Navbar)

1.  Copiez le code d'une **Navbar** simple de la documentation Bootstrap.
2.  Modifiez-la pour qu'elle ait :
    * Un fond sombre (`bg-dark`).
    * Le texte blanc (`navbar-dark`).
    * Un champ de recherche intégré.
3.  Ajoutez la classe **`fixed-top`** à la Navbar pour qu'elle reste en haut de l'écran lors du défilement.

### Exercice 2.3 : Cartes (Card)

1.  Créez une rangée (`.row`) dans votre page.
2.  Créez **trois Cartes** (`.card`) à l'intérieur de cette rangée. Utilisez les classes `.col-4` (que nous verrons en détail dans le TP 2) pour les aligner sur la même ligne.
3.  Chaque carte doit contenir :
    * Une image en haut : **`.card-img-top`**.
    * Un titre : **`.card-title`**.
    * Un bouton d'action.
4.  **But :** Rendre les trois cartes de **hauteur égale** en appliquant la classe `h-100` aux cartes.

