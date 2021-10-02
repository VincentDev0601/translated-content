---
title: Dessiner des formes avec le canevas
slug: Web/API/Canvas_API/Tutorial/Drawing_shapes
tags:
  - Canvas
  - Graphisme
  - Guide
  - HTML
  - HTML5
  - Intermédiaire
  - Tutoriel
translation_of: Web/API/Canvas_API/Tutorial/Drawing_shapes
original_slug: Web/API/Canvas_API/Tutoriel_canvas/Formes_géométriques
---
<p>{{CanvasSidebar}} {{PreviousNext("Tutoriel_canvas/Utilisation_de_base", "Tutoriel_canvas/Ajout_de_styles_et_de_couleurs")}}</p>

<p>Maintenant que nous avons défini notre <a href="/fr/docs/Tutoriel_canvas/Utilisation_de_base">environnement de canevas</a>, nous pouvons entrer dans les détails de la façon de dessiner sur le canevas. A la fin de cet article, vous aurez appris à tracer des rectangles, des triangles, des lignes, des arcs et des courbes, vous rendant ainsi familier avec certaines des formes de base. Le travail avec les trajets est essentiel lors du dessin d'objets sur le canevas, et nous verrons comment cela peut être fait.</p>

<h2 id="La_grille">La grille</h2>

<p>Avant de pouvoir commencer à dessiner, il nous faut parler de la grille ou <strong>système de coordonnées</strong>. Notre schéma HTML de la page précédente avait un élément canevas large de 150 pixels et haut de 150 pixels. À droite, vous voyez ce canevas avec la grille par défaut superposée. Normalement, 1 unité dans la grille correspond à 1 pixel sur le canevas. L'origine de cette grille est positionnée dans le coin <em>supérieur gauche</em> de coordonnées (0, 0). Tous les éléments sont placés relativement à cette origine. Ainsi, le coin supérieur gauche du carré bleu est à <code>x</code> pixels à partir de la gauche et à <code>y</code> pixels à partir du haut, aux coordonnées (x, y). Plus loin dans ce tutoriel, nous verrons comment déplacer l'origine à une position différente, faire pivoter la grille ou même la mettre à l'échelle ; mais pour l'instant, nous nous en tiendrons aux valeurs par défaut.</p>

<img alt="" src="canvas_default_grid.png">

<h2 id="Dessin_de_rectangles">Dessin de rectangles</h2>

<p>Au contraire de <a href="/fr/docs/Web/SVG">SVG</a>, le {{HTMLElement("canvas")}} ne supporte qu'une seule forme primitive : le rectangle. Toute autre forme doit être créée en combinant un ou plusieurs trajets, c'est-à-dire des listes de points reliés par des lignes. Heureusement, nous avons un assortiment de fonctions de dessin de trajets, qui rendent possible la composition de formes très complexes.</p>

<p>Commençons par le rectangle. Il y a trois fonctions qui dessinent des rectangles sur le canvas :</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.fillRect", "fillRect(x, y, largeur, hauteur)")}}</dt>
 <dd>Dessine un rectangle rempli.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.strokeRect", "strokeRect(x, y, largeur, hauteur)")}}</dt>
 <dd>Dessine un contour rectangulaire</dd>
 <dt>{{domxref("CanvasRenderingContext2D.clearRect", "clearRect(x, y, largeur, hauteur)")}}</dt>
 <dd>Efface la zone rectangulaire spécifiée, la rendant complètement transparente.</dd>
</dl>

<p>Chacune de ces trois fonctions a les mêmes paramètres. <code>x</code> et <code>y</code> indiquent la position sur le canevas (par rapport à l'origine) du coin supérieur gauche du rectangle sur le canvas. <code>largeur</code> et <code>hauteur</code> indiquent la taille du rectangle.</p>

<p>Ci-dessous la fonction <code>draw()</code> de la page précédente, mais utilisant maintenant ces trois fonctions.</p>

<h3 id="Exemple_de_forme_rectangulaire">Exemple de forme rectangulaire</h3>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="draw();"&gt;
   &lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');

    ctx.fillRect(25, 25, 100, 100);
    ctx.clearRect(45, 45, 60, 60);
    ctx.strokeRect(50, 50, 50, 50);
  }
}</pre>

<p>Le résultat de cet exemple est montré ci-dessous.</p>

