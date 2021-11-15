---
title: privacy.websites
slug: Mozilla/Add-ons/WebExtensions/API/privacy/websites
tags:
  - API
  - Add-ons
  - Extensions
  - Privacy
  - Property
  - Reference
  - WebExtensions
  - websites
translation_of: Mozilla/Add-ons/WebExtensions/API/privacy/websites
---
<div>{{AddonSidebar}}
<p>La propriété {{WebExtAPIRef("privacy.websites")}} contient les paramètres liés à la vie privée qui contrôlent la façon dont le navigateur interargit avec les sites web. Chaque propriété est un objet  {{WebExtAPIRef("types.BrowserSetting")}}.</p>

<p>Les valeurs par défaut  de ces propriétés ont tendance à varier selon les navigateurs.</p>

<h2 id="Propriétés">Propriétés</h2>

<dl>
 <dt><code>cookieConfig</code></dt>
 <dd>
 <p>Un objet {{WebExtAPIRef("types.BrowserSetting")}} dont la valeur sous-jacente est un objet.</p>

 <p>L'objet a deux propriétés :</p>

 <ul>
  <li><code>behavior</code>: une chaîne qui peut prendre l'une des valeurs suivantes:

   <ul>
    <li>"allow_all": accepte tous les cookies</li>
    <li>"reject_all": rejeter tous les cookies</li>
    <li>"reject_third_party": rejeter tous les cookies tiers</li>
    <li>"allow_visited" : accepte un cookie tiers uniquement si le domaine de premier niveau du cookie contient déjà au moins un cookie.</li>
    <li>"reject_trackers": rejeter les cookies de suivi</li>
   </ul>
  </li>
  <li><code>nonPersistentCookies</code>: un booléen. Si la valeur est true, tous les cookies seront traités comme des cookies de session.</li>
 </ul>
 </dd>
 <dt><code>firstPartyIsolate</code></dt>
 <dd>
 <p>Un objet {{WebExtAPIRef("types.BrowserSetting")}} dont la valeur sous-jacente est un booléen.</p>

 <p>SI <code>true</code>, la préférence <code>firstPartyIsolate</code> permet au navigateur d'associer toutes les données (y compris les cookies, les données HSTS, les images mises en cache, etc.) pour tous les domaines tiers avec le domaine dans la barre d'adresse. Cela empêche les suiveurs tiers d'utiliser directement les informations stockées pour identifier l'utilisateur sur différents sites Web, mais peut interrompre les sites Web dans lesquels l'utilisateur se connecte avec un compte tiers (tel qu'un compte Facebook ou Google).</p>

 <p>Par défaut à <code>false</code>.</p>
 </dd>
 <dt><code>hyperlinkAuditingEnabled</code></dt>
 <dd>Un objet {{WebExtAPIRef("types.BrowserSetting")}} dont la valeur sous-jacente est un booléen. Si <code>true</code>, le navigateur envoie des pings d'audit lorsqu'un site web utilise l'attribut <code>ping</code> pour les demander.</dd>
 <dt><code>protectedContentEnabled</code></dt>
 <dd>Un objet {{WebExtAPIRef("types.BrowserSetting")}} dont la valeur sous-jacente est un booléen. Disponible uniquement sur Windows. Si<code>true</code>, le navigateur fournit un ID unique aux plugins afin d'exécuter le contenu protégé.</dd>
 <dt><code>referrersEnabled</code></dt>
 <dd>Un objet {{WebExtAPIRef("types.BrowserSetting")}} dont la valeur  sous-jacente est un booléen. Si activé, le navigateur envoie les en-têtes de <a href="/fr/docs/Web/HTTP/Headers/Referer">référence</a> avec vos demandes.</dd>
 <dt><code>resistFingerprinting</code></dt>
 <dd>
 <p>Un objet {{WebExtAPIRef("types.BrowserSetting")}} dont la valeur sous-jacente est un booléen.</p>

 <p>Les empreintes digitales des navigateurs sont la pratique par laquelle les sites Web utilisent les API Web pour collecter des données d'état ou de configuration associées au navigateur ou à l'appareil sur lequel il s'exécute. En faisant cela, ils peuvent construire une empreinte numérique qu'ils peuvent utiliser pour identifier et suivre un utilisateur particulier.</p>

 <p>Si <code>true</code>, la préférence <code>resistFingerprinting</code> signale au navigateur des informations usurpées génériques pour les données couramment utilisées pour les empreintes digitales. Ces données incluent le nombre de cœurs de processeur, la précision des temporisateurs JavaScript et le fuseau horaire local. Il désactive également les fonctionnalités utilisées pour la prise d'empreintes digitales, telles que la prise en charge de GamePad et les API WebSpeech et Navigator.</p>

 <p>Par défaut à <code>false</code>.</p>
 </dd>
 <dt><code>thirdPartyCookiesAllowed</code></dt>
 <dd>Un objet {{WebExtAPIRef("types.BrowserSetting")}} dont la valeur sous-jacente est un booléen. Si <code>false</code>, le navigateur bloque les <a href="/fr/docs/Web/HTTP/Cookies#Third-party_cookies">cookies tiers</a>.</dd>
 <dt><code>trackingProtectionMode</code></dt>
 <dd>
 <p>La "protection de suivi" est une fonctionnalité de navigateur qui bloque les requêtes faites sur des domaines qui sont connus pour s'engager dans le suivi multi-sites des utilisateurs. Les sites qui suivent les utilisateurs sont généralement des sites publicitaires et analytiques tiers. Ce paramètre est un objet {{WebExtAPIRef("types.BrowserSetting")}} qui détermine si le navigateur doit activer  la protection de suivi. Sa valeur sous-jacente est une chaîne qui peut prendre l'une des trois valeurs :</p>

 <ul>
  <li><code>"always"</code>: La protection de suivi est activée.</li>
  <li><code>"never"</code>: La protection de suivi est désactivée.</li>
  <li><code>"private_browsing"</code>: La protection de suivi est activée uniquement dans les fenêtres de navigation privée.</li>
 </ul>
 </dd>
</dl>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.privacy.websites")}}</p>

<h2 id="Exemples">Exemples</h2>

<p>Définissez la propriété <code>hyperlinkAuditingEnabled</code> .</p>

<pre class="brush: js">function onSet(result) {
  if (result) {
    console.log("success");
  } else {
    console.log("failure");
  }
}

browser.browserAction.onClicked.addListener(() =&gt; {

  var getting = browser.privacy.websites.hyperlinkAuditingEnabled.get({});
  getting.then((got) =&gt; {
    console.log(got.value);
    if ((got.levelOfControl === "controlled_by_this_extension") ||
        (got.levelOfControl === "controllable_by_this_extension")) {
      var setting = browser.privacy.websites.hyperlinkAuditingEnabled.set({
        value: true
      });
      setting.then(onSet);
    } else {
      console.log("Not able to set hyperlinkAuditingEnabled");
    }
  });

});</pre>

<p>{{WebExtExamples}}</p>

<div class="note"><p><strong>Note :</strong></p>

<p>Cette API est basée sur l'API Chromium <a href="https://developer.chrome.com/extensions/privacy"><code>chrome.privacy</code></a>. Cette documentation est dérivée de <a href="https://chromium.googlesource.com/chromium/src/+/master/chrome/common/extensions/api/privacy.json"><code>privacy.json</code></a> dans le code de Chromium.</p>

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
</div>
