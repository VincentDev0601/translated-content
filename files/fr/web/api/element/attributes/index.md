---
title: element.attributes
slug: Web/API/Element/attributes
tags:
  - API
  - DOM
  - Element
  - Propriété
  - Reference
translation_of: Web/API/Element/attributes
---
<p>{{ APIRef("DOM") }}</p>

<p>La propriété <strong><code>Element.attributes</code></strong> renvoie une collection des noeuds d'attribut enregistrés dans le noeud spécifié. Il est une {{domxref("NamedNodeMap")}}, pas un tableau (<em>Array</em>), aussi il n'a pas de méthodes  {{jsxref("Array")}} et l'index de noeud {{domxref("Attr")}} peuvent différer entre les navigateurs. Pour être plus précis, les <code>attributs</code> sont une paire clé / valeur de chaînes représentant toutes les informations concernant cet attribut.</p>

<h2 id="Syntaxe_et_valeurs">Syntaxe</h2>

<pre class="syntaxbox">var <em>attr</em> =<em> element</em>.attributes;
</pre>

<h2 id="Exemple">Exemple</h2>

<h3 id="Exemples_basiques">Exemples basiques</h3>

<pre>// récupère le premier élément &lt;p&gt; du document
var para = document.getElementsByTagName("p")[0];
var attr = para.attributes;
</pre>

<h3 id="Énumération_des_attributs_d'éléments">Énumération des attributs d'éléments</h3>

<p>L'indexation numérique est utile pour parcourir tous les attributs d'un élément.<br>
 L'exemple suivant parcourt les nœuds d'attribut de l'élément du document avec l'ID "paragraph" et imprime la valeur de chaque attribut.</p>

<pre class="brush: html">&lt;!DOCTYPE html&gt;

&lt;html&gt;

 &lt;head&gt;
  &lt;title&gt;Exemple d'attributs&lt;/title&gt;
  &lt;script type="text/javascript"&gt;
   function listAttributes() {
     var paragraph = document.getElementById("paragraph");
     var result = document.getElementById("result");

     // D'abord, vérifier que le "paragraph" a quelques attributs    
     if (paragraph.hasAttributes()) {
       var attrs = paragraph.attributes;
       var output = "";
       for(var i = attrs.length - 1; i &gt;= 0; i--) {
         output += attrs[i].name + "-&gt;" + attrs[i].value;
       }
       result.value = output;
     } else {
       result.value = "No attributes to show";
     }
   }
  &lt;/script&gt;
 &lt;/head&gt;

&lt;body&gt;
 &lt;p id="paragraph" &gt;Sample Paragraph&lt;/p&gt;
 &lt;form action=""&gt;
  &lt;p&gt;
    &lt;input type="button" value="Show first attribute name and value"
      onclick="listAttributes();"&gt;
    &lt;input id="result" type="text" value=""&gt;
  &lt;/p&gt;
 &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

<p> </p>

<h2 id="Sp.C3.A9cification">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Status</th>
   <th scope="col">Comment</th>
  </tr>
  <tr>
   <td>{{SpecName('DOM WHATWG', '#dom-element-attributes', 'Element.attributes')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>De {{SpecName('DOM3 Core')}}, déplacé de {{domxref("Node")}} à {{domxref("Element")}}</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Core', 'core.html#ID-84CF096', 'Element.attributes')}}</td>
   <td>{{Spec2('DOM3 Core')}}</td>
   <td>Pas de changement de {{SpecName('DOM2 Core')}}</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 Core', 'core.html#ID-84CF096', 'Element.attributes')}}</td>
   <td>{{Spec2('DOM2 Core')}}</td>
   <td>Pas de changement de {{SpecName('DOM1')}}</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM1', 'level-one-core.html#ID-84CF096', 'Element.attributes')}}</td>
   <td>{{Spec2('DOM1')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Element.attributes")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{domxref("NamedNodeMap")}}, l'interface de l'objet retourné</li>
 <li>Considérations de compatibilité entre navigateurs : sur <a href="http://www.quirksmode.org/dom/w3c_core.html#attributes">quirksmode</a> (en)</li>
</ul>
