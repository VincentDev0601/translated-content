---
title: Element.scrollHeight
slug: Web/API/Element/scrollHeight
translation_of: Web/API/Element/scrollHeight
---
<p>{{ ApiRef() }}</p>

<p>L'attribut en lecture seule <strong><code>element.scrollHeight</code></strong> est une mesure de la hauteur du contenu d'un élément qui inclut le contenu débordant et non visible à l'écran. La valeur <code>scrollHeight</code> est égale à la hauteur minimum dont l'élément aurait besoin pour que le contenu rentre dans le viewpoint sans utiliser de barre de défilement. Cela inclut les marges internes mais pas les marges externes.</p>

<div class="note">
<p><strong>Note :</strong> Cette propriété arrondit la valeur à l'entier le plus proche. Si vous avez besoin d'une valeur précise, utilisez <a href="/fr/docs/DOM/element.getBoundingClientRect">element.getBoundingClientRect()</a>.</p>
</div>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="eval">var intElemScrollHeight = document.getElementById(id_attribute_value).scrollHeight;
</pre>

<p><code>intElemScrollHeight</code> est une variable contenant un entier correspondant à la valeur en pixels de la hauteur défilable de l'élément. <code>scrollHeight</code> est une propriété en lecture seule.</p>

<h2 id="Exemple">Exemple</h2>

<h2>Exemple</h2>

<p>Avec l'évènement {{domxref("GlobalEventHandlers/onscroll", "onscroll")}}, cette équivalence peut s'avérer utile afin de déterminer si un utilisateur a lu du texte ou non (voir aussi les propriétés {{domxref("element.scrollTop")}} et {{domxref("element.clientHeight")}}).</p>

<p>La case à cocher de la démo est désactivée et ne peut être cochée tant que l'ensemble du contenu n'a pas défilé.</p>

<h3 id="HTML">HTML</h3>

<pre class="brush: html">&lt;form name="registration"&gt;
  &lt;p&gt;
    &lt;textarea id="rules"&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum at laoreet magna.
Aliquam erat volutpat. Praesent molestie, dolor ut eleifend aliquam, mi ligula ultrices sapien, quis cursus
neque dui nec risus. Duis tincidunt lobortis purus eu aliquet. Quisque in dignissim magna. Aenean ac lorem at
velit ultrices consequat. Nulla luctus nisi ut libero cursus ultrices. Pellentesque nec dignissim enim. Phasellus
ut quam lacus, sed ultricies diam. Vestibulum convallis rutrum dolor, sit amet egestas velit scelerisque id.
Proin non dignissim nisl. Sed mi odio, ullamcorper eget mattis id, malesuada vitae libero. Integer dolor lorem,
mattis sed dapibus a, faucibus id metus. Duis iaculis dictum pulvinar. In nisi nibh, dapibus ac blandit at, porta
at arcu. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Praesent
dictum ipsum aliquet erat eleifend sit amet sollicitudin felis tempus. Aliquam congue cursus venenatis. Maecenas
luctus pellentesque placerat. Mauris nisl odio, condimentum sed fringilla a, consectetur id ligula. Praesent sem
sem, aliquet non faucibus vitae, iaculis nec elit. Nullam volutpat, lectus et blandit bibendum, nulla lorem congue
turpis, ac pretium tortor sem ut nibh. Donec vel mi in ligula hendrerit sagittis. Donec faucibus viverra fermentum.
Fusce in arcu arcu. Nullam at dignissim massa. Cras nibh est, pretium sit amet faucibus eget, sollicitudin in
ligula. Vivamus vitae urna mauris, eget euismod nunc. Aenean semper gravida enim non feugiat. In hac habitasse
platea dictumst. Cras eleifend nisl volutpat ante condimentum convallis. Donec varius dolor malesuada erat
consequat congue. Donec eu lacus ut sapien venenatis tincidunt. Quisque sit amet tellus et enim bibendum varius et
a orci. Donec aliquet volutpat scelerisque. Proin et tortor dolor. Ut aliquet, dolor a mattis sodales, odio diam
pulvinar sem, egestas pretium magna eros vitae felis. Nam vitae magna lectus, et ornare elit. Morbi feugiat, ipsum
ac mattis congue, quam neque mollis tortor, nec mollis nisl dolor a tortor. Maecenas varius est sit amet elit
interdum quis placerat metus posuere. Duis malesuada justo a diam vestibulum vel aliquam nisi ornare. Integer
laoreet nisi a odio ornare non congue turpis eleifend. Cum sociis natoque penatibus et magnis dis parturient montes,
nascetur ridiculus mus. Cras vulputate libero sed arcu iaculis nec lobortis orci fermentum.
    &lt;/textarea&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;input type="checkbox" id="agree" name="accept" /&gt;
    &lt;label for="agree"&gt;I agree&lt;/label&gt;
    &lt;input type="submit" id="nextstep" value="Next" /&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<h3 id="CSS">CSS</h3>

<pre class="brush: css">#notice {
  display: inline-block;
  margin-bottom: 12px;
  border-radius: 5px;
  width: 600px;
  padding: 5px;
  border: 2px #7FDF55 solid;
}

