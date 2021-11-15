---
title: Zone de grille
slug: Glossary/Grid_Areas
tags:
  - CSS
  - Glossaire
  - Grilles
translation_of: Glossary/Grid_Areas
original_slug: Glossaire/Zones_de_grille
---
<p>Une <strong>zone de grille</strong> est une {{glossary("grid cell","cellule de grille")}}  ou plus, qui constitue une zone rectangulaire sur la grille. Les zones de grille sont créées lorsque vous placez un élément en utilisant le  <a href="/fr/docs/Web/CSS/CSS_Grid_Layout/Placer_les_%C3%A9l%C3%A9ments_sur_les_lignes_d_une_grille_CSS">placement de la ligne de base</a> ou lors de la définition des zones par l'utilisation de <a href="/fr/docs/Web/CSS/CSS_Grid_Layout/D%C3%A9finir_des_zones_sur_une_grille">zones de grille nommées</a>.</p>

<p><img alt="Image showing a highlighted grid area" src="1_grid_area.png"></p>

<p>Les zones de grille doivent être de nature rectangulaire ; il n'est pas possible de créer, par exemple, une zone de grille en forme de T ou de L.</p>

<p>Dans l'exemple ci-dessous, nous avons un conteneur de grille avec deux éléments de grille nommés à l'aide de la propriété {{cssxref("grid-area")}}  et mis sur la grille en utilisant {{cssxref("grid-template-areas")}}. Cela crée deux zones de grille, l'une couvrant quatre cellules de la grille, et deux autres d'une seule cellule.</p>

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
  grid-template-rows: 100px 100px;
  grid-template-areas:
    "a a b"
    "a a b";
}
.item1 {
  grid-area: a;
}
.item2 {
  grid-area: b;
}
</pre>

<pre class="brush: html">&lt;div class="wrapper"&gt;
   &lt;div class="item1"&gt;Item&lt;/div&gt;
   &lt;div class="item2"&gt;Item&lt;/div&gt;
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
 <li>{{cssxref("grid-template-areas")}}</li>
 <li>{{cssxref("grid-area")}}</li>
</ul>

<h3 id="En_lire_plus">En lire plus</h3>

<ul>
 <li>Guide des grilles CSS : <em><a href="/fr/docs/Web/CSS/CSS_Grid_Layout/Les_concepts_de_base">Les concepts de base des grilles CSS</a></em></li>
 <li>Guide des grilles CSS : <em><a href="/fr/docs/Web/CSS/CSS_Grid_Layout/D%C3%A9finir_des_zones_sur_une_grille">Définir des zones sur une grille</a></em></li>
 <li><a href="https://drafts.csswg.org/css-grid/#grid-area-concept">Définition des zones de grille dans la spécification dans les grilles CSS</a> (en)</li>
</ul>
