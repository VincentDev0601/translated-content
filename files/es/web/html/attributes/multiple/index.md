---
title: 'HTML el atributo: multiple'
slug: Web/HTML/Attributes/multiple
tags:
  - Atributos
  - Resticción de validación
  - atributo
translation_of: Web/HTML/Attributes/multiple
original_slug: Web/HTML/Atributos/multiple
---
<p>El atributo booleano {{HTMLAttrxRef("multiple", "input")}}, si se establece, significa que el control del formulario acepta uno o más valores. Válido para los {{HTMLElement("input")}}s de tipo {{HTMLElement("input/email", "email")}}, {{HTMLElement("input/file", "file")}} y {{HTMLElement("select")}}, la forma en que el usuario opta por valores múltiples depende del control del formulario.</p>

<p>Dependiendo del tipo, el control de formulario puede tener una apariencia diferente si se establece el atributo {{HTMLAttrxRef("multiple", "input")}}. Para el {{HTMLElement("input")}} de tipo <code>file</code>, la mensajería nativa que proporciona el navegador es diferente. En Firefox, el {{HTMLElement("input")}} de tipo <code>file</code> dice "Ningún archivo seleccionado" cuando el atributo está presente y "Ningún archivo seleccionado", cuando no hay archivo seleccionado. La mayoría de los navegadores muestran un cuadro de lista de desplazamiento para un control {{HTMLElement("select")}} con el atributo {{HTMLAttrxRef("multiple", "input")}} establecido frente a un menú desplegable de una sola línea cuando se omite el atributo. El {{HTMLElement("input")}} {{HTMLElement("input/email", "email")}} muestra lo mismo, pero coincidirá con la pseudoclase {{CSSxRef(':invalid')}} si hay más de una dirección de correo electrónico separada por comas incluido si el atributo no está presente.</p>

<p>Cuando se establece {{HTMLAttrxRef("multiple", "input")}} en el tipo de entrada {{HTMLElement("input/email", "email")}}, el usuario puede incluir cero (si no es {{web.link("/es/docs/Web/HTML/Attributes/required", "required")}} también), una o más direcciones de correo electrónico separadas por comas.</p>

<pre class="brush: html notranslate"><code class="brush: html">&lt;input type="email" <strong>multiple</strong> name="emails" id="emails"&gt;</code></pre>

<p>Si y solo si se especifica el atributo {{HTMLAttrxRef("multiple", "input")}}, el valor puede ser una lista de direcciones de correo electrónico separadas por comas y formadas correctamente. Los espacios en blanco iniciales y finales se eliminan de cada dirección de la lista.</p>

<p>Cuando se establece {{HTMLAttrxRef("multiple", "input")}} en el tipo de entrada {{HTMLElement("input/file", "file")}}, el usuario puede seleccionar uno o más archivos. El usuario puede elegir varios archivos del selector de archivos de cualquier manera que la plataforma elegida lo permita (por ejemplo, manteniendo presionada la tecla <kbd>Mayús</kbd> o <kbd>Control</kbd> y luego haciendo clic).</p>

<pre class="brush: html notranslate"><code class="brush: html">&lt;input type="file" <strong>multiple</strong> name="uploads" id="uploads"&gt;</code></pre>

<p>Cuando se omite el atributo, el usuario solo puede seleccionar un único archivo por {{HTMLElement("input")}}.</p>

<p>El atributo {{HTMLAttrxRef("multiple", "input")}} en el elemento {{HTMLElement("select")}} representa un control para seleccionar cero o más opciones de la lista. De lo contrario, el elemento {{HTMLElement("select")}} representa un control para seleccionar una única {{HTMLElement("option")}} de la lista de opciones.</p>

<pre class="brush: html notranslate">&lt;select multiple name="drawfs" id="drawfs"&gt;
  &lt;option&gt;Gruñón&lt;/option&gt;
  &lt;option&gt;Feliz&lt;/option&gt;
  &lt;option&gt;Dormilón&lt;/option&gt;
  &lt;option&gt;Tímido&lt;/option&gt;
  &lt;option&gt;Estornudo&lt;/option&gt;
  &lt;option&gt;Tontín&lt;/option&gt;
  &lt;option&gt;Doc&lt;/option&gt;
&lt;/select&gt;</pre>

<p>Cuando se especifica {{HTMLAttrxRef("multiple", "input")}}, la mayoría de los navegadores mostrarán un cuadro de lista de desplazamiento en lugar de un menú desplegable de una sola línea.</p>

<h2 id="Ejemplos">Ejemplos</h2>

<h3 id="input_para_correoᵉ"><code>input</code> para correoᵉ</h3>

<pre class="brush: html notranslate">&lt;label for="emails"&gt;¿A quién deseas enviar un correo electrónico?&lt;/label&gt;
&lt;input type="email" multiple name="emails" id="emails" list="drawfemails" required size="64"&gt;

