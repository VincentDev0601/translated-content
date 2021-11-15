---
title: Compréhension fondamentale de la mise en page
slug: Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension
translation_of: Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension
original_slug: Apprendre/CSS/CSS_layout/Fundamental_Layout_Comprehension
---
<div>{{LearnSidebar}}</div>

<p>Si vous avez travaillé sur ce module, vous aurez déjà couvert les bases de ce que vous devez savoir pour faire la mise en forme CSS aujourd'hui, et pour travailler avec les anciennes CSS également. Cette tâche testera certaines de vos connaissances en développant une mise en page simple en utilisant diverses techniques.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row"><strong>Conditions préalables</strong>:</th>
   <td>Avant de tenter cette évaluation, vous devriez déjà avoir passé en revue tous les articles de ce module.</td>
  </tr>
  <tr>
   <th scope="row"><strong>Objectif</strong>:</th>
   <td>Pour tester la compréhension des compétences de base en aménagement couvertes dans ce module.</td>
  </tr>
 </tbody>
</table>

<h2 id="dossier_de_projet">dossier de projet</h2>

<p>Vous avez reçu du HTML brut, du CSS de base et des images - vous devez maintenant créer une mise en page pour la conception, qui devrait ressembler à l'image ci-dessous.</p>

<p><img alt="" src="layout-task-complete.png"></p>

<h3 id="configuration_de_base">configuration de base</h3>

<p>Vous pouvez télécharger le code HTML, CSS et un ensemble de six images <a  href="https://github.com/mdn/learning-area/tree/master/css/css-layout/fundamental-layout-comprehension">ici</a> .</p>

<p>Enregistrez le document HTML et la feuille de style dans un répertoire de votre ordinateur, puis ajoutez les images dans un dossier nommé <code>images</code>. Ouvrir le <code>index.html</code>fichier dans un navigateur devrait vous donner une page avec un style de base mais pas de mise en page, ce qui devrait ressembler à l'image ci-dessous.</p>

<p>Ce point de départ contient tout le contenu de votre mise en page, tel qu’il est affiché par le navigateur dans un flux normal.</p>

<p><img alt="" src="layout-task-start.png"></p>

<h3 id="Votre_section_detâches">Votre section de tâches</h3>

<p>Vous devez maintenant implémenter votre mise en page. Les tâches que vous devez accomplir sont:</p>

<ol>
 <li>Pour afficher les éléments de navigation dans une ligne, avec un espace égal entre les éléments.</li>
 <li>La barre de navigation doit défiler avec le contenu, puis rester bloquée en haut de la fenêtre d’affichage quand elle l’atteint.</li>
 <li>L'image qui se trouve à l'intérieur de l'article doit être entourée de texte.</li>
 <li>Les éléments <a href="/fr/docs/Web/HTML/Element/article"><code>&lt;article&gt;</code></a>et <a href="/fr/docs/Web/HTML/Element/aside"><code>&lt;aside&gt;</code></a>doivent s'afficher sous la forme d'une disposition à deux colonnes. La taille des colonnes doit être flexible de sorte que, si la fenêtre du navigateur est réduite, les colonnes deviennent plus étroites.</li>
 <li>Les photographies doivent s’afficher sous forme de grille à deux colonnes avec un intervalle de 1 pixel entre les images.</li>
</ol>

<p>Vous n'aurez pas besoin de modifier le code HTML pour obtenir cette présentation. Les techniques à utiliser sont les suivantes:</p>

<ul>
 <li>Positionnement</li>
 <li>Flotte</li>
 <li>Flexbox</li>
 <li>CSS Grid Layout</li>
</ul>

<p>Vous pouvez réaliser certaines de ces tâches de plusieurs manières et il n’existe souvent pas de bonne ou de mauvaise façon de faire les choses. Essayez différentes approches et voyez laquelle fonctionne le mieux. Prenez des notes pendant que vous expérimentez et vous pourrez toujours discuter de votre approche dans le fil de discussion de cet exercice ou dans le <a href="irc://irc.mozilla.org/mdn">canal</a> IRC <a href="irc://irc.mozilla.org/mdn">#mdn</a> .</p>

<h2 id="Evaluation">Evaluation</h2>

<p>Si vous suivez cette évaluation dans le cadre d'un cours organisé, vous devriez pouvoir donner votre travail à votre enseignant / mentor pour qu'il la corrige. Si vous vous auto-apprenez, vous pouvez obtenir le guide de notation assez facilement en vous renseignant sur le <a  href="https://discourse.mozilla.org/t/fundamental-layout-comprehension-assessment/29982" rel="noopener">fil de discussion relatif à cet exercice</a> ou sur le <a href="irc://irc.mozilla.org/mdn">canal</a> IRC <a href="irc://irc.mozilla.org/mdn">#mdn</a> sur <a  href="https://wiki.mozilla.org/IRC" rel="noopener">Mozilla IRC</a> . Essayez d’abord l’exercice - il n’ya aucun avantage à tricher!</p>

<h2 id="Dans_ce_module_Section">Dans ce module Section</h2>

<ul>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Introduction">Introduction à la mise en page CSS</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Normal_Flow">Débit normal</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Flexbox">Flexbox</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Grids">la grille</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Floats">Flotteurs</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Positioning">Positionnement</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Multiple-column_Layout">Mise en page à plusieurs colonnes</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Responsive_Design">Conception sensible</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Media_queries">Guide du débutant aux questions des médias</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods">Méthodes de mise en page héritées</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Supporting_Older_Browsers">Soutenir les anciens navigateurs</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension">Évaluation fondamentale de la compréhension de la mise en page.</a></li>
</ul>
