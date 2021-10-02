---
title: FormData.values()
slug: Web/API/FormData/values
tags:
  - API
  - FormData
  - Iteration
  - Méthode
  - Reference
  - XHR
  - XMLHttpRequestAPI
  - values
translation_of: Web/API/FormData/values
---
<p>{{APIRef("XMLHttpRequest")}}</p>

<p>La méthode <code><strong>FormData.values()</strong></code> renvoie une {{jsxref("Les_protocoles_iteration", "itération")}} permettant de passer en revue toutes les valeurs contenues dans cet objet. Les valeurs sont des objets {{domxref("USVString")}} ou {{domxref("Blob")}}.</p>

<div class="note">
<p><strong>Note :</strong> Cette méthode est disponible dans les <a href="/fr/docs/Web/API/Web_Workers_API" rel="noopener">Web Workers</a>.</p>
</div>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox">formData.values();</pre>

<h3 id="Valeur_de_retour">Valeur de retour</h3>

<p>Retourne une {{jsxref("Les_protocoles_iteration", "itération")}} .</p>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: js">// Créer un objet FormData test
var formData = new FormData();
formData.append('cle1', 'valeur1');
formData.append('cle2', 'valeur2');

// Affiche les valeurs
for (var value of formData.values()) {
   console.log(value);
}
</pre>

<p>Le résultat est :</p>

<pre>valeur1
valeur2</pre>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('XMLHttpRequest','#dom-formdata','values() (as iterator&lt;&gt;)')}}</td>
   <td>{{Spec2('XMLHttpRequest')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.FormData.values")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{domxref("XMLHTTPRequest")}}</li>
 <li><a href="/fr/docs/Web/API/XMLHttpRequest/Utiliser_XMLHttpRequest">Utiliser XMLHttpRequest</a></li>
 <li><a href="/fr/docs/Web/Guide/Using_FormData_Objects">Utiliser les objets FormData</a></li>
 <li>{{HTMLElement("Form")}}</li>
</ul>
