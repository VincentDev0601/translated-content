---
title: Référence du DOM
slug: Web/API/Document_Object_Model
tags:
  - API
  - DOM
  - Intermédiaire
  - Référence(2)
translation_of: Web/API/Document_Object_Model
---
<div>{{DefaultAPISidebar("DOM")}}</div>

<p>Le <em><strong>Document Object Model</strong></em> ou <strong>DOM</strong> (pour modèle objet de document) est une interface de programmation pour les documents HTML, XML et SVG. Il fournit une représentation structurée du document sous forme d'un arbre et définit la façon dont la structure peut être manipulée par les programmes, en termes de style et de contenu. Le DOM représente le document comme un ensemble de nœuds et d'objets possédant des propriétés et des méthodes. Les nœuds peuvent également avoir des gestionnaires d'événements qui se déclenchent lorsqu'un événement se produit. Cela permet de manipuler des pages web grâce à des scripts et/ou des langages de programmation. Les nœuds peuvent être associés à des gestionnaires d'événements. Une fois qu'un événement est déclenché, les gestionnaires d'événements sont exécutés.</p>

<p>Pour mieux comprendre le fonctionnement du DOM, <a href="/fr/docs/Web/API/Document_Object_Model/Introduction">une introduction est disponible</a>.</p>

<h2 id="Interfaces_du_DOM">Interfaces du DOM</h2>

<ul>
 <li>{{domxref("Attr")}}</li>
 <li>{{domxref("CharacterData")}}</li>
 <li>{{domxref("ChildNode")}} {{experimental_inline}}</li>
 <li>{{domxref("Comment")}}</li>
 <li>{{domxref("CustomEvent")}}</li>
 <li>{{domxref("Document")}}</li>
 <li>{{domxref("DocumentFragment")}}</li>
 <li>{{domxref("DocumentType")}}</li>
 <li>{{domxref("DOMError")}}  {{deprecated_inline}}</li>
 <li>{{domxref("DOMException")}}</li>
 <li>{{domxref("DOMImplementation")}}</li>
 <li>{{domxref("DOMString")}}</li>
 <li>{{domxref("DOMTimeStamp")}}</li>
 <li>{{domxref("DOMSettableTokenList")}}</li>
 <li>{{domxref("DOMStringList")}}</li>
 <li>{{domxref("DOMTokenList")}}</li>
 <li>{{domxref("Element")}}</li>
 <li>{{domxref("EventTarget")}}</li>
 <li>{{domxref("HTMLCollection")}}</li>
 <li>{{domxref("MutationObserver")}}</li>
 <li>{{domxref("Event")}}</li>
 <li>{{domxref("MutationRecord")}}</li>
 <li>{{domxref("NamedNodeMap")}}</li>
 <li>{{domxref("Node")}}</li>
 <li>{{domxref("NodeFilter")}}</li>
 <li>{{domxref("NodeIterator")}}</li>
 <li>{{domxref("NodeList")}}</li>
 <li>{{domxref("NonDocumentTypeChildNode")}}</li>
 <li>{{domxref("ParentNode")}}</li>
 <li>{{domxref("ProcessingInstruction")}}</li>
 <li>{{domxref("Selection")}}{{experimental_inline}}</li>
 <li>{{domxref("Range")}}</li>
 <li>{{domxref("Text")}}</li>
 <li>{{domxref("TextDecoder")}} {{experimental_inline}}</li>
 <li>{{domxref("TextEncoder")}} {{experimental_inline}}</li>
 <li>{{domxref("TimeRanges")}}</li>
 <li>{{domxref("TreeWalker")}}</li>
 <li>{{domxref("URL")}}</li>
 <li>{{domxref("Window")}}</li>
 <li>{{domxref("Worker")}}</li>
 <li>{{domxref("XMLDocument")}} {{experimental_inline}}</li>
</ul>

<h2 id="Interfaces_obsolètes_du_DOM_obsolete_inline">Interfaces obsolètes du DOM {{obsolete_inline}}</h2>

<p>Le DOM a été simplifié au cours du temps. Pour cette raison, les interfaces qui suivent, présentes dans la spécification du DOM de niveau 3 ou des niveaux antérieurs, ont été supprimées. Bien qu'il ne soit pas certain qu'elles ne soient pas réintroduites, elles doivent être considérées comme obsolètes et il faut éviter de les utiliser :</p>

