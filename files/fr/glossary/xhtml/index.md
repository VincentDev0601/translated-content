---
title: XHTML
slug: Glossary/XHTML
tags:
  - Encodage
  - Glossaire
  - XHTML
translation_of: Glossary/XHTML
original_slug: XHTML
---
<p><a href="/fr/docs/Web/HTML">HTML</a> peut voyager sur le réseau vers un navigateur soit en syntaxe HTML soit en syntaxe XML appelée XHTML.</p>

<h2 id="HTML5_et_HTMLXHTML">HTML5 et HTML/XHTML</h2>

<p>La norme <a href="/fr/docs/Web/Guide/HTML/HTML5">HTML5</a> définit ces deux syntaxes. Le type MIME (envoyé dans l'en-tête HTTP <code>Content-Type</code>) indique le choix de la syntaxe : pour XHTML, le type MIME sera <code>application/xhtml+xml</code>, sinon <code>text/html</code>.</p>

<p>Cet exemple montre un document HTML et un document XHTML inclus dans l'en-tête HTTP :</p>

<h3 id="Document_HTML">Document HTML</h3>

<pre class="brush: html">HTTP/1.1 200 OK
Content-Type: text/html

&lt;!DOCTYPE html&gt;
&lt;html lang=en&gt;
  &lt;head&gt;
    &lt;meta charset=utf-8&gt;
    &lt;title&gt;HTML&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;p&gt;Je suis un document HTML&lt;/p&gt;
  &lt;/body&gt;
&lt;/html&gt;</pre>

<h3 id="Document_XHTML">Document XHTML</h3>

<pre class="brush: xml">HTTP/1.1 200 OK
Content-Type: application/xhtml+xml

&lt;html xml:lang="en" xmlns="<code>http://www.w3.org/1999/xhtml</code>"&gt;
  &lt;head&gt;
    &lt;title&gt;XHTML&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;p&gt;Je suis un document XHTML&lt;/p&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>

<h2 id="Type_MIME_contre_DOCTYPE">Type MIME contre DOCTYPE</h2>

<p>Avant HTML5, les deux spécifications distinctes définissaient les deux syntaxes ( <a href="http://www.w3.org/TR/html4/">HTML 4.01</a>  et  <a href="http://www.w3.org/TR/xhtml1/">XHTML 1.0</a> ). Selon la norme XHTML1, vous pouvez utiliser XHTML en déclarant un DOCTYPE spécial. Cependant, aucun navigateur n'a jamais implémenté cela, et la norme HTML5 a inversé la décision. <strong>Si votre page est envoyée en tant que <code>texte/html</code>, vous n'utilisez pas XHTML</strong>.</p>

<p>Au lieu de cela, le type MIME correct doit être présent dans l'en-tête HTTP <code>Content-Type</code>. Si vous ne mettez que le type MIME dans une balise meta HTML comme = <code>&lt;meta http-equiv...&gt;</code>, il sera ignoré et traité comme du <code>texte/html</code>.</p>

<p>Si vous diffusez vos pages en tant que <code>texte/html</code> et que vous croyez que vous écrivez XHTML, vous pouvez rencontrer plusieurs problèmes, comme décrit dans ces articles :</p>

<ul>
 <li><a href="http://www.spartanicus.utvinternet.ie/no-xhtml.htm">No to XHTML</a> un excellent article de Spartanicus</li>
 <li><a href="http://www.webdevout.net/articles/beware-of-xhtml">Beware of XHTML</a> par David Hammond</li>
 <li><a href="http://www.hixie.ch/advocacy/xhtml">Sending XHTML as text/html Considered Harmful</a> par Ian Hickson</li>
 <li><a href="http://www.xml.com/pub/a/2003/03/19/dive-into-xml.html">XHTML's Dirty Little Secret</a> par Mark Pilgrim</li>
 <li><a href="http://hsivonen.iki.fi/xhtml-the-point/">XHTML - What's the Point?</a> par Henri Sivonen</li>
 <li><a href="http://lachy.id.au/log/2005/12/xhtml-beginners">XHTML is not for Beginners</a> par Lachlan Hunt</li>
</ul>

<h2 id="Prise_en_charge">Prise en charge</h2>

<p>La plupart des navigateurs prennent actuellement en charge XHTML, y compris Firefox, Chrome, Safari, Opera et Internet Explorer (depuis IE 9). (Les navigateurs Internet Explorer 8 et plus anciens affichent à la place une boîte de dialogue de téléchargement pour les types de fichiers inconnus lorsqu'ils voient un document XHTML avec le type MIME XHTML correct.)</p>

<p>Sachez également que de nombreuses bibliothèques et outils de développement {{Glossary("JavaScript")}} populaires ont un support limité ou inexistant pour XHTML.</p>

<h2 id="Différences_avec_HTML">Différences avec HTML</h2>

<p>Voir <a href="/fr/docs/Archive/Web/Properly_Using_CSS_and_JavaScript_in_XHTML_Documents_">Utilisation correcte de CSS et JavaScript dans les documents XHTML</a> pour une liste partielle des différences entre HTML et XHTML.</p>

<h2 id="Outils">Outils</h2>

<ul>
 <li><a href="fr/Outils_d'%c3%a9dition_respectueux_des_standards">Outils de création conformes aux normes</a></li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/HTML">HTML</a></li>
 <li><a href="/fr/docs/Namespaces">Namespaces</a></li>
</ul>
