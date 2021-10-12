---
title: Redirections en HTTP
slug: Web/HTTP/Redirections
tags:
  - Guide
  - HTTP
  - redirections
translation_of: Web/HTTP/Redirections
---
<div>{{HTTPSidebar}}</div>

<div>La redirection d'URL est une technique pour donner à une page, un formulaire ou une application Web entière, plus d'une adresse. HTTP fournit un type particulier de réponses, les <em><strong>redirections HTTP</strong></em>, pour effectuer cette opération utilisée pour de nombreux objectifs : redirection temporaire pendant la maintenance du site, redirection permanente pour que les liens externes continuent de fonctionner après un changement d'architecture du site, pages de progression lors du téléchargement d'un fichier, etc.</div>

<h2 id="Principe">Principe</h2>

<p>En HTTP, une redirection est déclenchée par le serveur en envoyant des réponses spéciales à une requête : <em>les redirections</em>. Les redirections HTTP sont des réponses avec un code d'état de <code>3xx</code>. Un navigateur, lorsqu'il reçoit une réponse de redirection, utilise la nouvelle URL fournie et la charge immédiatement : la plupart du temps, la redirection est transparente pour l'utilisateur, si ce n'est un petit impact de performance.</p>

<p><img alt="" src="httpredirect.png"></p>

<p>Il existe plusieurs types de redirections et elles se répartissent en trois catégories : les redirections permanentes, les temporaires et les spéciales.</p>

<h3 id="Redirections_permanentes">Redirections permanentes</h3>

<p>Ces redirections sont faites pour durer éternellement. Elles impliquent que l'URL d'origine ne doit plus être utilisée et que la nouvelle URL est préférée. Les robots des moteurs de recherche déclenchent une mise à jour de l'URL associée à la ressource dans leurs index.</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Code</th>
   <th scope="col">Texte</th>
   <th scope="col">Traitement des méthodes</th>
   <th scope="col">Cas d'utilisation typique</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>301</code></td>
   <td><code>Moved Permanently</code></td>
   <td>Requêtes {{HTTPMethod("GET")}} inchangées.<br>
    Les autres peuvent être changés ou non en {{HTTPMethod("GET")}}.</td>
   <td>Réorganisation d'un site Web.</td>
  </tr>
  <tr>
   <td><code>308</code></td>
   <td><code>Permanent Redirect</code></td>
   <td>Méthode et corps de la requête inchangés.</td>
   <td>Réorganisation d'un site Web, avec des liens/opérations non-GET.</td>
  </tr>
 </tbody>
</table>

<p>La spécification n'avait pas l'intention de permettre des changements de méthode, mais il y a en pratique des agents utilisateurs qui le font. <code>308</code> a été créé pour supprimer l'ambiguïté du comportement lors de l'utilisation de méthodes autres que <code>GET</code>.</p>

<h3 id="Redirections_temporaires">Redirections temporaires</h3>

<p>Parfois, la ressource demandée ne peut pas être accédée à partir de son emplacement standard, mais elle peut l'être à partir d'un autre endroit. Dans ce cas, une redirection temporaire peut être utilisée. Les robots des moteurs de recherche ne mémorisent pas le nouveau lien temporaire. Les redirections temporaires sont également utilisées lors de la création, de la mise à jour et de la suppression de ressources pour présenter des pages de progression temporaires.</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Code</th>
   <th scope="col">Texte</th>
   <th scope="col">Traitement des méthodes</th>
   <th scope="col">Cas d'utilisation typique</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>302</code></td>
   <td><code>Found</code></td>
   <td>Requêtes {{HTTPMethod("GET")}} inchangées.<br>
    Les autres peuvent être changés ou non en {{HTTPMethod("GET")}}.</td>
   <td>La page Web n'est temporairement pas disponible pour des raisons qui n'ont pas été imprévues. De cette façon, les moteurs de recherche ne mettent pas à jour leurs liens.</td>
  </tr>
  <tr>
   <td><code>303</code></td>
   <td><code>See Other</code></td>
   <td>Requêtes {{HTTPMethod("GET")}} inchangées.<br>
    Les autres sont changées en <code>GET</code> (le corps est perdu).</td>
   <td>Utilisé pour rediriger après un {{HTTPMethod("PUT")}} ou un {{HTTPMethod("POST")}} pour empêcher un rafraîchissement de la page qui redéclencherait l'opération.</td>
  </tr>
  <tr>
   <td><code>307</code></td>
   <td><code>Temporary Redirect</code></td>
   <td>Méthodes et corps inchangés</td>
   <td>La page Web n'est temporairement pas disponible pour des raisons qui n'ont pas été imprévues. De cette façon, les moteurs de recherche ne mettent pas à jour leurs liens. Mieux que <code>302</code> lorsque des liens/opérations non-GET sont disponibles sur le site.</td>
  </tr>
 </tbody>
