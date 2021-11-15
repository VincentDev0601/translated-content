---
title: La construction d'objet en pratique
slug: Learn/JavaScript/Objects/Object_building_practice
tags:
  - Apprendre
  - Article
  - Canvas
  - Débutant
  - JavaScript
  - Manuel
  - Objets
  - Tutoriel
translation_of: Learn/JavaScript/Objects/Object_building_practice
original_slug: Learn/JavaScript/Objects/la_construction_d_objet_en_pratique
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenuNext("Learn/JavaScript/Objects/JSON", "Learn/JavaScript/Objects/Adding_bouncing_balls_features", "Learn/JavaScript/Objects")}}</div>

<p>Dans l'article précédent, nous avons passé en revue l'essentiel de la théorie de l'objet Javascript et sa syntaxe détaillée, vous donnant ainsi des bases solides sur lesquelles commencer. Dans le présent article nous plongeons dans un exercice pratique afin d'accroître votre savoir-faire dans la construction d'objets entièrement personnalisés donnant un résultat plutôt amusant et très coloré.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Pré-requis :</th>
   <td>
    <p>Connaissance basique de l'informatique, une compréhension basique du HTML et du CSS, une familiarité avec  les bases du JavaScript (voir <a href="/fr/docs/Learn/JavaScript/First_steps">Premiers pas</a> et <a href="/fr/docs/Learn/JavaScript/Building_blocks">Les blocs de construction</a>) et les bases de la programmation objet en JavaScript (voir <a href="/fr/docs/Learn/JavaScript/Object-oriented/Introduction">Introduction aux objets</a>). </p>
   </td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>
    <p>Acquérir plus de pratique dans l'utilisation des objets et des techniques orientées objet dans un contexte "monde réel".</p>
   </td>
  </tr>
 </tbody>
</table>

<h2 id="Faisons_bondir_quelques_balles">Faisons bondir quelques balles</h2>

<p>Dans cet article, nous écrirons une démo classique de "balles bondissantes", pour vous montrer à quel point les objets peuvent être utiles en JavaScript. Nos petites balles bondiront partout sur notre écran et changeront de couleurs lorsqu'elles se toucheront. L'exemple finalisé ressemblera un peu à ceci : </p>

<p><img alt="" src="bouncing-balls.png"></p>

<ol>
</ol>

<p>Cet exemple utilise l'<a href="/fr/docs/Learn/JavaScript/Client-side_web_APIs/Drawing_graphics">API Canvas </a> pour dessiner les balles sur l'écran, et l'API <a href="/fr/docs/Web/API/window/requestAnimationFrame">requestAnimationFrame</a>  pour animer l'ensemble de l'affichage — Nul besoin d'avoir une connaissance préalable de ces APIs, nous expérons qu'une fois cet article terminé, vous aurez envie d'en faire une exploration approfondie. Tout le long du parcours nous utiliserons certains objets formidables et vous montrerons nombre de techniques sympathiques comme des balles bondissantes sur les murs et la vérification de balles qui s'entrechoquent (encore connue sous l'appelation <strong>détection de collision</strong>).</p>

<p>Pour commencer, faites des copies locales de nos fichiers <code><a href="https://github.com/mdn/learning-area/blob/master/javascript/oojs/bouncing-balls/index.html">index.html</a></code>, <code><a href="https://github.com/mdn/learning-area/blob/master/javascript/oojs/bouncing-balls/style.css">style.css</a></code>, et <code><a href="https://github.com/mdn/learning-area/blob/master/javascript/oojs/bouncing-balls/main.js">main.js</a></code>. Ces fichiers contiennent respectivement :</p>

<ol>
 <li>Un document  HTML très simple contenant un élément {{HTMLElement("h1")}} , un élément {{HTMLElement("canvas")}} pour dessiner nos balles dessus et des élements  pour appliquer notre CSS et notre JavaScript à notre HTML ;</li>
 <li>Quelques styles très simples qui servent principalement à mettre en forme et placer le <code>&lt;h1&gt;</code>, et se débarasser de toutes barres de défilement ou de marges autour du pourtour de notre page (afin que cela paraisse plus sympathique et élégant) ;</li>
 <li>Un peu de JavaScript qui sert à paramétrer l'élément  <code>&lt;canvas&gt;</code> et fournir les fonctions globalles que nous utiliserons.</li>
