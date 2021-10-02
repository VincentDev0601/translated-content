---
title: Console
slug: Web/API/Console
tags:
  - API
  - Interface
  - Reference
  - console
  - débogage
translation_of: Web/API/Console
---
<div>{{APIRef("Console API")}}</div>

<p>L'objet <strong><code>console</code></strong> donne accès à la console de débogage du navigateur (par exemple., la<a href="/fr/docs/Outils/Console_Web"> Console Web</a> dans Firefox). Les spécificités de fonctionnement varient d'un navigateur à l'autre, mais il y a tout de même un ensemble de fonctionnalités qui sont fournies de base.</p>

<p>La <code>console</code> est accessible de n'importe quel objet global, {{domxref("Window")}} du cadre de navigation, {{domxref("WorkerGlobalScope")}} et ses variantes spécifiques pour les workers. Elle est exposée comme {{domxref ("Window.console")}} et peut être référencée simplement comme console. Par exemple :</p>

<pre class="brush: js">console.log("Failed to open the specified link")</pre>

<p>Cette page documente les {{anch("Methods", "méthodes")}} disponibles pour l'objet <code>console</code> et donne quelques {{anch("Usage", "exemples d'utilisation")}}.</p>

<p>{{AvailableInWorkers}}</p>

<h2 id="Méthodes">Méthodes</h2>

<dl>
 <dt>{{domxref("Console.assert()")}}</dt>
 <dd>Affiche un message et une trace d'appels dans la console si l'assertion en argument est à <code>false</code>.</dd>
 <dt>{{domxref("Console.clear()")}}</dt>
 <dd>Vide la console.</dd>
 <dt>{{domxref("Console.count()")}}</dt>
 <dd>Affiche le nombre de fois que la ligne a été appelée avec un label donné.</dd>
 <dt>{{domxref("Console.debug()")}}</dt>
 <dd>Un alias de <code>log().</code></dd>
</dl>

<div class="note">
<p><strong>Note :</strong> À partir de Chromium 58, cette méthode n'apparaît que dans les consoles de navigateur Chromium lorsque le niveau "Verbose" est sélectionné.</p>
</div>

