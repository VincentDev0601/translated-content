---
title: Accessible multimedia
slug: Learn/Accessibility/Multimedia
tags:
  - Accessibilité
  - Apprendre
  - Audio
  - Débutant
  - HTML
  - Images
  - JavaScript
  - Multimedia
  - Video
translation_of: Learn/Accessibility/Multimedia
original_slug: Apprendre/a11y/Multimedia
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenuNext("Learn/Accessibility/WAI-ARIA_basics","Learn/Accessibility/Mobile", "Learn/Accessibility")}}</div>

<p>Le multimédia est une autre catégorie de contenu susceptible de créer des problèmes d'accessibilité: les contenus vidéo, audio et images doivent disposer de solutions de remplacement textuelles appropriées pour être compris par les technologies d'assistance et leurs utilisateurs. Cet article montre comment.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Conditions requise:</th>
   <td>Connaissances informatiques de base, une compréhension de base de HTML, CSS et JavaScript, une compréhension de <a href="/fr/docs/Apprendre/a11y/What_is_accessibility"> Qu'est ce que l'accessibilité?</a></td>
  </tr>
  <tr>
   <th scope="row">Objectif:</th>
   <td>Comprendre les problèmes d'accessibilité derrière le multimédia et comment les résoudre .</td>
  </tr>
 </tbody>
</table>

<h2 id="Multimédia_et_accessibilité">Multimédia et accessibilité</h2>

