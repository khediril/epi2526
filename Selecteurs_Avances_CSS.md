
# 🎯 Les Sélecteurs Avancés en CSS

---

## 🔹 Introduction

Les sélecteurs avancés permettent de cibler avec précision des éléments HTML selon leur **position**, leur **état**, leurs **relations** ou encore leurs **attributs**.

Ils constituent un pilier du langage CSS moderne et permettent d’éviter la surabondance de classes dans le code HTML.

---

## 🔸 1. Les sélecteurs d’attributs

Ils ciblent des éléments selon la **présence ou la valeur** d’un attribut HTML.

### Syntaxe :
```css
[attribut] { ... }             /* présence */
[attribut="valeur"] { ... }    /* correspondance exacte */
[attribut~="valeur"] { ... }   /* mot contenu dans une liste */
[attribut|="valeur"] { ... }   /* valeur suivie d’un tiret */
[attribut^="valeur"] { ... }   /* commence par */
[attribut$="valeur"] { ... }   /* se termine par */
[attribut*="valeur"] { ... }   /* contient */
```

### Exemple :
```css
a[target] { color: red; }          /* tout lien avec attribut target */
a[href^="https"] { color: green; } /* commence par "https" */
a[href$=".pdf"] { color: orange; } /* finit par ".pdf" */
```

💬 **Astuce :** Très utile pour styliser les liens externes, images ou fichiers spécifiques.

---

## 🔸 2. Les sélecteurs de relation (combinators)

Ils définissent des relations entre éléments.

| Combinateur | Signification | Exemple |
|--------------|----------------|----------|
| `E F` | Descendant | `div p` → tous les `<p>` dans un `<div>` |
| `E > F` | Enfant direct | `div > p` → `<p>` directement sous `<div>` |
| `E + F` | Frère immédiat | `h1 + p` → `<p>` juste après `<h1>` |
| `E ~ F` | Frères suivants | `h1 ~ p` → tous les `<p>` après `<h1>` |

### Exemple :
```css
ul > li { list-style: square; }
h2 + p { margin-top: 0; }
```

💡 **Attention :** `>` ne sélectionne que les enfants directs, pas les descendants plus profonds.

---

## 🔸 3. Les pseudo-classes

Les pseudo-classes décrivent **un état particulier** d’un élément.

### Pseudo-classes courantes :
```css
a:hover { color: red; }       /* survol */
a:active { color: blue; }     /* clic */
a:visited { color: purple; }  /* lien visité */
input:focus { border: 2px solid blue; } /* focus sur champ */
```

### Pseudo-classes structurelles :
```css
li:first-child { color: red; }
li:last-child { color: green; }
li:nth-child(2) { color: blue; }
li:nth-child(odd) { background: #eee; }
```

💬 **Astuce :** Combine `nth-child()` pour créer des motifs alternés (zébrage de tableaux).

---

## 🔸 4. Les pseudo-éléments

Ils ciblent **une partie d’un élément**.

### Exemples :
```css
p::first-line { font-weight: bold; }
p::first-letter { font-size: 2em; color: crimson; }
p::before { content: "👉 "; }
p::after { content: " ✅"; }
```

💡 **Attention :** Les pseudo-éléments utilisent **deux doubles-points (::)** selon la norme CSS3.

---

## 🔸 5. Les sélecteurs d’état (UI selectors)

Ils réagissent à l’état d’un élément de formulaire.

### Exemples :
```css
input:checked { outline: 2px solid green; }
input:disabled { background: #eee; }
input:required { border: 1px solid red; }
```

💬 **Astuce :** Combinez-les avec `label[for]` pour améliorer l’accessibilité.

---

## 🔸 6. Les sélecteurs de négation et de combinaison

### 🔹 Négation
```css
:not(p) { color: gray; }  /* tout sauf les <p> */
li:not(:first-child) { margin-top: 5px; }
```

### 🔹 Groupement
```css
h1, h2, h3 { font-family: sans-serif; }
```

💡 **Astuce :** Le sélecteur `:not()` permet d’éviter de multiplier les classes.

---

## 🔸 7. Les sélecteurs de niveau 4 (CSS Selectors Level 4)

De nouvelles pseudo-classes sont apparues avec CSS4 :

```css
:is(header, footer, main) { background: #f5f5f5; }
:where(section p) { margin: 0; }
:has(img) { border: 1px solid #ccc; }
```

- `:is()` : simplifie les sélecteurs complexes  
- `:where()` : comme `:is()` mais sans spécificité  
- `:has()` : sélectionne un élément **parent** contenant un autre élément

💬 **Exemple concret :**
```css
article:has(img) {
  border: 2px solid green;
}
```

💡 **Attention :** `:has()` n’est pas encore supporté sur tous les navigateurs.

---

## 🔹 Conclusion

Les sélecteurs avancés CSS offrent une **puissance expressive** permettant de cibler des éléments de manière précise sans alourdir le HTML.

**Bonnes pratiques :**
- Préférez les sélecteurs de classes pour la maintenance.  
- Combinez intelligemment sélecteurs et pseudo-classes.  
- Évitez les sélecteurs trop longs ou trop spécifiques.  

---

## 📚 Références utiles

- [MDN Web Docs — CSS Selectors](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Selectors)
- [W3C CSS Selectors Level 4](https://www.w3.org/TR/selectors-4/)
