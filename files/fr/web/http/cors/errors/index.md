---
title: CORS errors
slug: Web/HTTP/CORS/Errors
tags:
  - CORS
  - Errors
  - HTTP
  - HTTPS
  - Messages
  - Same-origin
  - Security
  - TopicStub
  - console
  - troubleshooting
translation_of: Web/HTTP/CORS/Errors
---
<div>{{HTTPSidebar}}</div>

<p><a href="/en-US/docs/Web/HTTP/CORS">Cross-Origin Resource Sharing</a> ({{Glossary("CORS")}}) </span>est une norme qui permet à un serveur d'assouplir la <a href="/en-US/docs/Web/Security/Same-origin_policy">politique de même origine</a>.</p>

<p>Celle-ci est utilisée pour autoriser explicitement certaines requêtes provenant d'autres sources tout en en rejetant d'autres. Par exemple, si un site offre un service intégrable, il peut être nécessaire d'assouplir certaines restrictions. La configuration d'une telle configuration CORS n'est pas nécessairement facile et peut présenter certains défis. Dans ces pages, nous examinerons quelques messages d'erreur CORS courants et comment les résoudre.</p>



<p>Si la configuration CORS n'est pas correctement effectuée, la console du navigateur affichera une erreur du type <code>"Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at $somesite"</code> (<code>"Requête Cross-Origin bloquée : La politique de même origine interdit la lecture de la ressource distante à $somesite"</code> en français) indiquant que la demande a été bloquée en raison d'une violation des règles de sécurité de CORS. Cependant, ce n'est pas nécessairement une erreur de configuration. Il est possible que la demande soit en fait intentionnellement refusée par l'application web de l'utilisateur et le service externe distant. Toutefois, si le terminal est destiné à être disponible, un certain débogage est nécessaire pour y parvenir.</p>

<h2 id="Identifier_le_problème">Identifier le problème</h2>

<p>Pour saisir la cause de l'erreur, il faut préalablement découvrir la requête fautive, ainsi que la configuration erronée. Ces étapes peuvent être utiles au processus:</p>

<ol>
 <li>Rendez-vous sur le site défaillant et ouvrez les <a href="/en-US/docs/Tools">Developer Tools</a>.</li>
 <li>Essayez de reproduir la requête qui échoue et vérifiez la <a href="/en-US/docs/Tools/Web_Console">console</a> pour trouver les messages de violation CORS, ce qui tournerait autours de:</li>
</ol>

<p><img alt="Firefox console showing CORS error" src="cors-error2.png"></p>

<p>Le text de l'erreur sera probablement similaire à:</p>

<pre>Cross-Origin Request Blocked: The Same Origin Policy disallows
reading the remote resource at <em>https://some-url-here</em>. (<em>Reason:
additional information here</em>).</pre>

<div class="note">
<p><strong>Note :</strong> Pour des raisons de sécurité, il <em>est impossible</em> d'analyser les causes de l'erreur CORS via JavaScript. Seule une indication de l'échec de la requête sera fournie. Il faut donc absolument regarder manuellement les messages d'erreur de la console pour débugger.</p>
</div>

<h2 id="Messages_derreur_CORS">Messages d'erreur CORS</h2>

<p>Firefox affiche les erreurs dans la console lors d'échec de requête CORS. Ce message contient entre autres un champ "reason" donnant un meilleur contexte quant à la raison de l'échec de la requête. Ces messages sont listés ci-dessous; chacun de ces liens pointent vers un article plus spécifique et contenant des pistes de solution.</p>

<ul>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSDisabled">Raison: CORS désactivé</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSDidNotSucceed">Raison: la requête CORS a échoué</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSOriginHeaderNotAdded">Raison: l'en-tête CORS ‘Origin’ ne peut pas être ajouté</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSExternalRedirectNotAllowed">Raison: Requête CORS redirection externe non autorisée</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSRequestNotHttp">Raison: Requête CORS non http</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSMissingAllowOrigin">Raison: En-tête CORS ‘Access-Control-Allow-Origin’ manquant</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSAllowOriginNotMatchingOrigin">Raison: l'en-tête CORS ‘Access-Control-Allow-Origin’ ne correspond pas à ‘xyz’</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSNotSupportingCredentials">Raison: les informations d'identification ne sont pas prises en charge si l'en-tête CORS ‘Access-Control-Allow-Origin’ est ‘*’</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSMethodNotFound">Raison: Méthode introuvable dans l'en-tête CORS 'Access-Control-Allow-Methods’</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSMissingAllowCredentials">Raison: ‘true’ attendu dans l'en-tête CORS ‘Access-Control-Allow-Credentials’</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSPreflightDidNotSucceed">Raison: Échec du canal de contrôle en amont CORS</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSInvalidAllowMethod">Raison: jeton ‘xyz’ non valide dans l'en-tête CORS ‘Access-Control-Allow-Methods’</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSInvalidAllowHeader">Raison: jeton ‘xyz’ non valide dans l'en-tête CORS ‘Access-Control-Allow-Headers’</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSMissingAllowHeaderFromPreflight">Raison: jeton ‘xyz’ manquant dans l'en-tête CORS ‘Access-Control-Allow-Headers’ du canal de contrôle en amont CORS</a></li>
 <li><a href="/en-US/docs/Web/HTTP/CORS/Errors/CORSMultipleAllowOriginNotAllowed">Raison: plusieurs en-têtes CORS ‘Access-Control-Allow-Origin’ ne sont pas autorisés</a></li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>Glossaire: {{Glossary("CORS")}}</li>
 <li><a href="/en-US/docs/Web/HTTP/CORS">CORS introduction</a></li>
 <li><a href="/en-US/docs/Web/HTTP/Server-Side_Access_Control">Paramètres CORS côté serveur</a></li>
 <li><a href="/en-US/docs/Web/HTML/CORS_enabled_image">Image compatible CORS</a></li>
 <li><a href="/en-US/docs/Web/HTML/CORS_settings_attributes">Attributs des paramètres CORS</a></li>
 <li><a href="https://www.test-cors.org">https://www.test-cors.org</a> – une page pour tester les requêtes CORS</li>
</ul>
