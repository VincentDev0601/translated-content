---
title: Event.eventPhase
slug: Web/API/Event/eventPhase
tags:
  - API
  - DOM
  - Evènement
  - Flux
  - Phase
  - Propriétés
translation_of: Web/API/Event/eventPhase
---
<p>{{ApiRef("DOM")}}</p>

<p>Indique quelle phase du flux d'événements est actuellement évaluée.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js"><em>var phase</em> = event.eventPhase;
</pre>

<p>Retourne un entier qui spécifie la phase courante d'évaluation du flux d'événements. Les valeurs possibles sont listées dans {{anch("Constantes de phase d'événement")}}.</p>

<h2 id="Constantes">Constantes</h2>

<h3 id="Constantes_de_phase_d'événement">Constantes de phase d'événement</h3>

<p>Ces valeurs décrivent quelle est la phase du flux d'événements actuellement évalué.</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Constant</th>
   <th scope="col">Value</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>Event.NONE</code></td>
   <td>0</td>
   <td>
    <p>Aucun événement n'est actuellement traité.</p>
   </td>
  </tr>
  <tr>
   <td><code>Event.CAPTURING_PHASE</code></td>
   <td>1</td>
   <td>
    <p>L'événement se propage à travers les objets ancêtres de la cible. Ce processus commence avec {{domxref("Window")}}, puis {{domxref("Document")}}, ensuite {{domxref("HTMLHtmlElement")}} et ainsi de suite à travers les éléments jusqu'à ce que le parent de la cible soit atteint. {{domxref("EventListener", "Event listeners", "", 1)}} sont enregistrés pour le mode capture lorsque {{domxref("EventTarget.addEventListener()")}} est appelé durant cette phase.</p>
   </td>
  </tr>
  <tr>
   <td><code>Event.AT_TARGET</code></td>
   <td>2</td>
   <td>L'événement est arrivé à {{domxref("EventTarget", "the event's target", "", 1)}}. Les écouteurs d'événements  enregistrés pour cette phase sont appelés à ce moment. Si {{domxref("Event.bubbles")}} vaut <code>false</code> (<em>faux</em>), le traitement de l'événement est terminé une fois la phase complète.</td>
  </tr>
  <tr>
   <td><code>Event.BUBBLING_PHASE</code></td>
   <td>3</td>
   <td>L'événement se propage à rebours à travers les ancêtres de la cible dans l'ordre inverse, commençant avec le parent, et atteignant finalement le contenant {{domxref("Window")}}. Ceci est connu comme propagation et arrive seulement si {{domxref("Event.bubbles")}} vaut <code>true</code> (<em>vrai</em>). Les {{domxref("EventListener", "Event listeners", "", 1)}} enregistrés pour cette phase sont déclenchés durant ce traitement.</td>
  </tr>
 </tbody>
</table>

<p>Pour plus de détails, voir <a href="http://www.w3.org/TR/DOM-Level-3-Events/#event-flow">section 3.1, Event dispatch and DOM event flow</a> (en) de la spécification du DOM niveau 3 sur les évènements .</p>

<h2 id="Example">Exemple</h2>

<h3 id="HTML">HTML</h3>

<pre class="brush: html">&lt;h4&gt;Event Propagation Chain&lt;/h4&gt;
&lt;ul&gt;
  &lt;li&gt;Click 'd1'&lt;/li&gt;
  &lt;li&gt;Analyse event propagation chain&lt;/li&gt;
  &lt;li&gt;Click next div and repeat the experience&lt;/li&gt;
  &lt;li&gt;Change Capturing mode&lt;/li&gt;
  &lt;li&gt;Repeat the experience&lt;/li&gt;
&lt;/ul&gt;
&lt;input type="checkbox" id="chCapture" /&gt;
&lt;label for="chCapture"&gt;Use Capturing&lt;/label&gt;
 &lt;div id="d1"&gt;d1
  &lt;div id="d2"&gt;d2
      &lt;div id="d3"&gt;d3
          &lt;div id="d4"&gt;d4&lt;/div&gt;
      &lt;/div&gt;
  &lt;/div&gt;
 &lt;/div&gt;
 &lt;div id="divInfo"&gt;&lt;/div&gt;
</pre>

<h3 id="CSS">CSS</h3>

<pre class="brush: css">div {
  margin: 20px;
  padding: 4px;
  border: thin black solid;
}

#divInfo {
  margin: 18px;
  padding: 8px;
  background-color:white;
  font-size:80%;
}</pre>

<h3 id="JavaScript">JavaScript</h3>

<pre class="brush: js">var clear = false, divInfo = null, divs = null, useCapture = false;
window.onload = function () {
  divInfo = document.getElementById("divInfo");
  divs = document.getElementsByTagName('div');
  chCapture = document.getElementById("chCapture");
  chCapture.onclick = function () {
    RemoveListeners();
    AddListeners();
  }
  Clear();
  AddListeners();
}

function RemoveListeners() {
  for (var i = 0; i &lt; divs.length; i++) {
    var d = divs[i];
    if (d.id != "divInfo") {
      d.removeEventListener("click", OnDivClick, true);
      d.removeEventListener("click", OnDivClick, false);
    }
  }
}

function AddListeners() {
  for (var i = 0; i &lt; divs.length; i++) {
    var d = divs[i];
    if (d.id != "divInfo") {
      if (chCapture.checked)
        d.addEventListener("click", OnDivClick, true);
      else
        d.addEventListener("click", OnDivClick, false);
      d.onmousemove = function () { clear = true; };
    }
  }
}

function OnDivClick(e) {
  if (clear) {
    Clear(); clear = false;
  }
  if (e.eventPhase == 2)
    e.currentTarget.style.backgroundColor = 'red';
  var level = e.eventPhase == 0 ? "none" : e.eventPhase == 1 ? "capturing" : e.eventPhase == 2 ? "target" : e.eventPhase == 3 ? "bubbling" : "error";
  divInfo.innerHTML += e.currentTarget.id + "; eventPhase: " + level + "&lt;br/&gt;";
}

function Clear() {
  for (var i = 0; i &lt; divs.length; i++) {
    if (divs[i].id != "divInfo")
      divs[i].style.backgroundColor = (i &amp; 1) ? "#f6eedb" : "#cceeff";
  }
  divInfo.innerHTML = '';
}</pre>

<p>{{ EmbedLiveSample('Example', '', '700', '', 'Web/API/Event/eventPhase') }}</p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th>Spécification</th>
   <th>Statut</th>
   <th>Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName("DOM WHATWG", "#dom-event-eventphase", "Event.eventPhase")}}</td>
   <td>{{Spec2("DOM WHATWG")}}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName("DOM4", "#dom-event-eventphase", "Event.eventPhase")}}</td>
   <td>{{Spec2("DOM4")}}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName("DOM2 Events", "#Events-Event-eventPhase", "Event.eventPhase")}}</td>
   <td>{{Spec2("DOM2 Events")}}</td>
   <td>Première définition</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.Event.eventPhase")}}</p>
