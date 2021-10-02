---
title: element.setAttributeNode
slug: Web/API/Element/setAttributeNode
tags:
  - API
  - DOM
  - Element
  - Méthode
  - Reference
translation_of: Web/API/Element/setAttributeNode
---
<p>{{ APIRef("DOM") }}</p>

<p><code>setAttributeNode</code><code>()</code>  ajoute un nouveau nœud <code>Attr</code> à l'élément courant.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var replacedAttr = element.setAttributeNode(attribute);</pre>

<ul>
 <li><code>attribute</code> est le nœud <code>Attr</code> à définir sur l'élément.</li>
 <li><code>replacedAttr</code> est le nœud d'attribut remplacé, renvoyé par la fonction, s'il y en avait un.</li>
</ul>

<h2 id="Exemple">Exemple</h2>

<pre>// &lt;div id="one" align="left"&gt;one&lt;/div&gt;
// &lt;div id="two"&gt;two&lt;/div&gt;
var d1 = document.getElementById("one");
var d2 = document.getElementById("two");
var a = d1.getAttributeNode("align");
d2.setAttributeNode(a);
alert(d2.attributes[1].value)
// retourne: `left'
</pre>

<h2 id="Notes">Notes</h2>

<p>Si l'attribut nommé existe déjà sur l'élément, cet attribut est remplacé par le nouveau et le nœud remplacé est renvoyé.</p>

<p>Cette méthode est peu utilisée. On lui préfère souvent  {{domxref("Element.setAttribute()")}}  pour modifier la valeur d'un attribut d'élément.</p>

<p>{{DOMAttributeMethods()}}</p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-887236154">DOM Level 2 Core : setAttributeNode</a> — <small><a href="http://www.yoyodesign.org/doc/w3c/dom2-core/core.html#ID-887236154">traduction en français</a> (non normative</small> (Introduit dans <a href="http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html#method-setAttributeNode">DOM Level 1 Core</a>)</li>
</ul>
