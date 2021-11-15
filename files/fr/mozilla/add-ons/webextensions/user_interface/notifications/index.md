---
title: Notifications
slug: Mozilla/Add-ons/WebExtensions/user_interface/Notifications
tags:
  - WebExtensions
translation_of: Mozilla/Add-ons/WebExtensions/user_interface/Notifications
---
<div>{{AddonSidebar}}</div>

<p>Les notifications vous permettent d'afficher des informations sur votre extension ou son contenu en utilisant le système d'exploitation sous-jacent.</p>

<p><img alt="" src="notify-shadowed.png"></p>
Les notifications peuvent inclure un appel d'action pour l'utilisateur, et votre extension peut écouter l'utilisateur en cliquant sur la notification ou la fermeture de la notification.

<h2 id="Spécification_des_notifications">Spécification des notifications</h2>

<p>Vous gérez les notifications en programmant, en utilisant l'API {{WebExtAPIRef("notifications")}}. Pour utiliser cette API, vous devez demander la permission de notification dans votre manifest.json :</p>

<pre class="brush: json">"permissions": ["notifications"]</pre>

<p>Vous utilisez ensuite {{WebExtAPIRef("notifications.create")}} pour créer vos notifications, comme dans cet exemple de <a href="https://github.com/mdn/webextensions-examples/tree/master/notify-link-clicks-i18n">notify-link-clicks-i18n</a> :</p>

<pre class="brush: js">var title = browser.i18n.getMessage("notificationTitle");
var content = browser.i18n.getMessage("notificationContent", message.url);
browser.notifications.create({
  "type": "basic",
  "iconUrl": browser.extension.getURL("icons/link-48.png"),
  "title": title,
  "message": content
});</pre>

<p>Ce code crée une notification avec un icône, un titre et un message.</p>

<p>Si la notification inclut un appel à l'action, vous pouvez écouter l'utilisateur en cliquant sur la notification pour appeler la fonction pour gérer l'action:</p>

<pre class="brush: js">browser.notifications.onClicked.addListener(handleClick);</pre>

<p>Si vous émettez des appels à l'action par le biais de notifications, vous souhaitez également définir l'ID de notification facultatif, afin de déterminer quel appel à l'action a sélectionné.</p>

<h2 id="Icônes">Icônes</h2>

<p>Pour plus d'informations sur la création d'icônes à utiliser avec votre notification, reportez-vous à la section <a href="https://design.firefox.com/photon/visuals/iconography.html">Iconography</a> dans la documentation <a href="https://design.firefox.com/photon/index.html">Photon Design System</a>.</p>

<h2 id="Exemples">Exemples</h2>

<p>Le dépôt <a href="https://github.com/mdn/webextensions-examples">webextensions-examples</a> sur GitHub contient plusieurs exemples de WebExtensions qui utilise la création de notifications :</p>

<ul>
 <li><a href="https://github.com/mdn/webextensions-examples/tree/master/notify-link-clicks-i18n">notify-link-clicks-i18n</a> utilise la création de notifications.</li>
</ul>