<p>{{EmbedLiveSample("Exemple_de_forme_rectangulaire", 160, 160, "canvas_rect.png")}}</p>

<p>La fonction <code>fillRect()</code> dessine un grand carré noir de 100 pixels de côté. La fonction <code>clearRect()</code> efface ensuite un carré de 60x60 pixels, et finalement, la fonction <code>strokeRect()</code> est appelée pour créer un contour rectangulaire de 50x50 pixels dans l'espace effacé.</p>

<p>Dans les pages qui suivent, nous verrons deux méthodes alternatives pour <code>clearRect()</code>, et nous verrons aussi comment changer la couleur et le style de trait des formes rendues.</p>

<p>A la différence des fonctions de trajet que nous allons voir dans la prochaine section, les trois fonctions de rectangles dessinent immédiatement sur le canvas.</p>

<h2 id="Dessin_de_trajets">Dessin de trajets</h2>

<p>Les seules autres formes primitives sont les <em>trajets</em>. Un trajet est une liste de points, reliés par des segments de lignes qui peuvent être de différentes formes, incurvées ou non, de largeur différente et de couleur différente. Un trajet, ou même un sous-trajet, peut être fermé. La réalisation de formes utilisant des trajets requiert quelques étapes supplémentaires :</p>

<ol>
 <li>Tout d'abord, vous devez créer le trajet.</li>
 <li>Ensuite vous devez utiliser des <a href="/fr-FR/docs/Web/API/CanvasRenderingContext2D#Paths">instructions de dessin</a> pour dessiner sur le trajet.</li>
 <li>Finalement, vous devez fermer le trajet.</li>
 <li>Une fois que le trajet a été créé, vous devez le tracer ou le remplir pour le faire apparaître.</li>
</ol>

<p>Voici les functions utilisées pour réaliser ces étapes :</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.beginPath", "beginPath()")}}</dt>
 <dd>Crée un nouveau trajet. Une fois créé, les fonctions de dessin ultérieures seront dirigées vers le trajet et utilisées pour le construire.</dd>
 <dt><a href="/fr-FR/docs/Web/API/CanvasRenderingContext2D#Paths">Méthodes de trajet</a></dt>
 <dd>Méthodes pour définir différents trajets pour les objets.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.closePath", "closePath()")}}</dt>
 <dd>Ferme le trajet pour que les fonctions de dessin ultérieures soient à nouveau dirigées vers le contexte.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.stroke", "stroke()")}}</dt>
 <dd>Dessine la forme en traçant son contour.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.fill", "fill()")}}</dt>
 <dd>Dessine une forme pleine en remplissant la zone de contenu du trajet.</dd>
</dl>

<p>La première étape pour créer un trajet est d'appeler <code>beginPath()</code>. En interne, les trajets sont stockés comme une liste de sous-trajets (lignes, arcs, etc) qui ensemble réalisent une forme. Chaque fois que cette méthode est appelée, la liste est remise à zéro, et nous pouvons commencer à dessiner de nouvelles formes.</p>

<div class="note">
  <p><strong>Note :</strong> Lorsque le trajet en cours est vide, par exemple immédiatement après avoir appelé <code>beginPath()</code>, ou sur un canvas nouvellement créé, la première instruction de construction de trajet est toujours traitée comme un <code>moveTo()</code>, indépendamment de ce qu'elle est en réalité. Pour cette raison, il sera pratiquement toujours souhaitable d'indiquer la position de départ après la réinitialisation d'un trajet.</p>
</div>

<p>La deuxième étape est d'appeler les méthodes qui indiquent effectivement les sous-trajets à dessiner. Nous verrons ces méthodes bientôt.</p>

<p>La troisième méthode, optionnelle, est l'appel à <code>closePath()</code>. Cette méthode essaye de fermer la forme géométrique en dessinant une ligne droite depuis le point courant jusqu'au début du trajet. Si la forme a déjà été fermée ou s'il n'y a qu'un seul point dans la liste, cette fonction ne fait rien.</p>

<div class="note">
  <p><strong>Note :</strong> Quand vous appelez <code>fill()</code>, toutes les formes ouvertes sont automatiquement fermées, ainsi vous n'avez pas à appeler <code>closePath()</code>. Ce n'est <strong>pas</strong> le cas quand vous appelez <code>stroke()</code>.</p>
</div>

