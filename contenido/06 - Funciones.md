# Funciones

Una **función** es un bloque de código capaz de realizar una o más tareas, y luego devolver un valor como resultado.

En JavaScript, las funciones también son un tipo de **objeto**.

```javascript
// declara una función `sumar`
// que retorna la operación 2 + 2
function sumar () {
  return 2 + 2;
}
```

La sentencia `return` es la que indica qué valor devolverá la función. Es opcional, y cuando no se especifica un valor de retorno, la función devuelve `undefined`.

El código dentro de una función es ejecutado una vez que la función es invocada, utilizando su nombre de identificador seguido de `()`.

```javascript
sumar();  // → 4
```

Este ejemplo nos muestra una función que suma `2 + 2`, y nos retorna el resultado.

En la práctica, esto no sería muy util, ya que si quisiéramos por ejemplo realizar la operación suma sobre otros valores, tendríamos que crear una nueva función para cada combinación posible.

Para resolver esto, las funciones aceptan *parámetros*.

## Parámetros y Argumentos

Para hacerla mas dinámicas, las funciones aceptan **argumentos**, que son valores que podemos pasarle a la función al invocarla con los `()`.

Para determinar qué argumentos acepta una función, al momento de declararla le definimos **parámetros**, entre los paréntesis y separados por `,`:

```javascript
function miFuncion (parametro1, parametro2, parametro3) {
  // contenido de la función
}
```

Veamos cómo podría quedar nuestra función `sumar()` al agregarle parámetros:

```javascript
function sumar (a, b) {
  return a + b;
}
```

Los argumentos quedan disponibles como variables dentro del ámbito de la función. Ahora, nuestra función `sumar()` recibe dos argumentos que serán los operandos de la suma, y por lo tanto es mucho más versátil que su versión anterior. Por ejemplo:

```javascript
sumar(4, 3);            // → 7
sumar(100.51, 3.1415);  // → 103.6515
```

A> Los términos **parámetro** y **argumento** suelen ser confundidos y utilizados indistintamente, lo cual es un error. Recuerda que el **parámetro** es el nombre que definimos dentro de los paréntesis al declarar la función, la *etiqueta*. Y el **argumento** es el valor que recibe un parámetro al invocarse la función.

Una función puede definir 0 o más parámetros, y aceptar 0 o más argumentos. Además puede no ser necesario pasarle a una función valores para todos sus parámetros, pero sí es importante el orden en que se los pasemos, que debe corresponder con el orden establecido al declarar la función.

También es posible pasarle argumentos a una función que no declarar ningún parámetro, ya que los argumentos son accesibles dentro del ámbito de la función en el objeto `arguments`.

Por ejemplo, nuestra función sumar podría declararse sin parámetros de la siguiente manera:

```javascript
function sumar () {
  return arguments[0] + arguments[1];
}

sumar(6, 3);  // → 9
```
