---
title: >-
  Cómo hacer que las PWAs se puedan volver a conectar usando Notificaciones y
  Push
slug: Web/Progressive_web_apps/Re-engageable_Notifications_Push
tags:
  - Notificaciones
  - PWAs
  - Push
  - aplicaciones web progresivas
  - js13kGames
  - progresiva
translation_of: Web/Progressive_web_apps/Re-engageable_Notifications_Push
---
<div>{{PreviousMenuNext("Web/Apps/Progressive/Installable_PWAs", "Web/Apps/Progressive/Loading", "Web/Apps/Progressive")}}</div>

<p class="summary">Tener la capacidad de almacenar en caché el contenido de una aplicación para que funcione sin conexión es una gran característica. Permitir que el usuario instale la aplicación web en su pantalla de inicio es aún mejor. Pero en lugar de depender solo de las acciones del usuario, podemos hacer más, utilizando mensajes <code>push</code> y notificaciones para volver a interactuar automáticamente y entregar contenido nuevo siempre que esté disponible.</p>

<h2 id="Dos_APIs_un_objetivo">Dos APIs, un objetivo</h2>

<p>{{web.link("/es/docs/Web/API/Push_API", "API Push")}} y {{web.link("/es/docs/Web/API/Notifications_API", "API de notificaciones")}} son dos APIs independientes, pero funcionan bien juntas cuando deseas proporcionar una funcionalidad atractiva en tu aplicación. <code>Push</code> se utiliza para entregar contenido nuevo desde el servidor a la aplicación sin ninguna intervención del lado del cliente, y su operación es manejada por el servicio <em>worker</em> de la aplicación. El servicio <em>worker</em> puede utilizar las notificaciones para mostrar nueva información al usuario, o al menos alertarlo cuando algo se haya actualizado.</p>

<p>Funcionan fuera de la ventana del navegador, al igual que el servicio <em>worker</em>, por lo que se pueden enviar actualizaciones y se pueden mostrar notificaciones cuando la página de la aplicación está desenfocada o incluso cerrada.</p>

<h2 id="Notificaciones">Notificaciones</h2>

<p>Comencemos con las notificaciones: pueden funcionar sin <code>push</code>, pero son muy útiles cuando se combinan con ellas. Para empezar, veámoslo de forma aislada.</p>

<h3 id="Pedir_permiso">Pedir permiso</h3>

<p>Para mostrar una notificación, primero debes solicitar permiso. Sin embargo, en lugar de mostrar la notificación de inmediato, la mejor práctica dicta que deberíamos mostrar la ventana emergente cuando el usuario la solicite haciendo clic en un botón:</p>

<pre class="brush: js notranslate">var button = document.getElementById("notifications");
button.addEventListener('click', function(e) {
    Notification.requestPermission().then(function(result) {
        if(result === 'granted') {
            randomNotification();
        }
    });
});</pre>

<p>Esto muestra una ventana emergente usando el propio servicio de notificaciones del sistema operativo:</p>

<p><img alt="Notificación de js13kPWA." src="https://mdn.mozillademos.org/files/15930/js13kpwa-notification.png" style="display: block; height: 640px; margin: 0px auto; width: 360px;"></p>

<p>Cuando el usuario confirma recibir notificaciones, la aplicación las puede mostrar. El resultado de la acción del usuario puede ser predeterminada, otorgada o denegada. La opción predeterminada se elige cuando el usuario no hace una elección, y las otras dos se establecen cuando el usuario hace clic en sí o no, respectivamente.</p>

<p>Cuando se acepta, el permiso funciona tanto para notificaciones como para <code>push</code>.</p>

<h3 id="Crea_una_notificación">Crea una notificación</h3>

<p>La aplicación de ejemplo crea una notificación a partir de los datos disponibles: se elige un juego al azar y el elegido alimenta la notificación con el contenido — establece el nombre del juego como título, menciona al autor en el cuerpo y muestra la imagen como un icono:</p>

<pre class="brush: js notranslate">function randomNotification() {
    var randomItem = Math.floor(Math.random()*games.length);
    var notifTitle = games[randomItem].name;
    var notifBody = 'Creado por '+games[randomItem].author+'.';
    var notifImg = 'data/img/'+games[randomItem].slug+'.jpg';
    var options = {
        body: notifBody,
        icon: notifImg
    }
    var notif = new Notification(notifTitle, options);
    setTimeout(randomNotification, 30000);
}</pre>

