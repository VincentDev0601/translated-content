---
title: transform-origin
slug: Web/CSS/transform-origin
tags:
  - CSS
  - CSS Transoforms
  - Propriété CSS
  - Reference
  - transform-origin
  - 'valeur par défaut : center'
translation_of: Web/CSS/transform-origin
---
<div>{{CSSRef}}</div>

<p>La propriété <strong><code>transform-origin</code></strong> permet de modifier l'origine du repère pour les opérations de transformation d'un élément.</p>

<div>{{EmbedInteractiveExample("pages/css/transform-origin.html")}}</div>

<p>Par exemple, l'origine par défaut pour la fonction <code>rotate()</code> est le centre de la rotation. Cette propriété est utilisée en :</p>

<ol>
 <li>Translatant l'élément avec l'opposé de la valeur fournie</li>
 <li>Appliquant la transformation souhaitée sur l'élément</li>
 <li>Translatant l'élément avec la valeur fournie pour cette propriété.</li>
</ol>

<p>Les valeurs qui ne sont pas définies explicitement sont réinitialisées avec les valeurs correspondantes.</p>

<p>Par défaut, l'origine d'une transformation est <code>center</code>.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: css no-line-numbers">/* Utilisation d'une seule valeur */
transform-origin: 2px<em>;</em>
transform-origin: bottom;

/* x-offset y-offset */
transform-origin: 3cm 2px;

/* y-offset x-offset-keyword */
transform-origin: 2px left;

/* x-offset-keyword y-offset */
transform-origin: left 2px;

/* x-offset-keyword y-offset-keyword */
transform-origin: right top;

/* y-offset-keyword x-offset-keyword */
transform-origin: top right;

/* x-offset y-offset z-offset */
transform-origin: 2px 30% 10px;

/* y-offset x-offset-keyword z-offset */
transform-origin: 2px left 10px;

/* x-offset-keyword y-offset z-offset */
transform-origin: left 5px -3px;

/* x-offset-keyword y-offset-keyword z-offset */
transform-origin: right bottom 2cm;

/* y-offset-keyword x-offset-keyword z-offset */
transform-origin: bottom right 2cm;

/* Valeurs globales */
transform-origin: inherit;
transform-origin: initial;
transform-origin: unset;
</pre>

<p>La propriété <code>transform-origin</code> peut être définie en utiisant une, deux ou trois valeurs.</p>

