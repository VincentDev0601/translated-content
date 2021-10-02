---
title: document.getElementsByName()
slug: Web/API/Document/getElementsByName
tags:
  - API
  - DOM
  - Document
  - HTML
  - Méthodes
translation_of: Web/API/Document/getElementsByName
---
<p>{{ ApiRef("DOM") }}</p>

<p>Renvoie une liste des éléments portant un {{domxref("element.name","name")}} donné dans le document (X)HTML.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="eval"><em>elements</em> = document.getElementsByName(<em>name</em>)
</pre>

<ul>
 <li><code>elements</code> est une collection de {{domxref("NodeList")}}</li>
 <li><code>name</code> est la valeur de l'attribut <code>name</code> des éléments.</li>
</ul>

<h2 id="Exemple">Exemple</h2>

<pre class="brush:html">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
 ...
&lt;/head&gt;

&lt;body&gt;
&lt;form name="up"&gt;&lt;input type="text"&gt;&lt;/form&gt;
&lt;div name="down"&gt;&lt;input type="text"&gt;&lt;/div&gt;

&lt;script&gt;
var up_forms = document.getElementsByName("up");
console.log(up_forms[0].tagName); // retourne "FORM"
&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

<h2 id="Notes">Notes</h2>

<p>L'attribut <code><a href="/fr/docs/Web/API/Element/name">name</a></code> est uniquement applicable aux documents (X) HTML. La méthode renvoie une collection  {{domxref("NodeList")}}  en cours qui contient tous les éléments avec une valeur donnée pour l'attribut name, tels que  {{htmlelement("meta")}}  ou  {{htmlelement("object")}}  ou même si le nom est placé sur des éléments qui ne supportent pas du tout un attribut <code>name</code>.</p>

<p>La méthode <strong>getElementsByName</strong> fonctionne différemment dans différents navigateurs. Dans IE &lt;10, la méthode getElementsByName () renvoie également les éléments qui ont un attribut id avec la valeur spécifiée. Vous devriez donc faire attention à ne pas utiliser la même chaîne pour le nom et l'identifiant.</p>

<h2 id="Sp.C3.A9cification">Spécifications</h2>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-HTML/html.html#ID-71555259">DOM Level 2 HTML : getElementsByName</a> — <a href="http://www.yoyodesign.org/doc/w3c/dom2-html/html.html#ID-71555259">traduction en français</a> (non normative)</li>
 <li><a href="http://www.whatwg.org/html/#dom-document-getelementsbyname">HTML5 : getElementsByName</a></li>
</ul>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('HTML WHATWG', '#dom-document-getelementsbyname', "Document.getElementsByName()")}}</td>
   <td>{{ Spec2('HTML WHATWG') }}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName("DOM2 HTML", "html.html#ID-71555259", "Document.getElementsByName()")}}</td>
   <td>{{Spec2("DOM2 HTML")}}</td>
   <td>Définition initiale</td>
  </tr>
 </tbody>
</table>

<h2 id="See_also">Voir aussi</h2>

<ul>
 <li>{{domxref("document.getElementById()")}} pour retourner une référence à un élément par son ID</li>
 <li>{{domxref("document.getElementsByTagName()")}} pour renvoyer les références sur les éléments avec la balise de nom donnée</li>
 <li>{{domxref("document.querySelector()")}} pour des sélecteurs par des requêtes comme <code>'div.myclass'</code></li>
</ul>

<p> </p>
