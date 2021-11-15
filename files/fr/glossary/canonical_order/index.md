---
title: Ordre canonique
slug: Glossary/Canonical_order
tags:
  - CSS
  - Encodage
  - Glossaire
  - ordre canonique
translation_of: Glossary/Canonical_order
original_slug: Glossaire/Ordre_canonique
---
<p>En CSS, la locution "ordre canonique" est utilisée pour désigner l'ordre dans lequel des valeurs séparées doivent être spécifiées (ou {{Glossary("parse","analysées")}}) ou doivent être {{Glossary("serialization","sérialisées")}} dans le cadre d'une valeur de propriété CSS. Il est défini par la {{Glossary ("Syntax","syntaxe")}} formelle de la propriété et se réfère normalement à l'ordre dans lequel les valeurs longues doivent être spécifiées dans le cadre d'une seule valeur raccourcie.</p>

<p>Par exemple, {{cssxref("background")}}, les valeurs de propriété raccourcie sont constituées de plusieurs propriétés  <code>background-*</code> . L'ordre canonique de ces valeurs longues est défini comme suit :</p>

<ol>
 <li>{{cssxref("background-image")}}</li>
 <li>{{cssxref("background-position")}}</li>
 <li>{{cssxref("background-size")}}</li>
 <li>{{cssxref("background-repeat")}}</li>
 <li>{{cssxref("background-attachment")}}</li>
 <li>{{cssxref("background-origin")}}</li>
 <li>{{cssxref("background-clip")}}</li>
 <li>{{cssxref("background-color")}}</li>
</ol>

<p>De plus, sa syntaxe exige que, si une valeur pour {{cssxref("background-size")}} est donnée, elle doit être spécifiée après la valeur de {{cssxref("background-position")}}, séparée par une barre oblique. D'autres valeurs peuvent apparaître dans n'importe quel ordre.</p>

<h2 id="En_apprendre_plus">En apprendre plus</h2>

<ul>
 <li><a href="https://stackoverflow.com/questions/28963536/what-does-canonical-order-mean-with-respect-to-css-properties">Que signifie “ordre canonique” en ce qui concerne les propriétés CSS ?</a> (en) sur Stack Overflow qui fournit également d'autres discussions utiles.</li>
 <li>La <a href="/fr/docs/Web/CSS/Syntaxe_de_d%C3%A9finition_des_valeurs">description de la syntaxe formelle utilisée pour les valeurs CSS</a> sur MDN</li>
</ul>