</ol>

<p>La première partie du script ressemble à ceci :</p>

<pre class="brush: js">const canvas = document.querySelector('canvas');

const ctx = canvas.getContext('2d');

const width = canvas.width = window.innerWidth;
const height = canvas.height = window.innerHeight;</pre>

<p>Ce script prend une référence à l'élément  <code>&lt;canvas&gt;</code> et ensuite invoque la méthode  <code><a href="/fr/docs/Web/API/HTMLCanvasElement/getContext">getContext()</a></code> sur lui, nous donnant ainsi un contexte sur lequel nous pouvons commencer à dessiner. La variable résultante  (<code>ctx</code>)  est l'objet qui représente directement la surface du Canvas où nous pouvons dessiner et qui nous permet de dessiner des formes 2D sur ce dernier. </p>

<p>Après, nous configurons  les variables <code>width</code> (largeur) et <code>height</code>(hauteur),  et la largeur et la hauteur de l'élément canvas (représentés par les propriétés  <code>canvas.width</code> et <code>canvas.height</code> ) afin qu'elles soient identiques à la fenêtre du navigateur (la surface sur laquelle apparaît la page web— Ceci peut être tiré des propriétés {{domxref("Window.innerWidth")}} et {{domxref("Window.innerHeight")}}).</p>

<p>Vous verrez qu'ici nous enchaînons les assignations des valeurs des différentes variables ensemble à des fins de rapidité. Ceci est parfaitement autorisé.</p>

<p>Le dernier morceau du script ressemble à ceci :</p>

<pre class="brush: js">function random(min, max) {
  var num = Math.floor(Math.random() * (max - min + 1)) + min;
  return num;
}</pre>

<p>Cette fonction prend deux nombres comme arguments, et renvoie un nombre compris entre les deux. </p>

<h2 id="Modéliser_une_balle_dans_notre_programme">Modéliser une balle dans notre programme</h2>

<p>Notre programme met en œuvre beaucoup de balles bondissant partout sur l'écran. Comme nos balles se comporteront toutes de la même façon, cela semble tout à fait sensé de les représenter avec un objet. Commençons donc en ajoutant le constructeur suivant à la fin de notre code.</p>

<pre class="brush: js">function Ball(x, y, velX, velY, color, size) {
  this.x = x;
  this.y = y;
  this.velX = velX;
  this.velY = velY;
  this.color = color;
  this.size = size;
}</pre>

<p>Ici, nous incluons des paramètres qui définissent  des propriétés dont chaque balle aura besoin pour fonctionner dans notre programme :</p>

<ul>
 <li>Les coordonnées <code>x</code> et <code>y</code>  — les coordonnées verticales et horizontales où la balle débutera sur l'écran. Ceci peut se trouver entre 0 (coin à gauche en haut) et la valeur de la hauteur et de la largeur de la fenêtre du navigateur (coin en bas à droite).</li>
 <li>Une vitesse horizontale et verticale (<code>velX</code> et <code>velY</code>) — à chaque balle est attribuée une vitesse horizontale et verticale; en termes réels ces valeurs seront régulièrement ajoutéés aux valeurs de la coordonnée <code>x</code>/<code>y</code> quand nous commencerons à animer les balles, afin de les faire bouger d'autant sur chaque vignette (frame).</li>
 <li><code>color</code> — chaque balle a une couleur.</li>
 <li><code>size</code> — chaque balle a une taille — ce sera son rayon mesuré en pixels.</li>
</ul>

<p>Ceci règle le problème des propriétés mais qu'en est il des méthodes ? Nous voulons maintenant amener nos balles à faire quelque chose dans notre programme.</p>

<h3 id="Dessiner_la_balle">Dessiner la balle</h3>

<p>En premier lieu ajoutez la méthode <code>draw()</code> au <code>prototype</code> de <code>Ball()</code> :</p>

<pre class="brush: js">Ball.prototype.draw = function() {
  ctx.beginPath();
  ctx.fillStyle = this.color;
  ctx.arc(this.x, this.y, this.size, 0, 2 * Math.PI);
  ctx.fill();
}</pre>

