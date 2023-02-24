# Jerarquías de herencia paralelas

## Signos y síntomas

Cada vez que crea una subclase para una clase, se encuentra con la necesidad de crear una subclase para otra clase.

![Alt text](https://refactoring.guru/images/refactoring/content/smells/parallel-inheritance-hierarchies-01.png?id%3D9167875f5f0e80256edcc8fcaaed3563)

## Razones del problema

Todo iba bien mientras la jerarquía se mantuviera pequeña. Pero con la adición de nuevas clases, hacer cambios se ha vuelto cada vez más difícil.

## Tratamiento

Puede desduplicar jerarquías de clases paralelas en dos pasos. Primero, haga que las instancias de una jerarquía se refieran a instancias de otra jerarquía. Luego, elimine la jerarquía en la clase referida, usando Move Method y Move Field.

## Saldar

· Reduce la duplicación de código.

· Puede mejorar la organización del código.

![Alt text](https://refactoring.guru/images/refactoring/content/smells/parallel-inheritance-hierarchies-02.png?id%3D4dca6795d3d087b23ad1027298d6f1dd)

## Cuándo ignorar

A veces, tener jerarquías de clases paralelas es solo una forma de evitar problemas aún mayores con la arquitectura del programa. Si encuentra que sus intentos de desduplicar jerarquías producen un código aún más feo, simplemente salga, revierta todos sus cambios y acostúmbrese a ese código.