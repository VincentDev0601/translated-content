---
title: L'audio dans les jeux Web
slug: Games/Techniques/Audio_for_Web_Games
tags:
  - API
  - Audio
  - Jeux
  - Web Audio API
  - audio sprites
translation_of: Games/Techniques/Audio_for_Web_Games
---
<div>{{GamesSidebar}}</div><p>  {{IncludeSubnav("/fr/docs/Jeux")}}</p>

<p>L'audio représente une chose essentielle dans n'importe quel jeu vidéo; il apporte de l'information et contribue à l'atmosphère du jeu. La prise en charge de l'audio a évolué de manière rapide mais il reste encore beaucoup de différences de prise en charge entre les navigateurs. Nous avons souvent besoin de décider quelles parties de notre contenu audio est intéressant et laquelle ne l'est pas, et mettre en place une stratégie en conséquence. Cet article fournit un guide détaillé sur l'implémentation de l'audio dans les jeux HTML5, détaillant quels choix technologiques fonctionneront sur le plus grand nombre de navigateurs.</p>

<h2 id="Avertissement_sur_l'audio_sur_mobile">Avertissement sur l'audio sur mobile</h2>

<p>Les plateformes mobiles sont de loin les plateformes où il est le plus difficile de mettre en place l'audio. Malheureusement c'est la plateforme la plus utilisée par les joueurs. Il y a certaines différences entre les plateformes de bureau (desktop) habituelles et les plateformes mobiles qui ont sûrement poussé les éditeurs de navigateur à faire des choix qui peuvent rendre difficle l'implémentation de l'audio par les utilisateurs. Regardons ensemble ces différences.</p>

<h3 id="Lecture_automatique">Lecture automatique</h3>

<p>Beaucoup de navigateurs mobiles vont simplement ignorer n'importe quelle requête de lancement automatique de musique faite par votre jeu; à la place, l'utilisateur va être obligé de lancer lui même la lecture via une action quelconque. Cela signifie que vous allez devoir prendre en compte cette diférence lors de l'implementation de votre lecture automatique. Ce problème est généralement atténué en chargeant l'audio à l'avance et en l'amorçant sur un événement initié par l'utilisateur.</p>

<p>Pour une lecture automatique audio plus passive, par exemple une musique de fond qui commence dès qu'un jeu se charge, une astuce consiste à détecter l'événement * any * initié par l'utilisateur et à démarrer la lecture. Pour d'autres sons plus actifs qui seront utilisés pendant le jeu, nous pouvons envisager de les amorcer dès que l'on appuie sur un bouton de démarrage.</p>

<p>Pour faire primer l'audio de cette façon, nous voulons en jouer une partie ; pour cette raison, il est utile d'inclure un moment de silence à la fin de votre échantillon audio. Ce silence signifiera que nous pouvons maintenant utiliser JavaScript pour lire ce fichier à des points arbitraires.</p>

<div class="note">
<p><strong>Note :</strong> Jouer une partie de votre fichier au volume zéro pourrait également fonctionner si le navigateur vous permet de changer le volume (voir ci-dessous). Notez également que la lecture et la mise en pause immédiate de votre audio ne garantissent pas qu'un petit morceau d'audio ne sera pas lu.</p>
</div>

<div class="note">
<p><strong>Note :</strong> L'ajout d'une application Web sur votre écran d'accueil mobile peut changer ses capacités. Dans le cas d'une lecture automatique sur iOS, cela semble être le cas actuellement. Si possible, vous devriez essayer votre code sur plusieurs appareils et platesformes pour voir comment cela fonctionne.</p>
</div>

<h3 id="Volume">Volume</h3>

<p>Le contrôle du volume programmé peut être désactivé dans les navigateurs mobiles. La raison souvent donnée est que l'utilisateur doit maîtriser le volume au niveau du système d'exploitation et cela ne doit pas être ignoré.</p>

