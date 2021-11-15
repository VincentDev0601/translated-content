---
title: 'Les bases de JavaScript, orienté objet'
slug: Learn/JavaScript/Objects/Basics
tags:
  - API
  - Apprendre
  - Débutant
  - JavaScript
  - Objet
  - Syntaxe
  - this
translation_of: Learn/JavaScript/Objects/Basics
---
<div>{{LearnSidebar}}</div>

<div>{{NextMenu("Learn/JavaScript/Objects/Object-oriented_JS", "Learn/JavaScript/Objects")}}</div>

<p>Dans ce premier article sur les objets JavaScript, nous verrons la syntaxe des objets JavaScript ainsi que quelques fonctionnalités JavaScript déjà aperçues dans les cours précédents, rappelant que beaucoup de fonctionnalités que vous utilisez sont en fait des objets.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Connaissances informatiques de base, connaissances basiques concernant HTML et CSS, bonnes connaissances des bases de JavaScript (cf. <a href="/fr/docs/Learn/JavaScript/First_steps">les premiers pas</a> et <a href="/fr/docs/Learn/JavaScript/Building_blocks">les briques de construction</a>).</td>
  </tr>
  <tr>
   <th scope="row">Objectifs :</th>
   <td>Comprendre les théories de base derrière la programmation orientée objet, comment l'appliquer à JavaScript, et comment travailler avec des objets JavaScript.</td>
  </tr>
 </tbody>
</table>

<h2 id="Les_bases_de_lobjet">Les bases de l'objet</h2>

<p>Un objet est une collection de données apparentées et/ou de fonctionnalités (qui, souvent, se composent de plusieurs variables et fonctions, appelées propriétés et méthodes quand elles sont dans des objets). Prenons un exemple pour voir à quoi cela ressemble.</p>

<p>Pour commencer, faites une copie locale de notre fichier <a href="https://github.com/mdn/learning-area/blob/master/javascript/oojs/introduction/oojs.html">oojs.html</a>. Il contient peu de choses : un élément {{HTMLElement("script")}} pour écrire notre code à l'intérieur. Nous utiliserons ces éléments de base pour explorer les bases de la syntaxe objet. Durant cette exemple, vous devriez avoir <a href="/fr/docs/Apprendre/D%C3%A9couvrir_outils_d%C3%A9veloppement_navigateurs#La_console_JavaScript">la console JavaScript des outils de développement</a> ouverte et prête, pour y saisir des commandes.</p>

<p>Comme souvent dans JavaScript, pour créer un objet, on commence avec la définition et l'initialisation d'une variable. Essayez de mettre le code ci-dessous sous le code déjà écrit de votre fichier JavaScript, puis sauvegardez et rafraichissez la page :</p>

<pre class="brush: js">var personne = {};</pre>

<p>Désormais ouvrez la <a href="/fr/docs/Outils/Console_JavaScript#Ouvrir_la_Console_du_navigateur">console JavaScript</a> de votre navigateur, saisissez <code>personne</code> à l'intérieur, et appuyez sur <kbd>Entrée</kbd>. Vous devriez obtenir le résultat suivant :</p>

<pre class="brush: js">[object Object]</pre>

<p>Félicitations, vous avez créé votre premier objet ! Mais c'est un objet vide, on ne peut pas faire grand-chose avec. Modifions notre objet pour qu'il ressemble à ceci :</p>

<pre class="brush: js">var personne = {
  nom: ['Jean', 'Martin'],
  age: 32,
  sexe: 'masculin',
  interets: ['musique', 'skier'],
  bio: function() {
    alert(this.nom[0] + ' ' + this.nom[1] + ' a ' + this.age + ' ans. Il aime ' + this.interets[0] + ' et ' + this.interets[1] + '.');
  },
  salutation: function() {
    alert('Bonjour ! Je suis ' + this.nom[0] + '.');
  }
};
</pre>

<p>Après avoir sauvegardé et rafraîchit la page, essayez d'entrer les lignes suivantes dans le champ de saisie <code>input</code> :</p>

<pre class="brush: js">personne.nom
personne.nom[0]
personne.age
personne.interets[1]
personne.bio()
personne.salutation()</pre>

<p>Vous avez désormais des données et des fonctionnalités dans votre objet, et vous pouvez y accéder avec une une syntaxe simple et claire !</p>

