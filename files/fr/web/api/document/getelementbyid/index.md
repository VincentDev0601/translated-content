---
title: document.getElementById
slug: Web/API/Document/getElementById
tags:
  - API
  - DOM
  - Document
  - Elements
  - Identifiant
  - Méthodes
translation_of: Web/API/Document/getElementById
---
<p>{{ ApiRef("DOM") }}</p>

<p>La méthode <code><strong>getElementById()</strong></code> de {{domxref("Document")}} renvoie un objet  {{domxref("Element")}} représentant l'élément dont la propriété  {{domxref("Element.id", "id")}} correspond à la chaîne de caractères spécifiée. Étant donné que les ID d'élément doivent être uniques, s'ils sont spécifiés, ils constituent un moyen utile d'accéder rapidement à un élément spécifique.</p>

<p>Si vous avez besoin d'accéder à un élément qui n'a pas d'ID, vous pouvez utiliser {{domxref("Document.querySelector","querySelector()")}} pour trouver l'élément en utilisant un {{Glossary("CSS selector","sélecteur")}}.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js"><em>var element</em> = document.getElementById(<em>id</em>);
</pre>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>id</code></dt>
 <dd><p>L'ID (<em>identifiant)</em> de l'élément à localiser. Il est une chaîne de caractères sensible à la casse qui est unique ; un seul élément peut avoir un ID donné.</p></dd>
</dl>

<h3 id="Valeur_de_retour">Valeur de retour</h3>

<p>Un objet {{domxref("Element")}} décrivant l'objet élément du DOM correspondant à l'ID spécifié ou <code>null</code> si aucun n'a été trouvé dans le document.</p>

<h2 id="Exemple">Exemple</h2>

<h3 id="Contenu_HTML">Contenu HTML</h3>

<pre class="brush: html">&lt;html&gt;
&lt;head&gt;
  &lt;title&gt;getElementById example&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;p id="para"&gt;Some text here&lt;/p&gt;
  &lt;button onclick="changeColor('blue');"&gt;blue&lt;/button&gt;
  &lt;button onclick="changeColor('red');"&gt;red&lt;/button&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

<h3 id="Contenu_JavaScript">Contenu JavaScript</h3>

<pre class="brush: js">function changeColor(newColor) {
  var elem = document.getElementById('para');
  elem.style.color = newColor;
}</pre>

<h3 id="Notes">Résultat</h3>

<p>{{ EmbedLiveSample('Example1', 250, 100) }}</p>

<h2 id="Notes">Notes d'utilisation</h2>

<p>L'écriture de la lettre capitale de « Id » dans le nom de cette méthode <em>doit</em> être respectée pour que le code fonctionne ; <code>getElementByID()</code> n'est pas valide et ne fonctionnera <em>pas</em>, même si elle semble naturelle.</p>

<p>Contrairement à d'autres méthodes de recherche d'éléments, comme  {{domxref("Document.querySelector()")}} et {{domxref("Document.querySelectorAll()")}}, <code>getElementById</code> est uniquement disponible comme méthode de l'objet global <code>document</code> et <em>n'est pas</em> disponible sur tous les objets du DOM. Parce que les valeurs d'ID doivent être uniques dans l'ensemble du document, il n'y pas besoin d'avoir une version "locale" de la fonction.</p>

<h2 id="Exemple_2">Exemple</h2>

<pre class="brush: html">&lt;!doctype html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;title&gt;Document&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id="parent-id"&gt;
        &lt;p&gt;hello word1&lt;/p&gt;
        &lt;p id="test1"&gt;hello word2&lt;/p&gt;
        &lt;p&gt;hello word3&lt;/p&gt;
        &lt;p&gt;hello word4&lt;/p&gt;
    &lt;/div&gt;
    &lt;script&gt;
        var parentDOM = document.getElementById('parent-id');
        var test1=parentDOM.getElementById('test1');
        //erreur de lancement 
        //TypeError inattendu : parentDOM.getElementById n'est pas une fonction 
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

<p>S'il n'y a pas d'élément avec l'<code>id</code> fourni, cette fonction retourne <code>null</code>. A noter que le paramètre <code>id</code> est sensible à la casse, ainsi<code> document.getElementById("Main")</code> retournera <code>null</code> au lieu de l'élément <code>&lt;div id="main"&gt;</code> étant donné que "M" et "m" sont différents pour cette méthode.</p>

<p><strong>Les éléments absents du document</strong> ne sont pas cherchés par <code>getElementById()</code>. Quand vous créez un élément et y assignez un ID, vous devez insérer l'élément dans l'arbre du document avec {{domxref("Node.insertBefore()")}} ou une méthode similaire avant de pouvoir y accéder avec <code>getElementById()</code> :</p>

<pre class="brush: js">var element = document.createElement('div');
element.id = 'testqq';
var el = document.getElementById('testqq'); // el vaudra null !</pre>

<p><strong>Les documents non-HTML.</strong> Les implémentations du DOM doivent avoir une information qui précise quels attributs sont de type ID. Un attribut portant le nom « id » n'est pas de type ID tant qu'il n'a pas été explicitement défini ainsi (dans la DTD du document). L'attribut <code>id</code> est défini comme étant de type ID dans les langages courants comme <a href="/fr/XHTML">XHTML</a> ou <a href="/fr/XUL">XUL</a>. Les implémentations ne sachant pas déterminer si les attributs sont de type ID ou non sont supposées renvoyer <code>null</code>.</p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('DOM1','level-one-html.html#method-getElementById','getElementById')}}</td>
   <td>{{Spec2('DOM1')}}</td>
   <td>Définition initiale de l'interface</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 Core','core.html#ID-getElBId','getElementById')}}</td>
   <td>{{Spec2('DOM2 Core')}}</td>
   <td>Remplace DOM 1</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Core','core.html#ID-getElBId','getElementById')}}</td>
   <td>{{Spec2('DOM3 Core')}}</td>
   <td>Remplace DOM 2</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM WHATWG','#interface-nonelementparentnode','getElementById')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>Remplacera DOM 3</td>
  </tr>
 </tbody>
</table>

<p>Traduction en français (non normative) : <a href="http://www.yoyodesign.org/doc/w3c/dom2/core/core.html#ID-getElBId">getElementById</a></p>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Document.getElementById")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{domxref("Document")}} référence pour d'autres méthodes et propriétés que vous pouvez utiliser pour obtenir la référence vers des éléments du document.</li>
 <li>{{domxref("Document.querySelector()")}} pour utiliser des sélecteurs avec des requêtes comme <code>'div.myclass'</code></li>
 <li><a href="/fr/xml/xml:id">xml:id</a> dispose d'une méthode utilitaire permettant à getElementById d'obtenir les valeur 'xml:id' dans les documents XML (comme ceux qui pourraient être renvoyés par des appels Ajax).</li>
</ul>
