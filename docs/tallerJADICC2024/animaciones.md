# Animaciones

Una animación por computadora consiste en dibujar un conjunto de *objetos en
movimiento* repetidamente en la pantalla (o canvas).

En cada ciclo se deben realizar los siguientes pasos:

1. Limpiar la pantalla
2. Ajustar velocidades por rebotes y aceleraciones
3. Calcular las posiciones de cada objeto
4. Dibujar los objetos

Ya vimos que en *p5.js* implementando estos pasos en la función `draw()` es
suficiente ya que se ejecuta repetidamente.

-------------------------------------------------------------------------------

## Física ultra-básica

Cada objeto en movimiento tendrá una *posición* actual y una *velocidad*. Ambas
propiedades pueden representarse por un *vector*.

> Un *vector* representa una *magnitud* y una *dirección*. Pueden usarse para
> representar un punto en un sistema cartesiano, o una *fuerza*.

Es posible representar un vector (ej: en 2D) como:

1. *Coordenadas cartesiana*: Un par de la forma *(x,y)*. 
    
    Su *magnitud* $m$ es la distancia desde el punto *(0,0)*:

    $$\mid \overrightarrow{v} \mid=\sqrt{v.x^2 + v.y^2}$$

    El *ángulo* $\alpha$:
    $$\alpha(\overrightarrow{v}) = cos^{-1}\left( {\frac{v.x}{\mid
    \overrightarrow{v} \mid}} \right)$$
    
2. *Coordenadas polares*: Un par de la forma *(ángulo, magnitud)*.

*P5.js* usa vectores cartesianos 3D de la forma $(x,y,z)$.
Ver [vectores](https://p5js.org/es/reference/p5/p5.Vector/).

Un *vector velocidad* $v$ indica cuál es la *variación horizontal y vertical* de
la posición del objeto en un intervalo de tiempo $t$. La *nueva posición* debe
computarse según la ecuación

$$p' = p + v \times t$$

donde $p'$ es la nueva posición, $p$ es la posición actual y $v$ es la
velocidad.

Para hacer nuestras animaciones simples, asumiremos que $t=1$, así que la nueva
posición se puede obtener simplemente haciendo $p' = p + v$.

?> Nota: Aquí, la suma representa *suma de vectores* (no escalares).

-------------------------------------------------------------------------------

## Representación de objetos móviles

Cada objeto de nuestro programa debe estar representado de alguna manera ya que
necesitaremos recordar su estado, como posición y velocidad, forma, color, etc.

Abajo se muestra un ejemplo de un objeto que representa un círculo posicionado
inicialmente en la esquina superior izquierda del canvas con velocidad *(1,1)*.

```js
let circulo = {
    diametro: 50,
    posicion: {x: 25, y: 25},
    velocidad: {x: 1, y: 1},
    color: rojo(),
    dibujar: function() {
        fill(this.color);
        circle(this.posicion.x, this.posicion.y, this.diametro);
    }
}
```

Debajo vemos un sketch con una podemos ver una primera versión de objetos en
movimiento. En `utils.js` podemos ver una función para crear círculos.

> Nota: Si sólo ven la ejecución del programa hacer click en el nombre del
> sketch (*taller-p5-v1*).

Hacer click [aquí](https://editor.p5js.org/marroyo/full/dZyp4-S06) si desean
abrir el sketch en otra pestaña o ventana del navegador.

<iframe src="https://editor.p5js.org/marroyo/full/dZyp4-S06"
        width="600" height="600"></iframe>

## Colisiones simples

Si queremos lograr efectos de rebotes, debemos hacer cambios en la *dirección*
de la velocidad de los objetos en una colisión.

Agreguemos la lógica para que los círculos reboten en los extremos del canvas.
Aplicaremos el efecto de rebote a los objetos que tengan la propiedad
`rebotaEnCanvas`.

En el siguiente sketch incluimos el efecto de rebote en los límites del canvas.

<iframe src="https://editor.p5js.org/marroyo/full/VQiUttPI5" 
        width="600" height="600"></iframe>

Se debe notar que se movió el código de cálculo de la posición a una función en
el archivo `dinamica.js` (script incluido en `index.html`).

En `dinamica.js` la función `actualizarPosición(obj)` invocada desde `draw()`
ahora invoca a `actualizarVelocidad(obj)` para eventualmente cambiar la
dirección de la velocidad ante un rebote en los límites del canvas.

Veamos la lógica para determinar si rebotamos en las paredes izquierda o derecha.

1. Rebota en la pared izquierda si la posición $x$ menos el radio es $\leq 0$
2. Rebota en la pared derecha si la posición $x$ más el radio es $\geq width$,
   donde `width` es una variable de `p5` con el *ancho del canvas*.

La reacción es muy simple: Invertimos la dirección (componente *x* del vector
*velocidad*).

Hacemos lo mismo para los rebotes en el techo y piso, usando la posición *y*
inviertiendo el componente *y* del vector *velocidad*.

## Interacción con el mouse

Si definimos la función `mouseClicked()`, éste se invocará en cada click del
mouse. El sistema, además, define las variables globales `mouseX` y `mouseY` que
representan la coordenada *(x,y)* del canvas donde ocurrió el click.

> ***Ejercicio***: Incrementar la velocidad horizontal del círculo cada vez que
> se hace un click sobre él.

¿Cómo detectar si se hizo click sobre el círculo?

> Un punto $(x,y)$ en el plano está dentro del círculo $c$ con centro $(c_x,
> c_y)$ y radio $r$, si la *distancia* entre $(x,y)$ y $(c_x, c_y)$ es menor que
> $r$.

Ya vimos cómo calcular la *distancia entre dos pintos* cuando vimos el cálculo
de la *magnitud* de un vector. En `sketch.js` está definida esta función (más
abajo).

<span style="color: blue;">¿Lo hacemos?</span>