</table>

<p>La spécification n'avait pas l'intention de permettre des changements de méthode, mais il y a en pratique des agents utilisateurs qui le font. <code>307</code> a été créé pour supprimer l'ambiguïté du comportement lors de l'utilisation de méthodes autres que <code>GET</code></p>

<h3 id="Redirections_spéciales">Redirections spéciales</h3>

<p>En plus de ces redirections habituelles, il existe deux redirections spécifiques. Le {{HTTPStatus("304")}} (Not Modified) redirige une page vers la copie mise en cache localement (qui était obsolète), et le {{HTTPStatus("300")}} (Multiple Choice) est une redirection manuelle : le corps, présenté par le navigateur comme une page Web, liste les redirections possibles et l'utilisateur clique sur une pour la sélectionner.</p>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Code</th>
   <th scope="col">Texte</th>
   <th scope="col">Cas d'utilisation typique</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>300</code></td>
   <td><code>Multiple Choice</code></td>
   <td>Pas beaucoup : les choix sont listés dans une page HTML dans le corps du texte. Pourrait être servi avec un {{HTTPStatus("200")}} <code>OK</code> status.</td>
  </tr>
  <tr>
   <td><code>304</code></td>
   <td><code>Not Modified</code></td>
   <td>Rafraîchissement du cache : ceci indique que la valeur dans le cache est encore correcte et peut être utilisée.</td>
  </tr>
 </tbody>
</table>

<h2 id="Autre_façon_de_spécifier_les_redirections">Autre façon de spécifier les redirections</h2>

<p>Les redirections HTTP ne sont pas les seuls moyens de définir des redirections. Il existe deux autres méthodes: les redirections HTML en utilisant l'élément {{HTMLElement("meta")}}, et les redirections JavaScript en utilisant le <a href="/en-US/docs/Web/API/Document_Object_Model">DOM</a>.</p>

<h3 id="Redirections_HTML">Redirections HTML</h3>

<p>Les redirections HTTP sont le moyen privilégié de créer des redirections, mais parfois le développeur Web n'a pas le contrôle du serveur ou ne peut pas le configurer. Pour ces cas spécifiques, les développeurs Web peuvent créer une page HTML avec un élément {{HTMLElement("meta")}} et son attribut {{htmlattrxref("http-equiv", "meta")}} avec la valeur <code>refresh</code>, positionné dans le {{HTMLElement("head")}} de la page. Lors de l'affichage de la page, le navigateur trouvera cet élément et ira à la page indiquée.</p>

<pre class="brush: html">&lt;head&gt;
  &lt;meta http-equiv="refresh" content="0; URL=http://www.example.com/" /&gt;
&lt;/head&gt;
</pre>

<p>L'attribut {{htmlattrxref("content")}} commence avec un nombre indiquant combien de secondes le navigateur doit attendre avant de rediriger vers l'URL fournie. Toujours le mettre à 0, pour une meilleure accessibilité.</p>

<p>Bien entendu, cette méthode ne fonctionne qu'avec des pages HTML (ou similaires) et ne peut être utilisée pour des images ou tout autre type de contenu.</p>

<div class="note">
<p><strong>Note :</strong> Ces redirections cassent le bouton de retour dans un navigateur : vous pouvez revenir à une page avec cet en-tête mais mais vous serez de nouveau instantanément rediriger.</p>
</div>

<h3 id="Redirections_JavaScript">Redirections JavaScript</h3>

<p>Les redirections en JavaScript se créent en définissant une valeur pour la propriété {{domxref("window.location")}} et la nouvelle page est alors chargée.</p>

<pre class="brush: js">window.location = "http://www.example.com/";</pre>

<p>Comme les redirections HTML, cela ne fonctionne pas sur toutes les ressources, et évidemment, cela ne marchera que pour les clients qui exécutent du JavaScript. D'un autre côté, il y a plus de possibilités car vous ne pouvez déclencher la redirection que si certaines conditions sont remplies, par exemple.</p>

<h3 id="Ordre_de_priorité">Ordre de priorité</h3>

<p>Avec trois possibilités de redirections d'URL, plusieurs méthodes peuvent être spécifiées en même temps, mais laquelle est appliquée en premier ? L'ordre de priorité est le suivant:</p>

