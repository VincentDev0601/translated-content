---
title: AudioWorklet
slug: Web/API/AudioWorklet
tags:
  - API
  - Audio
  - AudioWorklet
  - Background
  - Custom
  - Interface
  - Low-latency
  - Reference
  - Web Audio API
  - Worklet
  - Zero-latency
  - latency
  - sound
translation_of: Web/API/AudioWorklet
---
<p>{{APIRef("Web Audio API")}}{{securecontext_header}}</p>

<p>L'interface <strong><code>AudioWorklet</code></strong> dans l'<a href="/fr/docs/Web/API/Web_Audio_API">API Web Audio</a> est utilisée pour fournir des scripts de traitement audio personnalisés qui s'exécutent dans un thread séparé afin de fournir un traitement audio à très faible latence. Le code du worklet est exécuté dans le contexte d'exécution global {{domxref("AudioWorkletGlobalScope")}}, en utilisant un thread audio web séparé qui est partagé par le worklet et les autres nœuds audio.</p>

<p>L'accès à distance d'<code>AudioWorklet</code> du contexte audio se fait par la propriété {{domxref("BaseAudioContext.audioWorklet")}}.</p>

<h2 id="Propriétés">Propriétés</h2>

<p><em>L'interface <code>AudioWorklet</code> </em>ne définit pas de propriétés propres, mais hérite des propriétés de<em> {{domxref("Worklet")}}.</em></p>

<h2 id="Méthodes">Méthodes</h2>

<p>Cette interface hérite des méthodes de<em> {{domxref('Worklet')}}. L'interface <code>AudioWorklet</code> </em>ne définit aucune méthode propre<em>.</em></p>

<h2 id="Evénements">Evénements</h2>

<p>L'<em><code>AudioWorklet</code> </em>n'a pas d'événements auxquels il répond<em>.</em></p>

<h2 id="Exemples">Exemples</h2>

<p>Voir {{domxref("AudioWorkletNode")}} pour des exemples complets de création de nœuds audio personnalisés.</p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Status</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('Web Audio API','#audioworklet','AudioWorklet')}}</td>
   <td>{{Spec2('Web Audio API')}}</td>
   <td>Définition intiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<div>


<p>{{Compat("api.AudioWorklet")}}</p>
</div>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{domxref("AudioWorkletGlobalScope")}} — le contexte global d'exécution d'un <code>AudioWorklet</code></li>
 <li><a href="/fr/docs/Web/API/Web_Audio_API">API Web Audio</a></li>
 <li><a href="/fr/docs/Web/API/Web_Audio_API/Using_Web_Audio_API">Utiliser la Web Audio API</a></li>
</ul>
