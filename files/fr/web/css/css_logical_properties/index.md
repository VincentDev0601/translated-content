---
title: CSS Logical Properties
slug: Web/CSS/CSS_Logical_Properties
tags:
  - Aperçu
  - CSS
  - CSS Logical Properties
  - Propriété logique
  - Reference
translation_of: Web/CSS/CSS_Logical_Properties
---
<div>{{CSSRef}}</div>

<p><em><strong>CSS Logical Properties</strong></em> (les propriétés logiques CSS) est un module CSS qui définit une correspondance logique vers les propriétés physiques de contrôle de la mise en page selon le sens de lecture et l'orientation du texte. On aura deux directions logiques : <em>block</em> et <em>inline</em>, perpendiculaires, qui dépendent du sens de l'orientation du document.</p>

<p>Ce module définit également les propriétés logiques et les valeurs pour les propriétés précédemment définies avec <abbr title="Cascading Stylesheets">CSS</abbr> 2.1. Les propriétés logiques sont des propriétés dont l'orientation est relative au mode d'écriture du document et possèdent des propriétés physiques équivalentes.</p>

<h3 id="Dimension_de_bloc_ou_de_ligne">Dimension de bloc ou de ligne</h3>

<p>Les propriétés et valeurs logiques utilisent les termes abstraits <em>bloc</em> (<em>block</em>) ou ligne (<em>inline</em>) afin de décrire leur direction. La signification physique de ces termes dépend du <a href="/fr/docs/Web/CSS/CSS_Writing_Modes">mode d'écriture</a>.</p>

<dl>
 <dt>Dimension de bloc</dt>
 <dd>C'est la dimension perpendiculaire au flux du texte sur une ligne. Autrement dit, il s'agit de la dimension verticale lorsque le texte est écrit dans un mode horizontal et de la dimension horizontale lorsque le texte est écrit verticalement (pour le français, cette dimension correspond donc à l'axe vertical).</dd>
 <dt>Dimension en ligne</dt>
 <dd>C'est la dimension parallèle au flux du texte sur une ligne. Autrement dit, il s'agit de la dimension horizontale lorsque le texte est écrit dans un mode horizontal et de la dimension verticale lorsque le texte est écrit verticalement (pour le français, cette dimension correspond donc à l'axe horizontal).</dd>
</dl>

<h2 id="Référence">Référence</h2>

<h3 id="Propriétés_relatives_au_dimensionnement">Propriétés relatives au dimensionnement</h3>

<ul>
 <li>{{CSSxRef("block-size")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("inline-size")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("max-block-size")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("max-inline-size")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("min-block-size")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("min-inline-size")}} {{Experimental_Inline}}</li>
</ul>

<h3 id="Propriétés_relatives_aux_marges_bordures_et_remplissages">Propriétés relatives aux marges, bordures et remplissages</h3>

<ul>
 <li>{{CSSxRef("border-block")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-color")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-end-color")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-end-style")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-end-width")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-start")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-start-color")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-start-style")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-start-width")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-style")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-block-width")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-color")}} (mot-clé <code>logical</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("border-inline")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-color")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-end-color")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-end-style")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-end-width")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-start")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-start-color")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-start-style")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-start-width")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-style")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-inline-width")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-start-start-radius")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-start-end-radius")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-end-start-radius")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-end-end-radius")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("border-style")}} (mot-clé <code>logical</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("border-width")}} (mot-clé <code>logical</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("margin")}} (mot-clé <code>logical</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("margin-block")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("margin-block-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("margin-block-start")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("margin-inline")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("margin-inline-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("margin-inline-start")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("padding")}} (mot-clé <code>logical</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("padding-block")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("padding-block-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("padding-block-start")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("padding-inline")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("padding-inline-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("padding-inline-start")}} {{Experimental_Inline}}</li>
</ul>

<h3 id="Propriétés_relatives_aux_flottements_et_au_positionnement">Propriétés relatives aux flottements et au positionnement</h3>

<ul>
 <li>{{CSSxRef("clear")}} (mots-clés <code>inline-end</code> {{Experimental_Inline}} et <code>inline-start</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("float")}} (mots-clés <code>inline-end</code> {{Experimental_Inline}} et <code>inline-start</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("inset")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("inset-block")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("inset-block-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("inset-block-start")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("inset-inline")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("inset-inline-end")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("inset-inline-start")}} {{Experimental_Inline}}</li>
</ul>

<h3 id="Autres_propriétés">Autres propriétés</h3>

<ul>
 <li>{{CSSxRef("caption-side")}} (mots-clés <code>inline-end</code> {{Experimental_Inline}} et <code>inline-start</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("overflow-block")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("overflow-inline")}} {{Experimental_Inline}}</li>
 <li>{{CSSxRef("resize")}} {{Experimental_Inline}} (mots-clés <code>block</code> {{Experimental_Inline}} et <code>inline</code> {{Experimental_Inline}})</li>
 <li>{{CSSxRef("text-align")}} (mots-clés <code>end</code> {{Experimental_Inline}} et <code>start</code> {{Experimental_Inline}})</li>
</ul>

<h3 id="Propriétés_dépréciées">Propriétés dépréciées</h3>

<ul>
 <li>{{CSSxRef("inset-block-end")}} {{Non-standard_Inline}} {{Deprecated_Inline}} (désormais {{CSSxRef("inset-block-end")}} {{Experimental_Inline}})</li>
 <li>{{CSSxRef("inset-block-start")}} {{Non-standard_Inline}} {{Deprecated_Inline}} (désormais {{CSSxRef("inset-block-start")}} {{Experimental_Inline}})</li>
 <li>{{CSSxRef("inset-inline-end")}} {{Non-standard_Inline}} {{Deprecated_Inline}} (désormais {{CSSxRef("inset-inline-end")}} {{Experimental_Inline}})</li>
 <li>{{CSSxRef("inset-inline-start")}} {{Non-standard_Inline}} {{Deprecated_Inline}} (désormais {{CSSxRef("inset-inline-start")}} {{Experimental_Inline}})</li>
</ul>

<h2 id="Guides">Guides</h2>

<ul>
 <li><a href="/fr/docs/Web/CSS/CSS_Logical_Properties/Basic_concepts">Concepts de base pour les propriétés logiques et les valeurs logiques</a></li>
 <li><a href="/fr/docs/Web/CSS/CSS_Logical_Properties/Sizing">Les propriétés logiques utiles au dimensionnement</a></li>
 <li><a href="/fr/docs/Web/CSS/CSS_Logical_Properties/Margins_borders_padding">Les propriétés logiques utiles aux marges, bordures et remplissage (<em>padding</em>)</a></li>
 <li><a href="/fr/docs/Web/CSS/CSS_Logical_Properties/Floating_and_positioning">Les propriétés logiques utiles aux flottements et au positionnement</a></li>
</ul>

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
   <td>{{SpecName("CSS Logical Properties")}}</td>
   <td>{{Spec2("CSS Logical Properties")}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_générale">Compatibilité générale</h2>

<p>De façon générale :</p>

<ul>
 <li>Firefox prend en charge les propriétés logiques lorsqu'il existe une correspondance directe avec les propriétés physiques.</li>
 <li>Idem pour Chrome à partir de la version 69.</li>
 <li>Edge ne prend actuellement (décembre 2018) pas en charge ces propriétés.</li>
 <li>Firefox 66 introduit la prise en charge de deux valeurs raccourcies qui sont également derrière un <em>flag</em> pour Chrome.</li>
</ul>

<p>Pour des informations précises sur chaque propriété, se référer au tableau de compatibilité des pages des propriétés.</p>