<ol>
 <li>Les redirections HTTP sont toujours exécutées en premier, alors même que la page n'est pas transmise, et ni même lue.</li>
 <li>Les redirections HTML ({{HTMLElement("meta")}}) sont exécutées are executed s'il n'y avait pas de redirections HTTP.</li>
 <li>Les redirections JavaScript sont utilisées en dernier recours, et uniquement si JavaScript est activé côté client.</li>
</ol>

<p>Dans la mesure du possible, utilisez des redirections HTTP, et n'ajoutez pas d'élément {{HTMLElement("meta")}} de redirection. Si quelqu'un change les redirections HTTP et oublie de changer les redirections HTML, les redirections ne seront plus identiques, ce qui pourrait causer une boucle infinie ou d'autres cauchemars.</p>

<h2 id="Cas_dutilisation">Cas d'utilisation</h2>

<p>Il existe de nombreux cas d'utilisation pour les redirections, mais comme les performances sont affectées par chaque redirection, leur utilisation doit être réduite au minimum.</p>

<h3 id="Alias_de_domaine">Alias de domaine</h3>

<p>Idéalement, il n'y a qu'un seul emplacement, et donc qu'une seule URL pour une seule ressource. Mais il existe plein de raisons de vouloir des noms alternatifs pour une même ressource (plusieurs domaines, comme avec et sans le préfixe www ou des URLs plus courtes et faciles à retenir, ....). Dans ces cas, plutôt que de dupliquer la ressource, il est utile d'utiliser une redirection vers la vraie URL (canonique).</p>

<p>Un alias de domaine peut être fait pour plusieurs raisons:</p>

<ul>
 <li>Élargir la portée de votre site. Un cas courant est celui où votre site se trouve sous le domaine <code>www.example.com</code> et où l'accès à vos pages à partir de <code>example.com</code> devrait également être possible. Dans ce cas, des redirections vers <code>www.example.com</code> sont mises en place, pour les pages de <code>example.com</code>. Vous pouvez également fournir des noms synonymes couramment utilisés ou des fautes de frappe fréquentes de vos noms de domaine.</li>
 <li>Passer à un autre domaine. Par exemple, votre société a été renommée et lorsqu'on recherche l'ancien nom, vous voulez que les gens habitués à l'ancien site Web de la société vous trouvent sous le nouveau nom.</li>
 <li>Forcer HTTPS. Les requêtes vers la version HTTP non sécurisée de votre site seront redirigées vers la version HTTPS de votre site.</li>
</ul>

<h3 id="Maintenir_les_liens_en_vie">Maintenir les liens en vie</h3>

<p>Lorsque vous restructurez des sites Web, les URL des ressources changent. Même si vous pouvez mettre à jour les liens internes de votre site Web pour qu'ils correspondent au nouveau schéma de nommage, vous n'avez aucun contrôle sur les URL utilisées par les ressources externes. Vous ne voulez pas briser ces liens, car ils vous apportent des utilisateurs précieux (et aident votre référencement), donc vous configurez des redirections depuis les anciennes URL vers les nouvelles.</p>

<div class="note">
<p><strong>Note :</strong> Même si cette technique fonctionne également pour les liens internes, vous devriez éviter d'avoir des redirections internes. Une redirection a un coût significatif sur les performances (car une requête HTTP supplémentaire est faite) et si vous pouvez l'éviter en corrigeant les liens internes, vous devez corriger ces liens.</p>
</div>

<h3 id="Réponses_temporaires_aux_requêtes_non_sécurisées">Réponses temporaires aux requêtes non sécurisées</h3>

<p>Les requêtes {{Glossary("safe", "Unsafe")}} modifient l'état du serveur et l'utilisateur ne devrait pas les rejouer par inadvertance. Typiquement, vous ne voulez pas que vos utilisateurs renvoient des requêtes {{HTTPMethod("PUT")}}, {{HTTPMethod("POST")}} ou {{HTTPMethod("DELETE")}}. Si vous ne vous contentez que d'envoyer la réponse à la suite de cette requête, une simple clic sur le bouton de rechargement (éventuellement après un message de confirmation), renvoie la demande.</p>

<p>Dans ce cas, le serveur peut renvoyer une réponse {{HTTPStatus("303")}} (See Other) qui contiendra les bonnes informations, mais si le bouton de rechargement est pressé, seule cette page est réaffichée, sans rejouer les demandes non sécurisées.</p>

<h3 id="Réponses_temporaires_aux_longues_requêtes">Réponses temporaires aux longues requêtes</h3>

