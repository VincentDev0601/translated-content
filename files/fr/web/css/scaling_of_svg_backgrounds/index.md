---
title: Redimensionnement d'arrière-plans SVG
slug: Web/CSS/Scaling_of_SVG_backgrounds
tags:
  - CSS
  - Guide
  - SVG
translation_of: Web/CSS/Scaling_of_SVG_backgrounds
original_slug: Web/CSS/Redimensionnement_arrière-plans_SVG
---
<p>Les images SVG sont très flexibles et lorsqu'on les utilise en CSS avec les propriétés {{cssxref("background-image")}} et {{cssxref("background-size")}}, il faut s'assurer de considérer les différents aspects qui leurs sont propres. Dans cet article, on décrit comment les images SVG sont redimensionnées grâce à ces propriétés.</p>

<h2 id="Un_algorithme_simple">Un algorithme simple</h2>

<p>Dans la plupart des cas, l'algorithme utilisé pourra être réduit à ces quatre règles. Ces règles ne sont pas exhaustives et ne couvrent pas certains cas aux limites mais cela sera suffisant ici :</p>

<ol>
 <li>Si {{cssxref("background-size")}} définit une dimension fixe (des pourcentages ou des unités relatives fixées par le contexte), cette dimension l'emporte.</li>
 <li>Si l'image possède des proportions intrinsèques (autrement dit, si le ratio largeur/hauteur est constant : 16:9, 4:3, 2.39:1, 1:1), l'arrière-plan sera affiché en conservant ces proportions.</li>
 <li>Si l'image définit une taille et que celle-ci n'est pas modifiée par une contrainte quelconque, cette taille l'emporte.</li>
 <li>Dans tous les autres cas, l'image est affichée avec la taille de la zone dédiée à l'arrière-plan.</li>
</ol>

<p>On notera ici que l'algorithme ne prend en cas que les dimensions et/ou les proportions de l'image (leur absence éventullement). Ainsi, une image SVG dont les dimensions sont fixées sera traitée comme une image matricielle de la même taille.</p>

<h2 id="Fichiers_dexemples">Fichiers d'exemples</h2>

<p>Avant d'aller plus loin dans l'exploration des résultats avec {{cssxref("background-size")}}, il serait judicieux de disposer de différentes images sources avec différents paramètres de dimensions, proportions, etc.</p>

<p>Pour chaque cas d'exemple fourni ci-après, l'image est affichée dans une boîte carrée de 150 pixels et un lien est fourni vers le fichier SVG correspondant.</p>

<h3 id="Image_sans_dimension_ni_proportion">Image sans dimension ni proportion</h3>

<p>Cette image ne possède ni dimension ni proportion. Quelle que soit sa taille, il n'y aura pas de ratio largeur/hauteur particulier. On a ici une image qui forme un dégradé, quelles que soient les dimensions et la proportion de l'écran.</p>

<p><img src="no-dimensions-or-ratio.png"></p>

<p><a href="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3469/6587a382ffb2c944462a6b110b079496/no-dimensions-or-ratio.svg" title="no-dimensions-or-ratio.svg">Fichier SVG source</a></p>
<h3 id="Image_sans_proportion_avec_une_dimension_fixée">Image sans proportion avec une dimension fixée</h3>

<p>Cette image mesure 100 pixels de large mais n'a pas de hauteur ni de proportion intrinsèque. On a ainsi une bande d'arrière-plan qui peut être étirée sur toute la hauteur d'un bloc.</p>

<p><img src="100px-wide-no-height-or-ratio.png"></p>

<p><a href="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3468/af73bea307a10ffe2559df42fad199e3/100px-wide-no-height-or-ratio.svg" title="100px-wide-no-height-or-ratio.svg">Fichier SVG source</a></p>

<h3 id="Image_avec_une_dimension_fixée_et_des_proportions_intrinsèques">Image avec une dimension fixée et des proportions intrinsèques</h3>

<p>Cette image mesure 100 pixels de haut mais n'a pas de largeur fixée. Elle définit également une proportion de 3:4. Ainsi, le rapport largeur/hauteur sera toujours 3/4.</p>

