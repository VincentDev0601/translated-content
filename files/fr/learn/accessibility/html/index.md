---
title: 'HTML : une bonne base pour l''accessibilité'
slug: Learn/Accessibility/HTML
tags:
  - Accessibilité
  - Article
  - Clavier
  - Débutant
  - Forms
  - HTML
  - Liens
  - a11y
  - boutons
  - sémantique
translation_of: Learn/Accessibility/HTML
original_slug: Apprendre/a11y/HTML
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenuNext("Learn/Accessibility/What_is_Accessibility","Learn/Accessibility/CSS_and_JavaScript", "Learn/Accessibility")}}</div>

<p>Une grande partie des contenus web peut être rendue accessible simplement en s'assurant d'utiliser les éléments HTML appropriés systématiquement. Cet article détaille comment HTML peut être utilisé pour un maximum d'accessibilité.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Compétences informatiques de base, compréhension basique de HTML (voir<a href="/fr/Apprendre/HTML/Introduction_à_HTML"> </a><a href="/fr/docs/Learn/HTML/Introduction_to_HTML">I</a><a href="/fr/Apprendre/HTML/Introduction_à_HTML">ntroduction à HTML</a>), et compréhension de <a href="/fr/docs/Apprendre/a11y/What_is_accessibility"> Qu'est ce que l'accessibilité ?</a></td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Se familiariser avec les fonctionnalités de HTML qui bénéficient à l'accessibilité, et comment les utiliser de manière appropriée dans vos documents web.</td>
  </tr>
 </tbody>
</table>

<h2 id="HTML_et_accessibilité">HTML et accessibilité</h2>

<p>Plus vous apprenez le HTML — plus vous lisez de ressources, regardez d'exemples — plus vous recontrerez un thème récurrent : l'importance d'utiliser du HTML sémantique, parfois appelé POSH (Plain Old Semantic HTML). C'est l'usage des éléments HTML appropriés autant que possible.</p>

<p>Vous pouvez vous demander pourquoi c'est si important. Après tout, vous pouvez utiliser une combinaison de CSS et de JavaScript pour faire fonctionner n'importe quel élément HTML de la manière que vous souhaitez. Par exemple, un bouton de lecture pour une vidéo sur votre site pourrait être codé ainsi :</p>

<pre class="brush: html">&lt;div&gt;Lire la vidéo&lt;/div&gt;</pre>

<p>Mais comme vous le verrez en détail plus loin, il est beaucoup plus sensé d'utiliser le bon élément à cet effet :</p>

<pre class="brush: html">&lt;button&gt;Lire la vidéo&lt;/button&gt;</pre>

<p>Non seulement  <code>&lt;button&gt;</code> possède des styles adéquats par défaut (que vous voudrez probablement surcharger), il intègre aussi l'accès au clavier — on peut tabuler dessus, et l'activer avec la touche entrée.</p>

<p>Le HTML sémantique ne demande pas plus de temps à écrire que du (mauvais) balisage non-sémantique si vous le faites de manière constante dès le début de votre projet, et il a également des bénéfices au delà de l'accessibilité :</p>

<ol>
 <li><strong>Facilite les développements</strong> — comme mentionné ci-dessus, certaines fonctionnalités sont gratuites, et c'est indiscutablement plus compréhensible.</li>
 <li><strong>Meilleur pour le mobile</strong> — le HTML sémantique est indiscutablement plus léger en la taille du fichier que le code spaghetti non sémantique, et plus aisé à rendre responsive. </li>
 <li><strong>Bon pour le SEO</strong> — les moteurs de recherche donnent plus d'importance aux mots clés contenus dans les titres, liens, etc. que des mots-clés contenus dans des <code>&lt;div&gt;</code> non sémantiques, et donc vos documents seront plus facilement trouvés par vos clients.</li>
</ol>

<p>Continuons et jetons un œil au HTML accessible dans le détail.</p>

<div class="note">
<p><strong>Note :</strong> C'est une bonne idée d'avoir un lecteur d'écran configuré, pour tester les exemples ci-dessous. Voir notre guide pour <a href="/fr/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibilité#Screenreaders">gérer les problèmes courants d'accessibilité</a> pour plus de détails.</p>
</div>

<h2 id="Une_bonne_sémantique">Une bonne sémantique</h2>

<p>Nous avons déjà parlé de l'importance d'une bonne sémantique, et pourquoi nous devons utiliser le bon élément HTML pour le bon usage. Il ne faut pas l'ignorer car c'est une des principales causes d'importants problèmes d'accessibilité si ce n'est pas fait correctement.</p>

<p>En vérité sur le Web, les développeurs font d'étranges choses avec HTML. Certains abus en HTML sont hérités de vieilles pratiques obsolètes pas complètement oubliées, d'autre sont juste de l'ignorance. Dans tous les cas, vous devez remplacer ce mauvais code partout où vous le verrez, dès que vous le pourrez.</p>

<p>Parfois vous ne pourrez pas vous débarrasser du mauvais balisage — vos pages seront générées par quelque framework côté serveur dont vous n'aurez pas le contrôle total, ou vous aurez des contenus tiers (comme des bannières publicitaires) que nous ne contrôlerez pas.</p>

<p>L'objectif cependant n'est pas « tout ou rien » — toute amélioration que vous pouvez faire aidera la cause de l'accessibilité.</p>

<h3 id="Contenus_textuels">Contenus textuels</h3>

<p>L'une des meilleures aides en accessibilité qu'un utilisateur de lecteur d'écran peut avoir est une bonne structure des titres, paragraphes, listes, etc. Un bon exemple sémantique devrait ressembler au code suivant :</p>

