---
title: Travailler avec userScripts
slug: Mozilla/Add-ons/WebExtensions/API/userScripts/Working_with_userScripts
tags:
  - API
  - Extensions
  - How-to
  - Tutorial
  - userScripts
translation_of: Mozilla/Add-ons/WebExtensions/API/userScripts/Working_with_userScripts
original_slug: Mozilla/Add-ons/WebExtensions/API/userScripts/travailler_avec_userScripts
---
<p>{{draft}}</p>

<p>{{AddonSidebar}}</p>

<p>En implémentant userScripts, les développeurs d'extension peuvent modifier l'apparence et/ou le fonctionnement des sites pour mieux répondre aux besoins des utilisateurs.</p>

<p>Implémentez userScripts dans votre extension en suivant les étapes suivantes :</p>

<ol>
 <li>Définissez le script dans le manifeste de l'extension à l'aide de la clé <code>"user_scripts"</code>.</li>
 <li>Enregistrer le userScript</li>
 <li>Implémenter les fonctions userScript</li>
</ol>

<p>Passons en revue les processus à l'aide d'un petit exemple d'extension Web qui illustre le processus. L'exemple est disponible dans le dépôt <a href="https://github.com/mdn/webextensions-examples">webextensions-examples</a> sur GitHub.</p>

<h2 id="Manifest_userScripts">Manifest userScripts</h2>

<p>Un script utilisateur est identifié par le contenu de la clé <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/manifest.json/user_scripts">user_scripts</a> du manifeste des extensions. L'information minimale pour la clé <code>user_scripts</code> serait :</p>

<pre class="brush: json">  "user_scripts": {
    "api_script": "customUserScriptAPIs.js"
  }</pre>

<p>La propriété "api_script" indique le chemin d'accès au fichier JavaScript qui contient le code du <code>userScript</code>.</p>

<h2 id="Charge_lextension_dexemple">Charge l'extension d'exemple</h2>

<p>Une fois que vous avez téléchargé l'exemple  :</p>

<p>Naviguez jusqu'à about:debugging, cliquez sur <strong>Charger temporairement une extension... </strong>et double-cliquez sur le manifest des extensions.</p>

<p>/Le code par défaut inclus dans l'exemple vous permet de charger un <code>userScript</code> qui va "manger" le contenu des pages correspondant à l'entrée Hosts. Effectuez tous les changements que vous voulez faire avant de cliquer sur le bouton <strong>Enregistrer le script</strong> au bas du panneau.</p>

<p>Dans l'image suivante, l'extension va "manger" le contenu des pages dont le nom de domaine se termine par.org. C'est le comportement par défaut pour cette extension.</p>

<p><img alt="" src="userScriptExample.png"></p>

<p>Rien ne se passera tant que vous n'aurez pas cliqué sur le bouton <strong>Enregistrer le script</strong>. Le bouton implémente le script utilisateur en fonction des paramètres de cette boîte de dialogue. Cela signifie que vous pouvez expérimenter le comportement du script sans avoir à implémenter une extension vous-même.</p>

<h2 id="Register_the_userScript">Register the userScript</h2>

<p>Avant qu'un userScript puisse être exécuté, il doit être enregistré en utilisant la méthode  <code>userScripts.register()</code>. Voici le code pour enregistrer l'extension d'exemple :</p>

<pre class="brush: js">async function registerScript() {
  const params = {
    hosts: stringToArray(hostsInput.value),
    code: codeInput.value,
    excludeMatches: stringToArray(excludeMatchesInput.value),
    includeGlobs: stringToArray(includeGlobsInput.value),
    excludeGlobs: stringToArray(excludeGlobsInput.value),
    runAt: runAtInput.value,
    matchAboutBlank: stringToBool(matchAboutBlankInput.value),
    allFrames: stringToBool(allFramesInput.value),
    scriptMetadata: {name: scriptNameInput.value || null},
  };

  // Store the last submitted values to the extension storage
  // (so that they can be restored when the popup is opened
  // the next time).
  await browser.storage.local.set({
    lastSetValues: params,
  });

  try {
    // Clear the last userScripts.register result.
    lastResultEl.textContent = "";

    await browser.runtime.sendMessage(params);
    lastResultEl.textContent = "UserScript successfully registered";
    // Clear the last userScripts.register error.
    lastErrorEl.textContent = "";

    // Clear the last error stored.
    await browser.storage.local.remove("lastError");
  } catch (e) {
    // There was an error on registering the userScript,
    // let's show the error message in the popup and store
    // the last error into the extension storage.

    const lastError = `${e}`;
    // Show the last userScripts.register error.
    lastErrorEl.textContent = lastError;

    // Store the last error.
    await browser.storage.local.set({lastError});
  }
}</pre>

<p>Ce code initialise d'abord l'objet params pour passer les valeurs à la méthode  <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/API/userScripts/register">userScripts.register</a>.</p>

<h2 id="Implementer_les_fonctions_userScript">Implementer les fonctions userScript</h2>

<p>Une fois le script enregistré, naviguez vers une page dont le nom de domaine se termine par .org, et vous verrez quelque chose comme ceci :</p>

<p><img alt="" src="user_script_in_action.png"></p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{WebExtAPIRef("userScripts")}}</li>
 <li>{{WebExtAPIRef("userScripts.register()", "userScripts.register()")}}</li>
 <li>{{WebExtAPIRef("userScripts.onBeforeScript")}}</li>
</ul>