<div class="note">
<p><strong>Note :</strong> Si vous avez des difficultés pour le faire fonctionner, comparez votre code avec notre version — voir <a href="https://github.com/mdn/learning-area/blob/master/javascript/oojs/introduction/oojs-finished.html">oojs-finished.html</a> (ou <a href="https://mdn.github.io/learning-area/javascript/oojs/introduction/oojs-finished.html">voir en action</a>). Une erreur courante, quand on commence avec les objets, est de mettre une virgule après la dernière propriété — ce qui provoque une erreur.</p>
</div>

<p>Alors, comment ça fonctionne ? Un objet est fait de plusieurs membres, qui ont chacun un nom (par exemple <code>nom</code> et <code>age</code> ci-dessus) et une valeur (par exemple. <code>['Jean', 'Martin']</code> et <code>32</code>).</p>

<p>Chaque paire de nom/valeur doit être séparée par une virgule, et le nom et la valeur de chaque membre sont séparés par deux points. La syntaxe suit ce schéma :</p>

<pre class="brush: js">var monObjet = {
  nomDuMembre1: valeurDuMembre1,
  nomDuMembre2: valeurDuMembre2,
  nomDuMembre3: valeurDuMembre3
}</pre>

<p>La valeur d'un membre dans un objet peut être n'importe quoi — dans notre objet <code>personne</code>, nous avons du texte, un nombre, deux tableaux et deux fonctions. Les quatre premières éléments sont des données appelées <strong>propriétés</strong> de l'objet, et les deux derniers éléments sont des fonctions qui utilisent les données de l'objet pour faire quelque chose, et sont appelées des <strong>méthodes</strong> de l'objet.</p>

<p>Dans cet exemple, l'objet est créé grâce à un<strong> objet littéral</strong> : on écrit littéralement le contenu de l'objet pour le créer. On distinguera cette structure des objets instanciés depuis des classes, que nous verrons plus tard.</p>

<p>C'est une pratique très courante de créer un objet en utilisant un objet littéral :  par exemple, quand on envoie une requête au serveur pour transférer des données vers une base de données.</p>

<p>Envoyer un seul objet est bien plus efficace que d'envoyer ses membres de manière individuelle, et c'est bien plus simple de travailler avec un tableau quand on veut identifier des membres par leur nom.</p>

<h2 id="Notation_avec_un_point">Notation avec un point</h2>

<p>Ci-dessus, on accède aux membres de l'objet en utilisant la <strong>notation avec un point</strong>.</p>

<p>Le nom de l'objet (<code>personne</code>) agit comme un <strong>espace de noms</strong> (ou <em>namespace</em> en anglais) — il doit être entré en premier pour accéder aux membres <strong>encapsulés</strong> dans l'objet. Ensuite, on écrit un point, puis le membre auquel on veut accéder — que ce soit le nom d'une propriété, un élément d'un tableau, ou un appel à une méthode de l'objet. Par exemple :</p>

<pre class="brush: js">personne.age
personne.interets[1]
personne.bio()</pre>

<h3 id="Sous-espaces_de_noms">Sous-espaces de noms</h3>

<p>Il est même possible de donner un autre objet comme valeur d'un membre de l'objet. Par exemple, on peut essayer de changer la propriété <code>nom</code> du membre et la faire passer de</p>

<pre class="brush: js">nom: ['Jean', 'Martin'],</pre>

<p>à</p>

<pre class="brush: js">nom : {
  prenom: 'Jean',
  nomFamille: 'Martin'
},</pre>

<p>Ici, nous avons bien créé un <strong>sous-espace de noms</strong>. Ça a l'air compliqué, mais ça ne l'est pas. Pour accéder à ces élements, il suffit de chaîner une étape de plus avec un autre point. Essayez ceci :</p>

<pre class="brush: js">personne.nom.prenom
personne.nom.nomFamille</pre>

<p><strong>Important </strong>: à partir de maintenant, vous allez aussi devoir reprendre votre code et modifier toutes les occurrences de :</p>

<pre class="brush: js">nom[0]
nom[1]</pre>

<p>en</p>

<pre class="brush: js">nom.prenom
nom.nomFamille</pre>

<p>sinon vos méthodes ne fonctionneront plus.</p>

<h2 id="Notation_avec_les_crochets">Notation avec les crochets</h2>

<p>Il y a une autre façon d'accéder aux membres de l'objet : la notation avec les crochets. Plutôt que d'utiliser ceci :</p>

<pre class="brush: js">personne.age
personne.nom.prenom</pre>

<p>Vous pouvez utiliser :</p>

<pre class="brush: js">personne['age']
personne['nom']['prenom']</pre>

