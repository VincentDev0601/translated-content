---
title: Ajout de styles et de couleurs
slug: Web/API/Canvas_API/Tutorial/Applying_styles_and_colors
tags:
  - Canvas
  - Couleurs
  - Formes géométriques
  - Graphismes
  - Tutorial
translation_of: Web/API/Canvas_API/Tutorial/Applying_styles_and_colors
original_slug: Web/API/Canvas_API/Tutoriel_canvas/Ajout_de_styles_et_de_couleurs
---
<div>{{CanvasSidebar}} {{PreviousNext("Tutoriel_canvas/Formes_géométriques", "Dessin_de_texte_avec_canvas")}}</div>

<p>Dans le chapitre sur <a href="/fr/docs/Tutoriel_canvas/Formes_g%C3%A9om%C3%A9triques">les formes géométriques</a>, nous avons utilisé les styles de lignes et de remplissage par défaut. Ici, nous allons explorer les options de canvas à notre disposition pour rendre nos dessins un peu plus attrayants. Vous apprendrez comment ajouter des couleurs différentes, des styles de ligne, des dégradés, des motifs et des ombres à vos dessins.</p>

<h2 id="Colors">Les couleurs</h2>

<p>Jusqu'à présent, nous avons seulement vu des méthodes sur le contexte de dessin. Si nous voulons appliquer des couleurs à une forme, il y a deux propriétés importantes que nous pouvons utiliser : <code>fillStyle</code> et <code>strokeStyle</code> .</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle = color")}}</dt>
 <dd>Définit le style utilisé lors du remplissage de formes.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle = color")}}</dt>
 <dd>Définit le style pour les contours des formes.</dd>
</dl>

<p><code>color</code> est une chaîne représentant un CSS {{cssxref("&lt;color&gt;")}}, d'un objet gradient ou d'un objet motif. Nous allons examiner le gradient et la structure des objets plus tard. Par défaut, l'encadrement et la couleur de remplissage sont fixés sur noir (valeur <code>#000000</code> de CSS <code>color</code>).</p>

<div class="note">
<p><strong>Note :</strong> Lorsque vous définissez <code>strokeStyle</code> et <code>fillStyle</code>, la nouvelle valeur devient la valeur par défaut pour toutes les formes en cours d'élaboration à partir de là. Pour chaque forme que vous voulez dans une couleur différente, vous aurez besoin de réaffecter <code>fillStyle</code> ou <code>strokeStyle</code>.</p>
</div>

<p>Les chaînes pour être valides, doivent être conforme à la spécification CSS {{cssxref("&lt;color&gt;")}}. Chacun des exemples suivants décrit la même couleur.</p>

<pre class="brush: js">// Les valeurs possibles de fillStyle pour "orange"

ctx.fillStyle = 'orange';
ctx.fillStyle = '#FFA500';
ctx.fillStyle = 'rgb(255, 165, 0)';
ctx.fillStyle = 'rgba(255, 165, 0, 1)';</pre>

<h3 id="A_fillStyle_example">Un exemple <code>fillStyle</code></h3>

<p>Dans cet exemple, nous utilisons une nouvelle fois deux boucles <code>for</code> pour dessiner une grille de rectangles, chacun dans une couleur différente. L'image résultante devrait ressembler à la capture d'écran. Il n'y a rien de spectaculaire ici. Nous utilisons les deux variables <code>i</code> et <code>j</code> pour générer une couleur RVB unique pour chaque carré, et seulement modifier les valeurs rouges et vertes. Le canal bleu a une valeur fixe. En modifiant les canaux, vous pouvez générer toutes sortes de palettes. En augmentant les étapes, vous pouvez obtenir quelque chose qui ressemble à des palettes de couleurs que Photoshop utilise.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  for (var i = 0; i &lt; 6; i++) {
    for (var j = 0; j &lt; 6; j++) {
      ctx.fillStyle = 'rgb(' + Math.floor(255 - 42.5 * i) + ',' +
                       Math.floor(255 - 42.5 * j) + ',0)';
      ctx.fillRect(j * 25, i * 25, 25, 25);
    }
  }
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>


<p>Le résultat ressemble à ceci:</p>

<p>{{EmbedLiveSample("A_fillStyle_example", 160, 160, "canvas_fillstyle.png")}}</p>

<h3 id="A_strokeStyle_example">Un exemple <code>strokeStyle</code></h3>

<p>Cet exemple est similaire à celui ci-dessus, mais utilise <code>strokeStyle</code> pour changer les couleurs des contours des formes. Nous utilisons la méthode <code>arc()</code> pour dessiner des cercles au lieu de carrés.</p>

<pre class="brush: js">function draw() {
    var ctx = document.getElementById('canvas').getContext('2d');
    for (var i = 0; i &lt; 6; i++) {
      for (var j = 0; j &lt; 6; j++) {
        ctx.strokeStyle = 'rgb(0, ' + Math.floor(255 - 42.5 * i) + ', ' +
                         Math.floor(255 - 42.5 * j) + ')';
        ctx.beginPath();
        ctx.arc(12.5 + j * 25, 12.5 + i * 25, 10, 0, Math.PI * 2, true);
        ctx.stroke();
      }
    }
  }</pre>


<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>


<p>Le résultat ressemble à ceci :</p>

<p>{{EmbedLiveSample("A_strokeStyle_example", "180", "180", "canvas_strokestyle.png")}}</p>

<h2 id="Transparency">Transparence</h2>