<p>On a ici un cas très proche de l'image pour laquelle on définit une largeur et une hauteur car, une fois qu'on a une dimension et une proportion, la deuxième dimension est implicite. Cela n'en reste pas moins un exemple utile.</p>

<p><img src="100px-height-3x4-ratio.png"></p>

<p><a href="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3467/fd0c534c506be06d52f0a954a59863a6/100px-height-3x4-ratio.svg" title="100px-height-3x4-ratio.svg">Fichier SVG source</a></p>

<h3 id="Image_sans_largeur_ni_hauteur_mais_avec_des_proportions_intrinsèques">Image sans largeur ni hauteur mais avec des proportions intrinsèques</h3>

<p>Cette image n'indique pas de hauteur ou de largeur mais un ratio intrinsèque de 1:1. On obtiendra toujours un carré (qui pourra être utilisé comme une icône) pour n'importe quelle taille : 32x32, 128x128, or 512x512.</p>

<p><img src="no-dimensions-1x1-ratio.png"></p>

<p><a href="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3466/a3398e03c058d99fb2b7837167cdbc26/no-dimensions-1x1-ratio.svg" title="no-dimensions-1x1-ratio.svg">Fichier SVG source</a></p>

<h2 id="Exemples_de_redimensionnement">Exemples de redimensionnement</h2>

<p>Appliquons maintenant différents redimensionnements sur ces images. Pour chacun des exemples qui suivent, les rectangles dessinés font 300 pixels de large et 200 pixels de haut. De plus, on utilise {{cssxref("background-repeat")}} avec <code>no-repeat</code> pour plus de clarté..</p>

<div class="note">
  <p><strong>Note :</strong> Les images montrées ci-après illustrent le rendu <strong>attendu</strong>. Les navigateurs peuvent ne pas produire le bon résultat.</p>
</div>

<h3 id="Indiquer_des_dimensions_fixées_sur_les_deux_axes">Indiquer des dimensions fixées sur les deux axes</h3>

<p>Si on utilise {{cssxref("background-size")}} pour indiquer la longueur et la largeur de l'image, celles-ci seront toujours utilisées (cf. la règle n°1 précédemment énoncée). Autrement dit, l'image sera toujours étirée pour obtenir ces dimensions, quelles que soient les dimensions initiales de l'image ou ses proportions.</p>

<h4 id="SVG_source_Aucune_dimension_ni_proportion">SVG source : Aucune dimension ni proportion</h4>

<p>Avec ces déclarations CSS :</p>

<pre class="brush: css">background: url(no-dimensions-or-ratio.svg);
background-size: 125px 175px;
</pre>

<p>On doit obtenir un résultat semblable à :</p>

<p><img src="fixed-no-dimensions-or-ratio.png"></p>

<h4 id="SVG_source_Une_dimension_définie_et_aucune_proportion">SVG source : Une dimension définie et aucune proportion</h4>

<p>Avec ces déclarations CSS :</p>

<pre class="brush: css">background: url(100px-wide-no-height-or-ratio.svg);
background-size: 250px 150px;
</pre>

<p>On doit obtenir un résultat semblable à :</p>

<p><img src="fixed-100px-wide-no-height-or-ratio.png"></p>

<h4 id="SVG_source_Une_dimension_définie_et_des_proportions_intrinsèques">SVG source : Une dimension définie et des proportions intrinsèques</h4>

<p>Avec ces déclarations CSS :</p>

<pre class="brush: css">background: url(100px-height-3x4-ratio.svg);
background-size: 275px 125px;
</pre>

<p>On doit obtenir un résultat semblable à :</p>

<p><img src="fixed-100px-height-3x4-ratio.png"></p>

<h4 id="SVG_source_Aucune_largeur_ni_hauteur_définie_mais_des_proportions_intrinsèques">SVG source : Aucune largeur ni hauteur définie mais des proportions intrinsèques</h4>

<p>Avec ces déclarations CSS :</p>

