---
title: Raquette et contrôle clavier
slug: Games/Tutorials/2D_Breakout_game_pure_JavaScript/Paddle_and_keyboard_controls
tags:
  - Canvas
  - Clavier
  - Débutant
  - JavaScript
  - Jeux
  - Tuto
  - Tutoriel
  - contrôle clavier
  - graphique
translation_of: Games/Tutorials/2D_Breakout_game_pure_JavaScript/Paddle_and_keyboard_controls
original_slug: Games/Workflows/2D_Breakout_game_pure_JavaScript/Paddle_et_contrôle_clavier
---
<div>{{GamesSidebar}}</div>

<div>{{IncludeSubnav("/fr/docs/Games")}}</div>

<p>{{PreviousNext("Games/Workflows/2D_Breakout_game_pure_JavaScript/Faire_rebondir_la_balle_sur_les_murs", "Games/Workflows/2D_Breakout_game_pure_JavaScript/Game_over")}}</p>

<p>C'est la <strong>4<sup>e</sup> étape sur</strong> 10 de ce <a href="/fr/docs/Games/Workflows/2D_Breakout_game_pure_JavaScript">tutoriel Gamedev Canvas</a>. Vous pouvez retrouver le code source de cette leçon sur <a class="external external-icon" href="https://github.com/end3r/Gamedev-Canvas-workshop/blob/gh-pages/lesson04.html" rel="noopener">Gamedev-Canvas-workshop/lesson4.html</a>.</p>

<p>La balle rebondit librement partout et vous pourriez la regarder indéfiniment... Mais il n'y a pas d'interaction avec le joueur. Ce n'est pas un jeu si vous ne pouvez pas le contrôler ! Nous allons donc ajouter une interaction avec le joueur : une raquette contrôlable.</p>

<h2 id="Créer_une_raquette_pour_frapper_la_balle">Créer une raquette pour frapper la balle</h2>

<p>Il nous faut donc une raquette pour frapper la balle. Définissons quelques variables pour cela. Ajoutez les variables suivantes en haut de votre code, près de vos autres variables :</p>

<pre class="brush: js">var paddleHeight = 10;
var paddleWidth = 75;
var paddleX = (canvas.width-paddleWidth)/2;</pre>

<p>Ici, nous définissons la hauteur et la largeur de la raquette et son point de départ sur l'axe des x pour l'utiliser dans les calculs plus loin dans le code. Créons une fonction qui dessinera la raquette sur l'écran. Ajoutez ce qui suit juste en dessous de votre fonction <code>drawBall()</code> :</p>

<pre class="brush: js">function drawPaddle() {
    ctx.beginPath();
    ctx.rect(paddleX, canvas.height-paddleHeight, paddleWidth, paddleHeight);
    ctx.fillStyle = "#0095DD";
    ctx.fill();
    ctx.closePath();
}</pre>

<h2 id="Permettre_à_lutilisateur_de_contrôler_la_raquette">Permettre à l'utilisateur de contrôler la raquette</h2>

<p>Nous pouvons dessiner la raquette où nous voulons, mais elle doit répondre aux actions de l'utilisateur. Il est temps de mettre en place certaines commandes au clavier. Nous aurons besoin de ce qui suit :<br>
  </p>

<ul>
 <li>Deux variables pour stocker des informations sur l'état des touches "gauche" et "droite".</li>
 <li>Deux écouteurs d'événements pour les événements <code>keydown</code> et <code>keyup</code> du clavier. Nous voulons exécuter un code pour gérer le mouvement de la raquette lorsque des appuis sur les touches.</li>
 <li>Deux fonctions gérant les événements <code>keydown</code> et <code>keyup</code> et le code qui sera exécuté lorsque les touches sont pressées.</li>
 <li>La possibilité de déplacer la raquette vers la gauche et vers la droite</li>
</ul>

<p>L'état des touches peut être mémorisé dans des variables booléennes comme dans l'exemple ci-dessous. Ajoutez ces lignes près de vos variables :</p>

<pre class="brush: js">var rightPressed = false;
var leftPressed = false;</pre>

<p>La valeur par défaut pour les deux est fausse car au début, car les touches ne sont pas enfoncés. Pour être informé des appuis sur les touches, nous allons mettre en place deux écouteurs d'événements. Ajoutez les lignes suivantes juste au-dessus de la ligne setInterval() au bas de votre JavaScript :</p>

<pre class="brush: js">document.addEventListener("keydown", keyDownHandler, false);
document.addEventListener("keyup", keyUpHandler, false);</pre>

