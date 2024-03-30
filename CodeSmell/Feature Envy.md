# Feature Envy

## Signos y síntomas
Un método accede a los datos de otro objeto más que a sus propios datos.

![Imagen Feature Envy](https://refactoring.guru/images/refactoring/content/smells/feature-envy-01.png)

## Razones del problema

Este olor puede ocurrir después de que los campos se muevan a una clase de datos. Si este es el caso, es posible que también desee mover las operaciones sobre los datos a esta clase.

## Tratamiento
Como regla básica, si las cosas cambian al mismo tiempo, debes mantenerlas en el mismo lugar. Por lo general, los datos y las funciones que usan estos datos se cambian juntos (aunque son posibles las excepciones).

- Si claramente se debe mover un método a otro lugar, use [Move Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/tree/main/RefactoringPattern/MoveMethod.md) .

- Si solo una parte de un método accede a los datos de otro objeto, puede usar [Extract Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/ExtractMethod.md) todo para mover la parte en cuestión.

- Si un método usa funciones de varias otras clases, primero determine qué clase contiene la mayoría de los datos usados. 
Luego coloque el método en esta clase junto con los otros datos. De manera alternativa, use [Extraer método](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/ExtractMethod.md)
para dividir el método en varias partes que se pueden colocar en diferentes lugares en diferentes clases.

![](https://refactoring.guru/images/refactoring/content/smells/feature-envy-02.png)

## Beneficios
- Menos duplicación de código (si el código de manejo de datos se coloca en un lugar central).

- Mejor organización del código (los métodos para manejar los datos están al lado de los datos reales).

![](https://refactoring.guru/images/refactoring/content/smells/feature-envy-03.png)

## Cuándo ignorar
A veces, el comportamiento se mantiene separado deliberadamente de la clase que contiene los datos. La ventaja habitual de esto es la capacidad de cambiar dinámicamente el comportamiento.
