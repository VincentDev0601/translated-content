---
title: Dessin de texte avec canvas
slug: Web/API/Canvas_API/Tutorial/Drawing_text
tags:
  - Canvas
  - Graphismes
  - HTML
  - Tutoriels
translation_of: Web/API/Canvas_API/Tutorial/Drawing_text
original_slug: Web/API/Canvas_API/Tutoriel_canvas/Dessin_de_texte_avec_canvas
---
<p>{{CanvasSidebar}} {{PreviousNext("Tutoriel_canvas/Ajout_de_styles_et_de_couleurs", "Tutoriel_canvas/Utilisation_d'images")}}</p>

<p>Après avoir vu comment <a href="/fr/docs/Tutoriel_canvas/Ajout_de_styles_et_de_couleurs">appliquer les styles et les couleurs</a> dans le chapitre précédent, nous allons maintenant voir comment dessiner du texte sur canvas.</p>

<h2 id="Dessin_de_texte">Dessin de texte</h2>

<p>  Le contexte de rendu du canevas fournit deux méthodes pour le rendu du texte :</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.fillText", "fillText(text, x, y [, maxWidth])")}}</dt>
 <dd>Remplit un texte donné à la position (x, y). Facultatif, avec une largeur maximale à dessiner.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.strokeText", "strokeText(text, x, y [, maxWidth])")}}</dt>
 <dd>Trait d'un texte donné à la position (x, y). Facultatif, avec une largeur maximale à dessiner.</dd>
</dl>

<h3 id="A_fillText_example">Un exemple fillText</h3>

<p>Le texte est rempli en utilisant le <code>fillStyle</code> actuel.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  ctx.font = '48px serif';
  ctx.fillText('Hello world', 10, 50);
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="300" height="100"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>{{EmbedLiveSample("A_fillText_example", 310, 110)}}</p>

<h3 id="A_strokeText_example">Un exemple de strokeText</h3>

<p>Le texte est rempli en utilisant le  <code>strokeStyle</code> courant.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  ctx.font = '48px serif';
  ctx.strokeText('Hello world', 10, 50);
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="300" height="100"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>{{EmbedLiveSample("A_strokeText_example", 310, 110)}}</p>

<h2 id="M.C3.A9thodes">Style de texte</h2>

<p>Dans les exemples ci-dessus, nous utilisons déjà la propriété de police pour rendre le texte un peu plus grand que la taille par défaut. Il existe d'autres propriétés qui vous permettent d'ajuster la façon dont le texte est affiché sur le canevas :</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.font", "font = value")}}</dt>
 <dd>Le style de texte actuel utilisé lors du dessin du texte. Cette chaîne utilise la même syntaxe que la propriété CSS {{cssxref ("font")}}. La police par défaut est 10px sans-serif.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.textAlign", "textAlign = value")}}</dt>
 <dd>Paramètre d'alignement du texte. Valeurs possibles :  <code>start</code> <em>(</em><em>début)</em>,  <code>end</code> <em>(</em><em>fin)</em>,  <code>left</code> <em>(</em><em>gauche)</em>,  <code>right</code> <em>(</em><em>droite)</em> ou  <code>center</code> <em>(</em><em>centre)</em>. La valeur par défaut est <code>start</code>.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.textBaseline", "textBaseline = value")}}</dt>
 <dd>Paramètre d'alignement de base. Valeurs possibles :  <code>top</code> <em>(</em><em>haut)</em>,  <code>hanging</code> <em>(</em><em>suspendu)</em>,  <code>middle</code> <em>(</em><em>moyen)</em>,  <code>alphabetic</code> <em>(</em><em>alphabétique)</em>,  <code>ideographic</code> <em>(</em><em>idéographique)</em>,  <code>bottom</code> <em>(</em><em>en bas)</em>. La valeur par défaut est <code>alphabetic</code>.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.direction", "direction = value")}}</dt>
 <dd>Directionnalité. Valeurs possibles:  <code>ltr</code> <em>(de gauche à droite)</em>,  <code>rtl</code> <em>(de droite à gauche)</em>, <code>inherit</code> <em>(hérité)</em>. La valeur par défaut est <code>inherit</code>.</dd>
