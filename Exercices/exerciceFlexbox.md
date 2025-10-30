# 🧠 Exercice Avancé Flexbox : Le "Dashboard Complexe"

## Objectif :

Réaliser une mise en page d'un tableau de bord (Dashboard) à l'aide de Flexbox, en combinant des conteneurs horizontaux et verticaux (imbrication) et en manipulant l'ordre des éléments.

## Fichiers de Départ

Créez deux fichiers : `index.html` et `style.css`.

### 1\. Fichier `index.html` (La Structure)

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exercice Avancé Flexbox</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="dashboard-container">
        
        <div class="col-gauche">
            <div class="widget widget-profil">A - Profil Utilisateur</div>
            <div class="widget widget-menu">B - Menu de Navigation</div>
            <div class="widget widget-help">C - Aide & Support</div>
        </div>

        <div class="col-principale">
            
            <div class="row-kpi">
                <div class="kpi kpi-ventes">D1 - Ventes</div>
                <div class="kpi kpi-conversion">D2 - Conversion</div>
                <div class="kpi kpi-visites">D3 - Visites</div>
            </div>

            <div class="row-content">
                <div class="chart-area">E - Graphique Principal (Prend 70%)</div>
                <div class="notifications">F - Notifications (Prend 30%)</div>
            </div>

            <div class="row-footer">
                <div class="footer-stats">G - Statistiques Détaillées</div>
                <div class="footer-status">H - Statut du Serveur</div>
            </div>

        </div>

    </div>

</body>
</html>
```

### 2\. Fichier `style.css` (Styles de Base)

Ces styles rendent les blocs visibles, mais n'appliquent **aucune mise en page** Flexbox.

```css
/* Styles de base */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    background-color: #eee;
    padding: 20px;
    height: 100vh; /* Hauteur pour voir l'alignement vertical */
}

/* Styles visuels des conteneurs */
.dashboard-container {
    background-color: #fff;
    border: 1px solid #ccc;
    min-height: 90vh; 
    padding: 10px;
}

.col-gauche, .col-principale {
    padding: 10px;
    border: 2px dashed #ddd;
    margin: 5px;
}

/* Styles des Widgets/Cartes */
.widget, .kpi, .chart-area, .notifications, .footer-stats, .footer-status {
    background-color: #f8f8ff;
    border: 1px solid #cce;
    padding: 15px;
    margin: 5px;
    text-align: center;
    color: #333;
    font-weight: bold;
}

.widget {
    min-height: 100px;
}
.chart-area {
    min-height: 300px;
}
.notifications {
    min-height: 300px;
}
.kpi {
    min-height: 80px;
}
.row-content, .row-kpi, .row-footer {
    border: 1px solid #e0e0e0;
    margin-bottom: 10px;
    padding: 5px;
}

/* Ajoutez votre code Flexbox ci-dessous */
```

-----

## 3\. Les Missions Flexbox (Tâches à Réaliser)

Vous devez obtenir un agencement de tableau de bord moderne, comme le schéma suivant :

### Mission 1 : La Structure Principale (Disposition Mère)

1.  **Objectif :** Aligner la sidebar (`.col-gauche`) et le contenu principal (`.col-principale`) sur une ligne.
2.  **Tâche :**
      * Faire de `.dashboard-container` un conteneur Flexbox.
      * La `.col-gauche` (Sidebar) doit avoir une largeur **fixe de 250px**. Elle ne doit jamais rétrécir.
      * La `.col-principale` doit **prendre tout l'espace horizontal restant**.

### Mission 2 : Mise en Page Verticale de la Colonne Principale (Imbrication 1)

1.  **Objectif :** Organiser les trois sections de la colonne principale verticalement : les KPIs, le Contenu (Graphique/Notifs) et le Footer.
2.  **Tâche :**
      * Faire de `.col-principale` un conteneur Flexbox.
      * Changer l'axe principal pour qu'il soit **vertical** (`column`).
      * Le bloc du milieu (`.row-content`) doit pouvoir **grandir pour occuper le maximum de hauteur disponible**. Les autres lignes doivent prendre juste la hauteur nécessaire.

### Mission 3 : Les KPIs (Disposition Horizontale Imbriquée)

1.  **Objectif :** Afficher les trois KPIs (`D1`, `D2`, `D3`) sur une seule ligne avec une répartition égale de l'espace.
2.  **Tâche :**
      * Faire de `.row-kpi` un conteneur Flexbox.
      * Chacun des trois KPIs (`.kpi`) doit occuper **exactement un tiers de la largeur disponible**.

### Mission 4 : Le Graphique et les Notifications (Disposition à Ratio)

1.  **Objectif :** Aligner horizontalement le graphique (`E`) et les notifications (`F`), en respectant un ratio de taille strict.
2.  **Tâche :**
      * Faire de `.row-content` un conteneur Flexbox.
      * Le `.chart-area` (`E`) doit toujours prendre **70%** de la largeur.
      * Le `.notifications` (`F`) doit toujours prendre **30%** de la largeur.
      * *Indice :* Utilisez des valeurs spécifiques de `flex-grow` ou `flex-basis`.

### Mission 5 : Manipulation de l'Ordre (Test de Compréhension)

1.  **Objectif :** Malgré l'ordre dans le HTML, nous souhaitons que le statut du serveur (`H`) apparaisse à gauche et les statistiques détaillées (`G`) apparaissent à droite dans la ligne du footer.
2.  **Tâche :**
      * Faire de `.row-footer` un conteneur Flexbox.
      * Utiliser la propriété **`order`** sur les éléments `.footer-stats` et `.footer-status` pour inverser leur affichage.

### 🎯 Vérification Finale :

Après avoir appliqué tous les styles Flexbox, redimensionnez la fenêtre du navigateur :

  * La Sidebar doit rester à 250px.
  * La `.col-principale` doit toujours occuper l'espace restant et ses éléments internes doivent se redimensionner proportionnellement (sauf la sidebar).
  * L'ordre des éléments du footer doit être inversé.

