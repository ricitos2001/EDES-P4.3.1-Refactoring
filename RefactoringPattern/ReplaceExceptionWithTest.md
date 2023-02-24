# Reemplazar excepción con prueba (Replace exception with test)

## Problema

Lanzas una excepción cuando podrías usar una simple prueba.

```Kotlin
fun getValueForPeriod(periodNumber:Int ) {
  try {
    return values[periodNumber]
  } catch (ArrayIndexOutOfBoundsException e) {
    return 0
  }
}
```

## Solución

Reemplaza la excepción con una prueba usando condicionales.

```Kotlin
fun getValueForPeriod(periodNumber:Int) {
  if (periodNumber >= values.length) {
    return 0
  }
  return values[periodNumber]
}
```

## Por qué refactorizar

Las excepciones deben usarse para manejar el comportamiento irregular relacionado con un error inesperado, no deberían servir como reemplazo para las pruebas. Si se puede evitar una excepción simplemente verificando una condición antes de ejecutarla, hágalo. Las excepciones deben reservarse para errores reales.

## Beneficios

Un condicional simple puede ser más obvio que el código de manejo de excepciones.

## Cómo refactorizar

1. Crea un condicional para un caso límite y muévalo antes del bloque try/catch. Crea un nuevo método y asígnale un nombre que haga evidente su propósito
2. Mueve el código de la sección catch dentro de este condicional.
3. En el catch, coloque el código para lanzar una excepción habitual sin nombre y ejecute todas las pruebas.
4. Si no se generaron excepciones durante las pruebas, elimine el operador try/catch.
