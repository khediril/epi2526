# Guide de Référence Rapide - DOM et Événements

##  SÉLECTION D'ÉLÉMENTS

### Par ID
```javascript
let element = document.getElementById('monId');
```

### Par Classe
```javascript
let elements = document.getElementsByClassName('maClasse');
// Retourne une HTMLCollection (array-like)
```

### Par Balise
```javascript
let paragraphes = document.getElementsByTagName('p');
```

### Query Selector (CSS)
```javascript
// Premier élément correspondant
let premier = document.querySelector('.classe');
let premierP = document.querySelector('p');
let specifique = document.querySelector('#id .classe');

// Tous les éléments correspondants
let tous = document.querySelectorAll('.classe');
// Retourne une NodeList
```

---

##  MANIPULATION DU CONTENU

### innerHTML vs textContent
```javascript
let div = document.getElementById('demo');

// innerHTML : récupère/modifie le HTML
div.innerHTML = '<p>Nouveau <strong>contenu</strong></p>';
console.log(div.innerHTML); // "<p>Nouveau <strong>contenu</strong></p>"

// textContent : récupère/modifie le texte uniquement
div.textContent = 'Texte simple';
console.log(div.textContent); // "Texte simple"
```

### Autres propriétés
```javascript
element.innerText;     // Texte visible (respecte CSS)
element.value;         // Pour les inputs
element.textContent;   // Texte brut (recommandé)
```

---

##  MANIPULATION DES ATTRIBUTS

### Méthodes getAttribute/setAttribute
```javascript
let img = document.getElementById('photo');

// Récupérer
let src = img.getAttribute('src');

// Définir/Modifier
img.setAttribute('src', 'nouvelle-image.jpg');
img.setAttribute('alt', 'Description');

// Supprimer
img.removeAttribute('alt');

// Vérifier l'existence
if (img.hasAttribute('alt')) {
    console.log('A un attribut alt');
}
```

### Accès direct
```javascript
img.src = 'image.jpg';
img.id = 'nouvelId';
link.href = 'https://example.com';
input.value = 'texte';
input.placeholder = 'Entrez...';
input.disabled = true;
```

### Classes CSS
```javascript
let element = document.getElementById('demo');

// Ajouter une classe
element.classList.add('active');

// Supprimer une classe
element.classList.remove('active');

// Basculer une classe
element.classList.toggle('active');

// Vérifier une classe
if (element.classList.contains('active')) {
    console.log('A la classe active');
}

// Remplacer une classe
element.classList.replace('old', 'new');
```

---

## ➕ CRÉATION ET AJOUT D'ÉLÉMENTS

### Créer des éléments
```javascript
// Créer un élément
let div = document.createElement('div');
let p = document.createElement('p');

// Créer un nœud texte
let texte = document.createTextNode('Mon texte');

// Ajouter le texte à l'élément
p.appendChild(texte);

// Ou directement
p.textContent = 'Mon texte';
```

### Ajouter au DOM
```javascript
let container = document.getElementById('container');

// Ajouter comme dernier enfant
container.appendChild(p);

// Insérer avant un élément existant
let reference = document.getElementById('ref');
container.insertBefore(p, reference);

// insertAdjacentHTML
element.insertAdjacentHTML('beforebegin', '<p>Avant</p>');
element.insertAdjacentHTML('afterbegin', '<p>Début</p>');
element.insertAdjacentHTML('beforeend', '<p>Fin</p>');
element.insertAdjacentHTML('afterend', '<p>Après</p>');
```

### Positions insertAdjacentHTML
```
<!-- beforebegin -->
<div id="element">
    <!-- afterbegin -->
    Contenu
    <!-- beforeend -->
</div>
<!-- afterend -->
```

### Supprimer des éléments
```javascript
// Supprimer un enfant
parent.removeChild(enfant);

// Supprimer l'élément lui-même
element.remove();

// Vider un élément
element.innerHTML = '';
```

### Cloner un élément
```javascript
let clone = element.cloneNode(true);  // true = cloner les enfants aussi
```

---

## 🎨 MODIFICATION DU STYLE CSS

