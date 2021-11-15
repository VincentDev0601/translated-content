---
title: Truthy
slug: Glossary/Truthy
tags:
  - Glossaire
  - JavaScript
  - Programmation
translation_of: Glossary/Truthy
original_slug: Glossaire/Truthy
---
<p>En {{Glossary("JavaScript")}}, une valeur <code>truthy</code> est une valeur qui est considérée comme vraie quand elle est évaluée dans un contexte {{Glossary("Boolean","booléen")}} . Toutes les valeurs sont <code>truthy</code> sauf si elles sont definies comme {{Glossary("Falsy","falsy")}} (c'est-à-dire, sauf pour <code>false</code>, 0, "", <code>null</code>, <code>undefined</code>, et <code>NaN</code>).</p>

<p><br>
 {{Glossary("JavaScript")}} utilise la {{Glossary("Type_Conversion", "contrainte")}} de type dans un contexte booléen.</p>

<p><br>
 Exemples de valeurs truthy en JavaScript (qui seront considérées comme vraies, ce qui exécutera le bloc if):</p>

<pre class="brush: js">if (true)
if ({})
if ([])
if (42)
if ("foo")
if (new Date())
if (-42)
if (3.14)
if (-3.14)
if (Infinity)
if (-Infinity)</pre>

<h2 id="Voir_aussi">Voir aussi </h2>

<ul>
 <li>{{Glossary("Falsy")}}</li>
 <li>{{Glossary("Type_Conversion", "Contrainte")}}</li>
 <li>{{Glossary("Boolean","Booléen")}}</li>
</ul>
