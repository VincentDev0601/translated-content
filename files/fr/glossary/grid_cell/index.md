---
title: Cellule de grille
slug: Glossary/Grid_Cell
tags:
  - CSS
  - Glossaire
  - Grilles
translation_of: Glossary/Grid_Cell
original_slug: Glossaire/Cellule_de_grille
---
<p>Dans une <a href="/fr/docs/Web/CSS/CSS_Grid_Layout">Grille CSS</a>, une <strong>cellule de grille</strong> est la plus petite unité de la grille CSS. Elle est un espace entre 4 intersections {{glossary("grid lines","lignes de grille")}} et conceptuellement assimilable à une cellule de tableau.</p>

<p><img alt="Diagram showing an individual cell on the grid." src="1_grid_cell.png"></p>

<p>Si vous ne placez pas d'éléments à l'aide de l'une des méthodes de placement de grille, les enfants directs du conteneur de grille seront placés un dans chaque cellule individuelle par l'algorithme de placement automatique. Les {{glossary("Grid Tracks", "pistes")}}  de ligne ou colonne supplémentaire seront créées par la création des cellules nécessaires pour contenir tous les éléments.</p>

<p>Dans l'exemple, nous avons créé une grille de trois colonnes. Les cinq éléments sont placés dans des cellules de la grille le long d'une rangée initiale de trois cellules de la grille, puis par l'ajout d'une nouvelle ligne pour les deux autres.</p>


<h2 id="Exemple">Exemple</h2>

<pre class="brush: css hidden">* {box-sizing: border-box;}

.wrapper {
    border: 2px solid #f76707;
    border-radius: 5px;
    background-color: #fff4e6;
}

.wrapper &gt; div {
    border: 2px solid #ffa94d;
    border-radius: 5px;
    background-color: #ffd8a8;
    padding: 1em;
    color: #d9480f;
}
</pre>

<pre class="brush: css">.wrapper {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  grid-auto-rows: 100px;
}
</pre>

<pre class="brush: html">&lt;div class="wrapper"&gt;
   &lt;div&gt;One&lt;/div&gt;
   &lt;div&gt;Two&lt;/div&gt;
   &lt;div&gt;Three&lt;/div&gt;
   &lt;div&gt;Four&lt;/div&gt;
   &lt;div&gt;Five&lt;/div&gt;
&lt;/div&gt;
</pre>

<p>{{ EmbedLiveSample('Exemple', '300', '280') }}</p>

<h2 id="En_apprendre_plus">En apprendre plus</h2>

<h3 id="Références_de_propriété">Références de propriété</h3>

<ul>
 <li>{{cssxref("grid-template-columns")}}</li>
 <li>{{cssxref("grid-template-rows")}}</li>
 <li>{{cssxref("grid-auto-rows")}}</li>
 <li>{{cssxref("grid-auto-columns")}}</li>
</ul>

<h3 id="En_lire_plus">En lire plus</h3>

<ul>
 <li>Guide des grilles CSS : <em><a href="/fr/docs/Web/CSS/CSS_Grid_Layout/Les_concepts_de_base">Les concepts de base des grilles CSS</a></em></li>
 <li><a href="https://drafts.csswg.org/css-grid/#grid-track-concept">Définition des cellules de grille dans la spécification CSS</a> (en)</li>
</ul>