<h3 id="Dessin_dun_triangle">Dessin d'un triangle</h3>

<p>Par exemple, le code pour dessiner un triangle peut ressembler à ce qui suit :</p>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="dessiner();"&gt;
   &lt;canvas id="canevas" width="150" height="150"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function dessiner() {
  var canevas = document.getElementById('canevas');
  if (canevas.getContext) {
    var ctx = canevas.getContext('2d');

    ctx.beginPath();
    ctx.moveTo(75, 50);
    ctx.lineTo(100, 75);
    ctx.lineTo(100, 25);
    ctx.fill();
  }
}
</pre>

<p>Le résultat ressemble à :</p>

<p>{{EmbedLiveSample("Dessin_d'un_triangle", 110, 110, "triangle.png")}}</p>

<h3 id="Déplacement_du_stylo">Déplacement du stylo</h3>

<p>Une fonction très utile, qui ne dessine rien mais qui fait tout de même partie de la liste de trajets décrite plus haut, est la fonction <code>moveTo()</code>. La meilleure façon de l'imaginer est le fait de lever un stylo ou un crayon depuis une position sur un papier, et de le placer sur une autre.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.moveTo", "moveTo(x, y)")}}</dt>
 <dd>Déplace le stylo aux coordonnées <code>x</code> et <code>y</code>.</dd>
</dl>

<p>Lorsque le canevas est initialisé ou que <code>beginPath()</code> est appelé, vous souhaiterez typiquement utiliser <code>moveTo()</code> pour positionner le point de départ quelque part ailleurs. On pourrait aussi utiliser <code>moveTo()</code> pour dessiner des trajets non reliés. Jetez un coup d'œil à l'émoticon ci-dessous.</p>

<p>Pour essayer par vous-même, vous pouvez utiliser le fragment de code ci-dessous. Collez-le simplement dans la fonction <code>draw()</code> que nous avons vue plus tôt.</p>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="draw();"&gt;
   &lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');

    ctx.beginPath();
    ctx.arc(75, 75, 50, 0, Math.PI * 2, true);  // Cercle extérieur
    ctx.moveTo(110,75);
    ctx.arc(75, 75, 35, 0, Math.PI, false);  // Bouche (sens horaire)
    ctx.moveTo(65, 65);
    ctx.arc(60, 65, 5, 0, Math.PI * 2, true);  // Oeil gauche
    ctx.moveTo(95, 65);
    ctx.arc(90, 65, 5, 0, Math.PI * 2, true);  // Oeil droite
    ctx.stroke();
  }
}
</pre>

<p>Le résultat ressemble à ce qui suit :</p>

<p>{{EmbedLiveSample("Déplacement_du_stylo", 160, 160, "canvas_smiley.png")}}</p>

<p>Si vous voulez voir les lignes d'interconnexion, vous pouvez enlever les lignes qui appellent <code>moveTo()</code>.</p>

<div class="note">
<p><strong>Note :</strong> Pour en savoir plus sur la fonction <code>arc()</code>, voir la section {{anch("Arcs")}} ci-dessous.</p>
</div>

<h3 id="Les_lignes">Les lignes</h3>

<p>Pour dessiner des lignes droites, utilisez la méthode <code>lineTo()</code>.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.lineTo", "lineTo(x, y)")}}</dt>
 <dd>Dessine une ligne depuis la position de dessin courante jusqu'à la position spécifiée par <code>x</code> et <code>y</code>.</dd>
</dl>

<p>Cette méthode prend deux arguments, <code>x</code> et <code>y</code>, qui sont les coordonnées du point final de la ligne. Le point de départ dépend des trajets précédemment tracés, où le point final du trajet précédent est le point de départ du suivant, etc. Le point de départ peut aussi être changé en utilisant la méthode <code>moveTo()</code>.</p>

<p>L'exemple ci-dessous dessine deux triangles, un rempli et un filaire.</p>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="dessiner();"&gt;
   &lt;canvas id="canevas" width="150" height="150"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function dessiner() {
  var canevas = document.getElementById('canevas');
  if (canevas.getContext) {
    var ctx = canevas.getContext('2d');

    // Triangle plein
    ctx.beginPath();
    ctx.moveTo(25, 25);
    ctx.lineTo(105, 25);
    ctx.lineTo(25, 105);
    ctx.fill();

    // Triangle filaire
    ctx.beginPath();
    ctx.moveTo(125, 125);
    ctx.lineTo(125, 45);
    ctx.lineTo(45, 125);
    ctx.closePath();
    ctx.stroke();
  }
}
</pre>

