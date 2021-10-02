---
title: element.setAttributeNS
slug: Web/API/Element/setAttributeNS
tags:
  - API
  - DOM
  - Element
  - Méthodes
translation_of: Web/API/Element/setAttributeNS
---
<p>{{ APIRef("DOM") }}</p>

<p><code>setAttributeNS</code> ajoute un nouvel attribut ou modifie la valeur d'un attribut avec un espace de noms et un nom donnés.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">element.setAttributeNS(
namespace,
name,
value)</pre>

<ul>
 <li><code>namespace</code> est une chaîne spécifiant l'espace de noms de l'attribut.</li>
 <li><code>name</code> est une chaîne identifiant l'attribut par son nom qualifié ; c'est-à-dire un préfixe d'espace de noms suivi d'un deux-points suivi d'un nom local.</li>
 <li><code>value</code> est la valeur chaîne désirée pour le nouvel attribut.</li>
</ul>

<h2 id="Exemple">Exemple</h2>

<pre class="eval">var d = document.getElementById("d1");
d.setAttributeNS("http://www.mozilla.org/ns/specialspace", "align", "center");
</pre>

<h2 id="Notes">Notes</h2>

<p>{{ DOMAttributeMethods() }}</p>

<p><code>setAttributeNS</code>  est la seule méthode pour les attributs d'espace nom qui attend le nom qualifié complet, c'est-à-dire <code>"namespace:localname"</code>.</p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-ElSetAttrNS">DOM Level 2 Core: setAttributeNS (en)</a> <small>— <a href="http://www.yoyodesign.org/doc/w3c/dom2-core/core.html#ID-ElSetAttrNS">traduction en français</a> (non normative)</small></li>
 <li><a href="https://www.w3.org/TR/DOM-Level-2-Core/glossary.html#dt-qualifiedname">DOM-Level-2-Core: glossary qualified name</a></li>
</ul>
