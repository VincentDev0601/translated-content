---
title: element.setAttributeNodeNS
slug: Web/API/Element/setAttributeNodeNS
tags:
  - API
  - DOM
  - Element
  - Méthodes
translation_of: Web/API/Element/setAttributeNodeNS
---
<p>{{ APIRef("DOM") }}</p>

<p><code>setAttributeNodeNS</code> ajoute un nouveau nœud attribut avec l'espace de noms et le nom spécifiés.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="eval"><em>replacedAttr</em> = element.setAttributeNodeNS(<em>attributeNode</em>)
</pre>

<dl>
 <dt><code>replacedAttr</code></dt>
 <dd>Le nœud attribut remplacé, si applicable, renvoyé par cette fonction.</dd>
 <dt><code>attributeNode</code></dt>
 <dd>Un nœud <code>Attr</code>.</dd>
</dl>

<h2 id="Exemple">Exemple</h2>

<pre>// &lt;div id="one" special-align="utterleft"&gt;one&lt;/div&gt;
// &lt;div id="two"&gt;two&lt;/div&gt;

var myns = "http://www.mozilla.org/ns/specialspace";
var d1 = document.getElementById("one");
var d2 = document.getElementById("two");
var a = d1.getAttributeNodeNS(myns, "special-align");
d2.setAttributeNodeNS(a);

alert(d2.attributes[1].value) // renvoie : "utterleft"
</pre>

<h2 id="Notes">Notes</h2>

<p>Si l'attribut spécifié existe déjà sur l'élément, cet attribut est remplacé par le nouveau et l'ancien est renvoyé.</p>

<p>Notez que si vous essayez de définir sans cloner le noeud, Mozilla donne une erreur "Attribut déjà utilisé" NS_ERROR_DOM_INUSE_ATTRIBUTE_ERR, car le DOM nécessite que le clonage d'<code>Attr</code> soit réutilisé (contrairement aux autres Noeuds qui peuvent être déplacés).</p>

<p>{{ DOMAttributeMethods() }}</p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-ElSetAtNodeNS">DOM Level 2 Core: setAttributeNodeNS (en)</a> <small>— <a href="http://www.yoyodesign.org/doc/w3c/dom2-core/core.html#ID-ElSetAtNodeNS">traduction en français</a> (non normative)</small></li>
</ul>