<p>En utilisant cette fonction, nous pouvons dire à notre balle de se dessiner sur l'écran en appelant une série de membres du contexte 2D du canvas que nous avons défini plus tôt  (<code>ctx</code>). Le contexte est comme le papier et maintenant nous allons demander à notre stylo d'y dessiner quelque chose :</p>

<ul>
 <li>Premièrement, nous utilisons <code><a href="/fr/docs/Web/API/CanvasRenderingContext2D/beginPath">beginPath()</a></code> pour spécifier que nous voulons dessiner une forme sur le papier.</li>
 <li>Ensuite, nous utilisons <code><a href="/fr/docs/Web/API/CanvasRenderingContext2D/fillStyle">fillStyle</a></code> pour définir de quelle couleur nous voulons que la forme soit — nous lui attribuons la valeur de la propriété <code>color</code> de notre balle.</li>
 <li>Après, nous utilisons la méthode <code><a href="/fr/docs/Web/API/CanvasRenderingContext2D/arc">arc()</a></code> pour tracer une forme en arc sur le papier. Ses paramètres sont :
  <ul>
   <li>Les positions <code>x</code> et <code>y</code> du centre de l'arc — nous specifions donc les propriétés <code>x</code> et <code>y </code>de notre balle.</li>
   <li>Le rayon de l'arc — nous specifions la propriété <code>size</code> de notre balle.</li>
   <li>Les deux derniers paramètres spécifient l'intervalle de début et de fin en degrés pour dessiner l'arc. Ici nous avons spécifié 0 degrés et <code>2 * PI </code>qui est l'équivalent de 360 degrés en radians (malheureusement  vous êtes obligés  de spécifier ces valeurs en radians et non en degrés). Cela nous donne un cercle complet. Si vous aviez spécifié seulement  <code>1 * PI</code>, vous auriez eu un demi-cercle (180 degrés).</li>
  </ul>
 </li>
 <li>En dernière position nous utilisons la méthode <code><a href="/fr/docs/Web/API/CanvasRenderingContext2D/fill">fill()</a></code> qui est habituellement utilisée pour spécifier que nous souhaitons mettre fin au dessin que nous avons commencé avec <code>beginPath()</code>, et remplir la surface délimitée avec la couleur que nous avions spécifiée plus tôt avec <code>fillStyle</code>.</li>
</ul>

<p>Vous pouvez déjà commencer à tester votre objet.</p>

<ol>
 <li>Sauvegardez le code et chargez le fichier html dans un navigateur.</li>
 <li>Ouvrez la console JavaScript du navigateur et actualisez la page afin que la taille du canvas change et prenne la petite taille restante de la fenêtre lorsque la console est ouverte.</li>
 <li>Tapez dans la console ce qui suit afin de créer une nouvelle instance de balle :
  <pre class="brush: js">let testBall = new Ball(50, 100, 4, 4, 'blue', 10);</pre>
 </li>
 <li>Essayez d'appeler ses membres :
  <pre class="brush: js">testBall.x
testBall.size
testBall.color
testBall.draw()</pre>
 </li>
 <li>Lorsque vous entrerez la dernière ligne, vous devriez voir la balle se dessiner quelque part sur votre canvas.</li>
</ol>

<h3 id="Mettre_à_jour_les_données_de_la_balle">Mettre à jour les données de la balle</h3>

<p>Nous pouvons dessiner la balle dans n'importe quelle position, mais actuellement pour commencer à la bouger nous aurons besoin d'une sorte de fonction de mise à jour. Insérez donc le code suivant à la fin de votre fichier JavaScript pour ajouter une méthode <code>update()</code> au <code>prototype</code> de <code>Ball()</code>:</p>

<pre class="brush: js">Ball.prototype.update = function() {
  if ((this.x + this.size) &gt;= width) {
    this.velX = -(this.velX);
  }

  if ((this.x - this.size) &lt;= 0) {
    this.velX = -(this.velX);
  }

  if ((this.y + this.size) &gt;= height) {
    this.velY = -(this.velY);
  }

  if ((this.y - this.size) &lt;= 0) {
    this.velY = -(this.velY);
  }

  this.x += this.velX;
  this.y += this.velY;
}</pre>

