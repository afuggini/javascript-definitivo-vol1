# Coerción

La **coerción** es el mecanismo de ciertos lenguajes de programación, incluído JavaScript, por el cual un valor es convertido de un tipo a otro.

Es un proceso que suele ser desconocido, o en ocasiones simplemente evitado por algunos programadores, argumentando que es un comportamiento errático o un defecto de JavaScript.

Por el contrario, el mecanismo de coerción sigue reglas y algorítmos específicos, detallados en el estándar ECMAScript. Por lo cual, conocer sus reglas y dominarlo nos permitirá utilizarlo a nuestro favor para hacer un mejor uso del lenguaje, evitando introducir *bugs* en nuestro código.

Cualquier valor, sea primitivo u objeto, es posible de ser *coercionado* o convertido. La coerción puede suceder de dos formas: ***implícita*** y ***explícita***.

## Coerción Implícita

La **coerción implícita** es la que lleva a cabo JavaScript de forma automática.

En el capítulo sobre **booleanos** hablamos de valores *truthy* y *falsy*. Lo que hace posible que valores de diferentes tipos sean convertibles a booleano en determinados contextos, no es otra cosa que un proceso de de coerción implícita. Por ejemplo, dado el siguiente código:

```javascript
var numero = 1;
var texto = "";

if (numero) {
  console.log("numero es verdadero");
}

texto
  ? console.log("texto es verdadero")
  : console.log("texto es falso");
// → "texto es falso"
```

JavaScript lo interpreta de la siguiente manera:

```javascript
var numero = 1;
var texto = "";

if (Boolean(numero)) {
  console.log("numero es verdadero");
}

Boolean(texto)
  ? console.log("texto es verdadero")
  : console.log("texto es falso");
// → "texto es falso"
```

### Operadores de Igualdad (==)

El operador de igualdad `==` utiliza el mecanismo de coerción de forma implícita. Este simple operador de dos caracteres utiliza internamente un [algoritmo de 13 pasos](https://tc39.es/ecma262/#sec-abstract-equality-comparison) para determinar si dos valores son o no iguales (no es necesario conocerlas, pero si comprender que no hay nada de azaroso ni errático en la forma en que este operador funciona).

Dada la complejidad de este operador, vamos a centrarnos únicamente en algunas de sus reglas principales.

1. Si ambos valores son del mismo tipo, el operador `==` utiliza el mismo mecanismo que `===`.

2. si uno de los operandos es `null` y el otro `undefined`, la comparación devuelve `true`.

```javascript
null == undefined  // true
undefined == null  // true
```

3. Los operandos de tipo `string` y `boolean` son convertidos a `number`:

```javascript
3 == "3"  // true

// dado que...
Number("3")       // → 3
3 == Number("3")  // → true
```

```javascript
1 == true  // → true

// dado que...
Number(true)       // → 1
1 == Number(true)  // → true
```

```javascript
0 == false  // → true

// dado que...
Number(false)       // → 0
0 == Number(false)  // → true
```

Por último, los objetos son convertidos a valores primitivos. Ahora bien, esta conversión a primitivo también sucede según una serie de [reglas](https://tc39.es/ecma262/#sec-toprimitive) sobre las cuales no vamos a profundizar aquí. Lo recomendable es ser consciente en todo momento de los tipos de datos que estamos comparando, para evitar obtener resultados inesperados.

### Boxing

Un tipo particular de coerción implícita es el llamado **boxing**, que sucede cuando invocamos una propiedad o método sobre un valor primitivo. En estos casos, JavaScript promueve el valor al tipo *object*, para asi poder llevar a cabo nuestro requerimiento.

Por ejemplo:

| Cuando hacemos...            | JavaScript interpreta...             |
|------------------------------|--------------------------------------|
| `"Ariel Fuggini".split(" ")` | `String("Ariel Fuggini").split(" ")` |
| `"JavaScript".length`        | `String("JavaScript").length`        |
| `(23.5).toFixed(3)`          | `Number(23.5).toFixed(3)`            |
| `23.5.toFixed(3)`            | `Number(23.5).toFixed(3)`            |
| `true.toString()`            | `Boolean(true).toString()`           |

## Coerción Explícita

La **coerción explícita** es aquella que logramos intencionalmente mediante el uso de funciones u operadores. Por ejemplo:

```javascript
// coerción a boolean
var numero = 42;
Boolean(numero);  // → true
!numero;          // → false
!!numero;         // → true
```

```javascript
// coerción a string
String(numero);     // → "42"
numero + "";        // → "42"
`${numero}`;        // → "42"
numero.toString();  // → "42"
```

```javascript
// coerción a number
var texto = "42";
Number(texto);  // → 42
+texto;         // → 42
++texto;        // → 43
texto++;        // → 43
```
