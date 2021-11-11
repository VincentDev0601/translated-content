---
title: Exported WebAssembly functions
slug: WebAssembly/Exported_functions
translation_of: WebAssembly/Exported_functions
---
<div>{{WebAssemblySidebar}}</div>

<p>Les fonctions WebAssembly exportées sont la représentation des fonctions WebAssembly dans JavaScript. Cet article décrit un plus en détail à quoi elle correspondent...</p>

<h2 id="Exportée..._quoi">Exportée... quoi?</h2>

<p>Les fonctions WebAssembly exportées sont simplement des emballages (wrappers) Javascript autour de fonction WebAssembly afin de les représenter dans un contexte Javascript. Lorsqu'elles sont appelées, une procédure en arrière plan est engagée afin d'obtenir une conversion des types compatible avec WebAssembly (Par exemple convertir <code>numbers</code> en <code>Int32</code>), les arguments sont transmis à la fonction au sein du module wasm, la fonction est invoquée, et enfin le résultat est à nouveau convertit et retourner à Javascript.</p>

<p>Vous pouvez exporter les fonctions WebAssembly de deux manières:</p>

<ul>
 <li>Par un appel à <code><a href="/fr/docs/WebAssembly/API/Table/get">Table.prototype.get()</a></code> sur une table existante.</li>
 <li>Par un appel à une fonction exportée à partir de l'instance d'un module wasm via <code><a href="/fr/docs/WebAssembly/API/Instance/exports">Instance.exports</a></code>.</li>
</ul>

<p>Dans les deux cas, vous obtenez le même genre de wrapper pour la fonction sous jacente. Du point de vue de JavaScript, une fonction wasm est une fonction JavaScript— A la différence prés qu'elles sont encapsulées par l'instance d'une fonction exportée wasm et qu'il y a un nombre limité de façon d'y accéder.</p>

<h2 id="Un_exemple">Un exemple</h2>

<p>Regardons un exemple pour mettre les choses au clair (tu peux le trouver sur GitHub sur <a href="https://github.com/mdn/webassembly-examples/blob/master/other-examples/table-set.html">table-set.html</a>; à voir également en <a href="https://mdn.github.io/webassembly-examples/other-examples/table-set.html">live </a>, et check la <a href="https://github.com/mdn/webassembly-examples/blob/master/js-api-examples/table.wat">representation</a> textuelle wasm):</p>

<pre class="brush: js">var otherTable = new WebAssembly.Table({ element: "anyfunc", initial: 2 });

WebAssembly.instantiateStreaming(fetch('table.wasm'))
.then(obj =&gt; {
  var tbl = obj.instance.exports.tbl;
  console.log(tbl.get(0)());  // 13
  console.log(tbl.get(1)());  // 42
  otherTable.set(0,tbl.get(0));
  otherTable.set(1,tbl.get(1));
  console.log(otherTable.get(0)());
  console.log(otherTable.get(1)());
});</pre>

<p>Dans cet exemple, nous créons une table (<code>otherTable</code>) à partir de JavaScript en utilisant le constructeur {{jsxref("WebAssembly.Table")}}, puis nous chargeons table.wasm dans notre page en utilisant la méthode {{jsxref("WebAssembly.instantiateStreaming()")}}.</p>

<p>Nous pouvons ensuite accéder aux fonctions exportées à partir du module, récupérer les références de chaque fonction via  <code><a href="/fr/docs/WebAssembly/API/Table/get">tbl.get()</a></code> et logguer le résultat de chacune d'elles dans la console. Enfin, nous utilisons <code>set()</code> avec la table <code>otherTable</code> afin de lui fournir les references aux mêmes functions que la table <code>tbl</code>.</p>

<p>Pour vérifier que cela à fonctionné correctement, nous récupérons les références de la table <code>otherTable</code> et imprimons également les résultats dans la console, et les résultats sont identiques aux précédents.</p>

<h2 id="Des_fonctions_à_part_entière">Des fonctions à part entière</h2>

<p>Dans l'exemple précédent, la valeur de retour de chaque appel à <code><a href="/fr/docs/WebAssembly/API/Table/get">Table.prototype.get()</a></code> est une fonction WebAssembly exportée — exactement ce dont nous avons parlé jusqu'à maintenant.</p>

<p>Il vaut la peine d'être noté que ceux sont des fonctions JavaScript à part entière, en plus d'être un emballage à des fonctions WebAssembly. Si vous chargez l'exemple ci-dessus dans un navigateur compatible avec WebAssembly, et excécutez les lignes suivantes dans votre console:</p>

<pre class="brush: js">var testFunc = otherTable.get(0);
typeof testFunc;</pre>

<p>Vous obtiendrez le résultat <code>function</code> en valeur de retour. Cette fonction peut effectuer tout ce qu'une fonction Javascript classique peut effectuer — <code><a href="/fr/docs/Web/JavaScript/Reference/Global_Objects/Function/call">call()</a></code>, <code><a href="/fr/docs/Web/JavaScript/Reference/Global_Objects/Function/bind">bind()</a></code>, etc. <code>testFunc.toString()</code> retourne un résultat intéressant:</p>

<pre class="brush: js">function 0() {
    [native code]
}</pre>

<p>Cela vous donne une idée plus précise de la nature de l'emballage (wrapper-type).</p>

<p>Some other particulars to be aware of with exported WebAssembly functions:</p>

<ul>
 <li>Their <a href="/fr/docs/Web/JavaScript/Reference/Global_Objects/Function/length">length</a> property is the number of declared arguments in the wasm function signature.</li>
 <li>Their <a href="/fr/docs/Web/JavaScript/Reference/Global_Objects/Function/name">name</a> property is the <code>toString()</code> result of the function's index in the wasm module.</li>
 <li>If you try to call a exported wasm function that takes or returns an i64 type value, it currently throws an error because JavaScript currently has no precise way to represent an i64. This may well change in the future though — a new int64 type is being considered for future standards, which could then be used by wasm.</li>
</ul>