<p>En plus de dessiner des formes opaques sur la toile, nous pouvons également dessiner des formes semi-transparentes (ou translucides). Cela se fait soit par le réglage de <code>globalAlpha</code> ou en attribuant une couleur semi-transparente à <code>strokeStyle</code> et/ou <code>fillStyle</code>.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.globalAlpha", "globalAlpha = transparencyValue")}}</dt>
 <dd>Applique la valeur de transparence spécifiée à toutes les formes futures tracées sur le Canvas. La valeur doit être comprise entre 0.0 (complètement transparent) à 1.0 (complètement opaque). Cette valeur est de 1,0 (complètement opaque) par défaut.</dd>
</dl>

<p>La propriété<code> globalAlpha</code> peut être utile si vous voulez dessiner un grand nombre de formes sur la toile avec la même transparence, mais sinon, il est généralement plus utile de définir la transparence sur les formes individuelles lors de la définition de leurs couleurs.</p>

<p>Parce que <code>strokeStyle</code> et <code>fillStyle</code> acceptent les valeurs de couleur rvba CSS, nous pouvons utiliser la notation suivante pour attribuer une couleur transparente.</p>

<pre class="brush: js">//Affecter des couleurs transparentes pour dessiner et remplir le style

ctx.strokeStyle = "rgba(255, 0, 0, .5)";
ctx.fillStyle = "rgba(255, 0, 0, .5)";
</pre>

<p>La fonction <code>rgba()</code> <em>(rvba)</em> est similaire à la fonction <code>rgb()</code> <em>(rvb)</em> mais il a un paramètre supplémentaire. Le dernier paramètre définit la valeur de la transparence de cette couleur particulière. La plage valide est entre 0,0 (totalement transparent) et 1,0 (totalement opaque).</p>

<h3 id="A_globalAlpha_example">Un exemple <code>globalAlpha</code></h3>

<p>Dans cet exemple, nous allons dessiner un fond de quatre carrés de couleurs différentes. En plus de ceux-ci, nous allons dessiner un ensemble de cercles semi-transparents. <code>globalAlpha</code> est réglé à <code>0.2</code> et sera utilisé pour toutes les formes. Chaque étape de boucle <code>for</code> dessine un ensemble de cercles avec un rayon croissant. Le résultat final est un gradient radial. En superposant toujours plus de cercles, les uns au-dessus des autres, nous réduisons efficacement la transparence des cercles qui ont déjà été établis. En augmentant le pas et le nombre de cercles, l'arrière-plan devrait complètement disparaître du centre de l'image.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  // draw background
  ctx.fillStyle = '#FD0';
  ctx.fillRect(0, 0, 75, 75);
  ctx.fillStyle = '#6C0';
  ctx.fillRect(75, 0, 75, 75);
  ctx.fillStyle = '#09F';
  ctx.fillRect(0, 75, 75, 75);
  ctx.fillStyle = '#F30';
  ctx.fillRect(75, 75, 75, 75);
  ctx.fillStyle = '#FFF';

  // règle la valeur de transparence
  ctx.globalAlpha = 0.2;

  // Dessine des cercles semi-transparents
  for (i = 0; i &lt; 7; i++) {
    ctx.beginPath();
    ctx.arc(75, 75, 10 + 10 * i, 0, Math.PI * 2, true);
    ctx.fill();
  }
}</pre>


<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>{{EmbedLiveSample("A_globalAlpha_example", "180", "180", "canvas_globalalpha.png")}}</p>

<h3 id="An_example_using_rgba">Un exemple en utilisant <code>rgba()</code></h3>

<p>Dans ce deuxième exemple, nous faisons quelque chose de similaire, mais au lieu de dessiner des cercles, nous dessinons de petits rectangles à l'opacité croissante. L'utilisation de <code>rgba()</code> nous donne un peu plus de contrôle et de flexibilité.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');

  // Dessine le fond
  ctx.fillStyle = 'rgb(255, 221, 0)';
  ctx.fillRect(0, 0, 150, 37.5);
  ctx.fillStyle = 'rgb(102, 204, 0)';
  ctx.fillRect(0, 37.5, 150, 37.5);
  ctx.fillStyle = 'rgb(0, 153, 255)';
  ctx.fillRect(0, 75, 150, 37.5);
  ctx.fillStyle = 'rgb(255, 51, 0)';
  ctx.fillRect(0, 112.5, 150, 37.5);

  // Dessine des rectangles semi-transparents
  for (var i = 0; i &lt; 10; i++) {
    ctx.fillStyle = 'rgba(255, 255, 255, ' + (i + 1) / 10 + ')';
    for (var j = 0; j &lt; 4; j++) {
      ctx.fillRect(5 + i * 14, 5 + j * 37.5, 14, 27.5);
    }
  }
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>{{EmbedLiveSample("An_example_using_rgba()", "180", "180", "canvas_rgba.png")}}</p>

<h2 id="Line_styles">Le style des lignes</h2>

<p>Il y a plusieurs propriétés qui nous permettent de modifier le style des lignes.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.lineWidth", "lineWidth = value")}}</dt>
 <dd>Définit la largeur des lignes qui serons tracées.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.lineCap", "lineCap = type")}}</dt>
 <dd>Définit l'apparence des extrémités des lignes.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.lineJoin", "lineJoin = type")}}</dt>
 <dd>Définit l'apparence des «coins» où les lignes se rencontrent.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.miterLimit", "miterLimit = value")}}</dt>
 <dd>Établit une limite lorsque deux lignes se rejoignent en un angle aigu, pour permettre de contrôler l'épaisseur de la jonction.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.getLineDash", "getLineDash()")}}</dt>
 <dd>Retourne le tableau du modele courant de ligne contenant un nombre pair de nombres positifs.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.setLineDash", "setLineDash(segments)")}}</dt>
 <dd>Définit le modele de ligne.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.lineDashOffset", "lineDashOffset = value")}}</dt>
 <dd>Indique où commencer un modele sur une ligne.</dd>
