---
title: transform
slug: Web/SVG/Attribute/transform
tags:
  - Attribut
  - SVG
translation_of: Web/SVG/Attribute/transform
---
<div>{{SVGRef}}</div>

<p>L'attribut <strong><code>transform</code></strong> définit une liste de définitions de transformation qui sont appliquées à l'élément ainsi qu'à ses éléments fils.</p>

<h2>Exemple</h2>

<pre class="brush: css hidden">html,body,svg { height:100% }</pre>

<pre class="brush: html">&lt;svg viewBox="-40 0 150 100" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"&gt;
  &lt;g fill="grey"
     transform="rotate(-10 50 100)
                translate(-36 45.5)
                skewX(40)
                scale(1 0.5)"&gt;
    &lt;path id="heart" d="M 10,30 A 20,20 0,0,1 50,30 A 20,20 0,0,1 90,30 Q 90,60 50,90 Q 10,60 10,30 z" /&gt;
  &lt;/g&gt;

  &lt;use xlink:href="#heart" fill="none" stroke="red"/&gt;
&lt;/svg&gt;
</pre>

<p>{{EmbedLiveSample('exemple', '100%', 200)}}</p>

<div class="note">
  <p><strong>Note :</strong> Pour SVG2, <code>transform</code> est un attribut de présentation et peut donc être utilisé comme une propriété CSS. Attention toutefois aux différences de syntaxe entre la propriété CSS et cet attribut. Voir la documentation de la propriété {{cssxref('transform')}} pour la syntaxe .</p>
</div>

