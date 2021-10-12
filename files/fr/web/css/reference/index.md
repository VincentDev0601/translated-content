---
title: Référence CSS
slug: Web/CSS/Reference
tags:
  - CSS
  - CSS Data Types
  - I10n:priority
  - Overview
  - Reference
  - Types CSS
translation_of: Web/CSS/Reference
---
<div>{{CSSRef}}</div>

<p>Cette <strong>référence CSS</strong> fournit un <strong><a href="#index_des_mots-clés">index alphabétique</a></strong> de toutes les propriétés <a href="/fr/docs/Web/CSS">CSS</a> standards, des <a href="/fr/docs/Web/CSS/Pseudo-classes">pseudo-classes</a>, des <a href="/fr/docs/Web/CSS/Pseudo-elements">pseudo-éléments</a>, des <a href="/fr/docs/Web/CSS/CSS_Types">types de données</a> et des <a href="/fr/docs/Web/CSS/At-rule">règles @</a>. Vous pouvez également trouver une liste alphabétique de tous les <strong><a href="#sélecteurs">sélecteurs CSS par type</a></strong> et une liste des <strong><a href="#concepts">concepts clés de CSS</a></strong>. Enfin est inclus un bref sommaire de <strong><a href="#dom-css_cssom">référence sur DOM-CSS / CSSOM</a></strong>.</p>

<h2 id="Syntaxe_de_règle_basique">Syntaxe de règle basique</h2>

<h3 id="Syntaxe_de_style_basique">Syntaxe de style basique</h3>

<pre class="syntaxbox"><var>règle-de-style-basique</var> <strong>::=</strong>
    <var>liste-de-sélecteurs</var> <strong>{</strong>
      <var>liste-de-propriétés</var>
    <strong>}</strong>
</pre>

<p>... où :</p>

<pre class="syntaxbox"><var>liste-de-sélecteurs</var> <strong>::=</strong>
    <var>sélecteur[</var><strong>:</strong><var>pseudo-classe] [</var><strong>::</strong><var>pseudo-élément]
    [</var><strong>,</strong><var> liste-de-sélecteurs]</var>

<var>liste-de-propriétés</var> <strong>::=</strong>
<var>    [propriété </var><strong>:</strong> <var>valeur] [</var><strong>; </strong><var>liste-de-propriétés]</var>
</pre>

<p>Voir aussi les <a href="#sélecteurs"><em>sélecteurs</em></a>, <a href="#pseudo-classes"><em>pseudo-classes</em></a>, et <em><a href="#pseudo-éléments">pseudo-éléments</a></em> listés ci-dessous. La syntaxe des <em>valeurs</em> dépend du type de données attendu pour chaque <em>propriété</em> indiquée.</p>

<h4 id="Exemples_de_règle_de_style">Exemples de règle de style</h4>

<pre class="brush: css">strong {
  color: red;
}

div.menu-bar li:hover &gt; ul {
  display: block;
}
</pre>

<p>Pour une introduction à la syntaxe des sélecteurs CSS, consultez <a href="/fr/docs/Apprendre/CSS/Introduction_%C3%A0_CSS/La_syntaxe">ce tutoriel</a>. Soyez conscient que n’importe quelle erreur de <a href="/fr/docs/Learn/CSS/First_steps/How_CSS_is_structured">syntaxe CSS</a> dans une définition de règle l’invalide entièrement. Les règles non validées sont ignorées par le navigateur. Note : les définitions de règles CSS sont intégralement <a href="https://www.w3.org/TR/css-syntax-3/#intro">basées sur du texte</a> (ASCII) alors que DOM-CSS / CSSOM (le système de gestion des règles) est <a href="https://www.w3.org/TR/cssom/#introduction">basé sur des objets</a>.</p>

<h3 id="Syntaxe_des_règles"><strong>Syntaxe des règles @</strong></h3>

<p>Comme la structure des règles @ varie grandement, veuillez consulter <a href="/fr/docs/Web/CSS/At-rule">règle @</a> pour trouver la syntaxe que vous souhaitez.</p>

<h2 id="Index_des_mots-clés"><strong>Index des mots-clés</strong></h2>

<div class="note">
<p><strong>Note :</strong> Les noms de propriétés de cet index n’incluent <strong>pas</strong> les <a href="/fr/docs/Web/CSS/CSS_Properties_Reference">noms de l’API DOM JavaScript</a> lorsqu’ils sont différents des noms standards CSS.</p>
</div>

<p>{{CSS_Ref}}</p>

<h2 id="Sélecteurs">Sélecteurs</h2>

<p>Sont indiqués dans ce qui suit les divers <a href="/fr/docs/Web/CSS/CSS_Selectors">sélecteurs</a>, qui permettent aux styles d'être appliqués de façon conditionnelle selon diverses caractéristiques des éléments présents dans le DOM.</p>

