---
title: Document.designMode
slug: Web/API/Document/designMode
translation_of: Web/API/Document/designMode
---
<div>{{ ApiRef() }}</div>

<p>document.designMode contrôle si l'ensemble du document est modifiable. Les valeurs valides sont "on" et "off". Conformément à la spécification, cette propriété est par défaut sur "off". Firefox suit cette norme. Les versions antérieures de Chrome et IE ont par défaut la valeur "<code>inherit</code>". Pour les versions entre IE6-10, la valeur est en majuscule.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var mode = document.designMode;
document.designMode = "on";
document.designMode = "off";</pre>

<h2 id="Example">Exemple</h2>

<p>Rendre un document {{HTMLElement("iframe")}} éditable</p>

<pre>iframe_node.contentDocument.designMode = "on";
</pre>

<h2 id="Specifications">Spécifications</h2>

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
      <td>{{SpecName('HTML WHATWG', '#making-entire-documents-editable:-the-designmode-idl-attribute', 'designMode')}}</td>
      <td>{{Spec2('HTML WHATWG')}}</td>
      <td>Définition initiale.</td>
    </tr>
  </tbody>
</table>

<h2 id="Browser_compatibility">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Document.designMode")}}</p>

<h2 id="See_also">Voir aussi</h2>

<ul>
  <li><a href="/fr/docs/Web/Guide/HTML/Editable_content/Rich-Text_Editing_in_Mozilla">Rich-Text Editing in Mozilla</a></li>
  <li>{{domxref("HTMLElement.contentEditable")}}</li>
</ul>
