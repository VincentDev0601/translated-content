---
title: MediaDevices.getUserMedia()
slug: Web/API/MediaDevices/getUserMedia
translation_of: Web/API/MediaDevices/getUserMedia
---
<div>{{APIRef("WebRTC")}}</div>

<p>La méthode <code><strong>MediaDevices.getUserMedia()</strong></code> invite l'utilisateur à autoriser l'utilisation d'une entrée multimédia qui produit un {{domxref("MediaStream")}} avec des pistes contenant les types de médias demandés. Ce flux peut inclure, par exemple, une piste vidéo (produite par une source matérielle ou vidéo virtuelle telle qu'une caméra, un dispositif d'enregistrement vidéo, un service de partage d'écran, etc.), une piste audio (de la même manière, produite par une source physique ou Source audio virtuelle comme un microphone, convertisseur A / D ou similaire) et éventuellement d'autres types de piste.</p>

<p>Il renvoie un  {{jsxref("Promise")}}  qui est résolu avec succès si l'utilisateur donne son autorisation;   {{domxref("MediaStream")}}  est fourni à ce moment-là.  Si l'utilisateur refuse ou si le média correspondant n'est pas disponible, le  {{jsxref("Promise")}}  est rejetée avec respectivement <code>PermissionDeniedError</code> ou <code>NotFoundError</code>.</p>

<div class="note">
<p><strong>Note :</strong> Il est possible que le  {{jsxref("Promise")}}  renvoyé ne soit <em>ni</em> résolu ni rejeté, car l'utilisateur n'est pas tenu de faire un choix. .</p>
</div>

<p>Généralement, vous accédez à l'objet  {{domxref("MediaDevices")}}  avec  {{domxref("navigator.mediaDevices")}}  , comme ceci:</p>

<pre class="brush: js">navigator.mediaDevices.getUserMedia(constraints).then(function(stream) {
  /* use the stream */
}).catch(function(err) {
  /* handle the error */
});</pre>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox">var <em>promise</em> = navigator.mediaDevices.getUserMedia(<em>constraints</em>);
</pre>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>constraints</code></dt>
 <dd>
 <p>Un objet  {{domxref("MediaStreamConstraints")}}  spécifiant les types de supports à demander, ainsi que toutes les exigences pour chaque type.</p>

 <p>Le paramètre constraints est un objet <code>MediaStreamConstraints</code> avec deux membres: <code>video</code> et <code>audio</code> , décrivant les types de média demandés.  L'un ou l'autre ou les deux doivent être spécifiés.  Si le navigateur ne trouve pas toutes les pistes multimédia avec les types spécifiés qui répondent aux contraintes fournies, la promesse renvoyée est rejetée avec <code>NotFoundError</code> .</p>

 <p>Les demandes suivantes sont audio et vidéo sans aucune exigence spécifique:</p>

 <pre class="brush: js">{ audio: true, video: true }</pre>

 <p>Si <code>true</code> est spécifié pour un type de média, le flux résultant est <em>requis</em> pour obtenir ce type de piste.  Si on ne peut pas l'obtenir pour une raison quelconque, l'appel à <code>getUserMedia()</code> entraînera une erreur.</p>

 <p>Alors que les informations sur les caméras et les microphones d'un utilisateur sont inaccessibles pour des raisons de confidentialité, une application peut demander les capacités de caméra et de microphone dont elle a besoin en utilisant des contraintes supplémentaires.  Ce qui suit exprime une préférence pour la résolution de la caméra 1280x720:</p>

 <pre class="brush: js">{
  audio: true,
  video: { width: 1280, height: 720 }
}</pre>

 <p>Le navigateur essaiera d'honorer cela, mais peut renvoyer d'autres résolutions si une correspondance exacte n'est pas disponible, ou si l'utilisateur l'annule.</p>

 <p>Pour <em>exiger</em> une capacité, utilisez les mots-clés <code>min</code> , <code>max</code> ou <code>exact</code> (aka <code>min == max</code> ).  Ce qui suit exige une résolution minimale de 1280x720:</p>

 <pre class="brush: js">{
  audio: true,
  video: {
    width: { min: 1280 },
    height: { min: 720 }
  }
}</pre>

 <p>Si aucune caméra n'existe avec cette résolution ou plus haut, le  {{jsxref("Promise")}}  retourné sera rejeté avec <code>OverconstrainedError</code>.</p>

 <p>La raison de la différence de comportement est que les mots clés <code>min</code> , <code>max</code> et <code>exact</code> sont intrinsèquement obligatoires, alors que les valeurs simples et un mot-clé appelé <code>ideal</code> ne le sont pas.  Voici un exemple plus complet:</p>

 <pre class="brush: js">{
  audio: true,
  video: {
    width: { min: 1024, ideal: 1280, max: 1920 },
    height: { min: 776, ideal: 720, max: 1080 }
  }
}</pre>

 <p>Une valeur <code>ideal</code> , lorsqu'elle est utilisée, a une gravité, ce qui signifie que le navigateur essaiera de trouver le réglage (et la caméra, si vous en avez plus d'une), avec les valeurs les plus proches des valeurs idéales données.</p>

 <p>Les valeurs simples sont par nature idéales, ce qui signifie que le premier de nos exemples de résolution ci-dessus aurait pu être écrit comme ceci:</p>

 <pre class="brush: js">{
  audio: true,
  video: {
    width: { ideal: 1280 },
    height: { ideal: 720 }
  }
}</pre>

 <p>Toutes les contraintes ne sont pas des nombres.  Par exemple, sur les appareils mobiles, les éléments suivants préfèrent la caméra avant (si celle-ci est disponible) sur l'arrière:</p>

 <pre class="brush: js">{ audio: true, video: { facingMode: "user" } }</pre>

 <p>Pour <em>exiger</em> la caméra arrière, utilisez:</p>

 <pre class="brush: js">{ audio: true, video: { facingMode: { exact: "environment" } } }</pre>
 </dd>
