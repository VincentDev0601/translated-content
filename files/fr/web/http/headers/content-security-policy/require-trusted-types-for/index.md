---
title: 'CSP: require-trusted-types-for'
slug: Web/HTTP/Headers/Content-Security-Policy/require-trusted-types-for
tags:
  - CSP
  - Content-Security-Policy
  - Directive
  - HTTP
  - Security
  - Sécurité
  - TrustedTypes
  - require-trusted-types-for
  - source
translation_of: Web/HTTP/Headers/Content-Security-Policy/require-trusted-types-for
---
<div>{{HTTPSidebar}}</div>

<p>La directive HTTP {{HTTPHeader("Content-Security-Policy")}} (CSP) <code><strong>require-trusted-types-for</strong></code> {{experimental_inline}} directive informe l'agent utilisateur de contrôler les données passées au puits de fonctions XSS du DOM, tel que le mutateur <a href="/en-US/docs/Web/API/Element/innerHTML">Element.innerHTML</a>.</p>

<p>Lors de leur usage, ces fonctions n'acceptent que des valeurs typées et non falsifiables créées par des règles de Trusted Type et rejettent les chaines de caractère. Conjointement à la directive <strong><code><a href="/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/trusted-types">trusted-types</a></code></strong>, qui empêche la création de règles de Trusted Type, cette directive permet aux auteurs de définir des règles empêchant d'écrire des données dans le DOM et donc de réduire  la fenêtre de tir pour les attaques XSS sur le DOM à quelques pans isolés de la base de code d'une application, facilitant donc son contrôle et sa relecture.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre>Content-Security-Policy: require-trusted-types-for 'script';
</pre>

<dl>
 <dt><code>'script'</code></dt>
 <dd>Interdit l'usage de chaine de caractères avec les fonctions du puits d'injection XSS du DOM, et requiert que les types correspondant soient créés par des règles de Trusted Type.</dd>
</dl>

<h2 id="Exemples">Exemples</h2>

<pre class="brush: js">// Content-Security-Policy: require-trusted-types-for 'script'; trusted-types foo;

const attackerInput = '&lt;svg onload="alert(/cross-site-scripting/)" /&gt;';
const el = document.createElement('div');

if (typeof trustedTypes !== 'undefined') {
  // Create a policy that can create TrustedHTML values
  // after sanitizing the input strings with DOMPurify library.
  const sanitizer = trustedTypes.createPolicy('foo', {
    createHTML: (input) =&gt; DOMPurify.sanitize(input)
  });

  el.innerHTML = sanitizer.createHTML(attackerInput);  // Puts the sanitized value into the DOM.
  el.innerHTML = attackerInput;                        // Rejects a string value; throws a TypeError.
}
</pre>

<h2 id="Prothèse_démulaiton">Prothèse d'émulaiton</h2>

<p>Une <a href="https://github.com/w3c/webappsec-trusted-types#polyfill">prothèse d'émulation pour les Trusted Types</a> est disponible sur Github.</p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><a href="https://w3c.github.io/webappsec-trusted-types/dist/spec/">Trusted Types</a></td>
   <td>Draft</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("http.headers.csp.Content-Security-Policy.trusted-types")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{HTTPHeader("Content-Security-Policy")}}</li>
 <li><a href="/en-US/docs/Glossary/Cross-site_scripting">Cross-Site Scripting (XSS)</a></li>
 <li><a href="https://w3c.github.io/webappsec-trusted-types/dist/spec/#injection-sinks">DOM XSS injection sinks covered by Trusted Types</a></li>
 <li><a href="https://web.dev/trusted-types">Prevent DOM-based cross-site scripting vulnerabilities with Trusted Types</a></li>
 <li>Trusted Types with <a href="https://github.com/cure53/DOMPurify#what-about-dompurify-and-trusted-types">DOMPurify</a> XSS sanitizer</li>
</ul>
