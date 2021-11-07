---
title: Width
slug: Web/SVG/Attribute/width
translation_of: Web/SVG/Attribute/width
---
<p>« <a href="/fr/SVG/Attribute" title="en/SVG/Attribute">SVG Attribute reference home</a></p>

<p>Cet attribut indique une dimension horizontale <code>&lt;length&gt;</code> dans le système de coordonnées. La donnée (ou coordonnée) définie par cet attribut dépend de l'élément sur lequel il est appliqué. La plupart du temps, il représente la largeur de la région rectangulaire composant l'élément (voir les exceptions dans la documentation pour chaque type d'élément).</p>

<p>Cet attribut doit être spécifié, hormis pour les éléments {{ SVGElement("svg") }} dont la valeur par défaut est de 100% (exepté pour l'élément racine {{ SVGElement("svg") }} qui possède un parent HTML),  {{ SVGElement("filter") }} et {{ SVGElement("mask") }} dont la valeur par défaut est de 120%.</p>

<h2 id="Contexte_d'utilisation">Contexte d'utilisation</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Catégories</th>
   <td>Aucune</td>
  </tr>
  <tr>
   <th scope="row">Valeur</th>
   <td><a href="/fr/SVG/Content_type#Length" title="https://developer.mozilla.org/en/SVG/Content_type#Length">&lt;length&gt;</a></td>
  </tr>
  <tr>
   <th scope="row">Animable</th>
   <td>Oui</td>
  </tr>
  <tr>
   <th scope="row">Document normatif</th>
   <td><a href="http://www.w3.org/TR/SVG/extend.html#ForeignObjectElementWidthAttribute">SVG 1.1 (2nd Edition): foreignObject element</a><br>
    <a href="http://www.w3.org/TR/SVG/struct.html#ImageElementWidthAttribute">SVG 1.1 (2nd Edition): image element</a><br>
    <a href="http://www.w3.org/TR/SVG/pservers.html#PatternElementWidthAttribute">SVG 1.1 (2nd Edition): pattern element</a><br>
    <a href="http://www.w3.org/TR/SVG/shapes.html#RectElementWidthAttribute">SVG 1.1 (2nd Edition): rect element</a><br>
    <a href="http://www.w3.org/TR/SVG/struct.html#SVGElementWidthAttribute">SVG 1.1 (2nd Edition): svg element</a><br>
    <a href="http://www.w3.org/TR/SVG/struct.html#UseElementWidthAttribute">SVG 1.1 (2nd Edition): use element</a><br>
    <a href="http://www.w3.org/TR/SVG/filters.html#FilterPrimitiveWidthAttribute">SVG 1.1 (2nd Edition): Filter primitive</a><br>
    <a href="http://www.w3.org/TR/SVG/masking.html#MaskElementWidthAttribute">SVG 1.1 (2nd Edition): mask element</a></td>
  </tr>
 </tbody>
</table>

<p>{{ page("fr/docs/Web/SVG/Content_type","Length") }}</p>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: xml">&lt;?xml version="1.0"?&gt;
&lt;svg width="120" height="120"
     viewBox="0 0 120 120"
     xmlns="http://www.w3.org/2000/svg"&gt;

  &lt;rect x="10" y="10" width="100" height="100"/&gt;
&lt;/svg&gt;</pre>

<h2 id="Eléments">Eléments</h2>

<p>Les éléments suivants peuvent utiliser l'attribut <code>width</code> :</p>

<ul>
 <li><a href="/fr/SVG/Element#FilterPrimitive" title="en/SVG/Element#FilterPrimitive">Filter primitive elements</a> »</li>
 <li>{{ SVGElement("filter") }}</li>
 <li>{{ SVGElement("foreignObject") }}</li>
 <li>{{ SVGElement("image") }}</li>
 <li>{{ SVGElement("pattern") }}</li>
 <li>{{ SVGElement("rect") }}</li>
 <li>{{ SVGElement("svg") }}</li>
 <li>{{ SVGElement("use") }}</li>
 <li>{{ SVGElement("mask") }}</li>
</ul>
