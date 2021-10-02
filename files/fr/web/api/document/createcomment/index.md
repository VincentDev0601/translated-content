---
title: document.createComment
slug: Web/API/Document/createComment
tags:
  - API
  - DOM
  - Méthodes
  - Reference
translation_of: Web/API/Document/createComment
---
<div>{{APIRef("DOM")}}</div>

<p><code>createComment()</code> crée et retourne un nouveau noeud de type commentaire.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox"><em>CommentNode</em> = document.createComment(data)
</pre>

<h3 id="Parameters">Paramètres</h3>

<dl>
 <dt><code>data</code></dt>
 <dd>Une chaîne de caractères représentant le contenu du commentaire.</dd>
</dl>

<h2 id="Example">Exemple</h2>

<pre class="brush:js">var docu = new DOMParser().parseFromString('&lt;xml&gt;&lt;/xml&gt;',  "application/xml");
var comment = docu.createComment('Voici un commentaire pas très bien caché');

docu.getElementsByTagName('xml')[0].appendChild(comment);

alert(new XMLSerializer().serializeToString(docu));
// Affiche: &lt;xml&gt;&lt;!--Voici un commentaire pas très bien caché--&gt;&lt;/xml&gt;</pre>

<h2 id="Spécification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html#method-createComment">createComment</a></li>
</ul>
