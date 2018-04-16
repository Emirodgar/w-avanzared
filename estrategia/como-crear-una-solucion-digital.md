# Cómo crear una solución digital

En este capítulo vamos a conocer diferentes tecnologías y herramientas que nos ayudarán a gestionar y controlar los aspectos más técnicos de nuestro negocio. 

## Tecnologías y plataformas

En este capítulo vamos a hablar y definir el **corazón tecnológico** de nuestra estrategia. Es la base sobre la que el resto de estrategias, tácticas y futuros desarrollos se sostendrán, por lo que tenemos que hacerlo bien desde un primer momento.

La tecnología avanza muy rápido por lo que es crucial hacer uso de **estándares de programación** o **plataformas modulares fácilmente escalables**. Un término que tenemos que tener presente es *legacy* o heredado.

> El término **legacy** se refiere a un sistema informático o aplicación web que ha quedado anticuado pero que sigue siendo utilizado por los usuarios.

Si no somos capaces de diseñar nuestra aplicación pensando en las necesidades futuras, crearemos una solución únicamente apta a corto plazo pero que a largo plazo no cubrirá nuestras necesidades. Nuestro objetivo es disponer de una solución tecnológica **ágil y escalable**.

El concepto *Big Data* -aunque a nivel informático no supone nada nuevo- ha cambiado por completo la arquitectura software de las empresas. Si antes buscábamos aplicaciones que solucionaban problemas existentes, ahora buscamos aplicaciones que solucionan problemas existentes **de forma óptima** y preparadas para solucionar los problemas del futuro más cercano. 

Por ello, la **programación distribuida** y en especial el término **escalabilidad**, han cobrado mucha fuerza en los últimos años.

### Escalabilidad en aplicaciones

Dentro de la arquitectura de sistemas y de programación existe el **término escalable**. Cuando una aplicación comienza a dar signos de desgaste, bien por una carga de trabajo excesiva, un número de usuarios demasiado grande o por la imposibilidad de exprimir de forma eficiente los recursos con los que cuenta, llega el momento de escalarla. Podemos llevar a cabo dos tipos de escalados, **vertical** u **horizontal**.

#### Escalado vertical (up)

También denominado *up*, quizá sea el escalado más rápido y económico que podemos realizar. Se trata de aumentar los componentes *hardware* que utiliza nuestra aplicación. Por ejemplo, aumentando la memoria RAM conseguiremos mejorar la velocidad de ejecución, mejorando la capacidad de disco podremos almacenar más datos, etc.

Las principales ventajas son que nos permite escalar de forma rápida y no afecta para nada a la aplicación (*software*). Su principal desventaja es que no podemos escalar verticalmente de forma indefinida y llegará un punto en el que seguir mejorando el hardware resultará muy costoso.

#### Escalado horizontal (out)

Este tipo de escalado nos ofrece una posibilidad de crecimiento infinito ya que se trata de añadir, de forma ilimitada, nuevos servidores que permitan ejecutar nuestra aplicación de forma distribuida. Nuestra aplicación estaría utilizando un clúster.

> Un clúster es una red de ordenadores unidos entre sí que se comportan como si se tratase de una sola máquina.

Otras ventajas de implementar este escalado -además de un crecimiento infinito- sería la tolerancia a fallos, una alta disponibilidad del sistema y la posibilidad de aplicar un balanceo de carga que nos ayude a distribuir las ejecuciones de forma controlada por todos los nodos que conforman el clúster.

A la hora de diseñar nuestra solución tecnológica tenemos que tener presente la posibilidad de un escalado horizontal (vertical no hay problema ya que prácticamente todas las arquitecturas lo aceptan) ya que será la clave para que podamos utilizarla -de forma eficiente- a largo plazo.

### Plataformas tecnológicas

Existen múltiples plataformas tecnológicas que nos ayudarán en el diseño y desarrollo de nuestra solución web. Elegir una en detrimento de las otras dependerá fundamentalmente de nuestros recursos y necesidades.

Quizá las plataformas más conocidas a día de hoy sean la de [Google Cloud][2] y [Amazon Web Services][3].

[2]:https://cloud.google.com/?hl=es
[3]:https://aws.amazon.com/es/

### Otras herramientas

Para dotar a nuestra estrategia de diversas funcionalidades podemos hacer uso de herramientas disponibles en la red. A continuación se muestra un pequeño listado de recursos interesantes:

- [Httpstatus][5] analiza redirecciones
- [Browseo][6] nos permite ver nuestra web como la ven los buscadores
- [Similar page checker][7] comprueba similitudes entre diferentes páginas
- [Giphy][4] es un buscador de imágenes en formato GIF 
- [Way Back Machine][8] nos da acceso a versiones antiguas de las páginas web
- [CloudFlare][9] es un CDN gratuito para tu web
- [Buzzsumo][10] nos permite conocer tedencias online

[4]:https://giphy.com/
[5]:http://httpstatus.io/
[6]:http://www.browseo.net/
[7]:http://www.webconfs.com/similar-page-checker.php
[8]:http://archive.org/web/web.php
[9]:https://www.cloudflare.com/
[10]:http://buzzsumo.com/

## Optimizando aspectos técnicos

Nuestra solución digital debe estar preparada para ofrecer un rendimiento y una calidad excepcional. Tenemos que ser cuidadosos con aquellos aspectos que nos ayuden a ofrecer un buen servicio a nuestros visitantes.

