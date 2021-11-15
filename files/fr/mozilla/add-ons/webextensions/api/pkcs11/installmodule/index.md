---
title: pkcs11.installModule()
slug: Mozilla/Add-ons/WebExtensions/API/pkcs11/installModule
tags:
  - API
  - Add-ons
  - Extensions
  - Method
  - Reference
  - WebExtensions
  - installModule
  - pkcs11
translation_of: Mozilla/Add-ons/WebExtensions/API/pkcs11/installModule
---
<div>{{AddonSidebar()}}</div>

<p>Installe le module PKCS # 11 nommé, le rendant disponible pour Firefox</p>

<p>C'est une fonction asynchrone qui renvoie une <code><a href="/fr/docs/Web/JavaScript/Reference/Objets_globaux/Promise">Promise</a></code>.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var installing = browser.pkcs11.installModule(
  name,              // string
  flags              // integer
)
</pre>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>name</code></dt>
 <dd><code>string</code>. Nom du module à installer. Cela doit correspondre à la propriété <code>name</code> property dans le <a href="/fr/Add-ons/WebExtensions/Native_manifests#PKCS_11_manifests">manifest PKCS #11</a> pour le module.</dd>
 <dt><code>flags</code>{{optional_inline}}</dt>
 <dd><code>integer</code>. Drapeaux à transmettre au module.</dd>
</dl>

<h3 id="Valeur_retournée">Valeur retournée</h3>

<p>Une <code><a href="/fr/docs/Web/JavaScript/Reference/Objets_globaux/Promise">Promise</a></code> qui sera accompli sans arguments une fois le module installé.</p>

<p>Si le module n'a pas pu être trouvé ou qu'une autre erreur se produit, la promise sera rejetée avec un message d'erreur.</p>

<h2 id="Browser_compatibility">Browser compatibility</h2>

<p>{{Compat("webextensions.api.pkcs11.installModule", 10)}}</p>

<h2 id="Exemples">Exemples</h2>

<p>Installe un module, puis dresse la liste de ses emplacements et liste les jetons qu'ils contiennent :</p>

<pre class="brush: js">function onInstalled() {
  return browser.pkcs11.getModuleSlots("my_module");
}

function onGotSlots(slots) {
  for (slot of slots) {
    console.log(`Slot: ${slot.name}`);
    if (slot.token) {
      console.log(`Contains token: ${slot.token.name}`);
    } else {
      console.log('Is empty');
    }
  }
}

browser.pkcs11.installModule("my_module")
.then(onInstalled)
.then(onGotSlots);</pre>

<p>{{WebExtExamples}}</p>
