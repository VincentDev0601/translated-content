---
title: element.removeChild
slug: Web/API/Node/removeChild
tags:
  - API
  - DOM
  - Enfant
  - Méthodes
  - Noeuds
  - Suppression
translation_of: Web/API/Node/removeChild
---
<p>{{ ApiRef("DOM") }}</p>

<p>La méthode <code><strong>Node.removeChild()</strong></code> retire un nœud enfant de l'arbre DOM et retourne le nœud retiré.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><em>var oldChild</em> = <em>node</em>.removeChild(<em>child</em>);
<strong>OR</strong>
<em>node</em>.removeChild(<em>child</em>);
</pre>

<ul>
 <li><code>child</code> est le nœud enfant à retirer du DOM.</li>
 <li><code>node </code>est le nœud parent de <code>child</code>.</li>
 <li><code>oldchild</code> conserve une référence au nœud enfant retiré. <code>oldchild</code> === <code>child</code>.</li>
</ul>

<p>Le nœud enfant retiré existe toujours en mémoire, mais ne fait plus partie du DOM. Avec la première syntaxe, il est possible de réutiliser ultérieurement dans le code le nœud retiré, à l'aide de la référence à l'objet <code>ancienEnfant</code><em>. </em></p>

<p>Avec la seconde forme montrée en exemple, aucune référence à l'objet <code>ancienEnfant</code> n'est conservée ; ainsi, en supposant que votre code n'a conservé nulle part ailleurs cette référence à ce nœud, il devient immédiatement inutilisable et irrécupérable, et sera en général <a href="/fr/docs/Web/JavaScript/Gestion_de_la_m%C3%A9moire">automatiquement supprimé</a> de la mémoire après un court moment.</p>

<p>Si  <code>child</code> n'est pas un enfant du noeud  <code>element</code>, la méthode provoque une exception. Une exception sera aussi lancée dans la cas où le nœud <code>enfant </code>est bien un enfant du nœud <code>element </code>au moment de l'appel à la méthode, mais qu'il a été retiré par un gestionnaire d'événement invoqué dans la cadre d'une tentative de suppression du nœud <code>element </code>(comme <em>blur</em>).</p>

<p>La méthode peut lever une exception de deux façons :</p>

<ol>
 <li>Si <code>enfant</code> était bien un enfant de element et qu'il existe donc dans le DOM, mais qu'il a déjà été retiré, la méthode provoque l'exception suivante :<code>​​</code><br>
  <code>Uncaught NotFoundError: Failed to execute 'removeChild' on 'element': The node to be removed is not a child of this node</code>.</li>
 <li>si l'<code>enfant</code> n'existe pas dans le DOM de la page, la méthode provoque l'exception suivante :<br>
  <code>Uncaught TypeError: Failed to execute 'removeChild' on 'element': parameter 1 is not of type 'Node'.</code></li>
</ol>

<h2 id="Exemples">Exemples</h2>

<pre class="brush: html">&lt;!--Sample HTML code--&gt;
&lt;div id="top" align="center"&gt; &lt;/div&gt;

&lt;script type="text/javascript"&gt;
      var top = document.getElementById("top");
      var nested = document.getElementById("nested");

      var garbage = top.removeChild(nested);    //Cas test 2: la méthode lance l'exception (2)

&lt;/script&gt;

&lt;!--Sample HTML code--&gt;
&lt;div id="top" align="center"&gt;
 &lt;div id="nested"&gt;&lt;/div&gt;
&lt;/div&gt;

&lt;script type="text/javascript"&gt;
      var top = document.getElementById("top");
      var nested = document.getElementById("nested");

      var garbage = top.removeChild(nested); // Ce premier appel supprime correctement le noeud

      // ......
      garbage = top.removeChild(nested);   // Cas test 1 : la méthode dans le second appel ici, lance l'exception (1)

&lt;/script&gt;</pre>

<pre class="brush: html">&lt;!--Sample HTML code--&gt;

&lt;div id="top" align="center"&gt;
  &lt;div id="nested"&gt;&lt;/div&gt;
&lt;/div&gt;</pre>

<pre class="brush:js">// Supprime un élément spécifié quand son noeud parent est connu
var d = document.getElementById("top");
var d_nested = document.getElementById("nested");
var throwawayNode = d.removeChild(d_nested);</pre>

<pre class="brush:js">// Supprime un élément spécifié sans avoir à spécifier son noeud parent
var node = document.getElementById("nested");
if (node.parentNode) {
  node.parentNode.removeChild(node);
}</pre>

<pre class="brush:js">
// Supprime tous les enfant d'un élément
var element = document.getElementById("top");
while (element.firstChild) {
  element.removeChild(element.firstChild);
}</pre>

<h2 id="Sp.C3.A9cification">Spécifications</h2>

<ul>
 <li><a href="http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html#method-removeChild">DOM Level 1 Core: removeChild</a> — <a href="http://xmlfr.org/w3c/TR/REC-DOM-Level-1/level-one-core.html#method-removeChild">traduction en français</a> (non normative)</li>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-1734834066">DOM Level 2 Core: removeChild</a> — <a href="http://www.yoyodesign.org/doc/w3c/dom2/core/core.html#ID-1734834066">traduction en français</a> (non normative)</li>
 <li><a href="http://www.w3.org/TR/DOM-Level-3-Core/core.html#ID-1734834066">DOM Level 3 Core: removeChild</a></li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{domxref("Node.replaceChild")}}</li>
 <li>{{domxref("Node.parentNode")}}</li>
 <li>{{domxref("ChildNode.remove")}}</li>
</ul>
