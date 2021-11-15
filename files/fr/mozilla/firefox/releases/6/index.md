---
title: Firefox 6 pour les développeurs
slug: Mozilla/Firefox/Releases/6
tags:
  - Firefox
  - Firefox 6
translation_of: Mozilla/Firefox/Releases/6
original_slug: Mozilla/Firefox/Versions/6
---
<div>
  <ol>
    <li>
        
            <p>Notes de versions pour développeurs</p>
            <ol>
              <li><a href="/fr/docs/Mozilla/Firefox/Releases">Notes de versions pour développeurs</a></li>
            </ol>
        
    </li>
    <li>
        
            <p>Modules complémentaires</p>
            <ol>
              <li><a href="/fr/Add-ons/WebExtensions">WebExtensions</a></li>
              <li><a href="/fr/Add-ons/Themes">Thèmes</a></li>
            </ol>
        
    </li>
    <li>
        
            <p>Fonctionnement interne de Firefox</p>
            <ol>
              <li><a href="/fr/docs/Mozilla/">Le projet Mozilla</a></li>
              <li><a href="/fr/docs/Mozilla/Gecko">Gecko</a></li>
              <li><a href="/fr/docs/Mozilla/Firefox/Headless_mode">Mode « headless »</a></li>
              <li><a href="/fr/docs/Mozilla/JavaScript_code_modules">Modules de code Javascript</a></li>
              <li><a href="/fr/docs/Mozilla/js-ctypes">JS-ctypes</a></li>
              <li><a href="/fr/docs/Mozilla/MathML_Project">Le projet MathML</a></li>
              <li><a href="/fr/docs/Mozilla/MFBT">MFBT</a></li>
              <li><a href="/fr/docs/Mozilla/Projects">Les projets Mozilla</a></li>
              <li><a href="/fr/docs/Mozilla/Preferences">Le système de préférences</a></li>
              <li><a href="/fr/docs/Mozilla/WebIDL_bindings">Connexions WebIDL</a></li>
              <li><a href="/fr/docs/Mozilla/Tech/XPCOM">XPCOM</a></li>
              <li><a href="/fr/docs/Mozilla/Tech/XUL">XUL</a></li>
            </ol>
        
    </li>
    <li>
        
            <p>Développer et contribuer</p>
            <ol>
              <li><a href="/fr/docs/Mozilla/Developer_guide/Build_Instructions">Instructions de compilation</a></li>
              <li><a href="/fr/docs/Mozilla/Developer_guide/Build_Instructions/Configuring_Build_Options">Configuration des options de compilation</a></li>
              <li><a href="/fr/docs/Mozilla/Developer_guide/Build_Instructions/How_Mozilla_s_build_system_works">Fonctionnement de la compilation</a></li>
              <li><a href="/fr/docs/Mozilla/Developer_guide/Source_Code/Mercurial">Code source de Mozilla</a></li>
              <li><a href="/fr/docs/Mozilla/Localization">Localisation</a></li>
              <li><a href="/fr/docs/Mozilla/Mercurial">Mercurial</a></li>
              <li><a href="/fr/docs/Mozilla/QA">Assurance qualité</a></li>
              <li><a href="/fr/docs/Mozilla/Using_Mozilla_code_in_other_projects">Utilisation de code Mozilla dans d'autres projets</a></li>
            </ol>
        
    </li>
  </ol>
</div>
<p>Firefox 6, basé sur Gecko 6.0, est sorti le 16 août 2011. Cet article fournit des informations à propos des changements qui affectent les développeurs dans cette version.</p>

<h2 id="Changements_pour_les_développeurs_web">Changements pour les développeurs web</h2>

<h3 id="HTML">HTML</h3>

