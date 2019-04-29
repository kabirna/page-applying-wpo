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

