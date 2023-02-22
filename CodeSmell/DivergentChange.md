# Cambio Divergente (Divergent Change)

El cambio divergente se parece a la [cirugía de escopeta](./CodeSmell/ShotgunSurgery.md) pero en realidad es lo contrario. Cambio divergente es cuando se hacen muchos cambios a una sola clase. Cirugía de escopeta se refiere a cuando se realiza un solo cambio en varias clases a la vez.

## Signos y síntomas

Si te ves teniendo que cambiar muchos metodos que no están relacionados entre sí cuando haces cambios a una clase. Por ejemplo, cuando añades un tipo de producto tienes que cambiar los métodos para encontrar, enseñar y ordenar productos.

![](https://refactoring.guru/images/refactoring/content/smells/divergent-change-01.png?id=d62e68e1778d67bf82ff74064c24de33)

## Razones del problema

A menudo esas modificaciones divergentes se deben a una estructura pobre del programa o a "programación por copypaste".
## Tratamiento

* Divide el comportamiento de la clase mediante la [extracción de clase](https://refactoring.guru/es/extract-class).

* Si diferentes clases tienen el mismo comportamiento, puede que debas combinar las clases mediante herencia([extracción de superclase](https://refactoring.guru/es/extract-superclass) y [extraccion de subclase](https://refactoring.guru/es/extract-subclass))

![](https://refactoring.guru/images/refactoring/content/smells/divergent-change-02.png?id=21b6fd7cba36f123c09497cb8f5a5625)

## Beneficios

* Mejora la organización del código.

* Reduce el código duplicado.

* Simplifica el mantenimiento.