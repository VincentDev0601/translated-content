---
title: panneaux devtools
slug: Mozilla/Add-ons/WebExtensions/user_interface/devtools_panels
tags:
  - Débutant
  - Guide
  - WebExtensions
  - interface utilisateur
translation_of: Mozilla/Add-ons/WebExtensions/user_interface/devtools_panels
original_slug: Mozilla/Add-ons/WebExtensions/user_interface/panneaux_devtools
---
<div>{{AddonSidebar}}</div>

<div class="note">
<p><strong>Note :</strong> Cette fonctionnalité deviendra disponible dans Firefox 54.</p>
</div>

<p>Lorsqu'une extension fournit des outils utiles aux développeurs, il est possible d'ajouter une interface utilisateur pour les outils de développement du navigateur en tant que nouveau panneau.</p>

<p><img src="developer_panel_tab.png"></p>

<h2 id="Spécification_d'un_panneau_d'outils_de_développement">Spécification d'un panneau d'outils de développement</h2>

<p>Un panneau d'outils de développement est ajouté à l'aide de l'API <code><a href="/fr/Add-ons/WebExtensions/API/devtools.panels">devtools.panels</a></code>, qui, à son tour, doit être exécutée à partir d'une page spéciale devtools.</p>

<p>Ajoutez la page devtools en incluant la clé <code><a href="/fr/Add-ons/WebExtensions/manifest.json/devtools_page">devtools_page</a></code> dans l'extension <a href="/fr/Add-ons/WebExtensions/manifest.json">manifest.json</a> et fournissez l'emplacement du fichier de la page HTML dans l'extension :</p>

<pre class="brush: json">"devtools_page": "devtools-page.html"</pre>

<p>Dans la page des devtools, appelez un script qui ajoutera un panneau dans devtools:</p>

<pre class="brush: html">&lt;body&gt;
  &lt;script src="devtools.js"&gt;&lt;/script&gt;
&lt;/body&gt;</pre>

<p>Dans le script, créez un panneau devtools en spécifiant le titre, l'icône et le fichier HTML du panneau qui fournit le contenu du panneau:</p>

<pre class="brush: js">function handleShown() {
  console.log("panel is being shown");
}

function handleHidden() {
  console.log("panel is being hidden");
}

browser.devtools.panels.create(
  "My Panel",           // title
  "icons/star.png",           // icon
  "devtools/panel/panel.html"          // content
).then((newPanel) =&gt; {
  newPanel.onShown.addListener(handleShown);
  newPanel.onHidden.addListener(handleHidden);
});</pre>

<p>L'extension peut maintenant exécuter un code dans la fenêtre inspectée à l'aide de <a href="/fr/Add-ons/WebExtensions/API/devtools.inspectedWindow/eval"><code>devtools</code>.inspectedWindow.eval()</a> ou en injectant un script de contenu via le script en arrière en passant un message. Vous pouvez trouver plus de détails sur la façon de procéder dans l'<a href="/fr/Add-ons/WebExtensions/Extending_the_developer_tools">Extension des outils de développement.</a></p>

<h2 id="Conception_du_panneau_de_développement">Conception du panneau de développement</h2>

<p>Pour plus de détails sur la façon de concevoir la page Web de votre panneau de développeurs pour qu'elle corresponde au style de Firefox, consultez la documentation <a href="https://design.firefox.com/photon/index.html">Photon Design System</a>.</p>

<h2 id="Icônes">Icônes</h2>

<p>Pour plus de détails sur la création d'icônes à utiliser avec votre panneau d'outils de développement, voir Iconographie dans la documentation du <a href="https://design.firefox.com/photon/index.html">Photon Design System</a>.</p>



<h2 id="Exemples">Exemples</h2>

<p>Le depot <a href="https://github.com/mdn/webextensions-examples">webextensions-examples</a> sur GitHub contient plusieurs exemples de WebExtensions qui utilisent les panneaux devtools:</p>

<ul>
 <li>
  <p><a href="https://github.com/mdn/webextensions-examples/blob/master/devtools-panels/">devtools-panels</a> utilise la création d'un panneau dans devtools</p>
 </li>
</ul>