<p>En tant qu'attribut de présentation, <strong><code>transform</code></strong> peut être utilisé par n'importe quel élément (en SVG 1.1, seuls les 16 éléments suivants pouvaient l'utiliser : {{SVGElement('a')}}, {{SVGElement('circle')}}, {{SVGElement('clipPath')}}, {{SVGElement('defs')}}, {{SVGElement('ellipse')}}, {{SVGElement('foreignObject')}}, {{SVGElement('g')}}, {{SVGElement('image')}}, {{SVGElement('line')}}, {{SVGElement('path')}}, {{SVGElement('polygon')}}, {{SVGElement('polyline')}}, {{SVGElement('rect')}}, {{SVGElement('switch')}}, {{SVGElement('text')}} et {{SVGElement('use')}}).</p>

<p>Pour des raisons historiques liées à SVG 1.1, {{SVGElement('linearGradient')}} et {{SVGElement('radialGradient')}} prennent en charge l'attribut <code>gradientTransform</code> et {{SVGElement('pattern')}} permet d'utiliser <code>patternTransform</code>. Ces deux attributs sont exactement synonymes de l'attribut <code>transform</code>.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Valeur</th>
   <td><code><strong><a href="/fr/docs/Web/SVG/Content_type#Transform-list">&lt;transform-list&gt;</a></strong></code></td>
  </tr>
  <tr>
   <th scope="row">Valeur par défaut</th>
   <td><code>none</code></td>
  </tr>
  <tr>
   <th scope="row">Peut être animé</th>
   <td>Oui</td>
  </tr>
 </tbody>
</table>

<h2 id="Fonctions_de_transformation">Fonctions de transformation</h2>

<p>Les fonctions de transformation suivantes peuvent être utilisées par l'attribut <code>transform</code>.</p>

<div class="warning">
  <p><strong>Attention :</strong> Selon la spécification, on devrait également pouvoit utiliser les fonctions CSS {{cssxref('transform-function', 'transform functions')}} mais la compatibilité n'est pas assurée.</p>
</div>

<h3 id="matrix"><code>matrix()</code></h3>

<p>La fonction de transformation <code>matrix(&lt;a&gt; &lt;b&gt; &lt;c&gt; &lt;d&gt; &lt;e&gt; &lt;f&gt;)</code> permet d'appliquer une transformation géométrique décrite par 6 coefficients et <code>matrix(a,b,c,d,e,f)</code> sera équivalent à la matrice de transformation mathématique :<math display="block"><semantics><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><annotation encoding="TeX">\begin{pmatrix} a &amp; c &amp; e \\ b &amp; d &amp; f \\ 0 &amp; 0 &amp; 1 \end{pmatrix}</annotation></semantics></math>Le calcul des coordonnées s'obtient de la façon suivante :<math display="block"><semantics><mrow><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>n</mi><mi>e</mi><mi>w</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>n</mi><mi>e</mi><mi>w</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><mo>=</mo><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>p</mi><mi>r</mi><mi>e</mi><mi>v</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>p</mi><mi>r</mi><mi>e</mi><mi>v</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><mo>=</mo><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><mi>a</mi><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>p</mi><mi>r</mi><mi>e</mi><mi>v</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub><mo>+</mo><mi>c</mi><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>p</mi><mi>r</mi><mi>e</mi><mi>v</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub><mo>+</mo><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>p</mi><mi>r</mi><mi>e</mi><mi>v</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub><mo>+</mo><mi>d</mi><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>p</mi><mi>r</mi><mi>e</mi><mi>v</mi><mi>C</mi><mi>o</mi><mi>o</mi><mi>r</mi><mi>d</mi><mi>S</mi><mi>y</mi><mi>s</mi></mrow></mstyle></msub><mo>+</mo><mi>f</mi></mtd></mtr><mtr><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow></mrow><annotation encoding="TeX"> \begin{pmatrix} x_{\mathrm{newCoordSys}} \\ y_{\mathrm{newCoordSys}} \\ 1 \end{pmatrix} = \begin{pmatrix} a &amp; c &amp; e \\ b &amp; d &amp; f \\ 0 &amp; 0 &amp; 1 \end{pmatrix} \begin{pmatrix} x_{\mathrm{prevCoordSys}} \\ y_{\mathrm{prevCoordSys}} \\ 1 \end{pmatrix} = \begin{pmatrix} a x_{\mathrm{prevCoordSys}} + c y_{\mathrm{prevCoordSys}} + e \\ b x_{\mathrm{prevCoordSys}} + d y_{\mathrm{prevCoordSys}} + f \\ 1 \end{pmatrix} </annotation></semantics></math></p>

<h4 id="Exemples">Exemples</h4>

<pre class="brush: css hidden">html,body,svg { height:100% }
</pre>

<pre class="brush: html">&lt;svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;rect x="10" y="10" width="30" height="20" fill="green" /&gt;

  &lt;!--
  Dans l'exemple suivant, on applique la matrice suivante:
  [a c e]    [3 -1 30]
  [b d f] =&gt; [1  3 40]
  [0 0 1]    [0  0  1]

  qui transforme le rectangle de cette façon:

  top left corner: oldX=10 oldY=10
  newX = a * oldX + c * oldY + e = 3 * 10 - 1 * 10 + 30 = 50
  newY = b * oldX + d * oldY + f = 1 * 10 + 3 * 10 + 40 = 80

  top right corner: oldX=40 oldY=10
  newX = a * oldX + c * oldY + e = 3 * 40 - 1 * 10 + 30 = 140
  newY = b * oldX + d * oldY + f = 1 * 40 + 3 * 10 + 40 = 110

  bottom left corner: oldX=10 oldY=30
  newX = a * oldX + c * oldY + e = 3 * 10 - 1 * 30 + 30 = 30
  newY = b * oldX + d * oldY + f = 1 * 10 + 3 * 30 + 40 = 140

  bottom right corner: oldX=40 oldY=30
  newX = a * oldX + c * oldY + e = 3 * 40 - 1 * 30 + 30 = 120
  newY = b * oldX + d * oldY + f = 1 * 40 + 3 * 30 + 40 = 170
  --&gt;
  &lt;rect x="10" y="10" width="30" height="20" fill="red"
        transform="matrix(3 1 -1 3 30 40)" /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('matrix()', '100%', 200)}}</p>

<h3 id="translate"><code>translate()</code></h3>

<p>La fonction de transformation <code>translate(&lt;x&gt; [&lt;y&gt;])</code> permet de déplacer un objet de <code>x</code> sur l'axe horizontal et de <code>y</code> sur l'axe vertical (i.e. <code>x<sub>new</sub> = x<sub>old</sub> + &lt;x&gt;, y<sub>new</sub> = y<sub>old</sub> + &lt;y&gt;</code>). Si <code>y</code> n'est pas fourni, la valeur par défaut est 0.</p>

<h4 id="Exemples_2">Exemples</h4>

<pre class="brush: css hidden">html,body,svg { height:100% }
</pre>

<pre class="brush: html">&lt;svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;!-- Pas de translation --&gt;
  &lt;rect x="5" y="5" width="40" height="40" fill="green" /&gt;

  &lt;!-- Translation horizontale --&gt;
  &lt;rect x="5" y="5" width="40" height="40" fill="blue"
        transform="translate(50)" /&gt;

  &lt;!-- Translation verticale --&gt;
  &lt;rect x="5" y="5" width="40" height="40" fill="red"
        transform="translate(0 50)" /&gt;

  &lt;!-- Translation horizontale et verticale --&gt;
  &lt;rect x="5" y="5" width="40" height="40" fill="yellow"
         transform="translate(50,50)" /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('translate()', '100%', 200)}}</p>

