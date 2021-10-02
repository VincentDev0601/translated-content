---
title: element.tagName
slug: Web/API/Element/tagName
tags:
  - API
  - DOM
  - Element
  - Nom
  - Propriétés
translation_of: Web/API/Element/tagName
---
<p>{{ApiRef("DOM")}}</p>

<p>Renvoie le nom de l'étiquette de l'élément sur lequel elle est appelée. Si l'élément est une {{HTMLElement("img")}}, sa propriété <code>tagName</code> est <code>"IMG"</code> (pour les documents HTML, elle peut être différente pour les documents XML et XHTML).</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><em>elementName</em> = element.tagName;
</pre>

<h3 id="Valeur">Valeur</h3>

<p>Une chaîne indiquant le nom de l'étiquette de l'élément. Cette chaîne comporte des majuscules selon le type de document :</p>

<ul>
 <li>Pour l'arbre DOM qui représente un document HTML, le nom renvoyé est toujours en forme majuscule canonique. Par exemple, <code>tagName</code> appelé sur un élément {{HTMLElement("div")}} renvoie <code>"DIV"</code>.</li>
 <li>Les noms des éléments dans un arbre DOM XML, sont retournés dans la même casse que celle utilisée dans le fichier XML d'origine. Si un document XML inclut une étiquette <code>"&lt;SomeTag&gt;"</code>, alors la valeur de la propriété <code>tagName</code> est <code>"SomeTag"</code>.</li>
 <li>Pour les objets {{domxref("Element")}} , la valeur de l'étiquette de nom est la même que la valeur de la propriété {{domxref("Node.nodeName", "nodeName")}} héritée de {{domxref("Node")}}.</li>
</ul>

<h2 id="Exemple">Exemple</h2>

<h3 id="Contenu_HTML">Contenu HTML</h3>

<pre class="eval">&lt;span id="naissance"&gt;Lorsque je suis né…&lt;/span&gt;
</pre>

<h3 id="Contenu_JavaScript">Contenu JavaScript</h3>

<pre class="brush: js">var span = document.getElementById("naissance");
console.log(span.tagName);</pre>

<p>En XHTML (ou tout autre format XML), la casse d'origine sera conservée, de sorte que <code>"span"</code> sera affiché dans le cas où le nom de l'étiquette d'origine a été créé en minuscules. En HTML, <code>"SPAN"</code> serait affiché à la place quelle que soit la casse utilisée lors de la création du document original.</p>

<h2 id="Sp.C3.A9cification">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th>Spécification</th>
   <th>Statut</th>
   <th>Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName("DOM3 Core", "core.html#ID-104682815", "Element.tagName")}}</td>
   <td>{{Spec2("DOM3 Core")}}</td>
   <td>Pas de changement</td>
  </tr>
  <tr>
   <td>{{SpecName("DOM2 Core", "core.html#ID-104682815", "Element.tagName")}}</td>
   <td>{{Spec2("DOM2 Core")}}</td>
   <td>Définition initiale</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Element.tagName")}}</p>
