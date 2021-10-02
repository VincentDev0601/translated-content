---
title: element.childNodes
slug: Web/API/Node/childNodes
tags:
  - API
  - DOM
  - Enfants
  - Noeuds
  - Propriétés
translation_of: Web/API/Node/childNodes
---
<p>{{APIRef("DOM")}}</p>

<p>La propriété en lecture seule  <code><strong>Node.childNodes</strong></code> renvoie une {{domxref("NodeList")}} (<em>liste de noeuds</em>) de {{domxref("Node","noeuds")}} enfants de l'élément donné avec le premier noeud enfant affecté à l'index 0.</p>

<h2 id="Syntaxe_et_valeurs">Syntaxe</h2>

<pre class="eval"><a href="/fr/Référence_de_JavaScript_1.5_Core/Instructions/var">var</a> <var>collNoeuds</var> = elementDeReference.<a href="/fr/DOM/element.childNodes">childNodes</a>;
</pre>

<h2 id="Exemples">Exemples</h2>

<h3 id="Utilisation_simple">Utilisation simple</h3>

<pre class="brush:js">// parg est une référence d'objet pour un élément &lt;p&gt;

// D'abord vérifier que l'élément a des noeuds enfants 
if (parg.hasChildNodes()) {
  var children = parg.childNodes;

  for (var i = 0; i &lt; children.length; i++) {
    // faire quelque chose avec chaque enfant[i]
    // NOTE: La liste est en ligne, l'ajout ou la suppression des enfants changera la liste
  }
}</pre>

<h3 id="Supprimer_tous_les_enfants_d'un_nom">Supprimer tous les enfants d'un nom</h3>

<pre>// Voici une manière de supprimer tous les enfants d'un nœud
// (boite est une référence à un élément ayant des enfants)
<a href="/fr/Référence_de_JavaScript_1.5_Core/Instructions/while">while</a>( boite.<a href="/fr/DOM/element.firstChild">firstChild</a>) {
    // La liste n'est pas une copie, elle sera donc réindexée à chaque appel
    boite.<a href="/fr/DOM/element.removeChild">removeChild</a>( boite.<a href="/fr/DOM/element.firstChild">firstChild</a>);
}
</pre>

<h2 id="Notes">Notes</h2>

<p>Les éléments de la collection de noeuds sont des objets et non des chaînes de caractères. Pour en obtenir les données, vous devez utiliser leurs propriétés (par exemple <code>elementNodeReference.childNodes[1].nodeName</code> pour obtenir son nom, etc.)</p>

<p>L'objet <a href="/fr/DOM/document"><code>document</code></a> lui-même a deux enfants : la déclaration <a href="/fr/DOM/document.doctype">Doctype</a> et l'élément racine, généralement appelés  <code>documentElement</code> . (Dans les documents (X)HTML il s'agit d'éléments  <a href="/fr/HTML/Element/html"><code>HTML</code></a>).</p>

<p><code>childNodes</code>  inclut tous les noeuds enfants, y compris les noeuds qui ne sont pas des éléments comme les noeuds texte et commentaire. Pour obtenir une collection des seuls éléments, utilisez {{domxref("ParentNode.children")}} à la place.</p>

<p> </p>

<h2 id="Spécification">Spécification</h2>

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
   <td>{{SpecName('DOM WHATWG', '#dom-node-childnodes', 'Node.childNodes')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>Pas de changement</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Core', 'core.html#ID-1451460987', 'Node.childNodes')}}</td>
   <td>{{Spec2('DOM3 Core')}}</td>
   <td>Pas de changement</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 Core', 'core.html#ID-1451460987', 'Node.childNodes')}}</td>
   <td>{{Spec2('DOM2 Core')}}</td>
   <td>Pas de changement</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM1', 'level-one-core.html#ID-1451460987', 'Node.childNodes')}}</td>
   <td>{{Spec2('DOM1')}}</td>
   <td>Définition initiale</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Node.childNodes")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{domxref("Node.firstChild")}}</li>
 <li>{{domxref("Node.lastChild")}}</li>
 <li>{{domxref("Node.nextSibling")}}</li>
 <li>{{domxref("Node.previousSibling")}}</li>
 <li>{{domxref("ParentNode.children")}}</li>
</ul>
