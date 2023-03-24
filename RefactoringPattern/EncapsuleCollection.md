# Encapsule Collection

## Problema
Una clase contiene un campo de colección y un simple getter y setter para trabajar con la colección.

![Encapsular colección - Antes](https://refactoring.guru/images/refactoring/diagrams/Encapsulate%20Collection%20-%20Before.png)

## Solución
Hacer que el valor devuelto por el getter sea de solo lectura y crear métodos para agregar/eliminar elementos de la colección.

![Encapsular colección - Después](https://refactoring.guru/images/refactoring/diagrams/Encapsulate%20Collection%20-%20After.png)

## Por qué refactorizar
Una clase contiene un campo que contiene una colección de objetos. Esta colección podría ser un array, 
lista, conjunto o vector. Se ha creado un getter y setter normal para trabajar con la colección.

Pero las colecciones deberían ser utilizadas por un protocolo un poco diferente al utilizado por otros tipos de datos. 
El método getter no debería devolver el objeto de colección en sí, ya que esto permitiría a los clientes cambiar el 
contenido de la colección sin el conocimiento de la clase propietaria. Además, esto mostraría demasiadas estructuras 
internas de los datos del objeto a los clientes. El método para obtener elementos de la colección debería devolver un 
valor que no permita cambiar la colección o revelar datos excesivos sobre su estructura.

Además, no debería haber un método que asigne un valor a la colección. En su lugar, debería haber operaciones para 
agregar y eliminar elementos. Gracias a esto, el objeto propietario gana control sobre la adición y eliminación de
elementos de la colección.

Este protocolo encapsula adecuadamente una colección, lo que en última instancia reduce el grado de asociación entre 
la clase propietaria y el código del cliente.

## Beneficios
- El campo de colección está encapsulado dentro de una clase. Cuando se llama al getter, devuelve una copia de la
colección, lo que evita cambiar o sobrescribir accidentalmente los elementos de la colección sin el conocimiento de 
la clase que contiene la colección.

- Si los elementos de la colección están contenidos en un tipo primitivo, como un array, puede crear métodos más 
convenientes para trabajar con la colección.

- Si los elementos de la colección están contenidos en un contenedor no primitivo (clase de colección estándar), 
al encapsular la colección, puede restringir el acceso a los métodos estándar no deseados de la colección 
(como restringir la adición de nuevos elementos).

## Cómo refactorizar
1. Cree métodos para agregar y eliminar elementos de la colección. Deben aceptar elementos de colección en sus parámetros.

2. Asigne una colección vacía al campo como valor inicial si esto no se hace en el constructor de la clase.

3. Encuentre las llamadas del setter del campo de colección. Cambie el setter para que use operaciones para agregar y 
eliminar elementos, o haga que estas operaciones llamen al código del cliente.

> Tenga en cuenta que los setters solo se pueden usar para reemplazar todos los elementos de la colección por otros. 
Por lo tanto, puede ser recomendable cambiar el nombre del setter ([Rename Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/RenameMethod.md)) 
a reemplazar.

4. Encuentre todas las llamadas del getter de la colección después de las cuales se cambia la colección. Cambie el 
código para que use sus nuevos métodos para agregar y eliminar elementos de la colección.

5. Cambia el getter para que devuelva una representación de solo lectura de la colección.

6. Inspeccione el código del cliente que usa la colección para ver qué código se vería mejor dentro de la propia clase de colección.