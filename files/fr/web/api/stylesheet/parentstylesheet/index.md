---
title: StyleSheet.parentStyleSheet
slug: Web/API/StyleSheet/parentStyleSheet
translation_of: Web/API/StyleSheet/parentStyleSheet
---
<div>
<div>{{APIRef ("CSSOM")}}</div>
</div>

<p>Renvoie la feuille de style qui inclut celle-ci, le cas échéant.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox"><em>ObjRef</em> = stylesheet.parentStyleSheet
</pre>

<h2 id="Example">Exemple</h2>

<pre class="brush:js">// trouve la feuille de style de niveau supérieur
If (stylesheet.parentStyleSheet) {
    Feuille = stylesheet.parentStyleSheet;
} autre {
    Feuille = feuille de style;
}</pre>

<h2 id="Notes">Remarques</h2>

<p>Cette propriété renvoie NULL est la feuille de style actuelle est une feuille de style de haut niveau ou si l'inclusion de la feuille de style n'est pas prise en charge.</p>

<h2 id="Specification">spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/2000/REC-DOM-Level-2-Style-20001113/stylesheets.html#StyleSheets-StyleSheet-parentStyleSheet">ParentStyleSheet </a></li>
</ul>
