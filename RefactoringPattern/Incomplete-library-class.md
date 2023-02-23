# Clase de biblioteca incompleta

## Signos y síntomas

Tarde o temprano, las bibliotecas dejan de satisfacer las necesidades de los usuarios. La única solución al problema, cambiar la biblioteca, 
a menudo es imposible ya que la biblioteca es de solo lectura.

![](https://refactoring.guru/images/refactoring/content/smells/incomplete-library-class-01.png?id=ca51f740f7fd39b7de1430b64cae9f8c)

## Razones del problema

El autor de la biblioteca no ha proporcionado las funciones que necesita o se ha negado a implementarlas.

## Tratamiento
Para introducir algunos métodos en una clase de biblioteca, utilice [Introduce Foreign Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/17-refactoring-moving-features-between-objects-introduce-foreing-method/RefactoringPattern/RefactoringPatternIntroduce-Foreign-Method.md) .

Para grandes cambios en una biblioteca de clases, use Introduce Local Extension .

## Saldar
Reduce la duplicación de código (en lugar de crear su propia biblioteca desde cero, aún puede aprovechar una existente).

![](https://refactoring.guru/images/refactoring/content/smells/incomplete-library-class-02.png?id=05a8d9c631d43a3fb256196f366fd089)

## Cuándo ignorar
Ampliar una biblioteca puede generar trabajo adicional si los cambios en la biblioteca implican cambios en el código.
