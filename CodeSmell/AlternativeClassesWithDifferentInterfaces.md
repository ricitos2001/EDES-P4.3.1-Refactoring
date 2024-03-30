# Object Orientation Abusers: Alternative Classes with different interfaces

## ¿Cuál es el problema?

Este olor consiste en que dos clases cumplen las mismas funciones pero sus métodos tienen nombres distintos,normalmente esto se debe a que el programador no sabía que ya existía una clase que cumplia exactamente la misma función.

![](https://refactoring.guru/images/refactoring/content/smells/alternative-classes-with-different-interfaces-01.png)

## ¿Cómo gestionar el problema?

* Renombra los métodos para que se llamen igual en todas las clases alternativas.
* Si solo una parte de las clases está duplicada, se puede usar [Extraer Clase](../RefactoringPattern/ExtractClass.md) para extraer esta parte y convertirla en una super clase.
* Usar las siguientes técnicas [Move Method](../RefactoringPattern/MoveMethod.md), [Add Parameter](../RefactoringPattern/AddParameter.md) y [Parameterize Method](../RefactoringPattern/ParameterizeMethod.md), [Add Parameter](../RefactoringPattern/AddParameter.md) para hacer que la implementación de los métodos sean iguales

Una vez que hayas aplicado algunos de los métodos anteriormente comentados, puede ser que puedas eliminar una de las clases "duplicadas".

[Aquí un vídeo en inglés que explica el tema](https://code.tutsplus.com/courses/detecting-code-smells/lessons/alternative-classes-with-different-interfaces)

![](https://refactoring.guru/images/refactoring/content/smells/alternative-classes-with-different-interfaces-02.png)

## ¿Cuál es la importancia de todo esto?

Hacer que tu código no tenga duplicados, esto facilitará la lectura y entendimiento de tu código lo cual mejorará el mantenimiento a este mismo.

Cable aclarar que no siempre se puede fusionar las clases o hay veces que es tan complicado hacerlo que no tiene sentido el solucionarlo. Un ejemplo es que las clases estén en diferentes librerías.
