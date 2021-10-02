---
title: document.createTextNode
slug: Web/API/Document/createTextNode
tags:
  - API
  - DOM
  - Méthodes
  - Reference
translation_of: Web/API/Document/createTextNode
---
<p>{{APIRef("DOM")}}</p>

<p>Crée un nouveau nœud de texte.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><var>var text</var> = document.createTextNode(<var>données</var>);
</pre>

<ul>
 <li><code>texte</code> est un nœud de texte.</li>
 <li><code>donnees</code> est une chaîne contenant les données à placer dans le nœud de texte.</li>
</ul>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: html">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
&lt;title&gt;createTextNode example&lt;/title&gt;
&lt;script&gt;
function addTextNode(text) {
  var newtext = document.createTextNode(text),
      p1 = document.getElementById("p1");

  p1.appendChild(newtext);
}
&lt;/script&gt;
&lt;/head&gt;

&lt;body&gt;
  &lt;button onclick="addTextNode('YES! ');"&gt;YES!&lt;/button&gt;
  &lt;button onclick="addTextNode('NO! ');"&gt;NO!&lt;/button&gt;
  &lt;button onclick="addTextNode('WE CAN! ');"&gt;WE CAN!&lt;/button&gt;

  &lt;hr /&gt;

  &lt;p id="p1"&gt;First line of paragraph.&lt;/p&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

<h2 id="Sp.C3.A9cification">Spécifications</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName("DOM3 Core", "core.html#ID-1975348127", "Document.createTextNode()")}}</td>
   <td>{{Spec2("DOM3 Core")}}</td>
   <td>Pas de changement</td>
  </tr>
  <tr>
   <td>{{SpecName("DOM2 Core", "core.html#ID-1975348127", "Document.createTextNode()")}}</td>
   <td>{{Spec2("DOM2 Core")}}</td>
   <td>Définition initiale</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Document.createTextNode")}}</p>
