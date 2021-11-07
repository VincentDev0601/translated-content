---
title: Attributs SVG de traitement conditionnel
slug: Web/SVG/Attribute/Conditional_Processing
translation_of: Web/SVG/Attribute/Conditional_Processing
---
<p>Les <em>attributs SVG de traitement conditionnel</em> sont tous les attributs qui peuvent être spécifiés sur des éléments SVG pour contrôler si l'élément sur lequel il s'applique doit s'afficher ou non.</p>

<ul>
 <li>externalResourcesRequired</li>
 <li>requiredExtensions</li>
 <li>requiredFeatures</li>
 <li>systemLanguage</li>
</ul>

<h2 id="Attributs">Attributs</h2>

<dl>
 <dt>{{SVGAttr('externalResourcesRequired')}} {{deprecated_inline('svg2')}}</dt>
 <dd>Si sa valeur vaut <code>true</code>, cela indique que le navigateur doit attendre que toutes les ressources externes nécessaires au rendu de cet élément soient chargées avant de traiter l'élément associé.<br>
 <small><em>Valeur</em>: <strong><code>false</code></strong>|<code>true</code>; <em>Animation</em>: <strong>Non</strong></small></dd>
 <dt>{{SVGAttr('requiredExtensions')}}</dt>
 <dd>Liste toutes les fonctionnalités devant être prises en charge par le navigateur pour autoriser l'affichage de l'élément associé.<br>
 <small><em>Valeur</em>: Une liste d'URI séparées par des espaces; <em>Animation</em>: <strong>Non</strong></small></dd>
 <dt>{{SVGAttr('requiredFeatures')}} {{deprecated_inline('svg2')}}</dt>
 <dd>Liste toutes les fonctionnalités, <a href="https://www.w3.org/TR/SVG11/feature.html">telles que définies dans la spécification SVG 1.1</a>, devant être prises en charge par le navigateur pour autoriser l'affichage de l'élément associé.<br>
 <small><em>Valeur</em>: Une list d'URI séparées par espaces; <em>Animation</em>: <strong>Non</strong></small></dd>
 <dt>{{SVGAttr('systemLanguage')}}</dt>
 <dd>Indique la langue que l'utilisatteur doit avoir choisit pour autoriser l'affichage l'élément associé.<br>
 <small><em>Valeur</em>: Une liste d'<a href="http://www.ietf.org/rfc/bcp/bcp47.txt">ID de langage</a> séparés par des virgules; <em>Animation</em>: <strong>Non</strong></small></dd>
</dl>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("svg.attributes.conditional_processing")}}</p>