<p>Il commence par appeler <code>beginPath()</code> pour démarrer un nouveau trajet de forme. Nous utilisons ensuite la méthode <code>moveTo()</code> pour déplacer le point de départ à la position désirée. En dessous, deux lignes sont dessinées, qui constituent deux côtés du triangle.</p>

<p>{{EmbedLiveSample("Les_lignes", 160, 160, "canvas_lineto.png")}}</p>

<p>Vous remarquerez la différence entre le triangle plein et le filaire. Cela, comme mentionné précédemment, vient du fait que les formes sont automatiquement fermées lorsqu'un trajet est rempli, mais pas lorsqu'elles sont dessinées au trait. Si nous avions omis le <code>closePath()</code> pour le triangle filaire, seules deux lignes auraient été tracées, et non pas un triangle complet.</p>

<h3 id="Les_arcs">Les arcs</h3>

<p>Pour dessiner des arcs ou des cercles, on utilise les méthodes <code>arc() ou arcTo()</code>.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.arc", "arc(x, y, rayon, angleInitial, angleFinal, antihoraire)")}}</dt>
 <dd>Dessine un arc de cercle qui est centré à la position <em>(x, y),</em> de rayon <em>r</em>, commençant à <em>angleInitial</em> et finissant à <em>angleFinal</em> en allant dans le sens indiqué par <em>antihoraire</em> (par défaut, horaire).</dd>
 <dt><strong>{{domxref("CanvasRenderingContext2D.arcTo", "arcTo(x1, y1, x2, y2, rayon)")}}</strong></dt>
 <dd>Dessine un arc avec les points de contrôle et l'angle donnés, relié au point précédent par une ligne droite.</dd>
</dl>

<p>Regardons plus en détail la méthode <code>arc</code>, qui prend six paramètres : <code>x</code> et <code>y</code> sont les coordonnées du centre du cercle sur lequel l'arc doit être tracé. <code>rayon</code> se passe d'explication. Les paramètres <code>angleInitial et</code> <code>angleFinal</code> définissent en radians les points de départ et d'arrivée de l'arc, le long de la courbe du cercle. Ceux-ci sont mesurés à partir de l'axe des x. Le paramètre <code>antihoraire</code> est une valeur booléenne qui, lorsque <code>true</code>, dessine l'arc dans le sens antihoraire, sinon, l'arc est dessiné dans le sens horaire.</p>

<div class="note">
<p><strong>Note :</strong> Les angles dans la fonction <code>arc</code> sont mesurés en radians, et non en degrés. Pour convertir des degrés en radians, vous pouvez utiliser l'expression JavaScript suivante : <code>radians = (Math.PI/180)*degres</code>.</p>
</div>

<p>L'exemple suivant est un peu plus complexe que ceux que nous avons vus plus haut. Il dessine 12 arcs différents, avec des angles et des remplissages différents.</p>

<p>Les deux <a href="/fr-FR/docs/Web/JavaScript/Reference/Statements/for">boucles <code>for</code></a> bouclent sur les lignes et les colonnes des arcs. Pour chaque arc, on commence un nouveau trajet en appelant <code>beginPath()</code>. Dans le code, chacun des paramètres dans l'arc est une variable pour des raisons de clarté, mais en réalité, vous n'avez pas besoin de le faire.</p>

<p>Les coordonnées <code>x</code> et <code>y</code> devraient être claires. <code>rayon</code> et <code>angleInitial</code> sont fixés. L'<code>angleFinal</code> commence à 180 degrés (demi-cercle) dans la première colonne et il est augmenté par pas de 90 degrés, pour finir par un cercle complet dans la dernière colonne.</p>

<p>L'instruction pour le paramètre <code>antihoraire</code> a pour résultat que la première et de la troisième ligne sont dessinées comme des arcs de sens horaire, et que la deuxième et quatrième sont dessinées comme des arcs de sens antihoraire. Enfin, l'instruction <code>if</code> fait des arcs filaires dans la moité supérieure, et des arcs remplis dans la moitié inférieure.</p>

