---
title: d
slug: Web/SVG/Attribute/d
tags:
  - Attribut SVG
  - SVG
translation_of: Web/SVG/Attribute/d
---
<div>{{SVGRef}}</div>

<p>L'attribut <strong><code>d</code></strong> définit un tracé à dessiner.</p>

<p>La définition d'un tracé est une liste de commandes de tracé où chaque commande est composée d'une lettre pour la commande, et de nombres qui représentent les paramètres de la commande. Les commandes sont détaillées ci-dessous.</p>

<p>Trois éléments ont cet attribut : {{SVGElement("path")}}, {{SVGElement("glyph")}}, and {{SVGElement("missing-glyph")}}</p>

<h2>Exemple</h2>

<pre class="brush: css hidden">html,body,svg { height:100% }</pre>

<pre class="brush: html">&lt;svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;path fill="none" stroke="red"
    d="M 10,30
       A 20, 20 0, 0, 1 50, 30
       A 20, 20 0, 0, 1 90, 30
       Q 90, 60 50, 90
       Q 10, 60 10, 30 z" /&gt;
&lt;/svg&gt;</pre>

<p>{{EmbedLiveSample('exemple', '100%', 200)}}</p>

<h2 id="Tracé">Tracé</h2>

<p>Pour un {{SVGElement('path')}}, <code>d</code> est une chaîne de caractère qui contient une série de commandes de tracé qui définissent le tracé à dessiner.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Valeur</th>
   <td><strong><a href="/docs/Web/SVG/Content_type#String">&lt;string&gt;</a></strong></td>
  </tr>
  <tr>
   <th scope="row">Valeur par défaut</th>
   <td><em>aucune</em></td>
  </tr>
  <tr>
   <th scope="row">Animable</th>
   <td>Oui</td>
  </tr>
 </tbody>
</table>

<h2 id="glyph">glyph</h2>

<div class="warning">
  <p><strong>Attention :</strong> Depuis SVG2, {{SVGElement('glyph')}} est dépréciée et ne doit plus être utilisé.</p>
</div>

<p>Pour un {{SVGElement('glyph')}}, <code>d</code> est une chaîne de caractères qui contient une série de commandes de tracé qui définissent la forme du contour de la glyphe.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Valeur</th>
   <td><strong><a href="/docs/Web/SVG/Content_type#String">&lt;string&gt;</a></strong></td>
  </tr>
  <tr>
   <th scope="row">Valeur par défaut</th>
   <td><em>aucune</em></td>
  </tr>
  <tr>
   <th scope="row">Animable</th>
   <td>Oui</td>
  </tr>
 </tbody>
</table>

<div class="note">
  <p><strong>Note :</strong> Le point d'origine (coordonnée <code>0,0</code>) est généralement le point du <em>coin en haut à gauche</em> du context. Néanmoins, l'élément {{SVGElement("glyph")}} a son point d'origine dans le coin en bas à gauche de son enveloppe.</p>
</div>

<h2 id="missing-glyph">missing-glyph</h2>

<div class="warning">
  <p><strong>Attention :</strong> Depuis SVG2, {{SVGElement('missing-glyph')}} est dépréciée et ne doit plus être utilisé.</p>
</div>

<p>Pour un {{SVGElement('missing-glyph')}}, <code>d</code> est une chaîne de caractères qui contient une série de commandes de tracé qui définissent la forme du contour de la glyphe.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Valeur</th>
   <td><strong><a href="/docs/Web/SVG/Content_type#String">&lt;string&gt;</a></strong></td>
  </tr>
  <tr>
   <th scope="row">Valeur par défaut</th>
   <td><em>aucune</em></td>
  </tr>
  <tr>
   <th scope="row">Animable</th>
   <td>Oui</td>
  </tr>
 </tbody>
</table>

<h2 id="Commandes_de_tracé">Commandes de tracé</h2>

<p>Les commandes de tracé sont des instructions qui définissent un tracé à dessiner. Chaque commande est composée d'une lettre de commande et de nombres qui représentent les paramètres de la commande.</p>

