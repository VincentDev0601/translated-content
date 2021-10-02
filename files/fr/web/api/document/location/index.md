---
title: Document.location
slug: Web/API/Document/location
tags:
  - API
  - Document
  - HTML DOM
  - Propriété
  - Reference
  - lecture seule
translation_of: Web/API/Document/location
---
<p>La propriété en lecture seule <strong><code>Document.location</code></strong><code> renvoie un objet</code> {{domxref("Location")}}, contenant les informations sur l'URL du document et fournit des moyens pour modifier cette URL ou charger une autre URL.</p>

<p>Bien que <code>Document.location</code> soit un objet  <code>Location</code> en <em>lecture seule</em>, vous pouvez lui assigner un {{domxref("DOMString")}}. Cela signifie que vous pouvez dans la plupart des cas utiliser document.location comme s'il s'agissait d'une chaîne de caractères: <code>document.location = 'http://www.example.com'</code> est un synonyme de <code>document.location.href = 'http://www.example.com'</code>.</p>

<p>Pour récupérer uniquement l'URL en tant que chaîne de caractères, la propriété {{domxref("document.URL")}} peut également être utilisée.</p>

<p>Si le document courant n'est pas un contexte de navigation, la valeur renvoyée est <em>null</em>.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox"><em>locationObj</em> = document.location
document.location = 'http://www.mozilla.org' // équivalent à document.location.href = 'http://www.mozilla.org'
</pre>

<h2 id="Example">Exemple</h2>

<pre class="brush: js">console.log(document.location);
// Affiche un string-like
// "http://www.example.com/juicybits.html" dans la console
</pre>

<h2 id="Spécification">Spécification</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Specification</th>
   <th scope="col">Status</th>
   <th scope="col">Comment</th>
  </tr>
  <tr>
   <td>{{SpecName('HTML WHATWG', "history.html#the-location-interface", "Document.location")}}</td>
   <td>{{Spec2('HTML WHATWG')}}</td>
   <td>Pas de changement avec {{SpecName("HTML5 W3C")}}.</td>
  </tr>
  <tr>
   <td>{{SpecName('HTML5 W3C', "browsers.html#the-location-interface", "Document.location")}}</td>
   <td>{{Spec2('HTML5 W3C')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Document.location")}}</p>

<h2 id="Voir_également">Voir également</h2>

<ul>
 <li>L'interface de la valeur renvoyée, {{domxref("Location")}}.</li>
 <li>Une information similaire mais attachée au contexte de navigation, {{domxref("Window.location")}}</li>
</ul>
