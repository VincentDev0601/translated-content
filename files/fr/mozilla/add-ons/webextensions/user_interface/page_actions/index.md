---
title: Bouton de la barre d'adresse
slug: Mozilla/Add-ons/WebExtensions/user_interface/Page_actions
tags:
  - AddresseBarButton
  - Page Action
  - User Interface
  - WebExtensions
translation_of: Mozilla/Add-ons/WebExtensions/user_interface/Page_actions
---
<div>{{AddonSidebar}}</div>

<p>Généralement appelée <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/API/pageAction">action de page</a>, cette option d'interface utilisateur est un bouton ajouté à la barre d'adresse du navigateur. Les utilisateurs cliquent sur le bouton pour interagir avec votre extension.</p>

<p><img alt="" src="address_bar_button.png"></p>

<h2 id="Actions_de_pages_et_actions_du_navigateur">Actions de pages et actions du navigateur</h2>

<p>Le bouton de la barre d'adresse (ou action de la page) est très semblable au bouton de la barre d'outils (ou action du navigateur).</p>

<p>Les différences sont :</p>

<ul>
 <li><strong>L'emplacement du bouton :</strong>

  <ul>
   <li>L'action de la page s'affiche dans la barre d'adresse du navigateur.</li>
   <li>L'action du navigateur s'affiche en dehors de la barre d'adresse, dans la barre d'outils du navigateur.</li>
  </ul>
 </li>
 <li>La visibilité du bouton <strong>:</strong>
  <ul>
   <li>L'action page est masquée par défaut (bien que cette valeur par défaut puisse être modifiée via les propriétés <a href="/fr/Add-ons/WebExtensions/manifest.json/page_action">manifest </a>des clés <code>show_matches</code> et <code>hide_matches</code>), et vous appelez <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/API/PageAction/show"><code>pageAction.show()</code></a> et <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/API/PageAction/hide"><code>pageAction.hide()</code></a> pour l'afficher ou la masquer dans des onglets spécifiques.</li>
   <li>L'action du navigateur est toujours affichée.</li>
  </ul>
 </li>
</ul>

<p>Utilisez une action de page lorsque l'action est liée à la page en cours, et une action navigateur lorsque l'action est liée au navigateur dans son ensemble ou à trop de pages. Par exemple :</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="row">Type</th>
   <th scope="col">Bookmarks action</th>
   <th scope="col">Content action</th>
   <th scope="col">Tabs operation</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th scope="row">page action</th>
   <td>Bookmark this page</td>
   <td>Reddit enhancement</td>
   <td>Send tab</td>
  </tr>
  <tr>
   <th scope="row">browser action</th>
   <td>Show all bookmarks</td>
   <td>Enable ad-blocking</td>
   <td>Sync all open tabs</td>
  </tr>
 </tbody>
</table>



<h2 id="Spécification_de_l'action_de_la_page">Spécification de l'action de la page</h2>

<p>Vous définissez les propriétés de la clé de l'<code><a href="/fr/docs/Mozilla/Add-ons/WebExtensions/manifest.json/page_action">action de page</a></code> dans le manifest.json:</p>

<pre class="brush: json">"page_action": {
  "browser_style": true,
  "default_icon": {
    "19": "button/geo-19.png",
    "38": "button/geo-38.png"
  },
  "default_title": "Whereami?",
}</pre>

<p>La seule clé obligatoire est <code>default_icon</code>.</p>

<p>Il y a deux façons de spécifier une action de page : avec ou sans <a href="/fr/Add-ons/WebExtensions/Popups">popup</a>.</p>

<ul>
 <li><strong>Sans popup:</strong> Lorsque l'utilisateur clique sur le bouton, un événement est envoyé à l'extension, que l'extension écoute pour utiliser <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/API/pageAction/onClicked"><code>pageAction.onClicked</code></a>:</li>
 <li>
  <pre class="brush: js">browser.pageAction.onClicked.addListener(handleClick);</pre>
 </li>
 <li><strong>Avec un popup:</strong> L'événement <code>click</code> n'est pas envoyé. Au lieu de cela, le popup apparaît lorsque l'utilisateur clique sur le bouton. L'utilisateur interagit alors avec le popup. Lorsque l'utilisateur clique à l'extérieur de la fenêtre contextuelle, celle-ci se ferme automatiquement. Voir l'article <a href="/fr/Add-ons/WebExtensions/Popups">Popup </a>pour plus de détails sur la création et la gestion des popups.</li>
</ul>

<p>Notez que votre extension ne peut avoir qu'une seule page action.</p>

<p>Vous pouvez modifier l'une des propriétés d'action de la page de manière programmée en utilisant l'API de la <code><a href="/fr/docs/Mozilla/Add-ons/WebExtensions/API/pageAction">pageAction</a></code>.</p>

<h2 id="Icônes">Icônes</h2>

<p>Pour plus de détails sur la création d'icônes à utiliser avec l'action de votre page, voir   <a href="https://design.firefox.com/photon/visuals/iconography.html">Iconography</a> dans la documentation du <a href="https://design.firefox.com/photon/index.html">Photon Design System</a>.</p>



<h2 id="Exemples">Exemples</h2>

<p>Le dépôt <a href="https://github.com/mdn/webextensions-examples">webextensions-examples</a> sur GitHub contient plusieurs exemples de WebExtensions qui utilisent la page action :</p>

<ul>
 <li><a href="https://github.com/mdn/webextensions-examples/tree/master/chill-out">chill-out</a> utilise une action de navigateur sans popup</li>
</ul>