<h3 id="Sélecteurs_simples"><a href="/fr/docs/Web/CSS/CSS_Selectors#les_s%c3%a9lecteurs_simples/fr/docs/web/css/s%c3%a9lecteurs_css">Sélecteurs simples</a></h3>

<p>Les sélecteurs simples sont des sélecteurs fondamentaux. Ce sont les sélecteurs les plus élémentaires qui sont fréquemment combinés pour créer d'autres sélecteurs plus complexes.</p>

<ul>
 <li><a href="/fr/docs/Web/CSS/Type_selectors">Sélecteur de type</a> <code><var>nomElement</var></code></li>
 <li><a href="/fr/docs/Web/CSS/Class_selectors">Sélecteur de classe</a> <code><strong>.</strong><var>nomClasse</var></code></li>
 <li><a href="/fr/docs/Web/CSS/ID_selectors">Sélecteur d’identifiant</a> <code><strong>#</strong><var>nomID</var></code></li>
 <li><a href="/fr/docs/Web/CSS/Universal_selectors">Sélecteur universel</a> <code><strong>*</strong></code>, <code><var>ns</var><strong>|*</strong></code>, <code><strong>*|*</strong></code>, <code><strong>|*</strong></code></li>
 <li><a href="/fr/docs/Web/CSS/Attribute_selectors">Sélecteur d’attribut</a> <code><strong>[</strong><var>attr</var><strong>=</strong><var>valeur</var><strong>]</strong></code></li>
</ul>

<h3 id="Sélecteur_de_groupe">Sélecteur de groupe</h3>

<dl>
 <dt><a href="/fr/docs/Web/CSS/Selector_list">Sélecteur de conjonction</a> <code>A, B</code></dt>
 <dd>Indique que les éléments des sélecteurs <code>A</code> et <code>B</code> doivent être sélectionnés. Il s'agit d'une méthode de groupement pour sélectionner des éléments selon plusieurs critères.</dd>
</dl>

<h3 id="Combinateurs"><a href="/fr/docs/Web/CSS/CSS_Selectors#les_combinateurs">Combinateurs</a></h3>

<p>Les combinateurs sont des sélecteurs qui établissent une relation entre deux sélecteurs ou plus, tel que "A est un enfant de B" ou "A est adjacent à B".</p>

<dl>
 <dt><a href="/fr/docs/Web/CSS/Adjacent_sibling_combinator">Combinateur de voisin direct</a> <code><var>A</var> <strong>+</strong> <var>B</var></code></dt>
 <dd>Indique que les éléments sélectionnés par <code>A</code> et par <code>B</code> ont le même parent et que celui sélectionné par <code>B</code> suit immédiatement celui sélectionné par <code>A</code>.</dd>
 <dt><a href="/fr/docs/Web/CSS/General_sibling_combinator">Combinateur de voisin général</a> <code><var>A</var> <strong>~</strong> <var>B</var></code></dt>
 <dd>Indique que les éléments sélectionnés par <code>A</code> et par <code>B</code> ont le même parent et que celui sélectionné par <code>B</code> suit celui sélectionné par <code>A</code>, mais pas nécessairement immédiatement après lui.</dd>
 <dt><a href="/fr/docs/Web/CSS/Child_combinator">Combinateur d’enfant</a> <code><var>A</var> <strong>&gt;</strong> <var>B</var></code></dt>
 <dd>Indique que l’élément sélectionné par <code>B</code> est un enfant direct de l’élément sélectionné par <code>A</code>.</dd>
 <dt><a href="/fr/docs/Web/CSS/Descendant_combinator">Combinateur de descendant</a> <code><var>A</var> <var>B</var></code></dt>
 <dd>Indique que l’élément sélectionné par <code>B</code> est un descendant de l’élément sélectionné par <code>A</code>, mais n’en est pas nécessairement un enfant direct.</dd>
 <dt><a href="/fr/docs/Web/CSS/Column_combinator">Combinateur de colonne</a> <code><var>A</var> <strong>||</strong> <var>B</var></code> {{Experimental_Inline}}</dt>
 <dd>Indique que l’élément sélectionné par <code>B</code> est situé dans la colonne de table indiquée par <code>A</code>. Les éléments qui s’étendent sur des colonnes multiples sont considérés comme étant membres de chacune de ces colonnes.</dd>
</dl>

<h3 id="Pseudo">Pseudo</h3>

<dl>
 <dt><a href="/fr/docs/Web/CSS/Pseudo-classes">Pseudo-classes</a> <code>:</code></dt>
 <dd>Définit un état spécial pour le ou les éléments ciblés.</dd>
 <dt><a href="/fr/docs/Web/CSS/Pseudo-elements">Pseudo-éléments</a> <code>::</code></dt>
 <dd>Représente des entités qui ne sont pas incluses en HTML.</dd>
</dl>

