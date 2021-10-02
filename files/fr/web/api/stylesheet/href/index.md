---
title: Stylesheet.href
slug: Web/API/StyleSheet/href
translation_of: Web/API/StyleSheet/href
---
<div>{{APIRef ("CSSOM")}}</div>

<p>Renvoie l'emplacement de la feuille de style.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="eval"><em>Uri</em> = stylesheet.href
</pre>

<h3 id="Parameters">Paramètres</h3>

<ul>
 <li><code>uri</code> Est une chaîne contenant l'URI de la feuille de style.</li>
</ul>

<h2 id="Example">Exemple</h2>

<pre class="brush: html"> // sur une machine locale: 
 &lt;Html&gt; 
  &lt;Head&gt; 
   &lt;Link rel = "StyleSheet" href = "example.css" type = "text / css" /&gt; 
   &lt;Script&gt; 
    Function sref () { 
     Alerte (document.styleSheets [0] .href); 
    }
   &lt;/ Script&gt; 
  &lt;/ Head&gt; 
  &lt;Body&gt; 
   &lt;Div class = "tonnerre"&gt; Thunder &lt;/ div&gt;
   &lt;Button onclick = "sref ()"&gt; ss &lt;/ button&gt;
  &lt;/ Body&gt; 
 &lt;/ Html&gt;
// retourne "fichier: //// C: /Windows/Desktop/example.css
</pre>

<h2 id="Notes">Remarques</h2>

<p>Si la feuille de style est une feuille de style liée, la valeur de son attribut est son emplacement. Pour les feuilles de style en ligne, la valeur de cet attribut est <code>NULL</code>.</p>

<p>Cette propriété est en lecture seule sur Firefox, Opera, Google Chrome et Safari, et elle est lue / écrite dans Internet Explorer.</p>

<h2 id="Specification">spécification</h2>

<p><a href="http://www.w3.org/TR/2000/REC-DOM-Level-2-Style-20001113/stylesheets.html#StyleSheets-StyleSheet-href">Href </a></p>
