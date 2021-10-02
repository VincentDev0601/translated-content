---
title: element.normalize
slug: Web/API/Node/normalize
translation_of: Web/API/Node/normalize
---
<p>{{ ApiRef("DOM") }}</p>

<h2 id="R.C3.A9sum.C3.A9">Résumé</h2>

<p>Place le nœud spécifié et tout son sous-arbre dans une forme « normale ». Dans un sous-arbre normalisé, aucun nœud texte n'est vide et il n'y a pas de nœuds texte adjacents.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="eval"><em>élément</em>.normalize();
</pre>

<h2 id="Exemple">Exemple</h2>

<pre class="brush:js">var conteneur = document.createElement("div");
conteneur.appendChild( document.createTextNode("Partie 1 ") );
conteneu.appendChild( document.createTextNode("Partie 2 ") );

// Ici, conteneur.childNodes.length === 2
// conteneur.childNodes[0].textContent === "Partie 1 "
// conteneur.childNodes[1].textContent === "Partie 2 "

conteneur.normalize();

// À présent, conteneur.childNodes.length === 1
// conteneur.childNodes[0].textContent === "Partie 1 Partie 2 "</pre>

<h2 id="Notes">Notes</h2>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-normalize">DOM Level 2 Core: Node.normalize (en)</a> <small>— <a href="http://www.yoyodesign.org/doc/w3c/dom2-core/core.html#ID-normalize">traduction en français</a> (non normative)</small></li>
</ul>