</dl>

<h3 id="Valeur_de_retour">Valeur de retour</h3>

<p>Un  {{jsxref("Promise")}}  qui reçoit en objet  {{domxref("MediaStream")}}  lorsque les médias demandés ont été obtenus avec succès.</p>

<h3 id="Erreurs">Erreurs</h3>

<p>Les rejets du  {{jsxref("Promise")}}  retourné sont effectués en passant un objet erreur <a href="https://translate.googleusercontent.com/translate_c?depth=1&amp;hl=fr&amp;prev=search&amp;rurl=translate.google.fr&amp;sl=en&amp;sp=nmt4&amp;u=https://developer.mozilla.org/en-US/docs/Web/API/DOMException&amp;usg=ALkJrhgnRUAs3RQR8I7ulOitmhRQUlVEUA"><code>DOMException</code></a> au gestionnaire d'erreurs.  Les erreurs possibles sont:</p>

<dl>
 <dt><code>AbortError</code></dt>
 <dd>Bien que l'utilisateur et le système d'exploitation aient tous deux accédé à l'équipement matériel, et qu'aucun problème de matériel ne causerait un <code>NotReadableError</code> , un problème s'est produit, ce qui a empêché l'utilisation du périphérique.</dd>
 <dt><code>NotAllowedError</code></dt>
 <dd>L'utilisateur a spécifié que l'instance de navigation actuelle n'a pas accès au périphérique;  Ou l'utilisateur a refusé l'accès pour la session en cours;  Ou l'utilisateur a refusé tout l'accès aux périphériques multimédias utilisateurs dans le monde entier.
 <div class="note"><p><strong>Note :</strong> Les versions plus anciennes de la spécification ont utilisé <code>SecurityError</code> pour cela à la place;  <code>SecurityError</code> a pris une nouvelle signification.</p></div>
 </dd>
 <dt><code>NotFoundError</code></dt>
 <dd>Aucune piste multimédia du type spécifié n'a été trouvée satisfaisant les contraintes données.</dd>
 <dt><code>NotReadableError</code></dt>
 <dd>Bien que l'utilisateur ait autorisé l'utilisation des appareils correspondants, une erreur matérielle s'est produite sur le système d'exploitation, le navigateur ou le niveau de la page Web qui a empêché l'accès au périphérique.</dd>
 <dt><code>OverConstrainedError</code></dt>
 <dd>Aucun dispositif candidat répondant aux critères demandés.  L'erreur est un objet de type <code>OverconstrainedError</code> et possède une propriété de <code>constraint</code> dont la valeur de chaîne est le nom d'une contrainte impossible à honorer et une propriété <code>message</code> contenant une chaîne lisible par l'homme expliquant le problème.
 <div class="note"><p><strong>Note :</strong> Étant donné que cette erreur peut se produire même lorsque l'utilisateur n'a pas encore autorisé l'utilisation du périphérique sous-jacent, il peut être utilisé comme surface d'empreinte digitale.</p></div>
 </dd>
 <dt><code>SecurityError</code></dt>
 <dd>Le support multimédia utilisateur est désactivé sur le  {{domxref("Document")}}  sur lequel <code>getUserMedia()</code> été appelé.  Le mécanisme par lequel le support média utilisateur est activé/désactivé est laissé à la discrétion de l'utilisateur.</dd>
 <dt><code>TypeError</code></dt>
 <dd>La liste des contraintes spécifiées est vide ou toutes les contraintes sont définies comme <code>false</code> .</dd>
