---
title: Document.createEvent()
slug: Web/API/Document/createEvent
tags:
  - API
  - DOM
  - Méthode
  - Reference
translation_of: Web/API/Document/createEvent
---
<div class="warning">
<p><strong>Attention :</strong> De nombreuses méthodes utilisées avec <code>createEvent</code>, tels que <code>initCustomEvent</code>, sont obsolètes. Utilisez le <a href="/fr/docs/Web/API/CustomEvent">constructeur d'événement </a><a href="/fr/docs/Web/API/CustomEvent"> </a>à la place.</p>
</div>

<div>{{ ApiRef("DOM") }}</div>

<p>Crée un <a href="/en-US/docs/DOM/event">event</a> du type spécifié. L'objet retourné doit être intialisé et peut être passé ensuite à <a href="/en-US/docs/DOM/element.dispatchEvent">element.dispatchEvent</a>.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox">var <em>event</em> = <em>document</em>.createEvent(<em>type</em>);
</pre>

<ul>
 <li><code>event</code> est l'objet <a href="/en-US/docs/DOM/event">Event</a> créé.</li>
 <li><code>type</code> est une chaîne de caractères qui représente le type d'événement à créer. Les types possibles d'événement incluent <code>"UIEvents"</code>, <code>"MouseEvents"</code>, <code>"MutationEvents"</code> et <code>"HTMLEvents"</code>. Voir la section {{Anch("Notes")}} pour plus de détails.</li>
</ul>

<h2 id="Example">Exemple</h2>

<pre>// Crée l'événement.
var event = document.createEvent('Event');

// Nomme l'événement 'build'.
event.initEvent('build', true, true);

//  Écoute l'événement.
elem.addEventListener('build', function (e) {
  // e.target correspond à elem
}, false);

// target peut être tout Element ou autre EventTarget.
elem.dispatchEvent(event);
</pre>

<h3 id="Notes">Notes</h3>

<p>Les chaînes de type d'événement appropriées pour passer à <code>createEvent ()</code> sont répertoriées dans la norme DOM - voir le tableau à l'étape 2. Gardez à l'esprit que la plupart des objets événement ont maintenant des constructeurs, qui sont la méthode recommandée pour créer des occurrences d'objet événement.</p>

<p>Gecko prend en charge certains alias d'objet événement non standard, répertoriés ci-dessous :</p>

<table class="fullwidth-table">
 <tbody>
  <tr>
   <th>Event Module</th>
   <th>Standard event object</th>
   <th>Gecko also supports</th>
  </tr>
  <tr>
   <td>Text event module</td>
   <td><code>TextEvent</code></td>
   <td><code>TextEvents</code></td>
  </tr>
  <tr>
   <td>Keyboard event module</td>
   <td><code>KeyboardEvent</code></td>
   <td><code>KeyEvents</code></td>
  </tr>
  <tr>
   <td>Basic events module</td>
   <td><code>Event</code></td>
   <td><code>Events</code></td>
  </tr>
 </tbody>
</table>

<h2 id="Spécification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Events/events.html#Events-DocumentEvent-createEvent">DOM Level 2 Events: createEvent</a></li>
 <li><a href="http://www.w3.org/TR/DOM-Level-3-Events/#events-Events-DocumentEvent-createEvent">DOM Level 3 Events: createEvent</a></li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/Guide/DOM/Events/Creating_and_triggering_events">Création et déclenchement d'événements</a></li>
</ul>
