---
title: Opérations de glissement
slug: Web/API/HTML_Drag_and_Drop_API/Drag_operations
translation_of: Web/API/HTML_Drag_and_Drop_API/Drag_operations
original_slug: Web/API/API_HTML_Drag_and_Drop/Opérations_de_glissement
---
<p>Ce qui suit décrit les étapes qui se déroulent lors d'un Glisser Déposer.</p>

<div class="note">
  <p><strong>Note :</strong> Les opérations de glisser décrits dans ce document utilisent l'interface {{domxref("DataTransfer")}}. Ce document n'utilise pas l'interface {{domxref("DataTransferItem")}} ni l'interface {{domxref("DataTransferItemList")}}.</p>
</div>

<h2 id="draggableattribute">L'attribut draggable</h2>

<p>Dans une page Web, certains cas nécessitent l'usage du Glisser Déposer. Il peut servir pour des sélections de texte, d'images ou de liens. Lorsqu'une image ou un lien sont glissés, l'URL de l'image ou du lien est défini comme données du glissement, et le Glisser commence. Pour d'autres éléments, il peut s'agir d'une sélection effectuée qui servira au glissement. Pour voir cet effet, sélectionnez une zone dans une page Web, puis cliquez dedans en maintenant le bouton de la souris et glissez la sélection. Un rendu translucide de la sélection apparaitra en suivant le pointeur de la souris. Il s'agit toutefois du comportement par défaut du glissement si aucun scrutateur n'a été défini pour traiter les données.</p>

<p>En HTML, excepté le comportement par défaut des images, des liens et des sélections, aucun autre élément ne peut être glissé. Tous les éléments XUL peuvent être glissés.</p>

<p>Pour rendre un autre élément HTML glissable, deux choses doivent être faites :</p>

<ul>
 <li>Définissez l'attribut <code>{{htmlattrxref("draggable")}}</code> à <code>true</code> sur l'élément que vous voulez rendre glissable.</li>
 <li>Ajoutez un scrutateur sur l'événement <code>{{event("dragstart")}}</code> et définissez les données du glissement dans ce scrutateur.</li>
 <li>{{domxref("DataTransfer.setData","Définir la donnée de glissement")}} au sein du scrutateur ajouté précédemment.</li>
</ul>

<p>Voici un exemple qui permet à une section de contenu d'être glissée :</p>

<pre>&lt;div draggable="true" ondragstart="event.dataTransfer.setData('text/plain', 'Ce texte peut être glissé')"&gt;
  Ce texte &lt;strong&gt;peut&lt;/strong&gt; être glissé.
&lt;/div&gt;
</pre>

<p>L'attribut <code>{{htmlattrxref("draggable")}}</code> est défini à true, ce qui rend l'élément glissant. Si cet attribut est omis ou défini à false, l'élément ne serait pas glissant et le texte serait alors simplement sélectionné. Cet attribut peut être placé sur n'importe quel élément, y compris des images et des liens. Toutefois, pour les deux derniers, la valeur par défaut est true, donc vous n'utiliserez l'attribut <code>{{htmlattrxref("draggable")}}</code> <code> </code>que pour le définir à <code>false</code> pour interdire le glissement de ces éléments.</p>

<p>Notez que lorsqu'un élément est rendu glissable, le texte ou les autres éléments qu'il contient ne peuvent plus être sélectionné de manière classique en cliquant et déplaçant la souris. Au lieu de cela, l'utilisateur doit maintenir la touche <kbd>Alt</kbd> appuyée pour sélectionner le texte avec la souris, ou bien utilisez le clavier.</p>

<p>Pour des éléments XUL, il n'est pas nécessaire d'utiliser l'attribut <code>{{htmlattrxref("draggable")}}</code>, car tous les éléments XUL sont glissables.</p>

<pre>&lt;button label="Glisse moi" ondragstart="event.dataTransfer.setData('text/plain', 'Bouton à glisser');"&gt;
</pre>

<p> </p>

