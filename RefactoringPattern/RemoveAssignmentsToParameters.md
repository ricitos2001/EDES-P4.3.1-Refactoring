# Eliminar asignación a parámetros (Remove Assignments to Parameters)

## Problema

Algún valor es asignado a un parámetro dentro del cuerpo del método.

```Kotlin
fun discount(inputVal : Int, quantity : Int) {
  if (quantity > 50){
      inputVal -= 2
  }
}
```

## Solución

Utilice una variable local en lugar de un parámetro.

```Kotlin
fun discount(inputVal : Int, quantity : Int) {
  var result = inputVal
  if (quantity > 50){
      result -= 2
  }
}
```

## Por qué refactorizar

Las razones para esta refactorización son las mismas que para "***Split temporary variable***", pero tratándose de un parámetro, no una variable local.

Si un parámetro se pasa por referencia, luego de cambiar el valor del parámetro dentro del método, este valor se pasa al argumento que solicitó llamar a este método. Muy a menudo esto ocurre accidentalmente y conduce a efectos desafortunados. Incluso si los parámetros generalmente se pasan por valor (y no por referencia) en su lenguaje de programación, esta peculiaridad de codificación puede alejar a aquellos que no están acostumbrados a ella.

Además, las múltiples asignaciones de diferentes valores a un solo parámetro dificultan saber qué datos debe contener el parámetro en un momento determinado. El problema empeora si su parámetro y su contenido están documentados, pero el valor real puede diferir de lo que se espera dentro del método.

## Beneficios

* Cada elemento del programa debe ser responsable de una sola cosa. Esto hace que el mantenimiento del código sea mucho más fácil ya que se puede reemplazar código de manera segura.
* Esta refactorización ayuda a ver código repetitivo para separarlo en métodos.

## Cómo refactorizar

1. Cree una variable local y asigne el valor inicial de su parámetro.
2. En todo el código del método, reemplace el parámetro por su nueva variable local.