<p>Jusqu'ici, dans ce module, nous avons examiné une variété de contenus et ce qui doit être fait pour en assurer l'accessibilité, du simple contenu textuel aux tableaux de données, en passant par les images, les contrôles natifs tels que les éléments de formulaire et les boutons, et des structures de balisage encore plus complexes. (avec  <a href="/fr/docs/Learn/Accessibility/WAI-ARIA_basics">WAI-ARIA</a> l'attribut).</p>

<p>Cet article, par contre, examine une autre catégorie générale de contenu pour laquelle il est difficile d’assurer l’accessibilité au multimédia. Les images, les vidéos, les éléments {{htmlelement ("canvas")}} les animations Flash, etc. ne sont pas aussi faciles à comprendre par les lecteurs d'écran ou à naviguer au clavier, et nous devons leur donner un coup de main.</p>

<p>Mais ne désespérez pas - nous vous aiderons ici à naviguer parmi les techniques disponibles pour rendre le multimédia plus accessible.</p>

<h2 id="Simple_images">Simple images</h2>

<p>Nous avons déjà couvert des alternatives textuelles simples pour les images HTML dans notre article  <a href="/fr/docs/Apprendre/a11y/HTML"> HTML : une bonne base pour l'accessibilité</a>  —  vous pouvez vous y référer pour plus de détails. En bref, vous devez vous assurer que, dans la mesure du possible, le contenu visuel dispose d’un texte alternatif que les lecteurs d’écran peuvent lire et lire à leurs utilisateurs.</p>

<p>Par exemple:</p>

<pre class="brush: html">&lt;img src="dinosaur.png"
     alt=" Un Tyrannosaure Rex rouge: Un dinosaure a deux pattes se tenant droit comme un humain, avec de petits bras et une grosse tete avec beaucoup de dents acerees ."&gt;
</pre>

<h2 id="Commandes_audio_et_vidéo_accessibles">Commandes audio et vidéo accessibles</h2>

<p>La mise en œuvre de contrôles audio / vidéo sur le Web ne devrait pas poser de problème, n'est-ce pas? Enquêtons .</p>

<h3 id="Le_problème_avec_les_contrôles_HTML5_natifs">Le problème avec les contrôles HTML5 natifs</h3>

<p>Les instances audio et vidéo HTML5 sont même fournies avec un ensemble de commandes intégrées vous permettant de contrôler le contenu multimédia directement. Par exemple (voir  <code>native-controls.html</code> <a href="https://github.com/mdn/learning-area/blob/master/accessibility/multimedia/native-controls.html">code source</a> et <a href="https://mdn.github.io/learning-area/accessibility/multimedia/native-controls.html">en direct</a>):</p>

<pre class="brush: html">&lt;audio controls&gt;
  &lt;source src="viper.mp3" type="audio/mp3"&gt;
  &lt;source src="viper.ogg" type="audio/ogg"&gt;
  &lt;p&gt; Votre navigateur ne supporte pas l\'audio HTML5. Voici un &lt;a href="viper.mp3"&gt; lien vers l\'audio &lt;/a&gt;  au lieu .&lt;/p&gt;
&lt;/audio&gt;

&lt;br&gt;

&lt;video controls&gt;
  &lt;source src="rabbit320.mp4" type="video/mp4"&gt;
  &lt;source src="rabbit320.webm" type="video/webm"&gt;
  &lt;p&gt;Votre navigateur ne supporte pas l\'audio HTML5. Voici un &lt;a href="rabbit320.mp4"&gt;lien vers la video&lt;/a&gt; instead.&lt;/p&gt;
&lt;/video&gt;</pre>

<p>L'attribut controls comporte des boutons de lecture / pause, une barre de recherche, etc. - les commandes de base que vous êtes en droit d'attendre d'un lecteur multimédia. Il semble que dans Firefox et Chrome :</p>

<p><img alt="Screenshot of Video Controls in Firefox" src="native-controls-firefox.png"></p>

<p><img alt="Screenshot of Video Controls in Chrome" src="native-controls-chrome.png"></p>

<p>Cependant, il y a des problèmes avec ces contrôles :</p>

<ul>
 <li>Ils ne sont pas accessibles au clavier, dans aucun navigateur, sauf Opera.</li>
 <li>Différents navigateurs donnent aux contrôles natifs un style et des fonctionnalités différents. Ils ne sont pas stylables, ce qui signifie qu'ils ne peuvent pas être facilement conçus pour suivre un guide de style du site. .</li>
</ul>

<p>Pour remédier à cela, nous pouvons créer nos propres contrôles personnalisés. Regardons comment.</p>

<h3 id="Création_de_contrôles_audio_et_vidéo_personnalisés">Création de contrôles audio et vidéo personnalisés</h3>

<p>La vidéo et l'audio HTML5 partagent une API - HTML Media Element - qui vous permet de mapper des fonctionnalités personnalisées à des boutons et à d'autres commandes, que vous définissez vous-même. .</p>

<p>Prenons l'exemple vidéo ci-dessus et ajoutons-leur des contrôles personnalisés .</p>

<h4 id="Basic_setup">Basic setup</h4>

<p>Tout d'abord, prenez une copie de notre  <a href="https://github.com/mdn/learning-area/blob/master/accessibility/multimedia/custom-controls-start.html">custom-controls-start.html</a>, <a href="https://github.com/mdn/learning-area/blob/master/accessibility/multimedia/custom-controls.css">custom-controls.css</a>, <a href="https://raw.githubusercontent.com/mdn/learning-area/master/accessibility/multimedia/rabbit320.mp4">rabbit320.mp4</a>, et <a href="https://raw.githubusercontent.com/mdn/learning-area/master/accessibility/multimedia/rabbit320.webm">rabbit320.webm</a> fichiers et enregistrez-les dans un nouveau répertoire sur votre disque dur .</p>

<p>Créez un nouveau fichier appelé main.js et enregistrez-le dans le même répertoire .</p>

<p>Tout d’abord, regardons le code HTML pour le lecteur vidéo, dans le code HTML:</p>

<pre class="brush: html">&lt;section class="player"&gt;
  &lt;video controls&gt;
    &lt;source src="rabbit320.mp4" type="video/mp4"&gt;
    &lt;source src="rabbit320.webm" type="video/webm"&gt;
    &lt;p&gt;Votre navigateur ne supporte pas l\'audio HTML5. Voici un &lt;a href="rabbit320.mp4"&gt;lien vers la video&lt;/a&gt; instead.&lt;/p&gt;
  &lt;/video&gt;

  &lt;div class="controls"&gt;
    &lt;button class="playpause"&gt;Play&lt;/button&gt;
    &lt;button class="stop"&gt;Stop&lt;/button&gt;
    &lt;button class="rwd"&gt;Rwd&lt;/button&gt;
    &lt;button class="fwd"&gt;Fwd&lt;/button&gt;
    &lt;div class="time"&gt;00:00&lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;</pre>

<h4 id="JavaScript_basic_setup">JavaScript basic setup</h4>

<p>Nous avons inséré quelques boutons de commande simples sous notre vidéo. Bien sûr, ces contrôles ne feront rien par défaut; pour ajouter des fonctionnalités, nous allons utiliser JavaScript .</p>

<p>Nous devrons d’abord stocker les références à chacun des contrôles - ajoutez ce qui suit en haut de votre fichier JavaScript:</p>

<pre class="brush: js">var playPauseBtn = document.querySelector('.playpause');
var stopBtn = document.querySelector('.stop');
var rwdBtn = document.querySelector('.rwd');
var fwdBtn = document.querySelector('.fwd');
var timeLabel = document.querySelector('.time');</pre>

<p>Ensuite, nous devons saisir une référence au lecteur vidéo / audio lui-même - ajoutez cette ligne sous les lignes précédentes:</p>

<pre class="brush: js">var player = document.querySelector('video');</pre>

<p>Ceci contient une référence à un objet {{domxref ("HTMLMediaElement")}} qui possède plusieurs propriétés et méthodes utiles disponibles qui peuvent être utilisées pour connecter des fonctionnalités à nos boutons.</p>

<p>Avant de passer à la création de notre fonctionnalité de bouton, supprimons les contrôles natifs afin qu'ils ne gênent pas nos contrôles personnalisés. Ajoutez ce qui suit, encore une fois au bas de votre JavaScript:</p>

<pre class="brush: js">player.removeAttribute('controls');</pre>

<p>Le fait de procéder ainsi plutôt que de ne pas inclure les attributs de contrôle en premier lieu présente l'avantage que si notre JavaScript échoue pour une raison quelconque, l'utilisateur dispose toujours de certains contrôles.</p>

<h4 id="Câbler_nos_boutons">Câbler nos boutons</h4>

<p>Commençons par configurer le bouton lecture / pause. Nous pouvons le faire basculer entre lecture et pause avec une simple fonction conditionnelle, comme ci-dessous. Ajoutez-le à votre code, en bas:</p>

<pre class="brush: js">playPauseBtn.onclick = function() {
  if(player.paused) {
    player.play();
    playPauseBtn.textContent = 'Pause';
  } else {
    player.pause();
    playPauseBtn.textContent = 'Play';
  }
};</pre>

<p>Ensuite, ajoutez ce code en bas, qui contrôle le bouton d'arrêt:</p>

<pre class="brush: js">stopBtn.onclick = function() {
  player.pause();
  player.currentTime = 0;
  playPauseBtn.textContent = 'Play';
};</pre>

<p>Il n'y a pas de fonction  <code>stop()</code>  disponible sur {{domxref("HTMLMediaElement")}}s,  nous le mettons donc en <code>pause()</code>  et, dans le même temps, définissons la valeur <code>currentTime</code> sur 0.</p>

<p>Ensuite, nos boutons de rembobinage et d’avance rapide - ajoutez les blocs suivants au bas de votre  code:</p>

<pre class="brush: js">rwdBtn.onclick = function() {
  player.currentTime -= 3;
};

fwdBtn.onclick = function() {
  player.currentTime += 3;
  if(player.currentTime &gt;= player.duration || player.paused) {
    player.pause();
    player.currentTime = 0;
    playPauseBtn.textContent = 'Play';
  }
};</pre>

<p>Celles-ci sont très simples, il suffit d’ajouter ou de soustraire 3 secondes à   <code>currentTime</code> chaque fois qu’on clique dessus. Dans un vrai lecteur vidéo, vous voudrez probablement une barre de recherche plus élaborée, ou similaire.</p>

<p>Notez que nous vérifions également si la durée  <code>currentTime</code> est supérieure à la durée totale du support ou si le support n'est pas en cours de lecture lorsque le bouton Fwd est enfoncé. Si l'une ou l'autre de ces conditions est vraie, nous arrêtons simplement la vidéo pour éviter que l'interface utilisateur ne se détériore si elle tente d'effectuer une avance rapide lorsque la vidéo n'est pas en cours de lecture ou si la fin de la vidéo est terminée. .</p>

<p>Enfin, ajoutez ce qui suit à la fin du code pour contrôler l’affichage du temps écoulé:</p>

<pre class="brush: js">player.ontimeupdate = function() {
  var minutes = Math.floor(player.currentTime / 60);
  var seconds = Math.floor(player.currentTime - minutes * 60);
  var minuteValue;
  var secondValue;

  if (minutes&lt;10) {
    minuteValue = "0" + minutes;
  } else {
    minuteValue = minutes;
  }

  if (seconds&lt;10) {
    secondValue = "0" + seconds;
  } else {
    secondValue = seconds;
  }

  mediaTime = minuteValue + ":" + secondValue;
  timeLabel.textContent = mediaTime;
};</pre>

<p>Chaque fois que l'heure est mise à jour (une fois par seconde), nous activons cette fonction. Il calcule le nombre de minutes et de secondes à partir de la valeur actuelle donnée en secondes, ajoute un 0 au début si la valeur de minute ou de seconde est inférieure à 10, puis crée la lecture d'affichage et l'ajoute à l'étiquette de temps.</p>

<h4 id="Lectures_complémentaires">Lectures complémentaires</h4>

<p>Cela vous donne une idée de base sur la manière d’ajouter des fonctionnalités de lecteur personnalisées aux instances de lecteur vidéo / audio. Pour plus d'informations sur l'ajout de fonctionnalités plus complexes aux lecteurs vidéo / audio, y compris les solutions de secours Flash pour les navigateurs plus anciens, voir aussi:</p>

<ul>
 <li><a href="/fr/docs/Web/Apps/Fundamentals/Audio_and_video_delivery">Audio and video delivery</a></li>
 <li><a href="/fr/docs/Web/Apps/Fundamentals/Audio_and_video_delivery/Video_player_styling_basics">Video player styling basics</a></li>
 <li><a href="/fr/docs/Web/Apps/Fundamentals/Audio_and_video_delivery/cross_browser_video_player">Creating a cross-browser video player</a></li>
</ul>

<p>Nous avons également créé un exemple avancé pour montrer comment créer un système orienté objet permettant de rechercher tous les lecteurs vidéo et audio de la page (quel que soit leur nombre) et d'y ajouter nos contrôles personnalisés. Voir  <a href="http://mdn.github.io/learning-area/accessibility/multimedia/custom-controls-OOJS/">custom-controls-oojs</a> ( également <a href="https://github.com/mdn/learning-area/tree/master/accessibility/multimedia/custom-controls-OOJS">voir le code source</a>).</p>

<h2 id="Transcriptions_audio">Transcriptions audio</h2>

<p>Pour permettre aux sourds d'accéder au contenu audio, vous devez créer des transcriptions de texte. Ceux-ci peuvent être soit inclus sur la même page que l'audio d'une manière ou d'une autre, soit inclus sur une page séparée et liés à.</p>

<p>En termes de création de la transcription, vos options sont les suivantes:</p>

<ul>
 <li>Services commerciaux - Vous pouvez payer un professionnel pour effectuer la transcription, voir par exemple des entreprises telles que  <a href="https://scribie.com/">Scribie</a>, <a href="https://castingwords.com/">Casting Words</a>, ou <a href="https://www.rev.com/">Rev</a>. Regardez autour de vous et demandez conseil pour vous assurer de trouver une entreprise fiable avec laquelle vous pourrez travailler efficacement.</li>
 <li>Communauté / base / auto-transcription - Si vous faites partie d'une communauté ou d'une équipe active sur votre lieu de travail, vous pouvez leur demander de l'aide pour faire les traductions. Vous pouvez même essayer de les faire vous-même.</li>
 <li>Services automatisés - Des services d'intelligence artificielle sont disponibles, tels que   <a href="https://trint.com">Trint</a>. Téléchargez un fichier vidéo / audio sur le site, qui le transcrivera automatiquement pour vous. Sur YouTube, vous pouvez choisir de générer des sous-titres / transcriptions automatisés. Selon la clarté de l'audio parlé, la qualité de la transcription résultante variera considérablement. . </li>
</ul>

<p>Comme dans la plupart des choses de la vie, vous avez tendance à avoir ce que vous payez. la précision et le temps requis pour produire la transcription varient selon les services. Si vous payez une transcription pour une entreprise digne de confiance ou un service d’AI, vous le ferez probablement rapidement et avec une qualité élevée. Si vous ne voulez pas payer pour cela, vous le ferez probablement avec une qualité inférieure et / ou lentement.</p>

<p>Il n’est pas acceptable de publier une ressource audio mais de promettre de publier la transcription ultérieurement. De telles promesses ne sont souvent pas tenues, ce qui érodera la confiance entre vous et vos utilisateurs. Si le son que vous présentez ressemble à une réunion en face-à-face ou à une performance parlée en direct, il serait acceptable de prendre des notes pendant la performance, de les publier intégralement avec l'audio, puis de demander de l'aide pour les nettoyer par la suite.</p>

<h3 id="Exemples_de_transcription">Exemples de transcription</h3>

<p>Si vous utilisez un service automatisé, vous devrez probablement utiliser l'interface utilisateur fournie par l'outil. Par exemple, jetez un coup d’œil à  <a href="https://www.youtube.com/watch?v=zFFBsj97Od8">Audio Transcription Sample 1</a> <em>et choisissez plus &gt; Transcript</em>.</p>

<p>Si vous créez votre propre interface utilisateur pour présenter votre audio et la transcription associée, vous pouvez le faire comme bon vous semble, mais il serait peut-être judicieux de l'inclure dans un panneau pouvant être affiché / masqué; voir notre exemple  <a href="https://mdn.github.io/learning-area/accessibility/multimedia/audio-transcript-ui/">transcription audio-ui</a> exemple (voir aussi le <a href="https://github.com/mdn/learning-area/tree/master/accessibility/multimedia/audio-transcript-ui">code source</a>).</p>

<h3 id="Descriptions_audio">Descriptions audio</h3>

<p>Dans les cas où des éléments visuels accompagnent votre son, vous devez fournir une description de l’audio pour décrire ce contenu supplémentaire.</p>

<p>Dans de nombreux cas, il s'agira simplement d'une vidéo. Dans ce cas, vous pouvez implémenter des légendes à l'aide des techniques décrites dans la section suivante de l'article.</p>

<p>Cependant, il y a des cas extrêmes. Vous pouvez par exemple avoir un enregistrement audio d'une réunion qui fait référence à une ressource d'accompagnement telle qu'une feuille de calcul ou un graphique. Dans de tels cas, vous devez vous assurer que les ressources sont fournies avec la transcription audio +, et les lier spécifiquement aux endroits où elles sont mentionnées dans la transcription. Cela aidera évidemment tous les utilisateurs, pas seulement les sourds.</p>

<div class="note">
<p><strong>Note :</strong> Une transcription audio aidera en général plusieurs groupes d'utilisateurs. En plus de permettre aux utilisateurs sourds d'accéder aux informations contenues dans l'audio, pensez à un utilisateur disposant d'une connexion à faible bande passante et qui trouverait que le téléchargement de l'audio est gênant. Pensez également à un utilisateur dans un environnement bruyant, comme un pub ou un bar, qui tente d'accéder à l'information mais ne l'entend pas par dessus le bruit.</p>
</div>

<h2 id="Pistes_de_texte_vidéo">Pistes de texte vidéo</h2>

<p>Pour rendre la vidéo accessible aux sourds, aux aveugles ou même à d'autres groupes d'utilisateurs (par exemple, ceux dont la bande passante est faible ou qui ne comprennent pas la langue dans laquelle la vidéo est enregistrée), vous devez inclure des pistes de texte avec votre contenu vidéo. .</p>

<div class="note">
<p><strong>Note :</strong> Les pistes de texte sont également utiles pour n'importe quel utilisateur, pas seulement pour les personnes handicapées. Par exemple, certains utilisateurs peuvent ne pas être en mesure d’entendre le son car ils se trouvent dans des environnements bruyants (comme un bar bondé lorsqu’un match de sport est diffusé) ou peuvent ne pas déranger les autres s’ils sont dans un endroit calme (comme une bibliothèque). .)</p>
</div>

<p>Ce n'est pas un nouveau concept - les sous-titres codés sont disponibles depuis assez longtemps dans les services de télévision:</p>

<p><img alt='Frame from an old-timey cartoon with closed captioning "Good work, Goldie. Keep it up!"' src="closed-captions.png"></p>

<p>Alors que de nombreux pays proposent des films en anglais avec sous-titres écrits dans leur propre langue maternelle, des sous-titres en différentes langues sont souvent disponibles sur DVD, par exemple</p>

<p><img alt='An English film with German subtitles "Emo, warum erkennst du nicht die Schonheit dieses Ortes?"' src="Subtitles_German.jpg"></p>

<p>Il existe différents types de pistes de texte avec des objectifs différents. Les principaux que vous rencontrerez sont:</p>

<ul>
 <li>Sous-titres - pour le bénéfice des utilisateurs sourds qui ne peuvent pas entendre la piste audio, y compris les mots prononcés, et des informations contextuelles telles que le nom des personnes qui ont prononcé ces mots, si les personnes étaient en colère ou tristes et quelle ambiance la musique crée actuellement. .</li>
 <li>Sous-titres - Inclut les traductions de la boîte de dialogue audio, pour les utilisateurs qui ne comprennent pas la langue parlée.</li>
 <li>Descriptions - Celles-ci incluent des descriptions pour les personnes aveugles qui ne peuvent pas voir la vidéo, par exemple à quoi ressemble la scène.</li>
 <li>Titres de chapitre - Marqueurs de chapitre destinés à aider l'utilisateur à naviguer dans la ressource multimédia.</li>
</ul>

<h3 id="Implémentation_de_pistes_de_texte_vidéo_HTML5">Implémentation de pistes de texte vidéo HTML5</h3>

<p>Les pistes de texte à afficher avec une vidéo HTML5 doivent être écrites au format WebVTT, un format de texte contenant plusieurs chaînes de texte ainsi que des métadonnées, telles que l'heure à laquelle vous souhaitez afficher chaque chaîne de texte et même des informations de style / positionnement limitées. Ces chaînes de texte sont appelées cues .</p>

<p>Un fichier WebVTT typique ressemblera à ceci:</p>

<pre>WEBVTT

1
00:00:22.230 --&gt; 00:00:24.606
 Ceci est le premier sous-titre.

2
00:00:30.739 --&gt; 00:00:34.074
 C'est le deuxième .

  ...</pre>

<p>Pour que ceci soit affiché avec la lecture du média HTML, vous devez:</p>

<ul>
 <li>Enregistrez-le en tant que fichier .vtt dans un endroit approprié.</li>
 <li>Lien vers le fichier .vtt avec  l'élément {{htmlelement("track")}} . <code>&lt;track&gt;</code>  devrait être placé dans <code>&lt;audio&gt;</code> ou <code>&lt;video&gt;</code>,  mais après tout  <code>&lt;source&gt;</code> éléments .  Utilisez l’attribut {{htmlattrxref ("kind", "track")}} pour indiquer si les signaux sont des sous-titres, des légendes ou des descriptions. De plus, utilisez {{htmlattrxref ("srclang", "track")}} pour indiquer au navigateur la langue dans laquelle vous avez écrit les sous-titres. .</li>
</ul>

<p>Voici un exemple:</p>

<pre class="brush: html">&lt;video controls&gt;
    &lt;source src="example.mp4" type="video/mp4"&gt;
    &lt;source src="example.webm" type="video/webm"&gt;
    &lt;track kind="subtitles" src="subtitles_en.vtt" srclang="en"&gt;
&lt;/video&gt;</pre>

<p>Cela donnera une vidéo avec des sous-titres affichés, un peu comme ceci:</p>

<p><img alt='Video player with standard controls such as play, stop, volume, and captions on and off. The video playing shows a scene of a man holding a spear-like weapon, and a caption reads "Esta hoja tiene pasado oscuro."' src="video-player-with-captions.png"></p>

<p>Pour plus de détails, veuillez lire  <a href="/fr/docs/Web/Guide/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video">Ajouter des légendes et des sous titres à des vidéos HTML 5</a>.  Vous trouverez <a href="http://iandevlin.github.io/mdn/video-player-with-captions/">un exemple</a>  qui accompagne cet article sur Github, écrit par Ian Devlin (voir aussi le <a href="https://github.com/iandevlin/iandevlin.github.io/tree/master/mdn/video-player-with-captions">code source</a>.) Cet exemple utilise du JavaScript. pour permettre aux utilisateurs de choisir entre différents sous-titres. Notez que pour activer les sous-titres, vous devez appuyer sur le bouton "CC" et sélectionner une option - Anglais, Allemand ou Español.</p>

<div class="note">
<p><strong>Note :</strong> Les pistes de texte et les transcriptions vous aident également avec {{glossary ("SEO")}}, car les moteurs de recherche se développent particulièrement bien avec le texte. Les pistes de texte permettent même aux moteurs de recherche de se lier directement à un endroit en cours de vidéo.</p>
</div>

<h2 id="Autre_contenu_multimédia">Autre contenu multimédia</h2>

<p>Les sections ci-dessus ne couvrent pas tous les types de contenu multimédia que vous pourriez vouloir placer sur une page Web. Vous devrez peut-être également gérer des jeux, des animations, des diaporamas, des vidéos intégrées et du contenu créé à l'aide d'autres technologies disponibles, telles que:</p>

<ul>
 <li><a href="/fr/docs/Web/API/Canvas_API">HTML5 canvas</a></li>
 <li>Flash</li>
 <li>Silverlight</li>
</ul>

<p>Pour ce type de contenu, vous devez traiter les problèmes d’accessibilité au cas par cas. Dans certains cas, ce n'est pas si grave, par exemple:</p>

<ul>
 <li>Si vous intégrez du contenu audio à l'aide d'une technologie de plug-in telle que Flash ou Silverlight, vous pouvez probablement simplement fournir une transcription audio de la même manière que celle décrite ci-dessus dans la section {{anch("Transcript examples")}} .</li>
 <li>Si vous intégrez du contenu vidéo à l'aide d'une technologie de plug-in telle que Flash ou Silverlight, vous pouvez tirer parti des techniques de sous-titrage / sous-titrage disponibles pour ces technologies. Par exemple, voir  <a href="http://www.adobe.com/accessibility/products/flash/captions.html">Flash captions</a>, <a href="https://support.brightcove.com/en/video-cloud/docs/using-flash-only-player-api-closed-captioning">Using the Flash-Only Player API for Closed Captioning</a>, ou <a href="https://blogs.msdn.microsoft.com/anilkumargupta/2009/05/01/playing-subtitles-with-videos-in-silverlight/">Playing Subtitles with Videos in Silverlight</a>.</li>
</ul>

<p>Cependant, il est difficile de rendre les autres multimédias accessibles. Si, par exemple, vous avez affaire à un jeu immersif en 3D ou à une application de réalité virtuelle, il est vraiment difficile de fournir des alternatives textuelles pour une telle expérience, et vous pouvez soutenir que les utilisateurs non-voyants ne sont pas vraiment dans le groupe-cible de telles applications.</p>

<p>Vous pouvez toutefois vous assurer qu'une telle application présente un contraste de couleur suffisant et une présentation claire de sorte qu'elle soit perceptible par les personnes ayant une vision basse / daltonisme, et qu'elle soit également accessible au clavier. Rappelez-vous que l'accessibilité consiste à faire tout ce que vous pouvez, plutôt que de chercher à atteindre une accessibilité à 100% tout le temps, ce qui est souvent impossible.</p>

<h2 id="Résumé">Résumé</h2>

<p>Ce chapitre présente un résumé des problèmes d’accessibilité des contenus multimédias, ainsi que des solutions pratiques.</p>

<p>{{PreviousMenuNext("Learn/Accessibility/WAI-ARIA_basics","Learn/Accessibility/Mobile", "Learn/Accessibility")}}</p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Apprendre/a11y/What_is_accessibility">Qu'est ce que l'accessibilité?</a></li>
 <li><a href="/fr/docs/Apprendre/a11y/HTML">HTML : une bonne base pour l'accessibilité</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/CSS_and_JavaScript">CSS and JavaScript accessibility best practices</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/WAI-ARIA_basics">WAI-ARIA basics</a></li>
 <li><a href="/fr/docs/Apprendre/a11y/Multimedia">Accessible multimedia</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/Mobile">Mobile accessibility</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/Accessibility_troubleshooting">Accessibility troubleshooting</a></li>
</ul>

