# Operadores

Ya conocemos los tipos de datos que podemos manipular en JavaScript. Lo siguiente que vamos a necesitar saber es qué hacer con esos datos.

Para esto vamos a necesitar comprender los diferentes **operadores**, que nos van a permitir precisamente realizar todo tipo de *operaciones* sobre los datos para conocerlos, compararlos, modificarlos y crear nuevos.

## Operadores Aritméticos

### Suma (+)

```javascript
3 + 4  // → 7
```

El operador `+` también puede concatenar strings.

```javascript
"Hola" + " " + "mundo"  // → "Hola mundo"
```

### Resta (-)

```javascript
5 - 2  // → 3
```

### Multiplicación (*)

```javascript
6 * 4  // → 24
```

### División (/)

```javascript
8 / 2  // → 4
```

### Módulo (%)

También llamado *resto*, Devuelve el resto de la división de dos operandos.

```javascript
9 % 4  // → 1
```

### Incremento (++)

Incrementa en una unidad al operando. Si es usado antes del operando (`++x`) devuelve el valor del operando después de añadirle `1`, y si se usa después del operando (`x++`) devuelve el valor de este antes de añadirle `1`.

```javascript
var x = 0;
var y = ++x;  // incrementa x a 1, luego devuelve 1
var z = x++;  // devuelve 1, luego incrementa x a 2
x;            // → 2
y;            // → 1
z;            // → 1
```

### Decremento (--)

Resta una unidad al operando. La posición con respecto al operando tiene el mismo comportamiento que el operador de incremento.

```javascript
var x = 2;
var y = --x;  // decrementa x a 1, luego devuelve 1
var z = x--;  // devuelve 1, luego decrementa x a 0
x;            // → 0
y;            // → 1
z;            // → 1
```

### Negación Unaria (-)

Al anteponer el signo `-`, JavaScript intenta convertir a número al operando y devolver su forma negativa.

```javascript
-"3"   // → -3
-true  // → -1
```

### Unario Positivo (+)

Al anteponer el signo `-`, JavaScript intenta convertir a número al operando.

```javascript
+"3"   // → 3
+true  // → 1
```

### Exponenciación (**)

`x ** y` devuelve `x` a la potencia `y`. Introducido en ES2016.

```javascript
2 ** 3  // → 8
```

## Operadores Relacionales

Los **operadores relacionales** comparan sus operandos y retorna un booleano como resultado.

### in

```javascript
propiedad in objeto
```

Devuelve `true` si la propiedad especificada se encuentra en el objeto.

```javascript
"PI" in Math;    // → true
"length" in [];  // → true

var automovil = { marca: "Ford" };
"marca" in automovil;   // → true
"modelo" in automovil;  // → false
```

También se utiliza en el bucle de tipo `for...in`.

```javascript
var persona = { edad: 21, sexo: "Masculino", ojos: "Marrones" };

for (atributo in persona) {
  console.log(atributo + "->" + persona[atributo]);
}

// → edad -> 21
// → sexo -> "Masculino"
// → ojos -> "Marrones"
```

### instanceof

```javascript
objeto instanceof TipoDeObjeto
```

Devuelve `true` si el objeto especificado como primer operando es del tipo especificado en el segundo operando.

```javascript
[1, 2, 3] instanceof Array;    // → true
({ a: 1 }) instanceof Object;  // → true
```

## Operadores de Comparación

Los **operadores de comparación** también pertenecen a la categoría de **operadores relacionales**.

### Igualdad (==)

```javascript
x == y
```

Devuelve `true` si ambos operandos son iguales.

```javascript
"Ariel" == "Ariel"  // → true
2 == 2              // → true
null == null        // → true
```

Dado el funcionamiento de este operador, es importante tener en cuenta estos posibles resultados:

```javascript
0 == false         // → true
2 == "2"           // → true
"" == 0            // → true
false == ""        // → true
null == undefined  // → true
```

Esto no es un error, sino que es debido al algoritmo que utiliza el operador internamente para realizar la comparación. Este tema lo abordo con más detalle en el capítulo sobre ***coerción***.

### Igualdad estricta (===)

```javascript
x === y
```

Devuelve `true` si los operandos son del mismo tipo y valor.

```javascript
"Ariel" === "Ariel"  // → true
2 === 2              // → true
null === null        // → true

0 === false   // → false
2 === "2"     // → false
"" === 0      // → false
false === ""  // → false
```

### Desigualdad (!=)

```javascript
x != y
```

Devuelve `true` si ambos operandos no son iguales.

```javascript
"Ariel" != "Fuggini"  // → true
2 != 3                // → true
null != 0             // → true
```

Tener en cuenta también que:

```javascript
0 != false         // → false
2 != "2"           // → false
"" != 0            // → false
false != ""        // → false
null != undefined  // → false
```

### Desigualdad estricta (!==)

```javascript
x !== y
```

Devuelve `true` si los operandos no son del mismo tipo y/o valor.

```javascript
"Ariel" !== "Fuggini"  // → true
2 !== 3                // → true
null !== undefined     // → true

0 !== false   // → true
2 !== "2"     // → true
"" !== 0      // → true
false !== ""  // → true
```

### Mayor que (>)

```javascript
x > y
```

Devuelve `true` si el operando de la izquierda es mayor que el operando de la derecha.

### Mayor o igual que (>=)

```javascript
x >= y
```

Devuelve `true` si el operando de la izquierda es mayor o igual que el operando de la derecha.

### Menor que (<)

```javascript
x < y
```

