# Optimización de carga de sitios web con WPO (Web Performance Optimization)

## Conociendo Google PageSpeed Insights

Google dentro de sus herramientas para desarrolladores tiene una página que nos inidicara el nivel de rendimiento de una pagina web, tanto en su version móvil como en la pc, y nos dará recomendaciones para optimizar nuestra página:

<https://developers.google.com/speed/pagespeed/insights/>

## Eliminando bloqueos de renderizado

Google recomienda poner nuestras hojas de estilo debajo del **above the fold**, la expresión define la parte del sitio que los usuarios ven primero sin necesidad de desplazarse con el ratón.

![aboveTheFold](images/aboveTheFold.png)

## Comprimiendo nuestro archivo CSS

Esto se puede hacer de muchas maneras, ya sea utilizando preprocesadores como Sass, Less o Stylus, o también puedes utilizar Webpack, o bien mediante sitios en internet como <https://csscompressor.com/>

Una vez minificado deberemos crear un nuevo archivo CSS pero que termine en `min.css` para diferenciar de la version sin minificar. Una vez hecho esto debemos apuntar nuestro HTML a este archivo minificado.

```html
<link rel="stylesheet" href="css/style.min.css">
```

## Critical CSS o Critical Path CSS

Para eliminar el bloqueo de la visualización solamente nos queda hacer Critical Path CSS.

Al momento de cargar un sitio este se encontrará sin estilos hasta el momento de cargar el CSS por completo generando que la visualización del sitio sea mala, para solucionar esto solamente debemos escribir el CSS necesario para el Above the fold dentro de nuestro HTML. Haremos uso del sitio <https://jonassebastianohlsson.com/criticalpathcssgenerator/>.

Los pasos son los siguientes:
    1. Debemos colocar la URL de nuestro sitio a optimizar
    2. Colocar el codigo CSS completo
    3. Dar click en el boton **Create Critical Path CSS**
    4. El codigo resultante debemos colocarlo en nuestro index.html dentro de etiquetas `<style>` en el `<head>`.

## Optimizando las imágenes

Para tener nuestro sitio totalmente optimizado solamente nos queda optimizar nuestras imágenes.

Algunas veces estaremos renderizando una imagen con un tamaño mucho mayor del que tenemos en el sitio, por ello es buena práctica redimensionar nuestras imágenes al tamaño que mostramos en nuestro sitio, usaremos el servicio de <https://resizeimage.net/>.

No basta solamente con redimensionar nuestras imágenes, también debemos comprimirlas y de preferencia tenerlas en formato PNG para evitar perdidas en la calidad de imagen, para esto usaremos el servicio <https://tinypng.com/>.

Actualmente se recomienda el uso de formatos de compresión avanzados como **JPEG 2000** o **WebP**. Vale la pena mencionar que actualmente **Safari** no soporta WebP por lo que tendriamos que usar un fallback (imagen en caso de que falle la primera) en el caso de los navegadores que no soporten dicho formato.

Podriamos poner nuestra imagen por defecto en el atributo **data** de una etiqueta `<object>` y dentro de ella una etiqueta `<img>` que sera nuestro fallback en caso de que la primera falle:

```html
<object data="http://stackoverflow.com/default-image.png" type="image/png">
    <img src="https://appharbor.com/assets/images/fallback-image.png" alt="example">
</object>
```

Podemos encontrar recursos para optimizar en la pagina de desarrolladores de Google 

<https://developers.google.com/web/fundamentals/>