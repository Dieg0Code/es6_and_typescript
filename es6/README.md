# es6

## Declaración de variables `var` y `let`

Para entender este punto es necesario aclarar el termino `Scope`.

### Scope

El "ámbito" de una variable (llamado "scope" en inglés) es el contexto en el que se puede acceder a ella, la zona del programa en el que se define la variable.

JavaScript tiene dos tipos de ámbitos:

- Global
- Función

```javascript
var message = "Hello World!";
```

¿Como sabemos en qué ámbito se puede acceder a la variable `message`?, facil, si no estamos trabajando dentro de una función estamos en el `scope` global, sino estamos en el `scope` de una función.

```javascript
console.log(message);

var message = "Hello World!";
```

El código anterior retornaria un `undefined` el cual es el valor por defecto de las variables. El interprete barre el código de arriba a abajo, es por eso que retorna `undefined` ya que el console.log está declarado primero que la variable `message`. Esto es propio del `es5` o anterior.

En la versión `es6` se introdujo una nueva forma de declarar variables, la cual es `let`.

```javascript
console.log(message);

let message = "Hello World!";

```

Si declaro la variable usando `let` en vez de con `var` y ejecuto, ya no retorna `undefined` sino que devuelve un error de referencia `Uncaught ReferenceError: message is not defined`.

A diferencia de `var`, cuando el interprete recorre el archivo va a buscar la declaración de la variable, si está declarada con `var` va a retornar `undefined`, pero si está con `let` se rompe el flujo, esto obliga al programador a declarar la variable antes de usarla.

```javascript
let message = "Hello World!";

console.log(message);
```

```javascript
if (1 === 3) {
    var message = "Hello World!";
}

console.log(message);
```

Si ejecuto esto aparece `undefined`, pero ¿por qué?, si esta declarada antes de ser imprimida. Esto ocurre porque cuando el interprete recorre el archivo encuentra que la definicion de la variable está dentro del `if`, es decir su `scope` es el `if`, a pesar de que este no sea una función literal, se sigue considerando un `scope` independiente.

Si cambiamos `var` por `let`:

```javascript
if (1 === 3) {
    let message = "Hello World!";
}

console.log(message);
```

Obtenemos `Uncaught ReferenceError: message is not defined`.

Lo que hace el operador `let` es crear esa variable solamente dentro del `scope` en el que está definida, es decir, dentro del `if` en este caso. Cuando se termina de ejecutar el `if` se destruye la variable, es por eso que al tratar de imprimir la variable `message` retorna un error, porque ya no existe en el `scope` en el que está el `console.log`.

Incluso si el `if` resuelve en `true`, seguiria devolviendo error.

```javascript
if (1 === 1) {
    let message = "Hello World!";
}

console.log(message); // Uncaught ReferenceError: message is not defined
```

¿Que pasa si lo hacemos de la siguiente manera?

```javascript
let message = "123";

if (1 === 1) {
    message = "Hello World!";
}

console.log(message); // Hello World!
```

```javascript
let message = "123";

if (1 === 2) {
    message = "Hello World!";
}

console.log(message); // 123
```

Recordar que la declaracion de una variable con `let` nos permite definir el ciclo de vida de esta, ademas de que nos obliga a declararla antes de usarla.