### Propriété style
```javascript
let box = document.getElementById('box');

// Modifier une propriété
box.style.backgroundColor = 'red';
box.style.color = 'white';
box.style.fontSize = '20px';
box.style.border = '2px solid black';

// Propriétés CSS → camelCase
// background-color → backgroundColor
// font-size → fontSize
// border-radius → borderRadius
```

### Exemples courants
```javascript
element.style.display = 'none';        // Cacher
element.style.display = 'block';       // Afficher
element.style.visibility = 'hidden';   // Invisible mais prend de la place
element.style.opacity = '0.5';         // Transparence
element.style.width = '200px';
element.style.height = '100px';
element.style.margin = '10px';
element.style.padding = '20px';
```

### Récupérer les styles calculés
```javascript
let styles = window.getComputedStyle(element);
let couleur = styles.backgroundColor;
let largeur = styles.width;
```

---

## ⚡ LES ÉVÉNEMENTS

### addEventListener (Recommandé)
```javascript
element.addEventListener('click', function() {
    console.log('Cliqué!');
});

// Avec fonction nommée
function handleClick() {
    console.log('Cliqué!');
}
element.addEventListener('click', handleClick);
```

### Événements de Souris
```javascript
element.addEventListener('click', function() {});        // Clic
element.addEventListener('dblclick', function() {});     // Double-clic
element.addEventListener('mousedown', function() {});    // Bouton enfoncé
element.addEventListener('mouseup', function() {});      // Bouton relâché
element.addEventListener('mouseover', function() {});    // Souris entre
element.addEventListener('mouseout', function() {});     // Souris sort
element.addEventListener('mousemove', function(e) {      // Souris bouge
    console.log(e.clientX, e.clientY);  // Coordonnées
});
```

### Événements de Clavier
```javascript
element.addEventListener('keydown', function(e) {
    console.log('Touche:', e.key);
    console.log('Code:', e.keyCode);
});

element.addEventListener('keyup', function(e) {});
element.addEventListener('keypress', function(e) {});

// Détecter une touche spécifique
document.addEventListener('keydown', function(e) {
    if (e.key === 'Enter') {
        console.log('Enter pressé');
    }
    if (e.key === 'Escape') {
        console.log('Escape pressé');
    }
});
```

### Événements de Formulaire
```javascript
// Soumission
form.addEventListener('submit', function(e) {
    e.preventDefault();  // Empêcher la soumission
    // Traiter les données
});

// Changement de valeur
input.addEventListener('change', function() {
    console.log('Valeur:', this.value);
});

// Saisie en temps réel
input.addEventListener('input', function() {
    console.log('Saisie:', this.value);
});

// Focus
input.addEventListener('focus', function() {
    this.style.borderColor = 'blue';
});

// Perte de focus
input.addEventListener('blur', function() {
    this.style.borderColor = '';
});
```

### Événements de Page
```javascript
// Chargement complet de la page
window.addEventListener('load', function() {
    console.log('Page chargée');
});

// DOM prêt (avant les images)
document.addEventListener('DOMContentLoaded', function() {
    console.log('DOM prêt');
});

// Redimensionnement
window.addEventListener('resize', function() {
    console.log('Largeur:', window.innerWidth);
});

// Défilement
window.addEventListener('scroll', function() {
    console.log('Scroll:', window.scrollY);
});
```

---

## 🛡️ GESTION AVANCÉE DES ÉVÉNEMENTS

### Objet Event
```javascript
element.addEventListener('click', function(event) {
    console.log('Type:', event.type);           // 'click'
    console.log('Target:', event.target);       // Élément cliqué
    console.log('CurrentTarget:', event.currentTarget);  // Élément avec listener
    
    // Souris
    console.log('X:', event.clientX);
    console.log('Y:', event.clientY);
    
    // Clavier
    console.log('Touche:', event.key);
    console.log('Code:', event.keyCode);
});
```

