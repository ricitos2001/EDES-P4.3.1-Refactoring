# Push Down Method

## Problema
¿Se implementa un comportamiento en una superclase utilizado por solo una (o unas pocas) subclases?

![Método Push Down - Antes](https://refactoring.guru/images/refactoring/diagrams/Push%20Down%20Method%20-%20Before.png)

## Solución
Mueva este comportamiento a las subclases.

![Método Push Down - Después](https://refactoring.guru/images/refactoring/diagrams/Push%20Down%20Method%20-%20After.png)

## Por qué refactorizar
Inicialmente, se pretendía que un método fuera universal para todas las clases, pero en realidad solo se usa en una 
subclase. Esta situación puede ocurrir cuando las características planificadas no se materializan.

Estas situaciones también pueden ocurrir después de la extracción (o eliminación) parcial de la funcionalidad de una
jerarquía de clases, dejando un método que se utiliza en solo una subclase.

Si ve que se necesita un método en más de una subclase, pero no en todas, puede ser útil crear una subclase intermedia 
y mover el método a ella. Esto evita la duplicación de código que resultaría al empujar un método a todas las subclases.

## Beneficios
Mejora la coherencia de la clase. Un método se encuentra donde se espera verlo.
## Cómo refactorizar
1. Declare el método en una subclase y copie su código de la superclase.

2. Elimine el método de la superclase.

3. Encuentre todos los lugares donde se usa el método y verifique que se llame desde la subclase necesaria.