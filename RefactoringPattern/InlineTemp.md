# Inline Temp
## Problema
* Una variable temporal a la que se le asigna el resultado de una expresión simple y nada más.
```kotlin
fun hasDiscount(order: Order) : Boolean {
    val basePrice = order.basePrice()
    return basePrice > 1000
}
```
## Solución
* Reemplaza las refencias a la variable con la misma expresión.
```kotlin
fun hasDiscount(order: Order) : Boolean {
    return order.basePrice() > 1000
}
```
## Por qué refactorizar
Las variables locales en línea casi siempre se usan como parte de 
[Replace Temp with Query](https://refactoring.guru/replace-temp-with-query)
o para allanar el camino para [Extract Method](https://refactoring.guru/extract-method).
## Beneficios
Esta técnica de refactorización no ofrece casi ningún beneficio en sí misma. Sin embargo, si a la variable se le
asigna el resultado de un método, puede mejorar marginalmente la legibilidad del programa al deshacerse de la variable
innecesaria.
## Inconvenientes
A veces, se utilizan temporales aparentemente inútiles para almacenar en caché el resultado de una operación costosa
que se reutiliza varias veces. Entonces, antes de usar esta técnica de refactorización, asegúrese de que la simplicidad
no se produzca a costa del rendimiento.
## Como refactorizar
1. Encuentra todos los lugares que usan la variable. En lugar de la variable, utilice la expresión que le ha sido 
asignada.
2. Elimine la declaración de la variable y su línea de asignación.
