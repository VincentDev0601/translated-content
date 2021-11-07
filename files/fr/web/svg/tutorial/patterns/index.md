---
title: Motifs
slug: Web/SVG/Tutorial/Patterns
tags:
  - SVG
  - SVG:Tutoriel
translation_of: Web/SVG/Tutorial/Patterns
original_slug: Web/SVG/Tutoriel/Motifs
---
<p>{{ PreviousNext("Web/SVG/Tutoriel/Gradients", "Web/SVG/Tutoriel/Texts") }}</p>

<p>Les motifs (<em>patterns</em> en anglais) sont sans aucun doute les types de remplissages les plus complexes à utiliser en SVG. Ce sont également des outils très puissants, ils méritent donc d'être abordés pour que vous en connaissiez les fondamentaux. Comme les dégradés, l'élément {{SVGElement('pattern')}} doit être placé dans la section <code>&lt;defs&gt;</code> du fichier SVG.</p>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: html">&lt;svg width="200" height="200" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;defs&gt;
    &lt;linearGradient id="Gradient1"&gt;
      &lt;stop offset="5%" stop-color="white"/&gt;
      &lt;stop offset="95%" stop-color="blue"/&gt;
    &lt;/linearGradient&gt;
    &lt;linearGradient id="Gradient2" x1="0" x2="0" y1="0" y2="1"&gt;
      &lt;stop offset="5%" stop-color="red"/&gt;
      &lt;stop offset="95%" stop-color="orange"/&gt;
    &lt;/linearGradient&gt;

    &lt;pattern id="Pattern" x="0" y="0" width=".25" height=".25"&gt;
      &lt;rect x="0" y="0" width="50" height="50" fill="skyblue"/&gt;
      &lt;rect x="0" y="0" width="25" height="25" fill="url(#Gradient2)"/&gt;
      &lt;circle cx="25" cy="25" r="20" fill="url(#Gradient1)" fill-opacity="0.5"/&gt;
    &lt;/pattern&gt;
  &lt;/defs&gt;

  &lt;rect fill="url(#Pattern)" stroke="black" width="200" height="200"/&gt;
&lt;/svg&gt;</pre>

<p>{{ EmbedLiveSample('Exemple','220','220','/files/725/SVG_Pattern_Example.png') }}</p>

<p>À l'intérieur de l'élément <code>pattern</code>, vous pouvez inclure toutes les formes de bases de SVG et les styliser de la même manière que d'habitude (remplissage, contour, dégradés, opacité, etc). Dans notre exemple, on a dessiné un cercle et deux rectangles (qui se chevauchent et dont l'un est deux fois plus grand que l'autre pour remplir le motif en entier).</p>

<p>La partie pouvant apporter le plus de confusion avec les motifs est le système d'unité et la taille des éléments.</p>

<h2 id="Unités_du_motif_objectBoundingBox">Unités du motif: objectBoundingBox</h2>

<p>Les attributs <code>width</code> et <code>height</code> sur l'élément <code>pattern</code> décrivent jusqu'où le motif doit aller avant de se répéter. Les attributs <code>x</code> et <code>y</code> sont également disponibles si vous souhaitez décaler le point de départ du motif à l'intérieur du dessin.</p>

<p>Même principe que l'attribut <code>gradientUnits</code> (que nous avons vu précédemment avec les dégradés), les motifs peuvent prendre un attribut <code>patternUnits</code>, pour spécifier l'unité utilisée par le motif. La valeur par défaut est  "objectBoundingBox", ainsi une taille de 1 remplira entièrement la hauteur/largeur de l'objet auquel le motif est appliqué. Puisque dans notre cas, on veut que le motif se répète 4 fois horizontalement et verticalement, on a définit <code>height</code> et <code>width</code> à 0.25. Cela signifie que la hauteur et largeur du pattern sera de 25% celle de l'objet.</p>

