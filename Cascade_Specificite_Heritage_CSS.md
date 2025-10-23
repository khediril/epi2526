
# 🎓 Cascade, Spécificité et Héritage en CSS

---

## 🔹 Introduction

CSS signifie **Cascading Style Sheets**, littéralement “Feuilles de style en cascade”.  
La **cascade**, la **spécificité** et **l’héritage** déterminent **quelle règle s’applique** lorsqu’il y a plusieurs déclarations pour un même élément.

---

## 🔸 1. La Cascade

La **cascade** définit l’ordre de priorité des règles selon trois critères principaux :

1. **L’origine du style**
   - Styles de l’utilisateur (navigateurs, extensions)
   - Styles de l’auteur (nos fichiers CSS)
   - Styles en ligne (dans l’attribut `style`)

2. **L’importance (`!important`)**
   - Une règle marquée `!important` prend le dessus sur les autres.

3. **L’ordre d’apparition**
   - En cas d’égalité, la **dernière règle** définie dans le CSS l’emporte.

### Exemple :
```html
<p class="info" style="color: red;">Texte exemple</p>
```

```css
p { color: blue; }             /* Règle 1 */
.info { color: green; }        /* Règle 2 */
p.info { color: purple !important; } /* Règle 3 */
```

🔍 **Résultat :** le texte sera **violet**, car `!important` domine toutes les autres.

💡 **Astuce :** utilise `!important` avec parcimonie — cela complique la maintenance du code.

---

## 🔸 2. La Spécificité

La **spécificité** est une valeur numérique calculée selon le **type de sélecteur**.  
Plus un sélecteur est spécifique, plus il a de poids.

### Tableau des poids :

| Type de sélecteur | Exemple | Valeur |
|--------------------|----------|--------|
| Sélecteur d'identifiant | `#menu` | 100 |
| Sélecteur de classe, pseudo-classe ou attribut | `.active`, `[type="text"]`, `:hover` | 10 |
| Sélecteur d’élément ou pseudo-élément | `p`, `::before` | 1 |
| Style en ligne | `style="..."` | 1000 |
| `!important` | — | Priorité absolue |

### Exemple concret :
```html
<p id="texte" class="important">Bonjour CSS</p>
```

```css
p { color: blue; }           /* Spécificité : 1 */
.important { color: green; } /* Spécificité : 10 */
#texte { color: red; }       /* Spécificité : 100 */
```

🔍 **Résultat :** le texte sera **rouge**, car `#texte` a la spécificité la plus élevée.

💬 **Astuce :** Lorsque plusieurs règles ciblent le même élément, la plus **spécifique** l’emporte.

---

### Cas d’égalité de spécificité

Si deux règles ont la **même spécificité**, c’est la **dernière dans le code CSS** qui gagne.

```css
p.info { color: blue; }
.info p { color: green; }  /* s’applique si égalité */
```

---

## 🔸 3. L’Héritage

Certains styles **se propagent automatiquement** des éléments parents aux enfants.  
C’est ce qu’on appelle **l’héritage**.

### Exemples de propriétés héritées :
- `color`
- `font-family`
- `font-size`
- `line-height`
- `visibility`

### Exemple :
```html
<div class="parent">
  <p>Texte hérité</p>
</div>
```

```css
.parent {
  color: darkblue;
  font-family: Arial;
}
```

🔍 **Résultat :** le texte `<p>` sera aussi **darkblue**, car il hérite de la couleur du parent.

---

### ⚙️ Contrôle de l’héritage

On peut forcer ou bloquer l’héritage :

```css
/* Forcer l’héritage */
p {
  font-size: inherit;
}

/* Réinitialiser la valeur */
p {
  color: initial; /* valeur par défaut du navigateur */
}

/* Hériter de tout le parent */
p {
  all: inherit;
}
```

💡 **Astuce :**
- `inherit` → hérite la valeur du parent  
- `initial` → revient à la valeur CSS par défaut  
- `unset` → combine les deux selon le contexte  

---

## 🔸 4. Cascade + Spécificité + Héritage — Exemple global

### Exemple complet :
```html
<div id="conteneur" class="zone">
  <p style="color: red;">Bonjour le monde !</p>
</div>
```

```css
p { color: black; }             /* Spécificité : 1 */
.zone p { color: green; }       /* Spécificité : 11 */
#conteneur p { color: blue; }   /* Spécificité : 101 */
p { color: orange !important; } /* priorité absolue */
```

### Résultat :
1. `p` → noir (base)
2. `.zone p` → vert (plus spécifique)
3. `#conteneur p` → bleu (encore plus spécifique)
4. `!important` → orange (prend le dessus)

✅ **Couleur finale : orange**

---

## 🔹 Résumé synthétique

| Principe | Rôle | Exemple |
|-----------|------|----------|
| **Cascade** | Priorise les règles selon ordre, importance et source | `!important` > inline > CSS externe |
| **Spécificité** | Donne un poids selon le sélecteur | `#id` > `.classe` > `élément` |
| **Héritage** | Transmet des propriétés du parent à l’enfant | `color`, `font-family`, etc. |

---

## 💬 Bonnes pratiques

- Éviter les `!important` sauf en dernier recours.  
- Préférer des sélecteurs **clairs et cohérents**.  
- Bien comprendre l’héritage avant de surcharger un style.  
- Tester les interactions entre règles à l’aide des outils du navigateur (onglet *Inspecteur CSS*).

---

## 📚 Ressources recommandées

- [MDN – Cascade et spécificité](https://developer.mozilla.org/fr/docs/Web/CSS/Cascade)
- [CSS Tricks – Specificity Explained](https://css-tricks.com/specifics-on-css-specificity/)
- [W3C – CSS Cascade Level 4](https://www.w3.org/TR/css-cascade-4/)
