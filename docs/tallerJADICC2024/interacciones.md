# Aplicaciones interactivas

Dentro del conjunto de facilidades que provee *P5.js* se encuentran funciones y variables para registrar los eventos producidos por la interacción externa, desde aceleración y rotación de dispositivos móviles, detección de toque y arrastre sobre pantallas táctiles, hasta los simples movimientos de mouse y presión de teclas del teclado [Referencia](https://p5js.org/reference/#Events).

Los videojuegos son las aplicaciones interactivas por excelencia, y suelen ser muy buenos disparadores para motivar estudiantes a resolver nuevos desafíos. Vamos a desarrollar un pequeño juego interactivo usando algunas de las ideas que ya vimos.

[Pong](https://es.wikipedia.org/wiki/Pong): es un videojuego de consolas de primera generación, publicado por Atari en 1972. Pong fue el primer videojuego con éxito comercial.

<!-- La idea del juego es muy simple: dos jugadores controlan paletas y deben tratar de atajar/golpear la pelota evitando que esta toque el limite de la cancha que está a sus espaldas; si la pelota toca el limite que está detrás de la paleta, el contrario anota un punto.-->

![imagen pong .center](img/PongGame.gif)

-------------------------------------------------------------------------------

## Definiendo el área de juego

Para comenzar definamos el tamaño de nuestra cancha como una constante `const courtSize`, crearemos el canvas utilizándola y luego dibujaremos la red con la función `dibujarRed()`.

<iframe src="https://editor.p5js.org/gastonscilingoDC/sketches/WEus676AV" width="600" height="600"></iframe>





## Representando los objetos móviles


Nuestro juego contará de tres objetos móviles, la pelotita y las dos paletas. Intentaremos imitar la estética retro pixelada del juego original. La pelotita será un simple cuadrado y las paletas dos rectángulos por el momento. Definiremos objetos `javascript` para representar nuestros objetos del juego y utilizaremos la función `rect()` de *p5.js* para dibujarlos.

TBC

<iframe src="https://editor.p5js.org/gastonscilingoDC/full/3GwhDf4Gq" width="600" height="600">></iframe>

## Dando movimiento a las paletas

TBC : uso de keyPressed() y key 



## Versión final

TBD

<iframe src="https://editor.p5js.org/gastonscilingoDC/full/LPdkOm2zq" width="600" height="600"></iframe> 
