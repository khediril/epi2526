# Points Essentiels des Formulaires HTML

L'objectif de cette synthèse est de fournir une base solide pour la création de formulaires robustes, accessibles et efficaces en HTML.

## I. Les Fondamentaux du Formulaire

Un formulaire HTML est la structure essentielle pour capturer des données utilisateur.

1.  **La balise `<form>` : Le Conteneur**

    * C'est le point de départ qui englobe tous les champs de saisie.

    * **Attribut `action` :** Définit l'URL vers laquelle les données seront envoyées (le script côté serveur qui traitera l'information).

    * **Attribut `method` :** Spécifie la méthode HTTP pour l'envoi :

        * `GET` : Utilisé pour les requêtes de lecture (ex. : recherche), les données sont visibles dans l'URL.

        * `POST` : Utilisé pour l'envoi de données (création, modification), les données sont masquées dans le corps de la requête.

2.  **L'attribut `name` : L'Identifiant Serveur (Crucial)**

    * Chaque champ de saisie (`<input>`, `<textarea>`, `<select>`) **doit** avoir un attribut `name`.

    * **Rôle :** Il définit le nom de la variable que le serveur recevra avec la valeur saisie par l'utilisateur. Sans `name`, la donnée n'est pas transmise.

3.  **Accessibilité avec `<label>`**

    * **Règle :** Toujours associer un `<label>` à son champ de saisie correspondant.

    * **Liaison :** La valeur de l'attribut **`for`** du `<label>` doit correspondre exactement à l'attribut **`id`** du champ.

    * **Avantage :** Ceci améliore l'accessibilité (les lecteurs d'écran lisent l'étiquette) et l'ergonomie (cliquer sur le texte du label active le champ).

4.  **Types d'Inputs Sémantiques**

    * Utilisez des types spécifiques (`email`, `tel`, `date`, `number`, `url`) au lieu de `text` lorsque possible.

    * **Bénéfices :** Le navigateur applique une validation initiale et propose des interfaces optimisées (ex. : calendrier pour `date`, clavier numérique pour `tel` sur mobile).

5.  **Validation Côté Client**

    * **`required` :** Rends le champ obligatoire pour la soumission.

    * **`pattern` :** Permet de spécifier une expression régulière pour une validation de format avancée (ex. : code postal, format spécifique).

    * `min`, `max`, `maxlength`, `minlength` : Définissent des contraintes de valeur ou de taille.


---

## II. Précisions sur l'Attribut `name` pour les Éléments de Choix

L'attribut `name` est utilisé pour grouper les éléments de choix, ce qui influence directement la manière dont les données sont envoyées au serveur.

### 1. Les Boutons Radio (`<input type="radio">`)

| Rôle | Description |
| :--- | :--- |
| **Groupe d'Exclusivité** | Tous les boutons radio qui constituent un même groupe et dont l'utilisateur ne doit sélectionner qu'**un seul** choix doivent avoir le **même attribut `name`**. |
| **Transmission** | Le serveur reçoit uniquement la paire `name=value` du bouton sélectionné. |
| **Exemple** | `<input type="radio" name="couleur" value="bleu">` et `<input type="radio" name="couleur" value="rouge">`. |

### 2. Les Cases à Cocher (`<input type="checkbox">`)

| Rôle | Description |
| :--- | :--- |
| **Sélections Multiples** | Si l'utilisateur peut choisir plusieurs options d'une liste (le cas le plus courant). |
| **Convention** | Il est **fortement recommandé** d'ajouter des **crochets `[]`** à l'attribut `name` (ex. : `name="interets[]"`). |
| **Transmission** | Les crochets signalent au serveur que toutes les valeurs cochées doivent être rassemblées dans un **tableau** (ou une liste) unique. |
| **Exemple** | `<input type="checkbox" name="options[]" value="a">` et `<input type="checkbox" name="options[]" value="b">`. Si les deux sont cochés, le serveur reçoit `options=[a, b]`. |

### 3. Les Listes Déroulantes (`<select>`)

L'attribut `name` est placé sur le conteneur `<select>`.

| Rôle | Description |
| :--- | :--- |
| **Sélection Simple** | Par défaut, un seul choix est possible, le `name` est simple (ex. : `name="ville"`). |
| **Sélection Multiple** | Pour permettre à l'utilisateur de choisir plusieurs options (en utilisant `Ctrl`/`Cmd` + clic) : |
| **Attribut HTML** | La balise `<select>` **doit** avoir l'attribut **`multiple`**. |
| **Attribut `name`** | Le `name` doit également être suivi des **crochets `[]`** (ex. : `name="pays_visites[]"`). |

| **Élément** | **Sélections Autorisées** | **Emplacement du name** | **Règle name pour le Groupement** |
| :--- | :--- | :--- | :--- |
| **Radio** | Un seul choix | Sur chaque `<input>` | **Identique** pour tout le groupe |
| **Checkbox** | Plusieurs choix | Sur chaque `<input>` | **Crochets `[]`** recommandés pour les groupes |
| **Select** | Plusieurs choix | Sur le `<select>` | Attribut **`multiple`** requis et **crochets `[]`** sur `name` |