<pre class="brush: css">background: url(no-dimensions-1x1-ratio.svg);
background-size: 250px 100px;
</pre>

<p>On doit obtenir un résultat semblable à :</p>

<p><img src="fixed-no-dimensions-1x1-ratio.png"></p>

<h3 id="Utiliser_contain_ou_cover">Utiliser <code>contain</code> ou <code>cover</code></h3>

<p>En utilisant la valeur <code>cover</code> pour {{cssxref("background-size")}}, l'image sera réduite au maximum pour couvrir toute la zone de l'arrière-plan. <code>contain</code> fonctionne de façon symétrique, l'image est agrandie autant que possible sans être rognée par la zone de l'arrière-plan.</p>

<p>Pour une image avec des proportions intrinsèques, une seule dimension suffira à déterminer la taille pour <code>cover</code>/<code>contain</code>. En revanche, sans ratio, ce n'est pas suffisant et il faut donc utiliser les contraintes de la zone de l'arrière-plan.</p>

<h4 id="SVG_source_Aucune_dimension_ni_proportion_2">SVG source : Aucune dimension ni proportion</h4>

<p>Si une image n'a ni dimensions définie, ni proportions définies, les règles 2 ou 3 ne pourront pas s'appliquer. La règle 4 est donc utilisée et l'image couvre toute la zone (ce qui satisfait d'ailleurs les différentes contraintes).</p>

<pre class="brush: css">background: url(no-dimensions-or-ratio.svg);
background-size: contain;
</pre>

<p>Le résultat obtenu sera :</p>

<p><img src="no-dimensions-or-ratio-contain.png"></p>

<h4 id="SVG_source_Une_dimension_définie_et_aucune_proportion_2">SVG source : Une dimension définie et aucune proportion</h4>

<p>De même si l'image possède une dimension mais aucune proportion, la règle 4 sera appliquée : l'image est ainsi redimensionnée pour couvrir toute la zone.</p>

<pre class="brush: css">background: url(100px-wide-no-height-or-ratio.svg);
background-size: contain;
</pre>

<p>Le résultat obtenu sera :</p>

<p><img src="100px-wide-no-height-or-ratio-contain.png"></p>

<h4 id="SVG_source_Une_dimension_définie_et_des_proportions_intrinsèques_2">SVG source : Une dimension définie et des proportions intrinsèques</h4>

<p>Ici, on a des proportions intrinsèques. Dans ce cas, la règle 1 n'est pas pertinente et on utilise donc la règle 2 : le ratio est conservé (tout en respectant les consignes de <code>contain</code> ou <code>cover</code>). Ainsi, avec <code>contain</code>, la boîte de 300x200 et le ratio de 3:4 entraîneront le dessin d'un arrière-plan de 150x200.</p>

<h5 id="contain"><code>contain</code></h5>

<pre class="brush: css">background: url(100px-height-3x4-ratio.svg);
background-size: contain;
</pre>

<p>Le résultat obtenu sera :</p>

<p><img src="100px-height-3x4-ratio-contain.png"></p>

<p>On voit ici que toute l'image est affichée et est contenue dans la boîte sans être rognée.</p>

<h5 id="cover"><code>cover</code></h5>

<pre class="brush: css">background: url(100px-height-3x4-ratio.svg);
background-size: cover;
</pre>

<p>Le résultat obtenu sera :</p>

<p><img src="100px-height-3x4-ratio-cover.png"></p>

<p>Dans ce cas, le ratio 3:4 est conservé et l'image est étirée Here, the 3:4 ratio is preserved while still stretching the image to fill the entire box. That causes the bottom of the image to be clipped away.</p>

<h4 id="SVG_source_Aucune_dimension_mais_des_proportions_intrinsèques">SVG source : Aucune dimension mais des proportions intrinsèques</h4>

<p>On obtient des résultats analogues lorsqu'on manipule une image sans dimension intrinsèque mais avec des proportions intrinsèques.</p>

<h5 id="contain_2"><code>contain</code></h5>

<pre class="brush: css">background: url(no-dimensions-1x1-ratio.svg);
background-size: contain;
</pre>

