---
title: element.nextSibling
slug: Web/API/Node/nextSibling
tags:
  - API
  - DOM
  - Noeuds
  - Propriétés
translation_of: Web/API/Node/nextSibling
---
<p>{{APIRef("DOM")}}</p>

<p>La propriété en lecture seule  <code><strong>Node.nextSibling</strong></code> renvoie le nœud (<code>node</code>) suivant immédiatement le nœud spécifié dans la liste des enfants ( {{domxref("Node.childNodes","childNodes")}}) de son nœud parent, ou <code>null</code> si le nœud spécifié est le dernier dans cette liste.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><var>nextNode</var> = <var>node</var>.nextSibling
</pre>

<h2 id="Notes">Notes</h2>

<p></p><p>Les navigateurs basés sur Gecko insèrent des nœuds texte dans un document pour représenter des espaces
    vides dans le balisage source. Par conséquent, un nœud obtenu par exemple via <a href="/fr/docs/Web/API/Node/firstChild"><code>Node.firstChild</code></a> ou
    <a href="/fr/docs/Web/API/Node/previousSibling" title='{{APIRef("DOM")}}'><code>Node.previousSibling</code></a> peut faire référence à un nœud texte contenant des espaces plutôt qu'au véritable élément
    que l'auteur comptait obtenir.</p>

    <p>Consultez <a href="/fr/docs/Gestion_des_espaces_dans_le_DOM">Gestion des espaces dans le DOM</a>
    et <a href="http://www.w3.org/DOM/faq.html#emptytext" rel="noopener"><i>Why are some Text nodes empty?</i>
    dans la FAQ DOM 3 du W3C</a> pour plus d'informations.</p><p></p>

<p>{{domxref("Element.nextElementSibling")}} peut être utilisé pour obtenir l'élément suivant en ignorant les noeuds d'espace.</p>

<h2 id="Exemple">Exemple</h2>

<pre class="brush:html">&lt;div id="div-01"&gt;Here is div-01&lt;/div&gt;
&lt;div id="div-02"&gt;Here is div-02&lt;/div&gt;

&lt;script type="text/javascript"&gt;
var el = document.getElementById('div-01').nextSibling,
    i = 1;

console.log('Siblings of div-01:');

while (el) {
  console.log(i + '. ' + el.nodeName);
  el = el.nextSibling;
  i++;
}

&lt;/script&gt;

/**************************************************
  Ce qui suit est écrit sur la console pendant le chargement:

     Siblings of div-01

      1. #text
      2. DIV
      3. #text
      4. SCRIPT

**************************************************/</pre>

<p>Dans cet exemple, on peut voir que des nœuds <code>#text</code> sont insérés dans le DOM là où des espaces se trouvent dans le code source entre les balises (c'est-à-dire après la balise de fermeture d'un élément et avant la balise d'ouverture du suivant). Aucun espace n'est créé entre les éléments insérés par l'instruction <code>document.write</code> .</p>

<p>L'inclusion possible de nœuds textes dans le DOM doit être prise en compte pour le parcours du DOM à l'aide de <code>nextSibling</code>. Consultez les ressources dans la section Notes .</p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<ul>
 <li><a href="http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html#attribute-nextSibling">DOM Level 1 Core: nextSibling</a> <small>— <a href="http://xmlfr.org/w3c/TR/REC-DOM-Level-1/level-one-core.html#attribute-nextSibling">traduction</a> (non normative)</small></li>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-Core/core.html#ID-6AC54C2F">DOM Level 2 Core: nextSibling</a> <small>— <a href="http://www.yoyodesign.org/doc/w3c/dom2/core/core.html#ID-6AC54C2F">traduction</a> (non normative)</small></li>
</ul>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.Node.nextSibling")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<p>{{domxref("Element.nextElementSibling")}}</p>