<ul>
 <li>{{domxref("CDATASection")}}</li>
 <li>{{domxref("DocumentTouch")}}</li>
 <li>{{domxref("DOMConfiguration")}}</li>
 <li>{{domxref("DOMErrorHandler")}}</li>
 <li>{{domxref("DOMImplementationList")}}</li>
 <li>{{domxref("DOMImplementationRegistry")}}</li>
 <li>{{domxref("DOMImplementationSource")}}</li>
 <li>{{domxref("DOMLocator")}}</li>
 <li>{{domxref("DOMObject")}}</li>
 <li>{{domxref("DOMUserData")}}</li>
 <li>{{domxref("ElementTraversal")}}</li>
 <li>{{domxref("Entity")}}</li>
 <li>{{domxref("EntityReference")}}</li>
 <li>{{domxref("NamedNodeMap")}}</li>
 <li>{{domxref("NameList")}}</li>
 <li>{{domxref("Notation")}}</li>
 <li>{{domxref("TypeInfo")}}</li>
 <li>{{domxref("UserDataHandler")}}</li>
</ul>

<h2 id="Interfaces_HTML">Interfaces HTML</h2>

<p>Un document contenant du HTML est décrit grâce à l'interface {{domxref("HTMLDocument")}}. On notera que la spécification HTML étend également l'interface {{domxref("Document")}}.</p>

<p>Un objet <code>HTMLDocument</code> donne également accès à différentes fonctionnalités liées au navigateur comme l'onglet ou la fenêtre dans laquelle la page est dessinée, notamment grâce à l'interface {{domxref("Window")}}. On peut accéder à la mise en forme de la page via {{domxref("window.style")}} (généralement le CSS associé au document), à l'historique de navigation relatif au contexte via {{domxref("window.history")}} et enfin à la sélection faite dans le document via {{domxref("Selection")}}.</p>

<h3 id="Interfaces_des_éléments_HTML">Interfaces des éléments HTML</h3>

<ul>
 <li>{{domxref("HTMLAnchorElement")}}</li>
 <li>{{domxref("HTMLAppletElement")}}</li>
 <li>{{domxref("HTMLAreaElement")}}</li>
 <li>{{domxref("HTMLAudioElement")}}</li>
 <li>{{domxref("HTMLBaseElement")}}</li>
 <li>{{domxref("HTMLBodyElement")}}</li>
 <li>{{domxref("HTMLBRElement")}}</li>
 <li>{{domxref("HTMLButtonElement")}}</li>
 <li>{{domxref("HTMLCanvasElement")}}</li>
 <li>{{domxref("HTMLDataElement")}}</li>
 <li>{{domxref("HTMLDataListElement")}}</li>
 <li>{{domxref("HTMLDialogElement")}}</li>
 <li>{{domxref("HTMLDirectoryElement")}}</li>
 <li>{{domxref("HTMLDivElement")}}</li>
 <li>{{domxref("HTMLDListElement")}}</li>
 <li>{{domxref("HTMLElement")}}</li>
 <li>{{domxref("HTMLEmbedElement")}}</li>
 <li>{{domxref("HTMLFieldSetElement")}}</li>
 <li>{{domxref("HTMLFontElement")}}</li>
 <li>{{domxref("HTMLFormElement")}}</li>
 <li>{{domxref("HTMLFrameElement")}}</li>
 <li>{{domxref("HTMLFrameSetElement")}}</li>
 <li>{{domxref("HTMLHeadElement")}}</li>
 <li>{{domxref("HTMLHeadingElement")}}</li>
 <li>{{domxref("HTMLHtmlElement")}}</li>
 <li>{{domxref("HTMLHRElement")}}</li>
 <li>{{domxref("HTMLIFrameElement")}}</li>
 <li>{{domxref("HTMLImageElement")}}</li>
 <li>{{domxref("HTMLInputElement")}}</li>
 <li>{{domxref("HTMLKeygenElement")}}</li>
 <li>{{domxref("HTMLLabelElement")}}</li>
 <li>{{domxref("HTMLLegendElement")}}</li>
 <li>{{domxref("HTMLLIElement")}}</li>
 <li>{{domxref("HTMLLinkElement")}}</li>
 <li>{{domxref("HTMLMapElement")}}</li>
 <li>{{domxref("HTMLMediaElement")}}</li>
 <li>{{domxref("HTMLMenuElement")}}</li>
 <li>{{domxref("HTMLMetaElement")}}</li>
 <li>{{domxref("HTMLMeterElement")}}</li>
 <li>{{domxref("HTMLModElement")}}</li>
 <li>{{domxref("HTMLObjectElement")}}</li>
 <li>{{domxref("HTMLOListElement")}}</li>
 <li>{{domxref("HTMLOptGroupElement")}}</li>
 <li>{{domxref("HTMLOptionElement")}}</li>
 <li>{{domxref("HTMLOutputElement")}}</li>
 <li>{{domxref("HTMLParagraphElement")}}</li>
 <li>{{domxref("HTMLParamElement")}}</li>
 <li>{{domxref("HTMLPreElement")}}</li>
 <li>{{domxref("HTMLProgressElement")}}</li>
 <li>{{domxref("HTMLQuoteElement")}}</li>
 <li>{{domxref("HTMLScriptElement")}}</li>
 <li>{{domxref("HTMLSelectElement")}}</li>
 <li>{{domxref("HTMLSourceElement")}}</li>
 <li>{{domxref("HTMLSpanElement")}}</li>
 <li>{{domxref("HTMLStyleElement")}}</li>
 <li>{{domxref("HTMLTableElement")}}</li>
 <li>{{domxref("HTMLTableCaptionElement")}}</li>
 <li>{{domxref("HTMLTableCellElement")}}</li>
 <li>{{domxref("HTMLTableDataCellElement")}}</li>
 <li>{{domxref("HTMLTableHeaderCellElement")}}</li>
 <li>{{domxref("HTMLTableColElement")}}</li>
 <li>{{domxref("HTMLTableRowElement")}}</li>
 <li>{{domxref("HTMLTableSectionElement")}}</li>
 <li>{{domxref("HTMLTextAreaElement")}}</li>
 <li>{{domxref("HTMLTimeElement")}}</li>
 <li>{{domxref("HTMLTitleElement")}}</li>
 <li>{{domxref("HTMLTrackElement")}}</li>
 <li>{{domxref("HTMLUListElement")}}</li>
 <li>{{domxref("HTMLUnknownElement")}}</li>
 <li>{{domxref("HTMLVideoElement")}}</li>
