---
title: Node.parentElement
slug: Web/API/Node/parentElement
tags:
  - API
  - DOM
  - Noeuds
  - Propriétés
  - parent
translation_of: Web/API/Node/parentElement
---
<div>
<div>
<div>{{APIRef("DOM")}}</div>
</div>

<div>La propriété en lecture seule <code><strong>Node.parentElement</strong></code> renvoie le parent du noeud DOM ({{domxref("Element")}}) ou <code><strong>null</strong></code> si ce dernier n'a pas de parent ou si le parent n'est pas un {{domxref("Element")}} du DOM.</div>
</div>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox"><em>parentElement</em> = <em>node</em>.parentElement
</pre>

<p><code><strong>parentElement</strong></code> référence l'élément parent d'un nœud (<code><strong>node</strong></code>). C'est toujours un objet {{domxref("Element")}}  du DOM ou <code>null</code>.</p>

<h2 id="Example">Exemple</h2>

<pre class="brush:js">if (node.parentElement) {
    node.parentElement.style.color = "red";
}</pre>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>Sur quelques navigateurs, la propriété <code>parentElement</code> est seulement définie sur les noeuds qui sont eux-mêmes des {{domxref("Element")}}. En particulier, elle n'est pas définie sur les noeuds texte.</p>

<div>


<p>{{Compat("api.Node.parentElement")}}</p>
</div>

<h2 id="Spécifications">Spécifications</h2>

<ul>
 <li>{{spec("http://dvcs.w3.org/hg/domcore/raw-file/tip/Overview.html#parent-element", "DOM Level 4: Node.parentElement", "WD")}}</li>
</ul>

<h2 id="See_also">Voir aussi</h2>

<ul>
 <li>{{domxref("Node.parentNode")}}</li>
</ul>
