---
title: Écriture de serveurs WebSocket
slug: Web/API/WebSockets_API/Writing_WebSocket_servers
translation_of: Web/API/WebSockets_API/Writing_WebSocket_servers
---
<p>Un serveur WebSocket est une application TCP qui écoute sur n'importe quel port d'un serveur et suit un protocole spécifique, c'est aussi simple que cela. La création de son propre serveur TCP est quelque chose qui a tendance à effrayer alors qu'il n'est pas forcément très complexe de créer un serveur WebScoket sur la plateforme de votre choix.</p>

<p>Un serveur WebSocket peut être écrit dans n'importe quel language de programmation qui supporte les "<a href="https://fr.wikipedia.org/wiki/Berkeley_sockets">Berkeley sockets</a>", par exemple C(++), python ou même PHP et JavaScript (avec nodejs). Ceci n'est pas un tutoriel destiné à un language particulier mais un guide aidant à l'écriture de votre propre serveur.</p>

<p>Avant de débuter, vous <strong>devez</strong> connaître précisément le fonctionnement du protocole HTTP et disposer d'une certaine expérience sur celui-ci. Des connaissances sur les sockets TCP dans votre langage de développement est également précieux. Ce guide ne présente ainsi que le <em>minimum</em> des connaissances requises et non un guide ultime.</p>

<div class="note">
<p><strong>Note :</strong> Lire la dernière spécification officielle sur les WebSockets <a href="http://datatracker.ietf.org/doc/rfc6455/?include_text=1">RFC 6455</a>. Les sections 1 et 4-7 sont particulièrement intéressantes pour ce qui nous occupe. La section 10 évoque la sécurité et doit être connue et mise en oeuvre avant d'exposer votre serveur au-delà du réseau local / lors de la mise en production.</p>
</div>

