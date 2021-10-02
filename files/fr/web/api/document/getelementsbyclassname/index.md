---
title: document.getElementsByClassName
slug: Web/API/Document/getElementsByClassName
tags:
  - API
  - DOM
  - Méthodes
  - Reference
translation_of: Web/API/Document/getElementsByClassName
---
<p>{{APIRef("DOM")}}</p>

<p>Renvoie un objet de type tableau de tous les éléments enfants qui ont tous les noms de classe donnés. Lorsqu'il est appelé sur l'objet document, le document complet est recherché, y compris le nœud racine. Vous pouvez également appeler {{domxref ("Element.getElementsByClassName", "getElementsByClassName ()")}} sur n'importe quel élément; il retournera uniquement les éléments qui sont les descendants de l'élément racine spécifié avec les noms de classes donnés.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><var>var elements</var> = document.getElementsByClassName(<em>names</em>); // or:
<var>var elements</var> = rootElement.getElementsByClassName(<em>names</em>);</pre>

<ul>
 <li><var>elements</var> est une {{domxref ("HTMLCollection")}} des éléments trouvés.</li>
 <li><var>names</var> est une chaîne représentant le nom de la classe des éléments à trouver.</li>
 <li>getElementsByClassName peut être appelé sur n'importe quel élément, pas seulement sur le document. L'élément sur lequel il est appelé sera utilisé comme racine de la recherche.</li>
</ul>

<h2 id="Exemples">Exemples</h2>

<p>Trouve tous les éléments ayant la classe « test » :</p>

<pre class="eval"> document.getElementsByClassName('test')
</pre>

<p>Trouve tous les éléments ayant les classes « rouge » et « test » :</p>

<pre class="eval"> document.getElementsByClassName('rouge test')
</pre>

<p>Trouve tous les éléments qui ont la classe « test » à l'intérieur d'un élément ayant l'ID « main » :</p>

<pre class="eval"> document.getElementById('main').getElementsByClassName('test')
</pre>

<p>Nous pouvons également utiliser les méthodes de Array.prototype sur toute {{domxref ("HTMLCollection")}} en passant HTMLCollection comme valeur de la méthode. Ici, nous allons trouver tous les éléments div qui ont une classe de 'test':</p>

<pre class="brush: js">var testElements = document.getElementsByClassName('test');
var testDivs = Array.prototype.filter.call(testElements, function(testElement){
    return testElement.nodeName === 'DIV';
});</pre>

<p>XXX writeme == Notes == Une méthode semblable existe pour &lt;code&gt;Element&lt;/code&gt;</p>

<h2 id="Sp.C3.A9cification">Obtenir la classe  des éléments test</h2>

<p>C'est la méthode d'opération la plus couramment utilisée.</p>

<pre class="brush: html">&lt;!doctype html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;title&gt;Document&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id="parent-id"&gt;
        &lt;p&gt;hello word1&lt;/p&gt;
        &lt;p class="test"&gt;hello word2&lt;/p&gt;
        &lt;p &gt;hello word3&lt;/p&gt;
        &lt;p&gt;hello word4&lt;/p&gt;
    &lt;/div&gt;
    &lt;script&gt;
        var parentDOM = document.getElementById("parent-id");

        var test=parentDOM.getElementsByClassName("test");//test is not target element
        console.log(test);//HTMLCollection[1]

        var testTarget=parentDOM.getElementsByClassName("test")[0];//here , this element is target
        console.log(testTarget);//&lt;p class="test"&gt;hello word2&lt;/p&gt;
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>


<p>{{Compat("api.Document.getElementsByClassName")}}</p>



<h2 id="Specification">Spécification</h2>

<ul>
 <li><a href="https://dvcs.w3.org/hg/domcore/raw-file/tip/Overview.html#dom-document-getelementsbyclassname">W3C: getElementsByClassName</a></li>
</ul>
