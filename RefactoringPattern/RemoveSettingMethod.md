# Eliminar método de configuración (Remove Setting Method)

## Problema

El valor de un campo debe establecerse solo cuando se crea, no en ningún momento después de eso.

```Kotlin
class Cliente() {
  var ID: Int = 0
  fun setId(id: Int) {
    ID = id
  }
}
```

## Solución

Simplemente elimina los métodos que establecen el valor del campo.

```Kotlin
class Cliente(val ID: Int)
```

## Por qué refactorizar

* Quieres evitar cualquier cambio en el valor de un campo.

## Cómo refactorizar

1. El valor de un campo debe poder cambiarse solo en el constructor. Si el constructor no contiene un parámetro para establecer el valor, agregua uno.
2. Encuentra todas las llamadas de setter.

   * Si una llamada de setter se encuentra justo después de una llamada para el constructor de la clase actual, mueve su argumento a la llamada del constructor y elimina el setter.
   * Reemplaza las llamadas de setter en el constructor con acceso directo al campo.
3. Elimina el setter.
