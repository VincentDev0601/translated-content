---
title: Tutoriel canvas
slug: Web/API/Canvas_API/Tutorial
tags:
  - Canvas
  - Guide
  - HTML
  - Tutoriel_canvas
  - Tutoriels
translation_of: Web/API/Canvas_API/Tutorial
original_slug: Web/API/Canvas_API/Tutoriel_canvas
---
<div>{{CanvasSidebar}}</div>

<p><strong><a href="/fr/docs/Web/HTML/Element/canvas"><code>&lt;canvas&gt;</code></a></strong> est un nouvel élément <a href="/fr/docs/Web/HTML">HTML</a> qui peut être utilisé pour dessiner des éléments graphiques à l'aide de scripts (habituellement <a href="/fr/docs/Glossaire/JavaScript">JavaScript</a>). Il permet par exemple de dessiner des graphiques, de réaliser des compositions de photographies ou des animations simples (voire <a href="/fr/docs/Un_raycaster_basique_avec_canvas">pas si simples</a>). Les images à droite montrent quelques exemples d'implémentations utilisant <code>&lt;canvas&gt;</code> que nous verrons plus tard dans ce tutoriel.</p>

<p>Ce tutoriel explique comment utiliser l'élément <code>&lt;canvas&gt;</code> pour dessiner des graphiques 2D, en commençant par les bases. Les exemples fournis devraient vous donner des idées claires sur ce que vous pouvez faire avec la toile et fournir des extraits de code qui peuvent vous aider à créer votre propre contenu.</p>

<p>D'abord introduit dans WebKit par Apple pour le tableau de bord OS X, <code>&lt;canvas&gt;</code> a depuis été implémenté dans les navigateurs. Aujourd'hui, tous les principaux navigateurs le prennent en charge.</p>

<h2 id="Avant_de_commencer">Avant de commencer</h2>

<p>L'utilisation de l'élément <code>&lt;canvas&gt;</code> n'a rien de très compliqué, mais nécessite tout de même une compréhension de base de <a href="/fr/docs/Web/HTML">HTML</a> et <a href="/fr/docs/Glossaire/JavaScript">JavaScript</a>. L'élément <code>&lt;canvas&gt;</code> n'est pas reconnu par tous les vieux navigateurs, mais il est supporté par les versions les plus récentes des principaux. La taille par défaut de  canvas  est 300 px × 150 px (largeur × hauteur). Mais les tailles personnalisées peuvent être définies à l'aide des propriétés <a href="/fr/docs/Web/HTML">HTML</a> <code>height</code> et <code>width</code>. Afin de dessiner des graphiques sur  canvas , nous utilisons un objet de contexte JavaScript, qui crée des graphiques à la volée.</p>

<h2 id="Dans_ce_tutoriel">Dans ce tutoriel</h2>

<ul>
 <li><a href="/fr/docs/Tutoriel_canvas/Utilisation_de_base">Utilisation de base</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Formes_g%C3%A9om%C3%A9triques">Dessin de formes géométriques</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Ajout_de_styles_et_de_couleurs">Ajout de styles et de couleurs</a></li>
 <li><a href="/fr/docs/Dessin_de_texte_avec_canvas">Dessin de texte</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Utilisation_d'images">Utilisation d'images</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Transformations">Transformations</a></li>
 <li><a href="/fr/docs/Web/API/Canvas_API/Tutorial/Compositing">Compositions et découpage</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Animations_basiques">Animations basiques</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Advanced_animations">Animations avancées</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Pixel_manipulation_with_canvas">Manipulation des pixels</a></li>
 <li><a href="/fr/docs/Web/API/Canvas_API/Tutorial/Hit_regions_and_accessibility">Régions touchées et accessibilité</a></li>
 <li><a href="/fr/docs/Tutoriel_canvas/Optimizing_canvas">Optimisation</a></li>
 <li><a href="/fr/docs/Web/API/Canvas_API/Tutorial/Finale">Final</a></li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/HTML/Canvas">Page du sujet canvas</a></li>
 <li><a href="http://www.html5canvastutorials.com/">HTML5CanvasTutorials</a> (en)</li>
 <li><a href="/Special:Tags?tag=Exemples_d'utilisation_de_canvas&amp;language=fr">Exemples d'utilisation de canvas</a> (en)</li>
</ul>

<p>{{ Next("Tutoriel_canvas/Utilisation_de_base") }}</p>
