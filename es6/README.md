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

