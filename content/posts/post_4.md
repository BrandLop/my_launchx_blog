---
title: "Códigos de Estado HTTP"
date: 2022-05-16
description: 'Una guia de los códigos de estado de respuesta HTTP'
---

![image](https://user-images.githubusercontent.com/94416443/168721828-9a0abfe3-85f1-47de-afd1-08aa1971c5ce.png)

## Introducción

Este post es una continuación del contenido abordado en el post de [Métodos HTTP](https://brandlop.github.io/my_launchx_blog/posts/post_3/), en esta ocasión describiremos en que consisten los códigos HTTP, que básicamente, representan mensajes del servidor que permiten conocer cómo fueron las cosas cuando se recibe una petición de un cliente, como desarrollador web son una herramienta fundamental para diagnosticar y arreglar errores de configuración.

## Códigos de estado de respuesta HTTP

Los códigos de estado de respuesta HTTP indican si se ha completado satisfactoriamente una petición HTTP específica. Se dividen en 5 tipos, ya que son respuestas que tienen significados similares, conocer que representan puede ayudar a saber que esta ocurriendo cuando, por ejemplo estamos generando un API.

Los 5 tipos representan:

- Respuestas informativas (1XX)
- Respuestas satisfactorias (2XX)
- Redirecciones (3XX)
- Errores de los clientes (4XX)
- Errores de los servidores (5XX)

### Respuestas informativas

Un código de estado de tipo 1XX te dice que la solicitud que has hecho al servidor sigue en curso por alguna razón.

- **100 Continue:** Es una respuesta provisional que indica que todo hasta ahora está bien y que el cliente debe continuar con la solicitud o ignorarla si ya está terminada.
- **101 Switching Protocol:**
Este código se envía en respuesta a un encabezado de solicitud `Upgrade` por el cliente e indica que el servidor acepta el cambio de protocolo propuesto por el navegador web.
- **102 Processing:**
Este código indica que el servidor ha recibido la solicitud y aún se encuentra procesándose, por lo que no hay respuesta disponible.
- **103 Early Hints:**
Este código de estado está pensado principalmente para ser usado con el encabezado `Link`, permitiendo que el navegador web empiece a pre-cargar recursos mientras el servidor prepara una respuesta.

### Respuestas satisfactorias

Una respuesta de tipo 2XX significa que todo funciona exactamente como se esperaba.

- **200 OK:**
La solicitud ha tenido éxito. Este es el código que se recibe cuando un recurso actúa como se esperaba.
- **201 Created:**
La solicitud ha tenido éxito y se ha creado un nuevo recurso como resultado de ello. Ésta es típicamente la respuesta enviada después de una petición PUT.
- **202 Accepted:**
La solicitud se ha recibido, pero aún se esta procesando. La solicitud puede, en última instancia, dar lugar o no a una respuesta completa. Está pensado para los casos en que otro proceso o servidor maneja la solicitud, o para el procesamiento por lotes.
- **203 Non-Authoritative Information:**
La petición se ha completado con éxito, pero su contenido no se ha obtenido de la fuente originalmente solicitada, sino que se recoge de una copia local o de un tercero. Excepto esta condición, se debe preferir una respuesta de 200 OK en lugar de esta respuesta.
- **204 No Content:**
La petición se ha completado con éxito pero su respuesta no tiene ningún contenido, aunque los encabezados pueden ser útiles.
- **205 Reset Content:**
Contiene lo de un código 204 y además, el navegador web tiene que inicializar la vista desde la que se realizó la petición, este código es útil por ejemplo para páginas con formularios cuyo contenido debe borrarse después de que el usuario lo envíe.
- **206 Partial Content:**
La petición servirá parcialmente el contenido solicitado. Esta característica es utilizada por herramientas de descarga como wget para continuar la transferencia de descargas anteriormente interrumpidas, o para dividir una descarga y procesar las partes simultáneamente.

### Redirecciones

Un código de estado de tipo 3XX es el proceso utilizado para comunicar que un recurso ha sido trasladado a una nueva ubicación.

- **300 Multiple Choice:**
A veces, puede haber múltiples recursos posibles con los que el servidor puede responder para cumplir con la solicitud de su navegador. Un código de estado 300 significa que tu navegador ahora tiene que elegir entre ellos. Esto puede ocurrir cuando hay múltiples extensiones de tipo de archivo disponibles.
- **301 Moved Permanently:**
Este código se entrega cuando una página web o un recurso ha sido reemplazado permanentemente por un recurso diferente. Se utiliza para la redirección permanente del URL.
- **302 Found:**
Este código de respuesta significa que el recurso de la URL solicitada ha sido cambiado temporalmente. Se utiliza para la redirección temporal de la URL.
- **303 See Other:**
El servidor envía esta respuesta para dirigir al cliente a un nuevo recurso solicitado a otra dirección usando una petición GET.
- **304 Not Modified:**
Este código le dice al navegador que los recursos almacenados en la caché del navegador no han cambiado. Se usa para acelerar la carga de páginas web reutilizando los recursos descargados previamente.
- **307 Temporary Redirect:**
El servidor envía esta respuesta para dirigir al cliente a obtener el recurso solicitado a otra URL con el mismo método que se usó la petición anterior. Tiene la misma semántica que el código de respuesta HTTP `302 Found`, con la excepción de que el navegador web no puede cambiar el método HTTP usado.
- **308 Permanent Redirect:**
Significa que el recurso ahora se encuentra permanentemente en otra URL, tiene la misma semántica que el código de respuesta HTTP `301 Moved Permanently`, con la excepción de que el navegador web no debe cambiar el método HTTP usado.

### Errores de los clientes

En el nivel 400, los códigos de estado HTTP, son códigos de error que especifican que hay un fallo en el navegador web y/o en la petición.

- **400 Bad Request:**
Esta respuesta significa que el servidor no pudo interpretar la solicitud dada una sintaxis inválida.
- **401 Unauthorized:**
Es necesario autenticar para obtener la respuesta solicitada. Esta es similar a 403, pero en este caso, la autenticación es posible.
- **403 Forbidden:**
El cliente no posee los permisos necesarios para cierto contenido, por lo que el servidor está rechazando otorgar una respuesta apropiada.
- **404 Not Found:**
El servidor no pudo encontrar el contenido solicitado. Este código de respuesta es uno de los más famosos dada su alta ocurrencia en la web.
- **405 Method Not Allowed:**
El método solicitado es conocido por el servidor pero ha sido deshabilitado y no puede ser utilizado. Los dos métodos obligatorios, GET y HEAD, nunca deben ser deshabilitados y no deberían retornar este código de error.
- **406 Not Acceptable:**
El recurso solicitado es capaz de generar sólo contenido que no es aceptable según los encabezados de aceptación enviados en la petición.
- **407 Proxy Authentication Required :**
Esto es similar al código 401, pero la autenticación debe estar hecha a partir de un proxy.
- **408 Request Timeout:**
Esta respuesta es enviada cuando el servidor no recibió la solicitud completa que fue enviada por el navegador web. Una posible causa podría ser la saturación de la red, lo que provoca la pérdida de paquetes de datos entre el navegador y el servidor.
- **409 Conflict:**
Esta respuesta puede ser enviada cuando una petición tiene conflicto con el estado actual del servidor.
- **410 Gone:**
Esta respuesta puede ser enviada cuando el contenido solicitado ha sido borrado del servidor.
- **414 URI Too Long:**
La URL solicitada por el cliente es más larga de lo que el servidor está dispuesto a interpretar.
- **415 Unsupported Media Type:**
El formato multimedia de los datos solicitados no está soportado por el servidor, por lo cual el servidor rechaza la solicitud.
- **417 Expectation Failed:**
Significa que la expectativa indicada por el campo de encabezado Expect solicitada no puede ser cumplida por el servidor.
- **418 I'm a teapot:**
El servidor se rehúsa a intentar hacer café con una tetera. Este código fue parte del April Fools' Day de 1998 😂

### Errores de los servidores

En el nivel 500, los códigos de estado HTTP, son códigos de error que especifican que hay un fallo en el servidor web.

- **500 Internal Server Error:**
El servidor ha encontrado una situación que no sabe cómo manejarla.
- **501 Not Implemented:**
El método solicitado no está soportado por el servidor y no puede ser manejado. Los únicos métodos que los servidores requieren soporte (y por lo tanto no deben retornar este código) son `GET` y `HEAD`.
- **502 Bad Gateway:**
Esta respuesta de error significa que el servidor, mientras trabaja como gateway para obtener una respuesta necesaria para manejar la petición, obtuvo una respuesta inválida.
- **503 Service Unavailable:**
La solicitud no puede ser completada en este momento. Este respuesta de error puede ser devuelta por un servidor sobrecargado que no puede manejar solicitudes adicionales.
- **504 Gateway Timeout:**
Esta respuesta de error es dada cuando el servidor está actuando como una puerta de enlace y no puede obtener una respuesta a tiempo.
- **508 Loop Detected :**
El servidor detectó un ciclo infinito mientras procesaba la solicitud.

## 📕 Referencias

1. [Developer Mozilla](https://developer.mozilla.org/es/docs/Web/HTTP/Status)
2. [Una guía completa y una lista de códigos de estado HTTP](https://kinsta.com/es/blog/codigos-de-estado-de-http/)