</ul>

<h3 id="Autres_interfaces">Autres interfaces</h3>

<ul>
 <li>{{domxref("CanvasRenderingContext2D")}}</li>
 <li>{{domxref("CanvasGradient")}}</li>
 <li>{{domxref("CanvasPattern")}}</li>
 <li>{{domxref("TextMetrics")}}</li>
 <li>{{domxref("ImageData")}}</li>
 <li>{{domxref("CanvasPixelArray")}}</li>
 <li>{{domxref("NotifyAudioAvailableEvent")}}</li>
 <li>{{domxref("HTMLAllCollection")}}</li>
 <li>{{domxref("HTMLFormControlsCollection")}}</li>
 <li>{{domxref("HTMLOptionsCollection")}}</li>
 <li>{{domxref("HTMLPropertiesCollection")}}</li>
 <li>{{domxref("DOMStringMap")}}</li>
 <li>{{domxref("RadioNodeList")}}</li>
 <li>{{domxref("MediaError")}}</li>
</ul>

<h3 id="Interfaces_HTML_obsolètes_obsolete_inline">Interfaces HTML obsolètes {{obsolete_inline}}</h3>

<ul>
 <li>{{domxref("HTMLBaseFontElement")}}</li>
 <li>{{domxref("HTMLIsIndexElement")}}</li>
</ul>

<h2 id="Interfaces_SVG">Interfaces SVG</a></h2>

<h3 id="Interfaces_des_éléments_SVG">Interfaces des éléments SVG</h3>

