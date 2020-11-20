# Control de Flujo

El **control de flujo** (*Control flow*) es, en ciertos lenguajes de programación como en JavaScript, el orden en que son ejecutadas las instrucciones en el código.

El código JavaScript se ejecuta, a grandes rasgos, en un orden líneal, desde la primera línea de código hasta la última. Sin embargo, este orden se altera cuando el intérprete (el navegador) encuentra un bloque de código que cambia el flujo.

A los bloques de código que tienen la capacidad de alterar el flujo de ejecución de nuestro código JavaScript se les conoce como **estructuras de control**.

A continuación te explico las diferentes estructuras de control que existen en el lenguaje.

## Sentencia de bloque

La **sentencia de bloque** es una estructuras sencilla, que se utiliza simplemente para agrupar declaraciones, y no modifica el flujo de ejecución.

```javascript
{
  var mascota = "Perro";
  console.log("Mi mascota es " + mascota);
}
```

## Sentencia condicional

La **sentencia condicional** se utilizan para ejecutar un bloque de código únicamente si se cumple cierta condición.

```javascript
// si una condición es verdadera...
if (condicion) {

  // entonces ejecuta el código aquí dentro

}
```

Por ejemplo:

```javascript
if (edad >= 18) {
  console.log("Eres mayor de edad");
} else {
  console.log("Eres menor de edad");
}
```

```javascript
if (
  diaDeLaSemana === "sabado"
  || diaDeLaSemana === "domingo"
) {
  descansar();
} else if (diaDeLaSemana === "viernes") {
  prepararseParaElFinDeSemana();
} else {
  trabajar();
}
```

## Sentencias de iteración

Las **sentencias de iteración**, también llamadas *bucles* o *loops*, se utilizan para ejecutar un bloque de código de forma reiterativa, y basada en alguna condición.

JavaScript cuenta con varias estructuras de este tipo.

### while

La **sentencia while** itera sobre un bloque de código continuamente mientras la condición indicada sea verdadera.

```javascript
var i = 5;

while (i > 0) {
  console.log("i es igual a " + i);
  i--;
}

// → "i es igual a 5"
// → "i es igual a 4"
// → "i es igual a 3"
// → "i es igual a 2"
// → "i es igual a 1"
```

### do … while

La **sentencia do...while** funciona igual que **while**, pero con la diferencia de que el bloque de código se ejecuta al menos una vez, independientemente del valor de la condición.

El siguiente código obtiene el mismo resultado que `while`.

```javascript
var i = 5;

do {
  console.log("i es igual a " + i);
   i--;
} while (i > 0);

// → "i es igual a 5"
// → "i es igual a 4"
// → "i es igual a 3"
// → "i es igual a 2"
// → "i es igual a 1"
```

```javascript
do {
  console.log("Me veras solo una vez");
} while (true === false);

// → "Me veras solo una vez"
```

### for

La **sentencia for** recibe tres argumentos que determinan la forma de iteración del bloque de código.

* Una **expresión inicial** que se ejecuta una sola vez, antes de la primer iteración;
* Una **condición** que debe cumplirse para ejecutar el bloque de código;
* Una **expresión final** que se ejecuta al final de cada iteración;

Por lo tanto, el bucle va a iterar sobre el bloque de código tantas veces como se cumpla la condición, y teniendo disponible dentro de su contexto los valores de las expresiones inicial y final.

```javascript
for (expresionInicial; condicion; expresionFinal) {
  // código a ejecutar
}
```

```javascript
for (var i = 1; i <= 5; i++) {
  console.log("vuelta " + i);
}

// → "vuelta 1"
// → "vuelta 2"
// → "vuelta 3"
// → "vuelta 4"
// → "vuelta 5"
```

Aunque no es su único uso, es común el uso del bucle `for` para iterar sobre arrays, escrito de la siguiente forma:

```javascript
var array = [1, 3, 5, 7, 9];

for (var i = 0; i < array.length; i++) {
  console.log("El valor es: " + array[i]);
}

// → "El valor es: 1"
// → "El valor es: 3"
// → "El valor es: 5"
// → "El valor es: 7"
// → "El valor es: 9"
```

### for … in

La **sentencia for...in** itera sobre los elementos de un objeto en un orden arbitrario, ejecutando el bloque de código una vez por cada uno.

El valor a la izquierda de `in` representa el nombre de la propiedad del objeto correspondiente a la iteración en curso.

```javascript
var automovil = {
  marca: "Audi",
  modelo: "A1",
  año: 2020
}

for (var dato in automovil) {
  console.log(dato + " es " + automovil[dato]);
}

// → "marca es Audi"
// → "modelo es A1"
// → "año es 2020"
```

## Sentencia switch

La **sentencia switch** evalúa una expresión, comparando su valor con otro valor llamado `case`. Cuando los valores coinciden, se ejecuta el código comprendido desde el `case` hasta el final del bloque `switch`, o hasta encontrar una sentencia `break`.

Si ninguno de los `case` coincide con la expresión evaluada, se buscará una sentencia `default`, y si esta presente, se ejecutará el código que le sigue.

```javascript
var ahora = new Date();

// obtiene el número de día
// de la semana, de 0 a 6
var diaDeLaSemana = ahora.getDay();

switch (diaDeLaSemana) {
  case 0:
    console.log("Domingo");
    break;
  case 1:
    console.log("Lunes");
    break;
  case 2:
    console.log("Martes");
    break;
  case 3:
    console.log("Miércoles");
    break;
  case 4:
    console.log("Jueves");
    break;
  case 5:
    console.log("Viernes");
    break;
  case 6:
    console.log("Sábado");
    break;
  default:
    console.log("Día inexistente");
}
```

## Sentencia break

La **sentencia break** interrumpe abruptamente la ejecución de un **bloque**, **sentencia de iteración** o **sentencia switch**.

```javascript
// dado un bucle `for...in`
for (var x in objeto) {

  // si se cumple cierta condición...
  if (x === "modelo") {

    // interrumpir el bucle `for`
    break;
  }
}
```

## Sentencia continue

La **sentencia continue** interrumpe la iteración en curso, y hace que se *continúe* con la siguiente.

```javascript
var automovil = {
  marca: "Audi",
  modelo: "A1",
  año: 2020
}

for (var dato in automovil) {
  if (dato == "modelo") {
    continue;
  } else {
    console.log(dato + " es " + automovil[dato]);
  }
}

// → "marca es Audi"
// → "año es 2020"
```