<div class="note">
<p><strong>Note :</strong> Cet exemple requiert canevas légèrement plus large que les autres sur cette page : 150 x 200 pixels.</p>
</div>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="dessiner();"&gt;
   &lt;canvas id="canevas" width="150" height="200"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function dessiner() {
  var canevas = document.getElementById('canevas');
  if (canevas.getContext) {
    var ctx = canevas.getContext('2d');

    for(var i = 0; i &lt; 4; i++) {
      for(var j = 0; j &lt; 3; j++) {
        ctx.beginPath();
        var x = 25 + j * 50; // Coordonnée x
        var y = 25 + i * 50; // Coordonnée y
        var rayon = 20; // Rayon de l'arc
        var angleInitial = 0; // Point de départ sur le cercle
        var angleFinal = Math.PI + (Math.PI * j) / 2; // Point d'arrivée sur le cercle
        var antihoraire = i % 2 != 0; // Horaire ou antihoraire

        ctx.arc(x, y, rayon, angleInitial, angleFinal, antihoraire);

        if (i&gt;1) {
          ctx.fill();
        } else {
          ctx.stroke();
        }
      }
    }
  }
}
</pre>

<p>{{EmbedLiveSample("Les_arcs", 160, 210, "canvas_arc.png")}}</p>

<h3 id="Les_courbes_quadratiques_et_de_Bézier">Les courbes quadratiques et de Bézier</h3>

<p>Le type suivant de trajets disponible est la <a href="https://fr.wikipedia.org/wiki/Courbe_de_B%C3%A9zier">courbe de Bézier</a>, disponible en deux variétés, cubique et quadratique. Elles sont généralement utilisées pour dessiner des formes naturelles complexes.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.quadraticCurveTo", "quadraticCurveTo(cp1x, cp1y, x, y)")}}</dt>
 <dd>Dessine une courbe de Bézier quadratique depuis la position courante du stylo jusqu'au point final spécifié par <code>x</code> et <code>y</code>, en utilisant le point de contrôle spécifié par <code>cp1x</code> et <code>cp1y</code>.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.bezierCurveTo", "bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)")}}</dt>
 <dd>Dessine une courbe de Bézier cubique depuis la position courante du stylo jusqu'au point spécifié par <code>x</code> et <code>y</code>, en utilisant les points de contrôle (<code>cp1x</code>, <code>cp1y</code>) et (<code>cp2x</code>, <code>cp2y</code>).</dd>
</dl>

<p>La différence entre ces deux méthodes est mieux décrite par l'image à droite. Une courbe quadratique de Bézier a un point de départ et un point d'arrivée (points bleus), et seulement un <strong>point de contrôle</strong> (indiqué par le point rouge), tandis qu'une courbe de Bézier cubique utilise deux points de contrôle.</p>

<p><img alt="" src="canvas_curves.png"></p>

<p>Les paramètres <code>x</code> et <code>y</code> de ces deux méthodes sont les coordonnées du point d'arrivée. <code>cp1x</code> et <code>cp1y</code> sont les coordonnées du premier point de contrôle, et  <code>cp2x</code> et <code>cp2y</code> sont les coordonnées du second point de contrôle.</p>

<p>Utiliser des courbes quadratiques et cubiques de Bézier peut constituer un certain défi, car à la différence d'un logiciel de tracé des vecteurs comme <em>Adobe Illustrator</em>, nous n'avons pas de retour visuel direct concernant ce que nous faisons. Cela rend passablement difficile le dessin de formes complexes. Dans l'exemple suivant, nous allons dessiner quelques formes naturelles simples, mais si vous avez du temps et - surtout - de la patience, des formes bien plus complexes peuvent être créées.</p>

<p>Il n'y a rien de très difficile dans ces exemples. Dans les deux cas, on peut voir une succession de courbes être dessinées qui aboutissent finalement à une forme complète.</p>

<h4 id="Courbes_de_Bézier_quadratiques">Courbes de Bézier quadratiques</h4>