</dl>

<p>Vous aurez une meilleure compréhension de ce qu'ils font en regardant les exemples ci-dessous.</p>

<h3 id="A_lineWidth_example">Un exemple <code>lineWidth</code></h3>

<p>Cette propriété définit l'épaisseur de la ligne actuelle. Les valeurs doivent être des nombres positifs. Par défaut, cette valeur est définie à 1,0.</p>

<p>La largeur de ligne est l'épaisseur centrée sur le tracé. En d'autres termes, la zone qui est dessinée s'étend de part et d'autre du tracé. Parce que les coordonnées ne font pas référence directement aux pixels, une attention particulière doit être prise pour obtenir des lignes horizontales et verticales nettes.</p>

<p>Dans l'exemple ci-dessous, 10 lignes droites sont dessinées avec des largeurs croissantes. La ligne à l'extrême gauche a 1,0 unités de large. Cependant, celle ci et toutes les lignes d'épaisseur impair ne semblent pas nettes, en raison du positionnement du tracé.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  for (var i = 0; i &lt; 10; i++) {
    ctx.lineWidth = 1 + i;
    ctx.beginPath();
    ctx.moveTo(5 + i * 14, 5);
    ctx.lineTo(5 + i * 14, 140);
    ctx.stroke();
  }
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>{{EmbedLiveSample("A_lineWidth_example", "180", "180", "canvas_linewidth.png")}}</p>

<p>Pour l'obtention de lignes nettes, il faut comprendre comment les lignes sont tracées. Ci-dessous, la grille représente la grille de coordonnées. Les carrés sont des pixels réels de l'écran. Dans la première grille, un rectangle (2,1) à (5,5) est rempli. La zone entière couverte par les lignes (rouge clair) tombe sur les limites des pixels, de sorte que le rectangle rempli résultant aura des bords nets.</p>

<p><img alt="" src="canvas-grid.png"></p>

<p>Si vous considérez un tracé de (3,1) à (3,5) avec une épaisseur de ligne de <code>1.0</code>, vous vous retrouvez dans la situation de la deuxième grille. La surface réelle à remplir (bleu foncé) se prolonge seulement à moitié sur les pixels de part et d'autre du chemin. Une approximation de ceci doit être rendue, ce qui signifie que ces pixels sont partiellement ombrés, et le résultat est que toute la zone (le bleu clair et bleu foncé) est remplie avec une couleur moitié moins sombre que la couleur du tracé attendu. C'est ce qui arrive avec la largeur de <code>1.0</code> dans l'exemple précédent.</p>

<p>Pour résoudre ce problème, vous devez être très précis dans la création de votre tracé. Sachant qu'une largeur de <code>1.0</code> s'étendra d'une demi-unité de chaque côté du tracé, créer le tracé de (3.5,1) à (3.5,5) aboutit à l'exemple trois pour une largeur de <code>1.0</code> et au remplissage d'un seul pixel de ligne verticale.</p>