<div class="callout">
<p>See also <a href="https://www.w3.org/TR/selectors/#overview">Selectors in the Selectors Level 4 specification</a>.</p>
</div>

<h2 id="Concepts">Concepts</h2>

<h3 id="Syntaxe_et_sémantique">Syntaxe et sémantique</h3>

<ul>
 <li><a href="/fr/docs/Learn/CSS/First_steps/How_CSS_is_structured">Syntaxe CSS</a></li>
 <li><a href="/fr/docs/Web/CSS/At-rule">Règles @ (<em>at-rules</em>)</a></li>
 <li><a href="/fr/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance">Cascade</a></li>
 <li><a href="/fr/docs/Web/CSS/Comments">Commentaires</a></li>
 <li><a href="/fr/docs/Glossary/Descriptor_(CSS)">Descripteurs</a></li>
 <li><a href="/fr/docs/Web/CSS/inheritance">Héritage</a></li>
 <li><a href="/fr/docs/Web/CSS/Shorthand_properties">Propriétés raccourcies</a></li>
 <li><a href="/fr/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance#sp%c3%a9cificit%c3%a9">Spécificité</a></li>
 <li><a href="/fr/docs/Web/CSS/Value_definition_syntax">Syntaxe de définition des valeurs</a></li>
 <li><a href="/fr/docs/Web/CSS/CSS_Values_and_Units">Unités et valeurs CSS</a></li>
</ul>

<h3 id="Valeurs">Valeurs</h3>

<ul>
 <li><a href="/fr/docs/Web/CSS/actual_value">Valeur réelle</a></li>
 <li><a href="/fr/docs/Web/CSS/computed_value">Valeur calculée</a></li>
 <li><a href="/fr/docs/Web/CSS/initial_value">Valeur initiale</a></li>
 <li><a href="/fr/docs/Web/CSS/resolved_value">Valeur résolue</a></li>
 <li><a href="/fr/docs/Web/CSS/specified_value">Valeur spécifiée</a></li>
 <li><a href="/fr/docs/Web/CSS/used_value">Valeur utilisée</a></li>
</ul>

<h3 id="Disposition">Disposition</h3>

<ul>
 <li><a href="/fr/docs/Web/Guide/CSS/Block_formatting_context">Contexte de formatage de bloc</a></li>
 <li><a href="/fr/docs/Learn/CSS/Building_blocks/The_box_model">Modèle de boîte</a></li>
 <li><a href="/fr/docs/Web/CSS/Containing_block">Bloc englobant</a></li>
 <li><a href="/fr/docs/Web/CSS/Layout_mode">Modes de disposition</a></li>
 <li><a href="/fr/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing">Fusion des marges</a></li>
 <li><a href="/fr/docs/Web/CSS/Replaced_element">Éléments remplacés</a></li>
 <li><a href="/fr/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context">Contexte d'empilement</a></li>
 <li><a href="/fr/docs/Web/CSS/Visual_formatting_model">Modèle de mise en forme visuelle</a></li>
</ul>

<h2 id="DOM-CSS_CSSOM">DOM-CSS / CSSOM</h2>

<h3 id="Principaux_types_dobjets">Principaux types d'objets</h3>

<ul>
 <li>{{DOMxRef("Document.styleSheets")}}</li>
 <li><code>{{DOMxRef("StyleSheetList", "styleSheets", "", 1)}}[i].{{DOMxRef("CSSRuleList", "cssRules", "", 1)}}</code></li>
 <li><code>cssRules[i].{{DOMxRef("CSSRule.cssText", "cssText", "", 1)}}</code> (sélecteur et style)</li>
 <li><code>cssRules[i].{{DOMxRef("CSSStyleRule.selectorText", "selectorText", "", 1)}}</code></li>
 <li>{{DOMxRef("HTMLElement.style")}}</li>
 <li><code>HTMLElement.style.{{DOMxRef("CSSStyleDeclaration.cssText", "cssText", "", 1)}}</code> (style uniquement)</li>
 <li>{{DOMxRef("Element.className")}}</li>
 <li>{{DOMxRef("Element.classList")}}</li>
</ul>

<h3 id="Méthodes_importantes">Méthodes importantes</h3>

<ul>
 <li>{{DOMxRef("CSSStyleSheet.insertRule()")}}</li>
 <li>{{DOMxRef("CSSStyleSheet.deleteRule()")}}</li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/CSS/Mozilla_Extensions">Extensions spécifiques de Mozilla à CSS</a> (préfixées avec <code>-moz-</code>)</li>
 <li><a href="/fr/docs/Web/CSS/WebKit_Extensions">Extensions spécifiques de WebKit à CSS</a> (préfixées pour la plupart avec <code>-webkit-</code>)</li>
 <li><a href="/fr/docs/Web/CSS/Microsoft_Extensions">Extensions spécifiques de Microsoft à CSS</a> (préfixées pour la plupart avec <code>-ms-</code>)</li>
</ul>
