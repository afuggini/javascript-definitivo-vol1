# Booleanos

Un **boolean** es un dato binario, es decir, tiene solo dos valores posibles, `true` y `false`.

El tipo booleano es util cuando en nuestro código necesitamos distinguir entre dos posibilidades, por ejemplo:

* verdadero / falso
* prendido / apagado
* si / no

Como vimos, ciertos operadores arrojan como resultado un valor booleano.

```javascript
0 == "0"  // → true
0 === 1   // → false
0 != "1"  // → true
0 !== 1   // → true
0 < 1     // → true
0 >= 1    // → false
!0        // → true
```

## Valores Truthy y Falsy

En los contextos en que un valor booleano es lo esperado, y se utiliza en su lugar un valor que diferente tipo, JavaScript lo fuerza de manera implícita a comportarse como booleano.

Los valores convertibles a `false` se conocen como *falsy* o *falsey*, y son aquellos que cuando se encuentran en un contexto de booleano, JavaScript los convierte a `false`:

* `0` (cero)
* `-0` (cero negativo)
* `0n` (cero de tipo BigInt)
* `""` (comillas dobles vacías)
* `''` (comillas simples vacías)
* ``` `` ``` (tildes invertidas vacías)
* `null`
* `undefined`
* `NaN`

Entonces, si utilizaramos cualquiera de estos valores en un contexto de condicional, la condición resultara falsa.

```javascript
var resultado = Math.round("cero");
// → NaN

// por lo tanto resultado es falsy
if (resultado) {
  console.log("Esto nunca se mostrará");
}
```

Por consiguiente, el resto de los valores en JavaScript son convertibles a `true`, y se consideran *truthy*.

Esto es posible gracias al mecanismo de *coerción*, al cual le dedicamos un capítulo más adelante. Básicamente, cuando lo que se espera es un booleano, JavaScript fuerza el valor al tipo boolean, en una operación equivalente a llamar la función global `Boolean` sobre él.

```javascript
// todos los siguientes retornan `false`
Boolean(false)
Boolean(0)
Boolean(-0)
Boolean(0n)
Boolean("")
Boolean('')
Boolean(``)
Boolean(null)
Boolean(undefined)
Boolean(NaN)

// cualquier otro valor retorna `true`
Boolean(true)
Boolean([])
Boolean({})
Boolean('Hola mundo')
Boolean(new Date())
```