<pre class="brush: html example-good">&lt;h1&gt;Mon titre&lt;/h1&gt;

&lt;p&gt;Ceci est la premère section de mon document.&lt;/p&gt;

&lt;p&gt;Je vais ajouter ici un autre paragraphe.&lt;/p&gt;

&lt;ol&gt;
  &lt;li&gt;Voici&lt;/li&gt;
  &lt;li&gt;une liste pour&lt;/li&gt;
  &lt;li&gt;toi à lire.&lt;/li&gt;
&lt;/ol&gt;

&lt;h2&gt;Mon sous-titre&lt;/h2&gt;

&lt;p&gt;Ceci est la première sous-section de mon document. J'aurais aimé que les gens puissent trouver ce contenu!&lt;/p&gt;

&lt;h2&gt;Mon second sous-titre&lt;/h2&gt;

&lt;p&gt;Ceci est la seconde sous-section de mon document. Je pense qu'elle est plus intéressante que la dernière.&lt;/p&gt;</pre>

<p>Nous avons préparé pour vous une version avec un texte plus long afin de l'essayer avec lecteur d'écran (voir <a href="https://mdn.github.io/learning-area/accessibility/html/good-semantics.html">la bonne sémantique</a>). Si vous essayez de naviguer dans ce document, vous verrez qu'il est assez simple de s'y retrouver :</p>

<ol>
 <li>Le lecteur d'écran lit à voix haute chaque élément au fur et à mesure que vous progressez dans le contenu, vous notifiant ce qui est un paragraphe, ce qui est un titre, etc.</li>
 <li>Il s'arrête après chaque élément, vous laissant aller à n'importe quel endroit vous convenant.</li>
 <li>Vous pouvez sauter au précédent ou au prochain titre avec de nombreux lecteurs d'écran.</li>
 <li>Vous pouvez aussi dresser une liste de tous les titres avec de nombreux lecteurs d'écrans, vous permettant de les utiliser comme une table des matières pratique pour trouver un contenu spécifique.</li>
</ol>

<p>Les gens écrivent parfois des titres, des paragraphes, etc. utilisant le HTML de présentation et retours à la ligne, quelque chose comme ce qui suit :</p>

<pre class="brush: html example-bad">&lt;font size="7"&gt;Mon titre&lt;/font&gt;
&lt;br&gt;&lt;br&gt;
Ceci est la première section de mon document.
&lt;br&gt;&lt;br&gt;
Je vais ajouter ici un autre paragraphe.
&lt;br&gt;&lt;br&gt;
1. Voici
&lt;br&gt;&lt;br&gt;
2. une liste pour
&lt;br&gt;&lt;br&gt;
3. toi à lire.
&lt;br&gt;&lt;br&gt;
&lt;font size="5"&gt;Mon sous-titre&lt;/font&gt;
&lt;br&gt;&lt;br&gt;
&lt;p&gt;Ceci est la première sous-section de mon document. J'aurais aimé que les gens puissent trouver ce contenu!
&lt;br&gt;&lt;br&gt;
&lt;font size="5"&gt;My 2nd subheading&lt;/font&gt;
&lt;br&gt;&lt;br&gt;
Ceci est la seconde sous-section de mon document. Je pense qu'elle est plus intéressante que la dernière.</pre>

<p>Si vous essayez notre version plus longue avec un lecteur d'écran (voir <a href="https://mdn.github.io/learning-area/accessibility/html/bad-semantics.html">la mauvaise sémantique</a>), vous n'aurez pas une très bonne expérience – le lecteur d'écran n'a plus rien à utiliser comme indicateur, il ne peut pas récupérer une table des matières utilisable, et la page entière est vue comme un bloc unique, lu tout d'une traite.</p>

<p>Il y a aussi d'autres problèmes au-delà de l'accessibilité – le contenu est plus dur à mettre en forme avec le CSS, ou à manipuler avec JavaScript par exemple, car il n'y a pas d'élément à utiliser comme sélecteurs.</p>

<h4 id="Utiliser_un_langage_clair">Utiliser un langage clair</h4>

<p>Le langage que vous employez peut aussi affecter l'accessiblité. En général vous ne devriez pas utiliser un langage trop complexe, ni utiliser un jargon ou de l'argot inutiles. Cela ne profite pas qu'aux gens avec des handicaps congnitifs ou autres ; cela profite au lecteur pour qui le texte n'est pas écrit dans sa langue maternelle, pour des gens plus jeunes… à tout un chacun en fait ! Mis à part cela, vous devriez essayer d'éviter d'utiliser un langage et des caractères qui ne sont pas lus clairement à voix haute par le lecteur d'écran. Par exemple :</p>

<ul>
 <li>N'utilisez pas des tirets si vous le pouvez. Au lieu d'écrire 5–7, écrivez 5 à 7.</li>
 <li>Explicitez les abréviations — au lieu d'écrire Jan, écrivez Janvier.</li>
 <li>Explicitez les acronymes, au moins une ou deux fois. Au lieu d'écrire "HTML" en premier lieu, écrivez Hypertext Markup Language.</li>
</ul>

<h3 id="Disposition_des_pages">Disposition des pages</h3>

<p>Dans les âges sombres, les gens avaient pour habitude de créer les dispositions de leurs pages avec des tableaux HTML — en utilisant différentes cellules de ces tableaux pour contenir l'en-tête, le pied de page, une barre latérale, la colonne du contenu principal, etc. Ce n'est pas une bonne idée car un lecteur d'écran va donner des lectures déroutantes, surtout si la disposition est complexe et a de nombreux tableaux imbriqués.</p>

