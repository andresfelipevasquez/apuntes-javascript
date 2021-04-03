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

**Se debe tener en cuenta que no todas las funciones pueden ser puras. Sin embargo, se recomienda favorecerlas sobre otras opciones**

### Programación funcional

### ¿Qué es una Closure?

### Composición de funciones
