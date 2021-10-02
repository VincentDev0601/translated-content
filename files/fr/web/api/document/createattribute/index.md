---
title: document.createAttribute
slug: Web/API/Document/createAttribute
tags:
  - API
  - DOM
  - Méthodes
  - Reference
translation_of: Web/API/Document/createAttribute
---
<p>{{ApiRef("DOM")}}</p>

<p>La méthode <code><strong>Document.createAttribute()</strong></code> crée un nouveau nœud d'attribut et le renvoie. L'objet a créé un noeud implémentant l'interface {{domxref("Attr")}}. Le DOM   n'impose pas le type d'attribut à ajouter à un élément particulier de cette manière.  </p>

<div class="note">
<p><strong>Note :</strong> La chaîne de caractères donnée dans le paramètre est convertie en minuscules.</p>
</div>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="eval"><em>attribut</em> = document.createAttribute(nom)
</pre>

<h3 id="Param.C3.A8tres">Paramètres</h3>

<ul>
 <li><code>nom</code> est une chaîne de caractères contenant le nom de l'attribut.</li>
</ul>

<h3 id="Valeur_de_retour">Valeur de retour</h3>

<p>Un nœud {{domxref("Attr")}}.</p>

<h3 id="Exceptions_levées">Exceptions levées</h3>

<ul>
 <li><code>INVALID_CHARACTER_ERR</code>  si le paramètre contient un caractère invalide pour un attribut XML.</li>
</ul>

<h2 id="Exemples">Exemples</h2>


<pre class="brush:js">var node = document.getElementById("div1");
var a = document.createAttribute("my_attrib");
a.value = "newVal";
node.setAttributeNode(a);
console.log(node.getAttribute("my_attrib")); // "newVal"
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
   <td>{{SpecName('DOM WHATWG','#dom-document-createattribute','Document.createAttribute()')}}</td>
   <td>{{Spec2("DOM WHATWG")}}</td>
   <td>  Comportement précis avec des caractères majuscules.  </td>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Core','core.html#ID-1084891198','Document.createAttribute()')}}</td>
   <td>{{Spec2('DOM3 Core')}}</td>
   <td>Pas de modification.</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 Core','core.html#ID-1084891198','Document.createAttribute()')}}</td>
   <td>{{Spec2('DOM2 Core')}}</td>
   <td>Pas de modification.</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM1','level-one-core.html#ID-1084891198','Document.createAttribute()')}}</td>
   <td>{{Spec2('DOM1')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.Document.createAttribute")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{domxref("Document.createElement()")}}</li>
</ul>
