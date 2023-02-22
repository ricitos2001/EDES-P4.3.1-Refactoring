# Extraer variable

## Problema
Tienes una expresión que es difícil de entender.
 ```kotlin
fun renderBanner() {
    if (platform.toUpperCase().indexOf("MAC") > -1 && browser.toUpperCase().indexOf("IE") > -1 &&
        wasInitialized() && resize > 0
    ) {
        // do something
    }
}
 ```
## Solución
Coloque el resultado de la expresión o sus partes en variables separadas que se explican por sí mismas.
```kotlin
void renderBanner() {
  final boolean isMacOs = platform.toUpperCase().indexOf("MAC") > -1;
  final boolean isIE = browser.toUpperCase().indexOf("IE") > -1;
  final boolean wasResized = resize > 0;

  if (isMacOs && isIE && wasInitialized() && wasResized) {
    // do something
  }
}
```
## Por qué refactorizar
La principal razón para extraer variables es hacer que una expresión compleja sea más comprensible, dividiéndola en sus partes intermedias. Estos podrían ser:
- Condición del ```if()``` operador o una parte del ```?```: operador en lenguajes basados ​​en C.
- Una expresión aritmética larga sin resultados intermedios.
- Líneas largas de varias partes.
Extraer una variable puede ser el primer paso para realizar el [método de extracción](ExtractMethod.md) si ve que la expresión extraída se usa en otros lugares de su código.
## Beneficios
¡Código más legible! Trate de dar a las variables extraídas buenos nombres que anuncien alto y claro el propósito de la variable. Más legibilidad, menos comentarios prolijos. Busca nombres como ```customerTaxValue```, ```cityUnemploymentRate```, ```clientSalutationString``` , etc.

## Inconvenientes
- Más variables están presentes en su código. Pero esto se ve contrarrestado por la facilidad de lectura de su código.
- Al refactorizar expresiones condicionales, recuerde que lo más probable es que el compilador las optimice para minimizar la cantidad de cálculos necesarios para establecer el valor resultante. Digamos que tienes una siguiente expresión ```if (a() || b()) ....``` El programa no llamará al método ```b``` si el método ```a``` devuelve ```true``` porque el valor resultante seguirá siendo ```true```, sin importar qué valor devuelva ```b```.

Sin embargo, si extrae partes de esta expresión en variables, siempre se llamará a ambos métodos, lo que podría perjudicar el rendimiento del programa, especialmente si estos métodos realizan un trabajo pesado.

## Cómo refactorizar
1. Inserte una nueva línea antes de la expresión relevante y declare una nueva variable allí. Asigne parte de la expresión compleja a esta variable.
2. Reemplace esa parte de la expresión con la nueva variable.
3. Repita el proceso para todas las partes complejas de la expresión.
