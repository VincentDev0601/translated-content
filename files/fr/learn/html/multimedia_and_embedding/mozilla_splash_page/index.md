---
title: 'Évaluation : page d''accueil Mozilla'
slug: Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page
translation_of: Learn/HTML/Multimedia_and_embedding/Mozilla_splash_page
original_slug: Apprendre/HTML/Multimedia_and_embedding/Mozilla_splash_page
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenu("Learn/HTML/Multimedia_and_embedding/Responsive_images", "Learn/HTML/Multimedia_and_embedding")}}</div>

<p>Dans cette partie, nous testerons vos connaissances des quelques techniques abordées dans les articles de ce module, en vous demandant d'ajouter des images et des vidéos à une super page d'accueil entièrement dédiée à Mozilla !</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Avant de vous attaquer à cette étude, vous devriez avoir déjà travaillé sur les paragraphes précédents composant le module <a href="/fr/Apprendre/HTML/Multimedia_and_embedding">Multimedia et Intégration</a>.</td>
  </tr>
  <tr>
   <th scope="row">Objectif:</th>
   <td>Tester vos connaissances sur l'intégration d'images et vidéos dans des pages web ainsi que des techniques d'images adaptatives (images "responsive").</td>
  </tr>
 </tbody>
</table>

<h2 id="Point_de_départ">Point de départ</h2>

<p>Pour démarrer cette étude, vous devez aller chercher toutes les images et l'HTML disponibles dans le répertoire <a href="https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/mdn-splash-page-start/">mdn-splash-page-start</a> sur github. Mettez le contenu du fichier <a href="https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/mdn-splash-page-start/index.html">index.html</a> dans un fichier appelé <code>index.html</code> sur votre disque dur local, dans un nouveau répertoire. Puis copiez <a href="https://github.com/mdn/learning-area/blob/master/html/multimedia-and-embedding/mdn-splash-page-start/pattern.png">pattern.png</a> dans le même dossier (clic droit sur l'image pour le menu des options).</p>

<p>Allez dans le répertoire <a href="https://github.com/mdn/learning-area/tree/master/html/multimedia-and-embedding/mdn-splash-page-start/originals">originals</a> chercher les différentes images et faites la même chose; vous aurez peut-être à les enregistrer dans un nouveau dossier pour l'instant, au cas où vous auriez besoin d'en manipuler certaines en utilisant un éditeur graphique avant de pouvoir les utiliser.</p>

<div class="note">
<p><strong>Note :</strong> le fichier HTML en exemple contient un bon nombre de CSS, pour styliser la page. Vous n'avez pas besoin de modifier le CSS, juste l'HTML dans l'élément {{htmlelement("body")}} — tant que vous insérez les bonnes balises, le style sera cohérent.</p>
</div>

<h2 id="Énoncé_du_projet">Énoncé du projet</h2>

<p>Dans cette étude, nous vous présentons une page d'accueil Mozilla quasiment finie, qui a pour but de définir, en des termes agréables et intéressants, les objectifs de Mozilla et de fournir des liens vers des ressources supplémentaires. Malheureusement, aucune image ni vidéo n'a été ajoutée pour l'instant — c'est votre boulot ! Vous devez ajouter des choses qui donnent du sens à la page et la rendent belle. Les sous-sections suivantes détaillent ce que vous aurez besoin de faire :</p>

<h3 id="Préparer_les_images">Préparer les images</h3>

<p>Avec votre éditeur d'images favori, créez des versions de 400 et 120 px de large de :</p>

<ul>
 <li><code>firefox_logo-only_RGB.png</code></li>
 <li><code>firefox-addons.jpg</code></li>
 <li><code>mozilla-dinosaur-head.png</code></li>
</ul>

<p>Donnez-leur des noms similaires comme :  <code>firefoxlogo400.png</code> et <code>firefoxlogo120.png</code>.</p>

<p>Continuons avec <code>mdn.svg</code>, ces images seront vos icônes pour lier aux ressources externes, contenues dans l'espace<code>further-info</code>. Vous ferez aussi un lien vers le logo firefox dans l'en-tête du site. Réservez toutes ces copies dans le même dossier que l'<code>index.html</code>.</p>

<p>Puis, créez une version paysage de 1200px de large de <code>red-panda.jpg</code>, et une version portrait de 600px de large qui montre le panda en gros plan. Encore une fois, nommez-les de manière similaire pour les identifier facilement. Réservez toutes ces copies dans le même dossier que l'<code>index.html</code>.</p>

<div class="note">
<p><strong>Note :</strong> Vous devriez optimiser vos images JPG et PNG pour les rendre le plus petit possible tout en restant de bonne qualité. <a href="https://tinypng.com/">tinypng.com</a> est une bonne aide pour faire ça aisément.</p>
</div>

<h3 id="Ajouter_un_logo_à_l'en-tête">Ajouter un logo à l'en-tête</h3>

<p>A l'intèrieur de l'élément {{htmlelement("header")}} , ajoutez un élément {{htmlelement("img")}} qui intégrera une petite version du logo firefox dans l'en-tête.</p>