<p>Se crea una nueva notificación aleatoria cada 30 segundos hasta que se vuelve demasiado molesta y el usuario la desactiva. (En una aplicación real, las notificaciones deberían ser mucho menos frecuentes y más útiles). La ventaja de la API de notificaciones es que utiliza la funcionalidad de notificación del sistema operativo. Esto significa que las notificaciones se pueden mostrar al usuario incluso cuando no están mirando la aplicación web, y las notificaciones son similares a las que muestran las aplicaciones nativas.</p>

<h2 id="Push"><code>Push</code></h2>

<p><code>Push</code> es más complicado que las notificaciones: necesitamos suscribirnos a un servidor que luego enviará los datos a la aplicación. El servicio <em>worker</em> de la aplicación recibirá datos <code>push</code> del servidor, que luego se pueden mostrar usando el sistema de notificaciones u otro mecanismo si lo deseas.</p>

<p>La tecnología aún se encuentra en una etapa muy temprana; algunos ejemplos de uso utilizan la plataforma de mensajería en la nube de Google, pero se están reescribiendo para admitir <a href="#" title="https://blog.mozilla.org/services/2016/08/23/sending-vapid-protected-webpush-Notifications-via-mozillas-push-service/">IDVAP</a> (<strong>Id</strong>entificación <strong>vo</strong>luntaria de la <strong>ap</strong>licación), que ofrece una capa adicional de seguridad para tu aplicación. Puedes examinar los <a href="https://serviceworke.rs/push-payload.html">ejemplos del libro de recetas del servicio <em>workers</em></a>, intenta configurar un servidor de mensajería <code>push</code> usando <a href="https://firebase.google.com/">Firebase</a>, o crea tu propio servidor (utilizando Node.js, por ejemplo).</p>

<p>Como se mencionó anteriormente, para poder recibir mensajes <code>push</code>, debes tener un servicio <em>worker</em>, cuyos conceptos básicos ya se explican en {{web.link("/es/docs/Web/Apps/Progressive/Offline_Service_workers", "Cómo hacer que las PWAs funcionen sin conexión con el servicio workers")}}. Dentro del servicio <em>workers</em>, se crea un mecanismo de suscripción del servicio <code>push</code>.</p>

<pre class="brush: js notranslate">registration.pushManager.getSubscription() .then( /* ... */ );</pre>

<p>Una vez que el usuario está suscrito, puede recibir notificaciones automáticas del servidor.</p>

<p>Desde el lado del servidor, todo el proceso tiene que estar encriptado con claves públicas y privadas por razones de seguridad — permitir que todos envíen mensajes <code>push</code> sin seguridad usando tu aplicación sería una idea terrible. Consulta la <a href="https://jrconlin.github.io/WebPushDataTestPage/">página de prueba de encriptación de datos <code>Push</code> en la Web</a> para obtener información detallada sobre cómo proteger el servidor. El servidor almacena toda la información recibida cuando el usuario se suscribió, por lo que los mensajes se pueden enviar más tarde cuando sea necesario.</p>

<p>Para recibir mensajes <code>push</code>, podemos escuchar el evento {{event("push")}} en el archivo <code>Service Worker</code>:</p>

<pre class="brush: js notranslate">self.addEventListener('push', function(e) { /* ... */ });</pre>

<p>Los datos se pueden recuperar y luego mostrar como una notificación al usuario inmediatamente. Esto, por ejemplo, se puede usar para recordarle algo al usuario o para informarle sobre contenido nuevo disponible en la aplicación.</p>

<h3 id="Ejemplo_push">Ejemplo <code>push</code></h3>

<p><code>Push</code> necesita que la parte del servidor funcione, por lo que no podemos incluirla en el ejemplo js13kPWA alojado en las páginas de GitHub, ya que solo ofrece alojamiento de archivos estáticos. Todo se explica en el <a href="https://serviceworke.rs/">Libro de recetas para servicios <em>worker</em></a>; consulta el <a href="https://serviceworke.rs/push-payload.html">Demo de carga <code>push</code></a>.</p>