&lt;datalist id="drawfemails"&gt;
  &lt;option value="gruñón@woodworkers.com"&gt;Gruñón&lt;/option&gt;
  &lt;option value="feliz@woodworkers.com"&gt;Feliz&lt;/option&gt;
  &lt;option value="dormilón@woodworkers.com"&gt;Dormilón&lt;/option&gt;
  &lt;option value="tímido@woodworkers.com"&gt;Tímido&lt;/option&gt;
  &lt;option value="estornudo@woodworkers.com"&gt;Estornudo&lt;/option&gt;
  &lt;option value="tontín@woodworkers.com"&gt;Tontín&lt;/option&gt;
  &lt;option value="doc@woodworkers.com"&gt;Doc&lt;/option&gt;
&lt;/datalist&gt;</pre>

<div class="hidden">
<pre class="brush: css notranslate">input:invalid {border: red solid 3px;}</pre>
</div>

<p>Si y solo si se especifica el atributo {{HTMLAttrxRef("multiple", "input")}}, el valor puede ser una lista de direcciones de correo electrónico separadas por comas y formadas correctamente. Los espacios en blanco iniciales y finales se eliminan de cada dirección de la lista. Si el atributo {{web.link("/es/docs/Web/HTML/Attributes/required", "required")}} está presente, se requiere al menos una dirección de correo electrónico.</p>

<p>Algunos navegadores admiten la aparición de la {{web.link("/es/docs/Web/HTML/Attributes/list", "lista")}} de opciones del {{HTMLElement('datalist')}} para direcciones de correo electrónico posteriores cuando haya varias. Otros no lo hacen.</p>

<p>{{EmbedLiveSample("input_para_correoᵉ", 600, 80) }}</p>

<h3 id="input_de_tipo_file"><code>input</code> de tipo <code>file</code></h3>

<p>Cuando se establece {{HTMLAttrxRef("multiple", "input")}} en el {{HTMLElement("input")}} de tipo  {{HTMLElement("input/file", "file")}}, el usuario puede seleccionar uno o más archivos:</p>

<pre class="brush: html notranslate">&lt;form method="post" enctype="multipart/form-data"&gt;
  &lt;p&gt;
    &lt;label for="uploads"&gt;
       Elige las imágenes que deseas cargar:
    &lt;/label&gt;
    &lt;input type="file" id="uploads" name="uploads" accept=".jpg, .jpeg, .png, .svg, .gif" multiple&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;label for="text"&gt;Elige un archivo de texto para cargar: &lt;/label&gt;
    &lt;input type="file" id="text" name="text" accept=".txt"&gt;
 &lt;/p&gt;
  &lt;p&gt;
    &lt;input type="submit" value="Enviar"&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<p>{{EmbedLiveSample("input_de_tipo_file", 600, 80) }}</p>

<p>Nota la diferencia en la apariencia entre el ejemplo con {{HTMLAttrxRef("multiple", "input")}} establecido y el otro {{HTMLElement("input")}} sin <code>file</code>.</p>

<p>Cuando se envía el formulario, utilizas el {{web.link("/es/docs/Web/HTML/Element/form", "method='get'")}} el nombre de cada archivo seleccionado se habría agregado a los parámetros de la URL como <code>?uploads=img1.jpg&amp;uploads=img2.svg</code>. Sin embargo, dado que estamos asumiendo datos de formularios de {{web.link("/es/docs/Web/API/XMLHttpRequest/multipart", "multipart")}}, usamos mucho el <code>post</code>. Consulta el elemento {{HTMLElement('form')}} y {{web.link("/es/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data#The_method_attribute", "envío de datos del formulario")}} para obtener más información.</p>

<h3 id="select"><code>select</code></h3>

<p>El atributo {{HTMLAttrxRef("multiple", "input")}} en el elemento {{HTMLElement("select")}} representa un control para seleccionar cero o más opciones de la lista. De lo contrario, el elemento {{HTMLElement("select")}} representa un control para seleccionar una única {{HTMLElement("option")}} de la lista de opciones. El control generalmente tiene una apariencia diferente en función de la presencia del atributo {{HTMLAttrxRef("multiple", "input")}}, y la mayoría de los navegadores muestran un cuadro de lista de desplazamiento en lugar de una lista desplegable de una sola línea cuando el atributo está presente.</p>

<pre class="brush: html notranslate">&lt;form method="get" action="#"&gt;
&lt;p&gt;
 &lt;label for="dwarfs"&gt;Selecciona los leñadores que te gusten:&lt;/label&gt;
  &lt;select multiple name="drawfs" id="drawfs"&gt;
    &lt;option&gt;gruñón@woodworkers.com&lt;/option&gt;
    &lt;option&gt;feliz@woodworkers.com&lt;/option&gt;
    &lt;option&gt;dormilón@woodworkers.com&lt;/option&gt;
    &lt;option&gt;tímido@woodworkers.com&lt;/option&gt;
    &lt;option&gt;estornudo@woodworkers.com&lt;/option&gt;
    &lt;option&gt;tontín@woodworkers.com&lt;/option&gt;
    &lt;option&gt;doc@woodworkers.com&lt;/option&gt;
  &lt;/select&gt;
