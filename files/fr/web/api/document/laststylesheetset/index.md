---
title: Document.lastStyleSheetSet
slug: Web/API/Document/lastStyleSheetSet
tags:
  - API
  - DOM
  - Feuilles de styles
  - Propriétés
translation_of: Web/API/Document/lastStyleSheetSet
---
<p>{{ APIRef("DOM") }}{{ gecko_minversion_header("1.9") }}</p>

<p>Renvoie le dernier jeu de feuilles de styles activé ; cette valeur de la propriété change chaque fois que la propriété {{ domxref("document.selectedStyleSheetSet") }} est modifiée.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="eval"><em>lastStyleSheetSet</em> = document.lastStyleSheetSet
</pre>

<p>En retour, <code>lastStyleSheetSet</code> indique le jeu de feuilles de styles qui a été défini le plus récemment. Si le jeu de feuilles de style en cours n'a pas été modifié en définissant {{ domxref("document.selectedStyleSheetSet") }}, la valeur retournée est <code>null</code>.</p>

<div class="note">
  <p><strong>Note :</strong> Cette valeur ne doit pas changer lorsque {{ domxref("document.enableStyleSheetsForSet()") }} est appelé.</p>
</div>

<h2 id="Example">Exemple</h2>

<pre class="brush: js">var lastSheetSet = document.lastStyleSheetSet;
if (!lastSheetSet) {
  lastSheetSet = "Sheet not yet changed";
}
console.log("The last sheet set is: " + lastSheetSet);
</pre>

<h2 id="See_also">Voir aussi</h2>

<ul>
 <li>{{ domxref("document.preferredStyleSheetSet") }}</li>
 <li>{{ domxref("document.selectedStyleSheetSet") }}</li>
 <li>{{ domxref("document.styleSheetSets") }}</li>
 <li>{{ domxref("document.enableStyleSheetsForSet()") }}</li>
</ul>

<h2 id="Specification">Spécifications</h2>

<ul>
 <li><a href="http://www.whatwg.org/specs/web-apps/current-work/#alternate-style-sheets">HTML5: Alternate Style Sheets</a></li>
</ul>
