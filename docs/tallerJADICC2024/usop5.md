# Uso de *p5.js* en proyectos con alumnos

El uso más frecuente del uso de *p5.js* en proyectos educativos es cuando el
docente comparte un *sketch* con los estudiantes y les plantea extensiones o
modificaciones.

Cada estudiante puede acceder al *sketch* compartido y trabajar sobre él,
aunque no lo dejará grabar sus modificaciones hasta que ingrese con su cuenta.

Podemos crear una cuenta en el sitio de *p5.js* o acceder con nuestra cuenta de
*Google*.

-------------------------------------------------------------------------------

## Uso de *p5.js* localmente (desconectado)

En el caso que no se disponga de acceso a Internet, es posible trabajar con
*p5.js* localmente. Lo único que se necesitará es usar el navegador web y un
editor de código como [Visual Studio Code](https://code.visualstudio.com/) o
[Notepad++](https://notepad-plus-plus.org/).

En este caso debemos descargar el archivo Javascript `p5.js` o puede descargar
la biblioteca completa que incluye `p5.sound.min.js` con funciones de manejo de
sonido. Ver la sección [Descarga](https://p5js.org/es/download/).

[Aquí](assets/p5.zip ':ignore') les dejamos un sketch básico que pueden descargar un
comenzar a usar luego de

1. Descomprimir el archivo
2. Abrir el archivo `index.html` en el navegador web (hacer doble click en el
   archivo)

Con un editor de programación (o cualquier editor de textos plano) puede hacer
modificaciones y recargar en el navegador para ver los cambios.

## Uso en el editor (IDE) vscode

El editor libre [Visual Studio Code](https://code.visualstudio.com/) contiene
*complementos* para trabajar con *p5.js*. El complemento `p5.vscode` permite
instalar otros complementos que permiten crear proyectos y ejecutarlos lanzando un
*servidor web* local y abre la aplicación directamente en el navegador web.

-------------------------------------------------------------------------------

## Cómo incluir un sketch en una página web

Es muy simple incluir un sketch o el editor en una página web. Simplemente
debemos incluir un `ìframe` de la forma

```html
<iframe src="https://editor.p5js.org/" width="600" height="700"></iframe>
```

Reemplazá el *url* de tu propio sketch en el atributo `src` para que aparezca en
una página. En la opción `Archivo -> Compartir` el editor en línea ofrece los
urls en diferentes modos: incrustar, visualización de ejecución (full) y el
enlace de edición.