<p>Cet exemple utilise plusieurs courbes quadratiques de Bézier pour rendre une bulle de dialogue.</p>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="dessiner();"&gt;
   &lt;canvas id="canevas" width="150" height="150"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function dessiner() {
  var canevas = document.getElementById('canevas');
  if (canevas.getContext) {
    var ctx = canevas.getContext('2d');

    // Exemples de courbes quadratiques
    ctx.beginPath();
    ctx.moveTo(75, 25);
    ctx.quadraticCurveTo(25, 25, 25, 62.5);
    ctx.quadraticCurveTo(25, 100, 50, 100);
    ctx.quadraticCurveTo(50, 120, 30, 125);
    ctx.quadraticCurveTo(60, 120, 65, 100);
    ctx.quadraticCurveTo(125, 100, 125, 62.5);
    ctx.quadraticCurveTo(125, 25, 75, 25);
    ctx.stroke();
  }
}
</pre>

<p>{{EmbedLiveSample("Courbes_de_Bézier_quadratiques", 160, 160, "canvas_quadratic.png")}}</p>

<h4 id="Les_courbes_de_Bézier_cubiques">Les courbes de Bézier cubiques</h4>

<p>Cet exemple dessine un cœur en utilisant les courbes de Bézier cubiques.</p>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="dessiner();"&gt;
   &lt;canvas id="canevas" width="150" height="150"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function dessiner() {
  var canevas = document.getElementById('canevas');
  if (canevas.getContext) {
    var ctx = canevas.getContext('2d');

    // Exemple de courbes cubiques
    ctx.beginPath();
    ctx.moveTo(75, 40);
    ctx.bezierCurveTo(75, 37, 70, 25, 50, 25);
    ctx.bezierCurveTo(20, 25, 20, 62.5, 20, 62.5);
    ctx.bezierCurveTo(20, 80, 40, 102, 75, 120);
    ctx.bezierCurveTo(110, 102, 130, 80, 130, 62.5);
    ctx.bezierCurveTo(130, 62.5, 130, 25, 100, 25);
    ctx.bezierCurveTo(85, 25, 75, 37, 75, 40);
    ctx.fill();
  }
}
</pre>

<p>{{EmbedLiveSample("Les_courbes_de_Bézier_cubiques", 160, 160, "canvas_bezier.png")}}</p>

<h3 id="Rectangles">Rectangles</h3>

<p>En plus des trois méthodes que nous avons vues dans {{anch("Dessin de rectangles")}}, qui dessinent des formes rectangulaires directement sur le canevas, il y a la méthode <code>rect()</code>, qui ajoute un trajet rectangulaire à un trajet actuellement ouvert.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.rect", "rect(x, y, largeur, hauteur)")}}</dt>
 <dd>Dessine un rectangle dont l'angle supérieur gauche est spécifié par (<code>x</code>, <code>y</code>), avec les <code>largeur</code> et <code>hauteur</code> spécifiées.</dd>
</dl>

<p>Quand cette méthode est exécutée, la méthode <code>moveTo()</code> est automatiquement appelée avec les paramètres (0,0). En d'autres termes, la position en cours du stylo est automatiquement réinitialisée aux coordonnées par défaut.</p>

<h3 id="Combiner_les_possibilités">Combiner les possibilités</h3>

