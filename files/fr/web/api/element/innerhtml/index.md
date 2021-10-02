---
title: element.innerHTML
slug: Web/API/Element/innerHTML
tags:
  - API
  - DOM
  - Elements
  - HTML
  - Propriétés
translation_of: Web/API/Element/innerHTML
original_slug: Web/API/Element/innertHTML
---
<div>{{APIRef("DOM")}}</div>

<p>La propriété <strong><code>Element.innerHTML</code></strong> de {{domxref("Element")}} récupère ou définit la syntaxe HTML décrivant les descendants de l'élément.</p>

<div class="note">
  <p><strong>Note :</strong> Si un nœud {{HTMLElement("div")}}, {{HTMLElement("span")}}, ou {{HTMLElement("noembed")}} a un sous-nœud de type texte contenant les caractères <code>(&amp;), (&lt;),</code> ou <code>(&gt;)</code>, <code>innerHTML</code> renverra à la place les chaînes suivantes : <code>"&amp;amp;"</code>, <code>"&amp;lt;"</code> et <code>"&amp;gt;"</code> respectivement. Utilisez {{domxref("Node.textContent")}} pour obtenir une copie exacte du contenu de ces nœuds.</p>
</div>

<p>Pour insérer le HTML dans le document, plutôt que de remplacer le contenu d'un élément, utilisez la méthode {{domxref("Element.insertAdjacentHTML", "insertAdjacentHTML()")}}.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox">const <em>content</em> = <em>element</em>.innerHTML;

<em>element</em>.innerHTML = <em>htmlString</em>;
</pre>

<h3 id="Valeur">Valeur</h3>

<p>Une  {{domxref("DOMString")}} contenant la sérialisation HTML des descendants de l'élément. Définir la valeur de <code>innerHTML</code> supprime tous les descendants et les remplace par les noeuds construits en analysant le HTML donné dans la chaîne <code>htmlString</code>.</p>

<h3 id="Exceptions">Exceptions</h3>

<dl>
 <dt><code>SyntaxError</code></dt>
 <dd>Une tentative a été faite de définir la valeur de <code>innerHTML</code> en utilisant une chaîne qui n'est pas correctement formée HTML.</dd>
 <dt><code>NoModificationAllowedError</code></dt>
 <dd>Une tentative a été faite d'insérer le code HTML dans un noeud dont le parent est un {{domxref("Document")}}.</dd>
</dl>

<h2 id="Notes_dutilisation">Notes d'utilisation</h2>

<p>La propriété <code>innerHTML</code> peut être utilisée pour examiner la source HTML actuelle de la page, y compris tous les changements réalisés depuis son chargement initial.</p>

<h3 id="Lecture_du_contenu_HTML_dun_élément">Lecture du contenu HTML d'un élément</h3>

<p>La lecture de <code>innerHTML</code> amène l'agent utilisateur à sérialiser le fragment HTML ou XML composé des descendants de l'élément. La chaîne résultante est renvoyée.</p>

<pre class="brush: js">let contents = myElement.innerHTML;</pre>

<p>Cela vous permet de regarder le balisage HTML des nœuds de contenu de l'élément.</p>

<div class="note">
<p><strong>Note :</strong> Le fragment HTML ou XML renvoyé est généré en fonction du contenu actuel de l'élément. Il est donc probable que le balisage et la mise en forme du fragment renvoyé ne correspondent pas au balisage de la page d'origine.</p>
</div>

<h3 id="Remplacement_du_contenu_dun_élément">Remplacement du contenu d'un élément</h3>

<p>Définir la valeur de <code>innerHTML</code> vous permet de remplacer aisément le contenu existant d'un élément par un nouveau contenu.</p>

<p>Par exemple, vous pouvez effacer le contenu entier du document en effaçant le contenu de l'attribut {{domxref("Document.body", "body")}} du document.</p>

<pre class="brush: js">document.body.innerHTML = "";</pre>

