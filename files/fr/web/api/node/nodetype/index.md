---
title: element.nodeType
slug: Web/API/Node/nodeType
tags:
  - API
  - DOM
  - Noeuds
  - Propriétés
  - Types
translation_of: Web/API/Node/nodeType
---
<div>{{APIRef("DOM")}}</div>

<div>La propriété en lecture seule <code><strong>Node.nodeType</strong></code> représente le type du noeud.</div>

<h2 id="Description">Description</h2>

<p>La propriété <strong><code>nodeType</code></strong> peut être utilisée pour distinguer les uns des autres les différents genres de noeuds tels que {{domxref("Element")}}, {{domxref("Text")}} et {{domxref("Comment")}} .</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><var>Type</var> = <var>node</var> .nodeType
</pre>

<p>Renvoie un entier (<em>integer</em>) qui spécifie le type du noeud ; les valeurs possibles sont listées dans  {{anch("Constantes")}}.</p>

<h2>Constantes</h2>

<h3 id="Exemple">Constantes de type nœud</h3>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Constante</th>
   <th scope="col">Valeur</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>Node.ELEMENT_NODE</code></td>
   <td><code>1</code></td>
   <td>Un noeud {{domxref("Element")}}  tel que {{HTMLElement("p")}} ou {{HTMLElement("div")}}<code>.</code></td>
  </tr>
  <tr>
   <td><code>Node.TEXT_NODE</code></td>
   <td><code>3</code></td>
   <td>Le {{domxref("Text")}} actuel de l'{{domxref("Element")}} ou {{domxref("Attr")}}.</td>
  </tr>
  <tr>
   <td><code>Node.PROCESSING_INSTRUCTION_NODE</code></td>
   <td><code>7</code></td>
   <td>Une {{domxref("ProcessingInstruction")}} d'un document XML tel que la déclaration <code>&lt;?xml-stylesheet ... ?&gt;</code>.</td>
  </tr>
  <tr>
   <td><code>Node.COMMENT_NODE</code></td>
   <td><code>8</code></td>
   <td>Un noeud {{domxref("Comment")}}.</td>
  </tr>
  <tr>
   <td><code>Node.DOCUMENT_NODE</code></td>
   <td><code>9</code></td>
   <td>Un noeud {{domxref("Document")}}.</td>
  </tr>
  <tr>
   <td><code>Node.DOCUMENT_TYPE_NODE</code></td>
   <td><code>10</code></td>
   <td>Un noeud {{domxref("DocumentType")}} c'est-à-dire <code>&lt;!DOCTYPE html&gt;</code> pour des documents HTML5.</td>
  </tr>
  <tr>
   <td><code>Node.DOCUMENT_FRAGMENT_NODE</code></td>
   <td><code>11</code></td>
   <td>Un noeud {{domxref("DocumentFragment")}}.</td>
  </tr>
 </tbody>
</table>

<h3 id="Constantes_de_type_noeud_dépréciées_deprecated_inline()">Constantes de type noeud dépréciées {{deprecated_inline()}}</h3>

<p>Les constantes suivantes ont été dépréciées et ne doivent plus être utilisées.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <td>Constante</td>
   <td>Valeur</td>
   <td>Description</td>
  </tr>
  <tr>
   <td><code>Node.ATTRIBUTE_NODE</code></td>
   <td>2</td>
   <td>Un {{domxref("Attr", "Attribut")}} d'un {{domxref("Element")}}. Les attributs d'élément n'implémentent plus l'interface {{domxref("Node")}} dans la spécification {{SpecName("DOM4")}}.</td>
  </tr>
  <tr>
   <td><code>Node.CDATA_SECTION_NODE</code></td>
   <td><code>4</code></td>
   <td>Une {{domxref("CDATASection")}}. Supprimée dans la spécification {{SpecName("DOM4")}}.</td>
  </tr>
  <tr>
   <td><code>Node.ENTITY_REFERENCE_NODE</code></td>
   <td>5</td>
   <td>Un noeud référence d'entité XML. Supprimé dans la spécification {{SpecName("DOM4")}}.</td>
  </tr>
  <tr>
   <td><code>Node.ENTITY_NODE</code></td>
   <td>6</td>
   <td>Un noeud <code>&lt;!ENTITY ...&gt;</code> XML. Supprimé dans la spécificatioin {{SpecName("DOM4")}}.</td>
  </tr>
  <tr>
   <td><code>Node.NOTATION_NODE</code></td>
   <td>12</td>
   <td>Un noeud <code>&lt;!NOTATION ...&gt;</code> XML. Supprimé dans la spécification {{SpecName("DOM4")}}.</td>
  </tr>
 </tbody>
</table>

<h2 id="Exemple">Exemples</h2>

<h3 id="Différents_types_de_noeuds">Différents types de noeuds</h3>

<pre class="brush: js">document.nodeType === Node.DOCUMENT_NODE; // true (<em>vrai</em>)
document.doctype.nodeType === Node.DOCUMENT_TYPE_NODE; // true  (<em>vrai</em>)

var fragment = document.createDocumentFragment();
fragment.nodeType === Node.DOCUMENT_FRAGMENT_NODE; // true  (<em>vrai</em>)

<code>var p = document.createElement("p");
p.textContent = "Once upon a time...";</code>

p.nodeType === Node.ELEMENT_NODE; // true  (<em>vrai</em>)
p.firstChild.nodeType === Node.TEXT_NODE; // true  (<em>vrai</em>)
</pre>

<h3 id="Commentaires">Commentaires</h3>

<p>Cet exemple vérifie si le premier noeud dans l'élément du document est un noeud commentaire et si ce n'est pas le cas, affiche un message.</p>

<pre class="brush: js">var node = document.documentElement.firstChild;
if (node.nodeType != Node.COMMENT_NODE)
  console.log("You should comment your code well!");</pre>

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
   <td>{{SpecName('DOM WHATWG', '#dom-node-nodetype', 'Node.nodeType')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>Sont dépréciés les types <code>ATTRIBUTE_NODE, CDATA_SECTION_NODE, ENTITY_REFERENCE_NODE et NOTATION_NODE</code>.</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Core', 'core.html#ID-1950641247', 'Node.nodeType')}}</td>
   <td>{{Spec2('DOM3 Core')}}</td>
   <td>Pas de changement.</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 Core', 'core.html#ID-111237558', 'Node.nodeType')}}</td>
   <td>{{Spec2('DOM2 Core')}}</td>
   <td>Pas de changement.</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM1', 'level-one-core.html#ID-111237558', 'Node.nodeType')}}</td>
   <td>{{Spec2('DOM1')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.Node.nodeType")}}</p>