<p>Jusqu'à présent, chaque exemple de cette page a utilisé un seul type de fonction de trajet par forme. Cependant, il n'y a pas de limite au nombre ou aux types de trajets que vous pouvez utiliser pour créer une forme. Ainsi, dans ce dernier exemple, combinons toutes les fonctions de trajet pour faire un ensemble de personnages d'un jeu très célèbre.</p>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="dessiner();"&gt;
   &lt;canvas id="canevas" width="150" height="150"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function dessiner() {
  var canevas = document.getElementById('canevas');
  if (canevas.getContext) {
    var ctx = canevas.getContext('2d');

    rectArrondi(ctx, 12, 12, 150, 150, 15);
    rectArrondi(ctx, 19, 19, 150, 150, 9);
    rectArrondi(ctx, 53, 53, 49, 33, 10);
    rectArrondi(ctx, 53, 119, 49, 16, 6);
    rectArrondi(ctx, 135, 53, 49, 33, 10);
    rectArrondi(ctx, 135, 119, 25, 49, 10);

    ctx.beginPath();
    ctx.arc(37, 37, 13, Math.PI/7, -Math.PI/7, false);
    ctx.lineTo(31, 37);
    ctx.fill();

    for(var i = 0; i&lt; 8; i++) {
      ctx.fillRect(51 + i * 16, 35, 4, 4);
    }

    for(i = 0; i &lt; 6; i++) {
      ctx.fillRect(115, 51 + i * 16, 4, 4);
    }

    for(i = 0; i &lt; 8; i++) {
      ctx.fillRect(51 + i * 16, 99, 4, 4);
    }

    ctx.beginPath();
    ctx.moveTo(83, 116);
    ctx.lineTo(83, 102);
    ctx.bezierCurveTo(83, 94, 89, 88, 97, 88);
    ctx.bezierCurveTo(105, 88, 111, 94, 111, 102);
    ctx.lineTo(111, 116);
    ctx.lineTo(106.333, 111.333);
    ctx.lineTo(101.666, 116);
    ctx.lineTo(97, 111.333);
    ctx.lineTo(92.333, 116);
    ctx.lineTo(87.666, 111.333);
    ctx.lineTo(83, 116);
    ctx.fill();

    ctx.fillStyle = "white";
    ctx.beginPath();
    ctx.moveTo(91, 96);
    ctx.bezierCurveTo(88, 96, 87, 99, 87, 101);
    ctx.bezierCurveTo(87, 103, 88, 106, 91, 106);
    ctx.bezierCurveTo(94, 106, 95, 103, 95, 101);
    ctx.bezierCurveTo(95, 99, 94, 96, 91, 96);
    ctx.moveTo(103, 96);
    ctx.bezierCurveTo(100, 96, 99, 99, 99, 101);
    ctx.bezierCurveTo(99, 103, 100, 106, 103, 106);
    ctx.bezierCurveTo(106, 106, 107, 103, 107, 101);
    ctx.bezierCurveTo(107, 99, 106, 96, 103, 96);
    ctx.fill();

    ctx.fillStyle = "black";
    ctx.beginPath();
    ctx.arc(101, 102, 2, 0, Math.PI * 2, true);
    ctx.fill();

    ctx.beginPath();
    ctx.arc(89, 102, 2, 0, Math.PI * 2, true);
    ctx.fill();
  }
}

// Une fonction utilitaire pour tracer des rectangles avec des coins arrondis

function rectArrondi(ctx, x, y, largeur, hauteur, rayon) {
  ctx.beginPath();
  ctx.moveTo(x, y + rayon);
  ctx.lineTo(x, y + hauteur - rayon);
  ctx.quadraticCurveTo(x, y + hauteur, x + rayon, y + hauteur);
  ctx.lineTo(x + largeur - rayon, y + hauteur);
  ctx.quadraticCurveTo(x + largeur, y + hauteur, x + largeur, y + hauteur - rayon);
  ctx.lineTo(x + largeur, y + rayon);
  ctx.quadraticCurveTo(x + largeur, y, x + largeur - rayon, y);
  ctx.lineTo(x + rayon,y);
  ctx.quadraticCurveTo(x, y, x, y + rayon);
  ctx.stroke();
}

</pre>

<p>L'image résultante ressemble à ce qui suit :</p>

<p>{{EmbedLiveSample("Combiner_les_possibilités", 160, 160)}}</p>

<p>Nous ne l'expliquerons pas plus en détails, du fait que c'est étonnament simple. Les choses les plus importantes à noter sont l'utilisation de la propriété <code>fillStyle</code> sur le contexte du dessin, et l'utilisation d'une fonction utilitaire dans ce cas, rectArrondi<code>())</code>. L'utilisation de fonctions utilitaires pour des éléments de dessin que vous faites souvent peut être très utile, et peut réduire la quantité de code dont vous avez besoin, ainsi que sa complexité.</p>

<p>Nous reviendrons sur <code>fillStyle</code> plus en détail plus loin dans ce tutoriel. Pour l'instant, tout ce que nous faisons est de l'utiliser pour changer en blanc la couleur pour les trajets depuis la couleur noire par défaut, et inversement ensuite.</p>

<h2 id="Objets_Path2D">Objets Path2D</h2>

<p>Comme nous l'avons vu dans le dernier exemple, il peut y avoir une série de trajets et d'instructions de dessin pour dessiner des objets sur votre canevas. Pour simplifier le code et améliorer les performances, l'objet {{domxref("Path2D")}}, disponible dans les versions récentes des navigateurs, vous permet de mettre en cache ou d'enregistrer ces instrucions de dessin. Vous pourrez alors rejouer vos trajets rapidement.<br>
 Voyons comment nous pouvons construire un objet <code>Path2D </code>:</p>