<h3 id="scale"><code>scale()</code></h3>

<p>La fonction de transformation <code>scale(&lt;x&gt; [&lt;y&gt;])</code> définit une homothétie d'un facteur <code>x</code> en horizontal et d'un facteur <code>y</code> en vertical. Si la valeur <code>y</code> n'est pas fournie, on considère qu'elle est égale à <code>x</code>.</p>

<h4 id="Exemples_3">Exemples</h4>

<pre class="brush: css hidden">html,body,svg { height:100% }
</pre>

<pre class="brush: html">&lt;svg viewBox="-50 -50 100 100" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;!-- uniform scale --&gt;
  &lt;circle cx="0" cy="0" r="10" fill="red"
          transform="scale(4)" /&gt;

  &lt;!-- vertical scale --&gt;
  &lt;circle cx="0" cy="0" r="10" fill="yellow"
          transform="scale(1,4)" /&gt;

  &lt;!-- horizontal scale --&gt;
  &lt;circle cx="0" cy="0" r="10" fill="pink"
          transform="scale(4,1)" /&gt;

  &lt;!-- No scale --&gt;
  &lt;circle cx="0" cy="0" r="10" fill="black" /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('scale()', '100%', 200)}}</p>

<h3 id="rotate"><code>rotate()</code></h3>

<p>La fonction de transformation <code>rotate(&lt;a&gt; [&lt;x&gt; &lt;y&gt;])</code> définit une rotation de <code>a</code> degrés autour d'un point de coordonnées <code>x</code> et <code>y</code>. Si les paramètres optionnels <code>x</code> et <code>y</code> ne sont pas fournis, la rotation est effectuée autour de l'origine dans le système de coordonnés actuel.</p>

<h4 id="Exemples_4">Exemples</h4>

<pre class="brush: css hidden">html,body,svg { height:100% }
</pre>

<pre class="brush: html">&lt;svg viewBox="-12 -2 34 14" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;rect x="0" y="0" width="10" height="10" /&gt;

  &lt;!-- rotation is done around the point 0,0 --&gt;
  &lt;rect x="0" y="0" width="10" height="10" fill="red"
        transform="rotate(100)" /&gt;

  &lt;!-- rotation is done around the point 10,10 --&gt;
  &lt;rect x="0" y="0" width="10" height="10" fill="green"
        transform="rotate(100,10,10)" /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('rotate()', '100%', 200)}}</p>

<h3 id="skewX"><code>skewX()</code></h3>

<p>La fonction de transformation <code>skewX(&lt;a&gt;)</code> définit une distorsion horizontale de <code>a</code> degrés.</p>

<h4 id="Exemples_5">Exemples</h4>

<pre class="brush: css hidden">html,body,svg { height:100% }
</pre>

<pre class="brush: html">&lt;svg viewBox="-5 -5 10 10" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;rect x="-3" y="-3" width="6" height="6" /&gt;

  &lt;rect x="-3" y="-3" width="6" height="6" fill="red"
        transform="skewX(30)" /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('skewX()', '100%', 200)}}</p>

<h3 id="skewY"><code>skewY()</code></h3>

<p>La fonction de transformation <code>skewY(&lt;a&gt;)</code> définit une distorsion verticale de <code>a</code> degrés.</p>

<h4 id="Exemples_6">Exemples</h4>

<pre class="brush: css hidden">html,body,svg { height:100% }
</pre>

<pre class="brush: html">&lt;svg viewBox="-5 -5 10 10" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;rect x="-3" y="-3" width="6" height="6" /&gt;

  &lt;rect x="-3" y="-3" width="6" height="6" fill="red"
        transform="skewY(30)" /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('skewY()', '100%', 200)}}</p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">État</th>
   <th scope="col">Commentaires</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('CSS Transforms 2', '#svg-transform', 'transform')}}</td>
   <td>{{Spec2('CSS Transforms 2')}}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName('CSS3 Transforms', '#svg-transform', 'transform')}}</td>
   <td>{{Spec2('CSS3 Transforms')}}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName("SVG2", "coords.html#TransformProperty", "transform")}}</td>
   <td>{{Spec2("SVG2")}}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName("SVG1.1", "coords.html#TransformAttribute", "transform")}}</td>
   <td>{{Spec2("SVG1.1")}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>