<p>Cet exemple récupère le balisage HTML actuel du document et remplace les caractères <code>"&lt;"</code> par l'entité HTML <code>"&amp; lt;"</code>, convertissant ainsi essentiellement le code HTML en texte brut. Ceci est ensuite inclus dans un élément {{HTMLElement ("pre")}}. Puis, la valeur de <code>innerHTML</code> est modifiée dans cette nouvelle chaîne. Par conséquent, le contenu du document est remplacé par un affichage du code source entier de la page.</p>

<pre class="brush: js">document.documentElement.innerHTML = "&lt;pre&gt;" +
         document.documentElement.innerHTML.replace(/&lt;/g,"&amp;lt;") +
            "&lt;/pre&gt;";</pre>

<h4 id="Détails_opérationnels">Détails opérationnels</h4>

<p>Qu'arrive-t-il exactement quand vous définissez la valeur de <code>innerHTML</code> ?  Cela entraîne l'agent utilisateur à suivre ces étapes :</p>

<ol>
 <li>La valeur spécifiée est analysée en HTML ou XML (en fonction du type de document), ce qui donne un objet {{domxref ("DocumentFragment")}} représentant le nouvel ensemble de nœuds DOM pour les nouveaux éléments.</li>
 <li>Si l'élément dont le contenu est remplacé est un élément {{HTMLElement ("template")}}, l'attribut {{domxref ("HTMLTemplateElement.content", "content")}} de l'élément <code>&lt;template&gt;</code> est remplacé par le nouveau <code>DocumentFragment</code> créé à l'étape 1.</li>
 <li>Pour tous les autres éléments, le contenu de l'élément est remplacé par les noeuds du nouveau <code>DocumentFragment</code>.</li>
</ol>

<h3 id="Considérations_de_sécurité">Considérations de sécurité</h3>

<p>Il n'est pas rare de voir <code>innerHTML</code> utilisé pour insérer du texte dans une page Web. Il est possible que ceci devienne un vecteur d'attaque sur un site, ce qui crée potentiellement un risque de sécurité.</p>

<pre class="brush: js">const name = "John";
// en supposant que 'el' est un élément de document HTML
el.innerHTML = name; // inoffensif dans ce cas

// ...

name = "&lt;script&gt;alert('I am John in an annoying alert!')&lt;/script&gt;";
el.innerHTML = name; // inoffensif dans ce cas</pre>

<p>Bien que cela puisse ressembler à une attaque {{interwiki ("wikipedia", "cross-site_scripting","cross-site scripting")}}, le résultat est inoffensif. HTML5 spécifie qu'une balise {{HTMLElement ("script")}} insérée avec <code>innerHTML</code> <a href="https://www.w3.org/TR/2008/WD-html5-20080610/dom.html#innerhtml0">ne doit pas s'exécuter</a>.</p>

<p>Cependant, il existe des moyens d'exécuter JavaScript sans utiliser les éléments {{HTMLElement ("script")}}, donc il existe toujours un risque de sécurité chaque fois que vous utilisez <code>innerHTML</code> pour définir des chaînes sur lesquelles vous n'avez aucun contrôle. Par exemple :</p>

<pre class="brush: js">const name = "&lt;img src='x' onerror='alert(1)'&gt;";
el.innerHTML = name; // affiche l'alerte</pre>

<p>Pour cette raison, il est recommandé de ne pas utiliser <code>innerHTML</code> pour insérer du texte brut ; à la place, utilisez {{domxref("Node.textContent")}}. Cela n'analyse pas le contenu passé en HTML, mais l'insère à la place en tant que texte brut.</p>

<div class="warning">
<p><strong>Attention :</strong> Si votre projet est soumis à une vérification de sécurité, l'utilisation de <code>innerHTML</code> entraînera probablement le rejet de votre code. Par exemple, si vous utilisez <code>innerHTML</code> dans une extension de navigateur et soumettez l'extension à addons.mozilla.org, elle ne passera pas le processus de révision automatique.</p>
</div>

<h2 id="Exemple">Exemple</h2>