<h2 id="dragstart">Démarrer une opération de glissement</h2>

<p>Dans cet exemple, un scrutateur est ajouté à l'événement dragstart en utilisant l'attribut <code>ondragstart</code>.</p>

<pre>&lt;div draggable="true" ondragstart="event.dataTransfer.setData('text/plain', 'Ce texte peut être glissé')"&gt;
  Ce texte &lt;strong&gt;peut&lt;/strong&gt; être glissé.
&lt;/div&gt;
</pre>

<p>Lorsqu'un utilisateur commence un glissement, l'événement dragstart est déclenché. Dans cet exemple, le scrutateur dragstart a été ajouté à l'élément à déplacer lui-même. Vous pouvez toutefois mettre le scrutateur sur un ancètre plus élevé car l'événement drag diffuse comme le font les autres événements. À l'intérieur de l'événement dragstart, vous devez spécifier la donnée de glissement, l'image filligrane et les effets du glissement tels que décrits ci-dessous. Cependant, seule la donnée de glissement est nécessaire ; l'image et les effets du glissement par défaut sont suffisants pour la majorité des cas.</p>

<h2 id="dragdata">Donnée de glissement</h2>

<p>Tous les événements de glissement ont une propriété appelée <a href="/Fr/GlisserD%C3%A9poser/DataTransfer">dataTransfer</a> utilisée pour contenir la donnée de glissement.</p>

<p>Lorsqu'un glissement a lieu, une donnée doit être associée au glissement pour identifier ce qui est en train de glisser. Par exemple, lors du glissement d'un texte sélectionné dans un champs de texte, la donnée associée au glissement est le texte lui-même. De même, lors du glissement d'un lien, la donnée associée est l'URL du lien.</p>