<p>Esta demostración consta de tres archivos:</p>

<ul>
 <li><a href="https://github.com/mozilla/serviceworker-cookbook/blob/master/push-payload/index.js">index.js</a>, que contiene el código fuente de nuestra aplicación</li>
 <li><a href="https://github.com/mozilla/serviceworker-cookbook/blob/master/push-payload/server.js">server.js</a>, que contiene la parte del servidor (escrito en Node.js)</li>
 <li><a href="https://github.com/mozilla/serviceworker-cookbook/blob/master/push-payload/service-worker.js">service-worker.js</a>, que contiene el código específico de <code>Service Worker</code>.</li>
</ul>

<p>Exploremos todos estos</p>

<h4 id="index.js"><code>index.js</code></h4>

<p>El archivo <code>index.js</code> comienza registrando el servicio <code>worker</code>:</p>

<pre class="brush: js notranslate">navigator.serviceWorker.register('service-worker.js')
.then(function(registration) {
  return registration.pushManager.getSubscription()
  .then(async function(subscription) {
      // parte de registro
  });
})
.then(function(subscription) {
    // parte de la suscripción
});</pre>

<p>Es un poco más complicado que el servicio <em>worker</em> que vimos en la <a href="https://mdn.github.io/pwa-examples/js13kpwa/">demostración de js13kPWA</a>. En este caso particular, después de registrarse, usamos el objeto de registro para suscribirnos y luego usamos el objeto de suscripción resultante para completar todo el proceso.</p>

<p>En la parte de registro, el código se ve así:</p>

<pre class="brush: js notranslate">if(subscription) {
    return subscription;
}</pre>

<p>Si el usuario ya se ha suscrito, devolvemos el objeto de suscripción y pasamos a la parte de suscripción. Si no, iniciamos una nueva suscripción:</p>

<pre class="brush: js notranslate">const response = await fetch('./vapidPublicKey');
const vapidPublicKey = await response.text();
const convertedVapidKey = urlBase64ToUint8Array(vapidPublicKey);</pre>

<p>La aplicación obtiene la clave pública del servidor y convierte la respuesta en texto; luego se debe convertir a un Uint8Array (para admitir Chrome). Para obtener más información sobre las claves <em>IDVAP</em>, puedes leer <a href="https://blog.mozilla.org/services/2016/08/23/sending-vapid-identified-webpush-notifications-via-mozillas-push-service/">Envío de notificaciones <em>WebPush</em> identificadas por <em>IDVAP</em> a través de la publicación de blog del servicio <code>Push</code> de Mozilla</a>.</p>

<p>La aplicación ahora puede usar {{DOMxRef("PushManager")}} para suscribir al nuevo usuario. Hay dos opciones pasadas al método {{DOMxRef("PushManager.subscribe()")}} — la primera es <code>userVisibleOnly: true</code>, lo cual significa que todas las notificaciones enviadas al usuario serán visibles para ellos, y el segundo es <code>applicationServerKey</code>, que contiene nuestra clave <em>IDVAP</em> adquirida y convertida con éxito.</p>

<pre class="brush: js notranslate">return registration.pushManager.subscribe({
    userVisibleOnly: true,
    applicationServerKey: convertedVapidKey
});</pre>

<p>Ahora pasemos a la parte de la suscripción: la aplicación primero envía los detalles de la suscripción como JSON al servidor mediante <code>Fetch</code>.</p>

<pre class="brush: js notranslate">fetch('./register', {
    method: 'post',
    headers: {
        'Content-type': 'application/json'
    },
    body: JSON.stringify({
        subscription: subscription
    }),
});</pre>

<p>Luego, se define la función {{DOMxRef("onclick", "GlobalEventHandlers.onclick")}} en el botón <em>Suscribirse</em>:</p>

<pre class="brush: js notranslate">document.getElementById('doIt').onclick = function() {
    const payload = document.getElementById('notification-payload').value;
    const delay = document.getElementById('notification-delay').value;
    const ttl = document.getElementById('notification-ttl').value;

    fetch('./sendNotification', {
        method: 'post',
        headers: {
            'Content-type': 'application/json'
        },
        body: JSON.stringify({
            subscription: subscription,
            payload: payload,
            delay: delay,
            ttl: ttl,
        }),
    });
};</pre>

