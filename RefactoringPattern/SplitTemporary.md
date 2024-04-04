# Dividir variable temporal

## Problema

Tiene una variable local que se usa para almacenar varios valores intermedios dentro de un método (excepto las variables de ciclo).

```Kotlin
val temp = 2 * (height + width)
println(temp)
val temp = height * width
println(temp)
```

## Solución

Utilice diferentes variables para diferentes valores. Cada variable debe ser responsable de una sola cosa en particular.

``` Kotlin
val perimeter = 2 * (height + width)
println(perimeter)
val area = height * width
println(area)
```

## ¿Por qué Refactorizar?

Si está escatimando en el número de variables dentro de una función y reutilizándolas para varios propósitos no relacionados, seguramente encontrará problemas tan pronto como necesite realizar cambios en el código que contiene las variables. Tendrá que volver a comprobar cada caso de uso de variables para asegurarse de que se utilizan los valores correctos.

## Beneficios

* Cada componente del código del programa debe ser responsable de una sola cosa. Esto hace que sea mucho más fácil mantener el código, ya que puede reemplazar fácilmente cualquier cosa en particular sin temor a efectos no deseados.

* El código se vuelve más legible. Si una variable se creó hace mucho tiempo con prisas, probablemente tenga un nombre que no explique nada: , , , etc. Pero puede solucionar esta situación nombrando las nuevas variables de una manera comprensible y autoexplicativa. Tales nombres pueden parecerse a , , y similares.`k`,`a2`,`value`,`customerTaxValue`,`cityUnemploymentRate`,`clientSalutationString`.

* Esta técnica de refactorización es útil si preves utilizar el [método de extracción](./ExtractMethod.md) más adelante.

## Cómo refactorizar

1. Encuentra el primer lugar en el código donde se da un valor a la variable. Aquí debe cambiar el nombre de la variable con un nombre que corresponda al valor que se le está asignando.

2. Utilice el nuevo nombre en lugar del antiguo en los lugares donde se utilice este valor de la variable.

3. Repita el procedimiento según sea necesario para los lugares en los que se asigne un valor diferente a la variable.
