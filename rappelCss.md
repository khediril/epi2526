Voici le guide complet du CSS, combinant le parcours progressif et le détail des sélecteurs avancés, le tout dans un seul document Markdown.Markdown# Guide Complet du Langage CSS

Pensez au **HTML** comme à la **structure** d'une maison (les murs, les pièces, la charpente) et au **CSS** comme à toute la **décoration** (la peinture, les meubles, l'agencement).

---

### 1. La Syntaxe de Base et l'Intégration 🎨

Avant de peindre, il faut savoir comment ouvrir le pot de peinture.

#### La Règle CSS
Une règle CSS a deux parties :
1.  **Le Sélecteur** : Cible l'élément HTML à styliser (ex: `h1`, `.ma-classe`).
2.  **Le Bloc de Déclaration** : Contient les styles (entre `{ }`).

Chaque déclaration a une **propriété** (ex: `color`) et une **valeur** (ex: `blue`), séparées par deux-points (`:`) et se terminant par un point-virgule (`;`).

```css
/* Ceci est un commentaire CSS */

sélecteur {
  propriété: valeur;
  autre-propriété: autre-valeur;
}
Comment l'ajouter à votre page ?Il y a trois façons, mais la méthode 1 est la meilleure :CSS Externe (Recommandé) :Vous créez un fichier style.css et le liez dans votre HTML. C'est propre et réutilisable.(Dans votre index.html, à l'intérieur de <head>)HTML<link rel="stylesheet" href="style.css">
CSS Interne :Vous mettez vos styles directement dans le HTML (utile pour des tests rapides).(Dans votre index.html, à l'intérieur de <head>)HTML<style>
  body {
    background-color: #f0f0f0;
  }
</style>
CSS En Ligne (In-line) :Vous appliquez le style directement sur une balise HTML. À éviter autant que possible car c'est très difficile à maintenir.HTML<p style="color: red; font-size: 12px;">Texte en rouge.</p>
2. Les Sélecteurs : Cibler les Éléments 🎯Comment dire au CSS quel élément cibler ?Les Sélecteurs EssentielsType de SélecteurSyntaxeExempleCe qu'il cibleÉlémentnom-balisepTous les paragraphes <p>Classe.nom-classe.btn-primaireTous les éléments avec class="btn-primaire"ID#nom-id#headerL'unique élément avec id="header"Descendantparent enfantnav aTous les liens <a> qui sont à l'intérieur de <nav>Pseudo-classesélecteur:étata:hoverL'élément <a> quand la souris le survoleExemple concret :HTML :HTML<nav id="menu-principal">
  <a href="/" class="lien-actif">Accueil</a>
  <a href="/contact">Contact</a>
</nav>
CSS :CSS/* Cible tous les liens <a> */
a {
  text-decoration: none; /* Enlève le soulignement */
}

/* Cible tous les liens <a> dans l'ID #menu-principal */
#menu-principal a {
  color: blue;
  padding: 10px;
}

/* Cible uniquement le lien avec la classe .lien-actif */
.lien-actif {
  font-weight: bold;
}

/* Cible les liens du menu AU SURVOL de la souris */
#menu-principal a:hover {
  color: red;
}
Les Sélecteurs AvancésCes sélecteurs vous permettent de cibler des éléments avec une précision chirurgicale, sans surcharger votre HTML de classes inutiles.1. Les Combinateurs (La Relation entre Éléments)Ils définissent la relation entre deux sélecteurs.TypeSyntaxeExempleCe qu'il cibleEnfant directA > Bul > liCible tous les <li> qui sont des enfants directs de <ul>. Il ne ciblera pas un <li> dans une liste imbriquée.Frère adjacentA + Bh2 + pCible le premier <p> qui se trouve immédiatement après un <h2> (et qui partage le même parent).Frères suivantsA ~ Bh2 ~ pCible tous les <p> qui suivent un <h2> (et qui partagent le même parent), pas seulement le premier.2. Les Sélecteurs d'Attribut (Cibler par les Attributs HTML)Ils ciblent les éléments en fonction de la présence ou de la valeur de leurs attributs HTML.TypeSyntaxeExempleCe qu'il ciblePrésence[attribut]a[target]Cible tous les liens <a> qui ont un attribut target (peu importe sa valeur).Valeur exacte[attr="valeur"]a[target="_blank"]Cible tous les liens <a> qui ont exactement target="_blank".Commence par[attr^="valeur"]a[href^="https://"]Cible les liens <a> dont le href commence par https:// (pratique pour les liens externes).Finit par[attr$="valeur"]a[href$=".pdf"]Cible les liens <a> qui pointent vers un fichier .pdf.Contient[attr*="valeur"]a[href*="google"]Cible les liens <a> dont le href contient le mot "google".3. Les Pseudo-classes Structurelles (Cibler par la Position)Elles ciblent les éléments en fonction de leur place dans l'arborescence HTML.TypeSyntaxeExempleCe qu'il ciblePremier enfant:first-childli:first-childLe premier <li> de n'importe quelle liste.Dernier enfant:last-childli:last-childLe dernier <li> de n'importe quelle liste.N-ième enfant:nth-child(n)li:nth-child(even)Cible les <li> pairs (2, 4, 6...). odd cible les impairs.li:nth-child(3)Cible le 3ème <li> uniquement.li:nth-child(3n)Cible tous les 3 éléments (le 3ème, 6ème, 9ème...).Négation:not(sélecteur)li:not(.special)Cible tous les <li> qui n'ont pas la classe .special.Premier de son type:first-of-typep:first-of-typeCible le premier paragraphe <p> à l'intérieur de son conteneur parent, même s'il n'est pas le tout premier enfant (ex: s'il y a un <h2> avant).4. Les Pseudo-éléments (Créer des Éléments Virtuels)Ils permettent de styliser une partie spécifique d'un élément ou d'ajouter du contenu. Notez les deux-points doubles (::).TypeSyntaxeExempleCe qu'il cibleAvant le contenu::beforeh2::beforeCrée un "faux" élément avant le contenu du <h2>. Nécessite content: ""; en CSS pour s'afficher. Parfait pour ajouter des icônes.Après le contenu::aftera[href^="http"]::afterCrée un "faux" élément après le contenu. Idéal pour ajouter " ↗️" aux liens externes.Première lettre::first-letterp::first-letterCible la première lettre d'un paragraphe (pour créer une lettrine).Première ligne::first-linep::first-lineCible la première ligne de texte d'un paragraphe.3. Le Modèle de Boîte (Box Model) 📦C'est le concept le plus important du CSS. Chaque élément sur une page est une boîte rectangulaire. Cette boîte est composée de 4 couches :Content (Contenu) : Le texte, l'image, etc.Padding (Marge intérieure) : L'espace entre le contenu et la bordure.Border (Bordure) : La ligne qui entoure le padding.Margin (Marge extérieure) : L'espace à l'extérieur de la bordure, qui pousse les autres éléments.CSS.ma-boite {
  /* Dimensions du contenu */
  width: 300px;
  height: 150px;
  
  /* Marge intérieure (grosse boîte) */
  padding: 20px; 
  
  /* Bordure (fine ligne noire) */
  border: 1px solid black; 
  
  /* Marge extérieure (espace autour) */
  margin: 10px; 
}
Astuce de pro : Mettez toujours ceci au début de votre CSS. Cela simplifie le calcul des tailles.CSS* {
  box-sizing: border-box;
}
4. Les Propriétés display et position 📌displayLa propriété display définit comment un élément se comporte dans le flux de la page.display: block; : Prend toute la largeur, crée un retour à la ligne (ex: <h1>, <p>, <div>).display: inline; : Prend juste la place nécessaire, reste dans le flux du texte (ex: <a>, <strong>, <span>).display: none; : Cache complètement l'élément.positionLa propriété position vous permet de placer un élément de manière plus précise.position: relative; : Positionnement "normal". Requis pour servir de "parent" à un élément absolute.position: absolute; : L'élément est sorti du flux et positionné par rapport à son parent relative le plus proche.position: fixed; : L'élément est positionné par rapport à la fenêtre du navigateur (ex: un menu qui reste en haut).Exemple :CSS.parent {
  position: relative;
  background-color: #eee;
  height: 200px;
  width: 200px;
}

.enfant-absolu {
  position: absolute;
  top: 10px;   /* 10px depuis le HAUT du parent */
  right: 10px; /* 10px depuis la DROITE du parent */
  background-color: red;
  width: 50px;
  height: 50px;
}
5. Flexbox (Mise en page 1D) 🤸Flexbox est l'outil moderne pour aligner des éléments dans une direction (horizontale ou verticale).Pour l'utiliser, vous avez besoin de 2 choses :Un conteneur (display: flex;)Des enfants (les éléments à l'intérieur)Exemple : Créer une barre de navigationHTML :HTML<nav>
  <div class="logo">MonSite</div>
  <ul>
    <li>Accueil</li>
    <li>Projets</li>
    <li>Contact</li>
  </ul>
</nav>
CSS :CSSnav {
  display: flex; /* Active Flexbox */
  justify-content: space-between; /* Écarte les enfants au maximum */
  align-items: center; /* Centre les enfants verticalement */
  background-color: #333;
  color: white;
  padding: 10px;
}

nav ul {
  display: flex; /* On peut imbriquer les flexbox ! */
  list-style-type: none; /* Enlève les puces */
  gap: 20px; /* Ajoute un espace de 20px entre les enfants */
}
6. CSS Grid (Mise en page 2D) ▦Là où Flexbox est bon pour les lignes ou les colonnes, Grid est fait pour les deux en même temps. C'est parfait pour la structure globale de votre page.Exemple : Créer une galerie de 3 colonnesHTML :HTML<div class="galerie">
  <div class="carte">Projet 1</div>
  <div class="carte">Projet 2</div>
  <div class="carte">Projet 3</div>
  <div class="carte">Projet 4</div>
  <div class="carte">Projet 5</div>
  <div class="carte">Projet 6</div>
</div>
CSS :CSS.galerie {
  display: grid;
  /* Crée 3 colonnes de taille égale (1fr = 1 fraction) */
  grid-template-columns: 1fr 1fr 1fr; 
  /* Ajoute un espace de 20px entre toutes les cases */
  gap: 20px; 
}

.carte {
  background-color: #eee;
  padding: 20px;
  border: 1px solid #ccc;
}
7. Le Responsive Design (Media Queries) 📱💻Votre site doit être beau sur mobile, tablette et ordinateur. Les Media Queries vous permettent d'appliquer des styles CSS uniquement si certaines conditions sont remplies (ex: la largeur de l'écran).L'approche moderne est "Mobile First" : vous créez d'abord les styles pour mobile, puis vous ajoutez des media queries pour les écrans plus grands.Exemple : Reprenons notre galerie. Sur mobile, nous voulons 1 seule colonne, mais 3 sur ordinateur.CSS/* Styles "Mobile First" (par défaut) */
.galerie {
  display: grid;
  grid-template-columns: 1fr; /* 1 colonne par défaut */
  gap: 20px; 
}

/* Si la largeur de l'écran est 768px OU PLUS... */
@media (min-width: 768px) {
  .galerie {
    /* ...on passe à 3 colonnes */
    grid-template-columns: 1fr 1fr 1fr;
  }
}
8. Transitions et Variables (La Finition) ✨TransitionsPour animer en douceur un changement de style.CSS.bouton {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  /* Applique une transition de 0.3s à toutes les propriétés */
  transition: all 0.3s ease;
}

.bouton:hover {
  background-color: darkblue;
  transform: scale(1.05); /* Zoome légèrement */
}
Variables CSSPour réutiliser des valeurs (comme des couleurs) et maintenir votre code propre.CSS/* Déclarez vos variables globales en haut */
:root {
  --couleur-principale: #3498db;
  --couleur-texte: #333;
  --espacement-moyen: 20px;
}

/* Utilisez-les n'importe où */
body {
  color: var(--couleur-texte);
}

.bouton-primaire {
  background-color: var(--couleur-principale);
  padding: var(--espacement-moyen);
}
