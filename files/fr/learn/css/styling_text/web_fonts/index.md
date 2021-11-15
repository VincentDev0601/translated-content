---
title: Fontes Web
slug: Learn/CSS/Styling_text/Web_fonts
translation_of: Learn/CSS/Styling_text/Web_fonts
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenuNext("Learn/CSS/Styling_text/Styling_links", "Learn/CSS/Styling_text/Typesetting_a_homepage", "Learn/CSS/Styling_text")}}</div>

<p>Dans le premier article du module, nous avons exploré les fonctions CSS de base disponibles pour composer du texte. Dans cet article, nous allons plus loin et explorons les polices web en détail : comment télécharger des polices personnalisées en même temps que la page Web, pour donner un style plus varié et personnalisé au texte.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Connaissances informatiques de base, les bases HTML (étudiées dans l'<a href="/fr/docs/Learn/HTML/Introduction_to_HTML">Introduction au HTML</a>), les bases CSS (étudiées dans <a href="/fr/docs/Learn/CSS/Introduction_to_CSS">Introduction à CSS</a>).</td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Apprendre comment appliquer des fontes web à une page web, soit avec un service tierce partie, soit en écrivant vous-même le code.</td>
  </tr>
 </tbody>
</table>

<h2 id="Rappel_familles_de_fontes">Rappel : familles de fontes</h2>

<p>Comme nous l'avons vu dans <a href="/fr/docs/Learn/CSS/Styling_text/initiation-mise-en-forme-du-texte">Initiation à la mise en forme du texte</a>, les fontes appliquées aux HTML sont contrôlées par la propriété {{cssxref("font-family")}}. Elle accepte un ou plusieurs noms de familles de fontes et le navigateur parcourt la liste jusqu'à trouver la fonte disponible sur le système sur lequel il tourne :</p>

<pre class="brush: css">p {
  font-family: Helvetica, "Trebuchet MS", Verdana, sans-serif;
}</pre>

<p>Ce système fonctionne bien, mais généralement, le choix des développeurs Web en matière de polices sont limités. Il n'y en a qu'une poignée dont la disponibilité soit garantie sur tous les systèmes courants — les polices dites <a href="/fr/docs/Learn/CSS/Styling_text/initiation-mise-en-forme-du-texte#Polices_web_sûres">Web-safe</a>. La pile de polices vous permet de préciser la police préférable, puis la police alternative sûre pour le Web, puis la police par défaut du système, mais cela induit du travail supplémentaire de tests pour s'assurer que le désign reste correct avec chaque police, etc.</p>

<h2 id="Fontes_Web">Fontes Web</h2>

<p>Mais il y a autre chose qui fonctionne très bien, depuis la version 6 d'IE. La fonctionnalité CSS des polices Web permet de définir les fichiers de polices à télécharger avec le site Web au fur et à mesure de sa consultation ; autrement dit, tout navigateur prenant en charge les polices Web aura exactement la police précisée à sa disposition. Incroyable ! La syntaxe requise ressemble à ce qui suit.</p>

<p>Primo, un bloc {{cssxref("@font-face")}} est placé au début de la CSS ; il précise le ou les fichiers de fontes à télécharger :</p>

<pre class="brush: css">@font-face {
  font-family: "myFont";
  src: url("myFont.ttf");
}</pre>

<p>Sous cette déclaration, vous pouvez utiliser le nom de la famille de polices précisé dans @font-face pour appliquer la police personnalisée où vous le voulez, normalement :</p>

<pre class="brush: css">html {
  font-family: "myFont", "Bitstream Vera Serif", serif;
}</pre>

<p>La syntaxe peut devenir un peu plus complexe que cela, nous reviendrons sur le sujet plus bas.</p>

<p>Deux points important sont à garder présents à l'esprit à ce propos :</p>

<p>L'utilisation des polices n'est généralement pas gratuite. Vous devez payer pour les utiliser et/ou respecter d'autres conditions de licence telles que citer le créateur de la police dans le code (ou sur le site). Ne vous appropriez pas les polices et ne les utilisez pas sans donner le crédit voulu.</p>

<ol>
 <li>Les navigateurs prennent en charge divers formats de polices ; donc, vous aurez besoin de plusieurs formats de polices pour une prise en charge croisée correcte des navigateurs. Par ex., la plupart des navigateurs modernes prennent en charge les formats WOFF/WOFF2 (Web Open Font Format versions 1 et 2), le plus efficace, mais les vieilles versions d'IE n'acceptent que les polices EOT (Embedded Open Type) et, même, vous pourriez avoir besoin d'inclure une version SVG de la police pour être pris en charge par les anciennes versions de l'iPhone et des navigateurs Android. Nous vous montrerons ci-dessous comment générer le code voulu.</li>
 <li>Fonts generally aren't free to use. You have to pay for them, and/or follow other license conditions such as crediting the font creator in the code (or on your site.) You shouldn't steal fonts and use them without giving proper credit.</li>
</ol>

<div class="note">
<p><strong>Note :</strong> La technique des polices Web est prise en charge dans Internet Explorer depuis sa version 4 !</p>
</div>

<h2 id="Apprentissage_actif_un_exemple_de_fonte_web">Apprentissage actif : un exemple de fonte web</h2>

<p>En gardant en tête ce qui précède, construisons un exemple de police web de base à partir des premiers principes. Il est difficile de le montrer à l'aide d'un exemple direct intégré : nous aimerions donc que vous suiviez les étapes détaillées dans les paragraphes ci‑après afin d'avoir une idée du processus.</p>

<p>Utilisez les fichiers <a href="https://github.com/mdn/learning-area/blob/master/css/styling-text/web-fonts/web-font-start.html">web-font-start.html</a> et <a href="https://github.com/mdn/learning-area/blob/master/css/styling-text/web-fonts/web-font-start.css">web-font-start.css</a> comme point de départ pour ajouter votre code (voir l'<a href="http://mdn.github.io/learning-area/css/styling-text/web-fonts/web-font-start.html">exemple en direct</a> aussi.) Faites une copie de ces fichiers dans un nouveau répertoire sur votre ordinateur. Dans le fichier <code>web-font-start.css</code>, vous trouverez un CSS minimal pour traiter la mise en page et la composition de base de l'exemple.</p>

<h3 id="Recherche_des_polices">Recherche des polices</h3>

<p> </p>

<p>Dans cet exemple, nous utilisons deux polices web, une pour les en-têtes et une pour le corps du texte. Pour commencer, nous devons trouver les fichiers de ces polices. Les fontes des polices sont stockées en différents formats de fichiers. Il y a généralement trois types de sites où obtenir des fontes :</p>

<ul>
 <li>un distributeur de fontes gratuites : c'est un site de téléchargement de polices gratuites (la licence peut exiger certaines conditions, comme citer le créateur de la fonte). C'est le cas de <a href="https://www.fontsquirrel.com/">Font Squirrel</a>, <a href="http://www.dafont.com/">dafont</a> et <a href="https://everythingfonts.com/">Everything Fonts</a>.</li>
 <li>un distributeur de fontes payantes : c'est un site qui met à disposition des fontes contre paiement, comme <a href="http://www.fonts.com/">fonts.com</a> ou <a href="http://www.myfonts.com/">myfonts.com</a>. Vous pouvez aussi acheter directement auprès du fondeur, par exemple <a href="https://www.linotype.com/">Linotype</a>, <a href="http://www.monotype.com">Monotype</a> ou <a href="http://www.exljbris.com/">Exljbris</a>.</li>
 <li>un service de fontes en ligne : c'est un site qui stocke et téléverse les polices à votre intention, facilitant ainsi l'ensemble du processus. Voir la section {{anch("Utiliser un service de polices en ligne")}} pour plus de détails.</li>
</ul>

<p>Cherchons des polices de caractères ! Allez dans <a href="https://www.fontsquirrel.com/">Font Squirrel</a> et choisissez deux polices — une police adaptée aux en-têtes (peut-être une belle police d'affichage de blocs avec sérifs) et une police un peu moins criarde et plus lisible pour les paragraphes. Après avoir trouvé chaque police, appuyez sur le bouton de téléchargement et enregistrez le fichier dans le même répertoire que les fichiers HTML et CSS précéemment enregistrés. Peu importe qu'il s'agisse de TTF (True Type Fonts) ou OTF (Open Type Fonts).</p>

<p>Dans chaque cas, décompressez le paquet de la fonte (les fontes Web sont généralement distribuées dans des fichiers ZIP contenant les fichiers de police et l'information de licence). Vous pouvez trouver plusieurs fichiers de polices dans le paquet — certaines fontes sont distribuées sous forme de familles avec plusieurs variantes disponibles, par exemple fine, moyenne, grasse, italique, italique fine, etc. Pour cet exemple, ne vous interessez qu'à un seul fichier pour chacun des deux cas.</p>

<div class="note">
<p><strong>Note :</strong> Dans la partie « Find fonts » dans la colonne de droite, vous pouvez cliquer sur les diverses marques et classification pour filtrer les chois à afficher.</p>
</div>

<h3 id="Créer_le_code_requis">Créer le code requis</h3>

<p>Maintenant, créez le code requis (et les formats de police). Pour chaque police, suivez ces étapes :</p>

<ol>
 <li>Assurez-vous d'avoir satisfait aux exigences de la licence, si vous l'utilisez dans un projet commercial et/ou Web.</li>
 <li>Allez sur le <a href="https://www.fontsquirrel.com/tools/webfont-generator">Webfont Generator</a> de Fontsquirrel.</li>
 <li>Téléversez les deux fichiers de fontes avec le bouton <em>Upload Fonts</em>.</li>
 <li>Cochez la case nommée « Yes, the fonts I'm uploading are legally eligible for web embedding » (<em>Oui, les fontes téléversées sont légalement éligibles à une intégration web</em>).</li>
 <li>Cliquez sur « <em>Download your kit</em> » (<em>Télécharger le kit</em>) .</li>
</ol>

<p>Après que le générateur a terminé le traitement, vous obtenez un fichier ZIP à télécharger — enregistrez‑le dans le même répertoire que les fichiers HTML et CSS.</p>

<h3 id="Mise_en_œuvre_du_code_dans_la_démo">Mise en œuvre du code dans la démo</h3>

<p>Maintenant, faites l'extraction de l'ensemble des polices web crées. Dans le répertoire d'extraction, trois éléments utiles :</p>

<ul>
 <li>Plusieurs versions de chaque police : (par ex., <code>.ttf</code>, <code>.woff</code>, <code>.woff2</code>, etc. ; les polices exactement fournies sont mises à jour au fur et à mesure des modifications des exigences de prise en charge des navigateurs). Comme mentionné ci‑dessus, plusieurs polices sont nécessaires pour une prise en charge croisée entre navigateurs — c'est le moyen choisi par Fontsquirrel pour s'assurer que vous avez bien ce qui est nécessaire.</li>
 <li>Un fichier HTML de démo pour chaque police — chargez‑les dans votre navigateur pour voir ce à quoi elles ressemblent dans divers contextes d'emploi.</li>
 <li>Un fichier <code>stylesheet.css</code>, qui contient le code @font-face dont vous avez besoin.</li>
</ul>

<p>Pour mettre en œuvre ces polices dans la démo, suivez ces étapes :</p>

<ol>
 <li>Renommez le répertoire d'extraction avec quelque chose de simple, comme <code>fonts</code>.</li>
 <li>Ouvrez le fichier <code>stylesheet.css</code> et copiez y les deux blocs <code>@font-face</code> contenus dans le  fichier <code>web-font-start.css</code> — il faut les mettre tout en haut, avant tout élement du CSS, car les polices doivent être importées avant de pouvoir les utiliser sur votre site.</li>
 <li>Chaque fonction <code>url()</code> pointe sur un fichier de police à importer dans la CSS — assurez‑vous que les chemins vers les fichiers soient corrects, donc ajoutez  <code>fonts/</code> au début de chaque chemin (si nécessaire).</li>
 <li>Maintenant, vous pouvez vous servir de ces polices dans vos piles de fontes, tout à fait comme les polices système ou une police « web safe ». Par exemple :
  <pre class="brush: css">font-family: 'zantrokeregular', serif;</pre>
 </li>
</ol>

<p>Vous devriez obtenir une page de démonstration avec les belles polices implémentées ci‑dessus. Comme les diverses polices sont créées en différentes tailles, il se peut que vous deviez ajuster la taille, l'espacement, etc. pour parfaire l'aspect.</p>

<p><img alt="" src="web-font-example.png"></p>

<div class="note">
<p><strong>Note :</strong> Si vous avez des problèmes pour faire fonctionner votre travail, n'hésitez pas à comparer votre version à nos fichiers finis — voyez <a href="https://github.com/mdn/learning-area/blob/master/css/styling-text/web-fonts/web-font-finished.html">web-font-finished.html</a> et <a href="https://github.com/mdn/learning-area/blob/master/css/styling-text/web-fonts/web-font-finished.css">web-font-finished.css</a> (lancez l'<a href="http://mdn.github.io/learning-area/css/styling-text/web-fonts/web-font-finished.html">exemple terminé directement</a>).</p>
</div>

<h2 id="Utiliser_un_service_de_polices_en_ligne">Utiliser un service de polices en ligne</h2>

<p>Les services de polices en ligne stockent et servent généralement des polices pour vous afin que vous n'ayez pas à vous soucier d'écrire le code <code>@font-face</code>, et en général, il suffit d'insérer une simple ligne ou deux de code dans votre site pour que tout fonctionne. Les exemples incluent <a href="https://typekit.com/">Typekit</a> and <a href="http://www.typography.com/cloud/welcome/">Cloud.typography</a>. La plupart de ces services sont fondés sur l'abonnement, à l'exception notable de <a href="https://www.google.com/fonts">Google Fonts</a>, un service gratuit utile, en particulier pour les tests rapides et la rédaction de démos.</p>

<p> </p>

<p>La plupart de ces services sont faciles à utiliser, donc nous n'en parlerons pas dans le détail. Regardons rapidement les polices de Google, pour que vous puissiez vous faire une idée. Encore une fois, utilisez des copies de <code>web-font-start.html</code> et <code>web-font-start.css</code> comme point de départ.</p>

<ol>
 <li>Allez sur <a href="https://www.google.com/fonts">Google Fonts</a>.</li>
 <li>Utilisez les filtres sur la droite pour afficher les types de polices à choisir et retenez une paire de fontes qui vous plaisent.</li>
 <li>Pour sélectionner une famille de fontes, pressez le bouton ⊕ sur le côté.</li>
 <li>Après avoir choisi les familles de fontes, pressez la barre avec  <em>[Nombre] Families Selected</em> en bas de la page.</li>
 <li>Dans l'écran résultant, copiez d'abord la ligne de code HTML affichée et collez‑la dans l'en-tête de votre fichier HTML. Mettez-la au-dessus de l'élément {{htmlelement("link")}} existant, de sorte que la police soit importée avant que le navigateur essaye de l'utiliser dans la CSS.</li>
 <li>Copiez ensuite les déclarations CSS listées dans la CSS comme il convient pour appliquer la fonte personnalisée à votre HTML.</li>
</ol>

<div class="note">
<p><strong>Note :</strong> Vous pourrez trouver une version complétée sur <a href="https://github.com/mdn/learning-area/blob/master/css/styling-text/web-fonts/google-font.html">google-font.html</a> et <a href="https://github.com/mdn/learning-area/blob/master/css/styling-text/web-fonts/google-font.css">google-font.css</a>, si vous avez besoin de vérifier votre travail par rapport au nôtre (<a href="http://mdn.github.io/learning-area/css/styling-text/web-fonts/google-font.html">voir en direct</a>).</p>
</div>

<h2 id="font-face_plus_en_détail">@font-face plus en détail</h2>

<p>Examinons la syntaxe générée par fontsquirrel pour <code>@font-face</code>. C'est un bloc de ce type :</p>

<pre class="brush: css">@font-face {
  font-family: 'ciclefina';
  src: url('fonts/cicle_fina-webfont.eot');
  src: url('fonts/cicle_fina-webfont.eot?#iefix') format('embedded-opentype'),
         url('fonts/cicle_fina-webfont.woff2') format('woff2'),
         url('fonts/cicle_fina-webfont.woff') format('woff'),
         url('fonts/cicle_fina-webfont.ttf') format('truetype'),
         url('fonts/cicle_fina-webfont.svg#ciclefina') format('svg');
  font-weight: normal;
  font-style: normal;
}</pre>

<p>Elle est désignée sous le vocable « bulletproof @font-face syntax » (<em>syntaxe @font-face à puces garanties</em>), d'après un post de Paul Irish lors des débuts des succès de <code>@font-face</code> (<a href="http://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/">Bulletproof @font-face Syntax</a>). Voyons les actions :</p>

<ul>
 <li><code>font-family</code> : cette ligne précise la référence à la police. Vous pouvez mettre cette assertion comme bon vous semble, pour autant que ce soit utilisé de manière cohérent dans la CSS.</li>
 <li><code>src</code> : ces lignes indiquent les chemins vers les fichiers de fontes à importer dans la CSS (la partie <code>url</code>) et le format de chaque fichier de fonte (la partie <code>format</code>). Cette dernière partie est dans chaque cas optionnelle, mais il est utile de la déclarer car elle permet aux navigateurs de trouver la police à utiliser plus rapidement. Plusieurs déclarations peuvent être mises dans la liste, séparées par des virgules — le navigateur cherchera parmi celles-ci et utilisera la première trouvée qu'il comprend — toutefois il est préférable de mettre en tête les formats nouveaux comme WOFF2 et le plus anciens comme TTF en fin de liste. Les fontes EOT font exception — elles seront placées en tête pour corriger une paire de bogues dans les anciennes versions de IE, car IE essayera d'utiliser la première trouvée même s'il est en fait incapable de l'utiliser.</li>
 <li>{{cssxref("font-weight")}}/{{cssxref("font-style")}} : ces lignes définissent la graisse de la police, si elle est italique ou pas. Si vous importez plusieurs graisses d'une même police, vous pouvez indiquer quelles sont ses caractéristiques et utiliser diverses valeurs de {{cssxref("font-weight")}}/{{cssxref("font-style")}} pour faire votre choix au lieu d'appeler de noms différents les membres de la même famille. <a href="http://www.456bereastreet.com/archive/201012/font-face_tip_define_font-weight_and_font-style_to_keep_your_css_simple/">@font-face tip: define font-weight and font-style to keep your CSS simple</a> (<em>en anglais — Astuces pour @font-face : définir la graisse et le style des fontes pour avoir des CSS simples</em>) par Roger Johansson montre que faire plus en détail.</li>
</ul>

<div class="note">
<p><strong>Note :</strong> Vous pouvez aussi définir des valeurs particulières de {{cssxref("font-variant")}} et {{cssxref("font-stretch")}} pour vos polices. Dans les navigateurs les plus récents, vous pouvez également indiquer une valeur pour {{cssxref("unicode-range")}} : c'est la plage des codes caractères dont l'utilisation est prévue — dans les navigateurs prenant en charge cette propriété, seuls les caractères indiqués seront téléchargés, ce qui réduit les volumes téléchargés non nécessaires. <a href="https://24ways.org/2011/creating-custom-font-stacks-with-unicode-range/">Creating Custom Font Stacks with Unicode-Range</a> (<em>Création de piles de fontes personnalisées en définissant des plages unicode</em>) de Drew McLellan donne quelques indications utiles pour l'utilisation de cette propriété.</p>
</div>

<h2 id="Résumé">Résumé</h2>

<p>Maintenant que vous avez travaillé nos articles sur les principes fondamentaux pour composer du texte, il est temps de tester votre compréhension de la chose avec notre évaluation pour le module : composition d'une page d'accueil d'une école communale.</p>

<p>{{PreviousMenuNext("Learn/CSS/Styling_text/Styling_links", "Learn/CSS/Styling_text/Typesetting_a_homepage", "Learn/CSS/Styling_text")}}</p>

<p> </p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<p> </p>

<ul>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/initiation-mise-en-forme-du-texte">Initiation à la mise en forme du texte</a></li>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/Styling_lists">Style de listes</a></li>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/Mise_en_forme_des_liens">Mise en forme des liens</a></li>
 <li>Polices de caractères web</li>
 <li><a href="/fr/docs/Learn/CSS/Styling_text/Typesetting_a_homepage">Composition d'une page d'accueil d'une école de communauté</a></li>
</ul>