&lt;/p&gt;
&lt;p&gt;
 &lt;label for="favoriteOnly"&gt;Selecciona tu favorito:&lt;/label&gt;
  &lt;select name="favoriteOnly" id="favoriteOnly"&gt;
    &lt;option&gt;gruñón@woodworkers.com&lt;/option&gt;
    &lt;option&gt;feliz@woodworkers.com&lt;/option&gt;
    &lt;option&gt;dormilón@woodworkers.com&lt;/option&gt;
    &lt;option&gt;tímido@woodworkers.com&lt;/option&gt;
    &lt;option&gt;estornudo@woodworkers.com&lt;/option&gt;
    &lt;option&gt;tontín@woodworkers.com&lt;/option&gt;
    &lt;option&gt;doc@woodworkers.com&lt;/option&gt;
  &lt;/select&gt;
&lt;/p&gt;
&lt;p&gt;
  &lt;input type="submit" value="Enviar"&gt;
&lt;/p&gt;
&lt;/form&gt;</pre>

<p>{{EmbedLiveSample("select", 600, 120) }}</p>

<p>Ten en cuenta la diferencia de apariencia entre los dos controles de formulario.</p>

<pre class="brush: css notranslate">/* descomenta este CSS para que el multiple tenga la misma altura que single */

/*
select[multiple] {
  height: 1.5em;
  vertical-align: top;
}
select[multiple]:focus,
select[multiple]:active {
  height: auto;
}
*/</pre>

<p>Hay varias formas de seleccionar varias opciones en un elemento <code>&lt;select&gt;</code> con un atributo {{HTMLAttrxRef("multiple", "input")}}. Dependiendo del sistema operativo, los usuarios del ratón pueden mantener presionadas las teclas <kbd>Ctrl</kbd>, <kbd>Comando</kbd> o <kbd>Mayús</kbd> y luego hacer clic en varias opciones para seleccionarlas o deseleccionarlas. Los usuarios de teclado pueden seleccionar varios elementos contiguos centrándose en el elemento <code>&lt;select&gt;</code>, seleccionando un elemento en la parte superior o inferior del rango que desean seleccionar usando <kbd>Arriba</kbd> y <kbd>Teclas del cursor hacia abajo</kbd> para subir y bajar las opciones. La selección de elementos no contiguos no es tan compatible: los elementos se deben poder seleccionar y deseleccionar presionando <kbd>Espacio</kbd>, pero el soporte varía entre los navegadores.</p>

<h2 id="Especificaciones">Especificaciones</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Especificación</th>
   <th scope="col">Estado</th>
   <th scope="col">Comentario</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('HTML WHATWG', 'input.html#attr-input-multiple', 'Atributo multiple')}}</td>
   <td>{{ Spec2('HTML WHATWG') }}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName('HTML5 W3C', 'input.html#attr-input-multiple', 'Atributo multiple')}}</td>
   <td>{{ Spec2('HTML5 W3C') }}</td>
   <td></td>
  </tr>
 </tbody>
</table>

<h2 id="Problemas_de_accesibilidad">Problemas de accesibilidad</h2>

<p>Proporciona instrucciones para ayudar a los usuarios a comprender cómo completar el formulario y utilizar controles de formulario individuales. Indica cualquier entrada requerida y opcional, formatos de datos y otra información relevante. Cuando utilices el atributo {{HTMLAttrxRef("multiple", "input")}}, informa al usuario que se permiten múltiples valores y proporciona instrucciones sobre cómo proveer más valores, como "direcciones de correo electrónico separadas con una coma".</p>

<p>Configurar {{web.link("/es/docs/Web/HTML/Attributes/size", "size")}}<code>="1"</code> en una selección múltiple puedes hacer que aparezca como una única selección en algunos navegadores, pero luego no se expande en el enfoque, lo que perjudica la usabilidad. No hagas eso. Si cambias la apariencia de un <code>select</code>, e incluso si no lo haces, asegúrate de informar al usuario que se puede seleccionar más de una opción mediante otro método.</p>

<h2 id="Ve_también">Ve también</h2>

<ul>
 <li>{{HTMLElement('input')}}</li>
 <li>{{htmlelement('select')}}</li>
 <li>{{web.link("/es/docs/Web/HTML/Element/input/email#Allowing_multiple_e-mail_addresses", "Permitir varias direcciones de correo electrónico")}}</li>
</ul>
