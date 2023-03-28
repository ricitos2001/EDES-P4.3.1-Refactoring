# Extraer Subclase

## Problema

Una clase tiene características que se utilizan solo en ciertos casos.

![](https://refactoring.guru/images/refactoring/diagrams/Extract%20Subclass%20-%20Before.png)

## Solución

Crear una subclase y utilizarla en estos casos.

![](https://refactoring.guru/images/refactoring/diagrams/Extract%20Subclass%20-%20After.png)

## Por qué Refactorizar

Tu clase principal tiene métodos y campos para implementar un caso de uso raro para la clase. Aunque el caso es raro, 
la clase es responsable de él y sería incorrecto mover todos los campos y métodos asociados a una clase completamente 
separada. Pero podrían trasladarse a una subclase, que es precisamente lo que haremos con la ayuda de esta técnica de 
refactorización.

## Beneficios

* Crea una subclase rápidamente y fácilmente.

* Puedes crear varias subclases separadas si tu clase principal está implementando más de un caso especial de este tipo.

## Desventajas

A pesar de su aparente simplicidad, la Herencia puede llevar a un callejón sin salida si se tiene que separar varias 
jerarquías de clases diferentes. Por ejemplo, si tuvieras la clase Perros con diferentes comportamientos dependiendo del 
tamaño y del pelaje de los perros, podrías sacar dos jerarquías:

    por tamaño: Grande, Mediano y Pequeño

    por pelaje: Suave y Peludo

Y todo parecería bien, excepto que surgirán problemas tan pronto como necesites crear un perro que sea tanto Grande como 
Suave, ya que solo puedes crear un objeto de una clase. Dicho esto, puedes evitar este problema usando Composición en 
lugar de Herencia (ver patrón Estrategia). En otras palabras, la clase Perro tendrá dos campos componentes, tamaño y 
pelaje. Insertarás objetos componentes de las clases necesarias en estos campos. Así podrás crear un Perro que tenga un 
tamaño Grande y un pelaje Peludo.

## Como Refactorizar

1. Crea una nueva subclase de la clase de interés.

2. Si necesitas datos adicionales para crear objetos desde una subclase, crea un constructor y agrega los parámetros 
necesarios. No olvides llamar a la implementación del constructor padre.

3. Encuentra todas las llamadas al constructor de la clase padre. Cuando se necesite la funcionalidad de una subclase, 
reemplaza el constructor padre por el constructor de la subclase.

4. Mueve los métodos y campos necesarios de la clase padre a la subclase. Hazlo a través de los métodos [Empujar Método 
hacia Abajo](PushDownMethod.md) y [Empujar Campo hacia Abajo](PushDownField.md). Es más fácil empezar moviendo los 
métodos primero. De esta manera, los campos permanecen accesibles durante todo el proceso: desde la clase padre antes 
del movimiento, y desde la subclase después de que se complete el movimiento.

5. Después de que la subclase esté lista, encuentra todos los campos antiguos que controlaban la elección de la 
funcionalidad. Elimina estos campos utilizando el polimorfismo para reemplazar todos los operadores en los que se 
habían utilizado los campos. Un ejemplo sencillo: en la clase Carro, tenías el campo esCarroEléctrico y, dependiendo 
de ello, en el método refuel() el carro es o bien llenado de gasolina o bien cargado de electricidad. Después de la 
refactorización, se elimina el campo esCarroEléctrico y las clases Carro y CarroEléctrico tendrán sus propias 
implementaciones del método refuel().

## Refactorings Similares

[Extraer Clase](ExtractClass.md)

## Eliminar Olor

[Clase Grande](../CodeSmell/LargeClass.md)