<h3 id="Mise_en_mémoire_tampon_et_préchargement">Mise en mémoire tampon et préchargement</h3>

<p>Probablement comme une tentative d'atténuation de l'utilisation des données du réseau mobile, nous trouvons souvent que la mise en mémoire tampon est désactivée avant que la lecture n'ait été lancée. La mise en mémoire tampon est le processus par lequel le navigateur télécharge le média à l'avance, ce que nous devons souvent faire pour assurer une lecture fluide.</p>

<div class="note">
<p><strong>Note :</strong> À bien des égards, le concept de mise en mémoire tampon est obsolète. Tant que les demandes de plage d'octets sont acceptées (ce qui est le comportement par défaut), nous devrions pouvoir sauter à un point spécifique de l'audio sans avoir à télécharger le contenu précédent. Cependant, le préchargement est toujours utile; sans cela, il faudrait toujours avoir une certaine communication client-serveur avant de commencer à jouer.</p>
</div>

<h3 id="Lecture_audio_simultanée">Lecture audio simultanée</h3>

<p>Une exigence de nombreux jeux est de jouer plus d'un morceau audio en même temps ; par exemple, il peut y avoir de la musique de fond et des effets sonores pour diverses actions se produisant dans le jeu. Bien que la situation évolue rapidement avec l'adoption de l' <a href="/fr/docs/Web/API/Web_Audio_API">API Web Audio</a> , la méthode actuellement la plus largement supportée, utilisant l'élément vanilla {{htmlelement ("audio")}}, produit des résultats inégaux sur les appareils mobiles.</p>

<h3 id="Test_et_support">Test et support</h3>

<p>Voici un tableau qui montre quelles plateformes mobiles prennent en charge les fonctionnalités mentionnées ci-dessus.</p>

<table class="standard-table">
 <caption>Mobile support for web audio features</caption>
 <thead>
  <tr>
   <th scope="row">Navigateur de mobile</th>
   <th scope="col">Version</th>
   <th scope="col">Lecture simultanée</th>
   <th scope="col">Lecture automatique</th>
   <th scope="col">Ajustement du volume</th>
   <th scope="col">Préchargement</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th scope="row">Chrome (Android)</th>
   <td>32+</td>
   <td>Oui</td>
   <td>Non</td>
   <td>Non</td>
   <td>Non</td>
  </tr>
  <tr>
   <th scope="row">Firefox (Android)</th>
   <td>26+</td>
   <td>Oui</td>
   <td>Oui</td>
   <td>Non</td>
   <td>Non</td>
  </tr>
  <tr>
   <th scope="row">Firefox OS</th>
   <td>1.2+</td>
   <td>Oui</td>
   <td>Oui</td>
   <td>Oui</td>
   <td>Oui</td>
  </tr>
  <tr>
   <th scope="row">IE Mobile</th>
   <td>11+</td>
   <td>Oui</td>
   <td>Oui</td>
   <td>Non</td>
   <td>Oui</td>
  </tr>
  <tr>
   <th scope="row">Opera Mobile</th>
   <td>11+</td>
   <td>Non</td>
   <td>Non</td>
   <td>Non</td>
   <td>Non</td>
  </tr>
  <tr>
   <th scope="row">Safari (iOS)</th>
   <td>7+</td>
   <td>Oui/Non*</td>
   <td>Non</td>
   <td>Non</td>
   <td>Oui</td>
  </tr>
  <tr>
   <th scope="row">Android Browser</th>
   <td>2.3+</td>
   <td>Non</td>
   <td>Non</td>
   <td>Non</td>
   <td>Non</td>
  </tr>
 </tbody>
</table>

<div class="note">
<p><strong>Note :</strong> Safari 7 a des problèmes à jouer si vous essayez de démarrer tous les morceaux audio simultanément. Si vous échelonnez la lecture, vous aurez peut-être un certain succès.</p>
</div>

