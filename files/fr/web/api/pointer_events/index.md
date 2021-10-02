---
title: Événements de pointeur
slug: Web/API/Pointer_events
tags:
  - API
  - NeedsTranslation
  - Overview
  - TopicStub
translation_of: Web/API/Pointer_events
---
<p>{{DefaultAPISidebar("Pointer Events")}}</p>

<p>La plupart du contenu web d'aujourd'hui suppose que le périphérique de pointage de l'utilisateur sera une souris. Cependant, beaucoup d'appareils prennent en charge d'autres types de d'entrée pour pointeur, comme le stylet ou les doigts pour les écrans tactiles. Des extensions aux modèles d'événement de pointage sont nécessaires et les <em>événements de pointeur</em> répondent à ce besoin.</p>

<p>Les événements de pointeur sont des événements DOM déclenché pour tout périphérique de pointage. Ils sont conçus pour créer un modèle unique d'événement DOM pour gérer les périphériques de pointage comme la souris, le stylet ou le toucher (avec un ou plusieurs doigts). Un <em><a href="#term_pointer">pointeur</a></em> est agnostique du type de matériel utilisé pour cibler un endroit sur l'écran.</p>

<p>Avoir un seul modèle pour gérer les événements de pointeur peut simplifier la création de sites web et applications et fournir une bonne expérience utilisateur quelque soit le matériel de l'utilisateur. Toutefois, pour les scénarios dans lesquels une gestion spécifique au périphérique est souhaitée, les événements de pointeur définissent une propriété {{domxref("PointerEvent.pointerType","pointerType")}} qui permet de connaître le type de périphérique ayant déclenché l'événement.</p>

<p>Les événements nécessaires pour gérer les entrées de pointeur génériques sont analogues aux {{domxref("MouseEvent","événements de souris")}}. Par conséquent, les types d'événement de pointeur sont intentionnelement similaires aux événements de souris (<code>mousedown/pointerdown</code>, <code>mousemove/pointermove</code>, etc). De plus, les événements de pointeur contiennent les propriétés usuelles présentes dans les événements de souris (coordonnées client, élément cible, états des boutons, etc.) ainsi que de nouvelles propriétés pour les autres types d'entrée: pression, géométrie de contact, inclinaison, etc. En fait, l'interface {{domxref("PointerEvent")}} hérite toutes les propriétés de {{domxref("MouseEvent","MouseEvent")}} ce qui facilite la migration des événements souris aux événements de pointeur.</p>

<h2 id="Terminologie">Terminologie</h2>

<dl>
 <dt>pointeur actif</dt>
 <dd>Tout périphérique d'entrée <em><a href="#term_pointer">pointeur</a></em> pouvant produire des événements. Un pointeur est considéré actif s'il peut encore produire des événements. Par exemple, un stylet posé sur l'écran est considéré comme actif puisqu'il peut produire des événements en étant déplacé ou levé.</dd>
 <dt>numériseur (digitizer)</dt>
 <dd>Un dispositif avec une surface pouvant recevoir et détecter le contact. Le plus souvent, le dispositif est un écran tactile pouvant détecter l'entrée provenant du stylet ou du doigt.</dd>
 <dt>hit test</dt>
 <dd>Le procédé qu'utilise le navigateur pour détermine l'élément cible de l'événement pointeur. Typiquement, il est déterminé en utilisant l'emplacement du pointeur et la disposition visuelle des éléments dans un document d'un media écran.</dd>
 <dt>pointeur</dt>
 <dd>Une représentation agnostique du périphérique en entrée pouvant cibler des coordonnées sur un écran. Des exemples d'appareils de <em>pointeur</em> sont la souris, le stylet et la contact tactile.</dd>
 <dt>capture du pointeur</dt>
 <dd>La capture du pointeur permet aux événements d'être redirigé vers un élément particulier autre que le résultat du hit test.</dd>
 <dt>événement de pointeur</dt>
 <dd>Un {{domxref("PointerEvent","événement")}} DOM déclenché pour un <em>pointeur</em>.</dd>
</dl>

<h2 id="Interfaces">Interfaces</h2>

<p>L'interface principale est l'interface {{domxref("PointerEvent")}}, qui comprend un {{domxref("PointerEvent.PointerEvent","constructeur")}} ainsi que plusieurs événements. L'API ajoute également quelques extensions aux interfaces {{domxref("Element")}} et {{domxref("Navigator")}}. Les sous-sections suivantes décrivent brièvement chaque interface et propriétés liées.</p>

<h3 id="Interface_PointerEvent">Interface PointerEvent</h3>

