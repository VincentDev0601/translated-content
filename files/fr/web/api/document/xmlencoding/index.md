---
title: Document.xmlEncoding
slug: Web/API/Document/xmlEncoding
tags:
  - API
  - DOM
  - Document
  - Encodage
  - Propriétés
  - XML
translation_of: Web/API/Document/xmlEncoding
---
<p>{{APIRef("DOM")}}{{ obsolete_header("10.0") }}</p>

<p>Renvoie le codage déterminé par la déclaration XML. Devrait être <code>null</code> si non précisé ou inconnu.</p>

<div class="warning">
  <p><strong>Attention :</strong> N'utilisez pas cet attribut ; il a été supprimé de la spécification DOM Niveau 4 et n'est plus pris en charge dans Gecko 10.0 {{ geckoRelease("10.0") }}.</p>
</div>

<p>Si la déclaration XML indique :</p>

<pre>&lt;?xml version="1.0" encoding="UTF-16"?&gt;
</pre>

<p>... le résultat doit être "UTF-16".</p>

<p>Cependant, Firefox 3.0 inclut des informations sur l'"endianness" (par exemple, UTF-16BE pour le codage "big endian") et, tandis que cette information supplémentaire est supprimée à partir de Firefox 3.1b3, Firefox 3.1b3 consulte toujours l'encodage du fichier plutôt que la déclaration XML, comme la spécification le prévoit ("Un attribut spécifiant, <em>dans le cadre de la déclaration XML</em>, l'encodage de ce document.").</p>

<h3 id="Spécification">Spécification</h3>

<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-3-Core/core.html#Document3-encoding">http://www.w3.org/TR/DOM-Level-3-Cor...ment3-encoding</a></li>
 <li>A été supprimé de {{ spec("http://www.w3.org/TR/domcore/","DOM Core Level 4","WD") }}</li>
</ul>
