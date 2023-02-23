# Borrar Parametro (Remove Parameter)

## Problema
* Un parámetro no se utiliza en el cuerpo de un método.

![](https://refactoring.guru/images/refactoring/diagrams/Remove%20Parameter%20-%20Before.png)

## Solución
* Elimina el parámetro no utilizado.

![](https://refactoring.guru/images/refactoring/diagrams/Remove%20Parameter%20-%20After.png)

## Por qué refactorizar
Cada parámetro en una llamada de método obliga al programador que lo lee a descubrir qué información se encuentra en ese parámetro. Y si un parámetro no se utiliza en absoluto en el cuerpo del método, este "rascarse la cabeza" es en vano.

Y en cualquier caso, los parámetros adicionales son código adicional que debe ejecutarse.

A veces agregamos parámetros con la vista puesta en el futuro, anticipando cambios en el método para los cuales podría necesitarse el parámetro. Sin embargo, la experiencia muestra que es mejor agregar un parámetro solo cuando realmente se necesita. Después de todo, los cambios anticipados a menudo siguen siendo eso: anticipados.

## Beneficios

Un método contiene solamente los parámetros que realmente necesita.

## Cuando no usar

Si el método se implementa de diferentes maneras en las subclases o en una superclase, y su parámetro se utiliza en esas implementaciones, deje el parámetro tal cual.

## Como refactorizar

1- Verifique si el método está definido en una superclase o subclase. Si es así, ¿se utiliza el parámetro allí? Si el parámetro se utiliza en una de estas implementaciones, posponga esta técnica de refactorización.

2- El siguiente paso es importante para mantener el programa funcional durante el proceso de refactorización. Cree un nuevo método copiando el antiguo y elimine el parámetro correspondiente. Reemplace el código del antiguo método por una llamada al nuevo método.

3- Encuentre todas las referencias al antiguo método y reemplácelas por referencias al nuevo método.

4- Elimine el antiguo método. No realice este paso si el antiguo método forma parte de una interfaz pública. En este caso, marque el antiguo método como obsoleto.