---
title: Jeux 3D sur le web
slug: Games/Techniques/3D_on_the_web
tags:
  - 3D
  - Images
  - Jeux
  - WebGL
  - WebVR
  - three.js
translation_of: Games/Techniques/3D_on_the_web
---
<div>{{GamesSidebar}}</div>

<p>  {{IncludeSubnav("/fr/docs/Jeux")}}</p>

<p>Pour des expériences de jeu riches sur le Web, l'arme de choix est WebGL, qui est fourni sur HTML {{htmlelement ("canvas")}}. WebGL est essentiellement un OpenGL ES 2.0 pour le Web - c'est une API JavaScript fournissant des outils pour créer des animations interactives riches et bien sûr aussi des jeux. Vous pouvez générer et rendre des graphiques 3D dynamiques avec du JavaScript accéléré.</p>

<h2 id="Documentation_et_support_du_navigateur">Documentation et support du navigateur</h2>

<p>La documentation et les spécifications du projet <a href="/fr/docs/Web/API/WebGL_API">WebGL</a> sont gérées par le <a href="https://www.khronos.org/">Groupe Khronos</a>, pas le W3C comme pour la plupart des API Web. Le support sur les navigateurs modernes est très bon, même sur mobile, donc vous n'avez pas trop à vous en soucier. Les principaux navigateurs prennent en charge WebGL et tout ce dont vous avez besoin est de vous concentrer sur l'optimisation des performances sur les appareils que vous utilisez.</p>

<p>Il y a un effort continu pour rendre libre WebGL 2.0 (basé sur OpenGL ES 3.0) dans un proche avenir, ce qui apporterait de nombreuses améliorations et aiderait les développeurs à construire des jeux pour le Web moderne en utilisant le matériel puissant actuel.</p>

<h2 id="Explication_des_bases_de_la_théorie_3D">Explication des bases de la théorie 3D</h2>

<p>Les bases de la théorie 3D s'articulent autour des formes représentées dans un espace 3D, avec un système de coordonnées utilisé pour calculer leurs positions. Consultez <a href="/fr/docs/Games/Techniques/3D_on_the_web/Basic_theory">notre article de base sur la théorie 3D</a> pour toutes les informations dont vous avez besoin.</p>

<h2 id="Concepts_avancés">Concepts avancés</h2>

<p>Vous pouvez faire beaucoup plus avec WebGL. Il y a des concepts avancés dans lesquels vous devriez plonger et en apprendre davantage  —  les "shaders", la détection de collision ou le dernier sujet brûlant  — la réalité virtuelle sur le Web.</p>

<h3 id="Shaders">Shaders</h3>

<p>Il convient de distinguer les shaders, qui sont un cas particulier. Les Shaders utilisent GLSL, un langage d'ombrage OpenGL spécial avec une syntaxe similaire à C, qui est exécuté directement par le pipeline graphique. Ils peuvent être divisés en "Vertex Shaders" et "Fragment Shaders" (ou "Pixel Shaders")  —  le premier transforme les positions des formes en véritables coordonnées de dessin 3D, tandis que le second calcule les couleurs de rendu et d'autres attributs. Vous devriez absolument lire l'article <a href="/fr/docs/Games/Techniques/3D_on_the_web/GLSL_Shaders">GLSL Shaders</a> pour en apprendre plus à leur sujet.</p>

<h3 id="Détection_de_collision">Détection de collision</h3>

<p>Il est difficile d'imaginer un jeu sans la détection de collision  —  nous devons toujours mettre au point quand quelque chose frappe quelque chose d'autre. Nous avons des informations disponibles pour votre apprentissage de :</p>

<ul>
 <li><a href="/fr/docs/Games/Techniques/2D_collision_detection">détection de collision 2D</a></li>
 <li><a href="/fr/docs/Games/Techniques/3D_collision_detection">détection de collision 3D</a></li>
</ul>

<h3 id="Réalité_virtuelle_sur_le_web">Réalité virtuelle sur le web</h3>

<p>Le concept de réalité virtuelle n'est pas nouveau, mais il est en train de conquérir le web grâce à des avancées matérielles telles que l' <a href="https://www.oculus.com/en-us/rift/">Oculus Rift</a>  et l'<a href="/fr/docs/Web/API/WebVR_API">API WebVR</a> (actuellement expérimental) pour capturer les informations du matériel de réalité virtuelle et les rendre disponibles pour les applications JavaScript. Pour en savoir plus, lisez <a href="/fr/docs/Games/Techniques/3D_on_the_web/WebVR">WebVR - Réalité virtuelle pour le Web</a>.</p>

<p>Il y a aussi la <a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_A-Frame">construction d'une démo de base avec l'article A-Frame</a> qui montre comment il est facile de construire des environnements 3D pour la réalité virtuelle en utilisant le framework  <a href="http://aframe.io/">A-Frame</a> .</p>

<h2 id="Lessor_des_bibliothèques_et_des_cadres">L'essor des bibliothèques et des cadres</h2>

<p>Le codage de WebGL brut est assez complexe, mais vous aurez envie de le maîtriser à long terme, car vos projets seront plus avancés (consultez notre <a href="/fr/docs/Web/API/WebGL_API">documentation WebGL</a> pour commencer). Pour les projets de monde réel, vous utiliserez probablement aussi un  "framework"  pour accélérer le développement et vous aider à gérer le projet. L'utilisation d'un "framework" pour les jeux 3D permet également d'optimiser les performances, car les outils que vous utilisez vous permettent de vous concentrer sur la construction du jeu.</p>