<div class="note">
<p><strong>Note :</strong> La lecture audio simultanée est testée à l'aide de notre <a href="http://jsfiddle.net/dmkyaq0r/">exemple de test audio simultané</a>, avec lequel nous essayons de lire trois morceaux en même temps en utilisant l'API audio standard.</p>
</div>

<div class="note">
<p><strong>Note :</strong> La fonctionnalité de lecture automatique simple est testée avec notre <a href="http://jsfiddle.net/vpdspp2b/">exemp;e test lecture automatique</a>.</p>
</div>

<div class="note">
<p><strong>Note :</strong> La variabilité du volume est testée avec notre <a href="http://jsfiddle.net/7ta12vw4/">exemple test volume</a>.</p>
</div>

<h2 id="Solutions_de_contournement_pour_mobile">Solutions de contournement pour mobile</h2>

<p>Bien que les navigateurs mobiles puissent présenter les problèmes évoqués ci-dessus, il existe des moyens de les contourner.</p>

<h3 id="Les_sprites_audio">Les "sprites" audio</h3>

<p>Les "sprites" audio empruntent leur nom aux <a href="/fr/docs/Web/CSS/CSS_Images/Sprites_CSS">"sprites" CSS</a> ; c'est une technique visuelle permettant d'utiliser CSS avec une seule ressource graphique pour la découper en une série d'objets-images. Nous pouvons appliquer le même principe à l'audio, au lieu de disposer d'un petit nombre de petits fichiers audio qui prennent du temps à charger et à lire, nous avons un fichier audio plus grand contenant tous les fragments audio plus petits dont nous avons besoin. Pour lire un son spécifique à partir du fichier, nous utilisons simplement les périodes de début et de fin connues pour chaque "sprite" audio.</p>

<p>L'avantage est que nous pouvons amorcer un morceau d'audio et avoir nos "sprites" prêts à partir. Pour ce faire, nous pouvons juste jouer et mettre en pause instantanément la plus grande partie de l'audio. Nous réduisons également le nombre de demandes de serveur et économisons de la bande passante.</p>

<pre class="brush: js">var myAudio = document.createElement("audio");
myAudio.src = "mysprite.mp3";
myAudio.play();
myAudio.pause();</pre>

<p>Vous aurez besoin d'échantillonner l'heure actuelle pour savoir quand l'arrêter. Si vous espacez vos sons individuels d'au moins 500 ms, l'utilisation de l'événement <code>timeUpdate</code> (qui se déclenche toutes les 250 ms) devrait suffire. Vos fichiers peuvent être légèrement plus longs que ce qu'ils devraient être, mais le silence se compresse bien.</p>

<p>Voici un exemple d'un lecteur de "sprite" audio - nous allons d'abord configurer l'interface utilisateur en HTML :</p>

<pre class="brush: html">lt;audio id="myAudio" src="http://jPlayer.org/tmp/countdown.mp3"&gt;&lt;/audio&gt;
&lt;button data-start="18" data-stop="19"&gt;0&lt;/button&gt;
&lt;button data-start="16" data-stop="17"&gt;1&lt;/button&gt;
&lt;button data-start="14" data-stop="15"&gt;2&lt;/button&gt;
&lt;button data-start="12" data-stop="13"&gt;3&lt;/button&gt;
&lt;button data-start="10" data-stop="11"&gt;4&lt;/button&gt;
&lt;button data-start="8"  data-stop="9"&gt;5&lt;/button&gt;
&lt;button data-start="6"  data-stop="7"&gt;6&lt;/button&gt;
&lt;button data-start="4"  data-stop="5"&gt;7&lt;/button&gt;
&lt;button data-start="2"  data-stop="3"&gt;8&lt;/button&gt;
&lt;button data-start="0"  data-stop="1"&gt;9&lt;/button&gt;</pre>