<ul>
 <li>L'élément HTML5 <a href="/fr/docs/Web/HTML/Element/progress"><code>&lt;progress&gt;</code></a>, qui vous permet de créer une barre de progression, est maintenant supporté.</li>
 <li>L'analyse syntaxique de l'élément HTML5 <a href="/fr/docs/Web/HTML/Element/track"><code>&lt;track&gt;</code></a>, qui spécifie les pistes de texte pour les éléments multimédias, est désormais supporté. Cet élément devrait apparaître dans les DOM, si son comportement n'est pas encore implémenté.</li>
 <li>L'élément <a href="/fr/docs/Web/HTML/Element/iframe"><code>&lt;iframe&gt;</code></a> est désormais correctement coupé par son conteneur lorsque les coins du conteneur ont été arrondis à l'aide de la propriété <a href="/fr/docs/Web/CSS/border-radius"><code>border-radius</code></a>.</li>
 <li>Les champs <a href="/fr/docs/Web/HTML/Element/input"><code>&lt;input&gt;</code></a> des éléments <a href="/fr/docs/Web/HTML/Element/form"><code>&lt;form&gt;</code></a> ne sont plus supportés par la propriété XUL <code><a href="/fr/docs/XUL/Propriétés/maxwidth">maxwidth</a></code>, cela n'a jamais été volontaire, et est contraire à la spécification HTML. Vous devriez plutôt utiliser l'attribut <code><a href="/fr/docs/Web/HTML/Element/input#attr-size">size</a></code> pour définir la largeur maximum de champs de saisie.</li>
 <li>Les propriétés <code>fillStyle</code> et <code>strokeStyle</code> de <a href="/fr/docs/Web/API/CanvasRenderingContext2d"><code>CanvasRenderingContext2d</code></a> (<a href="/fr/docs/Web/HTML/Element/canvas"><code>&lt;canvas&gt;</code></a>) utilisées pour ignorer les déchets inclus après la définition d'une couleur valide, maintenant c'est traité comme une erreur. Par exemple, "rouge bleu" est une couleur utilisée pour être traitée comme du "rouge", alors qu'elle aurait dû être ignorée.</li>
 <li>La largeur et la hauteur des éléments <a href="/fr/docs/Web/HTML/Element/canvas"><code>&lt;canvas&gt;</code></a> peuvent être correctement mis à 0px ; avant, lorsque vous essayez de le faire, elles se fixaient à 300px.</li>
 <li>le support de l'attribut HTML <a href="/fr/docs/HTML/Global_attributes#attr-data-*">des données personnalisées</a> (data-*) a été ajouté. La propriété DOM <a href="/fr/docs/Web/API/Element/dataset"><code>element.dataset</code></a> permet d'y accéder.</li>
 <li>Quand un élément <a href="/fr/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code></a> reçoit le focus, le point d'insertion de texte est désormais placé, par défaut, au début du texte plutôt qu'à la fin. Le comportement de Firefox est ainsi conforme avec les autres navigateurs.</li>
</ul>

<h3 id="CSS">CSS</h3>