<dl>
 <dt>{{domxref("Path2D.Path2D", "Path2D()")}}</dt>
 <dd>Le constructor <code><strong>Path2D()</strong></code> retourne un objet <code>Path2D</code> nouvellement instancié, optionellement avec un autre trajet comme argument (crée une copie), ou optionellement avec une chaîne constituée de données de <a href="/fr-FR/docs/Web/SVG/Tutorial/Paths">trajet SVG</a>.</dd>
</dl>

<pre class="notranslate"><code>new Path2D();     // objet trajet vide
new Path2D(trajet); // copie depuis un autre objet Path2D
new Path2D(d);    // trajet depuis des données de trajet SVG</code></pre>

<p>Toutes les <a href="/en-US/docs/Web/API/CanvasRenderingContext2D#Paths">méthodes de trajet</a> telles que <code>moveTo</code>, <code>rect</code>, <code>arc</code> ou <code>quadraticCurveTo</code>, etc., que nous avons appris à connaître ci-dessus, sont disponibles sur les objets <code>Path2D</code>.</p>

<p>L'API <code>Path2D</code> ajoute aussi une manière de combiner des trajets en utilisant la méthode <code>addPath</code>. Cela peut être utile quand vous voulez contruire des objets à partir de plusieurs composants, par exemple.</p>

<dl>
 <dt>{{domxref("Path2D.addPath", "Path2D.addPath(trajet [, transformation])")}}</dt>
 <dd>Ajoute un trajet, au trajet en cours, avec une matrice de transformation.</dd>
</dl>

<h3 id="Exemple_de_Path2D">Exemple de Path2D</h3>

<p>Dans cet exemple, on crée un rectangle et un cercle. Tous deux sont stockés comme des objets <code>Path2D</code>, de sorte qu'ils sont disponibles pour un usage ultérieur. Avec la nouvelle API <code>Path2D</code>, plusieurs méthodes ont été mises à jour pour accepter optionnellement un objet <code>Path2D</code> à utiliser au lieu du trajet en cours. Ici, <code>stroke</code> et <code>fill</code> sont utilisés avec un argument de trajet pour dessiner les deux objets sur le canevas, par exemple.</p>

<pre class="brush: html hidden">&lt;html&gt;
 &lt;body onload="dessiner();"&gt;
   &lt;canvas id="canvas" width="130" height="100"&gt;&lt;/canvas&gt;
 &lt;/body&gt;
&lt;/html&gt;
</pre>

<pre class="brush: js">function dessiner() {
  var canevas = document.getElementById('canvas');
  if (canevas.getContext){
    var ctx = canevas.getContext('2d');

    var rectangle = new Path2D();
    rectangle.rect(10, 10, 50, 50);

    var cercle = new Path2D();
    cercle.moveTo(125, 35);
    cercle.arc(100, 35, 25, 0, 2 * Math.PI);

    ctx.stroke(rectangle);
    ctx.fill(cercle);
  }
}</pre>

<p>{{EmbedLiveSample("Exemple_de_Path2D", 130, 110, "path2d.png")}}</p>

<h3 id="Utilisation_de_trajets_SVG">Utilisation de trajets SVG</h3>

<p>Une autre fonctionnalité puissante de la nouvelle API <code>Path2D</code> de canevas est l'utilisation de <a href="/fr-FR/docs/Web/SVG/Tutorial/Paths">données de trajet SVG</a> pour initialiser des trajets sur votre canevas. Cela peut vous permettre de faire circuler des données de trajet et les réutiliser, à la fois en SVG et dans un canevas.</p>

<p>Le trajet se déplacera au point (<code>M10 10</code>) et se déplacera alors de 80 points horizontalement vers la droite (<code>h 80</code>), ensuite de 80 points vers le bas (<code>v 80</code>), puis de 80 points vers la gauche (<code>h -80</code>), et reviendra alors au départ (<code>z</code>). Vous pouvez voir cet exemple sur la page du <a href="/en-US/docs/Web/API/Path2D.Path2D#Using_SVG_paths">constructeur P<code>ath2D</code></a>.</p>

<pre class="notranslate"><code>var p = new Path2D("M10 10 h 80 v 80 h -80 Z");</code></pre>

<p>{{PreviousNext("Tutoriel_canvas/Utilisation_de_base", "Tutoriel_canvas/Ajout_de_styles_et_de_couleurs")}}</p>