</dl>

<p>Ces propriétés peuvent vous être familières si vous avez déjà travaillé avec CSS.</p>

<p>Le diagramme suivant du  <a href="http://www.whatwg.org/">WHATWG</a>  illustre les différentes lignes de base prises en charge par la propriété <code>textBaseline.</code></p>

<p><img alt="The top of the em square is
roughly at the top of the glyphs in a font, the hanging baseline is
where some glyphs like आ are anchored, the middle is half-way
between the top of the em square and the bottom of the em square,
the alphabetic baseline is where characters like Á, ÿ,
f, and Ω are anchored, the ideographic baseline is
where glyphs like 私 and 達 are anchored, and the bottom
of the em square is roughly at the bottom of the glyphs in a
font. The top and bottom of the bounding box can be far from these
baselines, due to glyphs extending far outside the em square." src="http://www.whatwg.org/specs/web-apps/current-work/images/baselines.png"></p>

<h3 id="Un_exemple_de_textBaseline">Un exemple de textBaseline</h3>

<p>Modifiez le code ci-dessous et visualisez vos mises à jour en direct dans le canevas :</p>

<pre class="brush: js">ctx.font = '48px serif';
ctx.textBaseline = 'hanging';
ctx.strokeText('Hello world', 0, 100);</pre>

<h4 id="Playable_code">Playable code</h4>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="400" height="200" class="playable-canvas"&gt;&lt;/canvas&gt;
&lt;div class="playable-buttons"&gt;
  &lt;input id="edit" type="button" value="Edit" /&gt;
  &lt;input id="reset" type="button" value="Reset" /&gt;
&lt;/div&gt;
&lt;textarea id="code" class="playable-code"&gt;
ctx.font = "48px serif";
ctx.textBaseline = "hanging";
ctx.strokeText("Hello world", 0, 100);&lt;/textarea&gt;</pre>

<pre class="brush: js hidden">var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');
var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var edit = document.getElementById('edit');
var code = textarea.value;

function drawCanvas() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  eval(textarea.value);
}

reset.addEventListener('click', function() {
  textarea.value = code;
  drawCanvas();
});

edit.addEventListener('click', function() {
  textarea.focus();
})

textarea.addEventListener('input', drawCanvas);
window.addEventListener('load', drawCanvas);</pre>

<p>{{ EmbedLiveSample('Playable_code', 700, 360) }}</p>

<h2 id="Mesures_de_texte_avancées">Mesures de texte avancées</h2>

<p>Dans le cas où vous avez besoin d'obtenir plus de détails sur le texte, la méthode suivante vous permet de le mesurer.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.measureText", "measureText()")}}</dt>
 <dd>Retourne un objet  {{domxref("TextMetrics")}}  contenant la largeur en pixels, sur la base duquel le texte spécifié sera dessiné dans le style de texte actuel.</dd>
</dl>

<p>L'extrait de code suivant montre comment vous pouvez mesurer un texte et obtenir sa largeur.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  var text = ctx.measureText('foo'); // objet TextMetrics
  text.width; // 16;
}</pre>

<h2 id="Notes_spécifiques_à_Gecko">Notes spécifiques à Gecko</h2>

<p>Dans Gecko (le moteur de rendu de Firefox, Firefox OS et d'autres applications basées sur Mozilla), certaines API préfixées ont été implémentées dans des versions antérieures pour dessiner du texte sur un canevas. Ceux-ci sont maintenant déconseillés et supprimés, et leur fonctionnement n'est pas garanti.</p>

<p>{{PreviousNext("Tutoriel_canvas/Ajout_de_styles_et_de_couleurs", "Tutoriel_canvas/Utilisation_d'images")}}</p>
