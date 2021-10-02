---
title: KeyboardEvent.key
slug: Web/API/KeyboardEvent/key
tags:
  - API
  - DOM
  - KeyboardEvent
  - Lecture-seule
  - Propriété
  - Reference
  - UI Events
translation_of: Web/API/KeyboardEvent/key
---
<p>{{APIRef("DOM Events")}}</p>

<p>La propriété en lecture seule de <code>key</code> de l'interface {{domxref("KeyboardEvent")}} retourne la valeur d’une ou plusieurs touches pressées par l’utilisateur, tout en tenant compte de l'état des touches de modification telles que la touche <kbd>Shift</kbd> (<em>majuscules</em>) ainsi que les paramètres régionaux des clavier et mise en page. Ce peut être l’une des valeurs suivantes :</p>

<h4 id="Valeurs_des_touches">Valeurs des touches</h4>

<p>Voir une liste complète des <a href="/fr/docs/Web/API/KeyboardEvent/key/Key_Values">valeurs de touches</a></p>

<ul>
 <li>
  <p>Si la valeur a une représentation d’impression, ce sera une chaîne de caractères Unicode non vide</p>
 </li>
 <li>Si la valeur est une touche de contrôle, une des <a href="#Key_values">valeurs de touches pré-définies</a>.</li>
 <li>Si l’<code>KeyboardEvent</code> est causé par l’appui sur une touche morte, la valeur de la touche sera "<code>Dead</code>".</li>
 <li>Certaines touches de clavier spécialisées (telles que les touches étendues de contrôle des médias sur les claviers multimédias) ne génèrent pas de codes de touches sous Windows ; à la place, ils déclenchent les événements <code>WM_APPCOMMAND</code>. Ces événements sont connectés aux événements de clavier DOM et sont répertoriés parmi les «codes de touche virtuelle» pour Windows, même s'ils ne sont pas réellement des codes de touche.</li>
 <li>Si la valeur ne peut être identifiée, '<code>Unidentified</code>' sera retourné.</li>
</ul>

<h2 id="Séquence_KeyboardEvent">Séquence KeyboardEvent</h2>

<p>Les événements <code>KeyboardEvents</code> sont déclenchés selon une séquence prédéterminée, et la compréhension de ces éléments contribuera à comprendre la valeur de la propriété <code>key</code> pour un événement <code>KeyboardEvent</code> particulier. Pour une touche donnée, la séquence de KeyboardEvents est la suivante, en supposant que {{domxref ("Event.preventDefault")}} n'est pas appelée :</p>

<ol>
 <li>Un événement {{domxref("Element/keydown_event", "keydown")}} (<em>touche abaissée</em>) est d'abord déclenché. Si la touche est maintenue enfoncée et que la touche est une touche de caractère, l'événement continue d'être émis dans un intervalle dépendant de l'implémentation de la plateforme, et la propriété en lecture seule {{domxref ("KeyboardEvent.repeat")}} est définie sur <code>true</code> (<em>vrai</em>).</li>
 <li>Si la touche est une touche de caractère qui entraînerait l'insertion d'un caractère dans {{HTMLElement ("entrée")}}, {{HTMLElement ("textarea")}} ou un élément dont {{domxref ("HTMLElement. contentEditable ")}} a la valeur <code>true</code>, les types d'événements {{domxref("HTMLElement/beforeinput_event", "beforeinput")}} et {{domxref("HTMLElement/input_event", "input")}} sont déclenchés dans cet ordre. Notez que d'autres implémentations peuvent déclencher l'événement {{event ("keypress")}} si elles sont prises en charge. Les événements seront déclenchés à plusieurs reprises tant que la touche est maintenue enfoncée.</li>
 <li>Un évènement {{domxref("Element/keyup_event", "keyup")}} est déclenché une fois la touche relachée. Ceci complète le processus.</li>
</ol>

<p>Dans les étapes 1 et 3, l'attribut <code>KeyboardEent.key</code> est défini et est déclaré à une valeur appropriée en fonction des règles définies.</p>

<h2 id="Exemple_de_séquence_KeyboardEvent">Exemple de séquence KeyboardEvent</h2>

<p>Considérez la séquence d'événements générée lorsque nous interagissons avec la touche <kbd>Shift</kbd> et la touche <kbd>2</kbd> en utilisant un clavier américain et un clavier britannique.</p>

<p>Essayez d'expérimenter en utilisant les deux cas de test suivants :</p>

