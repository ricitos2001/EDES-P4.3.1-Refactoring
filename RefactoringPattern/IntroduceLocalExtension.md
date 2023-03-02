# Introduce Local Extension

Se usa para agregar funcionalidad a una clase que no podemos modificar directamente. Esto suele ser útil cuando trabajamos con bibliotecas de terceros que no proporcionan la funcionalidad que necesitamos.

## ¿Cúal es el problema?

Como se ha dicho antes, cuando queremos añadir funcionalidad a una clase pero no podemos modificarla. En ese caso tendremos que hacer una subclase para añadir esa funcionalidad

## ¿Cómo solucionar el problema?

1. Crear una clase de extensión, que será un elemento secundario que aumente la funcionalidad de la clase principal
2. Crea un constructor que use los parámetros de la clase principal.
3. Cree un constructor alternativo de "conversión" que tome solo el objeto de la clase original en sus parámetros. Esto ayudará a sustituir la extensión por los objetos de la clase original.
4. Crea nuevos métodos extendidos en la clase. Mueva los métodos foráneos de otras clases a esta clase o elimine los métodos foráneos si su funcionalidad ya está presente en la extensión
5. Reemplace el uso de la clase de utilidad con la nueva clase de extensión en los lugares donde se necesita su funcionalidad

## Ejemplo

```
import java.util.Calendar
import java.util.Date

class DateUtils {
    companion object {
        // Agrega un método para sumar días a una fecha
        fun addDays(date: Date, days: Int): Date {
            val calendar = Calendar.getInstance()
            calendar.time = date
            calendar.add(Calendar.DATE, days)
            return calendar.time
        }

        // Agrega un método para restar días a una fecha
        fun subtractDays(date: Date, days: Int): Date {
            val calendar = Calendar.getInstance()
            calendar.time = date
            calendar.add(Calendar.DATE, -days)
            return calendar.time
        }
    }
}

fun main() {
    val date = Date()
    val newDate = DateUtils.addDays(date, 7)
    println("La fecha actual es: $date")
    println("La fecha después de sumar 7 días es: $newDate")
}
```
