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

> En la [guía oficial de Google](https://seranking.com/blog/google-analytics-setup/) nos explican cómo crear una propiedad GA4

Lo que haremos será que ambas propiedades convivan, recogiendo información al mismo tiempo.

## Instalar el código de GA4

Hay varios escenarios para comenzar a registrar información. 

### Instalar el código directamente sobre la web

 1. Añadir los dos códigos a la página. Por un lado, tendremos `analytics.js` (GA3) y por otro `gtag.js` (GA4). Cada código será independiente.
 2. Empleamos únicamente el código `gtag.js` y enviamos el flujo de información a las dos propiedades (GA3 y GA4).

### Instalar el código desde Google Tag Manager

Nuestra recomendación es hacerlo a través de GTM, por facilidad y escalabilidad.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ4NDgwMjQzMCwyNzMxMTA2NTIsMTAyOD
QwMzkyMCwtMTc2MjgxMDA3NCwtMjExMTQzMDE1MV19
-->