<p>Cuando se hace clic en el botón, <code>fetch</code> solicita al servidor que envíe la notificación con los parámetros dados: <code>payload</code> es el texto que se mostrará en la notificación, <code>delay</code> define un retraso en segundos hasta que se muestra la notificación, y <code>ttl</code> es la configuración de tiempo de vida que mantiene la notificación disponible en el servidor durante un período de tiempo específico, también definido en segundos.</p>

<p>Ahora, en el siguiente archivo JavaScript.</p>

<h4 id="server.js"><code>server.js</code></h4>

<p>La parte del servidor está escrita en Node.js y se debe alojar en un lugar adecuado, que es un tema de un artículo completamente separado. Aquí solo proporcionaremos una descripción general de alto nivel.</p>

<p>El <a href="https://www.npmjs.com/package/web-push">módulo <code>web-push</code></a> se utiliza para configurar las claves <code>IDVAP</code> y, opcionalmente, generarlas si aún no están disponibles.</p>

<pre class="brush: js notranslate">const webPush = require('web-push');

if (!process.env.VAPID_PUBLIC_KEY || !process.env.VAPID_PRIVATE_KEY) {
  console.log("Debes configurar las variables de entorno VAPID_PUBLIC_KEY y " +
    "VAPID_PRIVATE_KEY. Puedes utilizar las siguientes: ");
  console.log(webPush.generateVAPIDKeys());
  return;
}

webPush.setVapidDetails(
  'https://serviceworke.rs/',
  process.env.VAPID_PUBLIC_KEY,
  process.env.VAPID_PRIVATE_KEY
);
</pre>

<p>A continuación, un módulo define y exporta todas las rutas que una aplicación necesita manejar: obtener la clave pública <em>IDVAP</em>, registrarse y luego enviar notificaciones. Puedes ver las variables del archivo <code>index.js</code> que se está utilizando: <code>payload</code>, <code>delay</code> y <code>ttl</code>.</p>

<pre class="brush: js notranslate">module.exports = function(app, route) {
  app.get(route + 'vapidPublicKey', function(req, res) {
    res.send(process.env.VAPID_PUBLIC_KEY);
  });

  app.post(route + 'register', function(req, res) {

    res.sendStatus(201);
  });

  app.post(route + 'sendNotification', function(req, res) {
    const subscription = req.body.subscription;
    const payload = req.body.payload;
    const options = {
      TTL: req.body.ttl
    };

    setTimeout(function() {
      webPush.sendNotification(subscription, payload, options)
      .then(function() {
        res.sendStatus(201);
      })
      .catch(function(error) {
        console.log(error);
        res.sendStatus(500);
      });
    }, req.body.delay * 1000);
  });
};</pre>

<h4 id="service-worker.js"><code>service-worker.js</code></h4>

<p>El último archivo que veremos es el del servicio <em>worker</em>:</p>

<pre class="brush: js notranslate">self.addEventListener('push', function(event) {
    const payload = event.data ? event.data.text() : 'no payload';
    event.waitUntil(
        self.registration.showNotification('ServiceWorker Cookbook', {
            body: payload,
        })
    );
});</pre>

<p>Todo lo que hace es agregar un escucha para el evento {{Event("push")}}, crear la variable de carga útil que consiste en el texto tomado de los datos (o crear una cadena para usar si los datos están vacíos), y luego esperar hasta la notificación se muestra al usuario.</p>

<p>No dudes en explorar el resto de los ejemplos en el <a href="https://serviceworke.rs/">Libro de recetas para el servicio <em>workers</em></a> si deseas saber cómo se manejan: el <a href="https://github.com/mozilla/serviceworker-cookbook/">código fuente completo está disponible en GitHub</a>. Hay una gran colección de ejemplos de uso que muestran el uso general, pero también la inserción web, las estrategias de almacenamiento en caché, el rendimiento, el trabajo sin conexión y más.</p>

<p>{{PreviousMenuNext("Web/Apps/Progressive/Installable_PWAs", "Web/Apps/Progressive/Loading", "Web/Apps/Progressive")}}</p>

<div>{{QuickLinksWithSubpages("/es/docs/Web/Progressive_web_apps/")}}</div>