A continuación detallo algunos puntos que podemos trabajar para mejorar la experiencia de los usuarios.

### Especificar caché del navegador

Cuando navegamos por una página web diversos elementos de la misma son descargados a nuestro ordenador para facilitar que la navegación sea más fluida, evitando tener que descargarlos cada vez.

Estos elementos pueden ser ficheros HTML, CSS, PDF, javascript, imágenes y cualquier elemento del que haga uso la web. Si no especificamos un tiempo de estancia en la caché del navegador se utilizarán valores estándar poco optimizados y en algunos test de velocidad se hará referencia a "Leverage browser caching" como punto no optimizado.

Podemos comprobar el estado de cacheado de nuestra web con Redbot y, a mayores, podemos combinar la caché del servidor con la compresión GZIP de la web.

> En el caso de tener otro servidor diferente a Apache, podemos consultar esta [guía de configuración de servidores][1].

[1]:https://github.com/h5bp/server-configs

#### Módulo mod_expires de Apache

Para especificar la caché del navegador en Apache podemos hacerlo con el módulo mod_expires el siguiente bloque al archivo .htaccess. En el proyecto html5-boilerplate podemos encontrar muchos más ejemplos.

```
<IfModule mod_expires.c>
ExpiresActive On
ExpiresByType image/jpg "access 1 year"
ExpiresByType image/jpeg "access 1 year"
ExpiresByType image/gif "access 1 year"
ExpiresByType image/png "access 1 year"
ExpiresByType text/css "access 1 month"
ExpiresByType text/html "access 1 day"
ExpiresByType application/pdf "access 1 month"
ExpiresByType text/x-javascript "access 1 month"
ExpiresByType image/x-icon "access 1 year"
ExpiresDefault "access plus 1 month"
</IfModule>
```
En cada línea se establece el tipo de elemento que se va a cachear y el tiempo que permanecerá sin ser "descargado" y por tanto actualizado.

> Si disponemos de una página estática en HTML donde generamos cambios cada poco tiempo, tendremos que poner un valor de caché bajo para evitar que los visitantes reciban una página cacheada en lugar de la final

Para los valores de tiempo tendremos que utilizar los nombres en inglés (years, months, weeks, days, hours, minutes y seconds).

#### Módulo mod_headers de Apache

Tenemos una segunda opción para cachear elementos que sería utilizar mod_headers. Mod_expires nos permite controlar el tiempo máximo de cacheo para los ficheros, sin embargo, mod_headers nos permite mayor control sobre el tipo de cache y cuándo aplicarlo.

```
<ifModule mod_headers.c>
ExpiresActive On

# Expira en un mes
<filesMatch ".(gif|png|jpg|jpeg|ico|pdf|js|htm|html|txt)$">
Header set Cache-Control "max-age=2592000"
</filesMatch>

# Expira en un dia
<filesMatch ".(css)$">
Header set Cache-Control "max-age=86400"
</filesMatch>
</ifModule>
```

> De cara a valorar los resultados del tiempo de carga recomendamos utilizar WebpageTest

### Habilitar compresión Gzip en servidores Apache

Dentro del complejo proceso para reducir el tamaño y los tiempos de carga de las páginas web juega un papel muy importante la compresión Gzip. Primero recomendamos disponer de un buen sistema de caché de la web para después, comprimir todos los elementos incluyendo el conjunto de la web.

>Para comprobar si nuestra web soporta la compresión GZIP podemos hacer uso de GZIP Test o HTTP Compression Test.

Al comprimir nuestra página su tamaño será menor por lo que el tiempo de descarga desde el servidor hasta el navegador del usuario se reducirá notablemente.
Si contamos con un servidor Apache tendremos que incluir las siguientes líneas dentro del fichero .htaccess para habilitar la compresión por Gzip.

```
<ifModule mod_gzip.c>
  mod_gzip_on Yes
  mod_gzip_dechunk Yes
  mod_gzip_item_include file \.(html?|txt|css|js|php|pl)$
  mod_gzip_item_include handler ^cgi-script$
  mod_gzip_item_include mime ^text/.*
  mod_gzip_item_include mime ^application/x-javascript.*
  mod_gzip_item_exclude mime ^image/.*
  mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
</ifModule>
```

### Imagen por defecto cuando fallan las imágenes con .htaccess

Cuando una imagen no carga queda a disposición del navegador cómo mostrarla. Antiguamente Internet Explorer mantenía "el hueco" y mostraba un aspa roja para advertir al usuario de que había habido un problema. En otras ocasiones simplemente se ignora y el usuario nunca se da cuenta de que había una imagen.

A través del fichero .htaccess podemos redireccionar todas aquellas imágenes que no existen o dan error a una por defecto. El código que tendríamos que añadir en nuestro fichero .htaccess es el siguiente:

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} -s [OR]
RewriteCond %{REQUEST_FILENAME} -l [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^.*$ - [NC,L]
RewriteRule ^.*$ imagen-por-defecto.jpg [NC,L]
```

### Redireccionar todos los errores

Esta directiva debemos aplicarla solo en casos muy concretos. Por ejemplo, si acabamos de realizar una migración y estamos generando un número descontrolado de errores 404, puede ser buena idea utilizar este comando para redireccionar todo a la home y evitar generar una mala experiencia a nuestros visitantes.

No obstante, debería ser algo temporal en lo que solucionamos el problema que está generando los errores. Una vez solventado, es recomendable ofrecer una página de **error 404 personalizada**.

```
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ /? [L,R=301]
```