<p>Maintenant, nous avons des boutons avec des heures de début et de fin en quelques secondes. Le fichier MP3 "countdown.mp3" se compose d'un numéro qui est prononcé toutes les 2 secondes, l'idée étant de lire ce numéro lorsque le bouton correspondant est pressé.</p>

<p>Ajoutons du JavaScript pour que ça marche:</p>

<pre class="brush: js">var myAudio = document.getElementById('myAudio');
var buttons = document.getElementsByTagName('button');
var stopTime = 0;

for (var i = 0; i &lt; buttons.length; i++) {
  buttons[i].addEventListener('click', function() {
    myAudio.currentTime = this.getAttribute("data-start");
    stopTime = this.getAttribute("data-stop");
    myAudio.play();
  }, false);
}

myAudio.addEventListener('timeupdate', function() {
  if (this.currentTime &gt; stopTime) {
    this.pause();
  }
}, false);</pre>

<div class="note">
<p><strong>Note :</strong> Vous pouvez <a href="http://jsfiddle.net/59vwaame/">essayer notre lecteur de sprite audio</a> sur JSFiddle.</p>
</div>

<div class="note">
<p><strong>Note :</strong> Sur mobile nous pouvons avoir besoin de déclencher ce code à partir d'un événement initié par l'utilisateur, tel qu'un bouton de démarrage pressé, comme décrit ci-dessus.</p>
</div>

<div class="note">
<p><strong>Note :</strong> Attention aux débits binaires. L'encodage de votre audio à des débits binaires inférieurs signifie des tailles de fichier plus petites, mais une précision de recherche plus faible.</p>
</div>

<h2 id="Musique_de_fond">Musique de fond</h2>

<p>La musique dans les jeux peut avoir un effet émotionnel puissant. Vous pouvez mélanger et assortir divers échantillons de musique et, en supposant que vous pouvez contrôler le volume de votre élément audio, vous pouvez fondre différentes pièces musicales. En utilisant la méthode  <code><a href="/fr/Apps/Fundamentals/Audio_and_video_delivery/WebAudio_playbackRate_explained">playbackRate()</a></code> , vous pouvez même ajuster la vitesse de votre musique sans affecter la hauteur, pour mieux la synchroniser avec l'action.<br>
 <br>
 Tout ceci est possible en utilisant l'élément standard {{HTMLElement ("audio")}} associé à l'API  {{domxref("HTMLMediaElement")}} , mais il devient beaucoup plus facile et flexible avec l'<a href="/fr/docs/Web/API/Web_Audio_API">API Web Audio</a>.</p>

<h2 id="API_Web_Audio_pour_les_jeux">API Web Audio pour les jeux</h2>

<p>Maintenant qu'il est supporté dans tous les navigateurs modernes à l'exception d'Opera Mini et d'Internet Explorer (<a href="https://developer.microsoft.com/en-us/microsoft-edge/platform/status/webaudioapi/">bien que Microsoft travaille maintenant dessus</a>), une approche acceptable pour de nombreuses situations est d'utiliser l'<a href="/fr/docs/Web/API/Web_Audio_API">API Web Audio</a> (voir la page <a href="http://caniuse.com/#search=web%20audio%20api">Puis-je utiliser l'API Web Audio ?</a> pour plus d'informations sur la compatibilité du navigateur). L'API Web Audio est une API JavaScript audio avancée, idéale pour l'audio du jeu. Les développeurs peuvent générer de l'audio et manipuler des échantillons audio tout en positionnant le son dans l'espace de jeu 3D.</p>

<p>Une stratégie inter-navigateurs envisageable serait de fournir un son basique à l'aide de l'élément standard {{HTMLElement ("audio")}} et, là où cela est pris en charge, d'améliorer l'expérience en utilisant l'API Web Audio.</p>

<div class="note">
<p><strong>Note :</strong> De manière significative, iOS Safari prend désormais en charge l'API Web Audio, ce qui signifie qu'il est désormais possible d'écrire des jeux Web avec de l'audio de qualité native pour iOS.</p>
</div>

