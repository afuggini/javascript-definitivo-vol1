# Temporizadores

En JavaScript contamos con dos métodos globales que nos permiten llamar a una función luego de un tiempo determinado.

## setTimeout()

```javascript
setTimeout(funcion, delay, ...argumentos)
```

El método global `setTimeout()` recibe como primer argumento la función a llamar o una referencia a ella.

El segundo argumento representa el *delay* o tiempo de espera hasta llamar a la función, expresado en milisegundos.

Y, opcionalmente, podemos pasarle tantos argumentos como querramos que reciba a la función.

```javascript
function suma (a, b) {
  console.log(a + b);
}

var temporizador = setTimeout(suma, 2000, "Java", "Script");

// 2 segundos (2000 ms) después...
// -> "JavaScript"
```

Si deseamos cancelar la llamada a la función antes de los 2000 ms, podemos hacerlo utilizando el método global `clearTimeout()` pasándole como argumento la referencia al temporizador.

```javascript
clearTimeout(temporizador);
```

## setInterval()

El método global `setInterval()` funciona de la misma forma que `setInterval()`, con la única diferencia que la función se sigue llamando indefinidamente en los intervalos indicados, hasta que la detengamos o cerremos la ventana del navegador.

```javascript
setInterval(funcion, delay, ...argumentos)
```

Por ejemplo:

```javascript
function suma (a, b) {
  console.log(a + b);
}

var intervalo = setInterval(suma, 2000, "Java", "Script");

// 2 segundos (2000ms) después...
// -> "JavaScript"

// 2 segundos (2000ms) después...
// -> "JavaScript"

// 2 segundos (2000ms) después...
// -> "JavaScript"

// ...
```

Para interrumpir el intervalo, utilizamos el método global `clearInterval()`.

```javascript
clearInterval(intervalo);
```
