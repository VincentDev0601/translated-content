---
title: Jeu de casse-briques 2D en pur JavaScript
slug: Games/Tutorials/2D_Breakout_game_pure_JavaScript
tags:
  - 2D
  - Canvas
  - Débutant
  - JavaScript
  - Jeux
  - Tutoriel
translation_of: Games/Tutorials/2D_Breakout_game_pure_JavaScript
original_slug: Games/Workflows/2D_Breakout_game_pure_JavaScript
---
<div>{{GamesSidebar}}</div>

<div>{{IncludeSubnav("/fr/docs/Jeux")}}</div>

<p>{{Next("Games/Workflows/2D_Breakout_game_pure_JavaScript/creer_element_canvas_et_afficher")}}</p>

<p>Dans ce tutoriel, nous allons créer pas à pas un jeu de casse-briques MDN, créé entièrement avec JavaScript et sans framework, et rendu avec la balise HTML5 {{htmlelement("canvas")}}.</p>

<p>Chaque étape est modifiable en direct, et disponible en test pour que vous puissiez voir ce à quoi les étapes intermédiaires devraient ressembler. Vous apprendrez les bases d'utilisations de l'élément {{htmlelement("canvas")}} pour implémenter des mécaniques de base du jeu vidéo, comme charger et déplacer des images, les détections de collisions, les mécanismes de contrôle, et les conditions de victoire/défaite.</p>

<p>Pour comprendre la plupart des articles de ce tutoriel, vous devez déjà avoir un niveau basique ou intermédiaire en <a href="/fr/Learn/Getting_started_with_the_web/JavaScript_basics">JavaScript</a>. À la fin de ce tutoriel, vous serez capable de créer vos propres jeux Web.</p>

<p><img src="mdn-breakout-gameplay.png"></p>

<h2 id="Détail_de_la_leçon">Détail de la leçon</h2>

<p>Toutes les leçons — et les différentes versions de ce <a href="http://breakout.enclavegames.com/lesson10.html">jeu de casse-brique MDN</a> que nous allons créer ensemble — sont <a href="https://github.com/end3r/Canvas-gamedev-workshop">disponibles sur GitHub</a> :</p>

<ol>
 <li><a href="/fr/docs/Games/Workflows/2D_Breakout_game_pure_JavaScript/creer_element_canvas_et_afficher">Créer l'élément canvas et dessiner dessus</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Move_the_ball">Déplacer la balle</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Bounce_off_the_walls">Rebondir sur les murs</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Paddle_and_keyboard_controls">Contrôles clavier</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Game_over">Jeu terminé</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Build_the_brick_field">Construire le mur de briques</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Collision_detection">Détection des collisions</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Track_the_score_and_win">Afficher le score et gagner</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Mouse_controls">Contrôles souris</a></li>
 <li><a href="/fr/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript/Finishing_up">Finir</a></li>
</ol>

<p>Commencer avec du Javascript pur et dur est le meilleur moyen d'acquérir des connaissances de développement de jeu web. Après ceci, vous pourrez prendre n'importe quel "framework" et l'utiliser pour vos projets. Les "frameworks" sont des outils créés avec le langage Javascript ; donc, même si vous voulez travailler avec ces derniers, c'est toujours bon d'apprendre le langage lui-même pour savoir ce qu'il se passe exactement. Les "frameworks" améliorent la vitesse de développement et aident à traiter les parties les moins intéressantes du jeu, mais si quelque chose ne fonctionne pas comme prévu, vous pouvez toujours essayer de déboguer ou juste écrire vos propre solutions en Javascript. </p>

<div class="note">
<p><strong>Note :</strong> Si vous êtes intéressé par l'apprentissage du développement un jeu web 2D avec un "framework", consultez la série <a href="/fr/docs/Games/Tutorials/2D_breakout_game_Phaser">Jeu de casse-tête 2D avec Phaser</a>.</p>
</div>

<div class="note">
<p><strong>Note :</strong> Cette série d'articles peut être utilisée comme matériel pour des ateliers pratiques de développement de jeux. Vous pouvez également utiliser le <a href="https://github.com/end3r/Gamedev-Canvas-Content-Kit">Gamedev Canvas Content Kit</a> basé sur ce tutoriel si vous voulez faire une présentation sur le développement de jeux en général .</p>
</div>

<h2 id="Prochaines_étapes">Prochaines étapes</h2>

<p>Ok, c'est parti ! Rendez-vous au premier chapitre pour commencer — Créer l'élément canvas et dessiner dessus</p>

<p>{{Next("Games/Workflows/2D_Breakout_game_pure_JavaScript/creer_element_canvas_et_afficher")}} </p>