<p>Comme l'API Web Audio permet un timing et un contrôle précis de la lecture audio, nous pouvons l'utiliser pour jouer des échantillons à des moments spécifiques, ce qui est un aspect immersif crucial du jeu. Vous voulez que ces explosions soient<strong> accompagnées</strong> par un boom tonitruant, pas <strong>l'un après les autres</strong>, après tout.</p>

<h3 id="Musique_de_fond_avec_l'API_Web_Audio">Musique de fond avec l'API Web Audio</h3>

<p>Bien que nous puissions utiliser l'élément {{HTMLElement ("audio")}} pour fournir une musique de fond linéaire, qui ne change pas en réaction à l'environnement du jeu, l'API Web Audio est idéale pour implémenter une expérience musicale plus dynamique. Vous pouvez vouloir que la musique change selon que vous essayez de créer du suspense ou d'encourager le joueur d'une manière ou d'une autre. La musique est une partie importante de l'expérience de jeu et, selon le type de jeu, vous voudrez peut-être investir des efforts considérables pour bien faire les choses.</p>

<p>Une façon de rendre votre musique plus dynamique est de la diviser en boucles ou en pistes de composant. C'est souvent la façon dont les musiciens composent la musique de toute façon, et l'API Web Audio est extrêmement efficace pour garder ces parties synchronisées. Une fois que vous avez les différentes pistes qui composent votre morceau, vous pouvez apporter des pistes ou en retirer de la façon appropriée.</p>

<p>Vous pouvez également appliquer des filtres ou des effets à la musique. Votre personnage est-il dans une grotte ? Augmentez l'écho. Peut-être que vous avez des scènes sous-marines, alors appliquez un filtre qui étouffe le son.</p>

<p>Regardons quelques techniques de l'API Web Audio pour ajuster dynamiquement la musique à partir de ses pistes de base.</p>

<h3 id="Chargement_des_pistes">Chargement des pistes</h3>

<p>Avec l'API Web Audio, vous pouvez charger individuellement des pistes et des boucles séparées en utilisant  <a href="/fr/docs/Web/API/XMLHttpRequest"><code>XMLHttpRequest</code></a>, ce qui signifie que vous pouvez les charger de manière synchrone ou en parallèle. Le chargement synchrone peut signifier que certaines parties de votre musique sont prêtes plus tôt et vous pouvez commencer à les jouer pendant que d'autres se chargent.</p>

<p>De toute façon, vous pouvez vouloir synchroniser des pistes ou des boucles. L'API Web Audio contient la notion d'horloge interne qui commence à cocher le moment où vous créez un contexte audio. Vous devez prendre en compte le temps entre la création d'un contexte audio et le moment où la première piste audio commence à jouer. L'enregistrement de ce décalage et l'interrogation de l'heure actuelle de la piste de lecture vous donnent suffisamment d'informations pour synchroniser des morceaux audio distincts.</p>

<p>Pour voir cela en action, mettons en place des pistes distinctes :</p>

<pre class="brush: html">ul&gt;
  &lt;li&gt;&lt;a class="track" href="http://jPlayer.org/audio/mp3/gbreggae-leadguitar.mp3"&gt;Lead Guitar&lt;/a&gt;&lt;/li&gt;
  &lt;li&gt;&lt;a class="track" href="http://jPlayer.org/audio/mp3/gbreggae-drums.mp3"&gt;Drums&lt;/a&gt;&lt;/li&gt;
  &lt;li&gt;&lt;a class="track" href="http://jPlayer.org/audio/mp3/gbreggae-bassguitar.mp3"&gt;Bass Guitar&lt;/a&gt;&lt;/li&gt;
  &lt;li&gt;&lt;a class="track" href="http://jPlayer.org/audio/mp3/gbreggae-horns.mp3"&gt;Horns&lt;/a&gt;&lt;/li&gt;
  &lt;li&gt;&lt;a class="track" href="http://jPlayer.org/audio/mp3/gbreggae-clav.mp3"&gt;Clavi&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;</pre>