</dl>

<h2 id="Exemples"><strong>Exemple</strong>s</h2>

<h3 id="Largeur_et_hauteur">Largeur et hauteur</h3>

<p>Cet exemple donne une préférence pour la résolution de la caméra et attribue l'objet <a href="https://translate.googleusercontent.com/translate_c?depth=1&amp;hl=fr&amp;prev=search&amp;rurl=translate.google.fr&amp;sl=en&amp;sp=nmt4&amp;u=https://developer.mozilla.org/en-US/docs/Web/API/MediaStream&amp;usg=ALkJrhipdR5n2jQ-BGrPTomESH_A7nof4g"><code>MediaStream</code></a> résultant à un élément vidéo.</p>

<pre>// Prefer camera resolution nearest to 1280x720.
var constraints = { audio: true, video: { width: 1280, height: 720 } };

navigator.mediaDevices.getUserMedia(constraints)
.then(function(mediaStream) {
  var video = document.querySelector('video');
  video.srcObject = mediaStream;
  video.onloadedmetadata = function(e) {
    video.play();
  };
})
.catch(function(err) { console.log(err.name + ": " + err.message); }); // always check for errors at the end.
</pre>

<h3 id="Utilisation_de_la_nouvelle_API_dans_les_navigateurs_plus_anciens">Utilisation de la nouvelle API dans les navigateurs plus anciens</h3>

<p>Voici un exemple d'utilisation de <code>navigator.mediaDevices.getUserMedia()</code> , avec un adaptateur pour faire face aux navigateurs plus anciens.  Notez que cet adaptater ne corrige pas les différences existantes dans la syntaxe des contraintes, ce qui signifie que les contraintes ne fonctionneront pas bien dans les navigateurs.  Il est recommandé d'utiliser l'adaptateur <a href="https://github.com/webrtc/adapter">adapter.js</a>  a la place, qui gère les contraintes.</p>

<pre class="brush: js">// Older browsers might not implement mediaDevices at all, so we set an empty object first
if (navigator.mediaDevices === undefined) {
  navigator.mediaDevices = {};
}

// Some browsers partially implement mediaDevices. We can't just assign an object
// with getUserMedia as it would overwrite existing properties.
// Here, we will just add the getUserMedia property if it's missing.
if (navigator.mediaDevices.getUserMedia === undefined) {
  navigator.mediaDevices.getUserMedia = function(constraints) {

    // First get ahold of the legacy getUserMedia, if present
    var getUserMedia = navigator.webkitGetUserMedia || navigator.mozGetUserMedia;

    // Some browsers just don't implement it - return a rejected promise with an error
    // to keep a consistent interface
    if (!getUserMedia) {
      return Promise.reject(new Error('getUserMedia is not implemented in this browser'));
    }

    // Otherwise, wrap the call to the old navigator.getUserMedia with a Promise
    return new Promise(function(resolve, reject) {
      getUserMedia.call(navigator, constraints, resolve, reject);
    });
  }
}