<p>Un serveur WebSocket est compris ici en "bas niveau" (<em>c'est-à-dire plus proche du langage machine que du langage humain</em>. Les WebSockets sont souvent séparés et spécialisés vis-à-vis de leurs homologues serveurs (pour des questions de montées en charge ou d'autres raisons), donc vous devez souvent utiliser un <a href="https://fr.wikipedia.org/wiki/Proxy_inverse">proxy inverse</a> (<em>c'est-à-dire de l'extérieur vers l'intérieur du réseau local, comme pour un serveur HTTP classique</em>) pour détecter les "poignées de mains" spécifiques au WebSocket, qui précédent l'échange et permettent d'aiguiller les clients vers le bon logiciel. Dans ce cas, vous ne devez pas ajouter à votre serveur des <em>cookies</em> et d'autres méthodes d'authentification. </p>

<h2 id="La_poignée_de_mains_du_WebSocket">La "poignée de mains" du WebSocket</h2>

<p>En tout premier lieu, le serveur doit écouter les connexions sockets entrantes utilisant le protocole TCP standard. Suivant votre plateforme, celui-ci peut déjà le faire pour vous. Pour l'exemple qui suit, nous prenons pour acquis que votre serveur écoute le domaine <em>exemple.com</em> sur le port 8000 et votre serveur socket répond aux requêtes de type GET sur le chemin <em>/chat</em>. </p>

<div class="warning">
<p><strong>Attention :</strong> Si le serveur peut écouter n'importe quel port, mais que vous décidez de ne pas utiliser un port standard (80 ou 443 pour SSL), cela peut créer en avant des problèmes avec les parefeux et/ou les proxys. De plus, gardez en mémoire que certains navigateur Web (notablement Firefox 8+), n'autorisent pas les connexions WebSocket non-SSL sur une page SSL. </p>
</div>

<p>La <em>poignée de mains</em> est la partie "Web" dans les WebSockets : c'est le pont entre le protocole HTTP et le WebSocket. Durant cette poignée, les détails (les paramètres) de la connexion sont négociés et l'une des parties peut interromptre la transaction avant la fin si l'un des termes ne lui est pas autorisé / ne lui est pas possible. Le serveur doit donc être attentif à comprendre parfaitement les demandes et attentes du client, sans quoi des procédures de sécurité seront déclenchées. </p>

<h3 id="La_requête_de_poignée_de_mains_côté_client">La requête de <em>poignée de mains</em> côté client </h3>

<p>Même si vous construisez votre serveur au profit des WebSockets, votre client doit tout de même démarrer un processus dit de <em>poignée de main</em>. Vous devez donc savoir comment interprêter cette requête. En premier, le <strong>client </strong>enverra tout d'abord une requête HTTP correctement formée. La requête <strong>doit </strong>être à la version 1.1 ou supérieure et la méthode <strong>doit </strong>être de type GET : </p>

<pre>GET /chat HTTP/1.1
Host: exemple.com:8000
<strong>Upgrade: websocket</strong>
<strong>Connection: Upgrade</strong>
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Sec-WebSocket-Version: 13

</pre>

<p>Le client peut solliciter des extensions de protocoles ou des sous-protocoles à cet instant ; voir <a href="#Miscellaneous">Miscellaneous</a> pour les détails. En outre, des en-têtes communs tel que <em>User-Agent</em>, <em>Referer</em>, <em>Cookie</em> ou des en-têtes d'authentification peuvent être envoyés par la même requête : leur usage est laissé libre car ils ne se rapportent pas directement au WebSocket et au processus de poignée de main. A ce titre il semble préférable de les ignorer : d'ailleurs dans de nombreuses configurations communes, un proxy inverse les aura finalement déjà traitées. </p>

<p>Si un des entêtes n'est pas compris ou sa valeur n'est pas correcte, le serveur devrait envoyer une réponse  "<a href="/en-US/docs/HTTP/Response_codes#400">400 Bad Request</a>" (<em>erreur 400 : la requête est incorrecte</em>) et clore immédiatement la connexion. Il peut par ailleurs indiquer la raison pour laquelle la poignée de mains a échoué dans le corps de réponse HTTP, mais le message peut ne jamais être affiché par le navigateur (<em>en somme, tout dépend du comportement du client</em>). Si le serveur ne comprend pas la version de WebSockets présentée, il doit envoyer dans la réponse un entête <em>Sec-WebSocket-Version</em> correspondant à la ou les version-s supportée-s. Ici le guide explique la version 13, la plus récente à l'heure de l'écriture du tutoriel (<em>voir le tutoriel en version anglaise pour la date exacte ; il s'agit là d'une traduction</em>). Maintenant, nous allons passer à l'entête attendu : <em>Sec-WebSocket-Key</em>.</p>

<div class="note">
<p><strong>Note :</strong> Un grand nombre de navigateurs enverront un  <a href="/en-US/docs/HTTP/Access_control_CORS#Origin"><code>Entête d'origine</code></a>. Vous pouvez alors l'utiliser pour vérifier la sécurité de la transaction (par exemple vérifier la similitude des domaines, listes blanches ou noires, etc.) et éventuellement retourner une réponse <a href="/en-US/docs/HTTP/Response_codes#403">403 Forbidden</a> si l'origine ne vous plaît pas. Toutefois garder à l'esprit que cet entête peut être simulé ou trompeur (il peut être ajouté manuellement ou lors du transfert). De nombreuses applications refusent les transactions sans celui-ci. </p>
</div>

<div class="note">
<p><strong>Note :</strong> L'URI de la requête (<code>/chat </code>dans notre cas), n'a pas de signification particulièrement dans les spécifications en usage : elle permet simplement, par convention, de disposer d'une multitude d'applications en parallèle grâce à WebSocket. Par exemple <code>exemple.com/chat</code> peut être associée à une API/une application de dialogue multiutilisateurs lorsque <code>/game</code> invoquera son homologue pour un jeu. </p>
</div>

<div class="note">
<p><strong>Note:</strong> <a href="/en-US/docs/HTTP/Response_codes">Les codes réguliers (<em>c-à-d défini par le protocole standard</em>) HTTP</a> ne peuvent être utilisés qu'<strong><em>avant</em></strong> la poignée : ceux après la poignée, sont définis d'une manière spécifique dans la section 7.4 de la documentation sus-nommée. </p>
</div>

<h3 id="La_réponse_du_serveur_lors_de_la_poignée_de_mains">La réponse du serveur lors de la poignée de mains </h3>

<p>Lorsqu'il reçoit la requête du client, le serveur doit envoyer une réponse correctement formée dans un format non-standard HTTP et qui ressemble au code ci-dessous. Gardez à l'esprit que chaque entête se termine par un saut de ligne : <em>\r\n</em> ; un saut de ligne doublé lors de l'envoi du dernier entête pour séparer du reste du corps (même si celui-ci est vide). </p>

<pre><strong>HTTP/1.1 101 Switching Protocols</strong>
Upgrade: websocket
Connection: Upgrade
<strong>Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=

</strong></pre>

<p>En sus, le serveur peut décider de proposer des extensions de protocoles ou des sous-protocoles à cet instant ; voir <a href="#Miscellaneous">Miscellaneous</a> pour les détails. L'entête Sec-WebSocket-Accept nous intéresse ici : le serveur doit la former depuis l'entête Sec-WebSocket-Key envoyée précédemment par le client. Pour l'obtenir, vous devez concaténater (<em>rassembler</em>) la valeur de <em>Sec-WebSocket-Key</em> et "<em>258EAFA5-E914-47DA-95CA-C5AB0DC85B11</em>" (valeur fixée par défaut : c'est une "<a href="https://en.wikipedia.org/wiki/Magic_string">magic string</a>") puis procéder au hash par la méthode <a href="https://en.wikipedia.org/wiki/SHA-1">SHA-1</a> du résultat et retourner le format au format <a href="https://en.wikipedia.org/wiki/Base64">base64</a>. </p>

<div class="note">
<p><strong>Note :</strong> Ce processus qui peut paraître inutilement complexe, permet de certifier que le serveur et le client sont bien sur une base WebSocket et non une requête HTTP  (qui serait alors mal interprétée). </p>
</div>

<p>Ainsi si la clé (la valeur de l'entête du client) était "<code>dGhlIHNhbXBsZSBub25jZQ==</code>", le retour (<em>Accept * dans la version d'origine du tutoriel</em>) sera : "<code>s3pPLMBiTxaQ9kYGzzhZRbK+xOo=</code>". Une fois que le serveur a envoyé les entêtes attendues, alors la poignée de mains est considérée comme effectuée et vous pouvez débuter l'échange de données ! </p>

<div class="note">
<p><strong>Note :</strong> Le serveur peut envoyer à ce moment, d'autres entêtes comme par exemple Set-Cookie, ou demander une authenficiation ou encore une redirection via les codes standards HTTP et ce <em><strong>avant </strong></em>la fin du processus de poignée de main. </p>
</div>

<h3 id="Suivre_les_clients_confirmés">Suivre les clients confirmés </h3>

<p>Cela ne concerne pas directement le protocole WebSocket, mais mérite d'être mentionné maintenant : votre serveur pourra suivre le socket client : il ne faut donc pas tenter une poignée de mains supplémentaire avec un client déjà confirmé. Un même client avec la même IP pourrait alors se connecter à de multiples reprises, mais être finalement rejeté et dénié par le serveur si les tentatives sont trop nombreuses selon les règles pouvant être édictées pour éviter les attaques dites de <a href="https://en.wikipedia.org/wiki/Denial_of_service">déni de service</a>. </p>

<h2 id="L'échange_de_trames_de_données">L'échange de trames de données </h2>

<p>Le client ou le serveur peuvent choisir d'envoyer un message à n'importe quel moment à partir de la fin du processus de poignée de mains : c'est la magie des WebSockets (une connexion permanente). Cependant, l'extraction d'informations à partir des trames de données n'est pas une expérience si... magique. Bien que toutes les trames suivent un même format spécifique, les données allant du client vers le serveur sont masquées en utilisant le <a href="https://en.wikipedia.org/wiki/XOR_cipher">cryptage XOR</a> (avec une clé de 32 bits). L'article 5 de la spécification décrit en détail ce processus. </p>

<h3 id="Format">Format</h3>

<div class="warning">
<p><strong>Attention :</strong> Dans cette partie, <code>payload </code>équivaut en bon français à <em>charge utile</em>. C'est-à-dire les données qui ne font pas partie du fonctionnement de la trame mais de l'échange entre le serveur et le client. Ainsi j'ai traduit <code>payload data comme des <em>données utiles. </em></code></p>
</div>

<p>Chaque trame (dans un sens ou dans un autre) suit le schéma suivant : </p>

<pre> <strong>0</strong>               <strong>1</strong>               <strong>2</strong>               3
 0 1 2 3 4 5 6 7 0 1 2 3 4 5 6 7 0 1 2 3 4 5 6 7 0 1 2 3 4 5 6 7
+-+-+-+-+-------+-+-------------+-------------------------------+
|F|R|R|R| opcode|M| Payload len |    Extended payload length    |
|I|S|S|S|  (4)  |A|     (7)     |             (16/64)           |
|N|V|V|V|       |S|             |   (if payload len==126/127)   |
| |1|2|3|       |K|             |                               |
+-+-+-+-+-------+-+-------------+ - - - - - - - - - - - - - - - +
 4               5               6               7
+ - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - +
|     Extended payload length continued, if payload len == 127  |
+ - - - - - - - - - - - - - - - +-------------------------------+
 8               9               <strong>10</strong>              11
+ - - - - - - - - - - - - - - - +-------------------------------+
|                               |Masking-key, if MASK set to 1  |
+-------------------------------+-------------------------------+
 12              13              <strong>14</strong>              15
+-------------------------------+-------------------------------+
| Masking-key (continued)       |          Payload Data         |
+-------------------------------- - - - - - - - - - - - - - - - +
:                     Payload Data continued ...                :
+ - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - +
|                     Payload Data continued ...                |
+---------------------------------------------------------------+</pre>

<p>RSV1-3 peuvent être ignorés, ils concernent les extensions. </p>

<p>Le masquage de bits indique simplement si le message a été codé. Les messages du client doivent être masquée, de sorte que votre serveur doit attendre qu'il soit à 1. (<em>l'article 5.1 de la spécification prévoit que votre serveur doit se déconnecter d'un client si celui-ci envoie un message non masqué</em>). Lors de l'envoi d'une trame au client, ne masquez pas et ne réglez pas le bit de masque - cela sera expliqué plus tard.</p>

<p>Note: Vous devez masquer les messages même lorsque vous utilisez un socket sécurisé.</p>

<p>Le champ <code>opcode</code> définit comment est interpêtée la <em>charge utile</em> (<code>payload data</code>) : ainsi <code>0x0</code> indique la consigne "continuer", <code>0x1</code> indique du texte (qui est systématiquement encodé en UTF-8), <code>0x2</code> pour des données binaires, et d'autres "codes de contrôle" qui seront évoqués plus tard. Dans cette version des WebSockets, <code>0x3</code> à 0x7 et <code>0xB</code> à <code>0xF</code> n'ont pas de significations particulières. </p>

<p>Le bit FIN indique si c'est le dernier message de la série [<em>NDT : pour la concaténation, pas la fin de la connexion elle-même</em>]. S'il est à 0, alors le serveur doit attendre encore une ou plusieurs parties. Sinon le message est considéré comme complet. </p>

<h3 id="Connaître_la_taille_des_données_utiles">Connaître la taille des <em>données utiles </em></h3>

<p>Pour (pouvoir) lire les <em>données utiles</em>, vous devez savoir quand arrêter la lecture dans le flux des trames entrantes vers le serveur. C'est pourquoi il est important de connaître la taille des <em>données utiles</em>. Et malheureusement ce n'est pas toujours simple. Voici quelques étapes essentielles à connaître : </p>

<ol>
 <li>(<em>étape 1</em>) Lire tout d'abord les bits 9 à 15 (inclu) et les interprêter comme un entier non-signé. S'il équivaut à 125 ou moins, alors il correspond à la taille totale de la charge utile.<br>
  S'il vaut à 126, allez à l'étape 2 ou sinon, s'il vaut 127, allez à l'étape 3. </li>
 <li>(<em>étape 2</em>) Lire les 16 bits supplémentaires et les interprêter comme précédent (entier non-signé). Vous avez alors la taille des données utiles. </li>
 <li>(<em>étape 3</em>) Lire les 64 bits supplémentaires et les interprêter comme précédent (entier non-signé). Vous avez alors la taille des données utiles. Attention, le bit le plus significatif doit rester à 0.</li>
</ol>

<h3 id="Lire_et_démasquer_les_données">Lire et démasquer les données </h3>

<p>Si le bit MASK a été fixé (et il devrait l'être, pour les messages client-serveur), vous devez lire les 4 prochains octets (32 bits) : ils sont la clé de masquage. Une fois la longueur de charge utile connue et la clé de masquage décodée, vous pouvez poursuivre la lecture des autres bits comme étant les données utiles masquées. Par convention pour le reste du paragraphe, appelons-les <em>données encodées</em>, et la clé <em>masque</em>. Pour décoder les données, bouclez les octets du texte reçu en XOR avec l'octet du (<em>i modulo 4</em>) ième octet du <em>masque</em>. En voici le pseudo-code (<em>JavaScript valide</em>) : </p>

<pre>var DECODED = "";
for (var i = 0; i &lt; ENCODED.length; i++) {
    DECODED[i] = ENCODED[i] ^ MASK[i % 4];
}</pre>

<div class="note">
<p><strong>Note :</strong> Ici la variable <code>DECODED</code> correspond aux données utiles à votre application - en fonction de l'utilisation ou non d'un sous-protocole (<em>si c'est <code>json</code>, vous devez encore décoder les données utiles reçues avec le parseur JSON</em>). </p>
</div>

<h3 id="La_fragmentation_des_messages">La fragmentation des messages </h3>

<p>Les champs FIN et opcodes fonctionnent ensemble pour envoyer un message découpé en une multitude de trames. C'est ce que l'on appele la <em>fragmentation des messages</em>. La fragmentation est seulement possible avec les opcodes de <code>0x0 </code>à <code>0x2</code>. </p>

<p>Souvenez-vous de l'intérêt de l'opcode et ce qu'il implique dans l'échange des trames. Pour <em>0x1 </em>c'est du texte, pour <em>0x2 </em>des données binaires, etc. Toutefois pour <em>0x0</em>, la frame est dite "continue" (elle s'ajoute à la précédente). En voici un exemple plus clair, où il y a en réalité deux textes de message (sur 4 trames différentes) : </p>

<pre><strong>Client:</strong> FIN=1, opcode=0x1, msg="hello"
<strong>Server:</strong> <em>(process complete message immediately) </em>Hi.
<strong>Client:</strong> FIN=0, opcode=0x1, msg="and a"
<strong>Server:</strong> <em>(listening, new message containing text started)</em>
<strong>Client:</strong> FIN=0, opcode=0x0, msg="happy new"
<strong>Server:</strong> <em>(listening, payload concatenated to previous message)</em>
<strong>Client:</strong> FIN=1, opcode=0x0, msg="year!"
<strong>Server:</strong> <em>(process complete message) </em>Happy new year to you too!</pre>

<p>La première trame dispose d'un message en entier (FIN = 1 et optcode est différent de 0x0) : le serveur peut traiter la requête reçue et y répondre. A partir de la seconde trame et pour les deux suivantes (soit trois trames), l'opcode à 0x1 puis 0x0 signifie qu'il s'agit d'un texte suivi du reste du contenu (0x1 = texte ; 0x0 = la suite). La 3e trame à FIN = 1 indique la fin de la requête. <br>
 Voir la <a href="http://tools.ietf.org/html/rfc6455#section-5.4">section 5.4</a> de la spécification pour les détails de cette partie. </p>

<h2 id="Pings-Pongs_le_coeur_des_WebSockets">Pings-Pongs : le "coeur" des WebSockets</h2>

<p>A n'importe quel moment après le processus de poignée de mains, le client ou le serveur peut choisir d'envoyer un <em>ping </em>à l'autre partie. Lorsqu'il est reçu, l'autre partie doit renvoyer dès possible un <em>pong</em>. Cette pratique permet de vérifier et de maintenir la connexion avec le client par exemple. </p>

<p>Le <em>ping </em>ou le <em>pong </em>sont des trames classiques dites <strong>de contrôle</strong>. Les <em>pings </em>disposent d'un opcode à <code>0x9</code> et les <em>pongs </em>à <code>0xA</code>. Lorsqu'un <em>ping </em>est envoyé, le <em>pong </em>doit disposer de la même donnée utile en réponse que le ping (et d'une taille maximum autorisé de 125). Le <em>pong </em>seul (c-à-d sans <em>ping</em>) est ignoré. </p>

<div class="note">
<p><strong>Note :</strong> Lorsque plusieurs pings sont envoyés à la suite, un <strong>seul </strong>pong suffit en réponse (<em>le plus récent pour la donnée utile renvoyée</em>). </p>
</div>

<h2 id="Clore_la_connexion">Clore la connexion </h2>

<p>La connexion peut être close à l'initiative du client ou du serveur grâce à l'envoi d'une trame de contrôle contenant des données spécifiques permettant d'interrompre la poignée de main (de lever définitivement le masque pour être plus précis ; voir la <a href="http://tools.ietf.org/html/rfc6455#section-5.5.1">section 5.5.1</a>). Dès la réception de la trame, le récepteur envoit une trame spécifique de fermeture en retour (pour signifier la bonne compréhension de la fin de connexion). C'est l'émetteur à l'origine de la fermeture qui doit clore la connexion ; toutes les données supplémentaires sont éliminés / ignorés. </p>

<h2 id="Diverses_informations_utiles">Diverses informations utiles</h2>

<div class="note">
<p><strong>Note :</strong> L'ensemble des codes, extensions et sous-protocoles liés aux WebSocket sont enregistrés dans le (registre) <a href="http://www.iana.org/assignments/websocket/websocket.xml">IANA WebSocket Protocol Registry</a>.</p>
</div>

<p>Les extensions et sous-protocoles des WebSockets sont négociés durant <a href="#PoignéeDeMain">l'échange des entêtes de la poignée de mains</a>. Si l'on pourrait croire qu'extensions et sous-protocles sont finalement la même chose, il n'en est rien : <strong>le contrôle des extensions agit sur les trames</strong> ce qui modifie la charge utile ; <strong>alors que les sous-protocoles modifient uniquement la charge utile,</strong> et rien d'autre. Les extensions sont optionnelles et généralisées (par exemple pour la compression des données) ; les sous-protocoles sont souvent obligatoires et ciblés (par exemple dans le cadre d'une application de chat ou d'un jeu MMORPG). </p>

<div class="warning">
<p><strong>Attention :</strong> Les sous-extensions ou les sous-protocoles ne sont pas obligatoires pour l'échange de données par WebSockets ; mais l'esprit développé ici est de rendre soit plus efficace ou sécurisée la transmission (l'esprit d'une extension) ; soit de délimiter et de normaliser le contenu de l'échange (l'esprit d'un sous-protocole ; qui étend donc le protocole par défaut des WebSockets qu'est l'échange de texte simple au format UTF-8). </p>
</div>

<h3 id="Les_extensions">Les extensions</h3>

<p>L'idée des extensions pourrait être, par exemple, la compression d'un fichier avant de l'envoyer par courriel / email à quelqu'un : les données transférées ne changent pas de contenu, mais leur format oui (et leur taille aussi...). Ce n'est donc pas le format du contenu qui change que le mode transmission - c'est le principe des extensions en WebSockets, dont le principe de base est d'être un protocole simple d'échange de données. </p>

<div class="note">
<p><strong>Note :</strong> Les extensions sont présentées et expliquées dans les sections 5.8, 9, 11.3.2, and 11.4 de la documentation sus-nommées.</p>
</div>

<h3 id="Les_sous-protocoles">Les sous-protocoles </h3>

<p>Les sous-protocoles sont à comparer à <a href="https://en.wikipedia.org/wiki/XML_schema">un schéma XML</a> ou <a href="https://en.wikipedia.org/wiki/Document_Type_Definition">une déclaration de DocType</a>. Ainsi vous pouvez utiliser seulement du XML et sa syntaxe et, imposer par le biais des sous-protocoles, son utilisation durant l'échange WebSocket. C'est l'intérêt de ces sous-protocoles : établir une structure définie (<em>et intangible : le client se voit imposer la mise en oeuvre par le serveur</em>), bien que les deux doivent l'accepter pour communiquer ensemble. </p>

<div class="note">
<p><strong>Note :</strong> Les sous-protocoles sont expliqués dans les sections 1.9, 4.2, 11.3.4, and 11.5 de la documentation sus-nommés. </p>
</div>

<p>Exemple : un client souhaite demander un sous-protocole spécifique. Pour se faire, il envoie dans les entêtes d'origine du processus de poignées de mains : </p>

<pre>GET /chat HTTP/1.1
...
Sec-WebSocket-Protocol: soap, wamp
</pre>

<p>Ou son équivalent : </p>

<pre>...
Sec-WebSocket-Protocol: soap
Sec-WebSocket-Protocol: wamp
</pre>

<p>Le serveur doit désormais choisir l'un des protocoles suggérés par le client et qu'il peut prendre en charge. S'il peut en prendre plus d'un, le premier envoyé par le client sera privilégié. Dans notre exemple, le client envoit <code>soap </code>et <code>wamp</code>, le serveur qui supporte les deux enverra donc : </p>

<pre>Sec-WebSocket-Protocol: soap
</pre>

<div class="warning">
<p><strong>Attention :</strong> Le serveur ne peut (ne doit) envoyer plus d'un entête <code>Sec-Websocket-Protocol</code>. <strong>S'il n'en supporte aucun, il ne doit pas renvoyer l'entête <code>Sec-WebSocket-Protocol</code> (l'entête vide n'est pas correct). </strong>Le client peut alors interrompre la connexion s'il n'a pas le sous-protocole qu'il souhaite (ou qu'il supporte). </p>
</div>

<p>Si vous souhaitez que votre serveur puisse supporter certains sous-protocoles, vous pourriez avoir besoin d'une application ou de scripts supplémentaires sur le serveur. Imaginons par exemple que vous utilisiez le sous-protocole json - où toutes les données échangées par WebSockets sont donc formatés suivant le format <a href="https://fr.wikipedia.org/wiki/JavaScript_Object_Notation">JSON</a>. Si le client sollicite ce sous-protocole et que le serveur souhaite l'accepter, vous <strong>devez disposer</strong> d'un parseur (d'un décodeur) JSON et décoder les données par celui-ci. </p>

<div class="note">
<p><strong>Note :</strong> Pour éviter des conflits d'espaces de noms, il est recommandé d'utiliser le sous-protocole comme un sous-domaine de celui utilisé. Par exemple si vous utilisez un sous-protocole propriétaire qui utilise un format d'échange de données non-standard pour une application de <em>chat </em>sur le domaine <em>exemple.com</em>, vous devrirez utiliser : <code>Sec-WebSocket-Protocol: chat.exemple.com</code>. S'il y a différentes versions possibles, modifiez le chemin pour faire correspondre le path à votre version comme ceci : <code>chat.exemple.com/2.0</code>. Notez que ce n'est pas obligatoire, c'est une convention d'écriture optionnel et qui peut être utilisée d'une toute autre façon.</p>
</div>

<h2 id="Contenus_associés">Contenus associés</h2>

<ul>
 <li><a href="/en-US/docs/WebSockets/Writing_WebSocket_server">Tutorial: Websocket server in C#</a></li>
 <li><a href="/en-US/docs/WebSockets/Writing_WebSocket_client_applications">Writing WebSocket client applications</a></li>
 <li><a href="/en-US/docs/WebSockets/WebSocket_Server_Vb.NET">Tutorial: Websocket server in VB.NET</a></li>
</ul>
