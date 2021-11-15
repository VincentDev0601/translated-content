---
title: Actions du navigateur
slug: Mozilla/Add-ons/WebExtensions/Browser_actions
tags:
  - WebExtensions
translation_of: Mozilla/Add-ons/WebExtensions/Browser_actions
---
<div>{{AddonSidebar}}</div>

<p>Une action du navigateur est un bouton que vous pouvez ajouter à la barre d'outils du navigateur. Les utilisateurs peuvent cliquer sur le bouton pour interagir avec votre extension.</p>

<p><img alt="" src="browser-action.png"></p>

<p>Il existe deux façons de spécifier une action du navigateur : avec une <a href="/fr/Add-ons/WebExtensions/Popups">fenêtre contextuelle</a>, ou sans fenêtre contextuelle.</p>

<p>Si vous ne spécifiez pas de popup, alors lorsque l'utilisateur clique sur le bouton, un événement est envoyé à l'extension, que vous pouvez écouter à l'aide de <a href="/fr/Add-ons/WebExtensions/API/BrowserAction/onClicked"><code>browserAction.onClicked</code></a>:</p>

<pre class="brush: js">browser.browserAction.onClicked.addListener(handleClick);</pre>

<p>Si vous spécifiez un popup, l'événement click n'est pas distribué : au lieu de cela, le popup sera affiché lorsque l'utilisateur clique sur le bouton. L'utilisateur pourra interagir avec le popup et il se fermera automatiquement lorsque l'utilisateur clique à l'extérieur.</p>

<p>Notez que votre extension ne peut avoir qu'une seule action du navigateur.</p>

<h2 id="Specification_de_l'action_de_navigateur">Specification de l'action de navigateur</h2>

<p>Vous définissez les propriétés de l'action du navigateur - icône, titre, popup - en utilisant la clé <code><a href="/fr/Add-ons/WebExtensions/manifest.json/browser_action">browser_action</a></code> dans manifest.json:</p>

<pre class="brush: json">"browser_action": {
  "default_icon": {
    "19": "button/geo-19.png",
    "38": "button/geo-38.png"
  },
  "default_title": "Whereami?",
  "default_popup": "popup/geo.html"
}</pre>

<p>La seule clé obligatoire est <code>default_icon</code>. Vous pouvez changer n'importe laquelle de ces propriétés par programme à l'aide de l'API <code><a href="/fr/Add-ons/WebExtensions/API/browserAction">browserAction</a></code> .</p>

<h2 id="Exemples">Exemples</h2>

<p>Le repo <a href="https://github.com/mdn/webextensions-examples">webextensions-examples</a> sur GitHub contient plusieurs exemples d'extensions qui utilisent les actions du navigateur :</p>

<ul>
 <li><a href="https://github.com/mdn/webextensions-examples/blob/master/bookmark-it/">bookmark-it</a> utilise une action de navigateur sans popup</li>
 <li><a href="https://github.com/mdn/webextensions-examples/tree/master/beastify">beastify</a> utilise une action de navigateur avec une fenêtre popup</li>
</ul>