<p>Essayez notre exemple <a href="http://mdn.github.io/learning-area/accessibility/html/table-layout.html">table-layout.html</a>, qui ressemble à quelque chose comme ça :</p>

<pre class="brush: html">&lt;table width="1200"&gt;
      &lt;!-- main heading row --&gt;
      &lt;tr id="heading"&gt;
        &lt;td colspan="6"&gt;

          &lt;h1 align="center"&gt;Header&lt;/h1&gt;

        &lt;/td&gt;
      &lt;/tr&gt;
      &lt;!-- nav menu row  --&gt;
      &lt;tr id="nav" bgcolor="#ffffff"&gt;
        &lt;td width="200"&gt;
          &lt;a href="#" align="center"&gt;Home&lt;/a&gt;
        &lt;/td&gt;
        &lt;td width="200"&gt;
          &lt;a href="#" align="center"&gt;Our team&lt;/a&gt;
        &lt;/td&gt;
        &lt;td width="200"&gt;
          &lt;a href="#" align="center"&gt;Projects&lt;/a&gt;
        &lt;/td&gt;
        &lt;td width="200"&gt;
          &lt;a href="#" align="center"&gt;Contact&lt;/a&gt;
        &lt;/td&gt;
        &lt;td width="300"&gt;
          &lt;form width="300"&gt;
            &lt;input type="search" name="q" placeholder="Search query" width="300"&gt;
          &lt;/form&gt;
        &lt;/td&gt;
        &lt;td width="100"&gt;
          &lt;button width="100"&gt;Go!&lt;/button&gt;
        &lt;/td&gt;
      &lt;/tr&gt;
      &lt;!-- spacer row --&gt;
      &lt;tr id="spacer" height="10"&gt;
        &lt;td&gt;

        &lt;/td&gt;
      &lt;/tr&gt;
      &lt;!-- main content and aside row --&gt;
      &lt;tr id="main"&gt;
        &lt;td id="content" colspan="4" bgcolor="#ffffff"&gt;

          &lt;!-- main content goes here --&gt;
        &lt;/td&gt;
        &lt;td id="aside" colspan="2" bgcolor="#ff80ff" valign="top"&gt;
          &lt;h2&gt;Related&lt;/h2&gt;

          &lt;!-- aside content goes here --&gt;

        &lt;/td&gt;
      &lt;/tr&gt;
      &lt;!-- spacer row --&gt;
      &lt;tr id="spacer" height="10"&gt;
        &lt;td&gt;

        &lt;/td&gt;
      &lt;/tr&gt;
      &lt;!-- footer row --&gt;
      &lt;tr id="footer" bgcolor="#ffffff"&gt;
        &lt;td colspan="6"&gt;
          &lt;p&gt;©Copyright 2050 by nobody. All rights reversed.&lt;/p&gt;
        &lt;/td&gt;
      &lt;/tr&gt;
    &lt;/table&gt;</pre>

