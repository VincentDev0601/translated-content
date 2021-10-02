---
title: Console.group()
slug: Web/API/Console/group
tags:
  - API
  - DOM
  - Développement
  - Méthodes
  - Web
  - console
  - débogage
translation_of: Web/API/Console/group
---
<div>{{APIRef("Console API")}}</div>

<p>Création d'un nouveau groupe en ligne dans la <a href="/en-US/docs/Tools/Web_Console">console Web</a>. Cela indente les messages de console suivants par un niveau supplémentaire, jusqu'à ce que {{domxref("console.groupEnd()")}} soit appelé.</p>

<p>{{AvailableInWorkers}}</p>

<h2 id="Syntax">Syntax</h2>

<pre class="syntaxbox">console.group();
</pre>

<h2 id="Paramètres">Paramètres</h2>

<dl>
 <dt><code>label</code></dt>
 <dd>donne une étiquette au groupe. Facultatif. (Chrome 59 testé). Ne fonctionne pas avec<code> </code> <code>console.groupEnd()</code>.</dd>
</dl>

<p>{{h3_gecko_minversion("Using groups in the console", "9.0")}}</p>

<p>Vous pouvez utiliser des groupes imbriqués pour organiser votre sortie en associant visuellement les messages correspondants. Pour créer un nouveau bloc imbriqué, appelez <code>console.group ()</code>. La méthode <code>console.groupCollapsed ()</code> est similaire, mais le nouveau bloc est réduit et nécessite de cliquer sur un bouton de divulgation pour le lire.</p>

<div class="note">
<p><strong>Note :</strong> De Gecko 9 jusqu'à Gecko 51, la méthode <code>groupCollapsed()</code> n'était pas identique à <code>group()</code>. Les groupes réduits sont entièrement pris en charge depuis Gecko 52. Voir {{bug("1088360")}}.</p>
</div>

<p>Pour sortir du groupe courant, appeler <code>console.groupEnd()</code>. Par exemple, étant donné ce code :</p>

<pre class="brush: js">console.log("This is the outer level");
console.group();
console.log("Level 2");
console.group();
console.log("Level 3");
console.warn("More of level 3");
console.groupEnd();
console.log("Back to level 2");
console.groupEnd();
console.log("Back to the outer level");</pre>

<p>La sortie ressemble à ceci :</p>

<p><img alt="Une capture d'écran de messages imbriqués dans la sortie de la console." src="nesting.png"></p>

<p>Pour plus de détail, se reporter à l'article <a href="/fr/docs/Web/API/console#Using_groups_in_the_console">Using groups in the console</a> dans la documentation sur la {{domxref("console")}}.</p>

<h2 id="Spécifications">Spécifications</h2>

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
   <td>{{SpecName("Console API", "#consolegroupobject-object-", "console.group()")}}</td>
   <td>{{Spec2("Console API")}}</td>
   <td>Initial definition</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Console.group")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="http://www.opera.com/dragonfly/documentation/console/">Opera Dragonfly documentation: Console</a></li>
</ul>
