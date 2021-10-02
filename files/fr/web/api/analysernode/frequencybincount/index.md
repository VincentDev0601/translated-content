---
title: AnalyserNode.frequencyBinCount
slug: Web/API/AnalyserNode/frequencyBinCount
translation_of: Web/API/AnalyserNode/frequencyBinCount
---
<p>{{ APIRef("Web Audio API") }}<br>
 <br>
 La propriété <strong><code>frequencyBinCount</code></strong> de l'objet <a href="/fr/docs/Web/API/AnalyserNode"><code>AnalyserNode</code></a> est un nombre entier non signé équivalent à la moitié la taille de la FFT. Il correspond en général au nombre de valeurs que vous aurez à manipuler pour la visualisation.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var contexteAudio = new AudioContext();
var analyseur = contexteAudio.createAnalyser();
var tailleMemoireTampon = analyseur.frequencyBinCount;
</pre>

<h3 id="Valeur">Valeur</h3>

<p>Un nombre entier non signé.</p>

<h2 id="Example">Example</h2>

<p>L'exemple suivant montre comment créer simplement un  <code>AnalyserNode</code> avec <a href="/fr/docs/Web/API/AudioContext"><code>AudioContext</code></a>, puis utiliser  <a href="/fr/docs/Web/API/Window/requestAnimationFrame"><code>requestAnimationFrame</code></a> et <a href="/fr/docs/Web/HTML/Element/canvas"><code>&lt;canvas&gt;</code></a> pour collecter les données temporelles et dessiner un oscilloscopeen sortie. Pour des exemples plus complets, voir notre démo <a href="http://mdn.github.io/voice-change-o-matic/">Voice-change-O-matic</a>  (et en particulier <a href="https://github.com/mdn/voice-change-o-matic/blob/gh-pages/scripts/app.js#L128-L205">app.js lines 128–205</a>).</p>

<pre class="brush: js">var contexteAudio = new (window.AudioContext || window.webkitAudioContext)();
var analyseur = contexteAudio.createAnalyser();
analyseur.minDecibels = -90;
analyseur.maxDecibels = -10;

  ...

analyseur.fftSize = 256;
var tailleMemoireTampon = analyseur.frequencyBinCount;
console.log(tailleMemoireTampon);
var tableauDonnees = new Uint8Array(tailleMemoireTampon);

contexteCanvas.clearRect(0, 0, LARGEUR, HAUTEUR);

function dessiner() {
  dessin = requestAnimationFrame(dessiner);

  analyseur.getByteFrequencyData(tableauDonnees);

  contexteCanvas.fillStyle = 'rgb(0, 0, 0)';
  contexteCanvas.fillRect(0, 0, LARGEUR, HAUTEUR);

  var largeurBarre = (LARGEUR / tailleMemoireTampon) * 2.5 - 1;
  var hauteurBarre;
  var x = 0;

  for(var i = 0; i &lt; tailleMemoireTampon; i++) {
    hauteurBarre = tableauDonnees[i];

    contexteCanvas.fillStyle = 'rgb(' + (hauteurBarre+100) + ',50,50)';
    contexteCanvas.fillRect(x,HAUTEUR-hauteurBarre/2,largeurBarre,hauteurBarre/2);

    x += largeurBarre;
  }
};

dessiner();</pre>

<h2 id="Spécification">Spécification</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('Web Audio API', '#widl-AnalyserNode-frequencyBinCount', 'frequencyBinCount')}}</td>
   <td>{{Spec2('Web Audio API')}}</td>
   <td> </td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_navigateurs">Compatibilité navigateurs</h2>

<p>{{Compat("api.AnalyserNode.frequencyBinCount")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web_Audio_API/Using_Web_Audio_API">Utiliser la Web Audio API</a></li>
</ul>
