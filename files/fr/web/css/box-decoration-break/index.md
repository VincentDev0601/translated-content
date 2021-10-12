---
title: box-decoration-break
slug: Web/CSS/box-decoration-break
tags:
  - CSS
  - Experimental
  - Propriété
  - Reference
translation_of: Web/CSS/box-decoration-break
---
<div>{{CSSRef}}{{SeeCompatTable}}</div>

<p>La propriété <strong><code>box-decoration-break</code></strong> définit la façon dont les propriétés {{cssxref("background")}}, {{cssxref("padding")}}, {{cssxref("border")}}, {{cssxref("border-image")}}, {{cssxref("box-shadow")}}, {{cssxref("margin")}} et {{cssxref("clip")}} sont appliquées sur un élément lorsque la boîte de celui-ci est fragmentée. La fragmentation apparaît lorsqu'une boîte en ligne s'étend sur plusieurs lignes ou lorsqu'un bloc s'étend sur plus d'une colonne lorsque qu'il est dans conteneur disposé en colonne ou lorsqu'un bloc déclenche un saut de page sur un média imprimé. Chaque « morceau » de l'élément est alors appelé un fragment.</p>

<div>{{EmbedInteractiveExample("pages/css/box-decoration-break.html")}}</div>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush:css no-line-numbers">/* Valeurs avec un mot-clé */
box-decoration-break: slice;
box-decoration-break: clone;

/* Valeurs globales */
box-decoration-break: initial;
box-decoration-break: inherit;
box-decoration-break: unset;
</pre>

<p>La propriété <code>box-decoration-break</code> est définie avec l'un des mots-clés définis ci-après.</p>

<h3 id="Valeurs">Valeurs</h3>

<dl>
 <dt><code>clone</code></dt>
 <dd>Le rendu de chaque fragment de boîte est obtenu indépendamment avec la bordure, le remplissage, la marge indiqués pour chacun des fragments. Les propriétés {{cssxref("border-radius")}}, {{cssxref("border-image")}} et {{cssxref("box-shadow")}} sont appliquées indépendamment à chaque fragment. L'arrière-plan est dessiné indépendamment pour chaque fragment (ainsi, une image d'arrière-plan avec {{cssxref("background-repeat")}}: <code>no-repeat</code> pourra être présente à plusieurs reprises).</dd>
 <dt><code>slice</code></dt>
 <dd>L'élément est initialement affiché comme si la boîte n'était pas fragmentée puis le rendu de cette boîte hypothétique est découpé en fragments pour chaque ligne/colonne/page. On notera que la boîte hypothétique peut être différente pour chaque fragment car elle utilise sa propre hauteur (si la rupture apparaît dans la direction de l'élément) ou sa propre largeur (si la rupture apparaît dans la direction orthogonale). C'est la valeur initiale de la propriété.</dd>
</dl>

<h3 id="Syntaxe_formelle">Syntaxe formelle</h3>

{{csssyntax}}

<h2 id="Exemples">Exemples</h2>

<h3 id="Gestion_des_fragments_pour_les_boîtes_en_ligne">Gestion des fragments pour les boîtes en ligne</h3>

<h4 id="Avec_slice_(valeur_initiale)">Avec <code>slice</code> (valeur initiale)</h4>

<h5 id="CSS">CSS</h5>

<pre class="brush: css">.exemple {
  background: linear-gradient(to bottom right, yellow, green);
  box-shadow: 8px 8px 10px 0px deeppink, -5px -5px 5px 0px blue, 5px 5px 15px 0px yellow;
  padding: 0em 1em;
  border-radius: 16px;
  border-style: solid;
  margin-left: 10px;
  font: 24px sans-serif;
  line-height: 2;
}</pre>

<h5 id="HTML">HTML</h5>

<pre class="brush: html">&lt;span class="exemple"&gt;The&lt;br&gt;quick&lt;br&gt;orange fox&lt;/span&gt;</pre>

<h5 id="Résultat_live">Résultat <em>live</em></h5>

<p>{{EmbedLiveSample("Avec_slice_(valeur_initiale)","200","200")}}</p>

<h5 id="Image_équivalente">Image équivalente</h5>

<p><img alt="A screenshot of the rendering of an inline element styled with box-decoration-break:slice and styles given in the example." src="box-decoration-break-inline-slice.png"></p>

<h4 id="Avec_clone">Avec <code>clone</code></h4>

<h5 id="CSS_2">CSS</h5>

<pre class="brush: css">.exemple {
  background: linear-gradient(to bottom right, yellow, green);
  box-shadow: 8px 8px 10px 0px deeppink, -5px -5px 5px 0px blue, 5px 5px 15px 0px yellow;
  padding: 0em 1em;
  border-radius: 16px;
  border-style: solid;
  margin-left: 10px;
  font: 24px sans-serif;
  line-height: 2;

 -webkit-box-decoration-break: clone;
 -o-box-decoration-break: clone;
  box-decoration-break: clone;
}</pre>

<h5 id="HTML_2">HTML</h5>

<pre class="brush: html">&lt;span class="exemple"&gt;The&lt;br&gt;quick&lt;br&gt;orange fox&lt;/span&gt;</pre>

<h5 id="Résultat_live_2">Résultat <em>live</em></h5>

<p>{{EmbedLiveSample("Avec_clone","200","200")}}</p>

<h5 id="Image_équivalente_2">Image équivalente</h5>

<p><img alt="A screenshot of the rendering of an inline element styled with box-decoration-break:clone and styles given in the example" src="box-decoration-break-inline-clone.png"></p>

<h3 id="Gestion_des_fragments_pour_les_boîtes_en_bloc">Gestion des fragments pour les boîtes en bloc</h3>

<p>Voici ce qu'on pourra obtenir de façon analogue avec un élément de bloc sans fragmentation:</p>

<p><img alt="A screenshot of the rendering of the block element used in the examples without any fragmentation." src="box-decoration-break-block.png"></p>

<p>En décomposant le bloc sur trois colonnes, normalement (<code>slice</code>), on aura :</p>

<p><img alt="A screenshot of the rendering of the fragmented block used in the examples styled with box-decoration-break:slice." src="box-decoration-break-block-slice.png"></p>

<p>Si on applique <code>box-decoration-break:clone</code>, voici le résultat :</p>

<p><img alt="A screenshot of the rendering of the fragmented block used in the examples styled with box-decoration-break:clone." src="box-decoration-break-block-clone.png"></p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">État</th>
   <th scope="col">Commentaires</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('CSS3 Fragmentation', '#break-decoration', 'box-decoration-break')}}</td>
   <td>{{Spec2('CSS3 Fragmentation')}}</td>
   <td>Définition initiale</td>
  </tr>
 </tbody>
</table>

<p>{{cssinfo}}</p>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("css.properties.box-decoration-break")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{cssxref("break-after")}}</li>
 <li>{{cssxref("break-before")}}</li>
 <li>{{cssxref("break-inside")}}</li>
</ul>