<div class="note">
<p><strong>Note:</strong> Sachez que dans notre exemple de ligne verticale, la position Y fait toujours référence à une position de grille entière — sinon, vous verrez des pixels à moitié colorés à gauche et à droite (mais notez aussi que ce comportement dépend de l'actuel style <code>lineCap</code>, dont la valeur par défaut est <code>butt</code>. Vous pouvez essayer de tracer des traits consistants avec des coordonnées non-entières pour les lignes et avec une largeur particulière, en définissant le style <code>lineCap</code> à <code>square</code>, pour que le bord extérieur du trait autour du point final soit automatiquement étendu pour couvrir le pixel entier).</p>

<p>Notez également que seuls les points de début et de fin d'un chemin sont affectés : si un chemin est fermé avec <code>closePath ()</code>, il n'y a pas de point de départ ni de point final ; à la place, tous les points d'extrémité du chemin sont connectés à leurs segments joints précédent et suivant, en utilisant le paramètre courant du style <code>lineJoin</code>, dont la valeur par défaut est <code>miter</code>, avec pour effet d'étendre automatiquement les bordures extérieures des segments connectés à leur point d'intersection. Ainsi, le trait de rendu couvrira exactement les pixels pleins centrés à chaque extrémité si ces segments connectés sont horizontaux et / ou verticaux. Voir les deux sections suivantes pour les démonstrations de ces styles de lignes supplémentaires.</p>
</div>

<p>Pour les lignes de largeur paire, chaque moitié finit par être un nombre entier de pixels, vous voulez donc un chemin entre les pixels (c'est-à-dire (3,1) à (3,5)), au lieu de descendre au milieu des pixels .</p>

<p>Bien que légèrement ennuyeux quand on travaille avec des graphismes 2D évolutifs, en accordant une attention à la grille de pixels et à la position des tracés, vous vous assurez du comportement correct de vos dessins, et ce, indépendamment de la mise à l'échelle ou d'autres transformations. Une ligne verticale de largeur 1,0 à la bonne position deviendra une ligne de 2 pixels nette à l'échelle 2.</p>

<h3 id="A_lineCap_example">Un exemple de <code>lineCap</code></h3>

<p>La propriété <code>lineCap</code> détermine comment les extrêmités de chaque ligne sont dessinées. Il y a trois valeurs possibles pour la propriété : <code>butt</code>, <code>round</code> et <code>square</code>. Par défaut, la propriété est définie à <code>butt</code>.</p>

<dl>
 <dt><code>butt </code><em>(bout)</em></dt>
 <dd>L'extrémité des lignes est en angle droit.</dd>
 <dt><code>round </code><em>(rond)</em></dt>
 <dd>Les extrémités sont arrondies.</dd>
 <dt><code>square </code><em>(carré)</em></dt>
 <dd>Les extrémités sont en angle droit en ajoutant une extension d'une largeur égale à la ligne et une hauteur égale à la moitié de la largeur de la ligne.</dd>
</dl>

<p>Dans cet exemple, nous avons tracé trois lignes, chacune avec une valeur différente pour la propriété <code>lineCap</code>. Nous avons par ailleurs ajouté deux guides pour voir exactement les différences entre les trois lignes. Chacune de ces trois lignes est identique entre les deux traits bleus.</p>

<p>La ligne de gauche utilise l'option par défaut <code>butt</code>. Vous pourrez noter qu'elle est entièrement dessinée entre les deux guides. La deuxième utilise l'option <code>round</code>. Elle ajoute un demi-cercle à chaque extrémité d'un rayon valant la moitié de la largeur de la ligne. La ligne de droite utilise l'option <code>square</code>. Elle ajoute une extension avec une largeur égale à la ligne et une hauteur équivalante à la moitié de la largeur de la ligne.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  var lineCap = ['butt', 'round', 'square'];

  // Dessiner des guides
  ctx.strokeStyle = '#09f';
  ctx.beginPath();
  ctx.moveTo(10, 10);
  ctx.lineTo(140, 10);
  ctx.moveTo(10, 140);
  ctx.lineTo(140, 140);
  ctx.stroke();

  // Dessiner des lignes
  ctx.strokeStyle = 'black';
  for (var i = 0; i &lt; lineCap.length; i++) {
    ctx.lineWidth = 15;
    ctx.lineCap = lineCap[i];
    ctx.beginPath();
    ctx.moveTo(25 + i * 50, 10);
    ctx.lineTo(25 + i * 50, 140);
    ctx.stroke();
  }
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>{{EmbedLiveSample("A_lineCap_example", "180", "180", "canvas_linecap.png")}}</p>

<h3 id="A_lineJoin_example">Un exemple de <code>lineJoin</code></h3>

<p>La propriété <code>lineJoin</code> détermine comment deux segments (lignes, arcs ou courbes), de largeur non nulle se connectant dans une forme, sont joints ensemble (les segments de longueur nulle, dont les coordonnées de départ et de fin sont exactement les mêmes, sont ignorés).</p>

<p>Il existe trois valeurs possibles pour cette propriété : <code>round</code>, <code>bevel</code> et <code>miter</code>. Par défaut, cette propriété est définie à <code>miter</code>. Notez que le paramètre <code>lineJoin</code> n'a pas d'effet si les deux segments connectés ont la même direction, parce qu'aucune zone de jointure ne sera ajoutée dans ce cas.</p>

<dl>
 <dt><code>round </code><em>(rond)</em></dt>
 <dd>Arrondit les angles des segments en ajoutant un arc de cercle centré à l'extrémité commune des segments connectés. Le rayon de ces angles arrondis est égal à la moitié de la largeur du trait.</dd>
 <dt><code>bevel </code><em>(biseau)</em></dt>
 <dd>Ajoute un triangle à l'extrémité commune des segments connectés.</dd>
 <dt><code>miter </code><em>(onglet)</em></dt>
 <dd>Les segments connectés sont reliés en prolongeant leurs bords extérieurs pour se connecter en un seul point, avec pour effet de remplir une zone supplémentaire en forme de losange. Ce paramètre est effectué par la propriété miterLimit qui est expliquée ci-dessous.</dd>
</dl>

<p>L'exemple ci-dessous dessine trois chemins différents, démontrant chacun de ces trois paramètres de propriété<code> lineJoin</code> ; la sortie est montrée ci-dessus.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  var lineJoin = ['round', 'bevel', 'miter'];
  ctx.lineWidth = 10;
  for (var i = 0; i &lt; lineJoin.length; i++) {
    ctx.lineJoin = lineJoin[i];
    ctx.beginPath();
    ctx.moveTo(-5, 5 + i * 40);
    ctx.lineTo(35, 45 + i * 40);
    ctx.lineTo(75, 5 + i * 40);
    ctx.lineTo(115, 45 + i * 40);
    ctx.lineTo(155, 5 + i * 40);
    ctx.stroke();
  }
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>
</div>

<p>{{EmbedLiveSample("A_lineJoin_example", "180", "180", "canvas_linejoin.png")}}</p>

<h3 id="A_demo_of_the_miterLimit_property">Une démonstration de la propriété <code>miterLimit</code></h3>

<p>Comme vous l'avez vu dans l'exemple précédent, lorsque vous joignez deux lignes avec l'option d'onglet, les bords extérieurs des deux lignes d'assemblage sont étendus jusqu'au point où ils se rencontrent. Pour les lignes qui sont à grands angles les unes avec les autres, ce point n'est pas loin du point de connexion interne. Cependant, lorsque les angles entre chaque ligne diminuent, la distance entre ces points augmente exponentiellement.</p>

<p>La propriété <code>miterLimit</code> détermine dans quelle mesure le point de connexion externe peut être placé à partir du point de connexion interne. Si deux lignes dépassent cette valeur, une jointure biseau est dessinée à la place. Notez que la longueur ajoutée maximale est le produit de la largeur de ligne mesurée dans le système de coordonnées actuel, par la valeur de cette propriété <code>miterLimit</code> (dont la valeur par défaut est 10.0 dans le HTML  {{HTMLElement("canvas")}}). <code> </code><code>miterLimit</code> peut être défini indépendamment de l'échelle d'affichage actuelle ou de toutes les transformations affinées de chemins : il n'influence que la forme des bords de lignes effectivement rendues.</p>

<p>Plus précisément, la limite d'onglet est le rapport maximal autorisé de la longueur d'extension (dans le canvas HTML, il est mesuré entre le coin extérieur des bords joints de la ligne et le point d'extrémité commun des segments de connexion spécifiés dans le chemin) à la moitié de la largeur de la ligne. Il peut être défini, de manière équivalente, comme le rapport maximum autorisé de la distance entre les points de jonction intérieur et extérieur des bords et la largeur totale de la ligne. Il est alors égal à la cosécante de la moitié de l'angle interne minimum des segments de connexion, en-dessous de laquelle aucune jointure d'onglet ne sera rendue, mais seulement une jointure en biseau :</p>

<ul>
 <li><code>miterLimit</code> = <strong>max</strong> <code>miterLength</code> / <code>lineWidth</code> = 1 / <strong>sin</strong> ( <strong>min</strong> <em>θ</em> / 2 )</li>
 <li>La limite d'onglet par défaut de 10.0 supprimera tous les onglets pour les angles vifs inférieurs à environ 11 degrés.</li>
 <li>Une limite d'onglet égale à √2 ≈ 1.4142136 (arrondie au-dessus) enlèvera les onglets pour tous les angles aigus, en conservant les joints d'onglet seulement pour les angles obtus ou droits.</li>
 <li>Une limite d'onglet égale à 1.0 est valide mais désactivera tous les onglets.</li>
 <li>Les valeurs inférieures à 1.0 sont invalides pour la limite d'onglet.</li>
</ul>

<p>Voici une petite démo dans laquelle vous pouvez définir dynamiquement <code>miterLimit</code> et voir comment cela affecte les formes sur le canevas. Les lignes bleues indiquent où se trouvent les points de départ et d'arrivée de chacune des lignes du motif en zig-zag.</p>

<p>Si vous spécifiez une valeur <code>miterLimit</code> inférieure à 4.2 dans cette démo, aucun des coins visibles ne se joindra avec une extension onglet, mais seulement avec un petit biseau près des lignes bleues ; avec une limite à onglets au-dessus de 10, la plupart des coins de cette démo devraient se combiner avec un onglet loin des lignes bleues et dont la hauteur diminue entre les coins de gauche à droite, car ils se connectent avec des angles croissants ; avec des valeurs intermédiaires, les coins du côté gauche ne rejoignent qu'un biseau près des lignes bleues et les coins du côté droit avec une extension à onglets (également avec une hauteur décroissante).</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');

  // Éffacer canvas
  ctx.clearRect(0, 0, 150, 150);

  // Dessiner des guides
  ctx.strokeStyle = '#09f';
  ctx.lineWidth   = 2;
  ctx.strokeRect(-5, 50, 160, 50);

  // Définir les styles de lignes
  ctx.strokeStyle = '#000';
  ctx.lineWidth = 10;

  // Vérifier l'entrée (input)
  if (document.getElementById('miterLimit').value.match(/\d+(\.\d+)?/)) {
    ctx.miterLimit = parseFloat(document.getElementById('miterLimit').value);
  } else {
    alert('Value must be a positive number');
  }

  // Dessiner des lignes
  ctx.beginPath();
  ctx.moveTo(0, 100);
  for (i = 0; i &lt; 24 ; i++) {
    var dy = i % 2 == 0 ? 25 : -25;
    ctx.lineTo(Math.pow(i, 1.5) * 2, 75 + dy);
  }
  ctx.stroke();
  return false;
}</pre>

<pre class="brush: html hidden">&lt;table&gt;
  &lt;tr&gt;
    &lt;td&gt;&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;&lt;/td&gt;
    &lt;td&gt;Change the &lt;code&gt;miterLimit&lt;/code&gt; by entering a new value below and clicking the redraw button.&lt;br&gt;&lt;br&gt;
      &lt;form onsubmit="return draw();"&gt;
        &lt;label&gt;Miter limit&lt;/label&gt;
        &lt;input type="text" size="3" id="miterLimit"/&gt;
        &lt;input type="submit" value="Redraw"/&gt;
      &lt;/form&gt;
    &lt;/td&gt;
  &lt;/tr&gt;
&lt;/table&gt;</pre>

<pre class="brush: js hidden">document.getElementById('miterLimit').value = document.getElementById('canvas').getContext('2d').miterLimit;
draw();</pre>

<p>{{EmbedLiveSample("A_demo_of_the_miterLimit_property", "400", "180", "canvas_miterlimit.png")}}</p>

<h3 id="Using_line_dashes">Utilisation de lignes pointillées</h3>

<p><code>setLineDash</code> et <code>lineDashOffset</code> précisent le modèle de lignes. <code>setLineDash</code> accepte une liste de nombres qui spécifie les distances pour dessiner alternativement une ligne et un espace et <code>lineDashOffset</code> définit un décalage pour commencer le motif.</p>

<p>Dans cet exemple, nous créons un effet de fourmis en marche. C'est une technique d'animation souvent employée dans les  sélections d'outils des programmes graphiques. Cet effet permet à l'utilisateur de distinguer la frontière de l'image de fond de la sélection en animant la frontière. Dans une partie de ce tutoriel, vous pouvez apprendre comment faire cela et d'autres animations de base <a href="/fr/docs/Web/API/Canvas_API/Tutorial/Basic_animations">animation basiques.</a><a href="/fr/docs/Tutoriel_canvas/Animations_basiques">.</a></p>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="110" height="110"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js">var ctx = document.getElementById('canvas').getContext('2d');
var offset = 0;

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.setLineDash([4, 2]);
  ctx.lineDashOffset = -offset;
  ctx.strokeRect(10, 10, 100, 100);
}