<p>De même, pour que le motif commence à 10 pixels du bord supérieur-gauche de l'objet, il faudrait définir les valeurs de <code>x</code> et <code>y</code> à 0.05 (10/200 = 0.05).</p>

<h2 id="Unités_du_contenu_userSpaceOnUse">Unités du contenu: userSpaceOnUse</h2>

<p>Contrairement aux dégradés, les motifs ont un deuxième argument, <code>patternContentUnits</code>, qui lui spécifie l'unité utilisée par les formes à l'intérieur du motif. La valeur par défaut est "userSpaceOnUse", l'opposé de l'attribut <code>patternUnits</code>. Cela signifie qu'à moins de définir ces attributs aurement (<code>patternContentUnits</code> et/ou <code>patternUnits</code>), les formes que vous dessinez à l'intérieur du motif ont un système de coordonnées différent du motif, ce qui peut rendre les choses un peu déroutantes si vous écrivez le code à la main.</p>

<p>Pour que cela fonctionne dans l'exemple ci-dessus, nous avons dû prendre en compte la taille du rectangle sur lequel est appliqué le motif (200px) et le fait que l'on veut répéter le motif 4 fois horizontalement et verticalement, donc que le motif sera un carré de 50x50. Les deux rectangles et le cercle à l'intérieur du motif ont été dimensionnés pour tenir dans un carré de 50x50. Tout ce qui sortirait en dehors ne serait pas affiché.</p>

<p>La chose à retenir est que si l'objet change de taille, le motif lui-même sera mis à l'échelle mais les objets à l'intérieur non. Ainsi, alors qu'on aura toujours 4 motifs qui se répètent horizontalement et verticalement, les objets à l'intérieur du motif garderont la même taille, et une zone vide sera affichée.</p>


<h3>Exemple</h6>

<pre class="brush: html hidden">&lt;svg width="600" height="200" xmlns="http://www.w3.org/2000/svg" id="svg" class="playable-svg"&gt;
  &lt;defs&gt;
    &lt;linearGradient id="Gradient1"&gt;
      &lt;stop offset="5%" stop-color="white"/&gt;
      &lt;stop offset="95%" stop-color="blue"/&gt;
    &lt;/linearGradient&gt;
    &lt;linearGradient id="Gradient2" x1="0" x2="0" y1="0" y2="1"&gt;
      &lt;stop offset="5%" stop-color="red"/&gt;
      &lt;stop offset="95%" stop-color="orange"/&gt;
    &lt;/linearGradient&gt;

    &lt;pattern id="Pattern" x="0" y="0" width=".25" height=".25"&gt;
      &lt;rect x="0" y="0" width="50" height="50" fill="skyblue"/&gt;
      &lt;rect x="0" y="0" width="25" height="25" fill="url(#Gradient2)"/&gt;
      &lt;circle cx="25" cy="25" r="20" fill="url(#Gradient1)" fill-opacity="0.5"/&gt;
    &lt;/pattern&gt;
  &lt;/defs&gt;

  &lt;rect fill="url(#Pattern)" stroke="black" width="200" height="200"/&gt;
&lt;/svg&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="edit" type="button" value="Edit" /&gt;
  &lt;input id="reset" type="button" value="Reset" /&gt;
&lt;/div&gt;
&lt;textarea id="code" class="playable-code"&gt;
rect.setAttribute('width', 300);&lt;/textarea&gt;
</pre>

<pre class="brush: js hidden">var svg      = document.getElementById('svg'),
    rect     = svg.lastElementChild;

var textarea = document.getElementById('code'),
    reset    = document.getElementById('reset'),
    edit     = document.getElementById('edit'),
    code     = textarea.value;

function drawSvg() {
  eval(textarea.value);
}
reset.addEventListener('click', function() {
  textarea.value = code;
  drawSvg();
});
edit.addEventListener('click', function() {
  textarea.focus();
})

textarea.addEventListener('input', drawSvg);
window.addEventListener('load', drawSvg);
</pre>

