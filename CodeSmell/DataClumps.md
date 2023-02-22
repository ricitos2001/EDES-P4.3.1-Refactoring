# Grupos de datos (Data Clumps)

## Signos y síntomas

A veces, diferentes partes del código contienen grupos idénticos de variables (como parámetros para conectarse a una base de datos). Estos grupos deben convertirse en sus propias clases.

![](https://refactoring.guru/images/refactoring/content/smells/data-clumps-01.png?id=9d8a38ce942720cee728797eba695a2f)

## Razones del problema

A menudo, estos grupos de datos se deben a una estructura deficiente del programa o "programación copypasta".

Si desea asegurarse de que algunos datos sean o no un grupo de datos, simplemente elimine uno de los valores de datos y vea si los otros valores aún tienen sentido. Si este no es el caso, es una buena señal de que este grupo de variables debe combinarse en un objeto.

## Tratamiento

- Si los datos repetidos comprenden los campos de una clase, use [Extraer clase](./RefactoringPattern/ExtractClass.md) para mover los campos a su propia clase.

- Si se pasan los mismos grupos de datos en los parámetros de los métodos, use [Introducir objeto de parámetro](https://refactoring.guru/es/introduce-parameter-object) para establecerlos como una clase.

- Si algunos de los datos se pasan a otros métodos, piense en pasar todo el objeto de datos al método en lugar de solo campos individuales. [Preservar todo el objeto](https://refactoring.guru/es/preserve-whole-object) ayudará con esto.

- Mire el código usado por estos campos. Puede ser una buena idea mover este código a una clase de datos.

![](https://refactoring.guru/images/refactoring/content/smells/data-clumps-02.png?id=cfb0a8fa64a983473dd31527e28ae158)

## Saldar

- Mejora la comprensión y organización del código. Las operaciones en datos particulares ahora se recopilan en un solo lugar, en lugar de hacerlo al azar en todo el código.

- Reduce el tamaño del código.

![](https://refactoring.guru/images/refactoring/content/smells/data-clumps-03.png?id=c170bbdea77b7d4a26947ef328b70adc)

## Cuándo ignorar

Pasar un objeto completo en los parámetros de un método, en lugar de pasar solo sus valores (tipos primitivos), puede crear una dependencia no deseada entre las dos clases.