<p>SVG définit 6 types de commandes, pour un total de 20 commandes :</p>

<ul>
 <li>Aller à (Moveto)</li>
 <li>Tracer une ligne jusqu'à (Lineto)</li>
 <li>Tracer une courbe jusqu'à (Curveto)</li>
 <li>Tracer un arc de cercle jusqu'à (Arcto)</li>
 <li>Fermer le chemin (ClosePath)</li>
</ul>

<div class="note">
  <p><strong>Note:</strong> Les commandes sont sensibles à la casse; une commande en majuscule attend des positions absolues en arguments, alors qu'une commande en minuscule attend des points relatifs à la position actuelle du point.</p>
</div>

<p>Il est toujours possible de spécifier une valeur négative en argument d'une commande : des angles négatifs pointeront dans une direction vers le sens inverse des aiguilles d'une montre; des positions <code>x</code> et <code>y</code> seront interprétées commandes coordonnées négatives; des valeurs <code>x</code> négatives se déplaceront vers la gauche; et des valeurs <code>y</code> négatives se déplaceront vers le haut.</p>

<h2 id="Moveto_(aller_à)">Moveto (aller à)</h2>

<p>Cette instuction peut être vue comme un déplacement du pinceau à une position donnée sans rien tracer. Une bonne pratique consiste à commencer tous ses chemins par une instruction Moveto car, sans un positionnement initial, les instructions du chemin commencerons à un point quelconque ce qui peut donner des résultats non désirés.</p>

<p>Syntaxe:</p>

<ul>
 <li><strong><code>M x, y</code></strong> où x et y sont des coordonnées absolues, respectivement horizontale et verticale.</li>
 <li><strong><code>m dx, dy</code></strong> où dx et dy sont des distances relatives à la position courante, respectivement vers la droite et vers le bas.</li>
</ul>

<p>Exemples :</p>

<ul>
 <li>Positionnement absolu en x = 50, y = 100 : <code>&lt;path d="M 50, 100..." /&gt;</code></li>
 <li>Déplacement de 50 vers la droite et 100 vers le bas : <code>&lt;path d="m 50, 100..." /&gt;</code></li>
</ul>

