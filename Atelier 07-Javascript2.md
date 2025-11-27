# TP 08 JavaScript - 02 : DOM et Événements

## 📚 Table des matières
1. [Introduction au DOM](#1-introduction-au-dom)
2. [Sélection d'Éléments](#2-sélection-déléments)
3. [Manipulation du Contenu](#3-manipulation-du-contenu)
4. [Manipulation des Attributs](#4-manipulation-des-attributs)
5. [Création et Ajout d'Éléments](#5-création-et-ajout-déléments)
6. [Modification du Style CSS](#6-modification-du-style-css)
7. [Les Événements](#7-les-événements)
8. [Gestion Avancée des Événements](#8-gestion-avancée-des-événements)

---

## 1. Introduction au DOM

### 📖 Explication succincte

**DOM (Document Object Model)** : Représentation en arbre de la structure HTML d'une page web.
- Chaque élément HTML est un **nœud**
- JavaScript peut accéder et modifier ces nœuds
- Le DOM permet de rendre les pages web interactives

**Structure du DOM** :
```
document
  └── html
      ├── head
      │   └── title
      └── body
          ├── div
          │   └── p
          └── script
```

###  Exercice 1.1 : Comprendre le DOM
```html
<!-- Créez ce fichier HTML : exercice1.html -->
<!DOCTYPE html>
<html>
<head>
    <title>Mon Premier DOM</title>
</head>
<body>
    <h1 id="titre">Bienvenue</h1>
    <p class="description">Ceci est un paragraphe</p>
    <div id="container">
        <p>Premier paragraphe dans le div</p>
        <p>Deuxième paragraphe dans le div</p>
    </div>
    <script>
        // TODO: Affichez le nombre total d'éléments <p> dans la page
        
        // TODO: Affichez le contenu du titre (h1)
        
        // TODO: Affichez le nombre d'enfants du div#container
    </script>
</body>
</html>
```

---

## 2. Sélection d'Éléments

### 📖 Explication succincte

**Méthodes de sélection** :
- `getElementById(id)` : sélectionne par ID (retourne 1 élément)
- `getElementsByClassName(class)` : sélectionne par classe (retourne une collection)
- `getElementsByTagName(tag)` : sélectionne par balise (retourne une collection)
- `querySelector(selector)` : sélectionne le premier élément correspondant au sélecteur CSS
- `querySelectorAll(selector)` : sélectionne tous les éléments correspondants (retourne une NodeList)

###  Exercice 2.1 : Sélection par ID
```html
<!DOCTYPE html>
<html>
<body>
    <h1 id="titre">Mon Titre</h1>
    <p id="paragraphe">Mon paragraphe</p>
    <button id="btnClick">Cliquer</button>
    
    <script>
        // TODO: Sélectionnez l'élément avec l'id "titre"
        
        // TODO: Affichez son contenu texte dans la console
        
        // TODO: Sélectionnez le bouton et affichez son texte
    </script>
</body>
</html>
```

###  Exercice 2.2 : Sélection par classe et balise
```html
<!DOCTYPE html>
<html>
<body>
    <p class="info">Paragraphe 1</p>
    <p class="info">Paragraphe 2</p>
    <p class="warning">Attention!</p>
    <div class="info">Un div</div>
    
    <script>
        // TODO: Sélectionnez tous les éléments avec la classe "info"
        
        // TODO: Affichez le nombre d'éléments trouvés
        
        // TODO: Parcourez et affichez le contenu de chaque élément
        
        // TODO: Sélectionnez tous les <p> de la page
    </script>
</body>
</html>
```

###  Exercice 2.3 : querySelector et querySelectorAll
```html
<!DOCTYPE html>
<html>
<body>
    <div id="container">
        <p class="text">Premier</p>
        <p class="text highlight">Deuxième</p>
        <p class="text">Troisième</p>
    </div>
    
    <script>
        // TODO: Sélectionnez le premier <p> avec querySelector
        
        // TODO: Sélectionnez tous les <p> avec querySelectorAll
        
        // TODO: Sélectionnez le <p> qui a les deux classes "text" et "highlight"
        
        // TODO: Sélectionnez tous les <p> à l'intérieur de #container
    </script>
</body>
</html>
```

---

## 3. Manipulation du Contenu

### 📖 Explication succincte

**Propriétés pour modifier le contenu** :
- `innerHTML` : récupère/modifie le contenu HTML
- `textContent` : récupère/modifie le texte uniquement (sans HTML)
- `innerText` : similaire à textContent mais respecte le style CSS

###  Exercice 3.1 : innerHTML vs textContent
```html
<!DOCTYPE html>
<html>
<body>
    <div id="demo">
        <p>Contenu <strong>important</strong></p>
    </div>
    
    <script>
        // TODO: Affichez le innerHTML de #demo
        
        // TODO: Affichez le textContent de #demo
        
        // TODO: Modifiez le innerHTML pour ajouter un nouveau paragraphe
        
        // TODO: Créez un élément et modifiez son textContent
    </script>
</body>
</html>
```

###  Exercice 3.2 : Modification dynamique
```html
<!DOCTYPE html>
<html>
<body>
    <h1 id="titre">Titre Original</h1>
    <p id="description">Description originale</p>
    <button onclick="modifier()">Modifier</button>
    
    <script>
        function modifier() {
            // TODO: Changez le titre en "Nouveau Titre"
            
            // TODO: Changez la description en ajoutant du HTML (un <strong>)
            
            // TODO: Affichez une alerte confirmant la modification
        }
    </script>
</body>
</html>
```

---

## 4. Manipulation des Attributs

### 📖 Explication succincte

**Méthodes pour les attributs** :
- `getAttribute(attr)` : récupère la valeur d'un attribut
- `setAttribute(attr, value)` : définit/modifie un attribut
- `removeAttribute(attr)` : supprime un attribut
- `hasAttribute(attr)` : vérifie l'existence d'un attribut

**Accès direct** : `element.id`, `element.className`, `element.src`, etc.

###  Exercice 4.1 : Manipulation d'attributs
```html
<!DOCTYPE html>
<html>
<body>
    <img id="photo" src="image1.jpg" alt="Photo 1" width="200">
    <a id="lien" href="https://google.com">Google</a>
    <input id="champ" type="text" placeholder="Entrez votre nom">
    
    <script>
        // TODO: Récupérez et affichez l'attribut src de l'image
        
        // TODO: Modifiez l'attribut src pour "image2.jpg"
        
        // TODO: Changez le href du lien vers "https://github.com"
        
        // TODO: Ajoutez un attribut "disabled" au champ input
        
        // TODO: Vérifiez si l'image a un attribut "alt"
    </script>
</body>
</html>
```

###  Exercice 4.2 : Classes CSS
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .highlight { background-color: yellow; }
        .bold { font-weight: bold; }
        .large { font-size: 20px; }
    </style>
</head>
<body>
    <p id="texte">Mon paragraphe</p>
    
    <script>
        let texte = document.getElementById('texte');
        
        // TODO: Ajoutez la classe "highlight" au paragraphe
        
        // TODO: Ajoutez également la classe "bold"
        
        // TODO: Vérifiez si le paragraphe a la classe "large"
        
        // TODO: Supprimez la classe "highlight"
        
        // TODO: Basculez (toggle) la classe "large"
    </script>
</body>
</html>
```

---

## 5. Création et Ajout d'Éléments

### 📖 Explication succincte

**Création d'éléments** :
- `document.createElement(tag)` : crée un nouvel élément
- `document.createTextNode(text)` : crée un nœud texte

**Ajout au DOM** :
- `appendChild(node)` : ajoute comme dernier enfant
- `insertBefore(new, existing)` : insère avant un élément existant
- `insertAdjacentHTML(position, html)` : insère du HTML
  - Positions : `beforebegin`, `afterbegin`, `beforeend`, `afterend`

**Suppression** :
- `removeChild(node)` : supprime un enfant
- `remove()` : supprime l'élément lui-même

###  Exercice 5.1 : Créer et ajouter des éléments
```html
<!DOCTYPE html>
<html>
<body>
    <div id="container"></div>
    
    <script>
        // TODO: Créez un nouvel élément <p>
        
        // TODO: Créez un nœud texte "Bonjour le monde"
        
        // TODO: Ajoutez le texte au paragraphe
        
        // TODO: Ajoutez le paragraphe au container
        
        // TODO: Créez un deuxième paragraphe avec setAttribute pour l'id
    </script>
</body>
</html>
```

###  Exercice 5.2 : Liste dynamique
```html
<!DOCTYPE html>
<html>
<body>
    <ul id="liste"></ul>
    <button onclick="ajouterElement()">Ajouter</button>
    
    <script>
        let compteur = 1;
        
        function ajouterElement() {
            // TODO: Créez un élément <li>
            
            // TODO: Définissez son contenu texte comme "Élément " + compteur
            
            // TODO: Ajoutez-le à la liste
            
            // TODO: Incrémentez le compteur
        }
    </script>
</body>
</html>
```

###  Exercice 5.3 : insertAdjacentHTML
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .blue { background-color: lightblue; }
        .pink { background-color: pink; }
    </style>
</head>
<body>
    <p id="reference">Référence</p>
    
    <script>
        let ref = document.getElementById('reference');
        
        // TODO: Insérez un paragraphe AVANT #reference (beforebegin)
        // avec la classe "pink" et le texte "Avant"
        
        // TODO: Insérez un paragraphe APRÈS #reference (afterend)
        // avec la classe "blue" et le texte "Après"
        
        // TODO: Insérez du texte au DÉBUT de #reference (afterbegin)
        
        // TODO: Insérez du texte à la FIN de #reference (beforeend)
    </script>
</body>
</html>
```

###  Exercice 5.4 : Suppression d'éléments
```html
<!DOCTYPE html>
<html>
<body>
    <ul id="liste">
        <li>Élément 1</li>
        <li>Élément 2</li>
        <li id="special">Élément 3</li>
        <li>Élément 4</li>
    </ul>
    
    <script>
        // TODO: Supprimez l'élément avec l'id "special"
        
        // TODO: Supprimez le premier enfant de la liste
        
        // TODO: Supprimez le dernier enfant de la liste
    </script>
</body>
</html>
```

---

## 6. Modification du Style CSS

### 📖 Explication succincte

**Propriété style** : `element.style.propriété = valeur`
- Pour les propriétés CSS avec tiret, utilisez camelCase
- Exemple : `background-color` → `backgroundColor`

**Remarque** : `element.style` ne récupère que les styles inline, pas ceux définis dans une feuille CSS.

###  Exercice 6.1 : Modifier les styles
```html
<!DOCTYPE html>
<html>
<body>
    <div id="box" style="width: 100px; height: 100px;">
        Ma boîte
    </div>
    
    <script>
        let box = document.getElementById('box');
        
        // TODO: Changez la couleur de fond en rouge
        
        // TODO: Changez la couleur du texte en blanc
        
        // TODO: Ajoutez une bordure de 2px solid black
        
        // TODO: Centrez le texte
        
        // TODO: Ajoutez un padding de 20px
    </script>
</body>
</html>
```

###  Exercice 6.2 : Styles dynamiques
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        #carre {
            width: 100px;
            height: 100px;
            background-color: blue;
            transition: all 0.3s;
        }
    </style>
</head>
<body>
    <div id="carre"></div>
    <button onclick="agrandir()">Agrandir</button>
    <button onclick="changerCouleur()">Changer couleur</button>
    
    <script>
        function agrandir() {
            // TODO: Augmentez la largeur et hauteur à 200px
        }
        
        function changerCouleur() {
            // TODO: Changez la couleur de fond aléatoirement
            // Utilisez: '#' + Math.floor(Math.random()*16777215).toString(16)
        }
    </script>
</body>
</html>
```

---

## 7. Les Événements

### 📖 Explication succincte

**Événements courants** :
- **Souris** : `click`, `dblclick`, `mouseover`, `mouseout`, `mousedown`, `mouseup`, `mousemove`
- **Clavier** : `keydown`, `keyup`, `keypress`
- **Formulaire** : `submit`, `change`, `input`, `focus`, `blur`
- **Page** : `load`, `resize`, `scroll`

**Deux méthodes pour associer un événement** :
1. **Attribut HTML** : `<button onclick="maFonction()">` (déconseillé)
2. **addEventListener** : `element.addEventListener('click', fonction)` (recommandé)

###  Exercice 7.1 : Événement click
```html
<!DOCTYPE html>
<html>
<body>
    <button id="btn1">Méthode 1 (HTML)</button>
    <button id="btn2">Méthode 2 (addEventListener)</button>
    <p id="resultat"></p>
    
    <script>
        // Méthode 1 déjà dans le HTML
        function methode1() {
            document.getElementById('resultat').textContent = "Méthode 1 cliquée!";
        }
        
        // TODO: Utilisez addEventListener pour btn2
        // Affichez "Méthode 2 cliquée!" dans #resultat
    </script>
</body>
</html>
```

###  Exercice 7.2 : Événements de souris
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        #zone {
            width: 300px;
            height: 200px;
            border: 2px solid black;
            padding: 20px;
        }
    </style>
</head>
<body>
    <div id="zone">Passez la souris ici</div>
    <p id="info"></p>
    
    <script>
        let zone = document.getElementById('zone');
        let info = document.getElementById('info');
        
        // TODO: Ajoutez un événement mouseover qui change le fond en jaune
        
        // TODO: Ajoutez un événement mouseout qui remet le fond en blanc
        
        // TODO: Ajoutez un événement mousemove qui affiche les coordonnées
        // de la souris dans #info (utilisez event.clientX et event.clientY)
    </script>
</body>
</html>
```

###  Exercice 7.3 : Événements de clavier
```html
<!DOCTYPE html>
<html>
<body>
    <input type="text" id="champ" placeholder="Tapez quelque chose">
    <p id="affichage"></p>
    <p id="code"></p>
    
    <script>
        let champ = document.getElementById('champ');
        
        // TODO: Ajoutez un événement 'input' qui affiche en temps réel
        // ce qui est tapé dans #affichage
        
        // TODO: Ajoutez un événement 'keypress' qui affiche le code
        // de la touche pressée dans #code (event.charCode)
        
        // TODO: Ajoutez un événement 'keydown' qui détecte la touche Enter
        // et affiche une alerte
    </script>
</body>
</html>
```

###  Exercice 7.4 : Événements de formulaire
```html
<!DOCTYPE html>
<html>
<body>
    <form id="monForm">
        <input type="text" id="nom" placeholder="Nom" required>
        <input type="email" id="email" placeholder="Email" required>
        <select id="pays">
            <option value="">Choisir un pays</option>
            <option value="ma">Maroc</option>
            <option value="fr">France</option>
            <option value="tn">Tunisie</option>
        </select>
        <button type="submit">Envoyer</button>
    </form>
    <p id="message"></p>
    
    <script>
        // TODO: Empêchez la soumission du formulaire (preventDefault)
        
        // TODO: Récupérez les valeurs et affichez-les dans #message
        
        // TODO: Ajoutez un événement 'change' sur le select qui affiche
        // le pays sélectionné
        
        // TODO: Ajoutez un événement 'focus' sur le champ nom qui
        // change sa bordure en bleu
        
        // TODO: Ajoutez un événement 'blur' qui remet la bordure normale
    </script>
</body>
</html>
```

---

## 8. Gestion Avancée des Événements

### 📖 Explication succincte

**preventDefault()** : Empêche le comportement par défaut d'un événement
- Empêcher la soumission d'un formulaire
- Empêcher le suivi d'un lien
- Empêcher la saisie de certains caractères

**stopPropagation()** : Arrête la propagation de l'événement aux éléments parents

**removeEventListener()** : Supprime un écouteur d'événement

###  Exercice 8.1 : preventDefault
```html
<!DOCTYPE html>
<html>
<body>
    <a href="https://google.com" id="lien">Cliquez (ne suivra pas le lien)</a>
    <br><br>
    <input type="text" id="chiffres" placeholder="Seulement des chiffres">
    
    <script>
        // TODO: Empêchez le lien de rediriger vers Google
        
        // TODO: Sur le champ #chiffres, empêchez la saisie de tout
        // ce qui n'est pas un chiffre (utilisez keypress et charCode)
    </script>
</body>
</html>
```

###  Exercice 8.2 : stopPropagation
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        #parent {
            padding: 50px;
            background-color: lightblue;
            cursor: pointer;
        }
        #enfant {
            padding: 30px;
            background-color: lightcoral;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="parent">
        Parent
        <div id="enfant">
            Enfant
        </div>
    </div>
    
    <script>
        // TODO: Ajoutez un événement click sur parent qui affiche "Parent cliqué"
        
        // TODO: Ajoutez un événement click sur enfant qui affiche "Enfant cliqué"
        // ET qui empêche la propagation vers le parent
    </script>
</body>
</html>
```

###  Exercice 8.3 : removeEventListener
```html
<!DOCTYPE html>
<html>
<body>
    <button id="btn">Cliquez-moi (5 fois max)</button>
    <p id="compteur">Clics: 0</p>
    
    <script>
        let compteur = 0;
        let btn = document.getElementById('btn');
        
        function gererClic() {
            compteur++;
            document.getElementById('compteur').textContent = `Clics: ${compteur}`;
            
            // TODO: Si compteur atteint 5, supprimez l'événement
            // et changez le texte du bouton en "Désactivé"
        }
        
        // TODO: Ajoutez l'événement click
    </script>
</body>
</html>
```

###  Exercice 8.4 : Validation de formulaire avancée
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .error { border: 2px solid red; }
        .success { border: 2px solid green; }
        .message { color: red; font-size: 12px; }
    </style>
</head>
<body>
    <form id="inscription">
        <div>
            <input type="text" id="username" placeholder="Nom d'utilisateur (min 3 car.)">
            <span id="usernameMsg" class="message"></span>
        </div>
        <div>
            <input type="password" id="password" placeholder="Mot de passe (min 6 car.)">
            <span id="passwordMsg" class="message"></span>
        </div>
        <div>
            <input type="password" id="confirm" placeholder="Confirmer le mot de passe">
            <span id="confirmMsg" class="message"></span>
        </div>
        <button type="submit">S'inscrire</button>
    </form>
    
    <script>
        // TODO: Validez le nom d'utilisateur (min 3 caractères) sur 'blur'
        
        // TODO: Validez le mot de passe (min 6 caractères) sur 'blur'
        
        // TODO: Vérifiez que les mots de passe correspondent sur 'blur'
        
        // TODO: Sur submit, vérifiez tout et empêchez la soumission si erreur
        
        // TODO: Ajoutez/retirez les classes error/success selon la validation
    </script>
</body>
</html>
```

---

##  Bonnes Pratiques

### ✅ À faire
- Utiliser `addEventListener` plutôt que les attributs HTML
- Utiliser `querySelector` pour plus de flexibilité
- Toujours vérifier qu'un élément existe avant de le manipuler
- Utiliser `textContent` pour du texte simple (plus sûr que `innerHTML`)
- Nommer les fonctions de manière descriptive
- Séparer le JavaScript du HTML

### ❌ À éviter
- Mélanger JavaScript et HTML (attributs onclick, etc.)
- Oublier `preventDefault()` sur les formulaires
- Ne pas gérer les cas où l'élément n'existe pas
- Utiliser `innerHTML` avec des données utilisateur (risque XSS)
- Créer des variables globales inutile
