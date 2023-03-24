# Push Down Field 

## Problema
¿Es un campo utilizado solo en algunas subclases?

![Empuje hacia abajo el campo - Antes](https://refactoring.guru/images/refactoring/diagrams/Push%20Down%20Field%20-%20Before.png)

## Solución
Mueva el campo a estas subclases.

![Empuje hacia abajo el campo - Después](https://refactoring.guru/images/refactoring/diagrams/Push%20Down%20Field%20-%20After.png)

## ¿Por qué refactorizar?
Aunque se planeó utilizar un campo universalmente para todas las clases, en realidad el campo se utiliza solo en algunas subclases. Esta situación puede ocurrir cuando las características planificadas no se desarrollan, por ejemplo.

Esto también puede ocurrir debido a la extracción (o eliminación) de parte de la funcionalidad de las jerarquías de clases.

## Beneficios
Mejora la coherencia interna de la clase. Un campo se ubica donde realmente se utiliza.

Al moverlo simultáneamente a varias subclases, puede desarrollar los campos de manera independiente. Esto crea duplicación de código, por lo que solo empuje hacia abajo los campos cuando realmente tenga la intención de utilizarlos de diferentes maneras.

## Cómo refactorizar
1. Declare un campo en todas las subclases necesarias.

2. Elimine el campo de la superclase.