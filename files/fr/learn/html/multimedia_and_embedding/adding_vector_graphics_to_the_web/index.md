---
title: Ajouter des images vectorielles à une page web
slug: Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web
tags:
  - Graphics
  - Guide
  - HTML
  - Intermediate
  - Learn
  - SVG
translation_of: Learn/HTML/Multimedia_and_embedding/Adding_vector_graphics_to_the_Web
original_slug: Apprendre/HTML/Comment/Ajouter_des_images_vectorielles_à_une_page_web
---
<p>{{LearnSidebar}}<br>
 {{PreviousMenuNext("Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies", "Learn/HTML/Multimedia_and_embedding/Responsive_images", "Learn/HTML/Multimedia_and_embedding")}}</p>

<p>Les graphiques vectoriels sont les images adaptatives par excellence : légères et redimensionnables à volonté. Dans cet article, nous verrons comment intégrer des images vectorielles dans une page web.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Vous devriez au préalable savoir comment <a href="/fr/Apprendre/HTML/Write_a_simple_page_in_HTML">créer un document HTML simple</a> et comment <a href="/fr/Apprendre/HTML/Comment/Ajouter_des_images_à_une_page_web">insérer une image dans un document HTML</a>.</td>
  </tr>
  <tr>
   <th scope="row">Objectifs :</th>
   <td>Apprendre comment intégrer une image SVG dans une page web.</td>
  </tr>
 </tbody>
</table>

<h2 id="Qu'est-ce_que_SVG_Qu'apporte-t-il">Qu'est-ce que SVG ? Qu'apporte-t-il ?</h2>

<p><a href="/fr/docs/Web/SVG">SVG</a> est un langage basé sur {{glossary("XML")}} qui permet de décrire des images vectorielles. Commençons par définir ce qu'est une image vectorielle.</p>

<p>Certaines images (appelées images « <em>matricielles</em> ») sont en fait des tableaux de carrés colorés (appelés pixels). Si on agrandit une image de ce type, à un moment, on arrive à distinguer ces carrés et une ligne diagonale deviendra un « escalier » crénelé.</p>

<p>Au contraire, <strong>les images vectorielles</strong> décrivent des lignes et des formes. On obtient donc une image qui est toujours nette, quelle que soit la résolution de l'écran ou l'agrandissement effectué sur l'image. Une ligne diagonale sera donc toujours lisse. Une seule image source suffit car il est possible de redimensionner l'image avec CSS plutôt qu'en utilisant <code>srcset</code> et <code>sizes</code>.</p>

<p>De plus, les fichiers dans lesquels on stocke les images vectorielles sont beaucoup plus légers que leurs homologues matriciels. Le texte utilisé dans une image vectorielle reste accessible (ce qui peut également être utilisé lors du référencement). Les images SVG se prêtent particulièrement bien aux animations scriptées car chaque composant des images sera représenté dans le {{glossary("DOM")}}.</p>

<p>Il est possible de coder le SVG à la main grâce à un éditeur de texte. En revanche, pour réaliser des images moyennement complexes, il est préférable d'utiliser un éditeur graphique dédié, comme <a href="https://inkscape.org">Inkscape</a>. Malheureusement, les téléphones ne permettent pas de prendre des photos qui soient des images vectorielles mais Inkscape possède une fonctionnalité appelée Trace Bitmap qui permet de passer d'une image matricielle à une image vectorielle. Attention à l'utilisation de fichiers SVG complexes, le traitement de ces fichiers par le navigateur pourra entraîner une baisse des performances.</p>

<div class="note">
<p><strong>Note :</strong> Sous Inkscape, préférez le format « SVG simple » pour sauvegarder vos fichiers, cela permet d'économiser de l'espace. Pour plus d'informations sur la préparation, lire <a href="http://tavmjong.free.fr/INKSCAPE/MANUAL/html/Web-Inkscape.html">cet article qui décrit comment préparer des fichiers SVG pour les utiliser sur le Web</a>.</p>
</div>

<h2 id="La_méthode_rapide_htmlelement(img)">La méthode rapide : {{htmlelement("img")}}</h2>

<p>Vous pouvez simplement faire référence à un fichier SVG au sein de l'élément {{htmlelement("img")}}, comme vous l'auriez fait avec une image matricielle. Il faudra utiliser l'attribut <code>height</code> ou <code>width</code> (voire les deux si le fichier SVG ne possède pas de ratio inhérent). Si ce n'est pas déjà fait, vous pouvez <a href="/fr/Apprendre/HTML/Comment/Ajouter_des_images_à_une_page_web">lire ce tutoriel sur <code>&lt;img&gt;</code></a>.</p>

<pre class="brush: html">&lt;img
    src="equilateral.svg"
    alt="un triangle aux trois côtés égaux"
    height="87px"
    width="100px" /&gt;</pre>

