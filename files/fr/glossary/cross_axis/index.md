---
title: Axe transversal
slug: Glossary/Cross_Axis
tags:
  - CSS
  - Glossaire
  - axes
translation_of: Glossary/Cross_Axis
original_slug: Glossaire/Axe_transversal
---
<p>L'axe transversal d'une {{glossary("flexbox")}} traverse l'{{glossary("Main Axis","axe principal")}}, donc si la {{glossary("flex-direction")}} et l'axe principal sont <code>row</code> (<em>ligne</em>) ou <code>row-reverse</code> l'axe transversal est en colonne.</p>

<p><img alt="The cross axis runs down the column" src="basics3.png"></p>

<p>Si l'axe principal est <code>column</code> ou <code>column-reverse</code>, l'axe transversal est donc en ligne.</p>

<p><img alt="The cross axis runs along the row." src="basics4.png"></p>

<p>L'alignement des articles sur l'axe transversal est réalisé avec la propriété <code>align-items</code> sur le conteneur flexible ou la propriété <code>align-self</code> sur les éléments individuels. Dans le cas d'un conteneur flexible multi-lignes, avec un espace supplémentaire sur l'axe transversal, vous pouvez utiliser <code>align-content</code> pour contrôler l'espacement des lignes.</p>

<h2 id="En_apprendre_plus">En apprendre plus</h2>

<h3 id="Références_de_la_propriété">Références de la propriété</h3>

<ul>
 <li>{{cssxref("align-content")}}</li>
 <li>{{cssxref("align-items")}}</li>
 <li>{{cssxref("align-self")}}</li>
 <li>{{cssxref("flex-wrap")}}</li>
 <li>{{cssxref("flex-direction")}}</li>
 <li>{{cssxref("flex")}}</li>
</ul>

<h3 id="En_lire_plus">En lire plus</h3>

<ul>
 <li>Guide Flexbox CSS : <em><a href="/fr/docs/Web/CSS/Disposition_flexbox_CSS/Concepts_de_base_flexbox">Les concepts de base pour flexbox</a></em></li>
 <li>Guide Flexbox CSS : <em><a href="/fr/docs/Web/CSS/Disposition_flexbox_CSS/Aligner_des_%C3%A9l%C3%A9ments_dans_un_conteneur_flexible">Aligner des éléments dans un conteneur flexible</a></em></li>
 <li>Guide Flexbox CSS : <em><a href="/fr/docs/Web/CSS/Disposition_flexbox_CSS/Ma%C3%AEtriser_passage_%C3%A0_la_ligne_des_%C3%A9l%C3%A9ments_flexibles">Maîtriser l'enveloppe des éléments flexibles</a></em></li>
</ul>