<p>Les quatre premières parties de la fonction vérifient si la balle a atteint le rebord  du canvas. Si c'est le cas, nous inversons la polarité de la vitesse appropriée pour faire bouger la balle dans le sens opposé. Donc par exemple, si la balle se déplaçait vers le haut (positif <code>velY</code>) alors la vitesse verticale est changée afin qu'elle commence à bouger plutôt vers le bas (negatif <code>velY</code>).</p>

<p>Dans les quatre cas nous :</p>

<ul>
 <li>Verifions si la coordonnée <code>x</code> est plus grande que la largeur du canvas (la balle est en train de sortir du côté droit).</li>
 <li>Verifions si la coordonnée <code>x</code> est plus petite que 0 (la balle est en train de sortir du côté gauche).</li>
 <li>Verifions si la coordonnée <code>y</code> est plus grande que la hauteur du canvas (la balle est en train de sortir par le bas).</li>
 <li>Verifions si la coordonnée <code>y</code> est plus petite que 0 (la balle est en train de sortir par le  haut).</li>
</ul>

<p>Dans chaque cas, nous incluons la taille <code>size</code> de la balle dans les calculs parce que les coordonnées  <code>x</code>/<code>y</code>  sont situées au centre de la balle mais nous voulons que le pourtour de la balle rebondisse sur le rebord  — nous ne voulons pas que la balle sorte à moité hors de l'écran avant de commencer à rebondir vers l'arrière.</p>

<p>Les deux dernières lignes ajoutent la valeur <code>velX</code> à la coordonnée <code>x</code> et la valeur <code>velY</code> à la coordonnée <code>y</code> — la balle est en effet mise en mouvement chaque fois que cette méthode est invoquée.</p>

<p>Cela suffira pour l'instant, passons à l'animation !</p>

<h2 id="Animer_la_balle">Animer la balle</h2>

<p>Maintenant, rendons cela amusant. Nous allons commencer à ajouter des balles au canvas et à les animer.</p>

<ol>
 <li>Tout d'abord, nous avons besoin d'un endroit où stocker toutes nos balles. Le tableau suivant fera ce travail — ajoutez-le au bas de votre code maintenant :

  <pre class="brush: js">let balls = [];
</pre>

  <pre>while (balls.length &lt; 25) {
  let size = random(10,20);
  let ball = new Ball(
    // ball position always drawn at least one ball width
    // away from the edge of the canvas, to avoid drawing errors
    random(0 + size,width - size),
    random(0 + size,height - size),
    random(-7,7),
    random(-7,7),
    'rgb(' + random(0,255) + ',' + random(0,255) + ',' + random(0,255) +')',
    size
  );

  balls.push(ball);
}</pre>
  Tous les programmes qui animent les choses impliquent généralement une boucle d'animation, qui sert à mettre à jour les informations dans le programme et à restituer ensuite la vue résultante sur chaque image de l'animation. C'est la base de la plupart des jeux et autres programmes similaires.</li>
 <li>Ajoutez ce qui suit au bas de votre code maintenant :
  <pre class="brush: js">function loop() {
  ctx.fillStyle = 'rgba(0, 0, 0, 0.25)';
  ctx.fillRect(0, 0, width, height);

  for (let i = 0; i &lt; balls.length; i++) {
    balls[i].draw();
    balls[i].update();
  }

  requestAnimationFrame(loop);
}</pre>

  <p>Notre fonction <code>loop()</code> fonctionne comme suit :</p>

  <ul>
   <li>On définit la couleur de remplissage du canvas en noir semi-transparent, puis dessine un rectangle de couleur sur toute la largeur et la hauteur du canvas, en utilisant <code>fillRect()</code> (les quatre paramètres fournissent une coordonnée de départ et une largeur et une hauteur pour le rectangle dessiné ). Cela sert à masquer le dessin de l'image précédente avant que la suivante ne soit dessinée. Si vous ne faites pas cela, vous verrez juste de longs serpents se faufiler autour de la toile au lieu de balles qui bougent ! La couleur du remplissage est définie sur semi-transparent, <code>rgba (0,0,0,.25)</code>, pour permettre aux quelques images précédentes de briller légèrement, produisant les petites traînées derrière les balles lorsqu'elles se déplacent. Si vous avez changé 0.25 à 1, vous ne les verrez plus du tout. Essayez de faire varier ce dernier nombre (entre 0 et 1) pour voir l'effet qu'il a.</li>
   <li>On crée un nouvel objet <code>Ball()</code> avec des attributs générées aléatoirement grâce à la fonction <code>random()</code>, puis on ajoute l'objet au tableau, mais seulement lorsque le nombre de balles dans le tableau est inférieur à 25. Donc quand on a 25 balles à l'écran, plus aucune balle supplémentaire n'apparaît. Vous pouvez essayer de faire varier le nombre dans <code>balls.length &lt;25</code> pour obtenir plus, ou moins de balles à l'écran. En fonction de la puissance de traitement de votre ordinateur / navigateur, spécifier plusieurs milliers de boules peut ralentir l'animation de façon très significative !</li>
   <li>Le programme boucle à travers tous les objets du tableau sur chacun desquels il exécute la fonction <code>draw()</code> et <code>update()</code> pour dessiner à l'écran chaque balle et faire les mise à jour de chaque attribut vant le prochain rafraîchissement.</li>
   <li>Exécute à nouveau la fonction à l'aide de la méthode <code>requestAnimationFrame()</code> — lorsque cette méthode est exécutée en permanence et a reçu le même nom de fonction, elle exécute cette fonction un nombre défini de fois par seconde pour créer une animation fluide. Cela se fait généralement de manière récursive — ce qui signifie que la fonction s'appelle elle-même à chaque fois qu'elle s'exécute, de sorte qu'elle sera répétée encore et encore.</li>
  </ul>
 </li>
 <li>Finallement mais non moins important, ajoutez la ligne suivante au bas de votre code — nous devons appeler la fonction une fois pour démarrer l'animation.
  <pre class="brush: js">loop();</pre>
 </li>