function march() {
  offset++;
  if (offset &gt; 16) {
    offset = 0;
  }
  draw();
  setTimeout(march, 20);
}

march();</pre>

<p>{{EmbedLiveSample("Using_line_dashes", "120", "120", "marching-ants.png")}}</p>

<h2 id="Gradients">Dégradés</h2>

<p>Comme n'importe quel programme de dessin normal, nous pouvons remplir et découper des formes à l'aide de dégradés linéaires et radiaux. Nous créons un objet {{domxref ("CanvasGradient")}} en utilisant l'une des méthodes suivantes. Nous pouvons ensuite affecter cet objet aux propriétés <code>fillStyle</code> ou <code>strokeStyle</code>.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.createLinearGradient", "createLinearGradient(x1, y1, x2, y2)")}}</dt>
 <dd>Crée un objet dégradé linéaire avec un point de départ (<code>x1</code>, <code>y1</code>) et un point final (<code>x2</code>, <code>y2</code>).</dd>
 <dt>{{domxref("CanvasRenderingContext2D.createRadialGradient", "createRadialGradient(x1, y1, r1, x2, y2, r2)")}}</dt>
 <dd>Crée un dégradé radial. Les paramètres représentent deux cercles, l'un avec son centre à (<code>x1</code>, <code>y1</code>) et un rayon <code>r1</code>, l'autre avec son centre à (<code>x2</code>, <code>y2</code>) avec un rayon <code>r2</code>.</dd>