<p>L'interface {{domxref("PointerEvent")}} hérite de l'interface {{domxref("MouseEvent")}} et a les propriétés suivantes (toutes sont {{readonlyInline}}).</p>

<ul>
 <li>{{ domxref('PointerEvent.pointerId','pointerId')}} - un identifiant unique pour le pointeur ayant déclenché l'événement.</li>
 <li>{{ domxref('PointerEvent.width','width')}} - la largeur (ordre de grandeur sur l'axe X), en pixels CSS, du point de contact.</li>
 <li>{{ domxref('PointerEvent.height','height')}} - la hauteur (ordre de grandeur sur l'axe Y), en pixels CSS, du point de contact.</li>
 <li>{{ domxref('PointerEvent.pressure','pressure')}} - la pression du pointeur normalisée sur une échelle entre 0 et 1, où 0 et 1 représentent respectivement la pression minimale et le maximale que l'appareil est capable de détecter.</li>
 <li>{{ domxref('PointerEvent.tiltX','tiltX')}} - l'angle du plan (en degrés, sur une échelle de -90 à 90) entre le plan Y-Z et le plan qui contient l'axe du stylo et l'axe Y.</li>
 <li>{{ domxref('PointerEvent.tiltY','tiltY')}} - l'angle du plan (en degrés, sur une échelle de -90 à 90) entre le plan X-Z et le plan qui contient l'axe du stylo et l'axe X.</li>
 <li>{{ domxref('PointerEvent.pointerType','pointerType')}} - indique le type d'appareil ayant déclenché l'événement (souris, stylet, toucher, etc.)</li>
 <li>{{ domxref('PointerEvent.isPrimary','isPrimary')}} - indique si le pointeur est le pointeur principal de son type (utile dans le cas du multi-touch).</li>
</ul>

<h3 id="Types_dévénements_et_gestionnaires_dévénements_globaux">Types d'événements et gestionnaires d'événements globaux</h3>

<p>Il existe dix types d'événement de pointeur, dont sept qui ont la même sémantique que les événements souris (<code>down, up, move, over, out, enter, leave</code>). Vous trouverez ci-dessous une courte description de chaque type d'événement et son {{domxref("GlobalEventHandlers","gestionnaire d'événement global")}} associé.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Event</th>
   <th scope="col">On Event Handler</th>
   <th scope="col">Description</th>
  </tr>
  <tr>
   <td>{{event('pointerover')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointerover','onpointerover')}}</td>
   <td>déclenché quand un pointeur entre à l'intérieur des limites du <a href="#term_hit_test">hit test</a> d'un élément.</td>
  </tr>
  <tr>
   <td>{{event('pointerenter')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointerenter','onpointerenter')}}</td>
   <td>déclenché quand un pointeur entre à l'intérieur des limites du <a href="#term_hit_test">hit test</a> d'un élément ou d'un de ses descendants.</td>
  </tr>
  <tr>
   <td>{{event('pointerdown')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointerdown','onpointerdown')}}</td>
   <td>déclenché quand le pointeur devient <em>actif</em> (que le contact est établit).</td>
  </tr>
  <tr>
   <td>{{event('pointermove')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointermove','onpointermove')}}</td>
   <td>déclenché quand les coordonnées du pointeur changent (que le pointeur bouge).</td>
  </tr>
  <tr>
   <td>{{event('pointerup')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointerup','onpointerup')}}</td>
   <td>déclenché quand le pointeur n'est plus <em>actif</em> (que le contact est relaché).</td>
  </tr>
  <tr>
   <td>{{event('pointercancel')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointercancel','onpointercancel')}}</td>
   <td>le navigateur déclenche cet événement s'il détecte que le pointeur ne pourra plus générer d'événement (si l'appareil est désactivé par exemple).</td>
  </tr>
  <tr>
   <td>{{event('pointerout')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointerout','onpointerout')}}</td>
   <td>déclenché quand le pointeur n'est plus affecté à l'élément: qu'il sort des limites du <a href="term_hit_test">hit test</a> de l'élément; qu'il déclenche l'événement pointerup ou pointercancel; que le stylet sort de la zone de l'écran de l'appareil.</td>
  </tr>
  <tr>
   <td>{{event('pointerleave')}}</td>
   <td>{{domxref('GlobalEventHandlers.onpointerleave','onpointerleave')}}</td>
   <td>déclenché quand le pointeur sort des limites du <a href="term_hit_test">hit test</a> de l'élément. Cet événement est également déclenché lorsqu'on utilise un stylet et qu'il sort de la zone détectable par le numériseur.</td>
  </tr>
  <tr>
   <td>{{event('gotpointercapture')}}</td>
   <td>Aucun (voir <a href="#Extensions_d'Element">Extensions d'Elements</a>)</td>
   <td>déclenché quand un élément reçoit la capture du pointeur.</td>
  </tr>
  <tr>
   <td>{{event('lostpointercapture')}}</td>
   <td>Aucun (voir <a href="#Extensions_d'Element">Extensions d'Element</a>)</td>
   <td>déclenché quand la capture du pointeur est désactivée.</td>
  </tr>
 </tbody>
</table>

<h3 id="Extensions_dElement">Extensions d'Element</h3>

<p>Il existe quatre extensions à l'interface {{domxref("Element")}}:</p>

<ul>
 <li>{{domxref("Element.ongotpointercapture","ongotpointercapture")}} - an EventHandler that returns the event handler (function) for the gotpointercapture event type.</li>
 <li>{{domxref("Element.onlostpointercapture","onlostpointercapture")}} - an EventHandler interface that returns the event handler (function) for the lostpointercapture event type.</li>
 <li>{{domxref("Element.setPointerCapture()","setPointerCapture()")}} - this method designates a specific element as the <em>capture target</em> of future pointer events.</li>
 <li>{{domxref("Element.releasePointerCapture()","releasePointerCapture()")}} - the method releases (stops) <em>pointer capture</em> that was previously set for a specific pointer event.</li>
</ul>

<h3 id="Extension_de_Navigator">Extension de Navigator</h3>

<p>La propriété {{domxref("Navigator.maxTouchPoints")}} est utilisé pour déterminer le nombre maximum de points de contact pris en charge à n'importe quel moment.</p>

<h2 id="Exemples">Exemples</h2>

<p>Cette section contient des exemples basiques d'utilisation d'interfaces d'événement de pointeur.</p>

<h3 id="Enregistrer_des_gestionnaires_dévénement">Enregistrer des gestionnaires d'événement</h3>

<p>This example registers a handler for every event type for the given element.</p>

<pre class="brush: html">&lt;html&gt;
&lt;script&gt;
function over_handler(event) { }
function enter_handler(event) { }
function down_handler(event) { }
function move_handler(event) { }
function up_handler(event) { }
function cancel_handler(event) { }
function out_handler(event) { }
function leave_handler(event) { }
function gotcapture_handler(event) { }
function lostcapture_handler(event) { }

function init() {
 var el=document.getElementById("target");
 // Register pointer event handlers
 el.onpointerover = over_handler;
 el.onpointerenter = enter_handler;
 el.onpointerdown = down_handler;
 el.onpointermove = move_handler;
 el.onpointerup = up_handler;
 el.onpointercancel = cancel_handler;
 el.onpointerout = out_handler;
 el.onpointerleave = leave_handler;
 el.gotpointercapture = gotcapture_handler;
 el.lostpointercapture = lostcapture_handler;
}
&lt;/script&gt;
&lt;body onload="init();"&gt;
&lt;div id="target"&gt; Touch me ... &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

<h3 id="Propriétés_des_événements">Propriétés des événements</h3>

<p>This example illustrates accessing all of a touch event's properties.</p>

<pre class="brush: html">&lt;html&gt;
&lt;script&gt;
var id = -1;

function process_id(event) {
  // Process this event based on the event's identifier
}
function process_mouse(event) {
  // Process the mouse pointer event
}
function process_pen(event) {
  // Process the pen pointer event
}
function process_touch(event) {
  // Process the touch pointer event
}
function process_tilt(tiltX, tiltY) {
  // Tilt data handler
}
function process_pressure(pressure) {
  // Pressure handler
}
function process_non_primary(event) {
  // Pressure handler
}

function down_handler(ev) {
 // Calculate the touch point's contact area
 var area = ev.width * ev.height;

 // Compare cached id with this event's id and process accordingly
 if (id == ev.identifier) process_id(ev);

 // Call the appropriate pointer type handler
 switch (ev.pointerType) {
   case "mouse":
     process_mouse(ev);
     break;
   case "pen":
     process_pen(ev);
     break;
   case "touch":
     process_touch(ev);
     break;
   default:
     console.log("pointerType " + ev.pointerType + " is Not suported");
 }

 // Call the tilt handler
 if (ev.tiltX != 0 &amp;&amp; ev.tiltY != 0) process_tilt(ev.tiltX, ev.tiltY);

 // Call the pressure handler
 process_pressure(ev.pressure);

 // If this event is not primary, call the non primary handler
 if (!ev.isPrimary) process_non_primary(evt);
}

function init() {
 var el=document.getElementById("target");
 // Register pointerdown handler
 el.onpointerdown = down_handler;
}
&lt;/script&gt;
&lt;body onload="init();"&gt;
 &lt;div id="target"&gt; Touch me ... &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

<h2 id="Déterminer_le_pointeur_principal">Déterminer le pointeur principal</h2>

<p>In some scenarios there may be multiple pointers (for example a device with both a touchscreen and a mouse) or a pointer supports multiple contact points (for example a touchscreen that supports multiple finger touches). The application can use the {{domxref("PointerEvent.isPrimary","isPrimary")}} property to identify a master pointer among the set of <em>active pointers</em> for each pointer type. If an application only wants to support a primary pointer, it can ignore all pointer events that are not primary.</p>

<p>For mouse, there is only one pointer so it will always be the primary pointer. For touch input, a pointer is considered primary if the user touched the screen when there were no other active touches. For pen and stylus input, a pointer is considered primary if the user's pen initially contacted the screen when there were no other active pens contacting the screen.</p>

<h2 id="Déterminer_létat_des_boutons">Déterminer l'état des boutons</h2>

<p>Some pointer devices, such as mouse and pen, support multiple buttons and the button presses can be <em>chorded</em> i.e. depressing an additional button while another button on the pointer device is already depressed. To determine the state of button presses, pointer events uses the {{domxref("MouseEvent.button","button")}} and {{domxref("MouseEvent.buttons","buttons")}} properties of the {{domxref("MouseEvent")}} interface (that {{domxref("PointerEvent")}} inherits from). The following table provides the values of <code>button</code> and <code>buttons</code> for the various device button states.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Device Button State</th>
   <th scope="col">button</th>
   <th scope="col">buttons</th>
  </tr>
  <tr>
   <td>Mouse move with no buttons pressed</td>
   <td>-1</td>
   <td>0</td>
  </tr>
  <tr>
   <td>Left Mouse, Touch Contact, Pen contact (with no modifier buttons pressed)</td>
   <td>0</td>
   <td>1</td>
  </tr>
  <tr>
   <td>Middle Mouse</td>
   <td>1</td>
   <td>4</td>
  </tr>
  <tr>
   <td>Right Mouse, Pen contact with barrel button pressed</td>
   <td>2</td>
   <td>2</td>
  </tr>
  <tr>
   <td>X1 (back) Mouse</td>
   <td>3</td>
   <td>8</td>
  </tr>
  <tr>
   <td>X2 (forward) Mouse</td>
   <td>4</td>
   <td>16</td>
  </tr>
  <tr>
   <td>Pen contact with eraser button pressed</td>
   <td>5</td>
   <td>32</td>
  </tr>
 </tbody>
</table>

<h2 id="Capture_du_pointeur">Capture du pointeur</h2>

<p>Pointer capture allows events for a particular {{domxref("PointerEvent","pointer event")}} to be re-targeted to a particular element instead of the normal <a href="#term_hit_test">hit test</a> at a pointer's location. This can be used to ensure that an element continues to receive pointer events even if the pointer device's contact moves off the element (for example by scrolling).</p>

<p>The following example shows pointer capture being set on an element.</p>

<pre class="brush: html">&lt;html&gt;
&lt;script&gt;
function downHandler(ev) {
 var el=document.getElementById("target");
 //Element 'target' will receive/capture further events
 el.setPointerCapture(ev.pointerId);
}
function init() {
 var el=document.getElementById("target");
 el.onpointerdown = downHandler;
}
&lt;/script&gt;
&lt;body onload="init();"&gt;
&lt;div id="target"&gt; Touch me ... &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

<p>The following example shows a pointer capture being released (when a {{event("pointercancel")}} event occurs. The browser does this automatically when a {{event("pointerup")}} or {{event("pointercancel")}} event occurs.</p>

<pre class="brush: html">&lt;html&gt;
&lt;script&gt;
function downHandler(ev) {
 var el=document.getElementById("target");
 // Element "target" will receive/capture further events
 el.setPointerCapture(ev.pointerId);
}
function cancelHandler(ev) {
 var el=document.getElementById("target");
 // Release the pointer capture
 el.releasePointerCapture(ev.pointerId);
}
function init() {
 var el=document.getElementById("target");
 // Register pointerdown and pointercancel handlers
 el.onpointerdown = downHandler;
 el.onpointercancel = cancelHandler;
}
&lt;/script&gt;
&lt;body onload="init();"&gt;
&lt;div id="target"&gt; Touch me ... &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

<h2 id="Propriété_touch-action">Propriété touch-action</h2>

<p>The {{cssxref("touch-action")}} CSS property is used to specifiy whether or not the browser should apply its default (<em>native</em>) touch behavior (such as zooming or panning) to a region. This property may be applied to all elements except: non-replaced inline elements, table rows, row groups, table columns, and column groups.</p>

<p>A value of <code>auto</code> means the browser is free to apply its default touch behavior (to the specified region) and the value of <code>none</code> disables the browser's default touch behavior for the region. The values <code>pan-x</code> and <code>pan-y</code>, mean that touches that begin on the specified region are only for horizontal and vertical scrolling, respectively. The value <code>manipulation</code> means the browser may consider touches that begin on the element are only for scrolling and zooming.</p>

<p>In the following example, the browser's default touch behavior is disabled for the <code>div</code> element.</p>

<pre class="brush: html">&lt;html&gt;
&lt;body&gt;
 &lt;div style="touch-action:none;"&gt;Can't touch this ... &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

<p>In the following example, default touch behavior is disabled for some <code>button</code> elements.</p>

<pre class="brush: css">button#tiny {
  touch-action: none;
}
</pre>

<p>In the following example, when the <code>target</code> element is touched, it will only pan in the horizontal direction.</p>

<pre class="brush: css">#target {
  touch-action: pan-x;
}
</pre>

<h2 id="Compatibilité_avec_les_événements_de_souris">Compatibilité avec les événements de souris</h2>

<p>Although the pointer event interfaces enable applications to create enhanced user experiences on pointer enabled devices, the reality is the vast majority of today's web content is designed to only work with mouse input. Consequently, even if a browser supports pointer events, the browser must still process mouse events so content that assumes mouse-only input will work as is without direct modification. Ideally, a pointer enabled application does not need to explicitly handle mouse input. However, because the browser must process mouse events, there may be some compatibility issues that need to be handled. This section contains information about pointer event and mouse event interaction and the ramifications for application developers.</p>

<p>The browser <em>may map generic pointer input to mouse events for compatibility with mouse-based content</em>. This mapping of events is called <em>compatibility mouse events</em>. Authors can prevent the production of certain compatibility mouse events by canceling the pointerdown event but note that:</p>

<ul>
 <li>Mouse events can only be prevented when the pointer is down.</li>
 <li>Hovering pointers (e.g. a mouse with no buttons pressed) cannot have their mouse events prevented.</li>
 <li>The mouseover, mouseout, mouseenter, and mouseleave events are never prevented (even if the pointer is down).</li>
</ul>

<h2 id="Bonnes_pratiques">Bonnes pratiques</h2>

<p>Here are some <em>best practices</em> to consider when using pointer events:</p>

<ul>
 <li>Minimize the amount of work done that is done in the event handlers.</li>
 <li>Add the event handlers to a specific target element (rather than the entire document or nodes higher up in the document tree).</li>
 <li>The target element (node) should be large enough to accommodate the largest contact surface area (typically a finger touch). If the target area is too small, touching it could result in firing other events for adjacent elements.</li>
</ul>

<h2 id="Implémentation_et_déploiement">Implémentation et déploiement</h2>

<p>The <a href="/en-US/docs/Web/API/PointerEvents#Browser_compatibility">pointer events browser compatibility data</a> indicates pointer event support among desktop and mobile browsers is relatively low, although additional implementations are in progress.</p>

<p>Some new value have been proposed for the {{cssxref("touch-action", "CSS touch-action")}} property as part of <a href="https://w3c.github.io/pointerevents/">Pointer Events Level 2</a> specification but currently those new values have no implementation support.</p>

<h2 id="Démos_and_exemples">Démos and exemples</h2>

<ul>
 <li><a href="http://patrickhlauke.github.io/touch/">Touch/pointer tests and demos (by Patrick H. Lauke)</a></li>
</ul>

<h2 id="Communauté">Communauté</h2>

<ul>
 <li><a href="https://github.com/w3c/pointerevents">Pointer Events Working Group</a></li>
 <li><a href="http://lists.w3.org/Archives/Public/public-pointer-events/">Mail list</a></li>
 <li><a href="irc://irc.w3.org:6667/">W3C #pointerevents IRC channel</a></li>
</ul>

<h2 id="Sujets_et_ressources_liés">Sujets et ressources liés</h2>

<ul>
 <li><a href="http://www.w3.org/TR/touch-events/">Touch Events Standard</a></li>
</ul>
