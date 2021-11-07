---
title: Polices SVG
slug: Web/SVG/Tutorial/SVG_fonts
tags:
  - Police
  - SVG
  - font
translation_of: Web/SVG/Tutorial/SVG_fonts
original_slug: Web/SVG/Tutoriel/polices_SVG
---
<p>{{ PreviousNext("Web/SVG/Tutoriel/filtres","Web/SVG/Tutoriel/SVG_Image_Tag") }}</p>

<p>Lorsque SVG a été spécifié, le support des polices d'écriture pour le web n'était pas répandu dans les navigateurs. Comme l'accès au fichier de la police adéquate est cependant crucial pour afficher correctement le texte, une technologie de description des polices a été ajoutée à SVG pour offrir cette capacité. Elle n'a pas été conçue pour la compatibilité avec d'autres formats tels que le PostScript ou OTF, mais plutôt comme un moyen simple d'intégration des informations des glyphes en SVG lors de l'affichage.</p>

<div class="note">
  <p><strong>Note :</strong> Les Polices d'écritures SVG sont actuellement supportées uniquement sur Safari et le navigateur Android. Internet Explorer <a href="http://blogs.msdn.com/b/ie/archive/2010/08/04/html5-modernized-fourth-ie9-platform-preview-available-for-developers.aspx">n'a pas envisagé de les implémenter</a>, la fonctionnalité a été <a href="https://www.chromestatus.com/feature/5930075908210688">supprimée de Chrome 38</a> (et Opera 25) et Firefox a <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=119490">reporté sa mise en œuvre indéfiniment</a> pour se concentrer sur <a href="/fr/WOFF" title="en/About WOFF">WOFF</a>. Cependant, d'autres outils comme le plugin <a href="http://www.adobe.com/svg/viewer/install/">Adobe SVG Viewer</a>, Batik et des modèles de document d'Inkscape supportent l'incorporation des Police d'écriture SVG.</p>
</div>

<p>La base pour définir une police SVG est l'élément {{ SVGElement("font") }}.</p>

<h2 id="Définir_une_police">Définir une police</h2>

<p>Quelques ingrédients sont nécessaires pour intégrer une police en SVG. Prenons un exemple de déclaration (celle <a href="http://www.w3.org/TR/SVG/fonts.html#FontElement">de la spécification</a>), et expliquons-en les détails.</p>

<pre class="brush: html">&lt;font id="Font1" horiz-adv-x="1000"&gt;
  &lt;font-face font-family="Super Sans" font-weight="bold" font-style="normal"
      units-per-em="1000" cap-height="600" x-height="400"
      ascent="700" descent="300"
      alphabetic="0" mathematical="350" ideographic="400" hanging="500"&gt;
    &lt;font-face-src&gt;
      &lt;font-face-name name="Super Sans Bold"/&gt;
    &lt;/font-face-src&gt;
  &lt;/font-face&gt;
  &lt;missing-glyph&gt;&lt;path d="M0,0h200v200h-200z"/&gt;&lt;/missing-glyph&gt;
  &lt;glyph unicode="!" horiz-adv-x="300"&gt;&lt;!-- Outline of exclam. pt. glyph --&gt;&lt;/glyph&gt;
  &lt;glyph unicode="@"&gt;&lt;!-- Outline of @ glyph --&gt;&lt;/glyph&gt;
  &lt;!-- more glyphs --&gt;
&lt;/font&gt;</pre>

<p>Nous commençons avec l'élement {{ SVGElement("font") }}. Il contient un attribut id, ce qui permet de le référencer via une URI (voir plus bas). L'attribut <code>horiz-adv-x</code> définit sa largeur moyenne, comparée aux définitions des autres glyphes individules. La valeur 1000 définit une valeur raisonnable. Plusieurs autres attributs associés précisent l'affichage de la boite qui encapsule le glyphe.</p>

<p>L'élément  {{ SVGElement("font-face") }} est l'équivalent SVG de la déclaration CSS  <a href="/fr/CSS/@font-face" title="en/css/@font-face"><code>@font-face</code></a>. Il définit les propriétés de base de la police finale, telles que 'weight', 'style', etc. Dans l'exemple ci-dessus, la première et la plus importante est  <code>font-family</code> : Elle pourra alors être référencée via la propriété <code>font-family</code> présente dans les CSS et les SVG. Les attributs <code>font-weight</code> et <code>font-style</code> ont la même fonction que leurs équivalents CSS. Les attributs suivants sont des instructions de rendu, pour le moteur d'affichage des polices ; par exemple : quelle est la taille des jambages supérieurs des glyphes (<a href="http://en.wikipedia.org/wiki/Ascender_%28typography%29">ascenders</a>).</p>

