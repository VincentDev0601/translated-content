---
title: Manipulation vidéo avec la balise canvas
slug: Web/API/Canvas_API/Manipulating_video_using_canvas
tags:
  - Canvas
  - Video
translation_of: Web/API/Canvas_API/Manipulating_video_using_canvas
original_slug: HTML/Manipulating_video_using_canvas
---
<p>{{CanvasSidebar}}</p>

<p>En combinant les possibilités de l'élément <a href="/En/HTML/Element/Video"><code>video</code></a> avec celles de l'élément <a href="/en/HTML/Canvas"><code>canvas</code></a>, vous pouvez manipuler les données vidéos en temps réel, et y incorporer une variété d'effets visuels. Ce tutoriel explique comment réaliser un travail d'incrustation "chroma-keying" (<em>fond vert</em>) en utilisant JavaScript.</p>

<p><a href="/samples/video/chroma-key/index.xhtml">Voir l'exemple</a>.</p>

<h2 id="Le_contenu_du_document">Le contenu du document</h2>

<p>Le document XHTML utilisé pour rendre ce contenu est montré ci-dessous :</p>

<pre class="brush: html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;style&gt;
      body {
        background: black;
        color:#CCCCCC;
      }
      #c2 {
        background-image: url(foo.png);
        background-repeat: no-repeat;
      }
      div {
        float: left;
        border :1px solid #444444;
        padding:10px;
        margin: 10px;
        background:#3B3B3B;
      }
    &lt;/style&gt;
    &lt;script type="text/javascript" src="main.js"&gt;&lt;/script&gt;
  &lt;/head&gt;

  &lt;body onload="processor.doLoad()"&gt;
    &lt;div&gt;
      &lt;video id="video" src="video.ogv" controls="true"/&gt;
    &lt;/div&gt;
    &lt;div&gt;
      &lt;canvas id="c1" width="160" height="96"&gt;&lt;/canvas&gt;
      &lt;canvas id="c2" width="160" height="96"&gt;&lt;/canvas&gt;
    &lt;/div&gt;
  &lt;/body&gt;
&lt;/html&gt;</pre>

<p>Les éléments clés à retenir sont :</p>

<ol>
 <li>Ce document dispose de deux balises <a href="/fr/docs/Web/HTML/Element/canvas"><code>canvas</code></a>, avec les IDs <code>c1 </code>et <code>c2 :</code> l'élément <code>c1</code> est utilisé pour afficher l'image courante de la vidéo originale, pendant que <code>c2</code> est utilisé pour afficher la vidéo après application de l'effet d'incrustation ; <code>c2</code> est préchargé avec la même image que celle qui sera utilisée pour le remplacement du fond vert.</li>
 <li>Le code JavaScript est importé dans le script nommé <code>main.js</code> ; Ce script utilise les fonctionnalités propres à la version 1.8, aussi cette version est précisée, à la ligne 22, quand le script est importé.</li>
 <li>Quand le document se charge, la méthode <code>processor.doLoad()</code>, dans le script <code>main.js</code>, est exécutée.</li>
</ol>

<h2 id="Le_code_JavaScript">Le code JavaScript</h2>

<p>Le code JavaScript <code>main.js</code> est composé de trois méthodes.</p>

<h3 id="Initialisation_du_lecteur_avec_effet_d'incrustation_(chroma-key)">Initialisation du lecteur avec effet d'incrustation (<em>chroma-key</em>)</h3>

<p>La métode <code>doLoad()</code> est appelée quand le document XHTML se charge. Cette méthode sert à initialiser chaque variable nécessaire au code traitant l'incrustation (<em>chroma-key</em>), ainsi qu'à associer un écouteur d'évènement qui détectera le moment où l'utilisateur lancera la vidéo.</p>

<pre class="brush: js">var processor;

  processor.doLoad = function doLoad() {
    this.video = document.getElementById('video');
    this.c1 = document.getElementById('c1');
    this.ctx1 = this.c1.getContext('2d');
    this.c2 = document.getElementById('c2');
    this.ctx2 = this.c2.getContext('2d');
    let self = this;
    this.video.addEventListener('play', function() {
        self.width = self.video.videoWidth / 2;
        self.height = self.video.videoHeight / 2;
        self.timerCallback();
      }, false);
  },</pre>

<p>Le code récupère les références aux élément XHTML qui nous intéressent, à savoir l'élément <code>video</code> et les deux éléments <code>canvas</code>. Il définit également les contextes graphique de chacun des éléments <code>canvas</code>. Ce sera utile pour la suite, lorsque nous créerons l'effet d'incrustation.</p>

