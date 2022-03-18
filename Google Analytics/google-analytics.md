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

> En la [guía oficial de Google](https://seranking.com/blog/google-analytics-setup/) nos explican cómo crear una propiedad GA4

## Configurar la recogida de datos

Google Analytics Universal era relativamente sencillo de usar; incluíamos el código en la página y los datos aparecían en la herramienta. GA4, por su naturaleza integradora de varios flujos de información (web, app, etc.) necesita que se configure previamente la fuente de origen de los datos que vamos a procesar.

Si hemos creado la propiedad GA4 a partir de una GA3 existente, se habrá creado un flujo de datos web de forma automática. Lo podemos comprobar en `Asistente de configuración` y dentro del bloque de Recogida, pulsando sobre la opción de `Instalación de la etiqueta`. 

![enter image description here](https://i.imgur.com/PNMVN6Q.png)

En el siguiente menú debe aparecernos un elemento dentro de la tabla de flujos de datos.

![enter image description here](https://i.imgur.com/PUeF2fv.png)

Si no aparece, o simplemente queremos crear otro, pulsamos sobre `Añadir flujo`. Ahora se nos presentarán varias opciones; debemos seleccionar el origen de los nuevos datos, los cuales serán integrados con cualquier otro flujo que ya exista. Esto es sin duda una de las grandes ventajas de GA4 frente a las versiones anteriores.

![enter image description here](https://i.imgur.com/8aq3JOa.png)

En la siguiente ventana tendremos que rellenar los datos que nos soliciten. Para el caso de un nuevo flujo web, serán la URL del dominio y el nombre del flujo. Recomiendo dejar el resto de opciones tal como están

![enter image description here](https://i.imgur.com/8h1siBy.png)

## Instalar el código de GA4

Hay varios escenarios para comenzar a registrar información. 

### Instalar el código directamente sobre la web

 1. Añadir los dos códigos a la página. Por un lado, tendremos `analytics.js` (GA3) y por otro `gtag.js` (GA4). Cada código será independiente.
 2. Empleamos únicamente el código `gtag.js` y enviamos el flujo de información a las dos propiedades (GA3 y GA4).

### Instalar el código desde Google Tag Manager

Nuestra recomendación es hacerlo a través de GTM, por facilidad y escalabilidad.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNTIwMTM3ODYsMjczMTEwNjUyLDEwMj
g0MDM5MjAsLTE3NjI4MTAwNzQsLTIxMTE0MzAxNTFdfQ==
-->