<p>La donnée de glissement contient deux informations : son type ou format et sa valeur. Le format est une chaîne de caractère (telle que <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#text">text/plain</a> pour un texte), et la valeur est un texte. Lorsqu'un glissement démarre, vous devez lui ajouter en fournissant un type et la donnée. Dans les scrutateurs des événements <code>dragenter</code> et <code>dragover</code> au cours d'un glissement, vous pouvez vérifier les types de données et indiquer si un dépôt est permis ou non. Par exemple, une cible de dépôt qui accepte que des liens testera les types lien <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#link">text/uri-list</a>. Pendant un évément de dépôt, un scrutateur récupèrera la donnée glissée et l'insèrera dans la zone de dépôt.</p>

<p>Les types MIME habituels sont <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#text">text/plain</a> ou <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#image">image/jpeg</a>, mais vous pouvez créer vos propres types. La liste des types les plus utilisés est disponible sur <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement">cette page</a>.</p>

<p>Un glissement peut fournir une donnée dans différents types. Ceci permet à une donnée d'être disponible dans des types spécifiques, souvent personnalisés, toujours en fournissant un format pour les cibles ne supportant pas ces types spécifiques. Habituellement, il s'agit toujours d'une version textuelle de type <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#text">text/plain</a>. La donnée n'en sera qu'une représentation sous la forme d'un texte.</p>

<p>Pour définir une donnée dans un dataTransfer, utilisez la méthode <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#setData">setData</a>. Elle prend deux arguments qui sont le type de la donnée et sa valeur. Par exemple :</p>

<pre>event.dataTransfer.setData("text/plain", "Texte à glisser");
</pre>

<p>Dans ce cas, la valeur de la donnée est "Texte à glisser" et son format est <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#text">text/plain</a>.</p>

<p>Vous pouvez fournir une donnée dans de multiples formats. Il suffit d'appeler la méthode <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#setData">setData</a> plusieurs fois avec chacun des formats. Vous devez l'appeler dans l'ordre du format le plus spécifique au moins spécifique.</p>

<pre>var dt = event.dataTransfer;
dt.setData("application/x-bookmark", bookmarkString);
dt.setData("text/uri-list", "http://www.mozilla.org");
dt.setData("text/plain", "http://www.mozilla.org");
</pre>

<p>Ici, une donnée est ajoutée avec trois types différents. Le premier type 'application/x-bookmark' est un type personnalisé. Toutes les applications ne vont pas supporter ce type, mais vous pouvez l'utiliser pour le glissement entre des zones d'une même application ou d'un même site. En fournissant la donnée avec d'autres types, vous la rendez disponible à moindre échelle pour d'autres applications. Le type 'application/x-bookmark' fournira ainsi plus de détail à l'application qu'avec les autres types qui ne seraient que de simples liens ou textes.</p>

<p>Notez que cet exemple, <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#link">text/uri-list</a> et <a href="/Fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#text">text/plain</a> contiennent la même donnée. C'est souvent le cas, mais pas forcément nécessaire.</p>

<p>Si vous essayez d'ajouter une donnée deux fois avec le même format, alors la nouvelle donnée remplacera l'ancienne, mais à la même position que l'ancienne dans la liste.</p>

<p>Vous pouvez effacer la donnée en utilisant la méthode <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#clearData">clearData</a>, avec un seul argument qui est le type de la donnée à effacer.</p>

<pre>event.dataTransfer.clearData("text/uri-list");
</pre>

<p>L'argument de type de la méthode <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#clearData">clearData</a> est optionnel. S'il n'est pas précisé, la donnée associée à tous les types est effacée. Et si aucune donnée à glisser n'est ajoutée, alors l'opération de glissement ne s'effectue pas.</p>

<h2 id="dragfeedback">Définir l'image filigrane d'un glissement</h2>

<p>Lorsqu'un glissement a lieu, une image translucide est générée à partir de l'origine du glissement (l'élément d'origine ayant déclenché l'événement), et cette image suit le déplacement de la souris. Elle est créée automatiquement donc vous n'avez pas à le faire vous même. Toutefois, vous pouvez personnaliser cette image filigrane grâce à <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#setDragImage">setDragImage</a>.</p>

<pre>event.dataTransfer.setDragImage(image, xOffset, yOffset);
</pre>

<p>Trois arguments sont nécessaires. Le premier est la référence à une image. Cette référence pointera en gérénal vers un élément image, mais elle peut pointer aussi vers un canvas ou vers tous autres éléments. L'image filigrane sera simplement générée telle qu'elle ressemble à l'écran, et dessinée à sa taille d'origine. Il est également possible d'utiliser des images et des canvas qui ne sont pas dans un document, comme le montre cet exemple :</p>

<pre>function dragWithCustomImage(event)
{
  var canvas = document.createElement("canvas");
  canvas.width = canvas.height = 50;

  var ctx = canvas.getContext("2d");
  ctx.lineWidth = 4;
  ctx.moveTo(0, 0);
  ctx.lineTo(50, 50);
  ctx.moveTo(0, 50);
  ctx.lineTo(50, 0);
  ctx.stroke();

  var dt = event.dataTransfer;
  dt.setData('text/plain', 'Data to Drag');
  dt.setDragImage(canvas, 25, 25);
}
</pre>

<p>Cette technique est utile pour dessiner des images filigranes personnalisées en utilisant l'élément canvas.</p>

<p>Les deuxième et troisième arguments de la méthode <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#setDragImage">setDragImage</a> sont les décalages de l'image par rapport au pointeur de la souris. Dans cet exemple, comme le canvas fait 50 pixels de large et 50 pixels de haut, nous utilisons son centre (soit 25 et 25) pour que l'image soit centrée sur le pointeur de la souris.</p>

<h2 id="drageffects">Effets du glissement</h2>

<p>Lors d'un glisser/déposer, plusieur opérations se déroulent. L'opération <code>copy</code> indique que la donnée glissée sera copiée de son emplacement d'origine au lieu de dépot. L'opération <code>move</code> indique que la donnée glissée sera déplacée, et l'opération <code>link</code> indique une forme de relation ou de connexion entre l'origine et le lieu de dépot.</p>

<p>Vous pouvez spécifier laquelle de ces trois opérations sera autorisée au niveau de l'origine du glissement, en définissant la propriété <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#effectAllowed">effectAllowed</a> dans un scrutateur d'événement <code>dragstart</code>.</p>

<pre>event.dataTransfer.effectAllowed = "copy";
</pre>

<p>Dans cet exemple, seule une copie n'est autorisée. Vous pouvez combiner les valeurs de plusieurs façons :</p>

<dl>
 <dt>none</dt>
 <dd>Aucune opération permise</dd>
 <dt>copy</dt>
 <dd>Copie uniquement</dd>
 <dt>move</dt>
 <dd>Déplacement uniquement</dd>
 <dt>link</dt>
 <dd>Lien uniquement</dd>
 <dt>copyMove</dt>
 <dd>Copie ou déplacement uniquement</dd>
 <dt>copyLink</dt>
 <dd>Copie ou lien uniquement</dd>
 <dt>linkMove</dt>
 <dd>Lien ou déplacement uniquement</dd>
 <dt>all</dt>
 <dd>Copie, déplacement ou lien</dd>
</dl>

<p>Notez que ces valeurs doivent être écrites exactement comme cela. Si vous ne modifiez pas la propriété <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#effectAllowed">effectAllowed</a>, alors tous les opérations seront permises comme pour la valeur 'all'. L'usage de cette propriété intervient seulement si vous souhaitez exclure des types spécifiques.</p>

<p>Pendant une opération de glissement, un scrutateur pour les événements <code>dragenter</code> ou <code>dragover</code> peut tester la propriété <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#effectAllowed">effectAllowed</a> afin de voir quelles opérations sont autorisées. La propriété associée <a href="/Fr/GlisserD%C3%A9pose/DataTransfer#dropEffect">dropEffect</a> doit être définie dans un de ces événements pour spécifier ce que chaque opération aura à faire. Les valeurs valides pour <a href="/Fr/GlisserD%C3%A9pose/DataTransfer#dropEffect">dropEffect</a> sont <code>none</code>, <code>copy</code>, <code>move</code> ou <code>link</code>. Il n'y a pas de combinaison pour cette propriété.</p>

<p>Pour les événements <code>dragenter</code> et <code>dragover</code>, la propriété <a href="/Fr/GlisserD%C3%A9pose/DataTransfer#dropEffect">dropEffect</a> est initialisée avec l'effet attendu par l'utilisateur. L'utilisateur peut modifier l'effet désiré en appuyant sur une touche de modification. Bien que les touches varient selon la plateforme, habituellement, il s'agit d'une combinaison des touches Maj et Control qui permettent de copier, déplacer et créer un raccourci. Le pointeur de la souris change de forme pour montrer l'opération souhaitée, par exemple un signe + à côté de la souris pour une copie.</p>

<p>Vous pouvez modifier les propriétés <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#effectAllowed">effectAllowed</a> et <a href="/Fr/GlisserD%C3%A9pose/DataTransfer#dropEffect">dropEffect</a> pendant les événements <code>dragenter</code> ou <code>dragover</code>, si par exemple une cible ne supporte qu'un seul type d'opération. La modification de la propriété <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#effectAllowed">effectAllowed</a> vous permet de spécifier les opérations autorisées sur une cible donnée. Par exemple, mettre une propriété <code>copyMove</code> permet des opération de copie ou de déplacement, mais pas de créer un lien raccourci.</p>

<p>Vous pouvez modifier la propriété <a href="/Fr/GlisserD%C3%A9pose/DataTransfer#dropEffect">dropEffect</a> en remplaçant l'effet de l'utilisateur, et forcer à obtenir une opération spécifique. Notez que cet effet doit être un de ceux listé dans la propriété <a href="/Fr/GlisserD%C3%A9poser/DataTransfer#effectAllowed">effectAllowed</a>, sinon une valeur alternative sera attribuée.</p>

<pre>event.dataTransfer.effectAllowed = "copyMove";
event.dataTransfer.dropEffect = "copy";
</pre>

<p>Dans cet exemple, la copie est l'effet proposé qui est inclus dans la liste des effets autorisés.</p>

<p>Vous pouvez utiliser la valeur <code>none</code> pour interdir tout dépôt à cet emplacement.</p>

<h2 id="droptargets">Spécifier les cibles de dépôt</h2>

<p>Un scrutateur pour les événements <code>dragenter</code> et <code>dragover</code> est utilisé pour indiquer des cibles de dépôt valides, c'est-à-dire là où les items pourront être déposés. La plupart des zones d'une page Web ne sont pas des endroits valides pour déposer des données. Ainsi, le comportement par défaut pour ces événements ne permet pas un dépôt.</p>

<p>Si vous voulez autoriser un dépôt, vous devez empêcher le comportement par défaut en annulant l'événement. Il suffit soit de retourner <code>false</code> à partir d'un scrutateur d'événement, ou par l'appel de la méthode événementielle <a href="/fr/DOM/event.preventDefault">event.preventDefault</a>. Cette dernière solution est plus faisable avec une fonction définie dans un script séparé.</p>

<pre>&lt;div ondragover="return false"&gt;
&lt;div ondragover="event.preventDefault()"&gt;
</pre>

<p>L'appel de la méthode <a href="/fr/DOM/event.preventDefault">event.preventDefault</a> pendant les événements <code>dragenter</code> et <code>dragover</code> indiquera qu'un dépôt est permis à cet endroit. Toutefois, il est fréquent d'appeler la méthode <a href="/fr/DOM/event.preventDefault">event.preventDefault</a> seulement dans certaines situations, par exemple si un lien est en train d'être glissé. Pour cela, appelez une fonction qui testera une condition et annulera l'événement seulement si cette condition est rencontrée. Dans le cas contraire, il suffit de ne pas annuler l'événement et aucun dépôt ne se réalisera si l'utilisateur lache le bouton de la souris.</p>

<p>Il est plus fréquent d'accepter ou non un dépôt en fonction du type de la donnée glissée. Par exemple, permettre les images ou les liens, ou bien les deux. Pour cela, testez les <a href="/fr/GlisserD%C3%A9poser/DataTransfer#types">types</a> de l'objet <code>dataTransfer</code>. Les types sont sous la forme d'une liste de chaînes de caractères ajoutées au début du glissement, du plus signifiant au moins signifiant.</p>

<pre>function doDragOver(event)
{
  var isLink = event.dataTransfer.types.contains("text/uri-list");
  if (isLink)
    event.preventDefault();
}
</pre>

<p>Dans cet exemple, la méthode <code>contains</code> est utilisée pour vérifier si le type <a href="/fr/GlisserD%C3%A9poser/Types_de_glissement_recommand%C3%A9s#link">text/uri-list</a> est présent dans la liste des types. S'il l'est, l'événement est annulé, ce qui autorise un dépôt. Si la donnée ne contient pas un lien, l'événement ne sera pas annulé et le dépôt ne sera pas autorisé à cet endroit.</p>

<p>Vous pouvez également définir une propriété <a href="/fr/GlisserD%C3%A9poser/DataTransfer#effectAllowed">effectAllowed</a> ou <a href="/fr/GlisserD%C3%A9poser/DataTransfer#dropEffect">dropEffect</a> ou les deux à la fois si vous souhaitez être plus précis sur le type d'opération autorisé. Naturellement, le changement de propriété n'aura aucun effet si vous n'avez pas annulé l'événement.</p>

<h2 id="dropfeedback">Retour d'information du dépôt</h2>

<p>Il y a de nombreuses manières d'indiquer à l'utilisateur que le dépot est autorisé dans une certaine zone. Le pointeur de la souris va être mis à jour en fonction de la valeur de la propriété <a href="/En/DragDrop/DataTransfer#dropEffect.28.29">dropEffect</a>. L'apparence exacte dépend de la plateforme de l'utilisateur, généralement il s'agit d'un icone représentant un signe plus qui apparaît pour une copie par exemple, et un 'impossible de déposer ici' peut apparaître quand le dépôt n'est pas autorisé. Cette information contextuelle est suffisante dans la plupart des cas.</p>

<p>De plus, vous pouvez aussi mettre à jour l'interface utilisateur en surlignant au besoin. Pour un simple surlignage, vous pouvez utiliser la pseudo-classe <code>-moz-drag-over</code>sur la cible du dépôt.</p>

<pre>.droparea:-moz-drag-over {
  border: 1px solid black;
}
</pre>

<p>Dans cet example, l'élement comportant la classe <code>droparea</code> va recevoir un bord noir de un pixel tant que la cible sera valide, ce qui est le cas, si la méthode <a href="/en/DOM/event.preventDefault">event.preventDefault</a> est appelé durant l'évenement <code>dragenter</code>. Il est à noter que vous devez annuler l'évenement <code>dragenter</code> de cette pseudo-classe tant que l'état n'est pas verifié par l'évenement <code>dragover</code>.</p>

<p>For more complex visual effects, you can also perform other operations during the <code>dragenter</code> event, for example, by inserting an element at the location where the drop will occur. For example, this might be an insertion marker or an element that represents the dragged element in its new location. To do this, you could create an <a href="/en/XUL/image">image</a> or <a href="/en/XUL/separator">separator</a> element for example, and simply insert it into the document during the <code>dragenter</code> event.</p>

<p>The <code>dragover</code> event will fire at the element the mouse is pointing at. Naturally, you may need to move the insertion marker around a <code>dragover</code> event as well. You can use the event's <a href="/en/DOM/event.clientX">clientX</a> and <a href="/en/DOM/event.clientY">clientY</a> properties as with other mouse events to determine the location of the mouse pointer.</p>

<p>Finally, the <code>dragleave</code> event will fire at an element when the drag leaves the element. This is the time when you should remove any insertion markers or highlighting. You do not need to cancel this event. Any highlighting or other visual effects specified using the <code>-moz-drag-over</code> pseudoclass will be removed automatically. The <code>dragleave</code> event will always fire, even if the drag is cancelled, so you can always ensure that any insertion point cleanup can be done during this event.</p>

<h2 id="drop">Performing a Drop</h2>

<p>When the user releases the mouse, the drag and drop operation ends. If the mouse was released over an element that is a valid drop target, that is, one that cancelled the last <code>dragenter</code> or <code>dragover</code> event, then the drop will be successful, and a <code>drop</code> event will fire at the target. Otherwise, the drag operation is cancelled and no <code>drop</code> event is fired.</p>

<p>During the <code>drop</code> event, you should retrieve that data that was dropped from the event and insert it at the drop location. You can use the <a href="/En/DragDrop/DataTransfer#dropEffect.28.29">dropEffect</a> property to determine which drag operation was desired.</p>

<p>As with all drag related events, the event's <code>dataTransfer</code> property will hold the data that is being dragged. The <a href="/En/DragDrop/DataTransfer#getData.28.29">getData</a> method may be used to retrieve the data again.</p>

<pre>function onDrop(event)
{
  var data = event.dataTransfer.getData("text/plain");
  event.target.textContent = data;
  event.preventDefault();
}
</pre>

<p>The <a href="/En/DragDrop/DataTransfer#getData.28.29">getData</a> method takes one argument, the type of data to retrieve. It will return the string value that was set when the <a href="/En/DragDrop/DataTransfer#setData.28.29">setData</a> was called at the beginning of the drag operation. An empty string will be returned if data of that type does not exist. Naturally though, you would likely know that the right type of data was available, as it was previously checked during a <code>dragover</code> event.</p>

<p>In the example here, once we have retrieved the data, we insert the string as the textual content of the target. This has the effect of inserting the dragged text where it was dropped, assuming that the drop target is an area of text such as a <code>p</code> or <code>div</code> element.</p>

<p>In a web page, you should call the <a href="/en/DOM/event.preventDefault">preventDefault</a> method of the event if you have accepted the drop so that the default browser handling does not handle the droppped data as well. For example, when a link is dragged to a web page, Firefox will open the link. By cancelling the event, this behaviour will be prevented.</p>

<p>You can retrieve other types of data as well. If the data is a link, it should have the type <a href="/En/DragDrop/Recommended_Drag_Types#link">text/uri-list</a>. You could then insert a link into the content.</p>

<pre>function doDrop(event)
{
  var links = event.dataTransfer.getData("text/uri-list").split("\n");
  for each (var link in links) {
    if (link.indexOf("#") == 0)
      continue;

    var newlink = document.createElement("a");
    newlink.href = link;
    newlink.textContent = link;
    event.target.appendChild(newlink);
  }
  event.preventDefault();
}
</pre>

<p>This example inserts a link from the dragged data. As you might be able to guess from the name, the <a href="/En/DragDrop/Recommended_Drag_Types#link">text/uri-list</a> type actually may contain a list of URLs, each on a separate line. In this code, we use the <a href="/en/Core_JavaScript_1.5_Reference/Global_Objects/String/split">split</a> to split the string into lines, then iterate over the list of lines, inserting each as a link into the document. Note also that we skip links starting with a number sign (#) as these are comments.</p>

<p>For simple cases, you can use the special type <code>URL</code> to just retrieve the first valid URL in the list. For example:</p>

<pre>var link = event.dataTransfer.getData("URL");
</pre>

<p>This eliminates the need to check for comments or iterate through lines yourself, however it is limited to only the first URL in the list.</p>

<p>The <code>URL</code> type is a special type used only as a shorthand, and it does not appear within the list of types specified in the <a href="/En/DragDrop/DataTransfer#types.28.29">types</a> property.</p>

<p>Sometimes you may support a number of different formats, and you want to retrieve the data that is most specific that is supported. In this example, three formats are support by a drop target.</p>

<p>The following example returns the data associated with the best supported format:</p>

<pre>function doDrop(event)
{
  var types = event.dataTransfer.types;
  var supportedTypes = ["application/x-moz-file", "text/uri-list", "text/plain"];
  types = supportedTypes.filter(function (value) types.contains(value));
  if (types.length)
    var data = event.dataTransfer.getData(types[0]);
  event.preventDefault();
}
</pre>

<p>This method relies on JavaScript functionality available in Firefox 3. However the code could be adjusted to support other platforms.</p>

<h2 id="dragend">Finishing a Drag</h2>

<p>Once the drag is complete, a <code>dragend</code> is fired at the source of the drag (the same element that received the <code>dragstart</code> event). This event will fire if the drag was successful or if it was cancelled. However, you can use the <a href="/En/DragDrop/DataTransfer#dropEffect.28.29">dropEffect</a> to determine what drop operation occurred.</p>

<p>If the <a href="/En/DragDrop/DataTransfer#dropEffect.28.29">dropEffect</a> property has the value <code>none</code> during a <code>dragend</code>, then the drag was cancelled. Otherwise, the effect specifies which operation was performed. The source can use this information after a move operation to remove the dragged item from the old location. The <a href="/En/DragDrop/DataTransfer#mozUserCancelled.28.29">mozUserCancelled</a> property will be set to true if the user cancelled the drag (by pressing Escape), and false if the drag was cancelled for other reasons such as an invalid drop target, or if was successful.</p>

<p>A drop can occur inside the same window or over another application. The <code>dragend</code> event will always fire regardless. The event's <a href="/en/DOM/event.screenX">screenX</a> and <a href="/en/DOM/event.screenY">screenY</a> properties will be set to the screen coordinate where the drop occurred.</p>

<p>After the <code>dragend</code> event has finished propagating, the drag and drop operation is complete.</p>