<p>Ensuite, l'écouteur d'évènement <code>addEventListener()</code> est appelé sur l'élément <code>video</code> pour détecter le moment où l'utilisateur va cliquer sur le bouton de lecture. Dès lors, le code récupère la hauteur et la largeur de la vidéo, que l'on divise par deux (nécessaire pour plus tard effectuer l'effet d'incrustation), puis on appelle la méthode <code>timerCallback()</code> pour surveiller l'avancement de la vidéo et appliquer l'effet visuel.</p>

<h3 id="Le_rappel_du_minuteur">Le rappel du minuteur</h3>

<p>Le rappel du minuteur est initialisé lorsque la vidéo commence à jouer (lorsque l'événement "play" se produit), puis est chargé d'établir le rappel périodique afin de lancer l'effet d'ajustement pour chaque "frame".</p>

<pre class="brush: js">processor.timerCallback = function timerCallback() {
    if (this.video.paused || this.video.ended) {
      return;
    }
    this.computeFrame();
    let self = this;
    setTimeout(function() {
        self.timerCallback();
      }, 0);
  },</pre>

<p>La première chose que le rappel fait est de vérifier si la vidéo est en train de jouer. Si ce n'est pas le cas, le rappel revient immédiatement sans rien faire.</p>

<p>Ensuite, il appelle la méthode <code>computeFrame()</code>, qui effectue l'effet  "chroma-keying"  sur l'image vidéo en cours.</p>

<p>La dernière chose que fait le rappel est d'appeler <code>setTimeout()</code> pour programmer un nouvel appel. En réalité, vous planifierez probablement cela en fonction de la connaissance de la fréquence d'images de la vidéo.</p>

<h3 id="Manipulation_des_données_des_images_vidéo">Manipulation des données des images vidéo</h3>

<p>La méthode <code>computeFrame()</code> , présentée ci-dessous, est en charge de récupérer les données de chaque image et d'y appliquer l'effet d'incrustation.</p>

<pre class="brush: js">processor.computeFrame = function computeFrame() {
    this.ctx1.drawImage(this.video, 0, 0, this.width, this.height);
    let frame = this.ctx1.getImageData(0, 0, this.width, this.height);
    let l = frame.data.length / 4;

    for (let i = 0; i &lt; l; i++) {
      let r = frame.data[i * 4 + 0];
      let g = frame.data[i * 4 + 1];
      let b = frame.data[i * 4 + 2];
      if (g &gt; 100 &amp;&amp; r &gt; 100 &amp;&amp; b &lt; 43)
        frame.data[i * 4 + 3] = 0;
    }
    this.ctx2.putImageData(frame, 0, 0);
    return;
  }</pre>

<p>²</p>

<p>Quand la routine est appelée, l'élément vidéo affiche les données de la plus récente image de la vidéo, ce qui ressemble à :</p>

<p><img src="video.png"></p>

<p>À la seconde ligne, cette image est copiée dans le contexte graphique <code>ctx1</code> du premier élément <code>canvas</code>, en spécifiant ses hauteur et largeur, définies plus tôt (soit, réduites de moitié). Notez que c'est très simplement que vous passez les données de l'élément vidéo à afficher dans le contexte graphique avec la méthode <code>drawImage()</code>. Voici ce que cela donne :</p>

<p><img src="sourcectx.png"></p>

<p>La ligne 3 extrait une copie des données graphiques brutes pour l'image courante de la vidéo en appelant la méthode <code>getImageData() </code>sur le premier contexte. Cela fournit des données brutes d'image pixel 32 bits que nous pouvons ensuite manipuler. La ligne 4 calcule le nombre de pixels de l'image en divisant la taille totale des données d'image du cadre par quatre.</p>

<p>La boucle <code>for</code>, qui commence à la ligne 6, parcourt les pixels du cadre  en extrayant les valeurs rouges, vertes et bleues de chaque pixel et compare les valeurs aux nombres prédéterminés utilisés pour détecter l'écran vert qui sera remplacé par l'image de fond importée de <code>foo.png</code>.</p>

<p>Chaque pixel dans les données d'image, qui se trouve dans les paramètres considérés comme faisant partie de l'écran vert, a sa valeur alpha remplacée par un zéro, indiquant que le pixel est entièrement transparent. En conséquence, l'image finale a toute la zone d'écran vert 100% transparente, de sorte que lorsqu'elle est dessinée dans le contexte de destination à la ligne 13, le résultat est une superposition sur la toile de fond statique.</p>

<p>L'image résultante ressemble à ceci :</p>

<p><img src="output.png"></p>

<p>Cela se fait de façon répétée au fur et à mesure que la vidéo est lue, de sorte que, image après image, la vidéo est traitée et affichée avec l'effet de chrominance.</p>

<p><a href="/samples/video/chroma-key/index.xhtml">Voyez cet exemple réel</a>.</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content">Using audio and video</a></li>
</ul>
