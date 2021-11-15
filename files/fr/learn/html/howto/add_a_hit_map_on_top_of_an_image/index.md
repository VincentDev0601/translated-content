---
title: Ajouter une carte de zones cliquables sur une image
slug: Learn/HTML/Howto/Add_a_hit_map_on_top_of_an_image
tags:
  - Guide
  - HTML
  - Intermediate
  - Navigation
translation_of: Learn/HTML/Howto/Add_a_hit_map_on_top_of_an_image
original_slug: Apprendre/HTML/Comment/Ajouter_carte_zones_cliquables_sur_image
---
<p>Dans cet article, nous verrons comment construire une carte imagée cliquable en commençant par les inconvénients de cette méthode.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Vous devez au préalable savoir comment <a href="/fr/Apprendre/HTML/Écrire_une_simple_page_HTML">créer un document HTML simple</a> et connaître comment <a href="/fr/Apprendre/HTML/Comment/Ajouter_des_images_à_une_page_web">ajouter des images accessibles à une page web.</a></td>
  </tr>
  <tr>
   <th scope="row">Objectifs :</th>
   <td>Apprendre comment faire pour que différentes zones d'une même image pointent vers différentes pages.</td>
  </tr>
 </tbody>
</table>

<div class="warning">
<p><strong>Attention :</strong> Cet article n'aborde que les cartes générées côté client. Les cartes de zones générées côté serveur ne doivent pas être utilisée car elles ne sont accessibles qu'aux utilisateurs ayant des souris.</p>
</div>

<h2 id="Les_cartes_imagées_cliquables_et_leurs_inconvénients">Les cartes imagées cliquables et leurs inconvénients</h2>

<p>Lorsque vous imbriquez une image dans un élément {{htmlelement("a")}}, l'image entière pointe vers une page web. En revanche, les cartes imagées contiennent plusieurs régions (aussi appelées « <em>hotspots</em> » en anglais) qui pointent chacunes vers une ressource distincte.</p>

<p>Auparavant, les cartes imagées était assez populaires mais, malgré cette popularité, elles posent quelques problèmes en termes de performances et d'accessibilité.</p>

<p><a href="/fr/Apprendre/HTML/Comment/Créer_un_hyperlien">Les liens textuels</a> (éventuellement mis en formes avec CSS) sont préférables à ces cartes car ils sont plus légers, plus faciles à maintenir, plus utiles pour le référencement et qu'ils sont supportés par les outils d'accessibilité.</p>

<h2 id="Comment_insérer_une_carte_imagée">Comment insérer une carte imagée</h2>

<h3 id="Étape_1_l'image">Étape 1 : l'image</h3>

<p>N'importe quelle image ne fera pas l'affaire pour construire une telle carte.</p>

<ul>
 <li>L'image doit indiquer de façon claire ce qui doit se passer quand les visiteurs suivent les liens des différentes zones (le texte contenu dans l'attribut <code>alt</code> est bien entendu obligatoire mais de nombreux visiteurs ne le verront pas).</li>
 <li>L'image doit indiquer de façon claire où commencent et où se terminent les différentes régions.</li>
 <li>Les différentes zones de la cartes doivent être suffisamment grandes pour qu'on puisse cliquer ou appuyer dessus, quelle que soit la taille de l'écran utilisé. <a href="http://uxmovement.com/mobile/finger-friendly-design-ideal-mobile-touch-target-sizes/">Une image de 72 pixels CSS de long et de large</a> est un minimum acceptable (pour voir le problème posé par de trop petites régions : <a href="http://www.goethe-verlag.com/book2/">50languages.com</a>, où les grandes régions sont suffisamment grande mais où, pour l'Albanie et l'Estonie, c'est beaucoup plus compliqué</li>
</ul>

<p>On insère une image <a href="http://developer.mozilla.org/en-US/Learn/HTML/Howto/Add_images_to_a_webpage">de la même façon que d'habitude</a> (avec un élément {{htmlelement("img")}} et un texte dans l'attribut {{htmlattrxref("alt",'img')}}). Si l'image n'est présente qu'à des fins de navigations, <code>alt</code> peut être laissé vide : <code>alt=""</code>, si les valeurs pour les différents {{htmlattrxref("alt",'area')}} sont bien renseignés dans les éléments {{htmlelement('area')}} que nous allons présenter.</p>

<p>Cette image contiendra une attribut spécial {{htmlattrxref("usemap","img")}}. Celui-ci doit désigner avec un nom unique et sans espace la carte imagée. C'est ce nom qu'on placera dans cet attribut <code>usemap</code> :</p>

<pre class="brush: html">&lt;img
  src="image-map.png"
  alt=""
  usemap="#exemple-map-1" /&gt;
</pre>

<h3 id="Étape_2_Activer_les_régions_actives">Étape 2 : Activer les régions actives</h3>

<p>Dans cette étape, nous allons remplir le code de l'élément {{htmlelement('map')}}. Celui-ci n'a besoin que d'un seul attribut : {{htmlattrxref("name","map")}} dont la valeur doit correspondre à celle utilisée pour l'attribut <code>usemap</code> vue juste avant :</p>