</dl>

<p>Par exemple:</p>

<pre class="brush: js">var lineargradient = ctx.createLinearGradient(0, 0, 150, 150);
var radialgradient = ctx.createRadialGradient(75, 75, 0, 75, 75, 100);</pre>

<p>Une fois que nous avons créé un objet <code>CanvasGradient</code>, nous pouvons lui assigner des couleurs en utilisant la méthode <code>addColorStop ()</code>.</p>

<dl>
 <dt>{{domxref("CanvasGradient.addColorStop", "gradient.addColorStop(position, color)")}}</dt>
 <dd>Crée un nouvel arrêt de couleur sur l'objet <code>gradient</code> <em>(dégradé)</em>. La position est un nombre entre 0.0 et 1.0 et définit la position relative de la couleur dans le dégradé ; et l'argument <code>color</code> doit être une chaîne représentant une CSS {{cssxref ("&lt;color&gt;")}}, indiquant la couleur que le dégradé devrait atteindre.</dd>
</dl>

<p>Vous pouvez ajouter autant d'arrêts de couleur à un dégradé que vous le souhaitez. Ci-dessous figure un dégradé linéaire très simple du blanc au noir.</p>

<pre class="brush: js">var lineargradient = ctx.createLinearGradient(0, 0, 150, 150);
lineargradient.addColorStop(0, 'white');
lineargradient.addColorStop(1, 'black');</pre>

<h3 id="A_createLinearGradient_example">Un exemple de <code>createLinearGradient</code></h3>

<p>Dans cet exemple, nous allons créer deux dégradés différents. Comme vous pouvez le voir ici, les propriétés <code>strokeStyle</code> et <code>fillStyle</code> peuvent accepter un objet <code>canvasGradient</code> comme entrée valide.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');

  // Créer un dégradé
  var lingrad = ctx.createLinearGradient(0, 0, 0, 150);
  lingrad.addColorStop(0, '#00ABEB');
  lingrad.addColorStop(0.5, '#fff');
  lingrad.addColorStop(0.5, '#26C000');
  lingrad.addColorStop(1, '#fff');

  var lingrad2 = ctx.createLinearGradient(0, 50, 0, 95);
  lingrad2.addColorStop(0.5, '#000');
  lingrad2.addColorStop(1, 'rgba(0, 0, 0, 0)');

  // assigner des dégradés aux styles "fill" et "stroke"
  ctx.fillStyle = lingrad;
  ctx.strokeStyle = lingrad2;

  // Dessiner des formes
  ctx.fillRect(10, 10, 130, 130);
  ctx.strokeRect(50, 50, 50, 50);

}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>
</div>

<p>Le premier est un dégradé d'arrière-plan. Comme vous pouvez le voir, nous avons assigné deux couleurs à la même position. Vous faites cela pour faire des transitions de couleurs très nettes - dans ce cas du blanc au vert. Normalement, peu importe dans quel ordre vous définissez l'arrêt de la couleur, mais dans ce cas particulier, la différence peut être significative. Si vous conservez les affectations dans l'ordre où vous voulez qu'elles apparaissent, cela ne posera aucun problème.</p>

<p>Dans le second gradient, nous n'avons pas assigné la couleur de départ (à la position 0.0) puisqu'il n'était pas strictement nécessaire car il prendra automatiquement la valeur de la prochaine couleur. Par conséquent, l'attribution de la couleur noire à la position 0,5 fait automatiquement passer le dégradé, du début à l'arrêt, en noir.</p>

<p>{{EmbedLiveSample("A_createLinearGradient_example", "180", "180", "canvas_lineargradient.png")}}</p>

