---
title: options_ui
slug: Mozilla/Add-ons/WebExtensions/manifest.json/options_ui
tags:
  - Add-ons
  - Extensions
  - Manifest
  - Options
  - WebExtensions
  - options_ui
translation_of: Mozilla/Add-ons/WebExtensions/manifest.json/options_ui
---
<div>{{AddonSidebar}}</div>

<table class="standard-table" style="height: 166px; width: 852px;">
 <tbody>
  <tr>
   <th scope="row" style="width: 30%;">Type</th>
   <td><code>Objet</code></td>
  </tr>
  <tr>
   <th scope="row">Obligatoire</th>
   <td>Non</td>
  </tr>
  <tr>
   <th scope="row">Exemple</th>
   <td>
    <pre class="brush: json;">
"options_ui": {
  "page": "options/options.html"
}</pre>
   </td>
  </tr>
 </tbody>
</table>

<p>Utilisez la clé <code>options_ui</code> pour définir une <a href="/fr/Add-ons/WebExtensions/Options_pages">page d'options</a> pour votre extension.</p>

<p>La page d'options contient des paramètres pour l'extension. L'utilisateur peut y accéder à partir du gestionnaire des extensions du navigateur, et vous pouvez l'ouvrir à partir de votre extension à l'aide de {{WebExtAPIRef("runtime.openOptionsPage()")}}.</p>

<p>Vous spécifiez <code>options_ui</code> comme un chemin vers un fichier HTML intégré à votre extension. Le fichier HTML peut inclure des fichiers CSS et JavaScript, tout comme une page Web normale. Contrairement à une page normale, le JavaScript peut utiliser toutes les <a href="/fr/Add-ons/WebExtensions/API">APIs WebExtension</a> pour lesquelles l'extension possède des <a href="/fr/Add-ons/WebExtensions/manifest.json/permissions">permissions</a>. Cependant, il fonctionne dans un "scope" différent de celui de vos scripts d'arrière plan.</p>

<p>Si vous souhaitez <strong>partager</strong> des données ou des fonctions, entre JavaScript sur votre <strong>page d'options</strong> et vos <strong>scripts d'arrière-plan</strong>, vous pouvez le faire directement en obtenant une référence à la <a href="/fr/docs/Web/API/Window">fenêtre</a> de vos scripts d'arrière-plan avec {{WebExtAPIRef("extension.getBackgroundPage()")}}, ou une référence à {{domxref("Window")}} de l'une des pages s'exécutant dans votre extension avec {{WebExtAPIRef("extension.getViews()")}}. Ou, vous pouvez faire communiquer le JavaScript de votre page d'options et vos scripts en arrière-plan à l'aide de {{WebExtAPIRef("runtime.sendMessage()")}}, {{WebExtAPIRef("runtime.onMessage")}}, ou {{WebExtAPIRef("runtime.connect()")}}.</p>

<p>Ces derniers (ou les équivalents {{WebExtAPIRef("runtime.Port")}}  peuvent également être utilisés pour partager des options entre vos <a href="/fr/Add-frs/WebExtensions/Background_scripts">scripts d'arrière-plan</a> et vos <strong><a href="/fr/Add-ons/WebExtensions/Content_scripts">scripts de contenu.</a></strong></p>

<p>En général, vous souhaiterez stocker les options modifiées sur les pages d'options à l'aide de {{WebExtAPIRef("storage", "storage API", "", "true")}}  soit dans {{WebExtAPIRef("storage.sync()")}} (si vous souhaitez que les paramètres soient synchronisés sur toutes les instances du navigateur auxquelles l'utilisateur est connecté), ou {{WebExtAPIRef("storage.local()")}} (si les paramètres sont locaux, dans la machine/le profil actuel). Si vous le faites et que votre (vos) <a href="/fr/Add-ons/WebExtensions/Background_scripts">scripts d'arrière plan</a> (ou <a href="/fr/docs/">script(s) de contenus</a>)  doit connaître le changement, votre (vos) script(s) d'arrière plan pourra choisir d'ajouter un auditeur à {{WebExtAPIRef("storage.onChanged")}}.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<p>La clé <code>options_ui</code> est un objet avec le contenu suivant :</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Name</th>
   <th scope="col">Type</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>browser_style</code><br>
    {{optional_inline}}</td>
   <td><code>Booléen</code></td>
   <td>
    <p>Facultatif, par défaut : <code>true</code> .</p>

    <p>Utilisez cette option pour inclure une feuille de style dans votre page qui la rendra compatible avec l'interface utilisateur du navigateur et avec d'autres extensions qui utilisent la propriété <code>browser_style</code> . Bien qu'il contienne par défaut <code>true</code> , il est recommandé d'inclure cette propriété.</p>

    <p>Dans Firefox, la feuille de style peut être vue sur <code>chrome://browser/content/extension.css</code>, ou <code>chrome://browser/content/extension-mac.css</code> sur macOS. Lorsque vous fixez les dimensions, sachez que cette feuille de style fixe actuellement <code>box-sizing: border-box</code> (voir <a href="/docs/Web/CSS/box-sizing">box-sizing</a>).</p>

    <p>Le <a href="http://design.firefox.com/photon/">guide de style Firefox</a> décrit les classes que vous pouvez appliquer aux éléments de la fenêtre contextuelle afin d'obtenir des styles particuliers.</p>
   </td>
  </tr>
  <tr>
   <td><code>open_in_tab</code><br>
    {{optional_inline}}</td>
   <td><code>Booléen</code></td>
   <td>
    <p>par défaut : <code>false</code>.</p>

    <p>Si c'est <code>true</code> , la page options s'ouvrira dans un onglet normal du navigateur, plutôt que d'être intégrée au gestionnaire des extensions du navigateur.</p>
   </td>
  </tr>
  <tr>
   <td><code>page</code></td>
   <td><code>Chaîne de caractères</code></td>
   <td>
    <p>Obligatoire</p>

    <p>Le chemin d'accès au fichier HTML contenant la spécification de votre page d'options.</p>

    <p>Le chemin est relatif à l'emplacement du <code>manifest.json</code> lui-même.</p>
   </td>
  </tr>
 </tbody>
</table>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: json;">  "options_ui": {
    "page": "options/options.html"
  }</pre>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>



<p>{{Compat("webextensions.manifest.options_ui")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><code><a href="/fr/docs/Mozilla/Add-ons/WebExtensions/manifest.json/options_page">options_page</a></code> {{deprecated_inline}}</li>
 <li><a href="/fr/docs/Mozilla/Add-ons/WebExtensions/user_interface/Browser_styles">Browser styles</a></li>
 <li><a href="/fr/docs/Mozilla/Add-ons/WebExtensions/user_interface/Options_pages">Options pages</a></li>
</ul>
