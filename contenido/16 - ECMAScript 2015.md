# ECMAScript 2015

ECMAScript 2015, también conocido como ES2015 o ES6, es posiblemente la versión de este estándar que introdujo las novedades más significativas al lenguaje.

Existe la idea de que algunas de las nuevas características que introduce cada nueva versión de ECMAScript llegan para reemplazar características anteriores. Particularmente dos de las características de ES2015, la ***función flecha***, y las nuevas palabras clave `let` y `const`.

Y entonces es fácil caer en la tentación de limitarse exclusivamente a utilizar, por ejemplo, la sintaxis de ***función flecha***, y olvidarse para siempre de la palabra clave `function`. O apresurarse a realizar una búsqueda de la palabra `var` en nuestro viejo código, y sin más, reemplazar cada coincidencia por `let`.

Esto sería sencillamente un grave error. Tanto la ***función flecha***, como `let` y `const`, no son mejores que sus antecesoras, sino diferentes. Como anticipé en la introducción, en ECMAScript **lo nuevo no necesariamente viene a reemplazar a lo viejo**.

En lugar de eso, debemos evitar apresurarnos a elegir la novedad sin previo análisis, y tomarnos el tiempo para conocer con la mayor profundidad posible cada una de las nuevas características, tomándolas como **herramientas** adicionales de las que disponemos para utilizar a conciencia, y en muchas ocasiones, en conjunto con las anteriores.

## let y const

Las palabras clave `let` y `const` nos sirven para declarar variables variables, similar a `var`, pero con algunas diferencias importantes.

La primera diferencia radica en su ámbito de alcance. Mientras que el ámbito de las variables declaradas con `var` lo define la función, el ámbito de `let` y `const` es a nivel de bloque. Esto incluye tanto funciones, como cualquier sentencia de las que explicamos en la sección ***Control de flujo***:

* Sentencias bloque
* Sentencias condicionales
* Sentencias de iteración
* Sentencias switch

Veámoslo a través del siguiente ejemplo:

```javascript
function miFuncion () {
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }

  a;  // → 1
  b;  // → undefined
  c;  // → undefined
}

miFuncion();
// → ReferenceError: b is not defined
```

En este fragmento, `a` al ser declarada con `var` queda disponible dentro del ámbito de la función que la contiene, `miFuncion()`. Sin embargo, el alcance de `b` y `c`, al estar declaradas con `let` y `const`,respectivamente, queda limitado al ámbito del bloque condicional `if`.

Por lo cual, al invocar a la función `miFuncion()`, cuando intentamos obtener el valor de `b` y `c` fuera del condicional, lo que recibimos es un error de tipo `ReferenceError` anunciando que `b` no ha sido definida.

La segunda diferencia con `var` es la capacidad de ser redeclaradas. Mientras que `var` permite volver a declarar variables existentes con el mismo nombre, tanto `let` como `const` solo pueden declararse una vez.

```javascript
var a = false;
let b = 1;
const c = null;

// ...

var a = true;
a;  // → true

// todas las siguientes provocan `SyntaxError`
var b = 2;
var c = "";
let a = false;
let b = 2;
let c = {};
const a = [];
const b = 3;
const c = undefined;
```

La tercer distinción tiene que ver con la posibilidad de reasignar el valor de la variable. Tanto `var` como `let` permiten ser reasignadas a lo largo de nuestro código, es decir, pueden cambiar su valor. Sin embargo, una variable `const` debe obligatoriamente recibir un valor al ser declarada, y no podrá cambiar de valor.

```javascript
var a = 1;
a = true;
a;  // → true

let b = 2;
b = false;
b;  // → false

const c = 3;
c = {};
// → TypeError: Assignment to constant variable.
```

En la siguiente tabla comparativa podemos ver las principales características de las diferentes palabras claves.

