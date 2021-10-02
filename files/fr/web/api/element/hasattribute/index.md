---
title: element.hasAttribute
slug: Web/API/Element/hasAttribute
tags:
  - API
  - DOM
  - Element
  - Méthode
  - Reference
translation_of: Web/API/Element/hasAttribute
---
<p>{{APIRef("DOM")}}</p>

<p>La méthode  <strong><code>Element.hasAttribute()</code></strong>  renvoie une <strong>valeur booléenne</strong> indiquant si l'élément courant possède l'attribut spécifié ou non.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><var>var <em>result</em></var> = <em><var>element</var></em>.hasAttribute(<em><var>name</var></em>);
</pre>

<dl>
 <dt><code>result</code></dt>
 <dd>récupère la valeur de retour <code>true</code> ou <code>false</code>.</dd>
 <dt><code>name</code></dt>
 <dd>est une chaine de caractères représentant le nom de l'attribut.</dd>
</dl>

<h2 id="Exemple">Exemple</h2>

<pre class="brush:js">var foo = document.getElementById("foo");
if (foo.hasAttribute("bar")) {
    // faire quelque chose
}</pre>

<h2 id="Notes">Polyfill</h2>

<pre class="brush:js">;(function(prototype) {
    prototype.hasAttribute = prototype.hasAttribute || function(name) {
        return !!(this.attributes[name] &amp;&amp;
                  this.attributes[name].specified);
    }
})(Element.prototype);</pre>

<h2 id="Notes">Notes</h2>

<p>{{DOMAttributeMethods}}</p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('DOM WHATWG', '#dom-element-hasattribute', 'Element.hasAttribute()')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>Dans {{SpecName('DOM3 Core')}}, déplacé de {{domxref("Node")}} à {{domxref("Element")}}</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Core', 'core.html#ID-ElHasAttr', 'Element.hasAttribute()')}}</td>
   <td>{{Spec2('DOM3 Core')}}</td>
   <td>Pas de changement par rapport à {{SpecName('DOM2 Core')}}</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 Core', 'core.html#ID-ElHasAttr', 'Element.hasAttribute()')}}</td>
   <td>{{Spec2('DOM2 Core')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Browser_compatibility">Browser compatibility</h2>

<p>{{Compat("api.Element.hasAttribute")}}</p>
