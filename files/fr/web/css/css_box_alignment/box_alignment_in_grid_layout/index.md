---
title: L'alignement des boîtes avec une grille CSS
slug: Web/CSS/CSS_Box_Alignment/Box_Alignment_In_Grid_Layout
tags:
  - CSS
  - CSS Grid
  - Grilles CSS
  - Guide
translation_of: Web/CSS/CSS_Box_Alignment/Box_Alignment_In_Grid_Layout
original_slug: Web/CSS/CSS_Box_Alignment/Alignement_boîtes_disposition_grille
---
<div>{{CSSRef}}</div>

<p>Le module de spécification <em><a href="/fr/docs/Web/CSS/CSS_Box_Alignment">Box Alignment</a></em> détaille le fonctionnement de l'alignement selon les différentes méthodes de disposition. Dans cet article, nous verrons comment fonctionne l'alignement des boîtes avec <a href="/fr/docs/Web/CSS/CSS_Grid_Layout">les grilles CSS</a>. Cette page détaille les aspects spécifiques relatifs à l'alignement et aux grilles. Pour une description générale des fonctionnalités communes pour les différentes dispositions, voir <a href="/fr/docs/Web/CSS/CSS_Box_Alignment">la page principale sur cette spécification</a>.</p>

<h2 id="Exemple_simple">Exemple simple</h2>

<p>Dans l'exemple qui suit, on utilise une disposition en grille et le conteneur possède un espace restant après avoir disposé les pistes à largeur fixe le long de l'axe en ligne. L'espace restant est distribué grâce à la propriété <code>justify-content</code>. Le long de l'axe secondaire, les éléments sont alignés au sein de leurs zones avec la propriété <code>align-items</code>. Le premier objet surcharge la valeur fournie par <code>align-items</code> en utilisant <code>align-self</code> avec la valeur <code>center</code>.</p>

<p>{{EmbedGHLiveSample("css-examples/box-alignment/overview/grid-align-items.html", '100%', 500)}}</p>

<h2 id="Axes_de_la_grille">Axes de la grille</h2>

<p>La grille est une méthode de disposition sur deux dimensions.</p>