<p>Certaines requêtes peuvent nécessiter plus de temps sur le serveur comme parfois des requêtes {{HTTPHeader("DELETE")}} qui sont planifiés pour un traitement ultérieur. Dans ce cas, la réponse est un {{HTTPStatus("303")}} (See Other) qui renvoie à une page indiquant que l'action a été programmée, et informe éventuellement de l'avancement de l'action, ou permet de l'annuler.</p>

<h2 id="Configuration_des_redirections_dans_les_serveurs_les_plus_courants">Configuration des redirections dans les serveurs les plus courants</h2>

<h3 id="Apache">Apache</h3>

<p>Les redirections peuvent être définies soit dans le fichier de configuration du serveur, soit dans le fichier <code>.htaccess</code> de chaque répertoire.</p>

<p>Le module <a href="https://httpd.apache.org/docs/current/mod/mod_alias.html">mod_alias</a> a des directives <code>Redirect</code> et <code>RedirectMatch</code> qui définissent une réponse {{HTTPStatus("302")}} (par défaut):</p>

<pre>&lt;VirtualHost *:80&gt;
	ServerName example.com
	Redirect / http://www.example.com
&lt;/VirtualHost&gt;
</pre>

<p>L'URL <code>http://example.com/</code> sera redirigée vers <code>http://www.example.com/</code>, ainsi que les fichiers ou répertoires qui s'y trouvent (<code>http://example.com/index.html</code> sera redirigée vers <code>http://www.example.com/index.html</code>)</p>

<p><code>RedirectMatch</code> fait la même chose mais prend une expression régulière pour définir une liste d'URLs concernées:</p>

<pre>RedirectMatch ^/images/(.*)$ http://images.example.com/$1</pre>

<p>Tous les documents dans le répertoire <code>images/</code> seront redirigés vers un autre domaine.</p>

<p>Si vous ne souhaitez pas configurer une redirection temporaire, un paramètre supplémentaire (soit le code d'état HTTP à utiliser, soit le mot clé <code>permanent</code>) peut être utilisé pour configurer un autre type de redirection:</p>

<pre>Redirect permanent / http://www.example.com
Redirect 301 / http://www.example.com
</pre>

<p>Le module <a href="http://httpd.apache.org/docs/current/mod/mod_rewrite.html">mod_rewrite</a> peut également être utilisé pour créer des redirections. Il est plus flexible, mais un peu plus complexe à utiliser.</p>

<h3 id="Nginx">Nginx</h3>

<p>Dans Nginx, vous créez un bloc <code>server</code> spécifique pour le contenu que vous voulez rediriger:</p>

<pre>server {
	listen 80;
	server_name example.com;
	return 301 $scheme://www.example.com$request_uri;
}</pre>

<p>Pour appliquer une redirection pour un dossier ou un sous-ensemble de pages uniquement, utilisez la directive <code>rewrite</code>:</p>

<pre>rewrite ^/images/(.*)$ http://images.example.com/$1 redirect;
rewrite ^/images/(.*)$ http://images.example.com/$1 permanent;
</pre>

<h3 id="IIS">IIS</h3>

<p>Dans IIS, vous devez utiliser l'élément <code><a href="https://www.iis.net/configreference/system.webserver/httpredirect">&lt;httpRedirect&gt;</a></code> pour configurer les redirections.</p>

<h2 id="Boucles_de_redirection">Boucles de redirection</h2>

<p>Les boucles de redirection se produisent lorsque lorsque les redirections se succèdent en suivant celle déjà effectuée. En d'autres termes, il y a une boucle qui ne terminera jamais et aucune page ne sera finalement trouvée.</p>

<p>La plupart du temps, il s'agit d'un problème de serveur, et si le serveur ne peut pas le détecter, il renvoie le message {{HTTPStatus("500")}} <code>Internal Server Error</code>. Si vous rencontrez une telle erreur peu après avoir modifié une configuration de serveur, il s'agit probablement d'une boucle de redirection.</p>

<p>Parfois, le serveur ne le détecte pas : une boucle de redirection peut s'étendre sur plusieurs serveurs qui n'ont pas une vue globale de ce qui se passe. Dans ce cas, les navigateurs le détecteront et afficheront un message d'erreur. Firefox affichera:</p>

<pre>Firefox a détecté que le serveur redirige la demande pour cette adresse d'une manière qui n'aboutira pas.
</pre>

<p>tandis que Chrome affichera:</p>

<pre>Cette page Web présente une boucle de redirection</pre>

<p>Dans les deux cas, l'utilisateur ne peut pas faire grand-chose (à moins qu'une corruption ne se produise de son côté, comme une inadéquation du cache ou des cookies).</p>

<p>Il est important d'éviter les boucles de redirection car elles perturbent complètement l'expérience utilisateur.</p>