<p>Cet exemple utilise <code>innerHTML</code> pour créer un mécanisme pour consigner des messages dans une boîte sur une page Web.</p>

<h3 id="JavaScript">JavaScript</h3>

<pre class="brush: js">function log(msg) {
  var logElem = document.querySelector(".log");

  var time = new Date();
  var timeStr = time.toLocaleTimeString();
  logElem.innerHTML += timeStr + ": " + msg + "&lt;br/&gt;";
}

log("Logging mouse events inside this container...");</pre>

<p>La fonction <code>log()</code> crée la sortie du journal en récupérant l'heure actuelle à partir d'un objet {{jsxref ("Date")}} en utilisant {{jsxref ("Date.toLocaleTimeString", "toLocaleTimeString ()")}} et en créant une chaîne avec l'horodatage et le texte du message. Ensuite, le message est ajouté à la boîte avec la classe <code>"log"</code>.</p>

<p>Nous ajoutons une seconde méthode qui enregistre des informations sur les événements basés sur {{domxref ("MouseEvent")}} (tels que {{event ("mousedown")}}, {{event ("click")}} et {{event ("mouseenter") }}) :</p>

<pre class="brush: js">function logEvent(event) {
  var msg = "Event &lt;strong&gt;" + event.type + "&lt;/strong&gt; at &lt;em&gt;" +
            event.clientX + ", " + event.clientY + "&lt;/em&gt;";
  log(msg);
}</pre>

<p>Alors, nous utilisons ceci comme un gestionnaire d'évènements pour un certain nombre d'évènements de souris sur la boîte qui contient notre journal.</p>

<pre class="brush: js">var boxElem = document.querySelector(".box");

boxElem.addEventListener("mousedown", logEvent);
boxElem.addEventListener("mouseup", logEvent);
boxElem.addEventListener("click", logEvent);
boxElem.addEventListener("mouseenter", logEvent);
boxElem.addEventListener("mouseleave", logEvent);</pre>

<h3 id="HTML">HTML</h3>

<p>Le HTML est assez simple pour notre exemple.</p>

<pre class="brush: html">&lt;div class="box"&gt;
  &lt;div&gt;&lt;strong&gt;Log:&lt;/strong&gt;&lt;/div&gt;
  &lt;div class="log"&gt;&lt;/div&gt;
&lt;/div&gt;</pre>

<p>Le {{HTMLElement ("div")}} avec la classe <code>"box"</code> est juste un conteneur pour la mise en page, présentant le contenu avec une boîte autour de lui. Le <code>&lt;div&gt;</code> dont la classe est <code>"log"</code> est le conteneur pour le texte du journal lui-même.</p>

<h3 id="Notes">CSS</h3>

<p>Les styles CSS suivants pour notre exemple de contenu.</p>

<pre class="brush: css">.box {
  width: 600px;
  height: 300px;
  border: 1px solid black;
  padding: 2px 4px;
  overflow-y: scroll;
  overflow-x: auto;
}

.log {
  margin-top: 8px;
  font-family: monospace;
}</pre>

<h3 id="Résultat">Résultat</h3>

<p>Le contenu résultant ressemble à ceci. Vous pouvez voir la sortie dans le journal en déplaçant la souris dans et hors de la boîte, en cliquant dedans, et ainsi de suite.</p>

<p>{{EmbedLiveSample("Exemple", 640, 350)}}</p>

<h2 id="Specification">Spécification</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('DOM Parsing', '#innerhtml', 'Element.innerHTML')}}</td>
   <td>{{ Spec2('DOM Parsing') }}</td>
   <td>Définition initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="References">Voir aussi</h2>

<ul>
 <li>{{domxref("Node.textContent")}} and {{domxref("Node.innerText")}}</li>
 <li>{{domxref("Element.insertAdjacentHTML")}}</li>
 <li>Analyse HTML dans une arborescence DOM : {{domxref("DOMParser")}}</li>
 <li>Sérialisation XML ou HTML dans une arborescence DOM : {{domxref("XMLSerializer")}}</li>
</ul>