<p>Le résultat ressemblera à :</p>

<p><img src="no-dimensions-1x1-ratio-contain.png"></p>

<p>On voit ici que l'image est redimensionnée à la plus petite taille tout en conservant le ratio 1:1.</p>

<h5 id="cover_2"><code>cover</code></h5>

<pre class="brush: css">background: url(no-dimensions-1x1-ratio.svg);
background-size: cover;
</pre>

<p>Le résultat ressemblera à :</p>

<p><img src="no-dimensions-1x1-ratio-cover.png"></p>

<p>Ici, l'image est dimensionnée afin de couvrir la plus grande surface avec le ratio 1:1.</p>

<h3 id="Utiliser_auto_pour_les_deux_axes">Utiliser <code>auto</code> pour les deux axes</h3>

<p>Si {{cssxref("background-size")}} vaut <code>auto</code> ou <code>auto auto</code>, ce sera la règle n°2 qui s'appliquera : les proportions intrinsèques devront être conservées.</p>

<h4 id="SVG_source_Aucune_dimension_ni_proportion_intrinsèque">SVG source : Aucune dimension ni proportion intrinsèque</h4>

<p>Lorsque l'image n'a aucune proportion ni dimension, ce sera la dernière règle qui s'appliquera : l'image couvrira toute la surface de la zone.</p>

<pre class="brush: css">background: url(no-dimensions-or-ratio.svg);
background-size: auto auto;
</pre>

<p>Voici le résultat obtenu :</p>

<p><img src="auto-no-dimensions-or-ratio.png"></p>

<h4 id="SVG_source_une_dimension_mais_aucune_proportion_intrinsèque">SVG source : une dimension mais aucune proportion intrinsèque</h4>

<p>S'il n'y a aucune proportion définie mais qu'une dimension est fournie, la règle n°3 s'appliquera et l'image sera affichée avec ces dimensions.</p>

<pre class="brush: css">background: url(100px-wide-no-height-or-ratio.svg);
background-size: auto auto;
</pre>

<p>Voici le résultat obtenu :</p>

<p><img src="auto-100px-wide-no-height-or-ratio.png"></p>

