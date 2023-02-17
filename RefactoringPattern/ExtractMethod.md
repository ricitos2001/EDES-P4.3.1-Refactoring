# Extracción de método (Exgract Method)

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

Mueva este código a un nuevo método (o función) separado y reemplace el código anterior con una llamada al método.

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

## Por qué refactorizar

Cuantas más líneas se encuentran en un método, más difícil es averiguar qué hace el método. Esta es la razón principal de esta refactorización.

Además de eliminar las asperezas del código, la extracción de métodos también es un paso en muchos otros enfoques de refactorización.

## Beneficios

* ¡Código más legible! Asegurate de dar al nuevo método un nombre que describa el propósito del método: `createOrder()`, `renderCustomerInfo()`, etc.
* Menos duplicación de código. A menudo, el código que se encuentra en un método se puede reutilizar en otros lugares de tu programa. Entonces puede reemplazar ese codigo por las llamadas al nuevo método.
* Aísla partes independientes del código, lo que significa que es menos probable que se produzcan errores (por ejemplo, evitr modificae una variable incorrecta).

## Cómo refactorizar

1. Crea un nuevo método y asígnele un nombre que haga evidente su propósito.
2. Copia el fragmento de código relevante en su nuevo método. Elimina el fragmento de su ubicación anterior y crea una llamada al nuevo método allí.
   Encuentra todas las variables utilizadas en este fragmento de código. Si se declaran dentro del fragmento y no se usan fuera de él, simplemente déjalas sin cambios: se convertirán en variables locales para el nuevo método.
3. Si las variables se declaran antes del código que está extrayendo, deberás pasar estas variables a los parámetros de su nuevo método para usar los valores contenidos anteriormente en ellos. A veces es más fácil deshacerse de estas variables recurriendo a [Replace Temp with Query](https://refactoring.guru/es/replace-temp-with-query) .
4. Si ves que una variable local cambia dentro del código extraído, esto puede significar que este valor será necesario más adelante en el método principal. Asegurate que es asi y si este es el caso, retorna el valor de esta variable al método principal para que todo siga funcionando.
