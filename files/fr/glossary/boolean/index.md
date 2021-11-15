---
title: Booléen
slug: Glossary/Boolean
tags:
  - Booléen
  - Glossaire
  - JavaScript
  - Langages de programmation
  - Types de données
translation_of: Glossary/Boolean
original_slug: Glossaire/Boolean
---
<p>En informatique, un <strong>booléen</strong> est un type de données logique qui ne peut prendre que deux valeurs : <code>true</code><strong> </strong><em>(vrai)</em><strong> </strong>ou <code>false</code><em> (faux)</em>. Par exemple, en JavaScript, les conditions booléennes sont souvent ouvertes pour décider quelle section de code doit être exécutée (comme dans l'<a href="/fr/docs/Web/JavaScript/Reference/Instructions/if...else">instruction If</a>) ou répétée (comme pour une <a href="/fr/docs/Web/JavaScript/Reference/Instructions/for">boucle For</a>).</p>

<pre class="brush: js">/* JavaScript instruction if */
if (boolean conditional) {
   // code à exécuter si la condition est true (vrai)
}

if (boolean conditional) {
  console.log("boolean conditional resolved to true");
} else {
  console.log("boolean conditional resolved to false");
}


/* JavaScript boucle for */
for (control variable; boolean conditional; counter) {
  // code à exécuter répétitivement si la condition est vraie
}

for (var i=0; i &lt; 4; i++) {
  console.log("I print only when the boolean conditional is true");
}</pre>

<h2 id="Pour_Approfondir">Pour Approfondir</h2>

<h3 id="Culture_générale">Culture générale</h3>

<ul>
 <li><a href="http://fr.wikipedia.org/wiki/Bool%C3%A9en">Booléen</a> sur Wikipedia</li>
</ul>

<h3 id="Informations_techniques">Informations techniques</h3>

<ul>
 <li>L'objet JavaScript global : {{jsxref("Boolean")}}</li>
 <li><a href="/fr/docs/Web/JavaScript/Structures_de_donn%C3%A9es">Structures de données JavaScript</a> sur MDN</li>
</ul>