<h2 id="Lineto_(tracer_une_ligne_jusqu'à)">Lineto (tracer une ligne jusqu'à)</h2>

<p>À l'opposé de l'instruction Moveto, Lineto trace réellement une ligne de la position courante à la position définie. La syntaxe générique est <code>L x, y</code> ou <code>l dx, dy</code> avec <code>x, y</code> des coordonnées absolues et <code>dx, dy</code> des distances relatives au point courant, respectivement dans les sens de gauche à droite pour <code>dx</code> et de haut en bas pour <code>dy</code>.</p>

<p>Il existe aussi des raccourcis pour définir des lignes horizontales (H) ou verticales (V). Leur syntaxe est similaire à celle de L, mais il n'y a qu'une valeur à donner.</p>

<p>Exemples :</p>

<ul>
 <li>Dessiner un carré (avec coordonnées relatives) : <code>&lt;path d="M -10, -10 h 50 v 50 h -50 v -50"/&gt;</code></li>
 <li>Dessiner un carré (avec coordonnées absolues) : <code>&lt;path d="M -10, -10 H 40 V 40 H -10 V -10"/&gt;</code></li>
</ul>

<h2 id="Curveto">Curveto</h2>

<p>L'instruction Curveto trace une courbe de Bézier. Il existe deux types de courbes de Bézier : cubique et quadratique. Les courbes cubiques sont un cas particulier des courbes quadratiques puisque le point de contrôle est commun au point de départ et au point d'arrivée. La syntaxe d'une courbe quadratique de Bézier est "Q cx,cy x,y" ou "q dcx,dcy dx,dy". cx et cy sont les coordonnées absolues du point de contrôle tandis que dcx et dcy sont les coordonnées du point de contrôle relatives au point courant. x et y sont les coordonnées absolues du point d'arrivée tandis que dx et dy sont les coordonnées relatives de ce point par rapport au point courant.</p>

<p>Les courbes cubiques de Bézier suivent le même principe mais avec deux points de contrôle. La syntaxe de ces courbes est <code>C c1x, c1y c2x, c2y x, y</code> ou <code>c dc1x, dc1y dc2x, dc2y dx, dy</code>.</p>




<p>Pour réaliser des chaînes de courbes de Bézier "adoucies", il est possible d'utiliser les commandes T et S. Leur syntaxe est plus simple que les autres commandes Curveto car elles estiment que le premier point de contrôle est le symétrique du point de contrôle précédent par rapport au point terminal de la courbe précédente, ou que c'est le point précédent lui-même s'il n'y a pas eu de courbe tracée directement avant. La syntaxe de T est <code>T x, y</code> ou <code>t dx, dy</code> pour un point d'arrivée de position absolue ou relatives et sert à créer des courbes quadratiques de Bézier. S sert donc à faire des courbes cubiques de Bézier avec la syntaxe <code>S cx, cy x, y</code> ou <code>s dcx,dcy dx,dy</code>, où (d)cx indique le second point de contrôle.</p>

<p>Finalement, toutes les commandes de courbes de Bézier peuvent servir de "polybézier" en spécifiant tous les paramètres successivement après la commande initiale. En conséquence, les deux commandes suivantes sont équivalentes en résultat :</p>

<p><code>&lt;path d="c 50, 0 50, 100 100, 100 50, 0 50, -100 100, -100" /&gt;<br>
 &lt;path d="c 50, 0 50, 100 100, 100 c 50, 0 50, -100 100, -100" /&gt;</code></p>

<h2 id="Arcto">Arcto</h2>

<p>Parfois il est plus simple de définir un <code>path</code> comme une courbe elliptique plutôt que comme une courbe de Bézier. Dans cette optique, les commandes Arcto sont supportées par les balises <code>path</code>.</p>

<p>La définition d'un Arcto est relativement complexe : <code>A rx, ry xAxisRotate LargeArcFlag, SweepFlag x, y</code>, où <code>rx</code> et <code>ry</code> représentent les rayons sur les axes x et y, respectivement ; <code>LargeArcFlag</code> est une valeur à 0 ou 1, et permet de déterminer si le plus petit (0) ou le plus grand (1) arc possible doit être dessiné ; <code>SweepFlag</code> est une valeur à 0 ou 1 et définit le sens de balayage de la courbe : horaire (1) ou anti-horaire (0) ; et enfin <code>x</code> et <code>y</code> sont les coordonnées de destination.</p>

<p>La propriété <code>xAxisRotate</code> est censée changer l'axe des x relativement au viewport de référence. Cependant, il semble que cette propriété n'ait aucun effet avec le moteur de rendu Gecko 7.</p>

<h2 id="ClosePath_(fermer_un_chemin)">ClosePath (fermer un chemin)</h2>

<p>L'instruction ClosePath trace simplement une ligne droite de la position actuelle jusqu'au point initial de la courbe. C'est l'instruction la plus simple puisqu'elle n'attend aucun argument. Il n'y a pas de différence entre la version majuscule ("Z") et la version minuscule ("z").</p>

<h2 id="Éléments">Éléments</h2>

<p>Les éléments suivants peuvent utiliser l'attribut <strong>d</strong> :</p>

<ul>
 <li>{{SVGElement("path")}}</li>
 <li>{{SVGElement("glyph")}}</li>
</ul>

<p>De plus, les mêmes règles s'appliquent aux animations de chemin {{SVGElement("animate")}}.</p>

<h2 id="Notes">Notes</h2>

<p>Le point d'origine (de coordonnées 0,0) est habituellement le <strong>coin supérieur gauche</strong> du contexte. Cependant, l'élément {{SVGElement("glyph")}} a son origine dans le <strong>coin inférieur gauche</strong> de la boîte contenant son caractère.</p>