<ol>
 <li>Maintenez la touche <kbd>shift</kbd> enfoncée, puis appuyez sur <kbd>2</kbd> et relâchez-la. Ensuite, relâchez la touche <kbd>shift</kbd>.</li>
 <li>Maintenez la touche <code>shift</code> enfoncée, puis appuyez sur <kbd>2</kbd>. Relâchez la touche <kbd>shift</kbd>. Finalement, relâchez la touche <kbd>2</kbd>.</li>
</ol>

<h3 id="HTML">HTML</h3>

<pre class="brush: html">&lt;div class="fx"&gt;
  &lt;div&gt;
    &lt;textarea rows="5" name="test-target" id="test-target"&gt;&lt;/textarea&gt;
    &lt;button type="button" name="btn-clear-console" id="btn-clear-console"&gt;clear console&lt;/button&gt;
  &lt;/div&gt;
  &lt;div class="flex"&gt;
    &lt;div id="console-log"&gt;&lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</pre>

<h3 id="CSS">CSS</h3>

<pre class="brush: css">.fx {
  -webkit-display: flex;
  display: flex;
  margin-left: -20px;
  margin-right: -20px;
}

.fx &gt; div {
  padding-left: 20px;
  padding-right: 20px;
}

.fx &gt; div:first-child {
   width: 30%;
}

.flex {
  -webkit-flex: 1;
  flex: 1;
}

#test-target {
  display: block;
  width: 100%;
  margin-bottom: 10px;
}</pre>

<h3 id="JavaScript">JavaScript</h3>

<pre class="brush: js">let textarea = document.getElementById('test-target'),
consoleLog = document.getElementById('console-log'),
btnClearConsole = document.getElementById('btn-clear-console');

function logMessage(message) {
  let p = document.createElement('p');
  p.appendChild(document.createTextNode(message));
  consoleLog.appendChild(p);
}

textarea.addEventListener('keydown', (e) =&gt; {
  if (!e.repeat)
    logMessage(`first keydown event. key property value is "${e.key}"`);
  else
    logMessage(`keydown event repeats. key property value is "${e.key}"`);
});

textarea.addEventListener('beforeinput', (e) =&gt; {
  logMessage(`beforeinput event. you are about inputing "${e.data}"`);
});

textarea.addEventListener('input', (e) =&gt; {
  logMessage(`input event. you have just inputed "${e.data}"`);
});

textarea.addEventListener('keyup', (e) =&gt; {
  logMessage(`keyup event. key property value is "${e.key}"`);
});

btnClearConsole.addEventListener('click', (e) =&gt; {
  let child = consoleLog.firstChild;
  while (child) {
   consoleLog.removeChild(child);
   child = consoleLog.firstChild;
  }
});</pre>

<h3 id="Résultat">Résultat</h3>

<p>{{EmbedLiveSample('Exemple_de_séquence_KeyboardEvent')}}</p>

<div class="blockIndicator note">
<p><strong>Note :</strong> Sur les navigateurs qui n'implémentent pas complètement l'interface {{domxref("InputEvent")}} qui est utilisée pour les événements {{domxref("HTMLElement/beforeinput_event", "beforeinput")}} et {{domxref("HTMLElement/input_event", "input")}}, vous pouvez obtenir une réponse incorrecte sur ces lignes du journal de sortie.</p>
</div>

<h3 id="Cas_1">Cas 1</h3>

<p>Lorsque la touche Maj (<em>shift</em>) est enfoncée, un événement {{domxref("Element/keydown_event", "keydown")}} est d'abord déclenché et la valeur de la propriété <code>key</code> est définie sur la chaîne <code>"Shift"</code>. Comme nous gardons cette touche enfoncée, l'événement {{event ("keydown")}} est continu et ne se répéte pas car la touche Maj ne produit pas de caractère.</p>

<p>Lorsque la <code>key 2</code> est enfoncée, un autre événement {{domxref("Element/keydown_event", "keydown")}} est déclenché pour cette nouvelle touche, et la valeur de la propriété <code>key</code> pour l'événement est définie sur la chaîne <code>"@"</code> pour le clavier de type américain et <code>"""</code> pour le clavier de type britannique, à cause de la touche de changement de modificateur active. Les événements {{domxref("HTMLElement/beforeinput_event", "beforeinput")}} et {{domxref("HTMLElement/input_event", "input")}} sont déclenchés ensuite parce qu'une touche de caractère a été activée.</p>

