# Método de extracción

## Problema

Tiene un fragmento de código que se puede agrupar.

```Kotlin
fun printOwing() {
  printBanner();

  // Print details.
  println("name: " + name);
  println("amount: " + getOutstanding());
}
```

## Solución

Mueva este código a un nuevo método (o función) independiente y reemplace el código antiguo por una llamada al método.

```Kotlin
fun printOwing() {
  printBanner();
  printDetails(getOutstanding());
}

fun printDetails(outstanding:Double) {
  println("name: " + name);
  println("amount: " + outstanding);
}
```

## ¿Por qué Refactorizar?

Cuantas más líneas se encuentren en un método, más difícil será averiguar qué hace el método. Esta es la razón principal de esta refactorización.<br><br>Además de eliminar las asperezas en el código, la extracción de métodos también es un paso en muchos otros enfoques de refactorización.

## Beneficios

* Código más legible! Asegúrese de asignar al nuevo método un nombre que describa el propósito del método: `createOrder()`, `renderCustomerInfo()`, etc.

* Menos duplicación de código. A menudo, el código que se encuentra en un método se puede reutilizar en otros lugares del programa. Por lo tanto, puede reemplazar duplicados con llamadas a su nuevo método.

* Aísla partes independientes del código, lo que significa que los errores son menos probables (por ejemplo, si se modifica la variable incorrecta).

## Cómo refactorizar

1. Crea un nuevo método y nómbralo de una manera que haga que su propósito sea evidente.

2. Copie el fragmento de código correspondiente en el nuevo método. Elimine el fragmento de su ubicación anterior y coloque una llamada para el nuevo método allí en su lugar.<br>Busque todas las variables utilizadas en este fragmento de código. Si se declaran dentro del fragmento y no se usan fuera de él, simplemente déjelos sin cambios: se convertirán en variables locales para el nuevo método.

3. Si las variables se declaran antes del código que está extrayendo, deberá pasar estas variables a los parámetros del nuevo método para usar los valores contenidos anteriormente en ellas. A veces es más fácil deshacerse de estas variables recurriendo a [Reemplazar Temp por Query](./ReplaceTempwithQuery.md).

4. Si ve que una variable local cambia en el código extraído de alguna manera, esto puede significar que este valor modificado será necesario más adelante en el método principal. ¡Compruébalo dos veces! Y si este es el caso, devuelve el valor de esta variable al método principal para que todo siga funcionando.