<p>Cela ressemble beaucoup à la façon d'accéder aux éléments d'un tableau et c'est bien la même chose  — au lieu d'utiliser un indice numérique pour sélectionner un élément, on utilise le nom associé à chaque valeur d'un membre. Ce n'est pas pour rien que les objets sont parfois appelés tableaux associatifs : ils associent des chaînes de caractères (les noms des membres) à des valeurs, de la même façon que les tableaux associent des nombres à des valeurs.</p>

<h2 id="Définir_les_membres_dun_objet">Définir les membres d'un objet</h2>

<p>Jusqu'ici, nous avons vu comment <strong>accéder</strong> aux membres d'un objet. Vous pouvez aussi <strong>modifier</strong> la valeur d'un membre de l'objet en déclarant simplement le membre que vous souhaitez modifier(en utilisant la notation avec le point ou par crochet), comme ceci :</p>

<pre class="brush: js">personne.age = 45
personne['nom']['nomFamille'] = 'Rabuchon'</pre>

<p>Essayez de saisir ces deux lignes précédentes, puis accédez à nouveau aux membres pour voir ce qui a changé :</p>

<pre class="brush: js">personne.age
personne['nom']['nomFamille']</pre>

<p>Définir les membres ne s'arrête pas à mettre à jour la valeur de propriétés ou méthodes existantes; <strong>vous pouvez aussi créer de nouveaux membres</strong>. Essayez ceci :</p>

<pre class="brush: js">personne['yeux'] = 'noisette'
personne.auRevoir = function() { alert("Bye bye tout le monde !"); }</pre>

<p>Vous pouvez maintenant tester vos nouveaux membres :</p>

<pre class="brush: js">personne['yeux']
personne.auRevoir()</pre>

<p>Un des aspects pratiques de la notation par crochet est qu'elle peut être utilisée pour définir dynamiquement les valeurs des membres, mais aussi pour définir les noms. Imaginons que nous voulions que les utilisateurs puissent saisir des types de valeurs personnalisées pour les données des personnes, en entrant le nom du membre et sa valeur dans deux champs <code>input</code>. On pourrait avoir ses valeurs comme ceci :</p>

<pre class="brush: js">var monNomDeDonnee = nomInput.value
var maValeurDeDonnee = valeurNom.value</pre>

<p>On peut alors ajouter le nom et la valeur du nouveau membre de l'objet <code>personne</code> comme ceci :</p>

<pre class="brush: js">personne[monNomDeDonnee] = maValeurDeDonnee</pre>

<p>Pour le tester, essayez d'ajouter les lignes ci-dessous dans votre code, juste après le crochet fermante de l'objet <code>personne</code> :</p>

<pre class="brush: js">var monNomDeDonnee = 'hauteur'
var maValeurDeDonnee = '1.75m'
personne[monNomDeDonnee] = maValeurDeDonnee</pre>