</ol>

<p>Voilà pour les bases — essayez d'enregistrer et de rafraîchir pour tester vos balles bondissantes!</p>

<h2 id="Ajouter_la_détection_de_collision">Ajouter la détection de collision</h2>

<p>Maintenant, pour un peu de plaisir, ajoutons une détection de collision à notre programme, afin que nos balles sachent quand elles ont frappé une autre balle.</p>

<ol>
 <li>Tout d'abord, ajoutez la définition de méthode suivante ci-dessous où vous avez défini la méthode <code>update()</code> (c'est-à-dire le bloc <code>Ball.prototype.update</code>).

  <pre class="brush: js">Ball.prototype.collisionDetect = function() {
  for (let j = 0; j &lt; balls.length; j++) {
    if (!(this === balls[j])) {
      const dx = this.x - balls[j].x;
      const dy = this.y - balls[j].y;
      const distance = Math.sqrt(dx * dx + dy * dy);

      if (distance &lt; this.size + balls[j].size) {
        balls[j].color = this.color = 'rgb(' + random(0, 255) + ',' + random(0, 255) + ',' + random(0, 255) +')';
      }
    }
  }
}</pre>

  <p>Cette méthode est un peu complexe, donc ne vous inquiétez pas si vous ne comprenez pas exactement comment cela fonctionne pour le moment. Regardons cela pas-à-pas :</p>

  <ul>
   <li>Pour chaque balle <em>b</em>, nous devons vérifier chaque autre balle pour voir si elle est entrée en collision avec <em>b</em>. Pour ce faire, on inspecte toutes les balles du tableau <code>balls[]</code> dans une boucle <code>for</code>.</li>
   <li>Immédiatement à l'intérieur de cette boucle <code>for</code>, une instruction <code>if</code> vérifie si la balle courante  <em>b'</em> , inspectée dans la boucle, n'est égale à la balle <em>b. Le code correspondant est :  </em><code><em>b</em>'!== <em>b</em></code><em>. </em>En effet, nous ne voulons pas vérifier si une balle <em>b</em> est entrée en collision avec elle-même ! Nous contrôlons donc si la balle actuelle <em>b</em>—dont la méthode <code>collisionDetect()</code> est invoquée—est distincte de la balle <em>b' </em>inspectée dans la boucle<em>. </em>Ainsi le bloc de code venant après l'instruction <code>if</code> ne s'exécutera que si les balles <em>b</em> et <em>b'</em> ne sont pas identiques.</li>
   <li>Un algorithme classique permet ensuite de vérifier la superposition de deux disques. Ceci est expliqué plus loin dans <a href="/fr/docs/Games/Techniques/2D_collision_detection">2D collision detection</a>.</li>
   <li>Si une collision est détectée, le code à l'intérieur de l'instruction interne <code>if</code> est exécuté. Dans ce cas, nous définissons simplement la propriété <code>color</code> des deux cercles à une nouvelle couleur aléatoire. Nous aurions pu faire quelque chose de bien plus complexe, comme faire rebondir les balles de façon réaliste, mais cela aurait été beaucoup plus complexe à mettre en œuvre. Pour de telles simulations de physique, les développeurs ont tendance à utiliser des bibliothèques de jeux ou de physiques telles que <a href="http://wellcaffeinated.net/PhysicsJS/">PhysicsJS</a>, <a href="http://brm.io/matter-js/">matter.js</a>, <a href="http://phaser.io/">Phaser</a>, etc.</li>
  </ul>
 </li>
 <li>Vous devez également appeler cette méthode dans chaque image de l'animation. Ajouter le code ci-dessous  juste après la ligne <code>balls[i].update();</code>:
  <pre class="brush: js">balls[i].collisionDetect();</pre>
 </li>
 <li>Enregistrez et rafraîchissez la démo à nouveau, et vous verrez vos balles changer de couleur quand elles entrent en collision !</li>
