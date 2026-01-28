##  Atelier JavaScript : Les Bases

## Pour commencer

### 1️⃣ Explication : Où placer le JavaScript ?

Pour que javascript fonctionne, il doit être lié à votre fichier HTML. La meilleure pratique est d'utiliser un fichier externe.

  * **HTML** : Le squelette.
  * **CSS** : L'apparence.
  * **JavaScript (JS)** : Le comportement et l'interactivité.

<!-- end list -->

```html
<!DOCTYPE html>
<html>
<head>
    <title>Mon Premier JS</title>
</head>
<body>
    <h1>Bienvenue en JavaScript !</h1>

    <script src="app.js"></script>
</body>
</html>
```

### 2️⃣ Tâche : Initialisation du Projet

1.  Créez un dossier nommé `atelier-js`.
2.  Dans ce dossier, créez deux fichiers : `index.html` et `app.js`.
3.  Copiez le code HTML ci-dessus dans `index.html`.

### 3️⃣ Explication : La Console (Le carnet de bord)

La **console** du navigateur est votre meilleur ami en JavaScript. Elle permet :

  * D'afficher des informations pour vérifier que votre code s'exécute.
     * jjj
     * llll
  * De signaler les erreurs.

Pour afficher un message, on utilise la commande `console.log()`.

### 4️⃣ Tâche : Premier Code JS

Dans le fichier `app.js`, écrivez la ligne suivante :

```javascript
console.log("Le fichier JS est bien chargé !");
```

1.  Ouvrez `index.html` dans votre navigateur.
2.  Ouvrez les **Outils de développement** (souvent avec **F12** ou **clic droit \> Inspecter**).
3.  Cliquez sur l'onglet **Console**.
4.  Vous devriez voir le message : **"Le fichier JS est bien chargé \!"**

-----

## Les Variables et les Types de Données

Ce module introduit la façon dont JavaScript stocke et manipule l'information.

### 1️⃣ Explication : Les Variables 

Une **variable** est comme une petite boîte nommée où vous stockez une valeur. En JavaScript moderne, on utilise principalement `let` et `const`.

  * `let` : Pour les valeurs qui **vont changer** (par exemple, un score).
  * `const` : Pour les valeurs qui **ne doivent pas changer** (par exemple, le nom d'un site).

### 2️⃣ Explication : Types de Données de Base 

| Type | Description | Exemple |
| :--- | :--- | :--- |
| **String** | Texte (toujours entre guillemets). | `"Bonjour le monde"` |
| **Number** | Nombres entiers ou décimaux. | `10`, `3.14` |
| **Boolean** | Vrai ou Faux (oui ou non). | `true`, `false` |

### 3️⃣ Tâche : Déclarer et Afficher

Dans `app.js`, ajoutez le code suivant, puis vérifiez la console pour les résultats :

```javascript
// Déclaration d'une constante (ne change pas)
const nomAtelier = "Introduction à JavaScript";

// Déclaration d'une variable (peut changer)
let nombreEtudiants = 15;

// Opération simple
nombreEtudiants = nombreEtudiants + 2; // Le nombre passe de 15 à 17

// Affichage des variables dans la console
console.log("Nom de l'atelier:", nomAtelier);
console.log("Nombre d'étudiants actuel:", nombreEtudiants);

// Une variable booléenne
const estEnLigne = true;
console.log("L'atelier est-il en ligne ?", estEnLigne);
```

### 4️⃣ Tâche : Manipulation et Concaténation

Créez deux variables `prenom` (String) et `age` (Number), puis affichez une phrase complète dans la console en les combinant (concaténation avec `+`) :

```javascript
// Votre code ici...
// let prenom = ...
// const age = ...
// console.log("Je m'appelle " + prenom + " et j'ai " + age + " ans.");
```

-----

## Le DOM et l'Interactivité (Donner Vie à la Page)

Ce module est le plus important : comment JavaScript manipule la page web elle-même.

### 1️⃣ Explication : Le DOM 🌳

Le **DOM (Document Object Model)** est la représentation de votre page HTML sous forme d'arbre. JavaScript utilise le DOM pour trouver un élément HTML et le modifier (changer son texte, son style, ou le faire réagir).

### 2️⃣ Explication : Sélectionner un Élémente

Pour interagir, vous devez d'abord "attraper" l'élément. On le fait souvent en utilisant son **ID** unique.

| Méthode | Description |
| :--- | :--- |
| `document.getElementById('monId')` | Sélectionne l'élément ayant cet ID. |

### 3️⃣ Tâche : Changer du Texte

1.  Dans `index.html`, ajoutez un paragraphe avec un ID juste après le `<h1>` :

    ```html
    <p id="message-secret">Ceci est le texte original.</p>
    ```

2.  Dans `app.js`, écrivez le code suivant pour changer son contenu :

    ```javascript
    // 1. On "attrape" l'élément par son ID
    const elementMessage = document.getElementById('message-secret');

    // 2. On modifie la propriété 'textContent'
    elementMessage.textContent = "🥳 Le texte a été changé par JavaScript !";

    // 3. OPTIONNEL : Changer le style (la couleur)
    elementMessage.style.color = "blue";
    ```

    Vérifiez votre page : le texte devrait avoir changé.

### 4️⃣ Explication : Les Événements (Rendre Interactif)

Les **événements** sont des actions que l'utilisateur effectue (cliquer, bouger la souris, taper au clavier). JavaScript peut **écouter** ces événements et réagir.

### 5️⃣ Tâche : Gérer le Clic (Le Cœur de l'Interactivité)

1.  Dans `index.html`, ajoutez un bouton avec un ID :

    ```html
    <button id="bouton-compteur">Cliquez-moi !</button>
    ```

2.  Dans `app.js`, écrivez ce code pour faire réagir le bouton :

    ```javascript
    const bouton = document.getElementById('bouton-compteur');
    let compteur = 0;

    // La fonction qui sera exécutée à chaque clic
    function incrementerCompteur() {
        compteur = compteur + 1;
        // On change le texte du bouton pour afficher le nouveau compte
        bouton.textContent = "Vous avez cliqué " + compteur + " fois";
        console.log("Clic détecté ! Nouveau total :", compteur);
    }

    // On dit au bouton d'écouter le 'click' et d'appeler la fonction
    bouton.addEventListener('click', incrementerCompteur);
    ```
