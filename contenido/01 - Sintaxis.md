# Terminología y Sintaxis

## Literales

Un **literal** es un valor exacto, representado por una sintaxis específica. En otras palabras, la forma de escribir *literalmente* un valor.

```javascript
1024              // literal de number
"Hola mundo"      // literal de string
[0, 2, 4]         // literal de array
{ clave: valor }  // literal de object
true              // literal de boolean
```

En contraste, un valor no es literal cuando lo creamos por medio de constructos como pueden ser funciones o clases.

```javascript
Number(1024)
String("Hola mundo")
Object({ clave: valor })o
Array(0, 2, 4)
Boolean(true)
```

## Expresiones y Sentencias

Una **expresión** (en inglés *expression*) es una unidad de código que JavaScript evalúa, y devuelve a partir de ella un valor único.

Estas son algunas de las expresiones *primarias* de JavaScript:

```javascript
2.14
true
undefined
this
function
class
/[a-z0-9]/g     // expresión regular
i               // variable
4 / 2           // expresión aritmética
"Hola" + " mundo"  // expresión de string
x && y          // expresión lógica
function () {}  // expresión de declaración de función
new Object()    // expresión de declaración de objeto
```

Una **sentencia** (en inglés *statement*) es una unidad más compleja de código. Puede estar compuesta por una o más líneas, y contener múltiples expresiones.

```javascript
// sentencias de declaración
var x = 0;
let y = true;
const z = "";

// sentencia condicional
if (condicion) {
  // bloque de código
}

// sentencia de iteración
while (condicion) {
  // bloque de código
}

return valor;  // sentencia return
```

Para finalizar una sentencia y separarla del resto se utiliza el punto y coma (`;`).

## Uso de Punto y Coma

De acuerdo con el estándar ECMAScript, es recomendable finalizar cada línea de nuestro código JavaScript con punto y coma (`;`).

Sin embargo, esto no es estrictamente necesario en JavaScript, y el código funciona igual sin ellos. Y es que JavaScript, en la mayoría de los casos, los agrega internamente de forma automática cuando es requerido.

Personalmente tiendo a no utilizar punto y coma en mi código, excepto que trabaje sobre código existente que ya lo usa. Esto es una decisión personal, ya que considero que el código se ve más limpio de esta forma.

Sin embargo, mientras estés en etapa de aprendizaje, **te recomiendo utilizar punto y coma en todos los casos** para evitar errores en tu código.

## Comentarios

En JavaScript podemos utilizar una sintaxis especial para escribir comentarios entrelazados con nuestro código, sin que afecten la ejecución normal del mismo.

Los comentarios son útiles para colocar notas sobre la intención de un determinado bloque de código o para escribir primero nuestras ideas y luego transformarlas una a una en código, entre otros usos posibles.

En los ejemplos de código de este libro aparecerán muchas veces comentarios que representan el resultado de una expresión de JavaScript, o simplemente alguna nota sobre el código mismo.

```javascript
// Doble barra para comentarios de una línea

/*
  Barra y asterísco para comentarios
  que ocupan múltiples líneas.
*/

/***
 * Puedes crear cualquier otra variante
 * de los dos anteriores para generar
 * comentarios con mejor estilo visual.
 */
```