<p>L'axe en ligne correspond à l'axe selon lequel les mots d'une phrase sont écrits pour le mode d'écriture utilisé. Ainsi, pour une langue écrite horizontalement (comme le français ou l'arabe), l'axe en ligne sera horizontal. Pour les modes d'écriture verticaux, cet axe sera vertica.</p>

<p><img alt="" src="inline_axis.png"></p>

<p>Pour aligner des éléments selon l'axe en ligne, on utilisera les propriétés commençant par <code>justify-</code> : {{cssxref("justify-content")}}, {{cssxref("justify-items")}} et {{cssxref("justify-self")}}.</p>

<p>L'axe de bloc est orthogonal à l'axe en ligne et évolue dans le sens où les blocs sont affichés sur la page (en français, par exemple, les blocs sont disposés de bas en haut).</p>

<p>Pour aligner des éléments sur l'axe de bloc, on utilisera les propriétés commençant par <code>align-</code> : {{cssxref("align-content")}}, {{cssxref("align-items")}} et {{cssxref("align-self")}}.</p>

<p><img alt="" src="block_axis.png"></p>

<h2 id="Alignement_individuel">Alignement individuel</h2>

<ul>
 <li>{{cssxref("justify-self")}}</li>
 <li>{{cssxref("align-self")}}</li>
 <li>{{cssxref("place-self")}}</li>
 <li>{{cssxref("justify-items")}}</li>
 <li>{{cssxref("align-items")}}</li>
 <li>{{cssxref("place-items")}}</li>
</ul>

<p>Ces propriétés permettent d'aligner individuellement chacun des éléments au sein de leur zone de grille. Les propriétés <code>align-items</code> et <code>justify-items</code> sont appliquées au conteneur de grille et définissent <code>align-self</code> et <code>justify-self</code> pour l'ensemble des sujets d'alignement. Cela signifie qu'on peut indiquer un alignement global au niveau du conteneur puis surcharger cette règle au cas par cas si besoin en utilisant <code>align-self</code> ou <code>justify-self</code> sur les éléments souhaités.</p>

<p>Les valeurs initiales pour <code>align-self</code> et <code>justify-self</code> sont <code>stretch</code>. Aussi, l'objet sera étiré sur toute la zone de grille qui lui est dédié. Une exception est apportée à cette règle lorsque l'élément possède des proportions intrinsèques (une image par exemple) ; dans ce cas, l'élément est aligné avec <code>start</code>sur les deux axes et l'élément n'est pas déformé.</p>

<h2 id="Alignement_du_contenu">Alignement du contenu</h2>

<ul>
 <li>{{cssxref("justify-content")}}</li>
 <li>{{cssxref("align-content")}}</li>
 <li>{{cssxref("place-content")}}</li>
</ul>

<p>Ces propriétés indiquent comment aligner les pistes de la grille lorsqu'il reste de l'espace à répartir. Ce scénario se produit uniquement si la somme des tailles des pistes est inférieure à la taille du conteneur de grille.</p>

<h2 id="Gouttières_et_versions_préfixées_des_propriétés">Gouttières et versions préfixées des propriétés</h2>

<ul>
 <li>{{cssxref("row-gap")}}</li>
 <li>{{cssxref("column-gap")}}</li>
 <li>{{cssxref("gap")}}</li>
 <li>{{cssxref("row-gap")}}</li>
 <li>{{cssxref("grid-column-gap")}}</li>
 <li>{{cssxref("gap")}}</li>
</ul>

<p>La spécification sur les grilles contenaient initialement les définitions des propriétés {{cssxref("row-gap")}}, {{cssxref("grid-column-gap")}} et {{cssxref("gap")}}. Les définitions de ces propriétés ont depuis été déplacées dans le module de spécification <em>Box Alignment</em> et ont respectivement été renommées en {{cssxref("row-gap")}}, {{cssxref("column-gap")}} et {{cssxref("gap")}}. Ainsi, elles peuvent être utilisées pour d'autres méthodes de disposition où les gouttières sont pertinentes.</p>

<p>À l'heure actuelle (juin 2018), seul Microsoft Edge prend en charge les versions non-préfixées pour ces propriétés. Il vaut donc mieux utiliser les deux versions (avec puis sans préfixe <code>grid-</code>) afin d'assurer une meilleure compatibilité.</p>

<h2 id="Référence">Référence</h2>

<h3 id="Propriétés_CSS">Propriétés CSS</h3>

<ul>
 <li>{{cssxref("justify-content")}}</li>
 <li>{{cssxref("align-content")}}</li>
 <li>{{cssxref("place-content")}}t</li>
 <li>{{cssxref("justify-items")}}</li>
 <li>{{cssxref("align-items")}}</li>
 <li>{{cssxref("place-items")}}</li>
 <li>{{cssxref("justify-self")}}</li>
 <li>{{cssxref("align-self")}}</li>
 <li>{{cssxref("place-self")}}</li>
 <li>{{cssxref("row-gap")}}</li>
 <li>{{cssxref("column-gap")}}</li>
 <li>{{cssxref("gap")}}</li>
</ul>

<h3 id="Termes_du_glossaire">Termes du glossaire</h3>

<ul>
 <li><a href="/fr/docs/Glossary/Cross_Axis">Axe secondaire</a></li>
 <li><a href="/fr/docs/Glossary/Main_Axis">Axe principal</a></li>
</ul>

<h2 id="Guides">Guides</h2>

<ul>
 <li><a href="/fr/docs/Web/CSS/CSS_Grid_Layout/Box_Alignment_in_CSS_Grid_Layout">Aligner les boîtes dans une disposition en grille</a></li>
</ul>

<h2 id="Ressources_externes">Ressources externes</h2>

<ul>
 <li><a href="https://rachelandrew.co.uk/css/cheatsheets/box-alignment">Anti-sèche pour l'alignement des boîtes (en anglais)</a></li>
 <li><a href="https://www.smashingmagazine.com/2016/11/css-grids-flexbox-box-alignment-new-layout-standard/">Alignement pour les grilles, les boîtes flexibles et les boîtes (en anglais)</a></li>
 <li><a href="https://blogs.igalia.com/jfernandez/2017/05/03/can-i-use-css-box-alignment/">Quelques pensées sur les implémentations partielles de <em>Box Alignment</em> (en anglais)</a></li>
</ul>
