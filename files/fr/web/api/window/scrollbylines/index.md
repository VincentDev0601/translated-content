---
title: Window.scrollByLines()
slug: Web/API/Window/scrollByLines
tags:
  - API
  - DOM
  - DOM_0
  - Méthode
  - Non-standard
  - Window
translation_of: Web/API/Window/scrollByLines
---
<div>{{ ApiRef() }}</div>

<p>{{Non-standard_header}}</p>

<p>Fait défiler le document du nombre de lignes spécifié.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox">window.scrollByLines(<var>lignes</var>)
</pre>

<h2 id="Parameters">Paramètres</h2>

<ul>
 <li><code>lignes</code> est le nombre de lignes à faire défiler.</li>
 <li><code>lignes</code> peut être un entier positif ou négatif.</li>
</ul>

<h2 id="Example">Exemples</h2>

<pre class="brush:html">&lt;!-- Faire défiler le document de 5 lignes vers le bas. --&gt;
&lt;button onclick="scrollByLines(5);"&gt;5 lignes vers le bas&lt;/button&gt;
</pre>

<pre class="brush:html">&lt;!-- Faire défiler le document de 5 lignes vers le haut. --&gt;
&lt;button onclick="scrollByLines(-5);"&gt;5 lignes vers le haut&lt;/button&gt;
</pre>

<h2 id="Specification">Spécification</h2>

<p>Ne fait partie d'aucune spécification.</p>

<h2 id="See_also">See also</h2>

<ul>
 <li>{{domxref("window.scrollBy")}}, {{domxref("window.scrollByPages")}}</li>
</ul>
