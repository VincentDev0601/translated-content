---
title: Authorization
slug: Web/HTTP/Headers/Authorization
tags:
  - HTTP
  - Reference
  - en-tête
  - requête
translation_of: Web/HTTP/Headers/Authorization
---
<div>{{HTTPSidebar}}</div>

<p>L'en-tête de requête HTTP <strong><code>Authorization </code></strong>contient les identifiants permettant l'authentification d'un utilisateur auprès d'un serveur, habituellement après que le serveur ait répondu avec un statut {{HTTPStatus("401")}} <code>Unauthorized</code> et l'en-tête {{HTTPHeader("WWW-Authenticate")}}</p>

<table class="properties">
 <tbody>
  <tr>
   <th scope="row">Type d'en-tête</th>
   <td>{{Glossary("Request header")}}</td>
  </tr>
  <tr>
   <th scope="row"><a href="/fr/docs/Glossaire/Forbidden_header_name">Nom d'en-tête interdit</a></th>
   <td>Non</td>
  </tr>
 </tbody>
</table>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox">Authorization: &lt;type&gt; &lt;credentials&gt;</pre>

<h2 id="Directives">Directives</h2>

<dl>
 <dt><em>&lt;type&gt;</em></dt>
 <dd><p><a href="/fr/docs/Web/HTTP/Authentication#Schéma_d'authentification">Le type d'authentification</a>. Le type <code><a href="/en-US/docs/Web/HTTP/Authentication#Basic_authentication_scheme">"Basic"</a></code> est souvent utilisé. Pour connaître les autres types :</p>
 <ul>
  <li><a href="http://www.iana.org/assignments/http-authschemes/http-authschemes.xhtml">IANA registry of Authentication schemes</a></li>
 </ul>
 </dd>
 <dt><em>&lt;credentials&gt;</em></dt>
 <dd><p>Si c'est le type d'authentification <code>"Basic"</code> qui est utilisé, les identifiants sont construits de la manière suivante :</p>
 <ul>
  <li>L'identifiant de l'utilisateur et le mot de passe sont combinés avec deux-points : (<code>aladdin:sesameOuvreToi</code>).</li>
  <li>Cette chaîne de caractères est ensuite encodée en <a href="/fr/docs/Web/API/WindowBase64/Décoder_encoder_en_base64">base64</a> (<code>YWxhZGRpbjpzZXNhbWVPdXZyZVRvaQ==</code>).</li>
 </ul>
 <div class="note">
 <p><strong>Note :</strong> L'encodage en Base64 n'est pas un chiffrement ou un hachage ! Cette méthode est aussi peu sûre que d'envoyer les identifiants en clair (l'encodage base64 est un encodage réversible). Il faudra privilégier HTTPS lorsqu'on emploie une authentification "basique".</p>
 </div>
 </dd>
</dl>

<h2 id="Exemples">Exemples</h2>

<pre>Authorization: Basic YWxhZGRpbjpvcGVuc2VzYW1l
</pre>

<p>Voir aussi l'article <a href="/fr/docs/Web/HTTP/Authentication">authentification HTTP</a> avec des exemples de configuration de serveurs Apache ou nginx pour protéger votre site grâce à un mot de passe et l'authentification HTTP basique.</p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Titre</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{RFC("7235", "Authorization", "4.2")}}</td>
   <td>HTTP/1.1 : Authentification</td>
  </tr>
  <tr>
   <td>{{RFC("7617")}}</td>
   <td>Schéma d'Authentification HTTP 'Basic'</td>
  </tr>
 </tbody>
</table>

<h2 id="Voir">Voir</h2>

<ul>
 <li><a href="/fr/docs/Web/HTTP/Authentication">L'authentification HTTP</a></li>
 <li>{{HTTPHeader("WWW-Authenticate")}}</li>
 <li>{{HTTPHeader("Proxy-Authorization")}}</li>
 <li>{{HTTPHeader("Proxy-Authenticate")}}</li>
 <li>{{HTTPStatus("401")}}, {{HTTPStatus("403")}}, {{HTTPStatus("407")}}</li>
</ul>
