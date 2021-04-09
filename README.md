# Apuntes Javascript

## Conceptos de programación

_El código limpio no se crea siguiendo una serie de reglas. No se convertirá en un maestro del software aprendiendo una lista de heurísticas. La profesionalidad y la maestría provienen de los valores que impulsan las disciplinas - [_Clean Code_](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)_

### ¿Qué es una función pura? - What is a Pure Function?

Se podría decir que una función es pura si cumple con lo siguiente:

* Dada las mismas entradas (inputs) siempre devolverá la misma salida.
* No produce efectos secundarios (side effects), tales como: llamadas HTTP, mutar las entradas, modificar los valores de variables globales. De este modo, no puede alterar ningún estado externo.

Este tipo de funciones ofrecen grandes ventajas en la programación, dado que al ser completamente independientes de un estado externo facilita la refactorización y es adaptable a futuros cambios.

Un ejemplo básico de una función pura es la siguiente:

```javascript
const add = (x, y) => x + y;
```

`Para cada entrada x e y corresponde una única salida`

Ahora miremos la siguiente función:

```javascript
const addOrder = (obj, order) => {
    obj.orders.push({
        order
    });
    return obj;
}
```

Aunque dada las mismas entradas siempre retornará lo mismo, se está mutando un objeto que puede estar compartido, de este modo, no está cumpliendo la condición de que una función pura no produce efectos secundarios.

Una forma de corregir la función anterior es clonar el objeto que llega como parámetro de entrada, agregar el nuevo elemento y retornarlo, evitando modificar el objeto original.

```javascript
const addOrder = (obj, order) => {
    // Se  hace un clone profundo del objeto
    newObj = JSON.parse(JSON.stringify(obj));
    newObj.orders.push({
        order
    });
    return newObj;
}
```

**Se debe tener en cuenta que no todas las funciones pueden ser puras. Sin embargo, se recomienda favorecerlas sobre otras opciones.**

### ¿Qué es una Closure en JavaScript?

Para definir realmente que es un closure en JavaScript, veamos las siguientes definiciones:

_Una clausura o closure es una función que guarda referencias del estado adyacente (ámbito léxico). En otras palabras, una clausura permite acceder al ámbito de una función exterior desde una función interior. - [_MDN Web Docs_](https://developer.mozilla.org/es/docs/Web/JavaScript/Closures)_

_Un closure es la combinación de una función agrupada (encerrada) con referencias a su estado circundante (el entorno léxico). En otras palabras, un closure le da acceso al alcance de una función externa desde una función interna. En JavaScript, los closure se crean cada vez que se crea una función, en el momento de la creación de la función. - [_Eric Elliott_](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36)_

Closure es un comportamiento de funciones y solo de funciones. [_You Don't Know JS_](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch7.md)

Las closure puede ser un concepto que usemos a diario a la hora de programar, sin saber realmente que lo estamos usando. Veamos el siguiente ejemplo:

```javascript
const hello = (name) => {
    const hi = 'Hi';
    const sayHello = () => {
        console.log(`${hi} ${name}`);
    }
    sayHello();
}
hello('Peter');
```

Dentro de la función _hello()_ se crea una variable llamada _hi_. Como las funciones internas tienen acceso a las variables de las funciones externas, la función _sayHello()_ puede acceder a la variable _hi_. Lo descrito anteriormente se conoce como **_ámbito léxico_**, el cual se basa en el lugar donde la variable fue creada para determinar dónde estará disponible.

### Composición de funciones

### Programación funcional
