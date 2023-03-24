# Replace Delegation with Inheritance

## Problema
Una clase contiene muchos métodos simples que delegan a todos los métodos de otra clase.

![Reemplazar Delegación con Herencia - Antes](https://refactoring.guru/images/refactoring/diagrams/Replace%20Delegation%20with%20Inheritance%20-%20Before.png)

## Solución
Hacer que la clase sea una heredera delegada, lo que hace que los métodos de delegación sean innecesarios.

![Reemplazar Delegación con Herencia - Después](https://refactoring.guru/images/refactoring/diagrams/Replace%20Delegation%20with%20Inheritance%20-%20After.png)

## Por qué Refactorizar

La delegación es un enfoque más flexible que la herencia, ya que permite cambiar cómo se implementa la delegación y 
colocar allí otras clases también. No obstante, la delegación deja de ser beneficiosa si se delegan acciones solo a una 
clase y a todos sus métodos públicos.

En ese caso, si reemplaza la delegación con la herencia, limpia la clase de una gran cantidad de métodos de delegación
y se ahorra la necesidad de crearlos para cada nuevo método de clase delegado.

## Beneficios

Reduce la longitud del código. Todos estos métodos de delegación ya no son necesarios.

## Cuándo no usarlo

- No use esta técnica si la clase contiene delegación solo a una parte de los métodos públicos de la clase delegada.
Al hacerlo, violaría el principio de sustitución de Liskov.

- Esta técnica solo se puede utilizar si la clase aún no tiene padres.

## Cómo Refactorizar
1. Hacer que la clase sea una subclase de la clase delegada.

2. Colocar el objeto actual en un campo que contenga una referencia al objeto delegado.

3. Eliminar los métodos con delegación simple uno por uno. Si sus nombres eran diferentes, use la técnica
[Rename Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/RenameMethod.md) 
para darles un solo nombre.

4. Reemplace todas las referencias al campo delegado con referencias al objeto actual.

5. Eliminar el campo delegado.