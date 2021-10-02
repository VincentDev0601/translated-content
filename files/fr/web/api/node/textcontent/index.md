---
title: element.textContent
slug: Web/API/Node/textContent
tags:
  - API
  - DOM
  - Noeuds
  - Propriétés
translation_of: Web/API/Node/textContent
---
<p>{{APIRef("DOM")}}</p>

<p>La propriété <code><strong>Node.textContent</strong></code>  représente le contenu textuel d'un nœud et de ses descendants.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox">var <em>text</em> = element.textContent;
element.textContent = "ceci est un simple exemple de texte";
</pre>

<h2 id="Notes">Description</h2>

<ul>
 <li><code>textContent</code> renvoie <code>null</code> si l'élément est un <a href="/fr/docs/Web/API/document">document</a>, un type de document (doctype) ou une notation. Pour saisir toutes les données textuelles et CDATA pour l'ensemble du document, on peut utiliser <code> <a href="/fr/docs/Web/API/document/documentElement">document.documentElement</a>.textContent</code> .</li>
 <li>Si le nœud est une section CDATA, un commentaire, une instruction de traitement ou un nœud texte, <code>textContent</code> renvoie le texte à l'intérieur du nœud (la valeur <a href="/fr/docs/Web/API/Node/nodeValue">nodeValue</a>).</li>
 <li>Pour les autres types de nœuds, <code>textContent</code> renvoie la concaténation des valeurs de propriété <code>textContent</code> de chaque nœud enfant, à l'exception des commentaires et nœuds d'instructions de traitement. Si le nœud n'a pas d'enfants, il s'agira d'une chaîne vide.</li>
 <li>En définissant cette propriété sur un nœud, on enlève tous ses enfants et ceux-ci sont remplacés par un seul nœud texte avec la valeur donnée.</li>
</ul>

<h3 id="Différences_avec_innerText">Différences avec <code>innerText</code></h3>

<p>Internet Explorer a introduit une propriété {{domxref("node.innerText")}}. L'intention est similaire mais comporte les différences suivantes :</p>

<ul>
 <li><code>textContent</code> récupère le contenu de tous les éléments, y compris {{HTMLElement("script")}} et {{HTMLElement("style")}}, ce qui n'est pas le cas de <code>innerText</code>.</li>
 <li><code>innerText</code> prend en compte le style de l'élément et ne retournera rien pour les éléments cachés. Aussi, il déclenchera un reflow à l'inverse de <code>textContent</code>.</li>
 <li>Comme <code>innerText</code> reconnaît le style CSS, il déclenchera une refusion (<em>reflow</em>), alors que <code>textContent</code> ne le fera pas.</li>
 <li>Contrairement à <code>textContent</code>, la modification <code>innerText</code> dans Internet Explorer (jusqu'à la version 11 incluse), non seulement supprime les nœuds enfants de l'élément, mais détruit aussi définitivement tout nœud de texte descendant (il est donc impossible d'insérer à nouveau des nœuds dans un autre élément ou dans le même élément) .</li>
</ul>

<h3 id="Différences_avec_innerHTML">Différences avec <code>innerHTML</code></h3>

<p>{{domxref("Element.innerHTML")}} renvoie le HTML comme son nom l'indique. Souvent, pour récupérer ou écrire du texte dans un élément, les utilisateurs utilisent <code>innerHTML</code>. Cependant, <code>textContent</code> a souvent de meilleures performances car le texte n'est pas analysé en HTML. De plus, l'utilisation de <code>textContent</code> peut empêcher les attaques XSS.</p>

<h2 id="Exemple">Exemple</h2>

<pre class="eval">// Étant donné le fragment de HTML suivant :
//   &lt;div id="divA"&gt;Ceci est un &lt;span&gt;exemple de&lt;/span&gt; texte&lt;/div&gt;

// On obtient le contenu textuel :
var text = document.getElementById("divA").textContent;
// |text| vaut "Ceci est un exemple de texte".

// On définit le contenu textuel :
document.getElementById("divA").textContent = "Ceci est un exemple de texte";
// Le HTML pour divA est à présent &lt;div id="divA"&gt;Ceci est un exemple de texte&lt;/div&gt;
</pre>

<h2 id="Polyfill_pour_IE8">Polyfill pour IE8</h2>

<pre class="brush: js">// Source: Eli Grey @ http://eligrey.com/blog/post/textcontent-in-ie8
if (Object.defineProperty
  &amp;&amp; Object.getOwnPropertyDescriptor
  &amp;&amp; Object.getOwnPropertyDescriptor(Element.prototype, "textContent")
  &amp;&amp; !Object.getOwnPropertyDescriptor(Element.prototype, "textContent").get) {
  (function() {
    var innerText = Object.getOwnPropertyDescriptor(Element.prototype, "innerText");
    Object.defineProperty(Element.prototype, "textContent",
     // Passing innerText or innerText.get directly does not work,
     // wrapper function is required.
     {
       get: function() {
         return innerText.get.call(this);
       },
       set: function(s) {
         return innerText.set.call(this, s);
       }
     }
   );
  })();
}</pre>

<ul>
</ul>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.Node.textContent")}}</p>

<h2 id="Sp.C3.A9cification">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('DOM WHATWG','#dom-node-textcontent','Node.textContent')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>Pas de changement de DOM4</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM4','#dom-node-textcontent','Node.textContent')}}</td>
   <td>{{Spec2('DOM4')}}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Core','core.html#Node3-textContent','Node.textContent')}}</td>
   <td>{{Spec2('DOM3 Core')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="http://perfectionkills.com/the-poor-misunderstood-innerText/">Plus sur les différences entre <code>innerText</code> et <code>textContent</code></a> (blog post en)</li>
</ul>

<p> </p>