<p>Si vous essayez de naviguer à l'aide d'un lecteur d'écran, cela vous indiquera probablement qu'il existe un tableau à examiner (bien que certains lecteurs d'écran puissent deviner la différence entre les présentations de tableau et les tableaux de données). Vous devrez ensuite (en fonction du lecteur d’écran que vous utilisez) devoir accéder à la table en tant qu’objet et en examiner les caractéristiques séparément, puis sortir à nouveau de la table pour continuer à naviguer dans le contenu.</p>

<p>Les structures de table sont un vestige du passé – elles semblaient logiques lorsque le support CSS n’était pas répandu dans les navigateurs, mais elles semaient la confusion chez les utilisateurs de lecteurs d’écran, tout en étant mauvaises pour de nombreuses autres raisons (utilisation abusive des tableaux, nécessite plus de balisage, design manquant de souplesse). Ne les utilisez pas !</p>

<p>Vous pouvez vérifier ces affirmations en comparant votre expérience antérieure avec un  <a href="https://mdn.github.io/learning-area/html/introduction-to-html/document_and_website_structure/">exemple plus moderne de structure de site Web</a>, qui pourrait ressembler à ceci :</p>

<pre class="brush: html">&lt;header&gt;
  &lt;h1&gt;Entête&lt;/h1&gt;
&lt;/header&gt;

&lt;nav&gt;
  &lt;!--  navigation principale ici  --&gt;
&lt;/nav&gt;

&lt;!--  Voici le contenu principal de notre page  --&gt;
&lt;main&gt;

  &lt;!--  Il contient un article  --&gt;
  &lt;article&gt;
    &lt;h2&gt;Intitulé de l'article&lt;/h2&gt;

    &lt;!--  contenu de l'article ici  --&gt;
  &lt;/article&gt;

  &lt;aside&gt;
    &lt;h2&gt;en relation&lt;/h2&gt;

    &lt;!--  à part le contenu ici  --&gt;
  &lt;/aside&gt;

&lt;/main&gt;

&lt;!--  Et voici notre pied de page principal utilisé dans toutes les pages de notre site Web. --&gt;

&lt;footer&gt;
  &lt;!--  contenu du pied de page ici  --&gt;
&lt;/footer&gt;</pre>

<p>Si vous essayez notre exemple plus moderne de structure avec un lecteur d’écran, vous verrez que le balisage de présentation ne gêne plus ni ne rend la lecture du contenu confuse. Il est également beaucoup plus léger et plus petit en termes de taille de code, ce qui signifie une maintenance plus facile du code et une sollicitation moindre de la bande passante par l'utilisateur (particulièrement critique en cas de connexions lentes).</p>

<p>Une autre considération à prendre en compte lors de la création de dispositions consiste à utiliser des éléments sémantiques HTML5 comme dans l'exemple ci-dessus (voir <a href="/fr/docs/Web/HTML/Element#Content_sectioning">Référence des éléments HTML</a>). Vous pouvez créer une disposition en utilisant uniquement des éléments {{htmlelement("div")}} imbriqués, mais il est préférable d'utiliser des éléments de sectionnement appropriés pour envelopper votre navigation principale ({{htmlelement("nav")}}), footer ({{htmlelement("footer")}}), en répétant des unités de contenu ({{htmlelement("article")}}),  etc. Elles fournissent une sémantique supplémentaire aux lecteurs d’écran (et à d’autres outils) pour donner à l’utilisateur des indices supplémentaires sur le contenu qu’il navigue (voir <a href="http://www.weba11y.com/blog/2016/04/22/screen-reader-support-for-new-html5-section-elements/">Prise en charge du lecteur d’écran pour les nouveaux éléments de section HTML5</a> pour une idée de la prise en charge du lecteur d’écran).</p>

<div class="note">
<p><strong>Note :</strong> Outre le fait que votre contenu présente une bonne sémantique et une présentation attrayante, il convient que son ordre source soit logique : vous pouvez toujours le placer où vous le souhaitez à l'aide de CSS par la suite, mais vous devez définir l'ordre exact des sources pour commencer. les utilisateurs de lecteur d’écran qui se liront auront du sens.</p>
</div>

<h3 id="Contrôles_de_linterface_utilisateur">Contrôles de l'interface utilisateur</h3>

<p>Par contrôles d'interface utilisateur, nous entendons les parties principales des documents web avec lesquelles les utilisateurs interagissent – le plus souvent des boutons, des liens et des contrôles de formulaire. Dans cette section, nous examinerons les problèmes d’accessibilité de base à prendre en compte lors de la création de tels contrôles. Des articles ultérieurs sur WAI-ARIA et le multimédia aborderont d'autres aspects de l'accessibilité de l'interface utilisateur.</p>

<p>L'un des aspects clés de l'accessibilité des contrôles de l'interface utilisateur est que, par défaut, les navigateurs leur permettent d'être manipulés par le clavier. Vous pouvez essayer ceci en utilisant notre exemple <a href="https://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/native-keyboard-accessibility.html">accessibilité du clavier natif</a> (voir le <a href="https://github.com/mdn/learning-area/blob/master/tools-testing/cross-browser-testing/accessibility/native-keyboard-accessibility.html">code source</a>) – ouvrez-le dans un nouvel onglet et essayez d’appuyer sur la touche de tabulation; après quelques appuis, vous devriez voir le focus de l'onglet commencer à se déplacer à travers les différents éléments qui peuvent être mis au point ; les éléments focalisés se voient attribuer un style par défaut en surbrillance dans chaque navigateur (il diffère légèrement d’un navigateur à l’autre) afin que vous puissiez déterminer quel élément est ciblé.</p>

<p><img alt="" src="button-focused-unfocused.png"></p>

<p>Vous pouvez ensuite appuyer sur Entrée/Retour pour suivre un lien sélectionné ou appuyer sur un bouton (nous avons inclus du JavaScript pour que les boutons alertent un message), ou commencer à taper pour saisir du texte dans une entrée de texte (les autres éléments de formulaire ont des contrôles différents, par exemple, l'élément  {{htmlelement("select")}} peut avoir ses options affichées et alterner entre les touches fléchées haut et bas). </p>

<div class="note">
<p><strong>Note :</strong> Différents navigateurs peuvent avoir différentes options de contrôle du clavier disponibles. Voir comment <a href="/fr/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibilité#Using_native_keyboard_accessibility">gérer les problèmes courants d'accessibilité</a> pour plus de détails.</p>
</div>

<p>Vous obtenez essentiellement ce comportement gratuitement, en utilisant simplement les éléments appropriés, par exemple :</p>

<pre class="brush: html example-good">&lt;h1&gt;Liens&lt;/h1&gt;

&lt;p&gt; Ceci est un lien vers  &lt;a href="https://www.mozilla.org"&gt;Mozilla&lt;/a&gt;.&lt;/p&gt;

&lt;p&gt; Un autre lien, pour  &lt;a href="https://developer.mozilla.org"&gt;Mozilla Developer Network&lt;/a&gt;.&lt;/p&gt;

&lt;h2&gt;Boutons&lt;/h2&gt;

&lt;p&gt;
  &lt;button data-message="This is from the first button"&gt;Cliquez moi!&lt;/button&gt;
  &lt;button data-message="This is from the second button"&gt; Cliquez moi aussi !&lt;/button&gt;
  &lt;button data-message="This is from the third button"&gt;Et moi!&lt;/button&gt;
&lt;/p&gt;

&lt;h2&gt;formulaire&lt;/h2&gt;

&lt;form&gt;
  &lt;div&gt;
    &lt;label for="name"&gt; Remplis ton nom :&lt;/label&gt;
    &lt;input type="text" id="name" name="name"&gt;
  &lt;/div&gt;
  &lt;div&gt;
    &lt;label for="age"&gt; Entrez votre âge :&lt;/label&gt;
    &lt;input type="text" id="age" name="age"&gt;
  &lt;/div&gt;
  &lt;div&gt;
    &lt;label for="mood"&gt; Choisissez votre humeur :&lt;/label&gt;
    &lt;select id="mood" name="mood"&gt;
      &lt;option&gt;Heureux&lt;/option&gt;
      &lt;option&gt; Triste &lt;/option&gt;
      &lt;option&gt; Fâché &lt;/option&gt;
      &lt;option&gt; Préoccupé &lt;/option&gt;
    &lt;/select&gt;
  &lt;/div&gt;
&lt;/form&gt;</pre>

<p>Cela signifie que vous devez utiliser des liens, des boutons, des éléments de formulaire et des étiquettes de manière appropriée (y compris l'élément  {{htmlelement("label")}} pour les contrôles de formulaire).</p>

<p>Cependant, il est encore une fois que les gens font parfois des choses étranges avec HTML. Par exemple, vous voyez parfois des boutons balisés en utilisant {{htmlelement("div")}}s,  par exemple :</p>

<pre class="brush: html example-bad">&lt;div data-message="This is from the first button"&gt; Cliquez-moi!&lt;/div&gt;
&lt;div data-message="This is from the second button"&gt;  Cliquez moi aussi!&lt;/div&gt;
&lt;div data-message="This is from the third button"&gt; Et moi!&lt;/div&gt;</pre>

<p>Il est toutefois déconseillé d’utiliser un tel code. Vous perdriez immédiatement l’accessibilité au clavier natif que vous auriez obtenue si vous aviez utilisé des éléments  {{htmlelement("button")}}. De plus, vous n’obtenez aucun des styles CSS par défaut que les boutons ont.</p>

<h4 id="Remettre_laccessibilité_au_clavier">Remettre l'accessibilité au clavier</h4>

<p>Ajouter de tels avantages en retour demande un peu de travail (vous pouvez utiliser un exemple de code dans notre exemple <a href="https://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/fake-div-buttons.html">fake-div-buttons.html</a> –  voir également le <a class="external external-icon" href="https://github.com/mdn/learning-area/blob/master/tools-testing/cross-browser-testing/accessibility/fake-div-buttons.html">source code</a>). Ici, nous avons donné à nos faux boutons <code>&lt;div&gt;</code> la possibilité se focaliser (y compris via la touche Tab) en donnant à chacun l'attribut <code>tabindex="0"</code> :</p>

<pre class="brush: html">&lt;div data-message="This is from the first button" tabindex="0"&gt; Cliquez-moi!&lt;/div&gt;
&lt;div data-message="This is from the second button" tabindex="0"&gt; Cliquez moi aussi!&lt;/div&gt;
&lt;div data-message="This is from the third button" tabindex="0"&gt; Et moi!&lt;/div&gt;</pre>

<p>Fondamentalement, l'attribut {{htmlattrxref("tabindex")}} est principalement destiné à permettre aux éléments que l'on peut cibler avec la touche Tab d'avoir un ordre de tabulation personnalisé (spécifié dans l'ordre numérique positif), au lieu d'être simplement tabulés dans leur ordre source par défaut. C'est presque toujours une mauvaise idée, car cela peut causer une confusion majeure. Utilisez-le uniquement si vous en avez vraiment besoin, par exemple si la mise en page affiche les éléments dans un ordre visuel très différent de celui du code source et si vous souhaitez que les éléments fonctionnent de manière plus logique. Il y a deux autres options pour <code>tabindex</code> :</p>

<ul>
 <li><code>tabindex="0"</code> – comme indiqué ci-dessus, cette valeur permet aux éléments qui ne sont pas normalement tabulables de le devenir. C’est la valeur la plus utile de <code>tabindex</code>.</li>
 <li><code>tabindex="-1"</code> – cela permet aux éléments qui ne sont normalement pas tabulables d'être ciblés par le programme, par ex. via JavaScript, ou en tant que cible de liens.</li>
</ul>

<p>Bien que l’addition ci-dessus nous permette de tabuler les boutons, elle ne nous permet pas de les activer via la touche Entrée/Retour. Pour ce faire, nous avons dû ajouter le bout de code JavaScript suivant :</p>

<pre class="brush: js">document.onkeydown = function(e) {
  if(e.keyCode === 13) { // The Enter/Return key
    document.activeElement.onclick(e);
  }
}</pre>

<p>Ici, nous ajoutons un écouteur à l’objet <code>document</code> pour détecter le moment où un bouton a été appuyé sur le clavier. Nous vérifions quel bouton a été pressé via la propriété  <code><a href="/fr/docs/Web/API/KeyboardEvent/keyCode">keyCode</a></code> de l'objet événement; s'il s'agit du code clé qui correspond  Return/Enter, nous exécutons la fonction stockée dans le gestionnaire du bouton   <code>onclick</code>  à l'aide de <code>document.activeElement.onclick()</code>. <code><a href="/fr/docs/Web/API/Document/activeElement">activeElement</a></code> nous donne l'élément qui est actuellement ciblé sur la page.</p>

<div class="note">
<p><strong>Note :</strong> N'oubliez pas que cette technique ne fonctionnera que si vous définissez vos gestionnaires d'événements d'origine via les propriétés du gestionnaire d'événements (par exemple, onclick), <code>addEventListener</code> ne fonctionnera pas.</p>
</div>

<p>C’est beaucoup de tracas supplémentaire pour reconstruire la fonctionnalité. Et il y aura sûrement d’autres problèmes. <strong>Mieux vaut utiliser le bon élément pour le bon travail en premier lieu</strong>.</p>

<h4 id="Étiquettes_de_texte_significatives">Étiquettes de texte significatives</h4>

<p>Les étiquettes de texte de contrôle UI sont très utiles pour tous les utilisateurs, mais leur mise au point est particulièrement importante pour les utilisateurs handicapés.</p>

<p>Vous devez vous assurer que les libellés des boutons et des liens sont compréhensibles et distinctifs. Ne vous contentez pas d'utiliser « Cliquez ici » pour vos étiquettes, car les utilisateurs et utilisatrices de lecteur d'écran créent parfois une liste de boutons et de contrôles de formulaire. La capture d'écran suivante montre nos commandes répertoriées par VoiceOver sur Mac.</p>

<p><img alt="" src="voiceover-formcontrols.png"></p>

<p>Assurez-vous que vos étiquettes ont une signification hors contexte, qu'elles soient lues séparément ou dans le contexte du paragraphe dans lequel elles se trouvent. Par exemple, voici un exemple de texte de lien de qualité :</p>

<pre class="brush: html example-good">&lt;p&gt; Les baleines sont vraiment des créatures géniales . &lt;a href="whales.html"&gt; En savoir plus sur les baleines &lt;/a&gt;.&lt;/p&gt;</pre>

<p>c'est un mauvais texte du lien :</p>

<pre class="brush: html example-bad">&lt;p&gt; Les baleines sont des créatures vraiment impressionnantes. Pour en savoir plus sur les baleines,  &lt;a href="whales.html"&gt;cliquez ici&lt;/a&gt;.&lt;/p&gt;
</pre>

<div class="note">
<p><strong>Note :</strong> Vous pouvez trouver beaucoup plus d'informations sur l'implémentation de liens et les meilleures pratiques dans notre article sur la <a href="/fr/docs/Apprendre/HTML/Introduction_à_HTML/Creating_hyperlinks">création d'hyperliens</a>. Vous pouvez également voir quelques bons et mauvais exemples dans <a href="https://mdn.github.io/learning-area/accessibility/html/good-links.html">Bons-liens.html</a> et <a href="https://mdn.github.io/learning-area/accessibility/html/bad-links.html">Mauvais-liens.html</a>.</p>
</div>

<p>Les libellés de formulaire sont également importantes pour vous donner un indice sur ce que vous devez entrer dans chaque entrée de formulaire. Ce qui suit semble être un exemple assez raisonnable :</p>

<pre class="brush: html example-bad"> Remplis ton nom : &lt;input type="text" id="name" name="name"&gt;</pre>

<p>Cependant, ce n'est pas très utile pour les utilisateurs handicapés. Dans l'exemple ci-dessus, rien n'associe de manière non équivoque l'étiquette à la saisie de formulaire et explique clairement comment la remplir si vous ne la voyez pas. Si vous y accédez avec certains lecteurs d’écran, vous ne recevrez peut-être qu’une description du type « éditer le texte".</p>

<p>Ce qui suit est un exemple bien meilleur :</p>

<pre class="brush: html example-good">&lt;div&gt;
  &lt;label for="name"&gt;Entrez votre nom:&lt;/label&gt;
  &lt;input type="text" id="name" name="name"&gt;
&lt;/div&gt;</pre>

<p>Avec le code comme celui-ci, le label sera clairement associée à input; la description ressemblera davantage à "Entrez votre nom: éditez le texte".</p>

<p><img alt="" src="voiceover-good-form-label.png"></p>

<p>En prime, dans la plupart des navigateurs, associer a un label à une  form input signifie que vous pouvez cliquer sur celle-ci pour sélectionner / activer l'élément  label. Cela donne à input une zone de résultats plus grande, ce qui facilite la sélection</p>

<div class="note">
<p><strong>Note :</strong> vous pouvez voir des exemples de bonnes et de mauvaises de formulaire dans <a href="https://mdn.github.io/learning-area/accessibility/html/good-form.html">exemple de bon formulaire</a> et <a href="https://mdn.github.io/learning-area/accessibility/html/bad-form.html">exemple de mauvais formulaire</a>.</p>
</div>

<h2 id="Tableaux_de_données_accessibles">Tableaux de données accessibles</h2>

<p>Une table de données de base peut être écrite avec un balisage très simple, par exemple :</p>

<pre class="brush: html">&lt;table&gt;
  &lt;tr&gt;
    &lt;td&gt;Nom&lt;/td&gt;
    &lt;td&gt;Age&lt;/td&gt;
    &lt;td&gt;Sexe&lt;/td&gt;
  &lt;/tr&gt;
  &lt;tr&gt;
    &lt;td&gt;Gabriel&lt;/td&gt;
    &lt;td&gt;13&lt;/td&gt;
    &lt;td&gt;Male&lt;/td&gt;
  &lt;/tr&gt;
  &lt;tr&gt;
    &lt;td&gt;Elva&lt;/td&gt;
    &lt;td&gt;8&lt;/td&gt;
    &lt;td&gt;Femelle&lt;/td&gt;
  &lt;/tr&gt;
  &lt;tr&gt;
    &lt;td&gt;Freida&lt;/td&gt;
    &lt;td&gt;5&lt;/td&gt;
    &lt;td&gt;Femelle&lt;/td&gt;
  &lt;/tr&gt;
&lt;/table&gt;</pre>

<p>Mais cela pose des problèmes : un utilisateur de lecteur d’écran ne peut pas associer des lignes ou des colonnes en tant que groupes de données. Pour ce faire, vous devez savoir quelles sont les lignes d'en-tête et si elles sont dirigées vers le haut, des colonnes, etc. Cela ne peut être fait que visuellement pour le tableau ci-dessus (voir bad-table.html et essayez vous-même l'exemple).</p>

<p>Regardez maintenant notre  tableau d'exemple sur les groupes punk – vous pouvez voir quelques aides à l'accessibilité au travail ici :</p>

<ul>
 <li>Les en-têtes de tableau sont définis à l'aide d'éléments {{htmlelement("th")}} —  vous pouvez également spécifier s'il s'agit d'en-têtes de lignes ou de colonnes à l'aide de l'attribut  <code>scope</code>. Cela vous donne des groupes complets de données qui peuvent être consommés par les lecteurs d'écran en tant qu'unités simples</li>
 <li>L'élément {{htmlelement("caption")}} et l'attribut summary   <code>&lt;table&gt;</code> effectuent tous deux des travaux similaires. Ils agissent en tant que texte alternatif pour une table, offrant ainsi à un utilisateur de lecteur d'écran un résumé rapide et utile du contenu de la table.   <code>&lt;caption&gt;</code> est généralement préféré car il rend son contenu accessible aux utilisateurs malvoyants, qui pourraient également le trouver utile. Vous n'avez pas vraiment besoin des deux.</li>
</ul>

<div class="note">
<p><strong>Note :</strong> voir notre article  <a href="/fr/docs/Apprendre/HTML/Tableaux/Advanced">Tableaux HTML : dispositions avancées et accessibilité</a>  pour plus de détails sur les tables de données accessibles.</p>
</div>

<h2 id="Alternatives_textuelles">Alternatives textuelles</h2>

<p>Alors que le contenu textuel est intrinsèquement accessible, il n'en est pas de même pour le contenu multimédia : le contenu image/vidéo ne peut pas être vu par les personnes malvoyantes et le contenu audio ne peut pas être entendu par les malentendants. Nous verrons plus loin le contenu audio et vidéo dans l'article multimédia accessible, mais pour cet article, nous examinerons l'accessibilité pour l'élément humble {{htmlelement("img")}}.</p>

<p>Nous avons un exemple simple écrit, <a href="http://mdn.github.io/learning-area/accessibility/html/accessible-image.html">accessible-image.html</a>, comporte quatre copies de la même image :</p>

<pre>&lt;img src="dinosaur.png"&gt;

&lt;img src="dinosaur.png"
     alt="Un Tyrannosaure Rex rouge: Un dinosaure à deux pattes se tenant droit comme un humain, avec de petits bras et une grosse tête avec beaucoup de dents acérées."&gt;

&lt;img src="dinosaur.png"
     alt="Un Tyrannosaure Rex rouge: Un dinosaure à deux pattes se tenant droit comme un humain, avec de petits bras et une grosse tête avec beaucoup de dents acérées."
     title="Le dinosaure rouge de Mozilla "&gt;


&lt;img src="dinosaur.png" aria-labelledby="dino-label"&gt;

&lt;p id="dino-label"&gt; Tyrannosaure rouge Rex de Mozilla: Dinosaure à deux jambes, debout comme un être humain, avec des armes légères et une grosse tête avec beaucoup de dents acérées.&lt;/p&gt;
</pre>

<p>La première image, lorsqu'elle est visualisée par un lecteur d'écran, n'offre pas beaucoup d'aide à l'utilisateur. VoiceOver, par exemple, lit « /dinosaur.png, image ». Il lit le nom du fichier pour essayer de fournir de l'aide. Dans cet exemple, l'utilisateur ou l’utilisatrice saura au moins qu'il s'agit d'un dinosaure, mais les fichiers peuvent souvent être chargés avec des noms de fichiers générés par une machine (par exemple, à partir d'un appareil photo numérique) et ces noms de fichiers ne fourniront probablement aucun contexte au contenu de l'image.</p>

<div class="note">
<p><strong>Note :</strong> c'est pourquoi vous ne devriez jamais inclure de contenu textuel dans une image. Les lecteurs d'écran ne peuvent tout simplement pas y accéder. Il y a aussi d'autres inconvénients - vous ne pouvez pas le sélectionner et le copier/coller. Juste ne le faite pas !</p>
</div>

<p>Quand un lecteur d'écran rencontre la deuxième image, il lit l'intégralité de l'attribut alt – « Un Tyrannosaure Rex rouge : Un dinosaure à deux pattes se tenant droit comme un humain, avec des armes de petit calibre et une grosse tête avec beaucoup de dents acérées. »</p>

<p>Cela met en évidence l’importance non seulement d’utiliser des noms de fichiers significatifs au cas où ce qui est appelé <strong>alt text</strong> n’est pas disponible, mais aussi de s’assurer que le texte alternatif est fourni dans les attributs  <code>alt</code> chaque fois que possible. Notez que le contenu de l'attribut  <code>alt</code> doit toujours fournir une représentation directe de l'image et de ce qu'elle transmet visuellement. Aucune connaissance personnelle ou description supplémentaire ne devrait être incluse ici, car elle n’est pas utile pour les personnes qui n’ont jamais rencontré l’image auparavant.</p>

<p>Une chose à considérer est de savoir si vos images ont une signification dans votre contenu, ou si elles sont purement décoratives, n’ont donc aucune signification. S'ils sont décoratifs, il est préférable de les inclure dans la page en tant qu'images d'arrière-plan CSS.</p>

<div class="note">
<p><strong>Note :</strong> Lisez <a href="/fr/docs/Apprendre/HTML/Multimedia_and_embedding/Images_in_HTML">Les images en HTML</a> et<a href="/fr/docs/Apprendre/HTML/Comment/Ajouter_des_images_adaptatives_à_une_page_web"> Images adaptatives</a> pour plus d’informations sur la mise en œuvre des images et les meilleures pratiques.</p>
</div>

<p>Si vous souhaitez fournir des informations contextuelles supplémentaires, vous devez les insérer dans le texte entourant l'image ou dans un attribut title, comme indiqué ci-dessus. Dans ce cas, la plupart des lecteurs d’écran liront le texte alternatif, l’attribut title et le nom du fichier. En outre, les navigateurs affichent le texte du titre sous forme d’infos lors du survol de la souris.</p>

<p><img alt="" src="title-attribute.png"></p>

<p>Jetons un autre coup d'oeil à la quatrième méthode :</p>

<pre class="brush: html">&lt;img src="dinosaur.png" aria-labelledby="dino-label"&gt;

&lt;p id="dino-label"&gt; Le Tyrannosaure rouge Mozilla  ... &lt;/p&gt;</pre>

<p>Dans ce cas, nous n'utilisons pas du tout l'attribut <code>alt</code> Nous avons plutôt présenté notre description de l'image sous forme de paragraphe de texte normal, en lui attribuant un  <code>id</code> puis nous avons utilisé l'attribut  <code>aria-labelledby</code> pour : faire référence à cela  <code>id</code>, ce qui amène les lecteurs d’écran à utiliser ce paragraphe comme alt  text/label pour cette image. Ceci est particulièrement utile si vous souhaitez utiliser le même texte comme étiquette pour plusieurs images – quelque chose qui n’est pas possible avec <code>alt</code>.</p>

<div class="note">
<p><strong>Note :</strong> <code>aria-labelledby</code> fait partie de la spécification <a href="https://www.w3.org/TR/wai-aria-1.1/">WAI ARIA</a>, qui permet aux développeurs d'ajouter une sémantique supplémentaire à leur balisage afin d'améliorer l'accessibilité du lecteur d'écran, le cas échéant. Pour en savoir plus sur son fonctionnement, lisez notre article <a href="/fr/docs/Learn/Accessibility/WAI-ARIA_basics">WAI-ARIA basic</a>.</p>
</div>

<h3 id="Autres_mécanismes_alternatifs_de_texte">Autres mécanismes alternatifs de texte</h3>

<p>Les images ont également d'autres mécanismes disponibles pour fournir un texte descriptif. Par exemple, il existe un attribut <code>longdesc</code> destiné à pointer sur un document web distinct contenant une description étendue de l'image, par exemple :</p>

<pre class="brush: html">
&lt;img src="dinosaur.png" longdesc="dino-info.html"&gt;</pre>

<p>Cela semble être une bonne idée, en particulier pour les infographies telles que les grands graphiques contenant de nombreuses informations, qui pourraient peut-être être représentées sous forme de tableau de données accessible (voir section précédente). Cependant, longdesc n’est pas toujours pris en charge par les lecteurs d’écran et le contenu est totalement inaccessible aux utilisateurs autres que les lecteurs d’écran. Il est sans doute préférable d’inclure la description longue sur la même page que l’image, ou d’y accéder par un lien régulier.</p>

<p>HTML5 comprend deux nouveaux éléments  — {{htmlelement("figure")}} et {{htmlelement("figcaption")}} —  qui sont supposés associer une figure quelconque (ce peut être n'importe quoi, pas nécessairement une image) à une légende de figure :</p>

<pre class="brush: html">&lt;figure&gt;
  &lt;img src="dinosaur.png" alt="Le Mozilla Tyrannosaurus "&gt;
  &lt;figcaption&gt; Un Tyrannosaure Rex rouge: Un dinosaure à deux pattes se tenant droit comme un humain, avec de petits bras et une grosse tête avec beaucoup de dents acérées .&lt;/figcaption&gt;
&lt;/figure&gt;</pre>

<p>Malheureusement, la plupart des lecteurs d’écran ne semblent pas encore associer de légendes à leurs figures, mais la structure des éléments est utile pour le style CSS. Elle permet également de placer une description de l’image à côté de la source.</p>

<h3 id="Attributs_alt_vides">Attributs alt vides</h3>

<pre class="brush: html">
&lt;h3&gt;
  &lt;img src="article-icon.png" alt=""&gt;
  Tyrannosaurus Rex: le roi des dinosaures 
&lt;/h3&gt;</pre>

<p>Il peut arriver qu'une image soit incluse dans la conception d'une page, mais son objectif principal est la décoration visuelle. Vous remarquerez dans l'exemple de code ci-dessus que l'attribut   <code>alt </code> de l'image est vide – il s'agit pour que les lecteurs d'écran reconnaissent l'image, mais n'essayent pas de décrire l'image (au lieu de cela, ils diraient simplement « image », ou similaire) .</p>

<p>La raison d'utiliser un vide <code>alt</code> au lieu de ne pas l'inclure est due au fait que de nombreux lecteurs d'écran annoncent l'URL complète de l'image si aucun  <code>alt</code> n'est fourni. Dans l'exemple ci-dessus, l'image agit comme une décoration visuelle de l'en-tête auquel elle est associée. Dans ce cas, et dans les cas où une image est uniquement une décoration et n'a pas de valeur de contenu, vous devez mettre un vide  <code>alt</code> sur vos images. Une autre alternative consiste à utiliser l'attribut aria role role = "presentation" – cela empêche également les lecteurs d'écrans de lire du texte alternatif.</p>

<div class="note">
<p><strong>Note :</strong> si possible, vous devriez utiliser CSS pour afficher des images qui ne sont que des décorations.</p>
</div>

<h2 id="Résumé">Résumé</h2>

<p>Vous devriez maintenant bien connaître l'écriture HTML accessible pour la plupart des cas. Notre article sur les bases de WAI-ARIA comblera également certaines lacunes dans cette connaissance, mais cet article s’occupe des bases. Ensuite, nous allons explorer CSS et JavaScript, et comment l’accessibilité est affectée par leur bon ou mauvais usage.</p>

<p>{{PreviousMenuNext("Learn/Accessibility/What_is_Accessibility","Learn/Accessibility/CSS_and_JavaScript", "Learn/Accessibility")}}</p>