<p>Toutes ces pistes ont le même tempo et sont conçues pour être synchronisées les unes avec les autres.</p>

<pre class="brush: js">window.AudioContext = window.AudioContext || window.webkitAudioContext;

var offset = 0;
var context = new AudioContext();

function playTrack(url) {
  var request = new XMLHttpRequest();
  request.open('GET', url, true);
  request.responseType = 'arraybuffer';

  var audiobuffer;

  // Decode asynchronously
  request.onload = function() {

    if (request.status == 200) {

      context.decodeAudioData(request.response, function(buffer) {
        var source = context.createBufferSource();
        source.buffer = buffer;
        source.connect(context.destination);
        console.log('context.currentTime ' + context.currentTime);

        if (offset == 0) {
          source.start();
          offset = context.currentTime;
        } else {
          source.start(0,context.currentTime - offset);
        }

      }, function(e) {
        console.log('Error decoding audio data:' + e);
      });
    } else {
      console.log('Audio didn\'t load successfully; error code:' + request.statusText);
    }
  }
  request.send();
}

var tracks = document.getElementsByClassName('track');

for (var i = 0, len = tracks.length; i &lt; len; i++) {
  tracks[i].addEventListener('click', function(e){

    playTrack(this.href);
    e.preventDefault();
  });
}</pre>

<div class="note">
<p><strong>Note :</strong> Vous pouvez essayer notre <a href="http://jsfiddle.net/c87z11jj/1/">démo multipiste API Web Audio</a> sur JSFiddle.</p>
</div>

<p>Regardons maintenant le code. Nous créons d'abord un nouveau {{domxref ("AudioContext")}} et créons une fonction <code>(playTrack ())</code> qui charge et commence à jouer une piste.</p>

<p><code>start()</code> (anciennement appelé <code>noteOn ())</code> commence à lire un élément audio. <code>start ()</code> demande trois paramètres (facultatifs) :</p>

<ol>
 <li>when <em>(quand)</em> : le temps absolu pour commencer la lecture .</li>
 <li>where (offset) <em>(où)</em> : la partie de l'audio qui doit commencer à être jouée.</li>
 <li>how long <em>(combien de temps)</em> : la durée pendant laquelle elle doit être jouée.</li>
</ol>

<p><code>stop()</code> prend un paramètre facultatif - when - qui est le délai avant l'arrêt.<br>
 <br>
 Si le second paramètre de <code>start ()</code> —   the offset (<em>le décalage</em>)  —  est nul, nous commençons à jouer dès le début l'audio donné ; ce que nous faisons en premier. Nous stockons ensuite le {{domxref ("AudioContext.currentTime")}}  —  le décalage de la première lecture de la pièce, soustrayons celle des temps actuels pour calculer l'heure réelle, et utilisons cela pour synchroniser nos pistes.<br>
 <br>
 Dans le contexte de votre monde de jeu, vous pouvez avoir des boucles et des échantillons qui sont joués dans différentes circonstances, et il peut être utile de pouvoir les synchroniser avec d'autres pistes pour une expérience plus transparente.</p>

<div class="note">
<p><strong>Note :</strong> Cet exemple n'attend pas la fin du battement avant d'introduire le morceau suivant; nous pourrions le faire si nous connaissions le BPM (battement par minute) des pistes.</p>
</div>

<p>Vous pouvez trouver que l'introduction d'une nouvelle piste sonne plus naturelle si elle entre dans le battement, la mesure ou la phrase, selon l'unité que vous voulez pour votre musique de fond.</p>

