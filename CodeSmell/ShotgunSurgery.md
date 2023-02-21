# Cirugía de escopeta (Shotgun Surgery)

La cirugía de escopeta se parece al [cambio divergente](https://refactoring.guru/es/smells/divergent-change) pero en realidad es lo contrario. Cambio divergente es cuando se hacen muchos cambios a una sola clase. Cirugía de escopeta se refiere a cuando se realiza un solo cambio en varias clases a la vez.

## Signos y síntomas

Hacer cualquier modificación requiere que hagas cualquier pequeño cambio a muchas clases distintas.

![](https://refactoring.guru/images/refactoring/content/smells/shotgun-surgery-01.png?id=9cc1117a6d787364788e152a3adb6a53)

## Razones del problema

Una sola responsabilidad se ha dividido entre un gran número[cambio divergente](https://refactoring.guru/es/smells/divergent-change).

A single responsibility has been split up among a large number of classes. This can happen after overzealous application of [cambio divergente](https://refactoring.guru/es/smells/divergent-change).

![](https://refactoring.guru/images/refactoring/content/smells/shotgun-surgery-02.png?id=48f8a4a0f17d112e02ae73bacaed43fa)

## Tratamientoç

* Use [Move Method](https://refactoring.guru/es/move-method) and [Move Field](https://refactoring.guru/es/move-field) to move existing class behaviors into a single class. If there’s no class appropriate for this, create a new one.

* If moving code to the same class leaves the original classes almost empty, try to get rid of these now-redundant classes via [Inline Class](https://refactoring.guru/es/inline-class).

![](https://refactoring.guru/images/refactoring/content/smells/shotgun-surgery-03.png?id=cf013f14eb5cde98bd48595a1c9836a9)

## Beneficios

* Better organization.

* Less code duplication.

* Easier maintenance.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-03.png?id=82ce2d388aa14bdae4e8f62b875f0259)