Devuelve `true` si el operando de la izquierda es menor que el operando de la derecha.

### Menor o igual que (<=)

```javascript
x <= y
```

Devuelve `true` si el operando de la izquierda es menor o igual que el operando de la derecha.

## Operadores de Asignación

### Asignación (=)

```javascript
x = y
```

Con `x = y` estamos diciendo que la variable `x` es igual al valor de `y`.

```javascript
x = "JS";
y = 43;
z = y;
```

### Asignación de adición (+=)

```javascript
x += y
```

Equivale a `x = x + y`.

### Asignación de sustracción (-=)

```javascript
x -= y
```

Equivale a `x = x - y`.

### Asignación de multiplicación (*=)

```javascript
x *= y
```

Equivale a `x = x * y`.

### Asignación de división (/=)

```javascript
x /= y
```

Equivale a `x = x / y`.

### Asignación de resto (%=)

```javascript
x %= y
```

Equivale a `x = x % y`.

### Asignación de exponenciación (**=)

```javascript
x **= y
```

Equivale a `x = x ** y`. Introducido en ES2016.

## Operadores Lógicos

### AND (&&)

El valor producido por `&&` no es necesariamente de tipo boolean, sino que es siempre el valor de uno de sus dos operandos.

```javascript
x && y
```

Si `x` es un valor falso (*falsy*), devuelve `x`. Si no, devuelve `y`.

```javascript
true && true;       // → true
true && false;      // → false
false && true;      // → false
"Perro" && "Gato";  // → "Gato"

var debug = true;
debug && console.log("Debug ON");  // → "Debug ON"
```

### OR (||)

El valor producido por `||` no es necesariamente de tipo boolean, sino que es siempre el valor de uno de sus dos operandos.

```javascript
x || y
```

Si `x` es un valor verdadero (*truthy*), devuelve `x`. Si no, devuelve `y`.

```javascript
true || true;       // → true
true || false;      // → true
false || true;      // → true
"Perro" || "Gato";  // → "Perro"

var x = false;
x || console.log("Dev");  // → "Dev"
```

### NOT (!)

```javascript
!x
```

Devuelve un booleano contrario al valor del operando. Si el operando es verdadero, devuelve `false`. De lo contrario, devuelve `true`.

```javascript
!true       // → false
!false      // → true
!"Perro"    // → false
!0          // → true
!1          // → false
!undefined  // → true
!null       // → true
![]         // → false
!{}         // → false
```

Se suele utilizar también como `!!`, que no es más que dos negaciones consecutivas, logrando el resultado exactamente opuesto, es decir, convertir el operando a su versión booleana.

```javascript
!!true       // → true
!!false      // → false
!!"Perro"    // → true
!!0          // → false
!!1          // → true
!!undefined  // → false
!!null       // → false
!![]         // → true
!!{}         // → true
```

## Operador Condicional Ternario

```javascript
condicion ? valor1 : valor2
```

Si la condición es verdadera, devuelve `valor1`, de lo contrario devuelve `valor2`.

```javascript
function obtenerEstado (edad) {
  return (edad < 18) ? "menor" : "adulto";
}

obtenerEstado(14);  // → "menor"
obtenerEstado(32);  // → "adulto"
```

## Operadores Unarios

### typeof

```javascript
typeof operando
typeof (operando)
```

Devuelve una string indicando el tipo del operando evaluado. Los paréntesis son opcionales.

El resultado de la operación es siempre un string.

```javascript
typeof "Hola mundo"  // → "string"
typeof 39548         // → "number"
typeof true          // → "boolean"
typeof false         // → "boolean"
typeof {}            // → "object"
typeof []            // → "object"
typeof null          // → "object"
typeof Date          // → "object"
typeof Math.round    // → "function"
typeof BigInt(23)    // → "bigint"
typeof Symbol()      // → "symbol"
typeof noExiste      // → "undefined"
```

### void

```javascript
void expresion
void (expresion)
```

Previene que una expresión devuelva un valor. Los paréntesis son opcionales.

Su uso es poco frecuente, y se utiliza muchas veces para ejecutar una expresión en JavaScript desde un link HTML sin provocar efectos secundarios.

```html
<a href="javascript:void(0)">
  Este link no hace nada
</a>

<a href="javascript:void(unaFuncion())">
  Este link ejecuta unaFuncion()
</a>
```

### delete

```javascript
delete objeto.propiedad
delete array[indice]
```

Elimina una propiedad de un objeto o un elemento de un array. Como resultado devuelve un booleano indicando si la operación se realizó con éxito.

```javascript
var miObjeto = { x: 1, y: 2 };
var miArray = ["gato", "perro", "conejo"];

delete miObjeto.x;
// → true
// (la propiedad x se ha eliminado)

delete miObjeto;
// → false
// (no puede eliminar un objeto)

delete Math.PI;
// → false
// (no puede eliminar propiedades predefinidas de un objeto global)

delete miArray[2];
// → true
// (el valor "conejo" fue eliminado)

miArray[2];  // → undefined
```

## Operador Coma

El operador coma (`,`) evalúa dos operandos y retorna el valor del último.

Este operador se utiliza principalmente dentro de un bucle `for`, permitiendo declarar múltiples variables y evaluarlas en cada iteración.

```javascript
for (var i = 0, j = 10; i < j; i++, j--) {
  console.log(array[i][j]);
}
```

Además, también se puede utilizar para declarar múltiples variables en una misma expresión.

```javascript
var a, b, c;

var d = 0,
    f = true,
    f = "Usuario";
```
