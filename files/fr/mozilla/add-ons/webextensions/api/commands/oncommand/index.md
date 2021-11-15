---
title: onCommand
slug: Mozilla/Add-ons/WebExtensions/API/commands/onCommand
tags:
  - API
  - Add-ons
  - Event
  - Extensions
  - Non-standard
  - Reference
  - WebExtensions
  - commands
  - onCommand
translation_of: Mozilla/Add-ons/WebExtensions/API/commands/onCommand
---
<div>{{AddonSidebar()}}</div>

<div>Lancer quand une commande est exécutée à l'aide de son raccourci clavier associé.</div>

<div>L'écouteur reçoit  le nom de la commande. Cela correspond au nom donnée à la commande dans une  <a href="/fr/Add-ons/WebExtensions/manifest.json/commands">entrée manifest.json</a>.</div>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">browser.commands.onCommand.addListener(listener)
browser.commands.onCommand.removeListener(listener)
browser.commands.onCommand.hasListener(listener)
</pre>

<p>Les événements ont trois fonctions :</p>

<dl>
 <dt><code>addListener(callback)</code></dt>
 <dd>Ajoute un écouteur à un événement.</dd>
 <dt><code>removeListener(listener)</code></dt>
 <dd>Arrêter d'écouter un événement. L'arguement <code>listener</code> est l'écouteur à supprimer.</dd>
 <dt><code>hasListener(listener)</code></dt>
 <dd>Vérifiez si <code>listener</code> est enregistré pour cet événement . Renvoie <code>true</code> s'il écoute, <code>false</code> sinon.</dd>
</dl>

<h2 id="Syntaxe_addListener">Syntaxe addListener</h2>

<h3 id="Paramètre">Paramètre</h3>

<dl>
 <dt><code>callback</code></dt>
 <dd>
 <p>Fonction qui sera appelée lorsqu'un utilisateur entre dans le raccourci de la commande. La fonction recevra les arguments suivants :</p>

 <dl>
  <dt><code>name</code></dt>
  <dd><code>string</code>. Nom de la commande. Cela correspond au nom donné à la commande dans son <a href="/fr/Add-ons/WebExtensions/manifest.json/commands">entrée manifest.json</a>.</dd>
 </dl>
 </dd>
</dl>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.commands.onCommand")}}</p>

<h2 id="Exemples">Exemples</h2>

<div>Etant donnée une entrée manifest.json comme ceci :</div>

<pre class="brush: json">"commands": {
  "toggle-feature": {
    "suggested_key": {
      "default": "Ctrl+Shift+Y"
    },
    "description": "Send a 'toggle-feature' event"
  }
}</pre>

<div>Vous pouvez écouter cette commande particulière comme ceci :</div>

<pre class="brush: js">browser.commands.onCommand.addListener(function(command) {
  if (command == "toggle-feature") {
    console.log("toggling the feature!");
  }
});</pre>

<p>{{WebExtExamples}}</p>

<div class="note"><p><strong>Note :</strong></p>

<p>Cette API est basée sur l'API Chromium <a href="https://developer.chrome.com/extensions/commands"><code>chrome.commands</code></a>.</p>
</div>