#rules {
  width: 600px;
  height: 130px;
  padding: 5px;
  border: #2A9F00 solid 2px;
  border-radius: 5px;
}</pre>

<h3 id="JavaScript">JavaScript</h3>

<pre class="brush: js">function checkReading () {
  if (checkReading.read) {
    return;
  }
  checkReading.read = this.scrollHeight - Math.round(this.scrollTop) === this.clientHeight;
  document.registration.accept.disabled = document.getElementById("nextstep").disabled = !checkReading.read;
  checkReading.noticeBox.textContent = checkReading.read ? "Thank you." : "Please, scroll and read the following text.";
}

onload = function () {
  var oToBeRead = document.getElementById("rules");
  checkReading.noticeBox = document.createElement("span");
  document.registration.accept.checked = false;
  checkReading.noticeBox.id = "notice";
  oToBeRead.parentNode.insertBefore(checkReading.noticeBox, oToBeRead);
  oToBeRead.parentNode.insertBefore(document.createElement("br"), oToBeRead);
  oToBeRead.onscroll = checkReading;
  checkReading.call(oToBeRead);
}</pre>

<h3>Résultat</h3>

<p>{{EmbedLiveSample('Exemple', '640', '400')}}</p>

<h2 id="Sp.C3.A9cification">Problèmes et solutions</h2>

<h3 id="Déterminer_si_un_élément_a_complètement_été_défilé">Déterminer si un élément a complètement été défilé</h3>

<p>L'expression suivante renvoie <code>true</code> si l'élément est à la fin du défilement, <code>false</code> si ça ne l'est pas.</p>

<pre class="brush: js">element.scrollHeight - element.scrollTop === element.clientHeight</pre>

<p>Associée à l'événement <a href="/fr/docs/DOM/element.onscroll">element.onscroll</a>, l'expression peut être utile pour déterminer si un utilisateur a lu un texte ou non (voir aussi les propriétés <a href="/fr/docs/DOM/element.scrollTop">element.scrollTop</a> et <a href="/fr/docs/DOM/element.clientHeight">element.clientHeight</a>. Par exemple :</p>

<pre class="brush: html">&lt;!doctype html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;
&lt;title&gt;MDN Example&lt;/title&gt;
&lt;script type="text/javascript"&gt;
function checkReading () {
  if (checkReading.read) { return; }
  checkReading.read = this.scrollHeight - this.scrollTop === this.clientHeight;
  document.registration.accept.disabled = document.getElementById("nextstep").disabled = !checkReading.read;
  checkReading.noticeBox.innerHTML = checkReading.read ?
    "Merci." :
    "Veuillez faire défiler la page et lire le texte qui suit.";
}

onload = function () {
  var oToBeRead = document.getElementById("rules");
  checkReading.noticeBox = document.createElement("span");
  document.registration.accept.checked = false;
  checkReading.noticeBox.id = "notice";
  oToBeRead.parentNode.insertBefore(checkReading.noticeBox, oToBeRead);
  oToBeRead.parentNode.insertBefore(document.createElement("br"), oToBeRead);
  oToBeRead.onscroll = checkReading;
  checkReading.call(oToBeRead);
}</pre>

<p><a href="/files/4589/readme-example.html">Voir l'exemple en action</a></p>

<h2 id="Sp.C3.A9cification">Spécification</h2>

<p><code>scrollHeight</code> fait partie du modèle objet <abbr>DHTML</abbr> de Microsoft Internet Explorer. Elle fait partie de la spécification : {{ SpecName("CSSOM View") }}.</p>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Navigateur</th>
   <th scope="col">Version</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Internet Explorer</td>
   <td><strong>8.0</strong></td>
  </tr>
  <tr>
   <td>Firefox (Gecko)</td>
   <td><strong>3.0</strong> (1.9)</td>
  </tr>
  <tr>
   <td>Opera</td>
   <td>?</td>
  </tr>
  <tr>
   <td>Safari | Chrome | Webkit</td>
   <td><strong>4.0</strong> | <strong>4.0</strong> | ?</td>
  </tr>
 </tbody>
</table>

<p><strong>Dans les versions inférieures à Firefox 21 :</strong> quand le contenu d'un élément ne génère pas de barre de défilement verticale, alors sa propriété <code>scrollHeight</code> est égale à sa propriété <code>clientHeight</code>. Cela signifie soit que le contenu est trop court pour avoir besoin d'une barre de défilement, soit que la propriété CSS<code> {{ cssxref("overflow") }}</code> de l'élément a pour valeur <code>visible</code>.</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="https://docs.microsoft.com/en-us/previous-versions//hh781509(v=vs.85)">MSDN: Measuring Element Dimension and Location with CSSOM in Windows Internet Explorer 9</a></li>
 <li><a href="/fr/docs/DOM/element.clientHeight">element.clientHeight</a></li>
 <li><a href="/fr/docs/DOM/element.offsetHeight">element.offsetHeight</a></li>
</ul>
