# Números

En JavaScript gran parte del trabajo con números es posible gracias a los operadores. Sin embargo, también contamos con una serie de objetos y funciones con los cuales manipular números.

## Number()

La función global `Number()` nos permite crear valores de tipo `number` a partir de cualquier valor.

```javascript
Number(23)              // → 23
Number(3.14)            // → 3.14
Number("23")            // → 23
Number("3.14")          // → 3.14
Number(true)            // → 1
Number(false)           // → 0
Number(null)            // → 0
Number(undefined)       // → NaN
Number([])              // → 0
Number([0])             // → 0
Number([1])             // → 1
Number([2, 3, 4])       // → NaN
Number({})              // → NaN
Number({ a: 1, b: 2 })  // → NaN
```

A> Para conocer en mayor profundidad las posibilidades que nos da `Number` puedes visitar [este link](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Number).

## Métodos de Number

### parseInt()

El método global `parseInt()` recibe un string y lo convierte en un número entero. Es también accesible como método del objeto global `Number`.

Si el valor no puede ser convertido, retorna `NaN`.

```javascript
parseInt("10");               // → 10
parseInt("10.83");            // → 10
parseInt("10 20 30");         // → 10
Number.parseInt("10 años");   // → 10
Number.parseInt("Messi 10");  // → NaN
```

### parseFloat()

El método global `parseFloat()` recibe un string y lo convierte en un número decimal o *de punto flotante*. Es también accesible como método del objeto global `Number`.

Si el valor no puede ser convertido, retorna `NaN`.

```javascript
parseFloat("3.14");               // → 3.14
parseFloat("314e-2");             // → 3.14
parseFloat("0.0314E+2");          // → 3.14
Number.parseFloat("3.14 es PI");  // → 3.14
Number.parseFloat("PI es 3.14");  // → NaN
```

### toFixed()

El método `toFixed()` devuelve un string del número con la cantidad de decimales especificada como parámetro.

```javascript
var PI = 3.1415;
PI.toFixed(2);  // → "3.14"
PI.toFixed(3);  // → "3.141"
PI.toFixed(0);  // → "3"
PI.toFixed();   // → "3"
```

## NaN

`NaN` es una propiedad global de JavaScript. Comúnmente se dice que `NaN` no es un número, ya que si nombre proviene de *Not-a-Number"* (No-Numero). Sin embargo, si verificamos su valor mediante el operador `typeof`, veremos que en JavaScript, ([por especificación del estándar ECMAScript](https://tc39.es/ecma262/#sec-terms-and-definitions-nan)) `NaN` es un valor numérico:

```javascript
typeof NaN  // → "number"
```

Por lo tanto, es más apropiado considerar a `NaN` como un número, y más precisamente, un **número inválido**.

Muchos métodos de JavaScript retornan `NaN` cuando no pueden parsear sus parámetros como números válidos.

```javascript
Number(23 + {})                   // → NaN
parseInt(10 / 0)                  // → NaN
parseFloat(20 * "no soy numero")  // → NaN
43 - "veinte"                     // → NaN
```

`NaN` nunca equivale a ningún otro número, incluido `NaN`.

```javascript
NaN == NaN   // → false
NaN === NaN  // → false
```

Una de las formas en que podemos chequear si un valor es `NaN` es usando la función global `isNaN()`, que devuelve un booleano según si el argumento que recibe es o no `NaN`.

```javascript
isNaN(NaN)  // → true
isNaN(1)    // → false
```

Sin embargo, esta función también tiene ciertos *corner cases*, es decir casos en los que no resulto como se esperaría:

```javascript
isNaN()           // → true
isNaN("Ariel")    // → true
isNaN(undefined)  // → true
```

Esto es debido a que los valores no numéricos que recibe `isNaN()` son coercionados al tipo number antes de ser evaluados. Entonces, dado que cualquier string o `undefined` al ser forzados a number devuelven `NaN`, `isNaN(NaN)` siempre devuelve `true`.

```javascript
Number(undefined)  // → NaN
Number("Ariel")    // → NaN

// por lo tanto

isNaN(Number(undefined))  // → true
isNaN(Number("Ariel"))    // → true
```

Tanto `NaN` como `isNaN()` también son accesibles como `Number.NaN` y `Number.isNaN()`.

```javascript
var numeroInvalido = parseInt(2 / 0);  // → NaN
Number.isNaN(numeroInvalido);          // → true

Number.isNaN(Number.NaN);  // → true
```

## Infinity

`Infinity` es una propiedad global. En el navegador, las propiedades globales pertenecen al objeto `window`. Por lo tanto también es posible referirnos a `Infinity` como `window.Infinity`.

`Infinity` se comporta como el infinito matemático: cualquier numero multiplicado por `Infinity` da como resultado `Infinity`, mientras que dividir cualquier numero por `Infinity` resulta `0`.

```javascript
6 * Infinity  // → Infinity
8 / Infinity  // → 0
```

También existe en su forma negativa: `-Infinity`.

## Math

El objeto global `Math` cuenta con múltiples propiedades y métodos útiles para realizar operaciones matemáticas. A continuación veremos algunos de los más destacados.

A> Para una referencia completa del objeto `Math` puedes visitar [este link](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Math).

### Math.E

Devuelve el valor matemático E.

```javascript
Math.E  // → 2.718281828459045
```

### Math.PI

Devuelve el valor matemático PI.

```javascript
Math.PI  // → 3.141592653589793
```

### Math.round()

Redondea un número hacia el entero más próximo.

```javascript
Math.round(3.14)  // → 3
Math.round(5.79)  // → 6
Math.round(7.5)   // → 8
```

### Math.ceil()

Redondea un número hacia arriba, hacia el entero más próximo.

```javascript
Math.ceil(82)      // → 82
Math.ceil(2.02)    // → 3
Math.ceil(4.001)   // → 5
Math.ceil(-4.001)  // → -4
```

### Math.floor()

Redondea un número hacia abajo, hacia el entero más próximo.

```javascript
Math.floor(82)      // → 82
Math.floor(2.02)    // → 2
Math.floor(4.001)   // → 4
Math.floor(-4.001)  // → -5
```

### Math.pow()

`Math.pow(x, y)` retorna el valor de `x` a la potencia `y`.

```javascript
Math.pow(8, 3)  // → 512
```

### Math.sqrt()

Retorna la raíz cuadrada de un número.

```javascript
Math.sqrt(64)  // → 8
```

### Math.random()

Retorna un número aleatorio, mayor o igual a `0` y menor a `1`.

```javascript
Math.random()  // → 0.784405114211054
Math.random()  // → 0.81548726640262
Math.random()  // → 0.81548726640262
Math.random()  // → 0.07392369524727838
```

Si quisiéramos retornar un número entero dentro de un rango, debemos crear una función como la siguiente, empleando `Math.random()`:

```javascript
function enteroAlAzar (min, max) {
  return Math.floor(Math.random() * (max - min) + min);
}

// devuelve un entero mayor o igual a `0` y menor a `10`.
enteroAlAzar(0, 10);  // → 9
enteroAlAzar(0, 10);  // → 0
enteroAlAzar(0, 10);  // → 7
enteroAlAzar(0, 10);  // → 5
```
