# Animaciones

Una animación por computadora consiste en dibujar un conjunto de *objetos en
movimiento* repetidamente en la pantalla (o canvas).

En cada ciclo se deben realizar los siguientes pasos:

1. Limpiar la pantalla
2. Ajustar velocidades por rebotes y aceleraciones
3. Calcular las posiciones de cada objeto
4. Dibujar los objetos

Ya vimos que en *p5.js* implementando estos pasos en la función `draw()` es
suficiente ya que el sistema la ejecuta repetidamente en forma automática.

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

En el [sketch](https://editor.p5js.org/marroyo/sketches/dZyp4-S06) podemos ver
una primera versión de objetos en movimiento. En `utils.js` podemos ver una
función para crear círculos.

Analicémosla!!!

## Colisiones simples

Si queremos lograr efectos de rebotes, debemos hacer cambios en la *dirección*
de la velocidad de los objetos en una colisión.

Agreguemos la lógica para que los círculos reboten en los extremos del canvas.
Sería bueno que cada objeto tenga una propiedad que determine si debe rebotar en
los límites del canvas o no.

Debemos hacer que su dirección se invierta en la función
`actualizarVelocidad()`.

Lo hacemos?