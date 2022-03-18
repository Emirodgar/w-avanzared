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

El primero paso que tendremos que dar será crear una propiedad de GA4, puesto que las actuales corresponden a la versión que quedará obsoleta a partir del verano de 2023.

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
eyJoaXN0b3J5IjpbLTE0NzE4MzEwNTgsMTAyODQwMzkyMCwtMT
c2MjgxMDA3NCwtMjExMTQzMDE1MV19
-->