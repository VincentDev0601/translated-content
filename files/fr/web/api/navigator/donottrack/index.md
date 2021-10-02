---
title: Navigator.doNotTrack
slug: Web/API/Navigator/doNotTrack
tags:
  - API
  - DOM
  - Propriétés
  - Reference
translation_of: Web/API/Navigator/doNotTrack
---
<p>{{ApiRef("HTML DOM")}}{{SeeCompatTable}}</p>

<p>Renvoi le paramètre utilisateur de <strong>do-not-track</strong>. Cette valeur est "1" si l´utilisateur a demandé de ne pas être suivi par les sites web, le contenu ou la publicité.</p>

<h2 id="Syntax">Syntaxe</h2>

<pre class="eval"><em>dnt</em> = <em>navigator</em>.doNotTrack;
</pre>

<p>La valeur reflète celle de l'en-tête "do-not-track" <em>(ne pas suivre)</em>, c'est-à-dire {"1", "0", "unspecified" }. Note : Avant Gecko 32, Gecko a utilisé les valeurs { "yes", "no", "unspecified"} (<a href="https://bugzilla.mozilla.org/show_bug.cgi?id=887703">bug 887703</a>).</p>

<h2 id="Example">Exemple</h2>

<pre class="eval">dump(window.navigator.doNotTrack);
//  écrit "1" si DNT est activé; "0" si l'utilisateur a opté pour le suivi; sinon c'est "unspecified" <em>(non spécifié)</em>
</pre>

<h2 id="Specification">Spécifications</h2>

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
   <td>{{SpecName("Tracking", "#widl-Navigator-doNotTrack", "Navigator.doNotTrack")}}</td>
   <td>{{Spec2("Tracking")}}</td>
   <td>Définition initiale</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Navigator.doNotTrack")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/Security/Do_not_track_field_guide">Le guide pratique Do Not Track</a></li>
</ul>