<p>Lorsque l'événement <code>keydown</code> est déclenché par l'appui d'une des touches de votre clavier (lorsqu'elles sont enfoncées), la fonction <code>keyDownHandler()</code> est exécutée. Le même principe est vrai pour le deuxième écouteur : les événements <code>keyup</code> activent la fonction <code>keyUpHandler()</code> (lorsque les touches cessent d'être enfoncées). Ajoutez ces lignes à votre code, sous les lignes <code>addEventListener()</code> :</p>

<pre class="brush: js">function keyDownHandler(e) {
    if(e.key == "Right" || e.key == "ArrowRight") {
        rightPressed = true;
    }
    else if(e.key == "Left" || e.key == "ArrowLeft") {
        leftPressed = true;
    }
}

function keyUpHandler(e) {
    if(e.key == "Right" || e.key == "ArrowRight") {
        rightPressed = false;
    }
    else if(e.key == "Left" || e.key == "ArrowLeft") {
        leftPressed = false;
    }
}</pre>

<p>Quand on presse une touche du clavier, l'information est stockée dans une variable. La variable concernée est mis sur <code>true</code>. Quand la touche est relachée, la variable revient à  <code>false</code>.</p>

<p>Les deux fonctions prennent un événement comme paramètre, représenté par la variable <code>e</code>. De là, vous pouvez obtenir des informations utiles : la propriété <code>key</code> contient les informations sur la touche qui a été enfoncée.  La plupart des navigateurs utilisent <code>ArrowRight</code> et <code>ArrowLeft</code> pour les touches de flèche gauche/droite, mais nous devons également tester <code>Right</code> and <code>Left</code> pour prendre en charge les navigateurs IE/Edge. Si la touche gauche est enfoncé, la variable <code>leftPressed</code> est mise à <code>true</code>, et lorsqu'elle est relâchée, la variable <code>leftPressed</code> est mise à <code>false</code>. Le même principe s'applique à la touche droite et à la variable <code>RightPressed</code>.</p>

<h3 id="La_logique_du_déplacement_de_la_raquette">La logique du déplacement de la raquette</h3>

<p>Nous avons maintenant mis en place les variables pour stocker les informations sur les touches pressées, les écouteurs d'événements et les fonctions associées. Ensuite, nous allons entrer dans le code pour utiliser tout ce que nous venons de configurer et pour déplacer la palette à l'écran. Dans la fonction <code>draw()</code>, nous vérifierons si les touches gauche ou droite sont pressées lors du rendu de chaque image. Notre code pourrait ressembler à ceci :</p>

<pre class="brush: js">if(rightPressed) {
    paddleX += 7;
}
else if(leftPressed) {
    paddleX -= 7;
}</pre>

<p>Si la touche gauche est enfoncée, la raquette se déplacera de sept pixels vers la gauche, et si la droite est enfoncé, la raquette se déplacera de sept pixels vers la droite. Cela fonctionne actuellement, mais la raquette disparaît du bord du canevas si nous maintenons l'une ou l'autre des touches trop longtemps enfoncée. Nous pourrions améliorer cela et déplacer la raquette uniquement dans les limites du canevas en changeant le code comme ceci :</p>

<pre class="brush: js">if(rightPressed) {
    paddleX += 7;
    if (paddleX + paddleWidth &gt; canvas.width){
        paddleX = canvas.width - paddleWidth;
    }
}
else if(leftPressed) {
    paddleX -= 7;
    if (paddleX &lt; 0){
        paddleX = 0;
    }
}</pre>

<p>La position de <code>paddleX</code> que nous utilisons variera entre <code>0</code> sur le côté gauche du canevas et <code>canvas.width-paddleWidth</code> sur le côté droit, ce qui fonctionnera exactement comme nous le souhaitons.<br>
 <br>
 Ajoutez le bloc de code ci-dessus dans la fonction <code>draw()</code> en bas, juste au-dessus de l'accolade de fermeture.<br>
 <br>
 Il ne reste plus qu'à appeler la fonction <code>drawPaddle()</code> depuis la fonction <code>draw()</code>, pour l'afficher réellement à l'écran. Ajoutez la ligne suivante à l'intérieur de votre fonction <code>draw()</code>, juste en dessous de la ligne qui appelle <code>drawBall()</code> :</p>

<pre class="brush: js">drawPaddle();
</pre>

<h2 id="Comparez_votre_code">Comparez votre code</h2>

<p>Voici le code de référence auquel vous pouvez comparer le vôtre :</p>

<p>{{JSFiddleEmbed("https://jsfiddle.net/end3r/tgn3zscj/","","395")}}</p>

<p><strong>Exercice: </strong>faites aller la raquette plus vite ou plus lentement, ou changez sa taille.</p>

<h2 id="Dans_le_prochain_chapitre">Dans le prochain chapitre</h2>

<p>Maintenant, nous avons quelque chose qui ressemble à un jeu. Le seul problème, c'est que vous pouvez continuer à frapper la balle avec la raquette indéfiniment. Tout cela va changer dans le cinquième chapitre, <a href="/fr/docs/Games/Workflows/Breakout_game_from_scratch/Game_over">Game over</a>, lorsque nous commencerons à ajouter un état de fin de partie pour notre jeu.</p>

<p>{{PreviousNext("Games/Workflows/2D_Breakout_game_pure_JavaScript/Faire_rebondir_la_balle_sur_les_murs", "Games/Workflows/2D_Breakout_game_pure_JavaScript/Game_over")}}</p>
