---
title: Utiliser l'attribut aria-required
slug: Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-required_attribute
tags:
  - ARIA
  - Accessibilité
  - Attribut
translation_of: Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-required_attribute
original_slug: Accessibilité/ARIA/Techniques_ARIA/Utiliser_l_attribut_aria-required
---
<h3 id="Description">Description</h3>

<p>Cette technique présente l’utilisation de l’attribut <a href="http://www.w3.org/TR/wai-aria/states_and_properties#aria-required"><code>aria-required</code></a>.</p>

<p>L’attribut <code>aria-required</code> est utilisé pour indiquer que l’utilisateur doit obligatoirement remplir un champ de formulaire avant de le soumettre. Cet attribut peut être utilisé avec n’importe quel élément de formulaire HTML ; il n’est pas limité aux éléments auxquels a été assigné un <code>rôle</code> ARIA.</p>

<p>{{ HTMLVersionInline("5") }} a introduit l’attribut <a href="/fr/docs/Web/HTML/Attributes"><code>required</code></a>, mais <code>aria-required</code> est toujours utile pour les agents utilisateurs qui ne prennent pas encore en charge HTML5.</p>

<h3 id="Valeurs">Valeurs</h3>

<p><code>true</code> ou <code>false</code> (Valeur par défaut : <code>false</code>)</p>

<h3 id="Effets_possibles_sur_les_agents_utilisateurs_et_les_technologies_d’assistance">Effets possibles sur les agents utilisateurs et les technologies d’assistance</h3>

<p>Les lecteurs d’écran devraient annoncer le champ comme étant obligatoire.</p>

<p>Remarquez que cet attribut ne changera pas automatiquement la présentation du champ.</p>

<div class="note"><p><strong>Note :</strong> il existe plusieurs points de vue sur la façon dont les technologies d’assistance devraient traiter cette technique. L’information fournie ci-dessus est l’une de ces opinions et n’est pas normative.</p></div>

<h3 id="Exemples">Exemples</h3>

<h4 id="Exemple_1_un_formulaire_simple">Exemple 1 : un formulaire simple</h4>

<pre class="brush: html">&lt;form action="post"&gt;
  &lt;label for="prenom"&gt;Prénom&amp;nbsp;:&lt;/label&gt;
  &lt;input id="prenom" type="text" aria-required="true"&gt;
  &lt;br/&gt;
  &lt;label for="nom"&gt;Nom&amp;nbsp;:&lt;/label&gt;
  &lt;input id="nom" type="text" aria-required="true"&gt;
  &lt;br/&gt;
  &lt;label for="adresse"&gt;Adresse&amp;nbsp;:&lt;/label&gt;
  &lt;input id="adresse" type="text"&gt;
&lt;/form&gt;
</pre>

<h3 id="Notes">Notes</h3>

<h3 id="Utilisé_dans_les_rôles_ARIA">Utilisé dans les rôles ARIA</h3>

<ul>
 <li>Combobox ;</li>
 <li>Gridcell ;</li>
 <li>Listbox ;</li>
 <li>Radiogroup ;</li>
 <li>Spinbutton ;</li>
 <li><a href="/fr/Accessibilité/ARIA/Techniques_ARIA/Utiliser_le_rôle_textbox">Textbox</a> ;</li>
 <li>Tree.</li>
</ul>

<h3 id="Techniques_ARIA_connexes">Techniques ARIA connexes</h3>

<ul>
 <li><a href="/fr/Accessibilité/ARIA/Techniques_ARIA/Utiliser_l_attribut_aria-invalid">Utiliser l’attribut <code>aria-invalid</code></a></li>
</ul>

<h3 id="Autres_ressources">Autres ressources</h3>

<ul>
 <li><a href="http://www.w3.org/TR/wai-aria/states_and_properties#aria-required">Spécification WAI-ARIA pour <code>aria-required</code></a> ;</li>
 <li><a href="http://www.w3.org/TR/wai-aria-practices/#ariaform">WAI-ARIA Authoring Practices for forms</a> (Règles WAI-ARIA de création de formulaires) ;</li>
 <li><a href="/fr/docs/Web/Guide/HTML/HTML5/Constraint_validation">Validation de condition</a> en {{ HTMLVersionInline("5") }}.</li>
</ul>