| Palabra Clave | Ámbito  | Reasignable | Redeclarable |
|---------------|---------|-------------|--------------|
| ***var***     | Función | Si          | Si           |
| ***let***     | Bloque  | Si          | No           |
| ***const***   | Bloque  | No          | No           |

### const ≠ constante

Es importante tener en cuenta que, si bien el nombre sugiere que `const` nos permite crear *constantes*, es decir, valores inmutables, en realidad esto no es preciso.

Veamos un ejemplo:

```javascript
// creamos un objeto
const objeto = { a: 1, b: 2 };

// le agregamos una nueva propiedad
objeto.c = 3;

// el objeto fue mutado
objeto;  // → { a: 1, b: 2, c: 3 };
```

Como vemos, aunque usemos `const`, logramos mutar el objeto agregándole una propiedad nueva. Con lo cual, considerar `const` una *constante* es engañoso. En lugar de eso, debemos limitarnos a definir las variables `const` simplemente como *variables no reasignables*.

## Función Flecha

La ***función flecha*** consiste en una nueva sintaxis para declarar una función.

Veamos algunos ejemplos. Estas son algunas formas de declarar una función "clásica":

```javascript
function saludar (nombre) {
  return "Hola " + nombre;
}

// o bien

var saludar = function (nombre) {
  return "Hola " + nombre;
}
```

La misma función con la nueva sintaxis se vería así:

```javascript
let saludar = (nombre) => {
  return "Hola " + nombre;
}

// o bien

let saludar = nombre => "Hola " + nombre;
```

Como vemos, en los casos en que la función flecha consiste en una sola sentencia, esta puede ser declarada en una sola línea.

Por otra parte, si la función tiene un solo parámetro, los paréntesis pasan a ser opcionales.

La función flecha se vuelven muy útil para trabajar con *funciones de orden superior*, es decir las que toman como parámetro una función, y/o retornan una función como resultado.

La sintaxis de la función flecha se vuelve entonces especialmente sintética en estos casos:

```javascript
// función clásica
function sumar (a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    }
  }
}

// función flecha
const sumar = a => b => c => a + b + c;

// ambas se invocan de la misma forma
sumar(2)(3)(6);  // → 11
```

## Plantillas de Cadena de Texto

La **plantilla de cadena de texto**, o bien *plantilla de string* o *literal de plantilla* es una nueva sintaxis para literales de texto. Una de sus principales características es la posibilidad de incrustar expresiones dentro de ellas.

```javascript
// ES5
var texto = "El " + animal + " es de color " + color;
var suma = "El resultado es " + (2 + 3);

// ES6
let texto = `El ${animal} es de color ${color}`;
let suma = `El resultado es ${2 + 3}`;
```

Por otra parte, a diferencia de los string ES5, las nuevas líneas son parte de la cadena de texto.

```javascript
// ES5
var texto = "Esto es un texto que se\n
extiende múltiples líneas sin\n
necesidad de caracteres especiales";

// ES6
let texto = `Esto es un texto que se
extiende múltiples líneas sin
necesidad de caracteres especiales`;
```

## Propiedades Abreviadas de Objeto

Otra de las novedades de ES2015 es la posibilidad de abreviar los literales de objeto, cuando podemos asociar las propiedades de un objeto a variables del mismo nombre.

```javascript
// ES5
function crearObjeto (color, ancho, alto) {
  return {
    color: color,
    ancho: ancho,
    alto: alto
  };
}

// ES2015
function crearObjeto (color, ancho, alto) {
  return { color, ancho, alto };
}

crearObjeto("red", "140px", "60px");
// → {
// →   color: "red",
// →   ancho: "140px",
// →   alto: "60px"
// → }
```

## Desestructuración

La **desestructuración** (*destructuring*) nos permite crear variables fácilmente a partir de un objeto.

