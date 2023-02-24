# Object Orientation Abusers: Alternative Classes with different interfaces

## ¿Cuál es el problema?

Este bad smell consiste en que dos clases cumples las mismas funciones pero sus métodos tienen nombres distintos,normalmente esto se debe a que el programador no sabe que ya hay una clase que cumple exactamente la misma función

![](https://refactoring.guru/images/refactoring/content/smells/alternative-classes-with-different-interfaces-01.png)

## ¿Cómo gestionar el problema?

* Renombra los métodos para asegurarte que en todo el código usas los mismos métodos con el mismo nombre y todo.
* Si solo una parte de las clases está duplicado, se puede extraer esa parte y convertirla en una super clase.
* Usar las siguientes técnicas Move Method, Add Parameter y Parameterize Method para hacer que la implementación de los métodos sean iguales

Una vez que hayas aplicado algunos de los métodos anteriormente comentados, puedes eliminar una de las clases "duplicadas".

[Aquí un vídeo en inglés que explica el tema](https://code.tutsplus.com/courses/detecting-code-smells/lessons/alternative-classes-with-different-interfaces)

![](https://refactoring.guru/images/refactoring/content/smells/alternative-classes-with-different-interfaces-02.png)

## ¿Cuál es la importancia de todo esto?

Hacer que tu código no tenga duplicados, esto facilitará la lectura y entendimiento de tu código lo cual mejorará el mantenimiento a este mismo.

Cable aclarar que no siempre se puede fusionar las clases o hay veces que es tan complicado hacerlo que no tiene sentido el solucionarlo. Un ejemplo es que las clases estén en diferentes librerías
