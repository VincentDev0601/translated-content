---
title: NodeList.item()
slug: Web/API/NodeList/item
tags:
  - API
  - DOM
  - Liste
  - Méthodes
  - Noeuds
translation_of: Web/API/NodeList/item
---
<div>{{APIRef("DOM")}}</div>

<p>Renvoie un noeud depuis une <a href="/en-US/docs/Web/API/NodeList"><code>NodeList</code></a> par l'index. Cette méthode ne lance pas d'exceptions tant que vous fournissez des arguments. Une valeur <code>null</code> est renvoyée si l'index est hors des limites et une <code>TypeError</code> est lancée si aucun argument n'est fourni.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><em>nodeItem</em> = <em>nodeList</em>.item(<em>index</em>)
</pre>

<ul>
 <li><code>nodeList</code> est une <code>NodeList</code>. Elle est généralement obtenue à partir d'une autre propriété ou méthode DOM, telle que <a href="/en-US/docs/Web/API/Node/childNodes">childNodes</a>.</li>
 <li><code>index</code> est l'index du noeud à chercher. L'index commence à zéro.</li>
 <li><code>nodeItem</code> est le numéro d'<code>index</code> du noeud dans la <code>nodeList</code> retourné par la méthode <code>item</code>.</li>
</ul>

<h2 id="Syntaxe_alternative">Syntaxe alternative</h2>

<p>JavaScript propose également une syntaxe semblable à un tableau pour obtenir un élément d'une liste de nœuds par index :</p>

<pre class="eval"><em>nodeItem</em> = <em>nodeList</em>[<em>index</em>]
</pre>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: js">var tables = document.getElementsByTagName("table");
var firstTable = tables.item(1); // ou simplement tables[1] - renvoie le <strong>second</strong> tableau dans DOM
</pre>

<h2 id="Spécification">Spécification</h2>

<p><a href="https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html#method-item">DOM Level 1 Core: NodeList.item()</a></p>

<p><a href="https://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-844377136">DOM Level 2 Core: NodeList.item()</a></p>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.NodeList.item")}}</p>