<p>Its child, the {{ SVGElement("font-face-src") }} element, corresponds to CSS' <code>src</code> descriptor in <code>@font-face</code> declarations. You can point to external sources for font declarations by means of its children {{ SVGElement("font-face-name") }} and {{ SVGElement("font-face-uri") }}. The above example states that if the renderer has a local font available named "Super Sans Bold", it should use this instead.</p>

<p>Following {{ SVGElement("font-face-src") }} is a {{ SVGElement("missing-glyph") }} element. This defines what should be displayed if a certain glyph is not found in the font and if there are no fallback mechanisms. It also shows how glyphs are created: By simply adding any graphical SVG content inside. You can use literally any other SVG elements in here, even {{ SVGElement("filter") }}, {{ SVGElement("a") }} or {{ SVGElement("script") }}. For simple glyphs, however, you can simply add a <code>d</code> attribute — this defines a shape for the glyph exactly like how standard SVG paths work.</p>

<p>The actual glyphs are then defined by {{ SVGElement("glyph") }} elements. The most important attribute is <code>unicode</code>. It defines the unicode codepoint represented by this glyph. If you also specify the {{htmlattrxref("lang")}} attribute on a glyph, you can further restrict it to certain languages (represented by <code>xml:lang</code> on the target) exclusively. Again, you can use arbitrary SVG to define the glyph, which allows for great effects in supporting user agents.</p>

<p>There are two further elements that can be defined inside <code>font</code>: {{ SVGElement("hkern") }} and {{ SVGElement("vkern") }}. Each carries references to at least two characters (attributes <code>u1</code> and <code>u2</code>) and an attribute <code>k</code> that determines how much the distance between those characters should be decreased. The below example instructs user agents to place the "A" and "V" characters closer together the standard distance between characters.</p>

<pre class="brush: html">&lt;hkern u1="A" u2="V" k="20" /&gt;</pre>

<h2 id="Référencer_une_police">Référencer une police</h2>

<p>Lorsque vous avez mis en place votre déclaration de police comme décrit ci-dessus, vous pouvez utiliser un simple attribut <code>font-family</code> pour réellement appliquer la police à un texte SVG:</p>

<pre class="brush: html">&lt;font&gt;
  &lt;font-face font-family="Super Sans" /&gt;
  &lt;!-- ... --&gt;
&lt;/font&gt;

&lt;text font-family="Super Sans"&gt;My text uses Super Sans&lt;/text&gt;</pre>

<p>Cependant, vous êtes libre de combiner plusieurs méthodes pour une plus grande liberté de où et comment définir la police.</p>

<h3 id="Option_Utiliser_le_CSS_font-face">Option: Utiliser le CSS @font-face</h3>

<p>Vous pouvez utiliser <code>@font-face</code> pour les polices externes de référence :</p>

<pre class="brush: html">&lt;font id="Super_Sans"&gt;
  &lt;!-- ... --&gt;
&lt;/font&gt;

&lt;style type="text/css"&gt;
@font-face {
  font-family: "Super Sans";
  src: url(#Super_Sans);
}
&lt;/style&gt;

&lt;text font-family="Super Sans"&gt;My text uses Super Sans&lt;/text&gt;</pre>

<h3 id="Option_Référencer_une_police_externe">Option: Référencer une police externe</h3>

<p>L'élément mentionné <code>font-face-uri</code> vous permet de référencer une police externe, permettant donc une plus grande réutilisabilité :</p>


<pre class="brush: html">&lt;font&gt;
  &lt;font-face font-family="Super Sans"&gt;
    &lt;font-face-src&gt;
      &lt;font-face-uri xlink:href="fonts.svg#Super_Sans" /&gt;
    &lt;/font-face-src&gt;
  &lt;/font-face&gt;
&lt;/font&gt;</pre>

<p>{{ PreviousNext("Web/SVG/Tutoriel/filtres","Web/SVG/Tutoriel/SVG_Image_Tag") }}</p>