### preventDefault()
```javascript
// Empêcher le comportement par défaut

// Empêcher la soumission d'un formulaire
form.addEventListener('submit', function(e) {
    e.preventDefault();
});

// Empêcher le suivi d'un lien
link.addEventListener('click', function(e) {
    e.preventDefault();
});

// Empêcher la saisie de certains caractères
input.addEventListener('keypress', function(e) {
    if (e.charCode < 48 || e.charCode > 57) {
        e.preventDefault();  // Bloquer si pas un chiffre
    }
});
```

### stopPropagation()
```javascript
// Arrêter la propagation vers les parents

parent.addEventListener('click', function() {
    console.log('Parent cliqué');
});

enfant.addEventListener('click', function(e) {
    e.stopPropagation();  // Ne pas propager au parent
    console.log('Enfant cliqué');
});
```

### removeEventListener()
```javascript
function handleClick() {
    console.log('Cliqué');
}

// Ajouter
element.addEventListener('click', handleClick);

// Retirer (doit être la même fonction)
element.removeEventListener('click', handleClick);
```

---

## 🔄 PARCOURIR LE DOM

### Navigation
```javascript
// Parent
let parent = element.parentElement;
let parentNode = element.parentNode;

// Enfants
let enfants = element.children;           // HTMLCollection
let premierEnfant = element.firstElementChild;
let dernierEnfant = element.lastElementChild;

// Frères et sœurs
let suivant = element.nextElementSibling;
let precedent = element.previousElementSibling;
```

### Vérifications
```javascript
// A des enfants?
if (element.hasChildNodes()) {
    console.log('A des enfants');
}

// Nombre d'enfants
console.log(element.childElementCount);
```

---

## 💾 DONNÉES ET ATTRIBUTS DATA

### Attributs data-*
```html
<div id="user" data-id="123" data-name="Ahmed" data-role="admin"></div>
```

```javascript
let user = document.getElementById('user');

// Accès via dataset
console.log(user.dataset.id);      // "123"
console.log(user.dataset.name);    // "Ahmed"
console.log(user.dataset.role);    // "admin"

// Modification
user.dataset.id = "456";

// Ajout
user.dataset.email = "ahmed@example.com";
```

---

## 📦 EXEMPLES PRATIQUES

### Validation de formulaire
```javascript
form.addEventListener('submit', function(e) {
    e.preventDefault();
    
    let email = document.getElementById('email').value;
    let password = document.getElementById('password').value;
    
    if (email === '' || password === '') {
        alert('Tous les champs sont requis');
        return;
    }
    
    if (password.length < 6) {
        alert('Mot de passe trop court');
        return;
    }
    
    // Soumettre
    this.submit();
});
```

### Liste dynamique
```javascript
let liste = document.getElementById('liste');
let input = document.getElementById('input');
let btn = document.getElementById('btn');

btn.addEventListener('click', function() {
    let texte = input.value.trim();
    
    if (texte !== '') {
        let li = document.createElement('li');
        li.textContent = texte;
        liste.appendChild(li);
        input.value = '';
    }
});
```

### Toggle classe au clic
```javascript
element.addEventListener('click', function() {
    this.classList.toggle('active');
});
```

### Compteur de clics
```javascript
let compteur = 0;
let btn = document.getElementById('btn');
let affichage = document.getElementById('affichage');

btn.addEventListener('click', function() {
    compteur++;
    affichage.textContent = `Clics: ${compteur}`;
});
```

---

## 🎯 ASTUCES ET BONNES PRATIQUES

### Vérifier l'existence
```javascript
let element = document.getElementById('demo');
if (element) {
    // Manipulation sûre
    element.textContent = 'Texte';
}
```

### Délégation d'événements
```javascript
// Au lieu d'ajouter un listener à chaque élément
// Ajouter un seul listener au parent

liste.addEventListener('click', function(e) {
    if (e.target.tagName === 'LI') {
        console.log('Item cliqué:', e.target.textContent);
    }
});
```

### Convertir HTMLCollection en Array
```javascript
let elements = document.getElementsByClassName('item');
let array = Array.from(elements);

// Ou
let array = [...elements];

// Maintenant on peut utiliser forEach, map, etc.
array.forEach(el => console.log(el));
```