<dl>
 <dt>{{domxref("Console.dir()")}} {{Non-standard_inline}}</dt>
 <dd>Affiche une liste interactive des propriétés d'un objet JavaScript donné. Cette liste vous permet d'examiner le contenu des enfants de l'objet en ouvrant les détails (petits triangles).</dd>
 <dt>{{domxref("Console.dirxml()")}} {{Non-standard_inline}}</dt>
 <dd>
 <p>Affiche si possible une représentation d'éléments XML/HTML d'un objet spécifié. Sinon, c'est une vue de l'objet JavaScript.</p>
 </dd>
 <dt>{{domxref("Console.error()")}}</dt>
 <dd>Affiche un message d'erreur. Vous pouvez utiliser les <a href="/fr/docs/Web/API/console#Utiliser_les_caractères_de_substitution">caractères de substitution</a> et des arguments supplémentaires avec cette méthode.</dd>
 <dt>{{domxref("Console._exception()")}} {{Non-standard_inline}} {{deprecated_inline}}</dt>
 <dd>Un alias d'<code>error();</code></dd>
 <dt>{{domxref("Console.group()")}}</dt>
 <dd>Crée un nouveau <a href="/fr/docs/Web/API/console#Using_groups_in_the_console">groupe</a> en ligne, correspondant à un nouveau niveau d'indentation. Contrairement à <code>group()</code>. Pour revenir au niveau précédent, appeler <code>groupEnd()</code>.</dd>
 <dt>{{domxref("Console.groupCollapsed()")}}</dt>
 <dd>Crée un nouveau <a href="/fr/docs/Web/API/console#Using_groups_in_the_console">groupe</a> en ligne, correspondant à un nouveau niveau d'indentation. Contrairement à <code>group()</code> , cela commence avec le groupe en ligne effondré, nécessitant l'utilisation d'un bouton de divulgation pour l'agrandir. Pour revenir au niveau précédent, appeler <code>groupEnd()</code>.</dd>
 <dt>{{domxref("Console.groupEnd()")}}</dt>
 <dd>Quitte le <a href="/fr/docs/Web/API/console#Using_groups_in_the_console">groupe</a> d'indentation courant.</dd>
 <dt>{{domxref("Console.info()")}}</dt>
 <dd>Affiche un message d'information. Vous pouvez utiliser les <a href="/fr/docs/Web/API/console#Utiliser_les_caractères_de_substitution">caractères de substitution</a> et des arguments supplémentaires avec cette méthode.</dd>
 <dt>{{domxref("Console.log()")}}</dt>
 <dd>Permet d'afficher des messages dans la console. Vous pouvez utiliser les <a href="/fr/docs/Web/API/console#Utiliser_les_caractères_de_substitution">caractères de substitution</a> et des arguments supplémentaires avec cette méthode.</dd>
 <dt>{{domxref("Console.profile()")}} {{Non-standard_inline}}</dt>
 <dd>démarre le profilage du navigateur (par exemple, l'<a href="/fr/docs/Outils/Performance">outil performances de Firefox</a>). Vous pouvez spécifier un nom en option pour ce profil.</dd>
 <dt>{{domxref("Console.profileEnd()")}} {{Non-standard_inline}}</dt>
 <dd>Arrête le profilage. Vous pouvez voir le résultat de ce dernier dans l'outil « performance » du navigateur (par exemple, l'<a href="/fr/docs/Outils/Performance">outil performance Firefox</a>).</dd>
 <dt>{{domxref("Console.table()")}}</dt>
 <dd>Affiche des données tabulaires comme un tableau.</dd>
 <dt>{{domxref("Console.time()")}}</dt>
 <dd>Démarre un <a href="/fr/docs/Web/API/console#Timers">chronomètre</a> que l'on peut nommer en le spécifiant en tant que paramètre. Jusqu'à 10 000 chronomètres simultanés peuvent tourner sur une page.</dd>
 <dt>{{domxref("Console.timeEnd()")}}</dt>
 <dd>Arrête le <a href="/fr/docs/Web/API/console#Timers">chronomètre</a> spécifié et affiche le temps écoulé en millisecondes depuis son démarrage.</dd>
 <dt>{{domxref("Console.timeStamp()")}} {{Non-standard_inline}}</dt>
 <dd>Ajoute un marqueur dans la <a href="https://developer.chrome.com/devtools/docs/timeline">Timeline</a> du navigateur ou l'outil <a href="/fr/docs/Outils/Performance/Waterfall">Waterfall</a>.</dd>
 <dt>{{domxref("Console.trace()")}}</dt>
 <dd>Affiche une <a href="/fr/docs/Web/API/console#Traces_d%27appel">trace d'appels</a>.</dd>
 <dt>{{domxref("Console.warn()")}}</dt>
 <dd>Affiche un message d'avertissement. Vous pouvez utiliser les <a href="/fr/docs/Web/API/console#Utiliser_les_caractères_de_substitution">caractères de substitution</a> et des arguments supplémentaires avec cette méthode.</dd>
</dl>


<h2 id="Usage">Exemples d'utilisation</h2>

<h3 id="Outputting_text_to_the_console">Afficher du texte dans la console</h3>

<p>La fonction la plus utilisée de la console est d'afficher du texte ou autres données. Il y a quatre sortes d'affichages que vous pouvez générer, en utilisant les méthodes {{domxref("console.log()")}}, {{domxref("console.info()")}}, {{domxref("console.warn()")}}, et {{domxref("console.error()")}}. Chacune de ces méthodes génére un affichage différent dans la console, et vous pouvez utiliser les fonctions de filtrage du navigateur pour voir uniquement les types de sortie qui vous intéressent.</p>

<p>Il y a deux manières d'utiliser chacune de ces méthodes de sortie ; Vous pouvez passer une liste d'objets dont leur représentation sera concaténée dans une seule chaine et s'affichera dans la console, ou vous pouvez passer une chaîne de caractères contenant zéro et plus de caractères de substitution suivis d'une liste d'objets avec lesquels les remplacer.</p>

<h4 id="Afficher_un_seul_objet">Afficher un seul objet</h4>

<p>La manière la plus simple d'utiliser les méthodes de « log » est d'afficher un seul objet :</p>

<pre class="brush: js">var someObject = { str: "Some text", id: 5 };
console.log(someObject);
</pre>

<p>L'affichage ressemblera à ceci :</p>

<pre>[09:27:13.475] ({str:"Some text", id:5})</pre>

