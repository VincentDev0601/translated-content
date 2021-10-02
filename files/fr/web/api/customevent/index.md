---
title: CustomEvent
slug: Web/API/CustomEvent
tags:
  - API
  - DOM
  - Interface
  - Reference
  - évènements
translation_of: Web/API/CustomEvent
---
<p>{{APIRef("DOM")}}</p>

<p>Les interfaces <code>CustomEvent</code> DOM sont des évènements initialisés par une application pour n'importe quel usage.</p>

<p>{{AvailableInWorkers}}</p>

<h2 id="Method_overview">Constructeur</h2>

<dl>
 <dt>{{domxref("CustomEvent.CustomEvent", "CustomEvent()")}}</dt>
 <dd>Crée un <code>CustomEvent.</code></dd>
</dl>

<h2 id="Attributes">Propriétés</h2>

<dl>
 <dt>{{domxref("CustomEvent.detail")}} {{readonlyinline}}</dt>
 <dd>Toute donnée transmise lors de l'initialisation de l'événement.</dd>
</dl>

<p>Cette interface hérite des propriétés de son parent {{domxref("Event")}}:</p>

<p>{{Page("/fr/docs/Web/API/Event", "Propriétés")}}</p>

<h2 id="Méthodes">Méthodes</h2>

<dl>
 <dt>{{domxref("CustomEvent.initCustomEvent()")}} {{deprecated_inline}}</dt>
 <dd>Initialise un objet CustomEvent. Si l'événement a déjà été distribué, cette méthode ne fait rien.</dd>
</dl>

<p>Cette interface hérite les méthodes de son parent {{domxref("Event")}}:</p>

<p>{{Page("/fr/docs/Web/API/Event", "Méthodes")}}</p>

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
   <td>{{SpecName('DOM WHATWG','#interface-customevent','CustomEvent')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>Définition initial</td>
  </tr>
 </tbody>
</table>

<h2 id="Browser_compatibility">Compatibilité des navigateurs</h2>

<p>{{Compat("api.CustomEvent")}}</p>

<h2 id="Déclenchement_à_partir_de_code_privilégié_vers_du_code_non-privilégié">Déclenchement à partir de code privilégié vers du code non-privilégié</h2>

<p>Lors du déclenchement d'un CustomEvent depuis du code privilégié (une extension, par exemple) vers du code non-privilégié (une page web par exemple), vous devez prendre en considération la sécurité. Firefox et les autres applications Gecko empêchent qu'un objet créé dans un contexte soit utilisé dans un autre, ce qui empêchera généralement les failles de sécurité, mais ces restrictions peuvent aussi empêcher votre code de s'executer comme prévu.</p>

<p>Lors de la création d'un objet CustomEvent, vous devez créer l'objet à partir de la même <a href="/fr/docs/Mozilla/Tech/XUL/window">fenêtre</a> que celle où vous déclencherez l'évenement.</p>

<pre class="brush: js">// doc est une référence au contenu du document
function dispatchCustomEvent(doc) {
  var eventDetail = Components.utils.cloneInto({foo: 'bar'}, doc.defaultView);
  var myEvent = doc.defaultView.CustomEvent("mytype", eventDetail);
  doc.dispatchEvent(myEvent);
}</pre>

<p>Notez qu'exposer une fonction permettra au script de l'exécuter avec les privilèges qu'accorde Chrome ce qui peut ouvrir une faille de sécurité.</p>

<h2 id="Specification">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Extraits_de_code/Interaction_entre_des_pages_%C3%A0_privil%C3%A8ges_et_sans_privil%C3%A8ges">Interaction entre pages privilégiées et non-privilégiées</a></li>
 <li><a href="/fr/docs/Web/API/Window/postMessage">Window.postMessage</a></li>
 <li><a href="/fr/docs/Web/Guide/DOM/Events/Creating_and_triggering_events">Création et déclenchement d'événements</a></li>
</ul>