<h3 id="A_createRadialGradient_example">Un exemple de <code>createRadialGradient</code></h3>

<p>Dans cet exemple, nous définirons quatre dégradés radiaux différents. Parce que nous avons le contrôle sur les points de départ et de fermeture du dégradé, nous pouvons obtenir des effets plus complexes que nous aurions normalement dans les dégradés radiaux "classiques" (c'est-à-dire un dégradé avec un seul point central où le dégradé se développe vers l'extérieur dans une forme circulaire).</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');

  // Créer un dégradé
  var radgrad = ctx.createRadialGradient(45, 45, 10, 52, 50, 30);
  radgrad.addColorStop(0, '#A7D30C');
  radgrad.addColorStop(0.9, '#019F62');
  radgrad.addColorStop(1, 'rgba(1, 159, 98, 0)');

  var radgrad2 = ctx.createRadialGradient(105, 105, 20, 112, 120, 50);
  radgrad2.addColorStop(0, '#FF5F98');
  radgrad2.addColorStop(0.75, '#FF0188');
  radgrad2.addColorStop(1, 'rgba(255, 1, 136, 0)');

  var radgrad3 = ctx.createRadialGradient(95, 15, 15, 102, 20, 40);
  radgrad3.addColorStop(0, '#00C9FF');
  radgrad3.addColorStop(0.8, '#00B5E2');
  radgrad3.addColorStop(1, 'rgba(0, 201, 255, 0)');

  var radgrad4 = ctx.createRadialGradient(0, 150, 50, 0, 140, 90);
  radgrad4.addColorStop(0, '#F4F201');
  radgrad4.addColorStop(0.8, '#E4C700');
  radgrad4.addColorStop(1, 'rgba(228, 199, 0, 0)');

  // dessiner des formes
  ctx.fillStyle = radgrad4;
  ctx.fillRect(0, 0, 150, 150);
  ctx.fillStyle = radgrad3;
  ctx.fillRect(0, 0, 150, 150);
  ctx.fillStyle = radgrad2;
  ctx.fillRect(0, 0, 150, 150);
  ctx.fillStyle = radgrad;
  ctx.fillRect(0, 0, 150, 150);
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>Dans ce cas, nous avons légèrement décalé le point de départ du point final pour obtenir un effet 3D sphérique. Il est préférable d'éviter de laisser les cercles intérieurs et extérieurs se chevaucher car cela entraîne des effets étranges, difficiles à prédire.</p>

<p>Le dernier arrêt de couleur dans chacun des quatre dégradés utilise une couleur entièrement transparente. Si vous voulez une transition agréable de cette étape à la couleur précédente, les deux couleurs doivent être égales. Ce n'est pas très évident dans le code, car il utilise deux méthodes CSS différentes en démonstration, mais dans le premier dégradé <code># 019F62 = rgba (1,159,98,1)</code>.</p>

<p>{{EmbedLiveSample("A_createRadialGradient_example", "180", "180", "canvas_radialgradient.png")}}</p>

<h2 id="Patterns">Modèles</h2>

<p>Dans l'un des exemples de la page précédente, nous avons utilisé une série de boucles pour créer un motif d'images. Il existe cependant une méthode beaucoup plus simple : la méthode <code>createPattern ()</code>.</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.createPattern", "createPattern(image, type)")}}</dt>
 <dd>Crée et renvoie un nouvel objet de canvas. <code>image</code> est un {{domxref ("CanvasImageSource")}} (c'est-à-dire un {{domxref ("HTMLImageElement")}} ; un autre élément canvas,  <code>type</code>  est une chaîne indiquant comment utiliser l'image.</dd>
</dl>

<p>Le type spécifie comment utiliser l'image pour créer le motif et doit avoir l'une des valeurs de chaîne suivantes :</p>

<dl>
 <dt><code>repeat</code></dt>
 <dd>Tapisse la zone en répètant l'image dans les deux sens vertical et horizontal.</dd>
 <dt><code>repeat-x</code></dt>
 <dd>Tapisse la zone en répètant l'image horizontalement mais pas verticalement.</dd>
 <dt><code>repeat-y</code></dt>
 <dd>Tapisse la zone en répètant l'image verticalement mais pas horizontalement.</dd>
 <dt><code>no-repeat</code></dt>
 <dd>Ne tapisse pas la zone avec l'image, elle est utilisée une seule fois.</dd>
</dl>

<p>Nous utilisons cette méthode pour créer un objet {{domxref ("CanvasPattern")}} qui est très similaire aux méthodes de dégradé que nous avons vu ci-dessus. Une fois que nous avons créé un modèle, nous pouvons l'affecter aux propriétés fillStyle ou strokeStyle. Par exemple :</p>

<pre class="brush: js">var img = new Image();
img.src = 'someimage.png';
var ptrn = ctx.createPattern(img, 'repeat');</pre>

<div class="note">
<p><strong>Note:</strong> Comme avec la méthode <code>drawImage ()</code>, vous devez vous assurer que l'image que vous utilisez est chargée avant d'appeler cette méthode, ou le motif pourrait être mal dessiné.</p>
</div>

<h3 id="A_createPattern_example">Un exemple de <code>createPattern</code></h3>

<p>Dans ce dernier exemple, nous allons créer un modèle à affecter à la propriété <code>fillStyle</code>. La seule chose à noter, est l'utilisation du gestionnaire <code>onload</code> de l'image. Cela permet de s'assurer que l'image est chargée avant d'être affectée au motif.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');

  // créer un nouvel objet image à utiliser comme modèle
  var img = new Image();
  img.src = 'canvas_createpattern.png';
  img.onload = function() {

    // créer le modèle
    var ptrn = ctx.createPattern(img, 'repeat');
    ctx.fillStyle = ptrn;
    ctx.fillRect(0, 0, 150, 150);

  }
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="150"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>Le résultat ressemble à ceci :</p>

