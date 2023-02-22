# Cirugía de escopeta (Shotgun Surgery)

La cirugía de escopeta se parece al [cambio divergente](DivergentChange.md) pero en realidad es lo contrario. Cambio divergente es cuando se hacen muchos cambios a una sola clase. Cirugía de escopeta se refiere a cuando se realiza un solo cambio en varias clases a la vez.

## Signos y síntomas

Hacer cualquier modificación requiere que hagas cualquier pequeño cambio a muchas clases distintas.

![](https://refactoring.guru/images/refactoring/content/smells/shotgun-surgery-01.png?id=9cc1117a6d787364788e152a3adb6a53)

## Razones del problema

Una sola responsabilidad se ha dividido entre un gran número de clases. Esto puede pasar después de una aplicación demasiado intensiva del [cambio divergente](https://refactoring.guru/es/smells/divergent-change).

![](https://refactoring.guru/images/refactoring/content/smells/shotgun-surgery-02.png?id=48f8a4a0f17d112e02ae73bacaed43fa)

## Tratamiento

* Usa el [método de movimiento](https://refactoring.guru/es/move-method) y el [movimiento de campo](/./RefactoringPattern/MoveField.md) para mover comportamientos existentes de una clase a una sola clase, Si no hay una clase apropiada para esto, crea una nueva.

* Si mover código a la misma clase deja las clases originales casi vacía, intenta encargarte de estas clases ahora redundantes mediante la [clase alineada](https://refactoring.guru/es/inline-class).

![](https://refactoring.guru/images/refactoring/content/smells/shotgun-surgery-03.png?id=cf013f14eb5cde98bd48595a1c9836a9)

## Beneficios

* Mejor organización.

* Menos codigo duplicado.

* Mantenimuento más fácil.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-03.png?id=82ce2d388aa14bdae4e8f62b875f0259)