<p>{{ EmbedLiveSample('exemple_jouable','220','350') }}</p>

<h2 id="Unités_du_contenu_objectBoundingBox">Unités du contenu: objectBoundingBox</h2>

<p>En changeant l'attribut <code>patternContentUnits</code>, on peut utiliser le même système d'unité pour tous les éléments:</p>

<pre class="brush: xml"> &lt;pattern id="Pattern" width=".25" height=".25" patternContentUnits="objectBoundingBox"&gt;
   &lt;rect x="0" y="0" width=".25" height=".25" fill="skyblue"/&gt;
   &lt;rect x="0" y="0" width=".125" height=".125" fill="url(#Gradient2)"/&gt;
   &lt;circle cx=".125" cy=".125" r=".1" fill="url(#Gradient1)" fill-opacity="0.5"/&gt;
 &lt;/pattern&gt;
</pre>

<p>Maintenant, parce le contenu du motif utilise le même système d'unité que le motif, le motif redimensionne automatiquement son contenu. Cela contraste avec le système "userSpaceOnUse" par défaut, où lorsque le motif change le taille, le contenu garde la même taille.</p>

<h3 id="code_jouable_2">Code jouable 2</h3>

<pre class="brush: html hidden">&lt;svg width="600" height="200" xmlns="http://www.w3.org/2000/svg" id="svg" class="playable-svg"&gt;
  &lt;defs&gt;
    &lt;linearGradient id="Gradient1"&gt;
      &lt;stop offset="5%" stop-color="white"/&gt;
      &lt;stop offset="95%" stop-color="blue"/&gt;
    &lt;/linearGradient&gt;
    &lt;linearGradient id="Gradient2" x1="0" x2="0" y1="0" y2="1"&gt;
      &lt;stop offset="5%" stop-color="red"/&gt;
      &lt;stop offset="95%" stop-color="orange"/&gt;
    &lt;/linearGradient&gt;

    &lt;pattern id="Pattern" width=".25" height=".25" patternContentUnits="objectBoundingBox"&gt;
      &lt;rect x="0" y="0" width=".25" height=".25" fill="skyblue"/&gt;
      &lt;rect x="0" y="0" width=".125" height=".125" fill="url(#Gradient2)"/&gt;
      &lt;circle cx=".125" cy=".125" r=".1" fill="url(#Gradient1)" fill-opacity="0.5"/&gt;
    &lt;/pattern&gt;
  &lt;/defs&gt;

  &lt;rect fill="url(#Pattern)" stroke="black" width="200" height="200"/&gt;
&lt;/svg&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="edit" type="button" value="Edit" /&gt;
  &lt;input id="reset" type="button" value="Reset" /&gt;
&lt;/div&gt;
&lt;textarea id="code" class="playable-code"&gt;
rect.setAttribute('width', 300);&lt;/textarea&gt;
</pre>

<pre class="brush: js hidden">var svg      = document.getElementById('svg'),
    rect     = svg.lastElementChild;

var textarea = document.getElementById('code'),
    reset    = document.getElementById('reset'),
    edit     = document.getElementById('edit'),
    code     = textarea.value;

function drawSvg() {
  eval(textarea.value);
}
reset.addEventListener('click', function() {
  textarea.value = code;
  drawSvg();
});
edit.addEventListener('click', function() {
  textarea.focus();
})

textarea.addEventListener('input', drawSvg);
window.addEventListener('load', drawSvg);
</pre>

<p>{{ EmbedLiveSample('code_jouable_2','220','350') }}</p>

<div class="note">
  <p><strong>Note :</strong> Dans Gecko, les cercles semblent avoir du mal à être dessinés si le rayon est inférieur à 0.075 (on ignore s'il s'agit d'un bug de l'élément pattern ou non). Pour contourner ce problème, il est probablement préférable d'éviter de dessiner des cercles dans des unités "objectBoundingBox".</p>
</div>