<h3 id="Ajouter_une_vidéo_dans_le_contenu_principal_de_l'article">Ajouter une vidéo dans le contenu principal de l'article</h3>

<p>Dans l'élément {{htmlelement("article")}}  (juste en-dessous de la balise d'ouverture), intégrez la vidéo YouTube trouvée ici : <a href="https://www.youtube.com/watch?v=ojcNcvb1olg">https://www.youtube.com/watch?v=ojcNcvb1olg</a>, en utilisant les outils YouTube appropriés pour générer le code. La vidéo devra faire 400px de large.</p>

<h3 id="Ajouter_des_images_adaptatives_aux_liens_vers_les_ressources_externes">Ajouter des images adaptatives aux liens vers les ressources externes</h3>

<p>Dans l'élément {{htmlelement("div")}} de la catégorie <code>further-info</code> vous trouverez quatre autres éléments {{htmlelement("a")}} — chacun d'eux liant vers une page intéressante traitant de Mozilla. Pour compléter cette section, vous devrez insérer un élément {{htmlelement("img")}} dans ceux contenant les attributs {{htmlattrxref("src", "img")}}, {{htmlattrxref("alt", "img")}}, {{htmlattrxref("srcset", "img")}} et {{htmlattrxref("sizes", "img")}} adéquats.</p>

<p>Dans tous les cas (sauf un — lequel serait naturellement adaptatif ?) nous voulons que le navigateur desserve la version 120px de large quand la largeur du cadre est de 480px ou moins, ou la version 400px de large dans les autres cas.</p>

<p>Assurez-vous de faire correspondre les bonnes images avec les liens corrects !</p>

<div class="note">
<p><strong>Note :</strong> Pour tester correctement les exemples <code>srcset</code>/<code>sizes</code>, vous devez charger votre site sur un serveur (utiliser <a href="/fr/docs/Learn/Common_questions/Using_Github_pages">Github pages</a> est une solution simple et gratuite), ensuite vous pouvez tester si tout se déroule correctement en utilisant des outils de développeur, comme expliqué dans <a href="/fr/Learn/HTML/Multimedia_and_embedding/Responsive_images#Useful_developer_tools">Responsive images: useful developer tools</a>.</p>
</div>

<h3 id="Un_panda_rouge_créatif">Un panda rouge créatif</h3>

<p>Dans l'élément {{htmlelement("div")}} de la catégorie r<code>ed-panda</code>, nous voulons insérer un élément {{htmlelement("picture")}} qui affiche le petit portrait du panda si le cadre est de 600px de large, ou moins, et le paysage dans les autres cas.</p>

<h2 id="Exemple">Exemple</h2>

<p>La capture d'écran suivante montre à quoi devrait ressembler la page d'accueil aprés avoir été correctement balisée, avec un affichage large et un étroit.</p>

<p><img alt="A wide shot of our example splash page" src="wide-shot.png"></p>

<p><img alt="A narrow shot of our example splash page" src="narrow-shot.png"></p>

<h2 id="Évaluation">Évaluation</h2>

<p>Si vous suivez cette étude en faisant partie d'un programme de cours organisé, vous devriez pouvoir montrer votre travail à votre professeur/mentor pour une correction. Si vous apprenez seul, alors vous pourrez obtenir des informations et des corrections en demandant sur le  <a href="https://discourse.mozilla.org/t/mozilla-splash-page-assignment/24679">fil de discussion concernant cet exercice</a>, ou sur le canal IRC <a href="irc://irc.mozilla.org/mdn">#mdn</a> sur <a href="https://wiki.mozilla.org/IRC">Mozilla IRC</a>. Essayez de faire l'exercice d'abord — On ne gagne rien en trichant !</p>

<p>{{PreviousMenu("Learn/HTML/Multimedia_and_embedding/Responsive_images", "Learn/HTML/Multimedia_and_embedding")}}</p>

<p> </p>

<h2 id="Dans_ce_module">Dans ce module :</h2>

<ul>
 <li><a href="/fr/Apprendre/HTML/Multimedia_and_embedding/Images_in_HTML">Les images en HTML</a></li>
 <li><a href="/fr/Apprendre/HTML/Multimedia_and_embedding/Contenu_audio_et_video">Contenu audio et video</a></li>
 <li><a href="/fr/Apprendre/HTML/Multimedia_and_embedding/Other_embedding_technologies">Des objets aux "iframes" - autres techniques d'intégration</a></li>
 <li><a href="/fr/Apprendre/HTML/Comment/Ajouter_des_images_vectorielles_%C3%A0_une_page_web">Ajouter des images vectorielles à une page web</a></li>
 <li><a href="/fr/Apprendre/HTML/Comment/Ajouter_des_images_adaptatives_%C3%A0_une_page_web">Images adaptatives</a></li>
 <li><a href="/fr/Apprendre/HTML/Multimedia_and_embedding/Mozilla_splash_page">Évaluation : page d'accueil Mozilla</a></li>
</ul>

<p> </p>