<pre class="brush: html">&lt;map name="exemple-map-1"&gt;

&lt;/map&gt;
</pre>

<p>Dans cet élément <code>&lt;map&gt;</code>, on aura besoin d'utiliser les éléments {{htmlelement('area')}}. Chacun de ces éléments correspondra à une région donnée. Afin que la navigation au clavier reste intuitive, il faudra veiller à ce que l'ordre de ces éléments HTML corresponde bien à l'ordre visuel des régions.</p>

<p>Les éléments <code>&lt;area&gt;</code> sont des éléments vides mais qui utilisent quatres attributs :</p>

<dl>
 <dt>{{htmlattrxref('shape','area')}}</dt>
 <dt>{{htmlattrxref('coords','area')}}</dt>
 <dd>
 <p><code>shape</code> (« forme » en anglais) prend l'une de ces quatre valeurs : <code>circle</code> (pour un cercle), <code>rect</code> (pour un rectangle), <code>poly</code> (pour un polygone) ou <code>default</code> (une zone <code>default</code> occupera l'image entière à laquelle on aura retiré les autres zones déjà définies). La forme choisie détermine les informations de coordonnées qui seront utiles dans <code>coords</code>.</p>

 <ul>
  <li>Pour un cercle (<code>circle</code>) : on fournira les coordonnées X/Y du centre, suivies par la longueur du rayon.</li>
  <li>Pour un rectange (<code>rect</code>) : on fournira les coordonnées X/Y des coins haut/gauche et bas/droite.</li>
  <li>Pour un polygone (<code>poly</code>) : on fournira les coordonnées X/Y de chacun des sommets (et donc au moins six valeurs).</li>
 </ul>

 <p>Les coordonnées exprimées sont données en pixels CSS.</p>

 <p>Dans le cas où les définitions de certaines régions se chevauchent, ce sera l'ordre des zones qui donnera la priorité.</p>
 </dd>
 <dt>{{htmlattrxref('href','area')}}</dt>
 <dd>Cet attribut est l'URL de la ressource vers laquelle on crée un lien. Elle peut être laissée vide si on ne souhaite pas créer de lien pour cette région.</dd>
 <dt>{{htmlattrxref('alt','area')}}</dt>
 <dd>
 <p>Un attribut obligatoire qui indique aux personnes la direction ou le rôle du lien. Ce texte <code>alt</code> ne sera affiché que lorsque l'image ne sera pas disponible. Pour plus d'informations, voir <a href="/fr/Apprendre/HTML/Comment/Créer_un_hyperlien#Écrire_des_liens_accessibles">nos conseils pour écrire des hyperliens accessibles.</a></p>

 <p>Vous pouvez écrire <code>alt=""</code> si l'attribut <code>href</code> est vide <em>et</em> que l'image entière possède déjà un attribut <code>alt</code> renseigné.</p>
 </dd>
</dl>

<pre class="brush: html">&lt;map name="exemple-map-1"&gt;
  &lt;area shape="circle" coords="200,250,25"
    href="page-2.html" alt="exemple de cercle" /&gt;

  &lt;area shape="rect" coords="10, 5, 20, 15"
    href="page-3.html" alt="exemple de rectangle" /&gt;

&lt;/map&gt;</pre>

<h3 id="Étape_3_S'assurer_que_la_carte_fonctionne_pour_chacun">Étape 3 : S'assurer que la carte fonctionne pour chacun</h3>

<p>Ce n'est pas encore fini. Il est nécessaire de s'assurer que la carte fonctionne bien sur différents navigateurs et appareils. Vous pouvez essayer de naviguer en utilisant uniquement de clavier. Vous pouvez également désactiver les images.</p>

<p>Si votre carte imagée mesure plus de 240px environ, vous devrez réfléchir à comment l'ajuster pour que celle-ci soit adaptative. Il ne suffira pas de redimensionner l'image pour les écrans plus petits car les coordonnées qui resteraient les mêmes ne correspondraient plus aux différents points de l'image.</p>

<p>Si vous devez nécessairement utiliser de telles cartes, vous pouvez regarder <a href="https://github.com/stowball/jQuery-rwdImageMaps">ce plugin jQuery réalisé par Matt Stow.</a> Dudley Storey illustre une méthode qui consiste à <a href="http://thenewcode.com/696/Using-SVG-as-an-Alternative-To-Imagemaps">utiliser SVG pour réaliser un effet de carte imagée</a> ainsi qu'une bidouille pour les images matricielles avec <a href="http://thenewcode.com/760/Create-A-Responsive-Imagemap-With-SVG">une combinaison de SVG</a>.</p>

<h2 id="En_savoir_plus">En savoir plus</h2>

<ul>
 <li>{{htmlelement("img")}}</li>
 <li>{{htmlelement("map")}}</li>
 <li>{{htmlelement("area")}}</li>
 <li><a href="http://www.maschek.hu/imagemap/imgmap">Un éditeur de carte de zones en ligne (en anglais)</a></li>
 <li><a href="http://blog.goolara.com/2014/06/05/image-maps-revisited/">Des conseils sur comment gérer les cartes pour des clients mail (en anglais)</a></li>
</ul>
