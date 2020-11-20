# Introducción

## ¿Por qué JavaScript?

JavaScript es el lenguaje de programación fundamental en el ámbito de la web. Es ideal para aquellos que desean comenzar a programar por primera vez, y no tienen ninguna experiencia previa, dado que se puede comenzar a trabajar con él directamente en el navegador web, sin necesidad de instalar entornos de desarrollo ni herramientas complejas, como sucede con otros lenguajes.

Tiene la característica de ser mucho menos estricto que otros lenguajes, y esto lo hace más amigable con quienes lo adopten como su primer lenguaje de programación, debido a que posee mecanismos internos con los que permite que un programa funcione en casos en los que otros lenguajes arrojarían errores.

Por otra parte, cada vez más sitios web hacen uso extensivo de JavaScript, y ya no solamente para agregarle detalles atractivos. En los últimos años las plataformas web pasaron a delegar en el navegador y en JavaScript muchas de las tareas que antes sucedían del lado del servidor. Por lo cual hoy en día los sitios web están cada vez más basados en JavaScript, y desarrollando funcionalidades más complejas en el front-end.

JavaScript comenzó siendo un lenguaje orientado a la web, y por muchos años el navegador fue su único contexto posible. Sin embargo, hoy en día se puede utilizar JavaScript para proyectos que van mas allá de los sitios web, como pueden ser aplicaciones móviles, aplicaciones de escritorio, servicios web, APIs, infraestructuras de back-end, juegos, IoT, etc.

Por lo tanto, conocer JavaScript a fondo nos va a abrir una infinidad de posibilidades en los relacionado no solo al desarrollo web, sino al mundo del desarrollo de software en general.

## JavaScript vs. Otros Lenguajes

JavaScript posee algunos elementos, características e implementaciones que difieren sensiblemente de las de otros lenguajes. Como lector, si ya has trabajado con otros lenguajes de programación, te propongo mantener una mente abierta a la hora de incorporar los conceptos en este libro, dejando de lado los preconceptos que puedas tener. Y de esta forma, permitirte entrar en el mundo de este nuevo lenguaje, que por lo demás, no tiene nada de azaroso ni excéntrico, como se suele pensar, sino que esta basado, como el resto de los lenguajes, en reglas establecidas por un estándar.

## El Estándar ECMAScript

ECMAScript es una especificación de lenguaje de programación en la que se basa JavaScript.

La mayoría de navegadores web incluyen una implementación propia del estándar ECMAScript para interpretar JavaScript. Por ejemplo, Google desarrolló su propio intérprete de JavaScript para Chrome, llamado *V8*, que es también el motor de *Node.js*. Firefox, por su parte, hizo lo propio creando *SpiderMonkey*. Y *JavaScriptCore* es la versión creada y utilizada en Safari.

Las versiones vigentes de ECMAScript que existen al momento de escribir esto son:

* 5ta Edición
* 6ta Edición - ECMAScript 2015
* 7ma Edición - ECMAScript 2016
* 8va Edición - ECMAScript 2017
* 9na Edición - ECMAScript 2018
* 10ma Edición - ECMAScript 2019

A lo largo de este libro hago referencia en diferentes momentos a ECMAScript, a veces también abreviado como ES5, ES6, ES2015, etc. Los ejemplos de código que utilizo se basan mayormente en ECMAScript 5, con la intención de trazar una línea más clara entre lo que corresponde a cada versión estándar. Y además, para reforzar la idea de que las características que introduce cada nueva versión no llegan para reemplazar a las anteriores, sino a complementarlas, a agregar nuevas posibilidades técnicas y semánticas al lenguaje.

No obstante, dedico un capítulo completo exclusivamente a las novedades más destacadas de ECMAScript 2015. En futuros volúmenes de esta colección me dedicaré a profundizar aún más sobre características más modernas del estándar.

## Requerimientos Previos

Para comprender este libro no hace falta tener conocimientos previos en programación. Es recomendable contar con alguna experiencia básica en HTML y CSS, y tener alguna práctica mínima en la creación de páginas web con estos lenguajes. De esta forma, contarás con las herramientas básicas para comenzar a crear código, y además podrás comprender mejor la interacción de JavaScript con documentos web y lo que llamamos el DOM.

## Herramientas Útiles

### Visual Studio Code

Para comenzar a crear código JavaScript podemos utilizar diferentes herramientas. La principal sería un editor de código. Uno de los más populares en el ámbito del desarrollo web, y que personalmente utilizo hoy en día es **[Visual Studio Code](https://code.visualstudio.com/)**.

### Developer Tools

Para probar los ejemplos de este libro, así como cualquier fragmentos de código JavaScript mientras aprendes el lenguaje, te recomiendo tener a mano el navegador Google Chrome, y utilizar la herramienta de desarrollo o **Developer Tools**, a la que puedes acceder presionando `CMD + OPTION + i` en MacOS, o `CTRL + SHIFT + i` en Windows. Dentro de ella utiliza la pestaña *consola* para tipear y evaluar tu código.

### RunJS

En algunas ocasiones, ciertos fragmentos de código no devolverán un valor en la consola. Para esos casos te recomiendo una herramienta llamada **[RunJS](https://runjs.dev/)** que nos permite evaluar cualquier expresión de JavaScript en tiempo real para ver su resultado de forma aun más ágil.

### Editores Online

Por último, muy buenas existen herramientas online para ejecutar nuestro código. Algunas de ellas son:

* [CodePen](https://codepen.io/)
* [CodeSandbox](https://codesandbox.io/)
* [JSBin](https://jsbin.com/)
* [StaticBlitz](https://stackblitz.com/)