<h3 id="Avantages">Avantages</h3>

<ul>
 <li>Rapide à mettre en œuvre, syntaxe très proche avec les images matricielles, texte alternatif disponible.</li>
 <li>Il est également possible de créer des hyperliens en plaçant l'élément <code>&lt;img&gt;</code> dans un élément {{htmlelement("a")}}.</li>
</ul>

<h3 id="Inconvénients">Inconvénients</h3>

<ul>
 <li>Pour les navigateurs historiques qui existaient avant la démocratisation de SVG (Internet Explorer 8, Android 2.3 et autres), on pourra utiliser une image PNG ou JPG dans l'attribut <code>src</code> en combinaison avec l'attribut {{htmlattrxref("srcset","img")}} :

  <pre class="brush: html">&lt;img src="equilateral.png" alt="un triangle dont tous les côtés sont égaux" srcset="equilateral.svg"/&gt;
</pre>
 </li>
 <li>Il est impossible de manipuler l'image avec JavaScript.</li>
 <li>Si vous souhaitez contrôler le contenu du SVG avec du code CSS, vous devez inclure les styles CSS dans le code SVG (les feuilles de style externes appelées depuis le SVG n'auront aucun effet).</li>
 <li>Il n'est pas possible de remettre l'image en forme avec les pseudo-classes CSS (par exemple <code>:focus</code>).</li>
</ul>

<div class="note">
  <p><strong>Note :</strong></p>
<ul>
 <li>Les images SVG peuvent tout à fait être utilisées comme images d'arrière-plan dans du CSS. Cette méthode possèdera les mêmes limites que celles qui viennent d'être décrites ici (pour la méthode où on intègre une image SVG via <code>&lt;img&gt;</code>).

  <pre class="brush: css">background: url("image-de-secours.png");
background-image: url(image.svg);
background-size: contain;</pre>
 </li>
 <li>Si vos fichiers SVG ne s'affichent pas, cela peut vouloir dire que votre serveur n'est pas correctement paramétré. Dans ce cas, <a href="/fr/docs/Web/SVG/Tutoriel/Premiers_pas#Un_mot_sur_les_serveurs_Web">cet article pourra vous aider à résoudre le problème</a>.</li>
</ul>
</div>

<h2 id="Comment_inclure_une_image_SVG_directement_dans_le_code_du_document">Comment inclure une image SVG directement dans le code du document</h2>

<p>Il suffit d'ouvrir le fichier SVG avec un éditeur de texte, de copier le tout puis de le coller dans le document. Assurez-vous que votre fragment de code commence et finit avec la balise <code><a href="/fr/docs/Web/SVG/Element/svg">&lt;svg&gt;</a></code>. Voici un exemple très simple que vous pouvez directement copier-coller dans votre document :</p>

<pre class="brush: html">&lt;svg width="300" height="200"&gt;
    &lt;rect width="100%" height="100%" fill="green" /&gt;
&lt;/svg&gt;
</pre>

<p>La balise <code>&lt;svg&gt;</code> n'a pas besoin des attributs <code>version</code>, <code>baseProfile</code> ou <code>xmlns</code>. Assurez-vous de bien retirer les déclarations d'espaces de noms (<em>namespace</em>) éventuellement introduites par Inkscape (en effet, HTML ne tolère que les espaces de noms XHTML, XLink, MathML et SVG). Si vous souhaitez optimiser votre fichier de façon plus approfondie, vous pouvez utiliser <a href="http://petercollingridge.appspot.com/svg_optimiser">SVG Optimiser</a> ou <a href="http://www.codedread.com/scour/">Scour</a>.</p>

<h3 id="Avantages_2">Avantages</h3>

<ul>
 <li>Placer le SVG à même le document permet d'économiser une requête HTTP, ce qui peut permettre de réduire le temps de chargement de la page.</li>
 <li>Vous pouvez ajouter des attributs <code>class</code> et <code>id</code> aux éléments SVG pour les mettre en forme grâce à CSS (directement au sein du SVG ou dans les règles liées au document HTML). En fait, <a href="/fr/docs/Web/SVG/Attribute#Attributs_de_pr.C3.A9sentation">chaque attribut de présentation SVG</a> peut être utilisé comme propriété CSS.</li>
 <li>Cette approche est la seule qui permet d'utiliser des interactions CSS (telles que <code>:focus</code>) et des animations CSS. Il faut toutefois noter que les <a href="http://css-tricks.com/guide-svg-animations-smil/">animation SMIL</a> fonctionneront avec toutes les méthodes décrites dans cet article.</li>
 <li>Avec cette méthode, les images SVG peuvent être utilisées comme hyperlien.</li>
</ul>

<h3 id="Inconvénients_2">Inconvénients</h3>

<ul>
 <li>Cette méthode n'est utilisable que si le SVG n'est utilisé qu'à un seul endroit. S'il faut le dupliquer, cela compliquera la maintenance et gaspillera de la mémoire.</li>
 <li>Chaque image SVG augmente la taille du fichier HTML.</li>
 <li>Le navigateur ne peut pas placer ces images SVG en cache comme il pourrait le faire avec d'autres ressources.</li>
 <li>Vous pouvez inclure un contenu à utiliser au cas où le navigateur ne supporte pas le SVG, grâce à {{svgelement("foreignObject")}}. Toutefois, les navigateurs qui supportent SVG téléchargeront quand même les ressources supplémentaires. Il faut donc décider si cette charge supplémentaire est nécessaire pour gérer les anciens navigateurs.</li>
</ul>

<ul>
</ul>

<h2 id="Comment_intégrer_un_SVG_dans_un_élément_htmlelement(object)">Comment intégrer un SVG dans un élément {{htmlelement("object")}}</h2>

<p>Cette syntaxe est assez simple et permet également de définir un contenu à utiliser quand SVG n'est pas supporté :</p>

<pre class="brush: html">&lt;object data="parallelogramme.svg"
    width="300"
    height="250"
    type="image/svg+xml"&gt;

&lt;img src="parallelogramme.png"
    alt="un quadrilatère dont les côtés sont parallèles deux à deux" /&gt;

&lt;/object&gt;

</pre>

<h3 id="Inconvénients_3">Inconvénients</h3>

<ul>
 <li>Là aussi, les navigateurs qui supportent SVG téléchargeront également les ressources alternatives comme les images.</li>
 <li>Les éléments <code>&lt;object&gt;</code> ne peuvent pas être transformés en liens. Le SVG sera affiché mais ne sera pas déclenchable.</li>
 <li>Les éléments SVG peuvent être mis en forme avec CSS mais
  <ul>
   <li>le code SVG doit contenir les règles CSS (par exemple dans un élément <code>&lt;style&gt;</code>) ou</li>
   <li>le fichier SVG doit contenir un lien vers la feuille de style externe. Pour créer ce lien, vous pouvez utiliser ce code, à placer dans le code SVG avant les autres balises :
    <pre class="brush: xml">&lt;?xml-stylesheet type="text/css" href="svg.css" ?&gt;</pre>
    (Attention à ne pas utiliser ce code avec du SVG intégré directement dans le HTML car cela pourrait rendre la page non-fonctionnelle)</li>
  </ul>
 </li>
</ul>

<h2 id="Comment_intégrer_un_SVG_avec_un_élément_htmlelement(iframe)">Comment intégrer un SVG avec un élément {{htmlelement("iframe")}}</h2>

<p>Vous pouvez ouvrir des images SVG dans votre navigateur de la même façon qu'on peut ouvrir des pages web. Intégrer des images SVG dans un élément <code>&lt;iframe&gt;</code> n'est donc qu'une variation de <a href="/fr/Apprendre/HTML/Howto/Embed_a_webpage_within_another_webpage">l'intégration d'une page web dans une autre page web</a>.</p>

<p>Voici un rapide exemple :</p>

<pre class="brush: html">&lt;iframe src="triangle.svg" width="500" height="500" sandbox&gt;
    &lt;img src="triangle.png" alt="Un triangle avec trois côtés inégaux" /&gt;
&lt;/iframe&gt;</pre>

<p><code>iframe</code> permet d'afficher un contenu de secours qui ne sera affiché que si le navigateur ne supporte pas les <code>iframe</code>.</p>

<p>De plus, sauf si le SVG et la page web actuelle ont la même {{glossary('origine')}}, il n'est pas possible d'utiliser JavaScript pour manipuler le SVG depuis la page web.</p>

<h2 id="En_savoir_plus">En savoir plus</h2>

<ul>
 <li>{{htmlelement("iframe")}}</li>
 <li>{{htmlelement("object")}}</li>
 <li>{{htmlelement("img")}}</li>
 <li><a href="/fr/docs/Web/SVG/Tutoriel/Premiers_pas">Le tutoriel SVG</a> sur MDN</li>
 <li><a href="http://thenewcode.com/744/Making-SVG-Responsive">Conseils rapides pour des SVG adaptatifs (en anglais)</a></li>
 <li><a href="http://tympanus.net/codrops/2014/08/19/making-svgs-responsive-with-css/">Le tutoriel de Sara Soueidan sur les images SVG adaptatives (en anglais)</a></li>
 <li><a href="http://www.w3.org/TR/SVG-access/">Les bénéfices du format SVG pour l'accessibilité (en anglais)</a></li>
 <li><a href="https://css-tricks.com/scale-svg/">Comment redimensionner des fichiers SVG (en anglais)</a> (ce n'est pas aussi simple qu'avec les images matricielles)</li>
 <li><a href="http://www.w3.org/TR/SVG/">La spécification SVG</a></li>
</ul>