<p>Pour ce faire, avant de jouer la piste que vous voulez synchroniser, vous devez calculer combien de temps cela va durer jusqu'au début de la prochaine unité musicale.</p>

<p>Voici un peu de code qui donne un tempo (le temps en secondes de votre battement / mesure), calcule combien de temps attendre pour jouer la partie suivante  —  vous alimentez la valeur initiale de la fonction <code>start ()</code> avec le premier paramètre qui prend le temps absolu de début de la lecture. Notez que le deuxième paramètre (où commencer à jouer à partir de la nouvelle piste) est relatif :</p>

<pre class="brush: js">if (offset == 0) {
  source.start();
  offset = context.currentTime;
} else {
  var relativeTime = context.currentTime - offset;
  var beats = relativeTime / tempo;
  var remainder = beats - Math.floor(beats);
  var delay = tempo - (remainder*tempo);
  source.start(context.currentTime+delay, relativeTime+delay);
}</pre>

<div class="note">
<p><strong>Note :</strong> Ici, vous pouvez <a href="http://jsfiddle.net/c87z11jj/2/">essayer notre code calculateur d'attente</a> , sur JSFiddle (synchronisé à la mesure).</p>
</div>

<div class="note">
<p><strong>Note :</strong> Si le premier paramètre est 0 ou inférieur au contexte <code>currentTime</code>, la musique commence immédiatement.</p>
</div>

<h3 id="Audio_positionnel">Audio positionnel</h3>

<p>L'audio positionnel peut être une technique importante pour faire de l'audio un élément clé d'une expérience de jeu immersive. L'API Web Audio permet non seulement de positionner un certain nombre de sources audio dans un espace tridimensionnel, mais également d'appliquer des filtres qui rendent cet audio plus réaliste.</p>

<p>En bref, en utilisant les capacités positionnelles de l'API Web Audio, nous pouvons relier d'autres informations sur le monde du jeu pour le joueur.</p>

<p>Nous pouvons relier :</p>

<ul>
 <li>la position des objets</li>
 <li>la direction des objets (mouvement de position et génération de l'effet Doppler)</li>
 <li>l'environnement (caverneux, sous-marin, etc.)</li>
</ul>

<p>Ceci est particulièrement utile dans un environnement tridimensionnel rendu en utilisant <a href="/fr/docs/Web/API/WebGL_API">WebGL</a>, avec lequel l'API Web Audio permet d'associer l'audio aux objets et aux points de vue .</p>

<div class="note">
<p><strong>Note :</strong> Voir <a href="/fr/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics">Web Audio API Spatialization Basics</a> <em>(Bases de la spacialisation de l'API Web Audio)</em> pour plus de détails.</p>
</div>

<h2 id="See_Also">See Also</h2>

<ul>
 <li><a href="/fr/docs/Web/API/Web_Audio_API">Web Audio API sur MDN</a></li>
 <li><a href="/fr/docs/Web/HTML/Element/audio"><code>&lt;audio&gt;</code> sur MDN</a></li>
 <li><a href="http://www.html5rocks.com/en/tutorials/webaudio/games/">Developing Game Audio with the Web Audio API (HTML5Rocks) (en)</a></li>
 <li><a href="http://www.html5rocks.com/en/tutorials/webaudio/positional_audio/">Mixing Positional Audio and WebGL (HTML5Rocks) (en)</a></li>
 <li><a href="https://hacks.mozilla.org/2013/10/songs-of-diridum-pushing-the-web-audio-api-to-its-limits/">Songs of Diridum: Pushing the Web Audio API to Its Limits (en)</a></li>
 <li><a href="http://pupunzi.open-lab.com/2013/03/13/making-html5-audio-actually-work-on-mobile/">Making HTML5 Audio Actually Work on Mobile (en)</a></li>
 <li><a href="http://remysharp.com/2010/12/23/audio-sprites/">Audio Sprites (and fixes for iOS) (en)</a><br>
   </li>
</ul>