<dl>
 <dt><a href="/fr/docs/Web/CSS/text-decoration-color"><code>-moz-text-decoration-color</code></a></dt>
 <dd>Cette nouvelle propriété vous permet de définir la couleur utilisée par les décorations du texte, comme le soulignement, le surlignement et le texte barré.</dd>
 <dt><a href="/fr/docs/Web/CSS/text-decoration-line"><code>-moz-text-decoration-line</code></a></dt>
 <dd>Cette nouvelle propriété vous permet de définir le type de décorations du texte ajoutée à un élément.</dd>
 <dt><a href="/fr/docs/Web/CSS/text-decoration-style"><code>-moz-text-decoration-style</code></a></dt>
 <dd>Cette nouvelle propriété vous permet de définir le style de décorations du texte, comme le soulignement, le surlignement et le texte barré. Les styles incluent les simples lignes, les lignes doubles, les lignes ondulées, les lignes pointillées, etc.</dd>
 <dt><a href="/fr/docs/Web/CSS/hyphens"><code>-moz-hyphens</code></a></dt>
 <dd>Cette nouvelle propriété vous permet de contrôler la façon dont la césure des mots lors de retours à la ligne est gérée.</dd>
 <dt><a href="/fr/docs/Web/CSS/orient"><code>-moz-orient</code></a></dt>
 <dd>Une nouvelle propriété (pour l'instant spécifique à Mozilla) qui vous permet de contrôler l'orientation verticale ou horizontale de certains éléments (en particulier <a href="/fr/docs/Web/HTML/Element/progress"><code>&lt;progress&gt;</code></a>).</dd>
 <dt><a href="/fr/docs/Web/CSS/::-moz-progress-bar"><code>::-moz-progress-bar</code></a></dt>
 <dd>Un pseudo-élément spécifique à Mozilla qui vous permet de définir le style de la zone d'un élément <a href="/fr/docs/Web/HTML/Element/progress"><code>&lt;progress&gt;</code></a> représentant la fraction d'une tâche.</dd>
</dl>

<h4 id="Autres_changements">Autres changements</h4>

<ul>
 <li>La propriété <a href="/fr/docs/Web/CSS/@-moz-document"><code>@-moz-document</code></a> a une nouvelle fonction <code>regexp()</code>, qui vous permet d'adapter l'URL du document à une <a href="/fr/Guide_JavaScript_1.5/Expressions_rationnelles">regular expression</a>.</li>
 <li>La propriété CSS <a href="/fr/docs/Web/CSS/azimuth"><code>azimuth</code></a> n'est plus supportée, comme nous avons enlevé le peu de code que nous avions pour le groupe média <code>aural</code>. Il n'a jamais été implémenté de manière significative, donc il était plus logique de supprimer cette implémentation crufty pour le moment, au lieu d'essayer de le rafistoler.</li>
 <li>Avant, la pseudo-classe <a href="/fr/docs/Web/CSS/:hover"><code>:hover</code></a> n'était pas appliquée aux sélecteurs de classe quand on était en mode quirks, par exemple, <code>.someclass:hover</code> ne fonctionne pas. Cette bizarrerie a été enlevée.</li>
 <li>La pseudo-classe <a href="/fr/docs/Web/CSS/:indeterminate"><code>:indeterminate</code></a> peut être appliquée à l'élément <a href="/fr/docs/Web/HTML/Element/progress"><code>&lt;progress&gt;</code></a>. Cela n'est pas un standard, mais nous espérons que ce soit adopté par les autres navigateurs car c'est utile.</li>
 <li>La valeur <code>-moz-win-exclude-glass</code> a été ajoutée à la propriété CSS <a href="/fr/docs/Web/CSS/-moz-appearance"><code>-moz-appearance</code></a> afin d'exclure des zones opaques dans les effets d'Aero Glass sur les systèmes Windows.</li>
 <li>Le <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=658949">bug 658949</a> change la façon dont le symbole dièse (#) est traité dans les données URI qui peut briser les feuilles de style CSS qui contiennent un tel symbole.</li>
</ul>

<h3 id="DOM">DOM</h3>

<dl>
 <dt><a href="/fr/docs/CSS/Using_media_queries_from_code">Utilisation de media queries à partir de code</a></dt>
 <dd>Vous pouvez désormais tester le résultat d'une chaîne media query en programmant la méthode <a href="/fr/docs/Web/API/Window/matchMedia"><code>window.matchMedia()</code></a> et l'interface <a href="/fr/docs/Web/API/MediaQueryList"><code>MediaQueryList</code></a>.</dd>
 <dt><a href="/fr/docs/DOM/Touch_events">Evènements tactile</a></dt>
 <dd>Firefox 6 ajout le support du standard W3C sur les évènements tactile, cela facilite l'interprétation d'une ou plusieurs touches à la fois sur les surfaces tactiles comme les écrans tactiles et pavés tactiles.</dd>
 <dt><a href="/fr/docs/Server-sent_events">Evènements server-sent</a></dt>
 <dd>Les évènements server-sent permettent à une application Web de demander à un serveur pour envoyer des événements comme n'importe quel événement DOM localement créé.</dd>
</dl>

<ul>
 <li><code>navigator.securityPolicy</code>, qui a depuis longtemps retourné une chaîne vide, a simplement été supprimé.</li>
 <li><a href="/fr/docs/Web/API/BlobBuilder"><code>BlobBuilder</code></a> est maintenant implémenté, même si pour l'instant il est préfixé (vous devez utiliser <code>MozBlobBuilder</code>).</li>
 <li><a href="/fr/docs/Web/API/Document/height"><code>document.height</code></a> et <a href="/fr/docs/Web/API/Document/width"><code>document.width</code></a> ont été supprimées. <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=585877">bug 585877</a></li>
 <li>Les propriétés <code>entities</code> et <code>notations</code> de l'objet <a href="/fr/docs/Web/API/DocumentType"><code>DocumentType</code></a>, qui n'ont jamais été implémentées et renvoyées toujours <code>null</code>, ont été retirées, car elles ont également été enlevées de la spécification.</li>
 <li>L'interface <code>DOMConfiguration</code> et la propriété <code>document.domConfig</code> qu'elle utilisait ont été supprimées, elles n'ont jamais été supportées et ont depuis été retirées de la spécification DOM.</li>
 <li>L'évènement <code>hashchange</code> comprend désormais <a href="/fr/docs/DOM/window.onhashchange#The_hashchange_event">les champs <code>newURL</code> et <code>oldURL</code></a>.</li>
 <li>La méthode <code>abort()</code> de l'interface <a href="/fr/docs/Web/API/FileReader"><code>FileReader</code></a> retourne maintenant une exception si aucun fichier n'est en cours de lecture lorqu'elle est utilisée.</li>
 <li>La méthode <a href="/fr/docs/Web/API/Window/postMessage"><code>window.postMessage()</code></a> utilise maintenant <a href="/fr/docs/DOM/The_structured_clone_algorithm">l'algorithme de clonage structuré</a> pour vous permettre de transmettre d'une fenêtre à une autre des objets JavaScript au lieu de chaînes.</li>
 <li>L'API <a href="/fr/docs/Web/API/Window/history"><code>window.history</code></a> utilise désormais <a href="/fr/docs/DOM/The_structured_clone_algorithm">l'algorithme de clonage structuré</a> pour sérialiser des objets que vous passez avec les méthodes <code>pushState()</code> et <code>replaceState()</code>, ce qui vous permet d'utiliser des objets plus complexes (y compris ceux qui contiennent des références de graphes cycliques).</li>
 <li>Vous pouvez désormais <a href="/fr/docs/Printing#Detecting_print_requests">détecter lorsqu'une impression a été lancée et a été achevée</a> grâce aux nouveaux évènements <code>beforeprint</code> et <code>afterprint</code>.</li>
 <li>La propriété <code>document.strictErrorChecking</code> a été supprimée, car elle n'a jamais été implémentée et a été retiré de la spécification DOM.</li>
 <li>La propriété standard <a href="/fr/docs/Web/API/Event/defaultPrevented"><code>event.defaultPrevented</code></a> est maintenant supportée, vous devriez utiliser à la place la méthode non-standard <code>getPreventDefault()</code> pour détecter si <a href="/fr/docs/Web/API/Event/preventDefault"><code>event.preventDefault()</code></a> a été appelée sur l'événement.</li>
 <li>La propriété <a href="/fr/docs/Web/API/Window/top"><code>window.top</code></a> est désormais en lecture seule.</li>
 <li>DOM views, which we never documented, have been removed. This was a bit of implementation detail that was unnecessarily complicating things, so we got rid of it. If you notice this change, you're probably doing something wrong.</li>
 <li>La fonction <code>EventTarget</code> de la méthode <a href="/fr/docs/XPCOM_Interface_Reference/nsIDOMEventTarget"><code>addEventListener()</code></a> est désormais facultative, car ça l'est dans WebKit (et aussi dans la dernière version de la spécification).</li>
 <li>La propriété <code>mozResponseArrayBuffer</code> de l'objet <a href="/fr/docs/XMLHttpRequest"><code>XMLHttpRequest</code></a> a été remplacé par les propriétés <code>responseType</code> et <code>response</code>.</li>
 <li>La propriété <a href="/fr/docs/Web/API/Element/dataset"><code>element.dataset</code></a> a été ajoutée à l'interface <a href="/fr/docs/DOM/HTMLElement"><code>HTMLElement</code></a> permettant d'accéder aux attributs globaux <a href="/fr/docs/HTML/Global_attributes#attr-data-*"><code>data-*</code> global attributes</a> d'un élément.</li>
 <li>L'interface <a href="/fr/docs/Web/API/CustomEvent"><code>CustomEvent</code></a> a été implémentée. (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=427537">bug 427537</a>)</li>
 <li>Pour des raisons de sécurité, les URIs <code>data:</code> et <code>javascript:</code> n'héritent plus de l'environnment de sécurité de la page active lorsque l'utilisateur les saisit dans la barre d'adresse, mais un nouvel environnment de sécurité vide est créé. Par exemple, le script chargé en entrant l'URI <code>javascript:</code> dans la barre d'adresse n'a plus accès aux méthodes DOM et similaires. Ces URIs continueront à travailler comme avant lorsqu'elles sont utilisées par le script.</li>
</ul>

<h3 id="JavaScript">JavaScript</h3>

<ul>
 <li>Avant, il était possible d'utiliser l'opérateur <code>new</code> sur plusieurs fonctions natives (eval, parseInt, Date.parse, etc) ce qui, conformément à la spécification, n'était pas autorisé. Désormais ce comportement n'est plus supporté. Cette façon d'utiliser l'opérateur <code>new</code> n'a jamais été officiellement supportée et était peu utilisée, donc il est peu probable que ce changement vous affecte.</li>
 <li>ECMAScript Harmony <a href="/fr/docs/JavaScript/Référence_JavaScript/Objets_globaux/WeakMap">WeakMaps</a> a été ajouté en tant que prototype.</li>
</ul>

<h3 id="SVG">SVG</h3>

<ul>
 <li>L'attribut <code><a href="/fr/docs/Web/SVG/Attributs/pathLength">pathLength</a></code> est désormais supporté.</li>
 <li>Les modèles SVG, les dégradés et les filtres fonctionnent désormais correctement lorsqu'ils sont chargés à partir de <a href="/en/data_URIs"><code>data:</code> URLs</a>.</li>
</ul>

<h3 id="MathML">MathML</h3>

<ul>
 <li>L'implémentation de <code><a href="/fr/docs/Web/MathML/Element/mstyle">&lt;mstyle&gt;</a></code> a été corrigée.</li>
</ul>

<h3 id="Accessibilité_ARIA">Accessibilité (ARIA)</h3>

<ul>
 <li>Un événement de changement d'état est à présent correctement envoyé lors d'un changement de la valeur de <code>aria-busy</code>.</li>
 <li>Un événement de changement d'attribut est à présent correctement envoyé lorsque survient <code>aria-sort</code>.</li>
</ul>

<h3 id="Réseau">Réseau</h3>

<dl>
 <dt><a href="/fr/docs/WebSockets">WebSockets</a></dt>
 <dd>Pour Firefox 6, WebSockets a été mis à jour à la version 07 du protocole. De plus, l'objet <code>WebSocket</code> a été renommé en <code>MozWebSocket</code> pour l'empêcher d'être utilisé de façon incorrecte pour détecter la disponibilité des WebSockets sans préfixe.</dd>
</dl>

<ul>
 <li>L'analyse de l'en-tête <code>Content-Disposition</code> a été fixée afin d'interpréter correctement les antislashs des caractères ASCII. Auparavant, il été remplacé par le caractère underscore ("_").</li>
 <li>La valeur du champ du chemin de l'en-tête <code>Set-Cookie</code> est désormais correctement interprétée lors de l'utilisation de guillements, auparavant, ils étaient considérés comme faisant partie de la chaîne du chemin d'accès à la place d'être des délimiteurs. <strong>Ce changement peut affecter la compatibilité avec certains sites web</strong>, les auteurs doivent vérifier leur code.</li>
 <li>L'en-tête de la requête <a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.42"><code>Upgrade</code></a> est désormais supporté, vous pouvez demander la mise à niveau d'un canal vers un autre protocole HTTP en appelant <code><a href="/fr/docs/XPCOM_Interface_Reference/nsIHttpChannelInternal#HTTPUpgrade()">nsIHttpChannelInternal.HTTPUpgrade()</a></code>.</li>
</ul>

<h3 id="Autres_changements_2">Autres changements</h3>

<ul>
 <li>Le support des microrésumés a été enlevé, ils n'ont jamais été très utilisés, n'étaient pas très détectable et continuer leur support été d'apporter des améliorations à Places (favoris et historique) à l'architecture difficile.</li>
 <li>WebGL supporte maintenant l'extension <a href="http://www.khronos.org/registry/gles/extensions/OES/OES_texture_float.txt"><code>OES_texture_float</code></a>.</li>
 <li>Le nouvel outil <a href="/fr/docs/Outils/Ardoise">Ardoise</a> offre un endroit pratique pour expérimenter du code JavaScript.</li>
 <li>La méthode <code>console.trace()</code> a été ajouté à <a href="/fr/docs/Tools/Web_Console">ConsoleAPI</a> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=585956">bug 585956</a>).</li>
</ul>

<h2 id="Changements_pour_les_développeurs_de_Mozilla_et_de_modules_complémentaires">Changements pour les développeurs de Mozilla et de modules complémentaires</h2>

<p>Pour des conseils utiles sur la mise à jour des extensions pour Firefox 6, voir <a href="/fr/docs/Firefox/Updating_add-ons_for_Firefox_6">Updating add-ons for Firefox 6</a>.</p>

<div class="note">
  <p><strong>Note :</strong> Firefox 6 requiert que les composants binaires soient recompilés, comme pour toutes les versions majeures de Firefox. Pour plus de détails, voir <a href="/fr/docs/Developer_Guide/Interface_Compatibility#Binary_Interfaces">Interfaces Binaires</a>.</p>
</div>

<h3 id="Modules_de_code_JavaScript">Modules de code JavaScript</h3>

<h4 id="FileUtils.jsm">FileUtils.jsm</h4>

<ul>
 <li>La méthode <code>openSafeFileOutputStream()</code> ouvre maintenant les fichiers avec <a href="/fr/docs/XPCOM_Interface_Reference/nsIFileOutputStream#Behavior_flag_constants">l'indicateur de comportement</a> <code>DEFER_OPEN</code> au lieu d'essayer de les ouvrir immédiatement.</li>
</ul>

<h4 id="XPCOMUtils.jsm">XPCOMUtils.jsm</h4>

<ul>
 <li>La nouvelle méthode <a href="/fr/docs/JavaScript_code_modules/XPCOMUtils.jsm#importRelative()"><code>importRelative()</code></a> vous permet de charger un module de code JavaScript depuis un chemin relatif au chemin d'un autre module de code JavaScript. Cela rend plus facile la construction de modules qui dépendent les uns des autres.</li>
</ul>

<h3 id="XPCOM">XPCOM</h3>

<ul>
 <li><a href="/fr/docs/XPCOM_array_guide#nsCOMArray.3cT.3e"><code>nsCOMArray&lt;T&gt;</code></a> dispose désormais d'une méthode <a href="/fr/docs/XPCOM_array_guide#Deleting_objects"><code>RemoveObjectsAt()</code></a> pour enlever plusieurs objets à la fois à partir d'un tableau.</li>
</ul>

<h3 id="Utilisation_du_DOM_depuis_le_chrome">Utilisation du DOM depuis le chrome</h3>

<dl>
 <dt><a href="/fr/docs/Extensions/Using_the_DOM_File_API_in_chrome_code">Utilisation de l'API DOM File dans du code chrome</a></dt>
 <dd>Bien que vous avez toujours pu utiliser l'API DOM File à partir du code chrome, le constructeur <a href="/fr/docs/Web/API/File"><code>File</code></a> supporte désormais la spécification d'un chemin d'accès local lorsqu'il est utilisé depuis le chrome. De plus, vous pouvez également spécifier le fichier pour accéder à l'aide de l'API DOM File en utilisant un objet <code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIFile">nsIFile</a></code>.</dd>
</dl>

<h3 id="Changements_dans_les_interfaces">Changements dans les interfaces</h3>

<ul>
 <li><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsINavHistoryQueryOptions">nsINavHistoryQueryOptions</a></code> supporte désormais le tri par orde de frecency à l'aide des nouvelles constantes <code>SORT_BY_FRECENCY_ASCENDING</code> et <code>SORT_BY_FRECENCY_DESCENDING</code>.</li>
 <li><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIFilePicker">nsIFilePicker</a></code> a un nouvel attribut <code><a href="/fr/docs/XPCOM_Interface_Reference/nsIFilePicker#addToRecentDocs">nsIFilePicker.addToRecentDocs</a></code>, qui vous permet d'indiquer que le fichier sélectionné doit être ajoutée à la liste "documents récents" de l'utilisateur si il y en a une. Cet attribut n'a aucun effet en mode navigation privée.</li>
 <li>Les méthodes de <code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsINavBookmarkObserver">nsINavBookmarkObserver</a></code> avec les paramètres ID d'un élément exigent désormais un GUID.</li>
 <li><code><a href="/fr/docs/XPCOM_Interface_Reference/nsIPrefBranch#clearUserPref()">nsIPrefBranch.clearUserPref()</a></code> ne génère plus d'exception si la préférence spécifié n'existe pas ou n'a pas de valeur définie par l'utilisateur. Désormais, il ne fait rien.</li>
 <li>L'interface <code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIMemoryReporter">nsIMemoryReporter</a></code> prend désormais en charge l'indication du type de mémoire qui est décrite (mappée, heap, ou autre).</li>
 <li>L'attribut <code>stateData</code> de <code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsISHEntry">nsISHEntry</a></code> renvoi désormais à <code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIStructuredCloneContainer">nsIStructuredCloneContainer</a></code>.</li>
 <li><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIURI">nsIURI</a></code> a un nouvel attribut <code><a href="/fr/docs/XPCOM_Interface_Reference/nsIURI#ref">nsIURI.ref</a></code>, qui renvoie la partie de référence (la partie après le "#") de l'URI. Il y a également de nouvelles méthodes <code><a href="/fr/docs/XPCOM_Interface_Reference/nsIURI#cloneIgnoringRef()">nsIURI.cloneIgnoringRef()</a></code> qui clone <code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIURI">nsIURI</a></code> sans l'élément ref et <code><a href="/fr/docs/XPCOM_Interface_Reference/nsIURI#equalsExceptRef()">nsIURI.equalsExceptRef()</a></code> qui se compare à un autre <code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIURI">nsIURI</a></code> en ignorant l'élément ref.</li>
</ul>

<h4 id="Nouvelles_interfaces">Nouvelles interfaces</h4>

<dl>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/mozIAsyncFavicons">mozIAsyncFavicons</a></code></dt>
 <dd>Un nouveau service qui vous permet d'accéder au service favicon de façon asynchrone.</dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIEventSource">nsIEventSource</a></code></dt>
 <dd><em>Détails à venir.</em></dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIGSettingsCollection">nsIGSettingsCollection</a></code></dt>
 <dd><em>Détails à venir.</em></dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIGSettingsService">nsIGSettingsService</a></code></dt>
 <dd><em>Détails à venir.</em></dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIHttpUpgradeListener">nsIHttpUpgradeListener</a></code></dt>
 <dd>L'interface de rappel pour le traitement des demandes de mise à niveau HTTP via la méthode <code><a href="/fr/docs/XPCOM_Interface_Reference/nsIHttpChannelInternal#HTTPUpgrade()">nsIHttpChannelInternal.HTTPUpgrade()</a></code>.</dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIStructuredCloneContainer">nsIStructuredCloneContainer</a></code></dt>
 <dd>Un conteneur pour les objets qui ont été sérialisé à l'aide de <a href="/en/HTML/Structured_clones">l'algorithme de clonage structuré</a>.</dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsITelemetry">nsITelemetry</a></code></dt>
 <dd>Implémentation du support de la télémétrie permettant d'enregistrer des données de télémétrie pour être utilisé pour présenter des histogrammes à des fins de suivi des performances. Voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=649502">bug 649502</a> et <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=585196">bug 585196</a>.</dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsITimedChannel">nsITimedChannel</a></code></dt>
 <dd>Voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=576006">bug 576006</a>.</dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIWebSocketListener">nsIWebSocketListener</a></code></dt>
 <dd>Voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=640003">bug 640003</a>.</dd>
 <dt><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIWebSocketProtocol">nsIWebSocketProtocol</a></code></dt>
 <dd>Voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=640003">bug 640003</a>.</dd>
</dl>

<h4 id="Interfaces_supprimées">Interfaces supprimées</h4>

<p>Les interfaces suivantes ont été supprimées car elles n'étaient plus indispensables :</p>

<ul>
 <li><code>nsIDOMDocumentEvent</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=655517">bug 655517</a>)</li>
 <li><code>nsIDOMDocumentTraversal</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=655514">bug 655514</a>)</li>
 <li><code>nsIDOMDocumentRange</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=655513">bug 655513</a>)</li>
 <li><code>IWeaveCrypto</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=651596">bug 651596</a>)</li>
 <li><code>nsIDOM3DocumentEvent</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=481863">bug 481863</a>)</li>
 <li><code>nsIDOMAbstractView</code></li>
 <li><code>nsILiveTitleNotificationSubject</code></li>
 <li><code>nsIPlugin</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=637253">bug 637253</a>)</li>
 <li><code>nsIPluginInstance</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=637253">bug 637253</a>)</li>
 <li><code>nsIHTMLEditRules</code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=633750">bug 633750</a>)</li>
 <li><code><a href="/fr/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIXSLTProcessorObsolete">nsIXSLTProcessorObsolete</a></code> (voir <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=649534">bug 649534</a>)</li>
</ul>

<h3 id="Autres_changements_3">Autres changements</h3>

<dl>
 <dt><a href="/fr/docs/Mozilla/Preferences/Using_preferences_from_application_code">Utilisation des préférences à partir du code d'application</a></dt>
 <dd>Une nouvelle API statique est disponible pour accéder facilement aux préférences, ce n'est disponible que pour le code d'application et ne peut pas être utilisé par les modules complémentaires.</dd>
</dl>

<h2 id="Voir_également">Voir également</h2>

<ul>
<li><a href="/fr/docs/Mozilla/Firefox/Versions/5">Firefox 5 pour les développeurs</a></li><li><a href="/fr/docs/Mozilla/Firefox/Versions/4">Firefox 4 pour les développeurs</a></li><li><a href="/fr/docs/Mozilla/Firefox/Versions/3.6">Firefox 3.6 pour les développeurs</a></li><li><a href="/fr/docs/Mozilla/Firefox/Versions/3.5">Firefox 3.5 pour les développeurs</a></li><li><a href="/fr/docs/Mozilla/Firefox/Versions/3">Firefox 3 pour les développeurs</a></li><li><a href="/fr/docs/Mozilla/Firefox/Versions/2">Firefox 2 pour les développeurs</a></li><li><a href="/fr/docs/Mozilla/Firefox/Versions/1.5">Firefox 1.5 pour les développeurs</a></li></ul>
