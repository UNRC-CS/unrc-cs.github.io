# Fuerzas, aceleración y colisiones

Una fuerza aplicada a un objeto produce una *aceleración*, lo que afectará a su
*velocidad*.

Las fuerzas pueden representarse como vectores. Por ejemplo, la fuerza de
*gravedad* es una fuerza aplicada verticalmente, mientras que la *fricción* (o
*tracción*) sobre una superficie se aplica a la velocidad horizontal.

> Una *fuerza* aplicada a un objeto producirá una *aceleración* la cual a su vez
> modificará su velocidad.

Es común en animaciones simples en lugar de usar los vectores de fuerzas
directamente se usen *factores de aceleración*. Esto es común para simular
propiedades de objetos como la fricción sobre superficies y *elasticidad*
(cuánto *rebota* en una colisión).

## Efectos de gravedad, fricción y elasticidad

La *gravedad* es una fuerza descente. Aplicarla simplemente consiste en sumarle el
valor de la gravedad al componente *y* del vector velocidad.

La *elasticidad* o *factor de rebote (bouncing)* se multiplica al componente *x*
o *y* (según corresponda) en una colisión.

La *fricción* o *tracción* representa una fuerza que *frena* el objeto en su
dirección horizontal, comúnmente al desplazarse en el piso.

El siguiente sketch aplica estas ideas en la función `actualizarVelocidad(obj)`.

<iframe src="https://editor.p5js.org/marroyo/full/AB6ic6ELu"
        width="600" height="600"></iframe>

Podemos experimentar cambiando las propiedades al objeto.

## Colisiones entre objetos

