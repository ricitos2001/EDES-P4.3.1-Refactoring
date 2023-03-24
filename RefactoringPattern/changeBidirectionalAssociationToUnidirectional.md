# Change Bidirectional Association to Unidirectional

## Problema
Tiene una asociación bidireccional entre clases, pero una de las clases no usa las características de la otra.

![Cambie la Asociación Bidireccional a Unidireccional - Antes](https://refactoring.guru/images/refactoring/diagrams/Change%20Bidirectional%20Association%20to%20Unidirectional%20-%20Before.png)

## Solución
Elimine la asociación no utilizada.

![Cambie la Asociación Bidireccional a Unidireccional - Después](https://refactoring.guru/images/refactoring/diagrams/Change%20Bidirectional%20Association%20to%20Unidirectional%20-%20After.png)

## Por qué refactorizar

Una asociación bidireccional generalmente es más difícil de mantener que una unidireccional, lo que requiere código 
adicional para crear y eliminar adecuadamente los objetos relevantes. Esto hace que el programa sea más complicado.

Además, una asociación bidireccional implementada de manera incorrecta puede causar problemas para la recolección de 
basura (lo que a su vez conduce a una inflación de memoria por objetos no utilizados).

> **Ejemplo**: el recolector de basura elimina objetos de la memoria que ya no son referenciados por otros objetos.
> Supongamos que se creó, usó y luego abandonó un par de objetos Usuario-Pedido. Pero estos objetos no se eliminarán 
> de la memoria ya que aún se refieren entre sí. Dicho esto, este problema está perdiendo importancia gracias a los
> avances en lenguajes de programación, que ahora identifican automáticamente las referencias de objetos no utilizados 
> y los eliminan de la memoria

También está el problema de la interdependencia entre clases. En una asociación bidireccional, las dos clases deben 
conocerse entre sí, lo que significa que no se pueden usar por separado. Si hay muchas de estas asociaciones presentes,
las diferentes partes del programa se vuelven demasiado dependientes entre sí y cualquier cambio en un componente puede
afectar a los otros componentes.

## Beneficios
- Simplifica la clase que no necesita la relación. Menos código significa menos mantenimiento de código.

- Reduce la dependencia entre clases. Las clases independientes son más fáciles de mantener ya que cualquier cambio en 
una clase afecta solo a esa clase.

## Cómo refactorizar
1. Asegúrese de que una de las siguientes sea verdadera para sus clases:

    - No se usa ninguna asociación.

    - Hay otra forma de obtener el objeto asociado, por ejemplo, a través de una consulta de base de datos.

    - El objeto asociado se puede pasar como argumento a los métodos que lo utilizan.

2. Dependiendo de su situación, el uso de un campo que contiene una asociación con otro objeto debe reemplazarse por un parámetro o una llamada a método para obtener el objeto de otra manera.

3. Elimine el código que asigna el objeto asociado al campo.

4. Elimine el campo ahora no utilizado.