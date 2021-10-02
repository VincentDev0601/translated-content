---
title: Document.styleSheetSets
slug: Web/API/Document/styleSheetSets
tags:
  - API
  - DOM
  - Document
  - Feuilles de styles
  - Propriétés
translation_of: Web/API/Document/styleSheetSets
---
<div>{{APIRef("DOM")}}{{gecko_minversion_header("1.9")}}</div>

<p>Renvoie une liste active de tous les jeux de feuilles de styles actuellement disponibles.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox"><em>sets</em> = document.styleSheetSets
</pre>

<p>En retour, <code>sets</code> est une liste de jeux de feuilles de styles disponibles.</p>

<h2 id="Example">Exemple</h2>

<p>Étant donné un élément {{HTMLElement("ul")}} (liste) avec l'ID "sheetList", vous pouvez le remplir avec tous les noms de tous les jeux de feuilles de styles disponibles avec un code comme celui-ci :</p>

<pre class="brush:js">var list = document.getElementById("sheetList");
var sheets = document.styleSheetSets;

list.innerHTML = "";

for (var i = 0; i &lt; sheets.length; i++) {
  var item = document.createElement("li");

  item.innerHTML = sheets[i];
  list.appendChild(item);
}</pre>

<h2 id="Notes">Notes</h2>

<p>La liste des jeux de feuilles de styles disponibles est construite par énumération de toutes les feuilles de styles disponibles pour le document, dans l'ordre dans lequel elles sont répertoriées dans l'attribut {{domxref("document.styleSheets")}}, en ajoutant le <code>title</code> (<em>titre</em>) de chacune de celles en ayant un. Les doublons sont supprimés de la liste (en utilisant une comparaison sensible à la casse).</p>

<h2 id="Specification">Spécifications</h2>

<ul>
 <li><a href="http://www.whatwg.org/specs/web-apps/current-work/#alternate-style-sheets">HTML5 : Alternate Style Sheets</a></li>
</ul>

<h2 id="See_also">Voir aussi</h2>

<ul>
 <li>{{domxref("Stylesheet")}}</li>
 <li>{{domxref("document.styleSheets")}}</li>
 <li>{{domxref("document.lastStyleSheetSet")}}</li>
 <li>{{domxref("document.preferredStyleSheetSet")}}</li>
 <li>{{domxref("document.selectedStyleSheetSet")}}</li>
 <li>{{domxref("document.enableStyleSheetsForSet()")}}</li>
</ul>
