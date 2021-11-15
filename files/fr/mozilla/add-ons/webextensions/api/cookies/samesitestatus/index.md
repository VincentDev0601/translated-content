---
title: cookies.SameSiteStatus
slug: Mozilla/Add-ons/WebExtensions/API/cookies/SameSiteStatus
tags:
  - API
  - Add-ons
  - Cookies
  - Extensions
  - Interface
  - Non-standard
  - Reference
  - Type
  - WebExtensions
translation_of: Mozilla/Add-ons/WebExtensions/API/cookies/SameSiteStatus
---
<div>{{AddonSidebar()}}</div>

<div></div>

<p>Le type <code>SameSiteStatus</code> de l'API {{WebExtAPIRef("cookies")}} représente des informations sur l'état <code>SameSite</code> d'un cookie.</p>

<h2 id="Type">Type</h2>

<p>Les valeurs de ce type sont des chaînes de caractères. Les valeurs possibles sont :</p>

<dl>
 <dt><code>no_restriction</code></dt>
 <dd>Représente un ensemble de cookies sans attribut <code>SameSite</code>.</dd>
 <dt><code>lax</code></dt>
 <dd>Correspond au <code>SameSite=Lax</code></dd>
 <dt><code>strict</code></dt>
 <dd>Correspond à un ensemble de témoins avec <code>SameSite=Strict</code></dd>
</dl>

<p>Voir les <a href="/fr/docs/Web/HTTP/Cookies">cookies HTTP</a> pour plus d'informations.</p>
