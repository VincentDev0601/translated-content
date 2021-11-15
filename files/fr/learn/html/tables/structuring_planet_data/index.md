---
title: "Revue\_: structurer les données des planètes"
slug: Learn/HTML/Tables/Structuring_planet_data
translation_of: Learn/HTML/Tables/Structuring_planet_data
original_slug: Apprendre/HTML/Tableaux/Structuring_planet_data
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenu("Learn/HTML/Tables/Advanced", "Learn/HTML/Tables")}}</div>

<p>Dans notre évaluation, nous vous fournissons des données sur les planètes de notre système solaire pour vous permettre de les structurer dans un tableau HTML.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Avant de tenter cette évaluation, vous devez déjà avoir travaillé tous les articles de ce module.</td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Vérifier la compréhension des tableaux HTML et des fonctionnalités associées.</td>
  </tr>
 </tbody>
</table>

<h2 id="Point_de_départ">Point de départ</h2>

<p>Pour commencer cette évaluation, créez des copies locales de blank-template.html, minimal-table.css et planets-data.txt dans un nouveau répertoire dans votre ordinateur.</p>

<div class="note">
<p><strong>Note :</strong> Vous pouvez aussi utiliser un site comme<a class="external external-icon" href="https://jsbin.com/">JSBin</a> ou <a class="external external-icon" href="https://thimble.mozilla.org/">Thimble</a> pour votre évaluation. Vous pouvez coller les HTML, CSS et JavaScript dans l'un de ces éditeurs en ligne. Si votre éditeur en ligne n'a pas de panneaux séparés JavaScript/CSS, n'hésitez pas à les mettre en ligne <code>&lt;script&gt;</code>/<code>&lt;style&gt;</code> dans la page HTML.</p>
</div>

<h2 id="Résumé_du_projet">Résumé du projet</h2>

<p>Vous travaillez dans une école ; actuellement, vos étudiants étudient les planètes de notre système solaire, et vous souhaitez leur fournir un ensemble de données faciles à suivre, pour rechercher des faits et des chiffres sur les planètes. Un tableau de données HTML serait idéal : vous devez prendre les données brutes disponibles et les organiser en tableau, en suivant les étapes ci-dessous.</p>

<p>Le tableau terminé devrait ressembler à celui-ci :</p>

<p><img alt="" src="assessment-table.png"></p>

<p>Vous pouvez aussi <a href="https://mdn.github.io/learning-area/html/tables/assessment-finished/planets-data.html">regarder l'exemple ici</a> (sans regarder le code source — ne trichez pas !)</p>

<ul>
</ul>

<h2 id="Étapes_à_suivre">Étapes à suivre</h2>

<p>Les étapes suivantes décrivent ce que vous devez faire pour complèter l'exemple de tableau. Toutes les données dont vous avez besoin sont contenues dans le fichier <code>planets-data.txt</code>. Si vous avez du mal à visualiser les données, regardez l'exemple donné dans le lien ci-dessus, ou essayez de dessiner un diagramme.</p>

<ol>
 <li>Ouvrez votre copie de <code>blank-template.html</code>, et commencez le tableau en lui donnant un conteneur extérieur, un en-tête et un corps de tableau. Vous n'avez pas besoin d'un pied de tableau dans cet exemple.</li>
 <li>Ajoutez la légende fournie à votre tableau.</li>
 <li>Ajoutez une ligne à l'en-tête contenant tous les en-têtes de colonnes.</li>
 <li>Créez toutes les lignes de contenu du corps du tableau, en vous rappelant de faire systématiquement tous les en-têtes de lignes.</li>
 <li>Assurez-vous que tout le contenu est inséré dans les cellules de droite - dans les données brutes, chaque ligne de données d'une planète est affiché à côté de la planète associée.</li>
 <li>Ajoutez les attributs pour créer des en-têtes de lignes et colonnes ne pouvant être confondus avec les lignes, colonnes et groupes de lignes dont ils sont les en-têtes.</li>
 <li>Ajoutez une bordure noire pour entourer la colonne contenant les noms des planètes (en-têtes de lignes).</li>
</ol>

<h2 id="Conseils_et_astuces">Conseils et astuces</h2>

<ul>
 <li>La première cellule de la ligne d'en-tête doit être vierge et couvrir deux colonnes.</li>
 <li>Les en-têtes regrouppant des lignes (<em>exemple : les planètes joviennes</em>) qui sont à gauche des en-têtes de lignes des noms des planètes (exemple :  <em>Saturne</em>) sont un peu difficiles à trier — vous devez vous assurer que chacun d'eux couvre le bon nombre de lignes et colonnes.</li>
 <li>une des méthodes d'association des en-têtes avec leurs lignes et colonnes est un peu plus facile que l'autre.</li>
</ul>

<h2 id="Correction">Correction</h2>

<p>Si vous réalisez cette évaluation dans le cadre d'un cours organisé, vous devez pouvoir remettre votre travail à votre professeur/formateur pour la correction. Si vous êtes en auto-apprentissage, alors vous pouvez obtenir aisément le guide de correction par une demande auprès de <a href="https://discourse.mozilla-community.org/t/learning-web-development-marking-guides-and-questions/16294">Learning Area Discourse thread</a>, ou dans le <a href="irc://irc.mozilla.org/mdn">#mdn</a> canal IRC sur <a href="https://wiki.mozilla.org/IRC">Mozilla IRC</a>. Essayez d'abord l'exercice — il n'y a rien à gagner en trichant !</p>

<p>{{PreviousMenu("Learn/HTML/Tables/Advanced", "Learn/HTML/Tables")}}</p>
