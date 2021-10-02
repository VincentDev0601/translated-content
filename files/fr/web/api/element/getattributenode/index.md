---
title: element.getAttributeNode
slug: Web/API/Element/getAttributeNode
tags:
  - API
  - Attributs
  - DOM
  - Element
  - Méthodes
  - Noeud
translation_of: Web/API/Element/getAttributeNode
---
<p>{{ APIRef("DOM") }}</p>

<h2 id="R.C3.A9sum.C3.A9">Résumé</h2>

<p>Renvoie le nœud d'attribut spécifié pour l'élément courant, en tant que noeud <code>Attr</code>.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var attrNode = element.getAttributeNode(attrName);</pre>

<ul>
 <li><code>attrNode</code> est un nœud <code>Attr</code> pour l'attribut demandé.</li>
 <li><code>attrName</code> est une chaîne de caractères qui contient le nom de l'attribut.</li>
</ul>

<h2 id="Exemple">Exemple</h2>

<pre>// html: &lt;div id="top" /&gt;
var t = document.getElementById("top");
var idAttr = t.getAttributeNode("id");
alert(idAttr.value == "top")
</pre>

<h2 id="Notes">Notes</h2>

<p>Lorsqu'elle est appelée sur un élément HTML dans un DOM marqué comme un document HTML, <code>getAttributeNode</code> passe en minuscules son argument avant de continuer.</p>

<p>Les nœuds <code>Attr</code> héritent de <code>Node</code>, mais ne sont pas considérés comme faisant partie de l'arbre du document. Les attributs habituels des nœuds comme <a href="fr/DOM/element.parentNode">parentNode</a>, <a href="fr/DOM/element.previousSibling">previousSibling</a>, et <a href="fr/DOM/element.nextSibling">nextSibling</a> sont <code>null</code> pour un nœud <code>Attr</code>. Vous pouvez cependant accéder à l'élément auquel cet attribut appartient grâce à la propriété <code>ownerElement</code>.</p>

<p><a href="fr/DOM/element.getAttribute">getAttribute</a> est habituellement utilisé à la place de <code>getAttributeNode</code> pour obtenir la valeur d'un attribut d'un élément.</p>

<p>{{ DOMAttributeMethods() }}</p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-217A91B8">DOM Level 2 Core : getAttributeNode</a> — <small><a href="http://www.yoyodesign.org/doc/w3c/dom2-core/core.html#ID-217A91B8">traduction en français</a> (non normative)</small></li>
 <li><a href="http://www.whatwg.org/specs/web-apps/current-work/multipage/dom.html#apis-in-html-documents">HTML 5: APIs in HTML documents</a></li>
</ul>