<h4 id="Afficher_plusieurs_objets">Afficher plusieurs objets</h4>

<p>Vous pouvez aussi afficher plusieurs objets, en les séparant par une virgule, comme ceci :</p>

<pre class="brush: js">var car = "Dodge Charger";
var someObject = {str:"Some text", id:5};
console.info("My first car was a", car, ". The object is: ", someObject);</pre>

<p>L'affichage ressemblera à ceci :</p>

<pre>[09:28:22.711] My first car was a Dodge Charger . The object is:  ({str:"Some text", id:5})
</pre>

<h4 id="Utiliser_les_caractères_de_substitution">Utiliser les caractères de substitution</h4>

<p>Gecko 9.0 {{geckoRelease("9.0")}} a amené le support des caractères de substitution. Lorsque l'on passe en argument une chaîne à l'une des méthodes qui acceptent des chaînes de caractère, on peut utiliser ces caractères de substitution :</p>

<table class="standard-table">
 <tbody>
  <tr>
   <td class="header">caractère de substitution</td>
   <td class="header">description</td>
  </tr>
  <tr>
   <td>%o or %O</td>
   <td>Affiche un lien hypertexte sur un objet JavaScript. Cliquer le lien ouvre l'inspecteur.</td>
  </tr>
  <tr>
   <td>%d or %i</td>
   <td>Affiche un entier. Le formatage des nombres est supporté, par exemple console.log ("Foo% .2d", 1.1) affichera le nombre sous forme de deux chiffres significatifs avec un 0 : Foo 01</td>
  </tr>
  <tr>
   <td>%s</td>
   <td>Affiche une chaîne de caractères.</td>
  </tr>
  <tr>
   <td>%f</td>
   <td>Affiche un nombre réél. Le formatage est supporté, par exemple, <code>console.log("Foo %.2f", 1.1)</code> affichera un nombre avec 2 décimales : <code>Foo 1.10</code> .</td>
  </tr>
 </tbody>
</table>

<p>Chacun de ceux-ci ira chercher l'argument qui suit la chaîne à formater. Par exemple :</p>

<pre>for (var i=0; i&lt;5; i++) {
  console.log("Hello, %s. You've called me %d times.", "Bob", i+1);
}
</pre>

<p>L'affichage ressemblera à ceci :</p>

<pre>[13:14:13.481] Hello, Bob. You've called me 1 times.
[13:14:13.483] Hello, Bob. You've called me 2 times.
[13:14:13.485] Hello, Bob. You've called me 3 times.
[13:14:13.487] Hello, Bob. You've called me 4 times.
[13:14:13.488] Hello, Bob. You've called me 5 times.
</pre>

<h4 id="Donner_un_style_à_l'affichage_de_la_console">Donner un style à l'affichage de la console</h4>

<p>Vous pouvez utiliser l'instruction <code>"%c"</code> pour appliquer du style CSS à l'affichage de la console :</p>

<pre class="brush: js">console.log("This is %cMy stylish message", "color: yellow; font-style: italic; background-color: blue;padding: 2px");</pre>

<p><img alt="" src="css-styling.png"></p>

<div class="note">
<p><strong>Note :</strong> Un certain nombre de propriétés CSS sont supportées par ce style; vous devriez expérimenter et voir lesquels s'avèrent utiles.</p>
</div>

<p>{{h3_gecko_minversion("Using groups in the console", "9.0")}}</p>

<p>Vous pouvez utiliser des groupes imbriqués pour vous aider à vous repérer dans l'affichage. Pour créer un nouveau bloc, appelez <code>console.group()</code>. La méthode <code>console.groupCollapsed()</code> est similaire, mais elle crée un bloc qui sera réduit.</p>

<div class="note">
  <p><strong>Note :</strong> "Collapsed groups" ne sont pas supportés pour l'instant dans Gecko; La méthode <code>groupCollapsed()</code> est la même que <code>group()</code> en ce moment.</p>
</div>

<p>Pour quitter le groupe dans lequel on est, appeler <code>console.groupEnd()</code>. Par exemple, examinez ce code :</p>

<pre class="brush: js">console.log("This is the outer level");
console.group();
console.log("Level 2");
console.group();
console.log("Level 3");
console.warn("More of level 3");
console.groupEnd();
console.log("Back to level 2");
console.groupEnd();
console.debug("Back to the outer level");
</pre>

