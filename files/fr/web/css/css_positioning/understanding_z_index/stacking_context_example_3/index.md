---
title: Exemple d'empilement 3
slug: Web/CSS/CSS_Positioning/Understanding_z_index/Stacking_context_example_3
tags:
  - Avancé
  - CSS
  - Guide
translation_of: Web/CSS/CSS_Positioning/Understanding_z_index/Stacking_context_example_3
original_slug: Web/CSS/Comprendre_z-index/Exemple_3
---
<div>{{PreviousMenuNext("Web/CSS/Comprendre_z-index/Exemple_2","", "Web/CSS/Comprendre_z-index")}}</div>

<h2 id="Troisième_exemple">Troisième exemple</h2>

<p>Ce dernier exemple illustre les problèmes qui peuvent survenir lorsqu'on utilise des éléments positionnés dans une hiérarchie HTML à plusieurs niveaux et lorsque des {{cssxref("z-index")}} sont assignés à l'aide de sélecteurs de classe.</p>

<p>Prenons un exemple de menu hiérarchique à 3 niveaux, fait de plusieurs <em>DIV</em> positionnés. Les deuxième et troisième niveaux apparaissent lors du survol ou d'un clic sur leur parent. D'ordinaire, ce type de menu est généré par un script, côté client ou côté serveur, de façon à ce que les règles de styles soient assignées à l'aide de sélecteurs de classe plutôt qu'avec des sélecteurs d'<em>id</em>.</p>

<p>Si les trois niveaux du menu se chevauchent partiellement, alors la gestion de l'empilement peut devenir problématique.</p>

<p>{{ EmbedLiveSample('Exemple', '320', '330') }}</p>

<p>Le menu de premier niveau est positionné relativement, ainsi aucun contexte d'empilement n'est créé.</p>

<p>Le menu de deuxième niveau est positionné en absolu à l'intérieur de son élément parent. Afin de le faire apparaître au dessus de tous les menus de premier niveau, on utilise un <code>z-index</code>. Le problème est que pour chaque menu de deuxième niveau, un contexte d'empilement se crée et chaque menu de troisième niveau appartient au contexte d'empilement de son parent.</p>

<p>Ainsi donc, un menu de troisième niveau s'empilera sous les menus de deuxième niveau suivants, car tous les menus de deuxième niveau partagent la même valeur de <code>z-index</code> et que les règles d'empilement par défaut s'appliquent.</p>

<p>Pour mieux comprendre la situation, voici la hiérarchie du contexte d'empilement :</p>

<ul>
 <li>Contexte d'empilement racine
  <ul>
   <li>Niveau #1
    <ul>
     <li>Niveau #2 (z-index : 1)
      <ul>
       <li>Niveau #3</li>
       <li>…</li>
       <li>Niveau #3</li>
      </ul>
     </li>
     <li>Niveau #2 (z-index : 1)</li>
     <li>…</li>
     <li>Niveau #2 (z-index : 1)</li>
    </ul>
   </li>
   <li>Niveau #1</li>
   <li>…</li>
   <li>Niveau #1</li>
  </ul>
 </li>
</ul>

<p>On peut contourner ce problème en supprimant le chevauchement entre les différents niveaux du menu, ou en utilisant des valeurs de <code>z-index</code> individuelles (et différentes) assignées à l'aide de sélecteurs d'<em>id</em> plutôt que des sélecteurs de classe ou encore en aplatissant la hiérarchie HTML.</p>

<div class="note">
  <p><strong>Note :</strong> Dans le code source, vous remarquerez que les menus de deuxième et troisième niveaux sont construits à l'aide de plusieurs boîtes <em>DIV</em> contenues dans un élément positionné en absolu. Ceci sert à les grouper et à les positionner en une seule fois.
  </p>
</div>

<h2 id="Exemple">Exemple</h2>

<h3 id="CSS">CSS</h3>

<pre class="brush: css">div {
  font: 12px Arial;
}

span.bold {
  font-weight: bold;
}

div.lev1 {
  width: 250px;
  height: 70px;
  position: relative;
  border: 2px outset #669966;
  background-color: #ccffcc;
  padding-left: 5px;
}

#container1 {
  z-index: 1;
  position: absolute;
  top: 30px;
  left: 75px;
}

div.lev2 {
  opacity: 0.9;
  width: 200px;
  height: 60px;
  position: relative;
  border: 2px outset #990000;
  background-color: #ffdddd;
  padding-left: 5px;
}

#container2 {
  z-index: 1;
  position: absolute;
  top: 20px;
  left: 110px;
}

div.lev3 {
  z-index: 10;
  width: 100px;
  position: relative;
  border: 2px outset #000099;
  background-color: #ddddff;
  padding-left: 5px;
}</pre>

<h3 id="HTML">HTML</h3>

<pre class="brush: html">&lt;br/&gt;

&lt;div class="lev1"&gt;
&lt;span class="bold"&gt;LEVEL #1&lt;/span&gt;
  &lt;div id="container1"&gt;
    &lt;div class="lev2"&gt;
      &lt;br/&gt;&lt;span class="bold"&gt;LEVEL #2&lt;/span&gt;
      &lt;br/&gt;z-index: 1;
      &lt;div id="container2"&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
        &lt;div class="lev3"&gt;&lt;span class="bold"&gt;LEVEL #3&lt;/span&gt;&lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class="lev2"&gt;
      &lt;br/&gt;&lt;span class="bold"&gt;LEVEL #2&lt;/span&gt;
      &lt;br/&gt;z-index: 1;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;

&lt;div class="lev1"&gt;
  &lt;span class="bold"&gt;LEVEL #1&lt;/span&gt;
&lt;/div&gt;

&lt;div class="lev1"&gt;
  &lt;span class="bold"&gt;LEVEL #1&lt;/span&gt;
&lt;/div&gt;

&lt;div class="lev1"&gt;
  &lt;span class="bold"&gt;LEVEL #1&lt;/span&gt;
&lt;/div&gt;
</pre>


<div>{{PreviousMenuNext("Web/CSS/Comprendre_z-index/Exemple_2","", "Web/CSS/Comprendre_z-index")}}</div>
