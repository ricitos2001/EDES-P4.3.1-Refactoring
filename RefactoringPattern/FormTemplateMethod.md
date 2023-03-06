# Método de plantilla de formulario (Form Template Method)

## Problema

Tus subclases implementan algoritmos que contienen pasos similares en el mismo orden.

![](assets/FormTemplateMethod-Before.png)

## Solución

Mueve la estructura del algoritmo y los pasos idénticos a una superclase y deja la implementación de los diferentes pasos en las subclases.

![](assets/FormTemplateMethod-After.png)

## Por qué refactorizar

Las subclases se desarrollan en paralelo, a veces por diferentes personas, lo que genera duplicación de código, errores y dificultades en el mantenimiento del código, ya que cada cambio debe realizarse en todas las subclases.

## Beneficios

* La duplicación de código no siempre se refiere a casos de simple copia/pega. A menudo, la duplicación ocurre en un nivel superior, como cuando tienes un método para ordenar números y un método para ordenar colecciones de objetos que se diferencian solo por la comparación de elementos. La creación de un método de plantilla elimina esta duplicación al fusionar los pasos del algoritmo compartido en una superclase y dejar solo las diferencias en las subclases.
* Formar un método de plantilla es un ejemplo del principio abierto/cerrado en acción. Cuando aparece una nueva versión del algoritmo, solo necesita crear una nueva subclase; no se requieren cambios en el código existente.

## Cómo refactorizar

1. Divide los algoritmos en las subclases en sus partes constituyentes descritas en métodos separados. El método de extracción puede ayudar con esto.
2. Los métodos resultantes que son idénticos para todas las subclases se pueden mover a una superclase a través del método Pull Up.
3. A los métodos que no son similares se les pueden dar nombres consistentes a través de Rename Method.
4. Mueve las firmas de métodos no similares a una superclase como abstractas utilizando el método Pull Up. Deja sus implementaciones en las subclases.
5. Y finalmente, extrae el método principal del algoritmo a la superclase. Ahora debería funcionar con los pasos del método descritos en la superclase, tanto reales como abstractos.