<p>L'affichage ressemblera à ceci :</p>

<p><img alt="Démonstration de groupes imbriqués dans la console Firefox" src="console_groups_demo.png"></p>

<div>{{h3_gecko_minversion("Timers", "10.0")}}</div>

<p>Pour calculer la durée d'une opération spécifique, Gecko 10 a amené le supports des chronomètres dans l'objet <code>console</code>.  pour démarrer un chronomètre, appelez la méthode <code>console.time</code><code>()</code> en lui donnant un seul paramètre, son nom. Pour arrêter le chronomètre et obtenir le temps écoulé en millisecondes, utilisez la méthode <code>console.timeEnd()</code>, en passant à nouveau le nom du chronomètre comme paramètre. Une seule page peut faire tourner un maximum de 10.000 chronomètres.</p>

<p>Par exemple, voici ce code :</p>

<pre class="brush: js">console.time("answer time");
alert("Click to continue");
console.timeEnd("answer time");
</pre>

<p>affichera le temps pour l'utilisateur dont il a eu besoin pour faire disparaitre la fenêtre d'alerte :</p>

<p><img src="console-timelog.png"></p>

<p>Notez que le nom du chronomètre est affiché deux fois, à son départ et quand il se termine.</p>

<div class="note">
  <p><strong>Note:</strong> Il est important de noter que si vous vous servez de ceci pour enregistrer les durées du traffic réseau, le chronomètre renverra le temps total d'échanges, alors que les durées affichées dans l'onglet network représente seulement la durée à la réception du header. Si vous avez activer l'enregistrement de réponse du body, le temps listé pour la réponse du header et du body devrait correspondre à ce qu'affiche la sortie de la console.</p>
</div>

<h3 id="Traces_d'appel">Traces d'appel</h3>

<p>L'objet console supporte aussi l'affichage d'une trace d'appels ; cela montre le chemin pris pour atteindre l'endroit auquel vous avez fait appel à la fonction {{domxref("console.trace()")}}. Ce qui donne avec ce code :</p>

<pre>foo();

function foo() {
  function bar() {
    console.trace();
  }
  bar();
}
</pre>

<p>L'affichage dans la console ressemblera à ceci :</p>

<p><img alt="" src="api-trace2.png"></p>

<h2 id="Specification">Spécification</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Specification</th>
   <th scope="col">Status</th>
   <th scope="col">Comment</th>
  </tr>
  <tr>
   <td>{{SpecName('Console API')}}</td>
   <td>{{Spec2('Console API')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Notes">Notes</h2>

<ul>
 <li>Au moins dans Firefox, si une page définit un objet console, cet objet remplace celui créé dans Firefox.</li>
 <li>Antérieur à {{Gecko ("12.0")}}, les méthodes de l'objet console ne fonctionnent que lorsque la console Web est ouverte. À partir de {{Gecko ("12.0")}}, la sortie est mise en cache jusqu'à ce que la console Web soit ouverte, puis affichée à ce moment-là.</li>
 <li>Il est à noter que l'objet de console intégré de Firefox est compatible avec celui fourni par <a href="http://getfirebug.com/">Firebug</a>.</li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Outils">Outils de développement</a></li>
 <li><a href="/fr/docs/Outils/Console_Web">Console web</a> - comment la console Web de Firefox gère les appels d'API de console</li>
 <li><a href="/fr/docs/Outils/D%C3%A9bogage_distant">Débogage distant</a> - comment afficher la sortie de la console lorsque la cible de débogage est un périphérique mobile</li>
 <li><a href="/fr/docs/Archive/B2G_OS/Debugging/Journalisation_console">Journalisation console sur l'appareil</a> - comment se connecter sur les appareils Firefox OS</li>
</ul>

<h3 id="Autres_implémentations">Autres implémentations</h3>

<ul>
 <li><a href="https://developers.google.com/chrome-developer-tools/docs/console-api">Google Chrome DevTools</a></li>
 <li><a href="http://getfirebug.com/wiki/index.php/Console_API">Firebug</a></li>
 <li><a href="http://msdn.microsoft.com/en-us/library/hh772173(v=vs.85).aspx">Internet Explorer</a></li>
 <li><a href="https://developer.apple.com/library/safari/documentation/AppleApplications/Conceptual/Safari_Developer_Guide/Console/Console.html">Safari</a></li>
</ul>
