# Método en linea (Inline Method)

## Problema

El cuerpo del método (sus instrucciones) explica mejor el método en si, que su nombre.

```Kotlin
class EntregaDePizza {
    fun obtenerCalificacion(): Int {
        return if (masDeCincoEntregasTardias()) 2 else 1
    }

    fun masDeCincoEntregasTardias(): Boolean {
        return cantidadDeEntregasTardias > 5
    }
}
```

## Solución

Reemplaza las llamadas al método con el contenido del método y elimina el método en sí.

```Kotlin
class EntregaDePizza {
  fun obtenerCalificacion(): Int {
    return if (cantidadDeEntregasTardias > 5) 2 else 1
  }
}
```

## Por qué refactorizar

* Un método simplemente delega a otro método. En sí misma, esta delegación no es un problema. Pero cuando hay muchos métodos de este tipo, se convierten en una maraña confusa que es difícil de resolver.
* A menudo, los métodos no son demasiado cortos originalmente, pero se vuelven así a medida que se realizan cambios en el programa. Así que no tengas miedo de deshacerte de los métodos que han sobrevivido a su uso.

## Beneficios

Al minimizar la cantidad de métodos innecesarios, hace que el código sea más sencillo.

## Cómo refactorizar

1. Asegurate de que el método no esté redefinido en las subclases. Si se redefine el método, abstenerse de esta técnica.
2. Encuentra todas las llamadas al método y reemplaza estas llamadas con el contenido del método.
3. Eliminar el método.