<ul>
 <li>{{domxref("SVGAElement")}}</li>
 <li>{{domxref("SVGAltGlyphElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGAltGlyphDefElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGAltGlyphItemElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGAnimationElement")}}</li>
 <li>{{domxref("SVGAnimateElement")}}</li>
 <li>{{domxref("SVGAnimateColorElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGAnimateMotionElement")}}</li>
 <li>{{domxref("SVGAnimateTransformElement")}}</li>
 <li>{{domxref("SVGCircleElement")}}</li>
 <li>{{domxref("SVGClipPathElement")}}</li>
 <li>{{domxref("SVGColorProfileElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGComponentTransferFunctionElement")}}</li>
 <li>{{domxref("SVGCursorElement")}}</li>
 <li>{{domxref("SVGDefsElement")}}</li>
 <li>{{domxref("SVGDescElement")}}</li>
 <li>{{domxref("SVGElement")}}</li>
 <li>{{domxref("SVGEllipseElement")}}</li>
 <li>{{domxref("SVGFEBlendElement")}}</li>
 <li>{{domxref("SVGFEColorMatrixElement")}}</li>
 <li>{{domxref("SVGFEComponentTransferElement")}}</li>
 <li>{{domxref("SVGFECompositeElement")}}</li>
 <li>{{domxref("SVGFEConvolveMatrixElement")}}</li>
 <li>{{domxref("SVGFEDiffuseLightingElement")}}</li>
 <li>{{domxref("SVGFEDisplacementMapElement")}}</li>
 <li>{{domxref("SVGFEDistantLightElement")}}</li>
 <li>{{domxref("SVGFEDropShadowElement")}}</li>
 <li>{{domxref("SVGFEFloodElement")}}</li>
 <li>{{domxref("SVGFEFuncAElement")}}</li>
 <li>{{domxref("SVGFEFuncBElement")}}</li>
 <li>{{domxref("SVGFEFuncGElement")}}</li>
 <li>{{domxref("SVGFEFuncRElement")}}</li>
 <li>{{domxref("SVGFEGaussianBlurElement")}}</li>
 <li>{{domxref("SVGFEImageElement")}}</li>
 <li>{{domxref("SVGFEMergeElement")}}</li>
 <li>{{domxref("SVGFEMergeNodeElement")}}</li>
 <li>{{domxref("SVGFEMorphologyElement")}}</li>
 <li>{{domxref("SVGFEOffsetElement")}}</li>
 <li>{{domxref("SVGFEPointLightElement")}}</li>
 <li>{{domxref("SVGFESpecularLightingElement")}}</li>
 <li>{{domxref("SVGFESpotLightElement")}}</li>
 <li>{{domxref("SVGFETileElement")}}</li>
 <li>{{domxref("SVGFETurbulenceElement")}}</li>
 <li>{{domxref("SVGFilterElement")}}</li>
 <li>{{domxref("SVGFilterPrimitiveStandardAttributes")}}</li>
 <li>{{domxref("SVGFontElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGFontFaceElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGFontFaceFormatElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGFontFaceNameElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGFontFaceSrcElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGFontFaceUriElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGForeignObjectElement")}}</li>
 <li>{{domxref("SVGGElement")}}</li>
 <li>{{domxref("SVGGeometryElement")}}</li>
 <li>{{domxref("SVGGlyphElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGGlyphRefElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGGradientElement")}}</li>
 <li>{{domxref("SVGGraphicsElement")}}</li>
 <li>{{domxref("SVGHatchElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGHatchpathElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGHKernElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGImageElement")}}</li>
 <li>{{domxref("SVGLinearGradientElement")}}</li>
 <li>{{domxref("SVGLineElement")}}</li>
 <li>{{domxref("SVGMarkerElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGMaskElement")}}</li>
 <li>{{domxref("SVGMeshElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGMeshGradientElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGMeshpatchElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGMeshrowElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGMetadataElement")}}</li>
 <li>{{domxref("SVGMissingGlyphElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGMPathElement")}}</li>
 <li>{{domxref("SVGPathElement")}}</li>
 <li>{{domxref("SVGPatternElement")}}</li>
 <li>{{domxref("SVGPolylineElement")}}</li>
 <li>{{domxref("SVGPolygonElement")}}</li>
 <li>{{domxref("SVGRadialGradientElement")}}</li>
 <li>{{domxref("SVGRectElement")}}</li>
 <li>{{domxref("SVGScriptElement")}}</li>
 <li>{{domxref("SVGSetElement")}}</li>
 <li>{{domxref("SVGSolidcolorElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGStopElement")}}</li>
 <li>{{domxref("SVGStyleElement")}}</li>
 <li>{{domxref("SVGSVGElement")}}</li>
 <li>{{domxref("SVGSwitchElement")}}</li>
 <li>{{domxref("SVGSymbolElement")}}</li>
 <li>{{domxref("SVGTextContentElement")}}</li>
 <li>{{domxref("SVGTextElement")}}</li>
 <li>{{domxref("SVGTextPathElement")}}</li>
 <li>{{domxref("SVGTextPositioningElement")}}</li>
 <li>{{domxref("SVGTitleElement")}}</li>
 <li>{{domxref("SVGTRefElement")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGTSpanElement")}}</li>
 <li>{{domxref("SVGUseElement")}}</li>
 <li>{{domxref("SVGUnknownElement")}} {{experimental_inline}}</li>
 <li>{{domxref("SVGViewElement")}}</li>
 <li>{{domxref("SVGVKernElement")}} {{deprecated_inline}}</li>
</ul>

<h3 id="Interfaces_pour_les_types_de_donnée_SVG">Interfaces pour les types de donnée SVG</h3>

<p>Voici l'API du DOM pour les types de donnée utilisés pour les propriétés et attributs SVG.</p>

<div class="note">
<p><strong>Note :</strong> À partir de {{Gecko("5.0")}}, les interfaces suivantes relatives à SVG et qui représentent des listes d'objets sont indexées et permettent d'y accéder. Elles possèdent en plus une propriété de longueur qui indique le nombre d'éléments dans la liste : {{domxref("SVGLengthList")}}, {{domxref("SVGNumberList")}}, {{domxref("SVGPathSegList")}} et {{domxref("SVGPointList")}}.</p>
</div>

<h4 id="Interfaces_statiques">Interfaces statiques</h4>

<ul>
 <li>{{domxref("SVGAngle")}}</li>
 <li>{{domxref("SVGColor")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGICCColor")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGElementInstance")}}</li>
 <li>{{domxref("SVGElementInstanceList")}}</li>
 <li>{{domxref("SVGLength")}}</li>
 <li>{{domxref("SVGLengthList")}}</li>
 <li>{{domxref("SVGMatrix")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGNameList")}}</li>
 <li>{{domxref("SVGNumber")}}</li>
 <li>{{domxref("SVGNumberList")}}</li>
 <li>{{domxref("SVGPaint")}}</li>
 <li>{{domxref("SVGPathSeg")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegClosePath")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegMovetoAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegMovetoRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegLinetoAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegLinetoRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoCubicAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoCubicRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoQuadraticAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoQuadraticRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegArcAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegArcRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegLinetoHorizontalAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegLinetoHorizontalRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegLinetoVerticalAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegLinetoVerticalRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoCubicSmoothAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoCubicSmoothRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoQuadraticSmoothAbs")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegCurvetoQuadraticSmoothRel")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPathSegList")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPoint")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPointList")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGPreserveAspectRatio")}}</li>
 <li>{{domxref("SVGRect")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGStringList")}}</li>
 <li>{{domxref("SVGTransform")}}</li>
 <li>{{domxref("SVGTransformList")}}</li>
</ul>

<h4 id="Interfaces_animées">Interfaces animées</h4>

<ul>
 <li>{{domxref("SVGAnimatedAngle")}}</li>
 <li>{{domxref("SVGAnimatedBoolean")}}</li>
 <li>{{domxref("SVGAnimatedEnumeration")}}</li>
 <li>{{domxref("SVGAnimatedInteger")}}</li>
 <li>{{domxref("SVGAnimatedLength")}}</li>
 <li>{{domxref("SVGAnimatedLengthList")}}</li>
 <li>{{domxref("SVGAnimatedNumber")}}</li>
 <li>{{domxref("SVGAnimatedNumberList")}}</li>
 <li>{{domxref("SVGAnimatedPathData")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGAnimatedPoints")}}</li>
 <li>{{domxref("SVGAnimatedPreserveAspectRatio")}}</li>
 <li>{{domxref("SVGAnimatedRect")}}</li>
 <li>{{domxref("SVGAnimatedString")}}</li>
 <li>{{domxref("SVGAnimatedTransformList")}}</li>
</ul>

<h3 id="Interfaces_relatives_à_SMIL">Interfaces relatives à SMIL</h3>

<ul>
 <li>{{domxref("ElementTimeControl")}}</li>
 <li>{{domxref("TimeEvent")}}</li>
</ul>

<h3 id="Autres_interfaces_SVG">Autres interfaces SVG</h3>

<ul>
 <li>{{domxref("GetSVGDocument")}}</li>
 <li>{{domxref("ShadowAnimation")}}</li>
 <li>{{domxref("SVGColorProfileRule")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGCSSRule")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGDocument")}}</li>
 <li>{{domxref("SVGException")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGExternalResourcesRequired")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGFitToViewBox")}}</li>
 <li>{{domxref("SVGLangSpace")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGLocatable")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGRenderingIntent")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGStylable")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGTests")}}</li>
 <li>{{domxref("SVGTransformable")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGUnitTypes")}}</li>
 <li>{{domxref("SVGUseElementShadowRoot")}}</li>
 <li>{{domxref("SVGURIReference")}}</li>
 <li>{{domxref("SVGViewSpec")}} {{deprecated_inline}}</li>
 <li>{{domxref("SVGZoomAndPan")}}</li>
 <li>{{domxref("SVGZoomEvent")}} {{deprecated_inline}}</li>
</ul>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li><a href="/fr/docs/Web/API/Référence_du_DOM_Gecko/Exemples">Exemples appliqués pour le DOM</a></li>
</ul>