<h2 id="Unités_du_motif_userSpaceOnUse">Unités du motif: userSpaceOnUse</h2>

<p>Aucune des utilisations vu jusqu'ici ne correspond à l'usage habituel des motifs (tel qu'on le ferait en CSS): les motifs ont généralement une taille définie et se répètent indépendamment de la taille de l'objet sur lequel il est appliqué. Pour créer quelque chose comme ça, le motif et le contenu doivent être dessiné en mode "userSpaceOnUse":</p>

<pre class="brush: xml"> &lt;pattern id="Pattern" x="10" y="10" width="50" height="50" patternUnits="userSpaceOnUse"&gt;
   &lt;rect x="0" y="0" width="50" height="50" fill="skyblue"/&gt;
   &lt;rect x="0" y="0" width="25" height="25" fill="url(#Gradient2)"/&gt;
   &lt;circle cx="25" cy="25" r="20" fill="url(#Gradient1)" fill-opacity="0.5"/&gt;
 &lt;/pattern&gt;
</pre>

<p>Bien sûr, cela veut dire que le motif ne sera pas mis à l'échelle si vous modifiez la taille de l'objet ultérieurement.</p>

<h3>Exemple jouable</h3>

<pre class="brush: html hidden">&lt;svg width="600" height="200" xmlns="http://www.w3.org/2000/svg" id="svg" class="playable-svg"&gt;
  &lt;defs&gt;
    &lt;linearGradient id="Gradient1"&gt;
      &lt;stop offset="5%" stop-color="white"/&gt;
      &lt;stop offset="95%" stop-color="blue"/&gt;
    &lt;/linearGradient&gt;
    &lt;linearGradient id="Gradient2" x1="0" x2="0" y1="0" y2="1"&gt;
      &lt;stop offset="5%" stop-color="red"/&gt;
      &lt;stop offset="95%" stop-color="orange"/&gt;
    &lt;/linearGradient&gt;

    &lt;pattern id="Pattern" x="10" y="10" width="50" height="50" patternUnits="userSpaceOnUse"&gt;
      &lt;rect x="0" y="0" width="50" height="50" fill="skyblue"/&gt;
      &lt;rect x="0" y="0" width="25" height="25" fill="url(#Gradient2)"/&gt;
      &lt;circle cx="25" cy="25" r="20" fill="url(#Gradient1)" fill-opacity="0.5"/&gt;
    &lt;/pattern&gt;
  &lt;/defs&gt;

  &lt;rect fill="url(#Pattern)" stroke="black" width="200" height="200"/&gt;
&lt;/svg&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="edit" type="button" value="Edit" /&gt;
  &lt;input id="reset" type="button" value="Reset" /&gt;
&lt;/div&gt;
&lt;textarea id="code" class="playable-code"&gt;
rect.setAttribute('width', 300);&lt;/textarea&gt;
</pre>

<pre class="brush: js hidden">var svg      = document.getElementById('svg'),
    rect     = svg.lastElementChild;

var textarea = document.getElementById('code'),
    reset    = document.getElementById('reset'),
    edit     = document.getElementById('edit'),
    code     = textarea.value;

function drawSvg() {
  eval(textarea.value);
}
reset.addEventListener('click', function() {
  textarea.value = code;
  drawSvg();
});
edit.addEventListener('click', function() {
  textarea.focus();
})

textarea.addEventListener('input', drawSvg);
window.addEventListener('load', drawSvg);
</pre>

<p>{{ EmbedLiveSample('exemple_jouable_3','220','350') }}</p>

<h2 id="Récapitulatif">Récapitulatif</h2>

<p>Les trois exemples sont illustrés ci-dessous sur un rectangle allongé à une hauteur de 300px:</p>

<p><img src="svg_pattern_comparison_of_units.png"></p>

<p>{{ PreviousNext("Web/SVG/Tutoriel/Gradients", "Web/SVG/Tutoriel/Texts") }}</p>