<p>Ici, on voit que la largeur définie par le fichier SVG (100 pixels) est respectée. L'image s'étend sur toute la hauteur de la zone de l'arrière-plan car elle n'est pas définie (explicitement dans les déclarations ou intrinsèquement via l'image).</p>

<h4 id="SVG_source_une_dimension_et_des_proportions_intrinsèques">SVG source : une dimension et des proportions intrinsèques</h4>

<p>Si on dispose de proportions intrinsèques et d'une dimension fixée, les deux dimensions sont alors définies.</p>

<pre class="brush: css">background: url(100px-height-3x4-ratio.svg);
background-size: auto auto;
</pre>

<p>Le résultat sera le suivant :</p>

<p><img src="auto-100px-height-3x4-ratio.png"></p>

<p>Cette image mesure 100 pixels de haut et possède des proportions intrinsèques avec un ratio de 3:4. La largeur vaut donc 75 pixels et c'est ainsi qu'elle est affichée avec <code>auto</code>.</p>

<h4 id="SVG_source_Aucune_dimension_définie_mais_des_proportions_intrinsèques">SVG source : Aucune dimension définie mais des proportions intrinsèques</h4>

<p>Lorsqu'un ratio s'applique sans dimension, c'est la règle n°2 qui s'applique. L'image est affichée comme pour <code>contain</code>.</p>

<pre class="brush: css">background: url(no-dimensions-1x1-ratio.svg);
background-size: auto auto;
</pre>

<p>Le résultat ressemblera à :</p>

<p><img src="auto-no-dimensions-1x1-ratio.png"></p>

<h3 id="Utiliser_auto_et_une_dimension_fixée">Utiliser <code>auto</code> et une dimension fixée</h3>

<p>Avec la première règle, les dimensions définies sont toujours utilisées et il faut donc utiliser les autres règles pour déterminer la seconde dimension.</p>

<h4 id="SVG_source_aucune_dimension_ni_proportion_intrinsèque">SVG source : aucune dimension ni proportion intrinsèque</h4>

<p>Si l'image ne possède ni dimension ni proportion intrinsèque, c'est la règle 4 qui s'applique et les dimensions de la zone pour l'arrière-plan seront utilisées pour <code>auto</code>.</p>

<pre class="brush: css">background: url(no-dimensions-or-ratio.svg);
background-size: auto 140px;
</pre>

<p><img src="1auto-no-dimensions-or-ratio.png"></p>

<p>Ici, la largeur est déterminée grâce à la zone dédiée à l'arrière-plan (règle n°4) et la hauteur est indiquée via la feuille de style (140px).</p>

<h4 id="SVG_source_une_dimension_intrinsèque_mais_pas_de_proportion_intrinsèque">SVG source : une dimension intrinsèque mais pas de proportion intrinsèque</h4>

<p>Si l'image possède une dimension implicite mais pas de ratio, la dimension définie sera utilisée selon la règle n°3 si elle vaut <code>auto</code> dans le code CSS.</p>

<pre class="brush: css">background: url(100px-wide-no-height-or-ratio.svg);
background-size: 200px auto;
</pre>

<p><img src="100px-wide-no-height-or-ratio-length-auto.png"></p>

<p>Ici, la valeur de 200px fournie dans la feuille de style surcharge la valeur de 100px définie dans le fichier SVG. Puisqu'il n'y a aucune proportion intrinsèque ni hauteur de définie et qu'on utilise la valeur <code>auto</code>, l'image fera la même hauteur que la zone pour l'arrière-plan.</p>

<pre class="brush: css">background: url(100px-wide-no-height-or-ratio.svg);
background-size: auto 125px;
</pre>

<p><img src="100px-wide-no-height-or-ratio-auto-length.png"></p>

<p>Ici, c'est la largeur qui vaut <code>auto</code> et ce sera donc la valeur définie dans l'image SVG (100px) qui sera utilisée. La hauteur est fixée à 125 pixels via la feuille de style.</p>

<h4 id="SVG_source_une_dimension_définie_et_des_proportions_intrinsèques">SVG source : une dimension définie et des proportions intrinsèques</h4>

<p>Lorsqu'une dimension est indiquée, la première règle s'applique et la dimension du fichier SVG est utilisée sauf si le CSS la redéfinit. Lorsqu'un ratio est indiqué, celui-ci est utilisé pour déterminer la deuxième dimension.</p>

<pre class="brush: css">background: url(100px-height-3x4-ratio.svg);
background-size: 150px auto;
</pre>

<p><img src="1auto-100px-height-3x4-ratio.png"></p>

<p>Ici, la hauteur de l'image a été surchargée pour valoir 150px. Les proportions intrinsèques permettent ensuite de définir la largeur (<code>auto</code> dans la feuille de style).</p>

<h4 id="SVG_source_aucune_dimension_mais_des_proportions_intrinsèques">SVG source : aucune dimension mais des proportions intrinsèques</h4>

<p>Si aucune dimension n'est définie dans l'image SVG, ce sera celle du CSS qui sera appliquée. Les proportions intrinsèques sont ensuite utilisées pour déterminer l'autre dimension (selon la rgèle n°2).</p>

<pre class="brush: css">background: url(no-dimensions-1x1-ratio.svg);
background-size: 150px auto;
</pre>

<p><img src="1auto-no-dimensions-1x1-ratio.png"></p>

<p>La largeur est définie à 150 pixels via la feuille de style et la hauteur est calculée à partir de cette largeur en utilisant le ratio 1:1, elle vaudra donc 150px ce qui donnera le résultat ci-dessus.</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{cssxref("background-size")}}</li>
 <li>{{cssxref("background-image")}}</li>
 <li>Billet de blog de Jeff Walden : <a href="https://whereswalden.com/2011/10/21/properly-resizing-vector-image-backgrounds/">Properly resizing vector image backgrounds (en anglais)</a></li>
</ul>
