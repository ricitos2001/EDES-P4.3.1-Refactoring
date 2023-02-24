# Reemplazar parámetro con métodos explícitos (Replace Parameter with Explicit Methods)

## Problema

Un método se divide en partes, cada una de las cuales se ejecuta según el valor de un parámetro.

```Kotlin
fun imprime(type: String) {
    when (type) {
        "banner" -> {
            // Imprimir el banner.
        }
        "info" -> {
            // Imprimir la información.
        }
    }
}
```

## Solución

Extrae las partes individuales del método en métodos diferentes y llámalos, en lugar del método original.

```Kotlin
fun imprimeBanner() {
    // Imprimir el banner.
}

fun imprimeInfo() {
    // Imprimir la información.
}
```

## Por qué refactorizar

Un método que contiene variantes dependientes de parámetros se ha vuelto masivo. El código no trivial se ejecuta en cada rama y rara vez se agregan nuevas variantes.

## Beneficios

Mejora la legibilidad del código. Es mucho más fácil entender el propósito de ``startEngine()`` que ``setValue("engineEnabled", true)``.

## Cuándo no usarlo

No reemplaces un parámetro con métodos explícitos si un método rara vez se cambia y no se agregan nuevas variantes dentro de él.

## Cómo refactorizar

1. Para cada variante del método, crea un método separado. Ejecuta estos métodos en función del valor de un parámetro en el método principal.
2. Encuentra todos los lugares donde se llama al método original. En estos lugares, realiza una llamada para una de las nuevas variantes dependientes de parámetros.
3. Cuando no queden llamadas al método original, elimínalo.
