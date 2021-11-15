---
title: runtime.connect()
slug: Mozilla/Add-ons/WebExtensions/API/runtime/connect
tags:
  - API
  - Add-ons
  - Extensions
  - Method
  - Non-standard
  - Reference
  - WebExtensions
  - connect
  - runtime
translation_of: Mozilla/Add-ons/WebExtensions/API/runtime/connect
---
<div>{{AddonSidebar()}}</div>

<div></div>

<p>Créer une connexion pour plusieurs cas d'utilisation pout votre extension.</p>

<p>Vous pouvez utiliser cette facilité dans les situations suivantes:</p>

<ul>
 <li>Dans un script de contenu, pour établir une connexion avec le script d'arrière plan (ou tout script priviligié, comme les scripts de popup ou scripts de page d'option)</li>
 <li>Dans un script d'arrière plan (ou script priviligié équivalent), pour établir une connexion avec une extension différente.</li>
</ul>

<p>Attention, vous ne pouvez pas utiliser cette fonctionnalité pour connecter une extension à son script de contenu. Pour réaliser cette opération, il vaut mieux utiliser {{WebExtAPIRef('tabs.connect()')}}.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var port = browser.runtime.connect(
  extensionId, // optional string
  connectInfo  // optional object
)
</pre>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>extensionId</code>{{optional_inline}}</dt>
 <dd><code>string</code>. L'ID de l'extension à laquelle se connecter. Si la cible à défini un ID dans la clé <a href="/fr/Add-ons/WebExtensions/manifest.json/applications">applications</a> du fichier manifest.json, alors <code>extensionId</code> doit avoir cette valeur. Autrement, il doit avoir l'ID qui a été généré pour la cible.</dd>
 <dt><code>connectInfo</code>{{optional_inline}}</dt>
 <dd><p><code>object</code>. Détails de la connexion:</p>
 <dl>
  <dt><code>name</code>{{optional_inline}}</dt>
  <dd><code>string</code>. Sera passé dans {{WebExtAPIRef("runtime.onConnect")}} pour les processus qui écoutent un évènement de type connexion.</dd>
  <dt><code>includeTlsChannelId</code>{{optional_inline}}</dt>
  <dd><code>boolean</code>. indique si l'ID du canal TLS sera transmis à  {{WebExtAPIRef("runtime.onConnectExternal")}} pour le processus qui écoutent l'événement de connexion.</dd>
 </dl>
 </dd>
</dl>

<h3 id="Valeur_retournée">Valeur retournée</h3>

<p>{{WebExtAPIRef('runtime.Port')}}. Port à travers lequel les messages peuvent être envoyés et reçus. L'événement <code>onDisconnect</code> du port est déclenché si l'extension n'existe pas.</p>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.runtime.connect")}}</p>

<h2 id="Exemples">Exemples</h2>

<p>Le script de contenu :</p>

<ul>
 <li>se connecte au script d'arrière-plan et stocke le port dans une variable appelée <code>myPort</code>.</li>
 <li>Ecoute les messages sur <code>myPort</code> et les enregistre</li>
 <li>Envoie des messages au script d'arrière pla, en utilisant <code>myPort</code>, lorsque l'utilisateur clique sur le document.</li>
</ul>

<pre class="brush: js">// content-script.js

var myPort = browser.runtime.connect({name:"port-from-cs"});
myPort.postMessage({greeting: "hello from content script"});

myPort.onMessage.addListener(function(m) {
  console.log("In content script, received message from background script: ");
  console.log(m.greeting);
});

document.body.addEventListener("click", function() {
  myPort.postMessage({greeting: "they clicked the page!"});
});</pre>

<p>Les scripts d'arrière plan correspondant :</p>

<ul>
 <li>Ecoute les tentatives de connexion du script de contenu.</li>
 <li>Quand il reçoit une tentative de connexion :
  <ul>
   <li>Stocke le port dans une variable nommé <code>portFromCS</code>.</li>
   <li>envoie un message au script de contenu en utiliant le port.</li>
   <li>Commence à écouter les messages reçus sur le port, et les enregistre.</li>
  </ul>
 </li>
 <li>Envoie des messages au script de contenu, à l'aide de <code>portFromCS</code>, lorsque l'utilisateur clique sur l'action du navigateur de l'extension.</li>
</ul>

<pre class="brush: js">// background-script.js

var portFromCS;

function connected(p) {
  portFromCS = p;
  portFromCS.postMessage({greeting: "hi there content script!"});
  portFromCS.onMessage.addListener(function(m) {
    console.log("In background script, received message from content script")
    console.log(m.greeting);
  });
}

browser.runtime.onConnect.addListener(connected);

browser.browserAction.onClicked.addListener(function() {
  portFromCS.postMessage({greeting: "they clicked the button!"});
});</pre>

<p>{{WebExtExamples}}</p>

<div class="note"><p><strong>Note :</strong></p>

<p>Cette API est basée sur l'API Chromium <a href="https://developer.chrome.com/extensions/runtime#event-onConnect"><code>chrome.runtime</code></a>. Cette documentation est dérivée de <a href="https://chromium.googlesource.com/chromium/src/+/master/extensions/common/api/runtime.json"><code>runtime.json</code></a> dans le code de Chromium code.</p>

<p>Les données de compatibilité relatives à Microsoft Edge sont fournies par Microsoft Corporation et incluses ici sous la licence Creative Commons Attribution 3.0 pour les États-Unis.</p>
</div>

<div class="hidden">
<pre>// Copyright 2015 The Chromium Authors. All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are
// met:
//
//    * Redistributions of source code must retain the above copyright
// notice, this list of conditions and the following disclaimer.
//    * Redistributions in binary form must reproduce the above
// copyright notice, this list of conditions and the following disclaimer
// in the documentation and/or other materials provided with the
// distribution.
//    * Neither the name of Google Inc. nor the names of its
// contributors may be used to endorse or promote products derived from
// this software without specific prior written permission.
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
// "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
// LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
// A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
// OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
// SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
// LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
// DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
// THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
// (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
</pre>
</div>
