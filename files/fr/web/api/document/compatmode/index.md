---
title: document.compatMode
slug: Web/API/Document/compatMode
tags:
  - API
  - DOM
  - Propriété
  - Reference
translation_of: Web/API/Document/compatMode
---
<p>{{ ApiRef("DOM") }}</p>

<p>Indique si le document est affiché en mode dégradé (<a href="/fr/docs/Mode_quirks_de_Mozilla">Quirks mode</a>) ou dans le respect des standards.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="eval"><em>mode</em> = document.compatMode
</pre>

<h2 id="Valeurs">Valeurs</h2>

<ul>
 <li><code>"BackCompat"</code> si le document est a ffiché en mode   "quirks" ; </li>
</ul>

<dl>
 <dt>mode</dt>
 <dd>est une  valeur énumérée qui peut être :</dd>
</dl>

<ul>
 <li><code>"CSS1Compat"</code> si le document est affiché en mode "no-quirks" (aussi connu sous le nom de mode "standard") ou "limited-quirks" (mo de "proche du standard").</li>
</ul>

<dl>
</dl>

<div class="note">
<p><strong>Note :</strong> tous ces modes sont maintenant définis dans les normes, de sorte que les anciens «standards» et «presque standards» sont absurdes et ne sont plus utilisés dans les normes.</p>
</div>

<h2 id="Example">Exemple</h2>

<pre class="eval">if (document.compatMode == "BackCompat") {
  // en mode Quirks
}
</pre>

<h2 id="Specification">Spécifications</h2>

<ul>
 <li><a href="http://dom.spec.whatwg.org/#dom-document-compatmode">DOM: Document.compatMode</a></li>
</ul>
