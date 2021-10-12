---
title: flex-flow
slug: Web/CSS/flex-flow
tags:
  - CSS
  - Propriété
  - Reference
translation_of: Web/CSS/flex-flow
---
<div>{{ CSSRef}}</div>

<p>La propriété CSS <strong><code>flex-flow</code></strong> est une <a href="/fr/docs/Web/CSS/Propri%C3%A9t%C3%A9s_raccourcies">propriété raccourcie</a> pour les propriétés {{cssxref("flex-direction")}} et {{cssxref("flex-wrap")}}.</p>

<div>{{EmbedInteractiveExample("pages/css/flex-flow.html")}}</div>

<p>Pour plus d'informations, voir la page <a href="/fr/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox">Utiliser les boîtes flexibles (<em>flexbox</em>) CSS</a>.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush:css no-line-numbers">/* flex-flow: &lt;'flex-direction'&gt; */
flex-flow: row;
flex-flow: row-reverse;
flex-flow: column;
flex-flow: column-reverse;

/* flex-flow: &lt;'flex-wrap'&gt; */
flex-flow: nowrap;
flex-flow: wrap;
flex-flow: wrap-reverse;

/* flex-flow: &lt;'flex-direction'&gt; et &lt;'flex-wrap'&gt; */
flex-flow: row nowrap;
flex-flow: column wrap;
flex-flow: column-reverse wrap-reverse;

/* Valeurs globales */
flex-flow: inherit;
flex-flow: initial;
flex-flow: unset;
</pre>

<h3 id="Valeurs">Valeurs</h3>

<p>Voir {{cssxref("flex-direction")}} et {{cssxref("flex-wrap")}} pour plus d'informations sur les valeurs que peuvent prendre ces deux propriétés.</p>

<h3 id="Syntaxe_formelle">Syntaxe formelle</h3>

{{csssyntax}}

<h2 id="Exemples">Exemples</h2>

<pre class="brush:css">element {

  /* L'axe principal sera la direction de bloc  */
  /* et on commencera par le bas (main-start et */
  /* main-end inversés. Les éléments flexibles  */
  /* passent sur une nouvelle ligne si besoin   */

  flex-flow: column-reverse wrap;

}
</pre>

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
   <td>{{SpecName('CSS3 Flexbox','#flex-flow-property','flex-flow')}}</td>
   <td>{{Spec2('CSS3 Flexbox')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<p>{{cssinfo}}</p>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("css.properties.flex-flow")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>Guide sur les boîtes flexibles : <em><a href="/fr/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox">Les concepts de bases</a></em></li>
 <li>Guide sur les boîtes flexibles : <em><a href="/fr/docs/Web/CSS/CSS_Flexible_Box_Layout/Ordering_Flex_Items">Ordonner les éléments flexibles</a></em></li>
</ul>