<p>Lorsque nous relâchons la <code>key 2</code>, un événement {{domxref("Element/keyup_event", "keyup")}} est déclenché et la propriété <code>key</code> conserve les valeurs de chaîne <code>"@"</code> et <code>"""</code> pour les différents claviers respectivement.</p>

<p>Lorsque nous relâchons enfin la touche <code>shift</code>, un autre événement {{domxref("Element/keyup_event", "keyup")}} est déclenché pour elle, et la valeur de l'attribut de la touche reste <code>"Shift"</code>.</p>

<h3 id="Cas_2">Cas 2</h3>

<p>Lorsque la touche Maj est enfoncée, un événement {{domxref("Element/keydown_event", "keydown")}} est d'abord déclenché et la valeur de la propriété <code>key</code> est définie sur la chaîne "Shift". Comme nous maintenons cette touche enfoncée, l'événement {{domxref("Element/keydown_event", "keydown")}} est continu et ne se répéte pas car la touche Maj ne produit pas de caractère.</p>

<p>Lorsque la <code>key 2</code> est enfoncée, un autre événement {{domxref("Element/keydown_event", "keydown")}} est déclenché pour cette nouvelle touche, et la valeur de la propriété <code>key</code> pour l'événement est définie sur la chaîne <code>"@"</code> pour le clavier de type américain et <code>"""</code> pour le clavier de type britanique, à cause de la touche de changement de modificateur active. Les événements {{domxref("HTMLElement/beforeinput_event", "beforeinput")}} et {{domxref("HTMLElement/input_event", "input")}} sont déclenchés ensuite parce qu'une touche de caractère a été activée. Comme nous maintenons la touche enfoncée, l'événement {{domxref("Element/keydown_event", "keydown")}} continue à se déclencher à plusieurs reprises et la propriété {{domxref ("KeyboardEvent.repeat")}} est définie sur <code>true</code>. Les évènements {{domxref("HTMLElement/beforeinput_event", "beforeinput")}} et {{domxref("HTMLElement/input_event", "input")}} sont également déclenchés.</p>

<p>Lorsque nous relâchons la touche <code>shift</code>, un événement {{domxref("Element/keyup_event", "keyup")}} est déclenché et la valeur de l'attribut clé reste "Shift". À ce stade, notez que la valeur de la propriété <code>key</code> pour l'événement de répétition du clavier de la touche <code>key 2</code> est désormais "2" car la touche de modification du sélecteur n'est plus active. Il en va de même pour la propriété {{domxref("HTMLElement/beforeinput_event", "beforeinput")}} des événements {{domxref("HTMLElement/input_event", "input")}} et {{event ("input")}}.</p>

<p>Lorsque nous relâchons enfin la touche <code>key 2</code>, un événement {{domxref("Element/keyup_event", "keyup")}} est déclenché mais la propriété <code>key</code> est définie sur la valeur de chaîne <code>"2"</code> pour les deux configurations de clavier car la touche de modification <code>shift</code> n'est plus active.</p>

<h2 id="Exemple">Exemple</h2>

<p>Cet exemple utilise {{domxref("EventTarget.addEventListener()")}} pour écouter les événements  {{domxref("Element/keydown_event", "keydown")}} . Quand ils se produisent, la valeur de la touche est vérifiée pour voir si c'est l'une des touches qui intéressent le code, et si c'est le cas, elle est traitée (éventuellement en pilotant un vaisseau spatial, peut-être en changeant la cellule sélectionnée dans une feuille de calcul).</p>

<pre class="brush: js">window.addEventListener("keydown", function (event) {
  if (event.defaultPrevented) {
    return; // Ne devrait rien faire si l'événement de la touche était déjà consommé.
  }

  switch (event.key) {
    case "ArrowDown":
      // Faire quelque chose pour la touche "flèche vers le bas" pressée.
      break;
    case "ArrowUp":
      // Faire quelque chose pour la touche "up arrow" pressée.
      break;
    case "ArrowLeft":
      // Faire quelque chose pour la touche "left arrow" pressée.
      break;
    case "ArrowRight":
      // Faire quelque chose pour la touche "right arrow" pressée.
      break;
    case "Enter":
      // Faire quelque chose pour les touches "enter" ou "return" pressées.
      break;
    case "<code>Escape</code>":
      // Faire quelque chose pour la touche "esc" pressée.
      break;
    default:
      return; // Quitter lorsque cela ne gère pas l'événement touche.
  }

  // Annuler l'action par défaut pour éviter qu'elle ne soit traitée deux fois.
  event.preventDefault();
}, true);
</pre>

<h2 id="Spécification">Spécification</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commentaire</th>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Events', '#widl-KeyboardEvent-key', 'KeyboardEvent.key')}}</td>
   <td>{{Spec2('DOM3 Events')}}</td>
   <td>Définition initiale, incluant les valeurs de touches.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.KeyboardEvent.key")}}</p>