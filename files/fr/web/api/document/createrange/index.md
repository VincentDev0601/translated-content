---
title: Document.createRange
slug: Web/API/Document/createRange
tags:
  - API
  - DOM
  - Document
  - Méthodes
translation_of: Web/API/Document/createRange
---
<div>{{APIRef("DOM")}}</div>

<p>Retourne un objet {{domxref("Range")}}.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox">range = document.createRange();
</pre>

<p><code>range</code> devient un objet {{domxref("Range")}}.</p>

<h2 id="Example">Exemple</h2>

<pre class="brush:js">var range = document.createRange();

range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);
</pre>

<h2 id="Notes">Notes</h2>

<p>Une fois un objet <code>Range</code> créé, il est nécessaire de spécifier les limites de départ et de fin avant de pouvoir utiliser la plupart des méthodes.</p>

<h2 id="Specification">Spécification</h2>

<ul>
 <li><a href="https://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113/ranges.html#Level-2-DocumentRange-idl">DOM Level 2 Range: DocumentRange.createRange</a></li>
</ul>
