---
title: default_locale
slug: Mozilla/Add-ons/WebExtensions/manifest.json/default_locale
tags:
  - Add-ons
  - Extensions
  - WebExtensions
translation_of: Mozilla/Add-ons/WebExtensions/manifest.json/default_locale
---
<div>{{AddonSidebar}}</div>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row" style="width: 30%;">Type</th>
   <td>chaîne</td>
  </tr>
  <tr>
   <th scope="row">Obligatoire</th>
   <td>
    <p>Il doit être présent si le sous-répertoire _locales est présent, sinon il doit être absent.</p>
   </td>
  </tr>
  <tr>
   <th scope="row">Exemple</th>
   <td>
    <pre class="brush: json">
"default_locale": "fr"</pre>
   </td>
  </tr>
 </tbody>
</table>

<p>Cette clé doit être présente si l'extension contient le répertoire _locales, et doit être absente sinon. Il identifie un sous-répertoire de _locales, et ce sous-répertoire sera utilisé pour trouver les chaînes par défaut pour votre extension.</p>

<p>Voir <a href="/fr/Add-ons/WebExtensions/Internationalization">Internationalisation</a>.</p>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: json">"default_locale": "fr"</pre>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.manifest.default_locale")}}</p>