<p>{{EmbedLiveSample("A_createPattern_example", "180", "180", "canvas_createpattern.png")}}</p>

<h2 id="Ombres">Ombres</h2>

<p>L'utilisation des ombres ne comporte que quatre propriétés :</p>

<dl>
 <dt>{{domxref("CanvasRenderingContext2D.shadowOffsetX", "shadowOffsetX = float")}}</dt>
 <dd>Indique la distance horizontale sur laquelle l'ombre doit s'étendre à partir de l'objet. Cette valeur n'est pas affectée par la matrice de transformation. La valeur par défaut est 0.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.shadowOffsetY", "shadowOffsetY = float")}}</dt>
 <dd>Indique la distance verticale sur laquelle l'ombre doit s'étendre à partir de l'objet. Cette valeur n'est pas affectée par la matrice de transformation. La valeur par défaut est 0.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur = float")}}</dt>
 <dd>Indique la taille de l'effet de floutage ; cette valeur ne correspond pas à un nombre de pixels et n'est pas affectée par la matrice de transformation actuelle. La valeur par défaut est 0.</dd>
 <dt>{{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor = color")}}</dt>
 <dd>Une valeur de couleur CSS standard indiquant la couleur de l'effet d'ombre ; par défaut, il est entièrement noir transparent.</dd>
</dl>

<p>Les propriétés <code>shadowOffsetX</code> et <code>shadowOffsetY</code> indiquent sur quelle distance l'ombre doit s'étendre à partir de l'objet dans les directions X et Y; ces valeurs ne sont pas affectées par la matrice de transformation actuelle. Utilisez des valeurs négatives pour faire en sorte que l'ombre s'étende vers le haut ou vers la gauche et des valeurs positives pour que l'ombre s'étende vers le bas ou vers la droite. La valeur par défaut est 0 pour les 2 propriétés.</p>

<p>La propriété <code>shadowBlur</code> indique la taille de l'effet de flou ; cette valeur ne correspond pas à un nombre de pixels et n'est pas affectée par la matrice de transformation actuelle. La valeur par défaut est 0.</p>

<p>La propriété <code>shadowColor</code> est une valeur de couleur CSS standard indiquant la couleur de l'effet d'ombre ; par défaut, il est entièrement en noir transparent.</p>

<div class="note">
<p><strong>Note :</strong> Les ombres ne sont dessinées que pour les <a href="/fr/docs/Web/API/Canvas_API/Tutorial/Compositing">opérations de composition</a> <code>source-over</code>.</p>
</div>

<h3 id="A_shadowed_text_example">Un exemple de texte ombré</h3>

<p>Cet exemple dessine une chaîne de texte avec un effet d'ombrage.</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');

  ctx.shadowOffsetX = 2;
  ctx.shadowOffsetY = 2;
  ctx.shadowBlur = 2;
  ctx.shadowColor = 'rgba(0, 0, 0, 0.5)';

  ctx.font = '20px Times New Roman';
  ctx.fillStyle = 'Black';
  ctx.fillText('Sample String', 5, 30);
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="150" height="80"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>

<p>{{EmbedLiveSample("A_shadowed_text_example", "180", "100", "shadowed-string.png")}}</p>

<p>Nous allons regarder la propriété de la  <code>font</code> <em>(police de caratères)</em> et la méthode <code>fillText</code> dans le chapitre suivant sur le <a href="/fr/docs/Dessin_de_texte_avec_canvas">dessin de texte</a>.</p>

<h2 id="Canvas_fill_rules">Règles de remplissage Canvas</h2>

<p>Lors de l'utilisation de <code>fill</code> (ou {{domxref ("CanvasRenderingContext2D.clip", "clip")}} et  {{domxref("CanvasRenderingContext2D.isPointInPath", "isPointinPath")}}) ,  déterminez si un point est à l'intérieur ou à l'extérieur d'un chemin et ainsi, s'il est rempli ou non. Ceci est utile lorsqu'un chemin en croise  un autre ou est imbriqué.<br>
 <br>
 Deux valeurs sont possibles :</p>

<ul>
 <li><code><strong>"nonzero</strong></code>": la <a href="http://en.wikipedia.org/wiki/Nonzero-rule">règle non-zero</a>, qui est la règle par défaut.</li>
 <li><code><strong>"evenodd"</strong></code>: La <a href="http://en.wikipedia.org/wiki/Even%E2%80%93odd_rule">règle even-odd</a>.</li>
</ul>

<p>Dans cet exemple, nous utilisons la règle <code>evenodd</code> .</p>

<pre class="brush: js">function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  ctx.beginPath();
  ctx.arc(50, 50, 30, 0, Math.PI * 2, true);
  ctx.arc(50, 50, 15, 0, Math.PI * 2, true);
  ctx.fill('evenodd');
}</pre>

<pre class="brush: html hidden">&lt;canvas id="canvas" width="100" height="100"&gt;&lt;/canvas&gt;</pre>

<pre class="brush: js hidden">draw();</pre>
</div>

<p>{{EmbedLiveSample("Canvas_fill_rules", "110", "110", "fill-rule.png")}}</p>

<p>{{PreviousNext("Tutoriel_canvas/Formes_géométriques", "Dessin_de_texte_avec_canvas")}}</p>
