---
title: Event.stopPropagation()
slug: Web/API/Event/stopPropagation
tags:
  - API
  - DOM
  - Evènement
  - Méthode
  - Reference
translation_of: Web/API/Event/stopPropagation
---
<div>{{APIRef("DOM")}}</div>

<p>Évite que l'évènement courant ne se propage plus loin dans les phases de capture et de déploiement.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="syntaxbox"><em>event</em>.stopPropagation();</pre>

<h2 id="Example">Exemple</h2>

<p>Voir la section Exemple 5 : <a href="/fr/docs/Web/API/Document_Object_Model/Exemples#Exemple_5_:_propagation_d%27%C3%A9v%C3%A8nements">Propagation d'évènements</a> dans le chapitre Exemples pour un exemple plus détaillé de cette méthode et de la propagation d'évènements dans le DOM.</p>

<h2 id="Notes">Notes</h2>

<p>Voir <a href="http://www.w3.org/TR/DOM-Level-2-Events/events.html#Events-flow-capture">DOM specification</a> (en)  pour une explication du flux d'évènements. (Une illustration est disponible dans le brouillon <a href="http://www.w3.org/TR/DOM-Level-3-Events/#event-flow">DOM Level 3 Event draft</a> (en)).</p>

<p><a href="/fr/docs/Web/API/Event/preventDefault">preventDefault</a> est une méthode complémentaire qui peut être utilisée pour empêcher l'action par défaut de l'évènement.</p>

<h2 id="Specification">Spécification</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th>Spécification</th>
   <th>Statut</th>
   <th>Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName("DOM WHATWG", "#dom-event-stoppropagation", "Event.stopPropagation()")}}</td>
   <td>{{Spec2("DOM WHATWG")}}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName("DOM4", "#dom-event-stoppropagation", "Event.stopPropagation()")}}</td>
   <td>{{Spec2("DOM4")}}</td>
   <td> </td>
  </tr>
  <tr>
   <td>{{SpecName("DOM2 Events", "#Events-Event-stopPropagation", "Event.stopPropagation()")}}</td>
   <td>{{Spec2("DOM2 Events")}}</td>
   <td>Définition initiale</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Event.stopPropagation")}}</p>