<p>La bibliothèque 3D JavaScript la plus populaire est  <a href="http://threejs.org/">Three.js</a>, un outil polyvalent qui rend les techniques 3D plus simples à implémenter. Il existe d'autres bibliothèques et cadres de développement de jeux populaires qui valent la peine d'être regardés ;  <a href="https://aframe.io">A-Frame</a>, <a href="https://playcanvas.com/">PlayCanvas</a>  et  <a href="http://www.babylonjs.com/">Babylon.js</a>  sont parmi les plus reconnaissables avec une documentation riche, des éditeurs en ligne et des communautés actives.</p>

<h3 id="Construction_dune_démo_de_base_avec_A-Frame">Construction d'une démo de base avec A-Frame</h3>

<p>A-Frame est un "framework" web pour construire des expériences 3D et de la réalité virtuelle. Sous le capot, il s'agit d'un "framework"  three.js  avec un modèle déclaratif entité-composant, ce qui signifie que nous pouvons construire des scènes avec seulement du HTML. Voir la page <a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_A-Frame">Construction d'une démo de base avec</a><a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_A-Frame"> A-Frame</a> pour le processus étape par étape de création de la démo .</p>

<h3 id="Construction_dune_démo_de_base_avec_Babylon.js">Construction d'une démo de base avec Babylon.js</h3>

<p>Babylon.js  est l'un des moteurs de jeux 3D les plus populaires utilisés par les développeurs. Comme avec n'importe quelle autre bibliothèque 3D, il fournit des fonctions intégrées pour vous aider à implémenter les fonctionnalités 3D courantes plus rapidement. Voir la page <a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_Babylon.js">Construction d'une démo de base avec Babylon.js</a> sur les bases et l'utilisation de Babylon.js, y compris la mise en place d'un environnement de développement, la structuration du code HTML nécessaire et l'écriture du code JavaScript.</p>

<h3 id="Construction_dune_démo_de_base_avec_PlayCanvas">Construction d'une démo de base avec PlayCanvas</h3>

<p>PlayCanvas est un moteur de jeu 3D WebGL populaire ouvert sur GitHub, avec un éditeur disponible en ligne et une bonne documentation. Voir la page <a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_PlayCanvas">Construction d'une démo de base avec PlayCanvas</a> pour des détails de haut niveau, et d'autres articles montrant comment créer des démos à l'aide de la bibliothèque PlayCanvas et de l'éditeur en ligne.</p>

<h3 id="Construction_dune_démo_de_base_avec_Three.js">Construction d'une démo de base avec Three.js</h3>

<p>Three.js, comme toute autre bibliothèque, vous donne un énorme avantage : au lieu d'écrire des centaines de lignes de code WebGL pour construire quelque chose d'intéressant, vous pouvez utiliser des fonctions intégrées pour le faire beaucoup plus facilement et plus rapidement. Voir la page <a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_Three.js">Construction d'une démo de base avec Three.js</a>  pour le processus étape par étape de création de la démo .</p>

<h3 id="Autres_outils">Autres outils</h3>

<p>Les deux  <a href="http://unity3d.com/">Unity</a>  et  <a href="https://www.unrealengine.com/">Unreal</a>  peuvent exporter votre jeu vers  <a href="/fr/docs/Web/API/WebGL_API">WebGL</a>  avec  <a href="/fr/docs/Games/Tools/asm.js">asm.js</a> , de sorte que vous êtes libre d'utiliser leurs outils et techniques pour construire des jeux qui seront exportés vers le web.</p>

<p><img alt="" src="shapes.png"></p>

<h2 id="Où_aller_ensuite">Où aller ensuite</h2>

<p>Avec cet article, nous avons juste effleuré la surface de ce qu'il est possible de faire avec les technologies actuellement disponibles. Vous pouvez créer des jeux 3D immersifs, beaux et rapides à l'aide de WebGL, les bibliothèques et les frameworks s'appuient dessus.</p>

<h3 id="Code_source">Code source</h3>

<p>Vous pouvez trouver tous les codes source de cette série de <a href="http://end3r.github.io/MDN-Games-3D/">démos sur GitHub</a>.</p>

<h3 id="API">API</h3>

<ul>
 <li><a href="/fr/docs/Web/HTML/Canvas">Canvas API</a></li>
 <li><a href="/fr/docs/Web/API/WebGL_API">WebGL API</a></li>
 <li><a href="/fr/docs/Web/API/WebVR_API">WebVR API</a></li>
</ul>

<h3 id="Frameworks">Frameworks</h3>

<ul>
 <li><a href="http://threejs.org/">Three.js</a></li>
 <li><a href="http://whitestormjs.xyz/">Whitestorm.js</a> (basé sur Three.js)</li>
 <li><a href="https://playcanvas.com/">PlayCanvas</a></li>
 <li><a href="http://www.babylonjs.com/">Babylon.js</a></li>
 <li><a href="http://aframe.io/">A-Frame</a></li>
</ul>

<h3 id="Tutorials">Tutorials</h3>

<ul>
 <li><a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_Three.js">Construction d'une démo de base avec Three.js</a></li>
 <li><a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_PlayCanvas">Construction d'une démo de base avec PlayCanvas</a></li>
 <li><a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_Babylon.js">Construction d'une démo de base avec Babylon.js</a></li>
 <li><a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_A-Frame">Construction d'une démo de base avec</a><a href="/fr/docs/Games/Techniques/3D_on_the_web/Building_up_a_basic_demo_with_A-Frame"> A-Frame</a></li>
</ul>
