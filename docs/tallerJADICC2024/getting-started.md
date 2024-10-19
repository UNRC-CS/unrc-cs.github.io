# Comencemos

## El editor p5 online

Así se ve el editor online que nos provee [p5js.org](https://editor.p5js.org). Si, lo que ves más abajo es un editor de p5 totalmente funcional embebido en esta página, más adelante hablaremos de como hacer esto, por ahora puedes usarlo así o puedes abrir una nueva ventana e ir al sitio de p5

<iframe src="https://editor.p5js.org/"  width="600" height="600"></iframe>

### Usando el p5.js Web Editor:

1. Logearse en el editor web
2. Nombrar el proyecto clickeando el icono del lapiz.
3. En el menú file, guardar (save)
4. Confirmar que su proyecto ha sido guardado navegando la galería de sketches.

![guardar .center](img/save-sketch.gif ':size=60%')

### El codigo por defecto

Cada vez que creamos un nuevo proyecto, por defecto se incluye la librería p5.js y tres archivos: index.html, style.css, y sketch.js.

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}
````

Todo archivo sketch.js se inicia con dos funciones principales: setup() y draw(). Cuando se ejecute el código del sketch la función setup() se ejecutará una vez al principio, usualmente aprovecharemos esto para establecer configuraciones o valores iniciales de nuestro proyecto; seguidamente la función draw() se ejecutará repetidamente unas 60 veces por segundo. Aprovecharemos setup() para crear el área de dibujo invocando a createCanvas().