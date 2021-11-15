---
title: 'Évaluation: dépannage d''accessibilité'
slug: Learn/Accessibility/Accessibility_troubleshooting
tags:
  - Accessibilité
  - Apprendre
  - CSS
  - Débutant
  - HTML
  - JavaScript
translation_of: Learn/Accessibility/Accessibility_troubleshooting
original_slug: Apprendre/a11y/Accessibility_troubleshooting
---
<p>{{LearnSidebar}}<br>
 {{PreviousMenu("Learn/Accessibility/Mobile", "Learn/Accessibility")}}</p>

<p>Dans l’évaluation de ce module, nous vous présentons un site simple, qui présente un certain nombre de problèmes d’accessibilité que vous devez diagnostiquer et résoudre.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Conditions préalables:</th>
   <td>Connaissances informatiques de base, une compréhension de base de HTML, CSS et JavaScript, une compréhension de la  <a href="/fr/docs/Learn/Accessibility">previous articles in the course</a>.</td>
  </tr>
  <tr>
   <th scope="row">Objectif:</th>
   <td>Tester les connaissances de base sur les principes fondamentaux d'accessibilité.</td>
  </tr>
 </tbody>
</table>

<h2 id="Point_de_départ">Point de départ</h2>


<p>Pour lancer cette évaluation, vous devez aller chercher le   <a href="https://github.com/mdn/learning-area/blob/master/accessibility/assessment-start/assessment-files.zip?raw=true">ZIP containing the files that comprise the example</a>. Décompressez le contenu dans un nouveau répertoire quelque part sur votre ordinateur local</p>

<p>Le site d'évaluation terminé devrait ressembler à ceci:</p>

<p><img alt="" src="assessment-site-finished.png"></p>

<p>Vous verrez quelques différences / problèmes avec l'affichage de l'état de départ de l'évaluation - ceci est principalement dû aux différences dans le balisage, ce qui cause des problèmes de style car le CSS n'est pas appliqué correctement. Ne vous inquiétez pas, vous allez résoudre ces problèmes dans les prochaines sections!</p>

<h2 id="Résumé_du_projet">Résumé du projet</h2>

<p>Pour ce projet, vous êtes présenté avec un site naturel fictif affichant un article "factuel" sur les ours. Dans l'état actuel des choses, plusieurs problèmes d'accessibilité se posent. Votre tâche consiste à explorer le site existant et à le réparer au mieux de vos capacités, en répondant aux questions ci-dessous.</p>

<h3 id="Couleur">Couleur</h3>

<p>Le texte est difficile à lire en raison du schéma de couleurs actuel. Pouvez-vous tester le contraste de couleurs actuel (texte / arrière-plan), en rapporter les résultats, puis le corriger en modifiant les couleurs attribuées?</p>

<h3 id="Semantic_HTML">Semantic HTML</h3>

<ol>
 <li>Le contenu n'est toujours pas très accessible - faites un rapport sur ce qui se passe lorsque vous essayez de naviguer à l'aide d'un lecteur d'écran.</li>
 <li>Pouvez-vous mettre à jour le texte de l'article pour faciliter la navigation des utilisateurs de lecteurs d'écran?</li>
 <li>La partie du menu de navigation du site  ( <code>&lt;div class="nav"&gt;&lt;/div&gt;</code>) pourrait être rendue plus accessible en la plaçant dans un élément sémantique HTML5 approprié. Lequel devrait-il être mis à jour? Faites la mise à jour.</li>
</ol>

<div class="note">
<p><strong>Note :</strong> Vous devrez mettre à jour les sélecteurs de règles CSS qui attribuent aux balises le même style que les balises sémantiques. Une fois que vous avez ajouté des éléments de paragraphe, vous remarquerez que le style est meilleur.</p>
</div>

<h3 id="Les_images">Les images</h3>

<p>Les images sont actuellement inaccessibles aux utilisateurs de lecteur d'écran. Pouvez-vous réparer ceci?</p>

<h3 id="Le_lecteur_audio">Le lecteur audio</h3>

<ol>
 <li>Le lecteur   <code>&lt;audio&gt;</code>  n'est pas accessible aux malentendants (pouvez-vous ajouter une sorte d'alternative accessible pour ces utilisateurs)?</li>
 <li>Le lecteur  <code>&lt;audio&gt;</code>  n'est pas accessible aux utilisateurs de navigateurs plus anciens qui ne prennent pas en charge l'audio HTML5. Comment pouvez-vous leur permettre d'accéder encore à l'audio?</li>
</ol>

<h3 id="Les_formulaires">Les formulaires</h3>

<ol>
 <li>L'élément  <code>&lt;input&gt;</code>  dans le formulaire de recherche en haut pourrait être associé à une étiquette, mais nous ne souhaitons pas ajouter une étiquette de texte visible qui risquerait de gâcher la conception et qui n'est pas vraiment utile aux utilisateurs voyants. Comment ajouter une étiquette uniquement accessible aux lecteurs d’écran? ?</li>
 <li>Les deux éléments  <code>&lt;input&gt;</code>  du formulaire de commentaire ont des étiquettes de texte visibles, mais ils ne sont pas associés sans ambiguïté à leurs étiquettes. Comment y parvenir? Notez que vous devrez également mettre à jour certaines règles CSS.</li>
</ol>

<h3 id="Le_contrôle_afficher_masquer_les_commentaires">Le contrôle afficher / masquer les commentaires</h3>

<p>Le bouton de commande afficher / masquer les commentaires n’est pas actuellement accessible au clavier. Pouvez-vous le rendre accessible au clavier, à la fois en termes de focalisation à l'aide de la touche de tabulation et d'activation à l'aide de la touche de retour?</p>

<h3 id="La_table">La table</h3>

<p>Le tableau de données (data table ) n'est pas très accessible actuellement. Il est difficile pour les utilisateurs de lecteur d'écran d'associer des lignes et des colonnes de données. De plus, le tableau ne contient aucun type de résumé permettant de clarifier ce qu'il montre. Pouvez-vous ajouter des fonctionnalités à votre code HTML pour résoudre ce problème?</p>

<h3 id="Autres_considérations">Autres considérations?</h3>

<p>Pouvez-vous énumérer deux autres idées d’amélioration qui rendraient le site Web plus accessible?</p>

<h2 id="Évaluation">Évaluation</h2>

<p>Si vous suivez cette évaluation dans le cadre d'un cours organisé, vous devriez pouvoir donner votre travail à votre enseignant / mentor pour qu'il la corrige. Si vous vous auto-apprenez, vous pouvez obtenir le guide de notation assez facilement en le demandant sur la <a href="https://discourse.mozilla.org/t/accessibility-troubleshooting-assessment/24691">discussion thread for this exercise</a>,  ou sur le canal IRC  <a href="irc://irc.mozilla.org/mdn">#mdn</a>  sur   <a href="https://wiki.mozilla.org/IRC">Mozilla IRC</a>.  Essayez d'abord l'exercice - il n'y a rien à gagner à tricher!</p>

<p>{{PreviousMenu("Learn/Accessibility/Mobile", "Learn/Accessibility")}}</p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Learn/Accessibility/What_is_accessibility">What is accessibility?</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/HTML">HTML: A good basis for accessibility</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/CSS_and_JavaScript">CSS and JavaScript accessibility best practices</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/WAI-ARIA_basics">WAI-ARIA basics</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/Multimedia">Accessible multimedia</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/Mobile">Mobile accessibility</a></li>
 <li><a href="/fr/docs/Learn/Accessibility/Accessibility_troubleshooting">Accessibility troubleshooting</a></li>
</ul>
