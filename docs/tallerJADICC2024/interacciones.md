# Aplicaciones interactivas

Dentro del conjunto de facilidades que provee *P5.js* se encuentran funciones y variables para registrar los eventos producidos por la interacción externa, desde aceleración y rotación de dispositivos móviles, detección de toque y arrastre sobre pantallas táctiles, hasta los simples movimientos de mouse y presión de teclas del teclado [Referencia](https://p5js.org/reference/#Events).

Los videojuegos son las aplicaciones interactivas por excelencia, y suelen ser muy buenos disparadores para motivar estudiantes a resolver nuevos desafíos. Vamos a desarrollar un pequeño juego interactivo usando algunas de las ideas que ya vimos.

[Pong](https://es.wikipedia.org/wiki/Pong): es un videojuego de consolas de primera generación, publicado por Atari en 1972. Pong fue el primer videojuego con éxito comercial.

<!-- La idea del juego es muy simple: dos jugadores controlan paletas y deben tratar de atajar/golpear la pelota evitando que esta toque el limite de la cancha que está a sus espaldas; si la pelota toca el limite que está detrás de la paleta, el contrario anota un punto.-->

![imagen pong .center](img/PongGame.gif)

-------------------------------------------------------------------------------

## Definiendo el área de juego

Para comenzar definamos el tamaño de nuestra cancha como una constante `const courtSize`, crearemos el canvas utilizándola y luego dibujaremos la red mediante la función `dibujarRed()`.

<iframe src="https://editor.p5js.org/gastonscilingoDC/sketches/WEus676AV" width="600" height="600"></iframe>





## Representando los objetos móviles


Nuestro juego contará de tres objetos móviles, la pelotita y las dos paletas. Intentaremos imitar la estética retro pixelada del juego original. La pelotita será un simple cuadrado y las paletas dos rectángulos por el momento. Definiremos objetos `javascript` para representar nuestros objetos del juego y utilizaremos la función `rect()` de *p5.js* para dibujarlos.

Cada  uno de estos objeto (pelotita, paleta izquierda y paleta derecha) deberá estar representado de  manera tal que  podamos "recordar" su estado, como posición, velocidad, tamaño, color, etc. En el caso de las paletas  una función para construir  las paletas se verá como:

```js

function getPaleta(inicX, inicY) {
  return {
    x : inicX,
    y : inicY,
    ancho : 10,
    alto : 30,
  
    dibujar(){
      rect(this.x, this.y, this.ancho, this.alto);
    }
    
   }
}
```


donde `(x,y)`  almacenará la posición de la esquina  superior izquierda de la paleta, mientras que `ancho` y `alto`  almacenarán el ancho y alto de la paleta respectivamente. Recordemos que *p5js* nos provee funciones (`rect()`) para dibujar un rectángulo en el canvas. La función `dibujar()` encapsula este comportamiento para un objeto dado.


Pensemos ahora cómo se representa la pelotita y qué comportamiento deberá tener definido, luego  definimos la función apropiada (`getPelota()`).

<span style="color: blue;">¿Lo hacemos?</span>
 

<iframe src="https://editor.p5js.org/gastonscilingoDC/sketches/3GwhDf4Gq" width="600" height="600">></iframe>


> [!TIP|label:NOTA]
> Link para abrir este editor en otra ventana del navegador [Definiedo paletas y pelota en movimiento](https://editor.p5js.org/gastonscilingoDC/sketches/3GwhDf4Gq)
### Dando movimiento a la pelota

La pelota esta definida, pero... ¿Cómo logramos que se mueva? 

Revisamos los conceptos vistos en la sección  [fuerza y colisiones](colisiones.md) y retomamos nuestro juego. Analizamos las nuevas propiedades que ahora son parte del estado de la pelota y  completamos la función `mover()` 

<span style="color: blue;">¿Te animás?</span>


<iframe src="https://editor.p5js.org/gastonscilingoDC/sketches/N-yzZWI_z" width="600" height="600"></iframe>

> [!TIP|label:NOTA]
> Link para abrir este editor en otra ventana del navegador [Pelota en movimiento](https://editor.p5js.org/gastonscilingoDC/sketches/N-yzZWI_z)


### Dando movimiento a las paletas

En este juego, los jugadores controlarán las paletas utilizando el teclado. La paleta derecha se moverá con las teclas de flecha  &uarr; y  &darr;, mientras que la paleta izquierda se manipulará con las teclas `a` (arriba) y `z` (abajo). Para lograr esto, *p5.js* nos ofrece varias funciones y variables que facilitan la gestión de eventos del teclado, como `keyPressed()`, `key` y `keyCode`, las cuales permiten detectar y manejar las entradas del usuario através del teclado.

```js

function keyPressed() {
  if (key === 'a') {
    // Código a ejecutar si se presiona la letra a
  }

  if (keyCode === ENTER) {
    // Código a ejecutar si se presiona la tecla enter
  }
}


```


* `keyPressed()` es una función que se ejecuta automáticamente cuando el usuario presiona cualquier tecla del teclado. Es útil para capturar cuándo una tecla ha sido presionada y realizar acciones en consecuencia.

* `key` es una variable global de *p5.js* que almacena el valor de la tecla presionada más recientemente. `key` no se actualiza cuando se trata de caracteres especiales como `LEFT_ARROW` y `ENTER`. En estos casos utilizamos la variable `keyCode`. `keyCode` es una variable global que almacena el código ASCII de la última tecla presionada. 

> Las constantes `BACKSPACE`, `DELETE`, `ENTER`, `RETURN`, `TAB`, `ESCAPE`, `SHIFT`, `CONTROL`, `OPTION`, `ALT`, `UP_ARROW`, `DOWN_ARROW`, `LEFT_ARROW` y `RIGHT_ARROW` 
> son constantes útiles definidas por *p5.js* para los caracteres especiales.

<span style="color: blue;">¿Lo hacemos?</span>


<iframe src="https://editor.p5js.org/gastonscilingoDC/sketches/dy5-wUVe7" width="600" height="600"></iframe>


> [!TIP|label:NOTA]
> Link para abrir este editor en otra ventana del navegador [Moviendo las paletas](https://editor.p5js.org/gastonscilingoDC/sketches/dy5-wUVe7)

Ya podemos controlar las paletas con el teclado!  

Ahora necesitamos definir  cómo detectamos si una pelota tocó una de las paletas y cuál es la reacción de la misma ante esta situación. La idea será que la pelota rebote al tocar una paleta y para ello, debemos en primer lugar determinar si la pelota colisionó con una paleta, para luego en tal situación,  invertir la dirección  de la pelota.

### Devolviendo la pelota con la paleta
   
<iframe src="https://editor.p5js.org/gastonscilingoDC/sketches/Pj6feCWFu" width="600" height="600"></iframe>

Definamos, como parte del objeto paleta, la función `colisionaCon(pelota)` la cual retorna `true` si la paleta toca a la pelota y `false` en caso contrario. Luego restará definir la función `verificarColisiones()`,  lo cual produce que la pelota rebote  (cambie su dirección) cuando toca una de las paletas.


> Para detectar si dos rectángulos colisionan basta detectar si se superponen. Sean  los rectángulos $r$ y $s$ tales que 
> $r$ esta definido por los puntos ($rx_1$,$ry_1$) y ($rx_2$,$ry_2$) esquina superior izquierda y esquina inferior derecha de $r$ respectivamente; y $s$ esta definido por los puntos ($sx_1$,$sy_1$) y ($sx_2$,$sy_2$) esquinas superior izquierda y esquina inferior derecha de $s$  respectivamente.
> 
> $r$ y $s$ colisionan si:
>
> [$ry_1$,$ry_2$] $\cap$ [$sy_1$,$sy_2$] $\neq \emptyset$  y  [$rx_1$,$rx_2$] $\cap$ [$sx_1$,$sx_2$] $\neq \emptyset$.
>
> siendo  [$ry_1$,$ry_2$], [$sy_1$,$sy_2$], [$rx_1$,$rx_2$] y  [$sx_1$,$sx_2$] intervalos cerrados de puntos.

<span style="color: blue;">Manos a la obra!</span>


## ¿Quién es el ganador?


TBD

<iframe src="https://editor.p5js.org/gastonscilingoDC/full/LPdkOm2zq" width="600" height="600"></iframe> 
