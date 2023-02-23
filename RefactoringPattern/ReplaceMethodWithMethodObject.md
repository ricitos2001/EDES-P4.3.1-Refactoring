# Reemplazar método con objeto de método (Replace Method with Method Object)

## Problema

Tiene un método largo en el que las variables locales están tan entrelazadas que no puede aplicar el Método de extracción.

```Kotlin
class Order {
    fun price(): Double {
        var primaryBasePrice: Double
        var secondaryBasePrice: Double
        var tertiaryBasePrice: Double
        // Realiza el calculo.
        
    }
}
```

## Solución

Transforma el método en una clase separada para que las variables locales se conviertan en campos de la clase. Luego puede dividir el método en varios métodos dentro de la misma clase.

```Kotlin
class Order {
    fun price(): Double {
        return PriceCalculator(this).compute()
    }
}

class PriceCalculator(order: Order) {
    private var primaryBasePrice: Double
    private var secondaryBasePrice: Double
    private var tertiaryBasePrice: Double
    

    fun compute(): Double {
        // realiza el calculo.
        return 0.0 // remplaza el resultado
    }
}
```
## Por qué refactorizar

Un método es demasiado largo y no puedes separarlo debido al enrredo de variables locales que son difíciles de aislar entre sí.

El primer paso es aislar el método en una clase separada y convertir sus variables locales en campos de la clase.

En primer lugar, esto permite aislar el problema a nivel de clase. En segundo lugar, prepara el camino para dividir un método grande y difícil de manejar en otros más pequeños que de todos modos no encajarían con el propósito de la clase original.

## Beneficios

Aislar un método largo en su propia clase permite evitar que el método aumente de tamaño. Esto también permite dividirlo en submétodos dentro de la clase con métodos de utilidad sin contaminar la clase original.

## Inconvenientes

Se agrega otra clase, lo que aumenta la complejidad general del programa.

## Cómo refactorizar

1. Crear una nueva clase. Nómbrala según el propósito del método que estas refactorizando.

2. En la nueva clase, crea un campo privado para almacenar una referencia a una instancia de la clase en la que se encontraba el método anteriormente. Podría usarse para obtener algunos datos requeridos de la clase original si es necesario.

3. Crea un campo privado separado para cada variable local del método.

4. Crea un constructor que acepte como parámetros los valores de todas las variables locales del método y también inicialice los campos privados correspondientes.

5. Declara el método principal y copia el código del método original en él, reemplazando las variables locales con campos privados.

6. Reemplaza el cuerpo del método original en la clase original creando un objeto de método y llamando a su método principal.