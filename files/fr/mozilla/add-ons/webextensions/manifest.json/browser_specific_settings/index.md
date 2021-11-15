---
title: browser_specific_settings
slug: Mozilla/Add-ons/WebExtensions/manifest.json/browser_specific_settings
tags:
  - Add-ons
  - Extensions
  - WebExtensions
  - browser_specific_settings
translation_of: Mozilla/Add-ons/WebExtensions/manifest.json/browser_specific_settings
---
<p>{{AddonSidebar}}</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row" style="width: 30%;">Type</th>
   <td><code>Object</code></td>
  </tr>
  <tr>
   <th scope="row">Obligatoire</th>
   <td>
    <p>Habituellement, non (mais voir aussi <a href="/fr/Add-ons/WebExtensions/WebExtensions_and_the_Add-on_ID#When_do_you_need_an_Add-on_ID">Quand avec-vous besoin d'une ID Complémentaire</a><a href="/fr/Add-ons/WebExtensions/manifest.json/applications#When_do_I_need_the_applications_key">?</a>). Obligatoire avant Firefox 48 (desktop) et Firefox pour Android.</p>
   </td>
  </tr>
  <tr>
   <th scope="row">Example</th>
   <td>
    <pre class="brush: json;">
"browser_specific_settings": {
  "gecko": {
    "id": "addon@example.com",
    "strict_min_version": "42.0"
  }
}
</pre>
   </td>
  </tr>
 </tbody>
</table>

<h2 id="Description">Description</h2>

<p>La clé <code>browser_specific_settings</code> contient des clés qui sont spécifiques à certaines applications hôtes.</p>

<h3 id="Propriétés_Gecko_Firefox">Propriétés (Gecko) Firefox</h3>

<p>Actuellement, elle contient uniquement une clé, <code>gecko</code>, qui est structurée ainsi :</p>

<ul>
 <li><code>id</code> est l'ID de l'extension. Facultatif à partir de Firefox 48, obligatoire avant Firefox 48. Voir les <a href="/fr/Add-ons/WebExtensions/WebExtensions_and_the_Add-on_ID">WebExtensions et l'ID des extensions</a> pour voir quand vous devez spécifier un identifiant complémentaire.</li>
 <li><code>strict_min_version </code>: la version minimum de Gecko supportée. Les versions contenant un "*" ne sont pas valides dans ce domaine. Par défaut, c'est "42a1".</li>
 <li><code>strict_max_version</code> : la version maximum de Gecko supportée. Si la version de Firefox sur laquelle l'extension est en cours d'installation ou d'exécution est au-dessus de cette version, l'extension sera désactivée ou ne sera pas autorisée à être installée. Par défaut, c'est "*", qui désactive la vérification d'une version maximale.</li>
 <li>
  <p><code>update_url</code> est lien vers un <a href="/fr-FR/Add-ons/Install_Manifests#updateURL">manifeste de mise à jour personnalisé</a>. Notez que le lien doit commencer par "https". Cette clé consiste à gérer vous-même les mises à jour d'extension (c'est-à-dire pas via AMO).</p>
 </li>
</ul>

<p>Vois la liste des <a href="https://addons.mozilla.org/en-US/firefox/pages/appversions/">versions Gecko valides</a>.</p>

<h4 id="Format_dID_dextension">Format d'ID d'extension</h4>

<p>L'ID d'extension doit être l'un des suivants :</p>

<ul>
 <li><a href="https://en.wikipedia.org/wiki/Universally_unique_identifier">GUID</a></li>
 <li>Une chaîne formatée comme une adresse e-mail : <code>extensionname@example.org</code></li>
</ul>

<p>Ce dernier format est plus facile à générer et à manipuler. Sachez que l'utilisation d'une véritable adresse e-mail ici peut attirer des spams.</p>

<p>Par exemple :</p>

<pre class="brush: json">"id": "extensionname@example.org"</pre>

<pre class="brush: json">"id": "{daf44bf7-a45e-4450-979c-91cf07434c3d}"</pre>

<h3 id="Propriétés_Microsoft_Edge">Propriétés Microsoft Edge</h3>

<div class="warning">
<p><strong>Attention :</strong> L'ajout de propriétés spécifiques à Edge au manifeste a causé une erreur avant Firefox 69 qui peut empêcher l'extension de s'installer.</p>
</div>

<p>Microsoft Edge stocke les paramètres spécifiques à son navigateur dans la sous-clé <code>edge</code>, qui possède les propriétés suivantes :</p>

<dl>
 <dt><code>browser_action_next_to_addressbar</code></dt>
 <dd>
 <p>Propriété booléenne qui contrôle le placement de l'<a href="/fr/docs/Mozilla/Add-ons/WebExtensions/Browser_actions">action du navigateur</a>.</p>

 <ul>
  <li><code>true</code> est équivalent à la définition <code><a href="/fr/docs/Mozilla/Add-ons/WebExtensions/manifest.json/browser_action#Syntax">browser_action.default_area</a></code> à <code>navbar</code>.</li>
  <li><code>false</code> is équivalent à la définition <code><a href="/fr/docs/Mozilla/Add-ons/WebExtensions/manifest.json/browser_action#Syntax">browser_action.default_area</a></code> à <code>menupanel</code>.</li>
 </ul>
 </dd>
</dl>

<h2 id="Exemples">Exemples</h2>

<p>Exemple avec toutes les clés possibles. Notez que vous n'incluez normalement ni une version <code>strict_max_version</code> ni une clé <code>update_url</code>.</p>

<pre class="brush: json">"browser_specific_settings": {
  "gecko": {
    "id": "addon@example.com",
    "strict_min_version": "42.0",
    "strict_max_version": "50.*",
    "update_url": "https://example.com/updates.json"
  },
  "edge": {
    "browser_action_next_to_addressbar": true
  }
}</pre>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("webextensions.manifest.browser_specific_settings")}}</p>
