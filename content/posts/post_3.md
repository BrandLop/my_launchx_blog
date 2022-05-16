---
title: "Métodos HTTP"
date: 2022-05-15
description: 'Explicación de métodos de petición HTTP'
---
<div align="center">
    <img src="../../docs/images/http_design.png" width="700">
</div>

## Introducción

Cuando estamos navegando en internet, al momento de querer visitar cualquier sitio web, se genera una comunicación entre nuestro navegador web (chrome, firefox, safari, edge, etc) y un servidor web, esto, con ayuda del protocolo (_Hypertext Transfer Protocol_) que se encarga de administrar las peticiones (request en ingles) y respuestas (response en ingles) que proporciona el servidor web.

## Métodos de petición HTTP

HTTP tiene predefinidos un conjunto de métodos de petición, son solicitudes que se realizan para efectuar una determinada acción en un recurso en concreto, como acceder a una pagina web, enviar datos de un formulario, consultar un API, etc.

### GET

El método `GET`  solicita una representación de un recurso específico, con un formato especifico: HTML, JSON, imágenes, etc. Las peticiones que usan el método GET sólo deben recuperar datos. Se pueden utilizar para consultar datos de una base de datos.

### POST

El método `POST` se utiliza para enviar datos al servidor por medio del `body`, el tipo de body de solicitud se define en la cabecera `Content-Type`, esta orientado a crear un nuevo recurso y el servidor procese la información recibida.

### PUT

Es similar al metodo `POST`, la principal diferencia entre ambos es que `PUT` actualiza recursos existentes en el servidor y `POST` crea un nuevos recursos cada vez que se ejecuta.

### DELETE

El método `DELETE` permite borrar un recurso en específico.

## 📕 Referencias

1. [Developer Mozilla](https://developer.mozilla.org/es/docs/Web/HTTP/Methods)