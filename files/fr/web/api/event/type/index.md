---
title: Event.type
slug: Web/API/Event/type
tags:
  - API
  - DOM
  - Evènement
  - Propriétés
  - Type
translation_of: Web/API/Event/type
---
<p>{{APIRef}}</p>

<p>La propriété en lecture seule<strong> Event.type </strong>retourne une chaîne de caractères (<em>string</em>) contenant le type de l'événement. Le type est défini lors de la construction de l'événement et est le nom d'usage pour se référer à celui-ci, tel que  <code>click</code>, <code>load</code> ou <code>error</code>.</p>

<p>L'argument <code><em>event</em></code> de {{ domxref("EventTarget.addEventListener()") }} et {{ domxref("EventTarget.removeEventListener()") }} n'est pas sensible à la casse.</p>

<p>Pour une liste des types d'événements disponibles, aller voir la page <a href="/fr/docs/Web/Events">Référence des évènements</a>.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox">event.type
</pre>

<h2 id="Example">Exemples</h2>

<pre class="brush: html">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
    &lt;meta charset="utf-8"&gt;

    &lt;title&gt;Event.type Example&lt;/title&gt;

    &lt;script&gt;
        var currEvent;
        function getEvtType(evt) {
            console.group();

            currEvent = evt.type;
            console.log(currEvent);

            document.getElementById("Etype").innerHTML = currEvent;

            console.groupEnd();
        }

        //Évènements du clavier
        document.addEventListener("keypress", getEvtType, false); //[second]  

        document.addEventListener("keydown", getEvtType, false); //premier
        document.addEventListener("keyup", getEvtType, false); //troisième

        //Évènements de la souris
        document.addEventListener("click", getEvtType, false); // troisième

        document.addEventListener("mousedown", getEvtType, false); //premier
        document.addEventListener("mouseup", getEvtType, false); //second

    &lt;/script&gt;
&lt;/head&gt;

&lt;body&gt;

&lt;p&gt;Press any key or click the mouse to get the event type.&lt;/p&gt;
&lt;p&gt;Event type: &lt;span id="Etype" style="color:red"&gt;-&lt;/span&gt;&lt;/p&gt;

&lt;/body&gt;
&lt;/html&gt;</pre>

<h3 id="Specifications">Résultat</h3>

<p>{{EmbedLiveSample('Example')}}</p>

<h2 id="Specifications">Spécifications</h2>

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
   <td>{{SpecName('DOM WHATWG', '#dom-event-type', 'Event.type')}}</td>
   <td>{{ Spec2('DOM WHATWG') }}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 Events', '#Events-Event-type', 'Event.type')}}</td>
   <td>{{ Spec2('DOM2 Events') }}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.Event.type")}}</p>