<ul>
 <li>Avec une valeur, celle-ci doit être :
  <ul>
   <li>Une longueur (type {{cssxref("&lt;length&gt;")}})</li>
   <li>Un pourcentage (type {{cssxref("&lt;percentage&gt;")}}</li>
   <li>Un mot-clé parmi <code>left</code>, <code>center</code>, <code>right</code>, <code>top</code>, <code>bottom</code>.</li>
  </ul>
 </li>
 <li>Avec deux valeurs
  <ul>
   <li>La première valeur doit être une longueur (type {{cssxref("&lt;length&gt;")}}), un pourcentage (type {{cssxref("&lt;percentage&gt;")}} ou un mot-clé parmi <code>left</code>, <code>center</code>, <code>right</code></li>
   <li>La seconde valeur doit être une longueur (type {{cssxref("&lt;length&gt;")}}), un pourcentage (type {{cssxref("&lt;percentage&gt;")}} ou un mot-clé parmi <code>top</code>, <code>center</code>, <code>bottom</code>.</li>
  </ul>
 </li>
 <li>Avec trois valeurs
  <ul>
   <li>Les deux premières valeurs doivent être structurées comme la syntaxe avec deux valeurs</li>
   <li>La troisième valeur doit être une longueur (type {{cssxref("length")}}</li>
  </ul>
 </li>
</ul>

<h3 id="Valeur">Valeur</h3>

<dl>
 <dt><code>x-offset</code></dt>
 <dd>Une valeur du type {{cssxref("&lt;length&gt;")}} ou {{cssxref("&lt;percentage&gt;")}} qui décrit la distance, depuis le bord gauche de la boîte, à laquelle l'origine de la transformation sera placée.</dd>
 <dt><code>offset-keyword</code></dt>
 <dd>Un mot-clé parmi <code>left</code>, <code>right</code>, <code>top</code>, <code>bottom</code> ou <code>center</code> qui décrit le décalage correspondant.</dd>
 <dt><code>y-offset</code></dt>
 <dd>Une valeur du type {{cssxref("&lt;length&gt;")}} ou {{cssxref("&lt;percentage&gt;")}} qui décrit la distance, depuis le bord haut de la boîte, à laquelle l'origine de la transformation sera placée.</dd>
 <dt><code>x-offset-keyword</code></dt>
 <dd>Un mot-clé parmi <code>left</code>, <code>right</code> ou <code>center</code> qui décrit la distance, depuis le bord gauche de la boîte, à laquelle l'origine de la transformation sera placée.</dd>
 <dt><code>y-offset-keyword</code></dt>
 <dd>Un mot-clé parmi <code>top</code>, <code>bottom</code> ou <code>center</code> qui décrit la distance, depuis le bord haut de la boîte, à laquelle l'origine de la transformation sera placée.</dd>
 <dt><code>z-offset</code></dt>
 <dd>Une valeur du type {{cssxref("&lt;length&gt;")}} (et jamais une valeur du type {{cssxref("&lt;percentage&gt;")}}, sinon la déclaration serait invalide) qui décrit la distance, depuis l'œil de l'utilisateur, de l'origine de la transformation sur l'axe de profondeur (z)..</dd>
</dl>

<p>Les mots-clés sont des raccourcis qui correspondent aux valeurs {{cssxref("&lt;percentage&gt;")}} suivantes :</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Mot-clé</th>
   <th scope="col">Valeur</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>left</code></td>
   <td><code>0%</code></td>
  </tr>
  <tr>
   <td><code>center</code></td>
   <td><code>50%</code></td>
  </tr>
  <tr>
   <td><code>right</code></td>
   <td><code>100%</code></td>
  </tr>
  <tr>
   <td><code>top</code></td>
   <td><code>0%</code></td>
  </tr>
  <tr>
   <td><code>bottom</code></td>
   <td><code>100%</code></td>
  </tr>
 </tbody>
</table>

<h3 id="Syntaxe_formelle">Syntaxe formelle</h3>

{{csssyntax}}

<h2 id="Exemples">Exemples</h2>

<p>Voir la page sur <a href="/fr/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms">l'utilisation des transformations CSS</a> pour des exemples supplémentaires.</p>

<h3 id="a_demonstration_of_various_transform_values">Illustrations des différentes valeurs de transform</h3>

<p>Cet exemple illustre ce que donnent les différentes valeurs de <code>transform-origin</code> pour différentes fonctions de transformation.</p>

<pre class="brush: html hidden">
&lt;div class="container"&gt;

&lt;div class="example"&gt;
  &lt;div class="box box1"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: none;
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box2"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: rotate(30deg);
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box3"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: rotate(30deg);
transform-origin: 0 0;
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box4"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: rotate(30deg);
transform-origin: 100% 100%;
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box5"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: rotate(30deg);
transform-origin: -1em -3em;
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box6"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: scale(1.7);
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box7"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: scale(1.7);
transform-origin: 0 0;
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box8"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: scale(1.7);
transform-origin: 100% -30%;
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box9"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: skewX(50deg);
transform-origin: 100% -30%;
&lt;/pre&gt;

&lt;div class="example"&gt;
  &lt;div class="box box10"&gt;&amp;nbsp;&lt;/div&gt;
  &lt;div class="box original"&gt;&amp;nbsp;&lt;/div&gt;
&lt;/div&gt;

&lt;pre&gt;
transform: skewY(50deg);
transform-origin: 100% -30%;
&lt;/pre&gt;

&lt;/div&gt;
</pre>

<pre class="brush: css hidden">
.container {
  display: grid;
  grid-template-columns: 200px 100px;
  gap: 20px;
}

.example {
  position: relative;
  margin: 0 2em 4em 5em;
}

.box {
  display: inline-block;
  width: 3em;
  height: 3em;
  border: solid 1px;
  background-color: palegreen;
}

.original {
  position: absolute;
  left: 0;
  opacity: 20%;
}

.box1 {
  transform: none;
}

.box2 {
  transform: rotate(30deg);
}

.box3 {
  transform: rotate(30deg);
  transform-origin: 0 0;
}

.box4 {
  transform: rotate(30deg);
  transform-origin: 100% 100%;
}

.box5 {
  transform: rotate(30deg);
  transform-origin: -1em -3em;
}

.box6 {
  transform: scale(1.7);
}

.box7  {
  transform: scale(1.7);
  transform-origin: 0 0;
}

.box8 {
  transform: scale(1.7);
  transform-origin: 100% -30%;
}

.box9 {
  transform: skewX(50deg);
  transform-origin: 100% -30%;
}

.box10 {
  transform: skewY(50deg);
  transform-origin: 100% -30%;
}

</pre>

<p>{{EmbedLiveSample('a_demonstration_of_various_transform_values', '', 1350) }}</p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">État</th>
   <th scope="col">Commentaires</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('CSS3 Transforms', '#transform-origin-property', 'transform-origin')}}</td>
   <td>{{Spec2('CSS3 Transforms')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<p>{{cssinfo}}</p>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("css.properties.transform-origin")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms">Utiliser les transformations CSS</a></li>
 <li><a href="https://css-tricks.com/almanac/properties/t/transform-origin/">https://css-tricks.com/almanac/properties/t/transform-origin/</a></li>
</ul>