navigator.mediaDevices.getUserMedia({ audio: true, video: true })
.then(function(stream) {
  var video = document.querySelector('video');
  // Older browsers may not have srcObject
  if ("srcObject" in video) {
    video.srcObject = stream;
  } else {
    // Avoid using this in new browsers, as it is going away.
    video.src = window.URL.createObjectURL(stream);
  }
  video.onloadedmetadata = function(e) {
    video.play();
  };
})
.catch(function(err) {
  console.log(err.name + ": " + err.message);
});
</pre>

<h3 id="Taux_d'images">Taux d'images</h3>

<p>Des cadences inférieures peuvent être souhaitables dans certains cas, comme les transmissions WebRTC avec des restrictions de bande passante.</p>

<pre class="brush: js">var constraints = { video: { frameRate: { ideal: 10, max: 15 } } };
</pre>

<h3 id="Caméra_avant_et_arrière">Caméra avant et arrière</h3>

<p>Sur les téléphones portables.</p>

<pre class="brush: js">var front = false;
document.getElementById('flip-button').onclick = function() { front = !front; };

var constraints = { video: { facingMode: (front? "user" : "environment") } };
</pre>

<h2 id="Permissions">Permissions</h2>

<p>Pour utiliser <code>getUserMedia()</code> dans une application installable (par exemple, une <a href="https://translate.googleusercontent.com/translate_c?depth=1&amp;hl=fr&amp;prev=search&amp;rurl=translate.google.fr&amp;sl=en&amp;sp=nmt4&amp;u=https://developer.mozilla.org/en-US/Apps/Build/Building_apps_for_Firefox_OS/Firefox_OS_app_beginners_tutorial&amp;usg=ALkJrhjjqOGYUEn75gZx3AcoQDArrosa9Q">application Firefox OS</a> ), vous devez spécifier un ou les deux champs suivants dans votre fichier manifeste:</p>

<pre class="brush: js">"permissions": {
  "audio-capture": {
    "description": "Required to capture audio using getUserMedia()"
  },
  "video-capture": {
    "description": "Required to capture video using getUserMedia()"
  }
}</pre>

<p>Voir  <a href="/en-US/Apps/Developing/App_permissions#audio-capture">permission: audio-capture</a>  et  <a href="/en-US/Apps/Developing/App_permissions#video-capture">permission: video-capture</a>  pour plus d'informations.</p>

<h2 id="Specifications">Specifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Specification</th>
   <th scope="col">Status</th>
   <th scope="col">Comment</th>
  </tr>
  <tr>
   <td>{{SpecName('Media Capture', '#dom-mediadevices-getusermedia', 'MediaDevices.getUserMedia()')}}</td>
   <td>{{Spec2('Media Capture')}}</td>
   <td>Initial definition</td>
  </tr>
 </tbody>
</table>

<h2 id="Browser_compatibility">Compatibilité des navigateurs</h2>

<p>{{Compat("api.MediaDevices.getUserMedia")}}</p>

<h2 id="See_also">Voir aussi</h2>

<ul>
  <li>L'ancienne API {{domxref("navigator.getUserMedia()")}}.</li>
  <li>{{domxref("mediaDevices.enumerateDevices()")}} : Apprenez les types et le nombre de périphériques que l'utilisateur dispose.</li>
  <li><a href="/fr/docs/Web/API/WebRTC_API">WebRTC API</a></li>
  <li><a href="/fr/docs/Web/API/Media_Streams_API">Media Capture and Streams API (Media Streams)</a></li>
  <li><a href="/fr/docs/Web/API/WebRTC_API/Taking_still_photos">Taking webcam photos</a> : un tutoriel sur l'utilisation de <code>getUserMedia()</code> pour prendre des photos plutôt que de la vidéo.</li>
</ul>
