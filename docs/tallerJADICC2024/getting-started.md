# Comencemos

## El editor p5 online

Así se ve el editor online que nos provee [p5.js editor](https://editor.p5js.org).
Si, lo que ves más abajo es un editor de p5 totalmente funcional embebido en
esta página, más adelante hablaremos de como hacer esto, por ahora puedes usarlo
así o puedes abrir una nueva ventana e ir al sitio de *p5.js*.

La siguiente figura muestra los diferentes elementos del editor en línea:

![editor mapa](img/web-editor-map.webp)

Debajo está el editor embebido en éste documento, en el cual podemos trabajar
directamente o ustedes pueden abrirlo en
[otra ventana de su navegador](https://editor.p5js.org/). Ante la pregunta de
usar *cookies*, pulsar en el botón `Allow Essential` (permitir sólo lo
esencial). Pueden seleccionar el idioma español en el menú de arriba a la
izquierda.

<iframe src="https://editor.p5js.org/"  width="600" height="600"></iframe>

### Usando el p5.js Web Editor:

1. Ingresar con una cuenta en el editor web. Podemos hacerlo con nuestra cuenta
   de gmail y otras, o crear un usuario en el sitio.
2. Nombrar el proyecto clickeando el icono del lapiz.
3. En el menú file, guardar (save)
4. Confirmar que su proyecto ha sido guardado navegando la galería de sketches.

![guardar .center](img/save-sketch.gif ':size=60%')

### El código inicial

Cada vez que creamos un nuevo proyecto, el sistema crea tres archivos:
`index.html`, `style.css`, y `sketch.js`.

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}
```

El archivo `sketch.js` contiene inicialmente dos funciones: `setup()` y
`draw()`. Al iniciarse la aplicación, *p5.js* ejecutará `setup()` se una vez al
principio. Podemos usar esta función para definir configuraciones o valores
iniciales de nuestro proyecto, como por ejemplo crear el *canvas* (área de
dibujo) en la página web.

El código de *p5.js* invocará a la función `draw()` repetidamente unas 60 veces
por segundo, permitiéndonos programar animaciones fácilmente.

Si ejecutamos el programa, sólo visualizaremos el canvas con un fondo gris
suave.

## Nuestra primera animación

Para confirmar que el sistema ejecuta la función `draw()` repetidamente, podemos
ir cambiando el color de fondo del canvas de la siguiente manera:

```js
// color de fondo del canvas
let fondoCanvas = 255;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(fondoCanvas);
  fondoCanvas = (fondoCanvas + 1) % 256;
}
```