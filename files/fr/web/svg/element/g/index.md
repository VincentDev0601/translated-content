---
title: <g>
slug: Web/SVG/Element/g
tags:
  - Element
  - Reference
  - SVG
  - SVG Conteneur
translation_of: Web/SVG/Element/g
---
<div>{{SVGRef}}</div>

<p>L'élément <code>g</code> est un conteneur utilisé pour grouper des objets.</p>

<p>Les transformations appliquées à l'élément <code>g</code> sont reportées à tous ses éléments enfants. Les attributs appliqués sont également reportés aux éléments enfants. De plus, il peut être utilisé pour définir des objets complexes qui seront référencés ultérieurement avec l'élément {{SVGElement("use")}}.</p>

<h2>Exemple</h2>

<pre class="brush: css hidden">html,body,svg { height:100% }</pre>


<pre class="brush: html">&lt;svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;!-- Les enfants de g héritent de ses attributs de présentation --&gt;
  &lt;g fill="white" stroke="green" stroke-width="5"&gt;
    &lt;circle cx="40" cy="40" r="25" /&gt;
    &lt;circle cx="60" cy="60" r="25" /&gt;
  &lt;/g&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('exemple', 100, '100%')}}</p>

<h2 id="Attributs">Attributs</h2>

<p>Cet élément n'a que des attributs globaux</p>

<h3 id="Attributs_globaux">Attributs globaux</h3>

<dl>
 <dt><a href="/fr/docs/Web/SVG/Attribute/Core">Attributs de base</a></dt>
 <dd><small>Notamment: {{SVGAttr('id')}}, {{SVGAttr('tabindex')}}</small></dd>
 <dt><a href="/fr/docs/Web/SVG/Attribute/Styling">Attributs de style</a></dt>
 <dd><small>{{SVGAttr('class')}}, {{SVGAttr('style')}}</small></dd>
 <dt><a href="/fr/docs/Web/SVG/Attribute/Conditional_Processing">Attributs de traitement conditionnel</a></dt>
 <dd><small>Notamment: {{SVGAttr('requiredExtensions')}}, {{SVGAttr('systemLanguage')}}</small></dd>
 <dt>Attributs d'événement</dt>
 <dd><small><a href="/fr/docs/Web/SVG/Attribute/Events#Attributs_d'événement_globaux">Attributs d'événement globaux</a>, <a href="/fr/docs/Web/SVG/Attribute/Events#Attributs_d'événement_graphiques">Attributs d'événement graphiques</a></small></dd>
 <dt><a href="/fr/docs/Web/SVG/Attribute/Presentation">Attributs de présentation</a></dt>
 <dd><small>Notamment: {{SVGAttr('clip-path')}}, {{SVGAttr('clip-rule')}}, {{SVGAttr('color')}}, {{SVGAttr('color-interpolation')}}, {{SVGAttr('color-rendering')}}, {{SVGAttr('cursor')}}, {{SVGAttr('display')}}, {{SVGAttr('fill')}}, {{SVGAttr('fill-opacity')}}, {{SVGAttr('fill-rule')}}, {{SVGAttr('filter')}}, {{SVGAttr('mask')}}, {{SVGAttr('opacity')}}, {{SVGAttr('pointer-events')}}, {{SVGAttr('shape-rendering')}}, {{SVGAttr('stroke')}}, {{SVGAttr('stroke-dasharray')}}, {{SVGAttr('stroke-dashoffset')}}, {{SVGAttr('stroke-linecap')}}, {{SVGAttr('stroke-linejoin')}}, {{SVGAttr('stroke-miterlimit')}}, {{SVGAttr('stroke-opacity')}}, {{SVGAttr('stroke-width')}}, {{SVGAttr("transform")}}, {{SVGAttr('vector-effect')}}, {{SVGAttr('visibility')}}</small></dd>
 <dt>Attributs Aria</dt>
 <dd><small><code>aria-activedescendant</code>, <code>aria-atomic</code>, <code>aria-autocomplete</code>, <code>aria-busy</code>, <code>aria-checked</code>, <code>aria-colcount</code>, <code>aria-colindex</code>, <code>aria-colspan</code>, <code>aria-controls</code>, <code>aria-current</code>, <code>aria-describedby</code>, <code>aria-details</code>, <code>aria-disabled</code>, <code>aria-dropeffect</code>, <code>aria-errormessage</code>, <code>aria-expanded</code>, <code>aria-flowto</code>, <code>aria-grabbed</code>, <code>aria-haspopup</code>, <code>aria-hidden</code>, <code>aria-invalid</code>, <code>aria-keyshortcuts</code>, <code>aria-label</code>, <code>aria-labelledby</code>, <code>aria-level</code>, <code>aria-live</code>, <code>aria-modal</code>, <code>aria-multiline</code>, <code>aria-multiselectable</code>, <code>aria-orientation</code>, <code>aria-owns</code>, <code>aria-placeholder</code>, <code>aria-posinset</code>, <code>aria-pressed</code>, <code>aria-readonly</code>, <code>aria-relevant</code>, <code>aria-required</code>, <code>aria-roledescription</code>, <code>aria-rowcount</code>, <code>aria-rowindex</code>, <code>aria-rowspan</code>, <code>aria-selected</code>, <code>aria-setsize</code>, <code>aria-sort</code>, <code>aria-valuemax</code>, <code>aria-valuemin</code>, <code>aria-valuenow</code>, <code>aria-valuetext</code>, <code>role</code></small></dd>
</dl>

<h2 id="Contexte_d'utilisation">Contexte d'utilisation</h2>

<p>{{svginfo}}</p>

<h2 id="Spécifications">Spécifications</h2>

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
   <td>{{SpecName("SVG2", "struct.html#GElement", "&lt;g&gt;")}}</td>
   <td>{{Spec2("SVG2")}}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName("SVG1.1", "struct.html#Groups", "&lt;g&gt;")}}</td>
   <td>{{Spec2("SVG1.1")}}</td>
   <td>Initial definition</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("svg.elements.g")}}</p>
