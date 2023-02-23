# Algoritmo de sustitución

## Problema
* Un método no tiene suficientes datos para realizar ciertas acciones.
![](https://refactoring.guru/images/refactoring/diagrams/Add%20Parameter%20-%20Before.png)

## Solución
* Cree un nuevo parámetro para pasar los datos necesarios.
![](https://refactoring.guru/images/refactoring/diagrams/Add%20Parameter%20-%20After.png)

## Por qué refactorizar
Necesita realizar cambios en un método y estos cambios requieren agregar información o datos que anteriormente no estaban disponibles para el método.

## Beneficios

La elección aquí es entre agregar un nuevo parámetro y agregar un nuevo campo privado que contenga los datos necesarios para el método. Un parámetro es preferible cuando necesita algunos datos ocasionales o que cambian con frecuencia y no tiene sentido mantenerlos en un objeto todo el tiempo. En este caso, el refactorización valdrá la pena. De lo contrario, agregue un campo privado y llénelo con los datos necesarios antes de llamar al método.

## Inconvenientes
Agregar un nuevo parámetro siempre es más fácil que eliminarlo, lo que explica por qué las listas de parámetros a menudo crecen a tamaños grotescos. Este olor se conoce como [Large Parametrer List](https://refactoring.guru/es/smells/long-parameter-list).

Si necesita agregar un nuevo parámetro, a veces esto significa que su clase no contiene los datos necesarios o que los parámetros existentes no contienen los datos relacionados necesarios. En ambos casos, la mejor solución es considerar mover los datos a la clase principal o a otras clases cuyos objetos ya son accesibles desde el interior del método.

## Como refactorizar

1. Verifique si el método está definido en una superclase o subclase. Si el método está presente en ellas, deberá repetir todos los pasos en esas clases también.

2. El siguiente paso es crítico para mantener su programa funcional durante el proceso de refactorización. Cree un nuevo método copiando el antiguo y agregue el parámetro necesario. Reemplace el código del antiguo método con una llamada al nuevo método. Puede agregar cualquier valor al nuevo parámetro (como null para objetos o cero para números).

3. Encuentre todas las referencias al antiguo método y reemplácelas con referencias al nuevo método.

4. Elimine el antiguo método. La eliminación no es posible si el antiguo método forma parte de la interfaz pública. Si ese es el caso, marque el antiguo método como obsoleto.