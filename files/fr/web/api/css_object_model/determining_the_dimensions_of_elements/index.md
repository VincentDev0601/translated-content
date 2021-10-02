---
title: Déterminer les dimensions des éléments
slug: Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements
translation_of: Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements
---
<p>{{APIRef("CSSOM View")}}</p>

<p>Il y a plusieurs propriétés que vous pouvez regarder dans le but de déterminer la largeur et la hauteur des éléments, et il peut être difficile de déterminer quelle est la bonne pour vos besoins.</p>

<p>Cet article est conçu pour vous aider à prendre cette décision. Notez que toutes ces propriétés sont en lecture seule .</p>

<p>Si vous voulez définir la largeur et la hauteur d'un élément, utilisez <code><a href="/fr/docs/Web/CSS/width">width</a></code> et <code><a href="/fr/docs/Web/CSS/height">height</a></code>; ou les propriétés <a href="/fr/docs/Web/CSS/min-width"> <code>min-width</code></a>, <a href="/fr/docs/Web/CSS/max-width"> <code>max-width</code></a>, <a href="/fr/docs/Web/CSS/min-height"> <code>min-height</code></a> et <a href="/fr/docs/Web/CSS/max-height"> <code>max-height</code></a>.</p>

<h2 id="How_much_room_does_it_use_up.3F">Que faut-il utiliser ?</h2>

<p>Si vous avez besoin de connaître les dimensions totales de l'espace occupé par un élément, y compris la largeur du contenu visible, les barres de défilement (le cas échéant), le rembourrage, et les frontières, vous pouvez utiliser les propriétés <code><a href="/fr/DOM/element.offsetWidth">offsetWidth</a></code> et <code><a href="/fr/DOM/element.offsetHeight">offsetHeight</a></code>.</p>

<p>La plupart du temps ce sont les mêmes que la largeur et la hauteur de <code><a href="/fr/DOM/element.getBoundingClientRect">getBoundingClientRect()</a></code>, quand il n'y a pas de transformations appliquées à l'élément. En cas de transformations, <code>offsetWidth</code> et <code>offsetHeight</code> renvoie la disposition de la largeur et la hauteur de l'élément, tandis que <code>getBoundingClientRect()</code> retourne le rendu de la largeur et de la hauteur.</p>

<p>A titre d'exemple, si l'élément a <code>width: 100px;</code> et <code>transform: scale(0.5);</code> <code>getBoundingClientRect()</code> retournera 50 comme largeur, tandis que <code>offsetWidth</code> retournera 100.</p>

<p><img src="dimensions-offset.png"></p>

<h2 id="What.27s_the_size_of_the_displayed_content.3F">Quelle est la taille du contenu affiché ?</h2>

<p>Si vous avez besoin de savoir combien prend d'espace le contenu réel affiché, y compris le rembourrage mais sans les frontières, les marges, ou les barres de défilement, vous pouvez utiliser les propriétés <code><a href="/fr/DOM/element.clientWidth">clientWidth</a></code> et  <a href="/fr/DOM/element.clientHeight"><code> clientHeight</code></a> :</p>

<p><img src="dimensions-client.png"></p>

<h2 id="How_big_is_the_content.3F">Grandeur totale</h2>

<p>Si vous avez besoin de connaître la taille réelle d'un élement, peu importe sa visibilité, vous devez utiliser les propriétés <code><a href="/fr/DOM/element.scrollWidth">scrollWidth</a></code> et <code><a href="/fr/docs/Web/API/Element.scrollHeight">scrollHeight</a></code>.</p>

<p>Elles retournent la largeur et la hauteur de l'ensemble du contenu d'un élément, même si seulement une partie de celui-ci est actuellement visible en raison de l'utilisation des barres de défilement.</p>

<p>Par exemple, si un élément de 600x400 pixels est affiché dans une boîte de défilement de 300x300 pixels, <code>scrollWidth</code> retourne 600 tandis que <code>scrollHeight</code> retourne 400.</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="http://www.w3.org/TR/cssom-view/">http://www.w3.org/TR/cssom-view/</a></li>
 <li><a href="https://docs.microsoft.com/en-us/previous-versions//hh781509(v=vs.85)">MSDN: Measuring Element Dimension and Location</a></li>
</ul>
