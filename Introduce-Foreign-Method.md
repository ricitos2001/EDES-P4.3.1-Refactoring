# Introducir método extranjero

## Problema

Una clase de utilidad no contiene el método que necesita y no puede agregar el método a la clase.

``` Java 
class Report {
  // ...
  void sendReport() {
    Date nextDay = new Date(previousEnd.getYear(),
      previousEnd.getMonth(), previousEnd.getDate() + 1);
    // ...
  }
}

```

## Solución
Agregue el método a una clase de cliente y pásele un objeto de la clase de utilidad como argumento.

``` Java
class Report {
  // ...
  void sendReport() {
    Date newStart = nextDay(previousEnd);
    // ...
  }
  private static Date nextDay(Date arg) {
    return new Date(arg.getYear(), arg.getMonth(), arg.getDate() + 1);
  }
}
```

## Por qué refactorizar

Tiene código que utiliza los datos y métodos de una determinada clase. Te das cuenta de que el código se verá y funcionará mucho mejor
dentro de un nuevo método en la clase. Pero no puede agregar el método a la clase porque, por ejemplo, la clase se encuentra en una biblioteca de terceros.

Esta refactorización tiene una gran recompensa cuando el código que desea mover al método se repite varias veces en diferentes lugares de su programa.

Dado que está pasando un objeto de la clase de utilidad a los parámetros del nuevo método, tiene acceso a todos sus campos. Dentro del método, puedes hacer prácticamente todo lo que quieras, como si el método fuera parte de la clase de utilidad.

## Beneficios

Elimina la duplicación de código. Si su código se repite en varios lugares, puede reemplazar estos fragmentos de código con una llamada de método.
Esto es mejor que la duplicación incluso considerando que el método extraño se encuentra en un lugar subóptimo.

## Inconvenientes
Las razones para tener el método de una clase de utilidad en una clase de cliente no siempre serán claras para la persona que mantiene el código
después de usted. Si el método se puede usar en otras clases, podría beneficiarse creando un contenedor para la clase de utilidad y colocando el 
método allí. Esto también es beneficioso cuando existen varios métodos de utilidad de este tipo. Introducir Extensión Local puede ayudar con esto.

## Cómo refactorizar

1. Cree un nuevo método en la clase de cliente.

2. En este método, cree un parámetro al que se pasará el objeto de la clase de utilidad. Si este objeto se puede obtener de la clase de cliente, no es necesario que cree dicho parámetro.

3. Extraiga los fragmentos de código relevantes para este método y reemplácelos con llamadas a métodos.

4. Asegúrese de dejar la etiqueta del método Extranjero en los comentarios del método junto con el consejo de colocar este método en una clase de utilidad si es posible más adelante. Esto facilitará la comprensión de por qué este método se encuentra en esta clase en particular para aquellos que mantendrán el software en el futuro.