<p>Sauvegardez, rafraîchissez et entrez le texte suivant dans le champ de saisie (l'élément <code>input</code>) :</p>

<pre class="brush: js">personne.hauteur</pre>

<p>Nous n'aurions pas pu construire ce membre avec la notation avec un point, car celle-ci n'accepte qu'un nom et pas une variable pointant vers un nom.</p>

<h2 id="Quest-ce_que_«_this_»">Qu'est-ce que « <code>this</code> » ?</h2>

<p>Vous avez dû remarquer quelque chose d'un peu étrange dans vos méthodes. Celle-ci, par exemple :</p>

<pre class="brush: js">salutation: function() {
  alert('Bonjour! Je suis ' + this.nom.prenom + '.');
}</pre>

<p>Vous vous demandez probablement ce que signifie « <code>this</code> ». Le mot-clé <code>this</code> se réfère à l'objet courant dans lequel le code est écrit —  dans notre cas, <code>this</code> est l'équivalent de <code>personne</code>.  Alors, pourquoi ne pas écrire <code>personne</code> à la place ? Comme vous le verrez dans l'article <a href="/fr/docs/Learn/JavaScript/Objects/Object-oriented_JS">la programmation JavaScript orientée objet pour les débutants</a>, <code>this</code> est très utile — il permet de s'assurer que les bonnes valeurs sont utilisées quand le contexte d'un membre change (on peut par exemple avoir deux personnes, sous la forme de deux objets, avec des noms différents).</p>

<p>Essayons d'illustrer nos propos par une paire d'objet <code>personne</code> simplifiée :</p>

<pre class="brush: js">var personne1 = {
  nom: 'Christophe',
  salutation: function() {
    alert('Bonjour ! Je suis ' + this.nom + '.');
  }
}

var personne2 = {
  nom: 'Bruno',
  salutation: function() {
    alert('Bonjour ! Je suis ' + this.nom + '.');
  }
}</pre>

<p>Dans ce cas,  <code>personne1.salutation()</code> affichera "Bonjour ! Je suis Christophe.", tandis que <code>personne2.salutation()</code> affichera "Bonjour ! Je suis Bruno." alors que le code est le même dans les deux cas. Comme expliqué plus tôt, <code>this</code> est égal à l'objet dans lequel se situe le code. Ce n'est pas très utile quand on écrit des objets littéraux à la main, mais ça prend tout son sens quand on génère des objets dynamiques (avec des constructeurs par exemple).</p>

<h2 id="Vous_utilisiez_des_objets_depuis_le_début_!">Vous utilisiez des objets depuis le début !</h2>

<p>Tout au long de ces exemples, vous vous êtes probablement dit que la notation avec un point vous était très familière. C'est parce que vous l'avez utilisée tout au long du cours ! À chaque fois que vous avez travaillé avec un exemple qui utilise une API ou un objet JavaScript natif, nous avons utilisé des objets. Ces fonctionnalités sont construites exactement comme les objets que nous avons manipulés ici, mais sont parfois plus complexes que dans nos exemples.</p>

<p>Ainsi, quand vous utilisez une méthode comme :</p>

<pre class="brush: js">maChaineDeCaracteres.split(',');</pre>

<p>Vous utilisez une méthode disponible dans une instance du type {{jsxref("String")}}. Dès que vous créez une chaîne de caractères dans votre code, cette chaîne est automatiquement créée comme une instance de <code>String</code> et possède donc plusieurs méthodes/propriétés communes.</p>

<p>Quand vous accédez au DOM (<em>Document Object Model</em> ou « modèle objet du document ») avec <code>document</code> et des lignes telles que :</p>

<pre class="brush: js">var monDiv = document.createElement('div');
var maVideo = document.querySelector('video');</pre>

<p>Vous utilisez une méthode disponible dans l'instance de la classe {{domxref("Document")}}. Pour chaque page web chargée, une instance de <code>Document</code> est créée, appelée <code>document</code> et qui représente la structure entière de la page, son contenu et d'autres caractéristiques telles que son URL. Encore une fois, cela signifie qu'elle possède plusieurs méthodes/propriétés communes.</p>

<p>C'est également vrai pour beaucoup d'autres objets/API natifs que vous avez utilisé  — {{jsxref("Array")}}, {{jsxref("Math")}}, etc.</p>

<p>On notera que les objets/API natifs ne créent pas toujours automatiquement des instances d'objet. Par exemple, <a href="/fr/docs/Web/API/Notifications_API">l'API Notifications</a> — qui permet aux navigateurs modernes de déclencher leurs propres notifications — vous demande d'instancier vous-même une nouvelle instance d'objet en utilisant le constructeur pour chaque notification que vous souhaitez lancer. Essayez d'entrer le code ci-dessous dans la console JavaScript :</p>

<pre class="brush: js">var maNotification = new Notification('Bonjour !');</pre>

<p>Nous verrons les constructeurs dans un prochain article.</p>

<div class="note">
<p><strong>Note :</strong> On peut voir le mode de communication des objets comme un <strong>envoi de message</strong>. Quand un objet a besoin d'un autre pour faire une action, souvent il va envoyer un message à un autre objet via l'une de ses méthode et attendre une réponse, qui retournera une valeur.</p>
</div>

<h2 id="Résumé">Résumé</h2>

<p>Félicitations, vous avez terminé notre premier article sur les objets JavaScript  — vous devriez maintenant mieux comprendre comment on travaille avec des objets en JavaScript. Vous avez pu créer vos propres objets basiques. Vous devriez aussi voir que les objets sont très pratiques pour stocker des données et des fonctionnalités. Si on ne passe pas par un objet et qu'on a une variable différente pour chaque propriété et méthode de notre objet <code>personne</code>, cela sera inefficace et frustrant et vous prendrez le risque de créer des conflits avec d'autres variables et fonctions du même nom.</p>

<p>Les objets permettent de conserver les informations de façon sûre, enfermées dans leur propre « paquet », hors de danger.</p>

<p>Dans le prochain article, nous commencerons à voir la théorie de la programmation orientée objet (POO) et comment utiliser ces techniques en JavaScript.</p>

<p>{{NextMenu("Learn/JavaScript/Objects/Object-oriented_JS", "Learn/JavaScript/Objects")}}</p>
