---
title: Guía para migrar a Google Analytics 4 (GA4)
description: 
layout: default_new
author: Emirodgar
lang: es_ES
sitemap: 1
feed: 1
date: 18/03/2022
folder: google-analytics
permalink: google-analytics

--- 

Google ha anunciado que [en julio de 2023, Google Analytics Universal dejará de funcionar](https://blog.google/products/marketingplatform/analytics/prepare-for-future-with-google-analytics-4/), y el único producto de analítica disponible será Google Analytics 4, comúnmente conocido como GA4.

GA4 fue lanzado en 2020 y, aunque sigue en beta, tenemos que comenzar a trabajar en la migración, ya que, aunque aún queda tiempo, la nueva plataforma utiliza un método disruptivo tanto en la medición como en la visualización de la información.

1. 
{:toc}

## Crear una propiedad GA4

El primer paso que tendremos que dar será crear una propiedad de GA4, puesto que las actuales corresponden a la versión que quedará obsoleta a partir del verano de 2023.

Se puede crear una nueva propiedad de GA4 en cualquier cuenta existente de Analytics. Al generarla, no mantendrá histórico, ya que empieza desde cero, por lo que es importante que convivan ambas propiedades (GA3 con histórico y GA4 con los datos recogidos a partir del momento de su creación).

Si accedemos a una cuenta de Analytics, veremos un mensaje en la parte superior con el siguiente texto:

> Universal Analytics dejará de procesar nuevos datos en propiedades estándar a partir del 1 de julio del 2023. Puede prepararse ya cambiando a una propiedad Google Analytics 4 y configurándola.

Justo al lado hay un botón que dice "Empezar". Hacemos clic sobre el mismo para comenzar el proceso de migración a una propiedad de GA4.

![Aviso Analytics migración a GA4](https://i.imgur.com/Znip5dj.png)

En la siguiente imagen recibimos un aviso tranquilizador en el que se nos indica que la propiedad Universal Analytics actual no se verá afectada. Podemos avanzar con tranquilidad.

Tenemos dos opciones, conectar a esta cuenta una propiedad GA4 ya existente, o crear una nueva. En este punto, pulsamos sobre el botón de "Cómo empezar" para crear nuestra propiedad de GA4.

![enter image description here](https://i.imgur.com/NuMJBfM.png)

Aparecerá una ventana emergente con más información acerca de los datos y configuraciones que se importarán desde GA3 a GA4 y con el botón de "Crear propiedad". Lo pulsamos y avanzamos al siguiente paso.

Si todo ha ido bien, recibiremos el aviso de que nuestra propiedad ha sido generada, que está conectada (ver siguiente imagen) y también el ID de propiedad.

![enter image description here](https://i.imgur.com/bKDjGw6.png)

Si pulsamos sobre el botón de "Ver propiedad GA4" iremos al panel de configuración de la propiedad, necesario para crear un flujo de recogida de información.

> Usa la [guía oficial de Google](https://seranking.com/blog/google-analytics-setup/) para ver otros ejemplos

Una de las grandes diferencias de GA4 frente a GA3 es que en este caso sólo disponemos de propiedades; en este caso, **no existen las vistas**.

## Configurar la recogida de datos

Google Analytics Universal era relativamente sencillo de usar; incluíamos el código en la página y los datos aparecían en la herramienta. GA4, por su naturaleza integradora de varios flujos de información (web, app, etc.) necesita que se configure previamente la fuente de origen de los datos que vamos a procesar.

Si hemos creado la propiedad GA4 a partir de una GA3 existente, se habrá creado un flujo de datos web de forma automática. Lo podemos comprobar en `Asistente de configuración` y dentro del bloque de Recogida, pulsando sobre la opción de `Instalación de la etiqueta`. 

![enter image description here](https://i.imgur.com/PNMVN6Q.png)

En el siguiente menú debe aparecernos un elemento dentro de la tabla de flujos de datos.

![enter image description here](https://i.imgur.com/PUeF2fv.png)

Si no aparece, o simplemente queremos crear otro, pulsamos sobre `Añadir flujo`. Ahora se nos presentarán varias opciones; debemos seleccionar el origen de los nuevos datos, los cuales serán integrados con cualquier otro flujo que ya exista. Esto es sin duda una de las grandes ventajas de GA4 frente a las versiones anteriores.

![enter image description here](https://i.imgur.com/8aq3JOa.png)

En la siguiente ventana tendremos que rellenar los datos que nos soliciten. Para el caso de un nuevo flujo web, serán la URL del dominio y el nombre del flujo. Recomiendo dejar el resto de opciones asociadas a la medición mejorada, tal como están, puesto que cualificarán los datos que se recojan.

![enter image description here](https://i.imgur.com/8h1siBy.png)

## Instalar el código de GA4

Una vez que tengamos nuestro flujo de datos listo, debemos pulsar sobre el mismo para ver tanto el ID de medición como las instrucciones necesarias para la instalación del código.

![enter image description here](https://i.imgur.com/vrUty7h.png)



El código de GA4 usa el objeto `gtag.js`, el mismo que la versión [Global Site Tag](https://emirodgar.com/versiones-google-analytics) y diferente al `analytics.js` de la versión GA3. En nuestro caso habremos recibido un código similar al siguiente para que incluyamos en nuestra web.

Este código debe ser insertado justo al principio de la etiqueta `<head>`.

    <!-- Global site tag (gtag.js) - Google Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-5YP5FZCQ8W"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
    
      gtag('config', 'G-5YP5FZCQ8W');
    </script>

Nuestra recomendación es hacer la implementación a través de GTM, por facilidad y escalabilidad. En este caso necesitaríamos crear una nueva etiqueta de e incluir el ID que nos hayan generado. En nuestro ejemplo sería `G-5YP5FZCQ8W`.

> Si hacemos uso de algún CMS lo más seguro es que ya existan plugins que nos permitan instalar directamente el código a partir del ID de la propiedad. Usa esta tabla para saber [si tu plataforma es compatible con GA4](https://support.google.com/analytics/answer/10447272#native-support).

## Validar la implementación

Asociado a cada flujo de datos, habrá un mensaje informativo que nos indica, si se están recogiendo datos o no. Eventualmente, nos informará de si el flujo funciona, pero no nos servirá para verificar en el momento si todo está funcionando bien.

![enter image description here](https://i.imgur.com/Y4lIhel.png)

Para ello lo mejor será acceder a la web (para que el código de GA4 se ejecute) y hacer uso del informe en tiempo real para constatar que, al menos nosotros, aparecemos en el informe.

![enter image description here](https://i.imgur.com/Ori3yvb.png)


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY2MDA1MTY4OSwtOTE5NjUzOTI1LC0xNz
E3NTQxNDM4LDI3MzExMDY1MiwxMDI4NDAzOTIwLC0xNzYyODEw
MDc0LC0yMTExNDMwMTUxXX0=
-->