</ol>

<div class="note">
<p><strong>Note :</strong> Si vous avez des difficultés à faire fonctionner cet exemple, essayez de comparer votre code JavaScript avec notre <a href="https://github.com/mdn/learning-area/blob/master/javascript/oojs/bouncing-balls/main-finished.js">version finale</a> (voir également la <a href="http://mdn.github.io/learning-area/javascript/oojs/bouncing-balls/index-finished.html">démo en ligne</a>).</p>
</div>

<h2 id="Résumé">Résumé</h2>

<p>Nous espérons que vous vous êtes amusé à écrire votre propre exemple de balles aléatoires bondissantes comme dans le monde réel, en utilisant diverses techniques orientées objet et divers objets d'un bout à l'autre du module ! Nous espérons vous avoir offert un aperçu utile de l'utilisation des objets.</p>

<p>C'est tout pour les articles sur les objets — il ne vous reste plus qu'à tester vos compétences dans l'évaluation sur les objets.</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/API/Canvas_API/Tutorial">Didacticiel sur canvas</a> — un guide pour débutants sur l'utilisation de canvas 2D.</li>
 <li><a href="/fr/docs/Web/API/window/requestAnimationFrame">requestAnimationFrame()</a></li>
 <li><a href="/fr/docs/Games/Techniques/2D_collision_detection">Détection de collision 2D</a> </li>
 <li><a href="/fr/docs/Games/Techniques/3D_collision_detection">Détection de collision 3D</a> </li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript">Jeu d'évasion 2D utilisant du JavaScript pu</a> —un excellent tutoriel pour débutant montrant comment construire un jeu en 2D.</li>
 <li><a href="/fr/docs/Games/Tutorials/2D_breakout_game_Phaser">Jeu d'évasion 2D utilisant phaser</a> — explique les bases de la construction d'un jeu 2D en utilisant une bibliothèque de jeux JavaScript.</li>
</ul>

<p>{{PreviousMenuNext("Learn/JavaScript/Objects/JSON", "Learn/JavaScript/Objects/Adding_bouncing_balls_features", "Learn/JavaScript/Objects")}}</p>



<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Learn/JavaScript/Objects/Basics">Les bases de l'objet</a></li>
 <li><a href="/fr/docs/Learn/JavaScript/Objects/Object-oriented_JS">JavaScript orienté objet pour les débutants</a></li>
 <li><a href="/fr/docs/Learn/JavaScript/Objects/Object_prototypes">Prototypes d'objets</a></li>
 <li><a href="/fr/docs/Learn/JavaScript/Objects/Inheritance">Héritage en JavaScript</a></li>
 <li><a href="/fr/docs/Learn/JavaScript/Objects/JSON">Travailler avec des données JSON</a></li>
 <li><a href="/fr/docs/Learn/JavaScript/Objects/Object_building_practice">Pratique de construction d'objets</a></li>
 <li><a href="/fr/docs/Learn/JavaScript/Objects/Adding_bouncing_balls_features">Ajout de fonctionnalités à notre démo de balles bondissantes</a></li>
</ul>
