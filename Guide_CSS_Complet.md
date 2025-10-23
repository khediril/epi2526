
# 🎓 Guide Progressif du Langage CSS

---

## 🔹 1. Introduction à CSS

### 🔸 Qu’est-ce que CSS ?
CSS (*Cascading Style Sheets*) est un langage de style utilisé pour décrire la présentation d’un document HTML.  
Il permet de séparer le **contenu (HTML)** de la **mise en forme (CSS)**.

### Exemple :
```html
<!-- HTML -->
<p class="intro">Bienvenue dans le monde du CSS !</p>

<!-- CSS -->
.intro {
  color: blue;
  font-size: 18px;
}
```

💬 **Astuce :** Un bon CSS rend le code HTML plus lisible et plus réutilisable.

---

## 🔹 2. Structure d’une règle CSS

### 🔸 Composition :
Une règle CSS comprend :
- **Sélecteur** : identifie l’élément HTML ciblé.
- **Bloc de déclaration** : contient des propriétés et leurs valeurs.

### Exemple :
```css
p {
  color: red;
  font-size: 16px;
}
```

💡 **Lecture :** “Tous les `<p>` ont un texte rouge et une taille de 16px.”

---

## 🔹 3. Les différents types de sélecteurs

### 🔸 Sélecteurs de base
```css
p { color: blue; }            /* Par balise */
.intro { font-weight: bold; } /* Par classe */
#menu { background: gray; }   /* Par identifiant */
```

### 🔸 Sélecteurs combinés
```css
div p { color: red; }         /* Descendant */
h1, h2, h3 { color: navy; }   /* Groupement */
```

### 🔸 Pseudo-classes et pseudo-éléments
```css
a:hover { color: orange; }           /* Survol */
p::first-letter { font-size: 2em; }  /* Première lettre */
```

💬 **Astuce :** Utilise les classes pour le style, pas les IDs.

---

## 🔹 4. Couleurs, unités et valeurs

### 🔸 Couleurs
```css
color: red;
color: #ff0000;
color: rgb(255,0,0);
```

### 🔸 Unités
```css
width: 200px;     /* Absolue */
width: 50%;       /* Relative */
font-size: 1.5em; /* Relative à l’élément parent */
```

---

## 🔹 5. Le modèle de boîte (Box Model)

Chaque élément HTML est une “boîte” composée de :
- **content** → contenu réel  
- **padding** → espace intérieur  
- **border** → bordure  
- **margin** → espace extérieur  

### Exemple :
```css
div {
  margin: 10px;
  padding: 15px;
  border: 2px solid black;
}
```

💡 **Astuce :** Utilise `box-sizing: border-box;` pour simplifier les calculs.

---

## 🔹 6. Gestion du texte et des polices

### Exemple :
```css
p {
  font-family: 'Roboto', sans-serif;
  font-size: 16px;
  font-weight: 500;
  text-align: justify;
  text-transform: capitalize;
}
```

💬 **Remarque :** Utiliser des polices web sûres ou via Google Fonts.

---

## 🔹 7. Positionnement et affichage

### 🔸 Types d’affichage
```css
display: block;   /* Occupe toute la largeur */
display: inline;  /* S’aligne dans la ligne */
display: flex;    /* Disposition flexible */
```

### 🔸 Positionnement
```css
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

💡 **Astuce :** Utilise `flexbox` pour aligner facilement les éléments.

---

## 🔹 8. Flexbox — mise en page moderne

### Exemple :
```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

### Alignement rapide :
- `justify-content` → horizontal  
- `align-items` → vertical  
- `flex-direction` → orientation des enfants  

💬 **Astuce :** Flexbox remplace avantageusement les `float`.

---

## 🔹 9. Responsive Design avec Media Queries

### Exemple :
```css
@media (max-width: 768px) {
  .menu {
    flex-direction: column;
  }
}
```

💡 **Principe :** Adapter le style à la taille de l’écran pour une expérience utilisateur optimale.

---

## 🔹 10. Transitions, transformations et animations

### Exemple :
```css
button {
  background-color: royalblue;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: navy;
}
```

### Animation simple :
```css
@keyframes blink {
  0% { opacity: 1; }
  50% { opacity: 0; }
  100% { opacity: 1; }
}

p {
  animation: blink 1s infinite;
}
```

---

## 🔹 11. Méthodologie BEM (Block, Element, Modifier)

### 🔸 Principe :
- **Block** → composant autonome  
- **Element** → sous-partie du block  
- **Modifier** → variation de style  

### Exemple :
```html
<div class="card card--highlighted">
  <h2 class="card__title">Article</h2>
</div>
```

💬 **Astuce :** Favorise la clarté et la réutilisabilité du code CSS.

---

## 🔹 12. Bonnes pratiques CSS

- Toujours séparer **structure (HTML)** et **présentation (CSS)**.  
- Grouper le CSS dans des fichiers dédiés (`style.css`).  
- Préférer les **classes** aux identifiants.  
- Utiliser une **nomenclature cohérente (BEM)**.  
- Tester sur plusieurs navigateurs.  
- Utiliser un **normalize.css** pour homogénéiser les styles par défaut.
