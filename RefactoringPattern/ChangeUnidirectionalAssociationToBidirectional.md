# Cambiar Asociación Unidireccional a Bidireccional

## Problema

Tienes dos clases que necesitan utilizar las características de la otra, pero la asociación entre ellas es solo 
unidireccional.

![](https://refactoring.guru/images/refactoring/diagrams/Change%20Unidirectional%20Association%20to%20Bidirectional%20-%20Before.png)

## Solución

Añadir la asociación que falta a la clase que la necesita.

![](https://refactoring.guru/images/refactoring/diagrams/Change%20Unidirectional%20Association%20to%20Bidirectional%20-%20After.png)

## Por qué Refactorizar

Originalmente, las clases tenían una asociación unidireccional. Pero con el tiempo, el código del cliente necesitó 
acceso a ambos lados de la asociación.

## Beneficios

Si una clase necesita una asociación inversa, se puede calcular fácilmente. Pero si estos cálculos son complejos, es 
mejor mantener la asociación inversa.

## Desventajas

* Las asociaciones bidireccionales son mucho más difíciles de implementar y mantener que las unidireccionales.

* Las asociaciones bidireccionales hacen que las clases sean interdependientes. Con una asociación unidireccional, una 
de ellas se puede utilizar de forma independiente de la otra.

## Cómo refactorizar

1. Añade un campo para mantener la asociación inversa.

2. Decide cuál clase será "dominante". Esta clase contendrá los métodos que crean o actualizan la asociación a medida 
que se agregan o cambian elementos, estableciendo la asociación en su clase y llamando a los métodos de utilidad para 
establecer la asociación en el objeto asociado.

3. Crea un método de utilidad para establecer la asociación en la clase "no dominante". El método debe usar lo que se le 
da en parámetros para completar el campo. Dale al método un nombre obvio para que no se use más tarde para ningún otro 
propósito.

4. Si los antiguos métodos para controlar la asociación unidireccional estaban en la clase "dominante", complétalos con 
llamadas a los métodos de utilidad del objeto asociado.

5. Si los antiguos métodos para controlar la asociación estaban en la clase "no dominante", crea los métodos en la clase 
"dominante", llámalos y delega la ejecución en ellos.

## Anti-Refactorizar

[Cambiar Asociación Bidireccional a Unidireccional](ChangeBidirectionalAssociationToUnidirectional.md)