```javascript
var persona = {
  nombre: "Ariel",
  edad: 34,
  sexo: "Masculino"
}

// ES5
var nombre = persona.nombre;
var edad = persona.edad;
var sexo = persona.sexo;

// ES2015
let { nombre, edad, sexo } = persona;

nombre;  // → "Ariel"
edad;    // → 34
sexo;    // → "Masculina"
```

Esto también funciona con los arrays:

```javascript
let dias = ["lunes", "martes", "miercoles"];
let [primero, segundo, tercero] = dias;

primero;  // → "lunes"
segundo;  // → "martes"
tercero;  // → "miercoles"

// también es posible omitir valores
let [primero,, tercero] = dias;

primero;  // → "lunes"
tercero;  // → "miercoles"
```

En el caso que tengamos objetos o arrays anidados, la desestructuración se vería asi:

```javascript
let libro = {
  titulo: "JavaScript Definitivo",
  autor: {
    nombre: "Ariel",
    apellido: "Fuggini"
  }
}

let { titulo, autor: { nombre, apellido } } = libro;

titulo;    // → "JavaScript Definitivo"
nombre;    // → "Ariel"
apellido;  // → "Fuggini"
```

```javascript
let dias = [31, 28, [31, 30]];
let [enero, febrero, [marzo, abril]] = dias;

enero;    // → 31
febrero;  // → 28
marzo;    // → 31
abril;    // → 30
```

## Operador de Propagación

El **operador de propagación** (*spread operator*) permite expandir arrays y objetos, en lugares donde se esperan otros valores, como pueden ser otros arrays u objetos, o argumentos de funciones.

```javascript
let array1 = [1, 2, 3];
let array2 = [...array1, 4, 5];

array2;  // → [1, 2, 3, 4, 5]

let objeto1 = { x: 1, y: 2 };
let objeto2 = { ...objeto1, z: 3 };

objeto2;  // → { x: 1, y: 2, z: 3 };

const sumar = (x, y, z) => x + y + z;

sumar(...array1); // → 6
// equivale a sumar(1, 2, 3);
```

Ese sencillo operador nos permite algunos usos bastante prácticos:

### Clonar un array

```javascript
var array1 = [1, 2, 3];

// ES5
var array2 = array1.splice();

// ES6
var array2 = [...array1];
```

### Concatenar arrays

```javascript
var array1 = [1, 2, 3];
var array2 = [4, 5, 6];

// ES5
var array3 = array1.concat(array2);

// ES6
var array3 = [...array1, ...array2];
```

### Clonar un objeto

```javascript
var objeto1 = { a: 1, b: 2, c: 3 };

// ES5
function clonar (objeto) {
  var copia = objeto.constructor();
  for (var propiedad in objeto) {
    if (objeto.hasOwnProperty(propiedad)) {
      copia[propiedad] = objeto[propiedad];
    }
  }
  return copia;
}
var objeto2 = clonar(objeto1);

// ES6
var objeto2 = { ...objeto1 };
```

### Concatenar objetos

```javascript
var objeto1 = { a: 1, b: 2 };
var objeto2 = { c: 3 };

// ES5
// Requiere crear otra función

// ES6
var objeto3 = { ...objeto1, ...objeto2 };
```

## Parámetro Resto

El **parámetro resto** nos permite transformar un número indefinido de parámetros de función en un array.

```javascript
const prueba = (a, b, ...resto) => {
  console.log(a);
  console.log(b);
  console.log(resto);
}

prueba(1, 2, 3, 4, 5);
// → 1
// → 2
// → [3, 4, 5]
```

## Parámetros por Defecto

ES2015 nos permite asignarle a los parámetros de una función un valor por defecto, que será utilizado en los casos en que al invocar la función el parámetro no reciba un valor, o bien reciba `undefined`.

```javascript
function suma (a = 0, b = 0) {
  return a + b;
}

suma(1, 2);          // → 3 (1 + 2)
suma(1);             // → 1 (1 + 0)
suma();              // → 0 (0 + 0)
suma(4, undefined);  // → 4 (4 + 0)
```
