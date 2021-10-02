---
title: Comment()
slug: Web/API/Comment/Comment
tags:
  - API
  - Commentaires
  - DOM
translation_of: Web/API/Comment/Comment
---
<p>{{ApiRef("DOM")}}{{seeCompatTable}}</p>

<p>Le constructeur <code><strong>Comment()</strong></code> renvoie un objet {{domxref("Comment")}} <em>(Commentaire)</em> nouvellement créé avec le {{domxref ("DOMString")}} donné en paramètre comme contenu textuel.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox"><em>comment</em>1 = new Comment(); // Create an empty comment
<code><em>comment2</em></code> = new Comment("This is a comment");
</pre>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: js">var comment = new Comment("Test");</pre>

<h2 id="Specification">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('DOM WHATWG', '#comment', 'Comment.Comment()')}}</td>
   <td>{{Spec2('DOM WHATWG')}}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>



<p>{{Compat("api.Comment.Comment")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/API/Document_Object_Model">The DOM interfaces index</a></li>
</ul>

<p> </p>
