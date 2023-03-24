# Extract Superclass


## Problema
Tienes dos clases con campos y métodos comunes.

![Extraer Superclase - Antes](https://refactoring.guru/images/refactoring/diagrams/Extract%20Superclass%20-%20Before.png)

## Solución
Crea una superclase compartida para ellas y mueve todos los campos y métodos idénticos a ella.

![Extraer Superclase - Después](https://refactoring.guru/images/refactoring/diagrams/Extract%20Superclass%20-%20After.png)

## Por qué Refactorizar

Un tipo de duplicación de código ocurre cuando dos clases realizan tareas similares de la misma manera, o realizan tareas similares de diferentes maneras. Los objetos ofrecen un mecanismo incorporado para simplificar tales situaciones a través de la herencia. Pero a menudo esta similitud pasa desapercibida hasta que se crean las clases, lo que requiere la creación de una estructura de herencia más tarde.

## Beneficios
Deduplicación de código. Los campos y métodos comunes ahora "viven" en un solo lugar.
Cuándo no usar
No se puede aplicar esta técnica a clases que ya tienen una superclase.

## Cómo Refactorizar

1. Crea una superclase abstracta.

2. Utiliza [Pull Up Field](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/PullUpField.md),
[Pull Up Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/123-refactoring-dealing-with-generalization-pull-up-method/RefactoringPattern/Pull-up-Method.md)
y [Pull Up Constructor Body](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/Pull-Up-Constructor-Body.md)
para mover la funcionalidad común a una superclase.
Comienza con los campos, ya que además de los campos comunes tendrás que mover los campos que se utilizan en los métodos
comunes.

3. Busca lugares en el código del cliente donde se puedan reemplazar el uso de subclases con tu nueva clase (como en las declaraciones de tipo).