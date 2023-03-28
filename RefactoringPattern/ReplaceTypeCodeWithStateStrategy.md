# Reemplazar el código de tipo por estado/estrategia

## ¿Qué es el código de tipo? 

El código de tipo ocurre cuando, en lugar de tener un tipo de datos separado, se tiene un conjunto de números o cadenas 
que forman una lista de valores permitidos para alguna entidad. A menudo, estos números y cadenas específicos reciben 
nombres comprensibles a través de constantes, lo que explica por qué se encuentra este código de tipo con tanta 
frecuencia.

## Problema

Tienes un tipo codificado que afecta el comportamiento, pero no puedes usar subclases para eliminarlo.

![](https://refactoring.guru/images/refactoring/diagrams/Replace%20Type%20Code%20with%20State-Strategy%20-%20Before.png?id=5fa75a3c084933dcb4d1d1f0c60e56d3)

## Solución

Reemplaza el código de tipo con un objeto de estado. Si es necesario reemplazar el valor del campo con código de tipo, 
se "enchufa" otro objeto de estado.

![](https://refactoring.guru/images/refactoring/diagrams/Replace%20Type%20Code%20with%20State-Strategy%20-%20After.png?id=1fb190a5b389c0a88e7335648b869748)

## Por qué refactorizar

Tienes código de tipo y afecta el comportamiento de una clase, por lo tanto, no podemos usar [Reemplazar código de tipo 
con clase](ReplaceTypeCodeWithClass.md).

El código de tipo afecta el comportamiento de una clase, pero no podemos crear subclases para el tipo codificado debido 
a la jerarquía de clases existente u otras razones. Esto significa que no podemos aplicar [Reemplazar código de tipo con 
subclases](ReplaceTypeCodewithSubclasses.md).

## Beneficios

* Esta técnica de refactorización es una forma de salir de situaciones en las que un campo con un tipo codificado cambia 
su valor durante la vida útil del objeto. En este caso, se realiza el reemplazo del valor mediante el reemplazo del 
objeto de estado al que se refiere la clase original.

* Si necesita agregar un nuevo valor de un tipo codificado, todo lo que necesita hacer es agregar una nueva subclase de 
estado sin alterar el código existente (cf. el Principio Abierto/Cerrado).

## Desventajas

Si tiene un caso simple de código de tipo pero utiliza esta técnica de refactorización de todos modos, tendrá muchas 
clases adicionales (y no necesarias).

## Bueno Saber

La implementación de esta técnica de refactorización puede hacer uso de uno de dos patrones de diseño: Estado o 
Estrategia. La implementación es la misma sin importar qué patrón elija. Entonces, ¿qué patrón debería elegir en una 
situación particular?

Si está tratando de dividir una condicional que controla la selección de algoritmos, use Estrategia.

Pero si cada valor del tipo codificado es responsable no solo de seleccionar un algoritmo sino de toda la condición de 
la clase, el estado de la clase, los valores de los campos y muchas otras acciones, Estado es mejor para el trabajo.

## Cómo refactorizar

1. Use [Encapsulamiento de campo](SelfEncapsulateField.md) para crear un getter para el campo que contiene el código de 
tipo.

2. Cree una nueva clase y déle un nombre comprensible que se adapte al propósito del código de tipo. Esta clase 
desempeñará el papel de estado (o estrategia). En ella, cree un getter abstracto para el campo codificado.

3. Cree subclases de la clase de estado para cada valor del código de tipo. En cada subclase, redefina el getter del 
campo codificado para que devuelva el valor correspondiente del código de tipo.

4. En la clase abstracta de estado, cree un método de fábrica estático que acepte el valor del código de tipo como 
parámetro. Dependiendo de este par

5. En la clase original, cambia el tipo del campo de código de tipo a la clase de estado. En el setter del campo, llama 
al método de fábrica de estado para obtener nuevos objetos de estado.

6. Luego, puedes empezar a mover los campos y métodos de la superclase a las subclases de estado correspondientes (usando 
las técnicas de [Empujar Campo Hacia abajo](PushDownField.md) y [Empujar Metodo Hacia Abajo](PushDownMethod.md)).

7. Cuando todo lo que se pueda mover haya sido movido, utiliza 
[Reemplazar Condicional con Polymorphism](ReplaceConditionalWithPolymorphism.md) para deshacerte de las condiciones que 
usan el código de tipo de una vez por todas.

## Refactorings Similares

[Reemplazar Codigo Tipo con Clase](ReplaceTypeCodeWithClass.md)

[Reemplazar Codigo Tipo con Sub-clases](ReplaceTypeCodewithSubclasses.md)

## Implements Design Patterns

[Estado](https://refactoring.guru/es/design-patterns/state)

[Estrategia](https://refactoring.guru/es/design-patterns/strategy)

## Elimina Olor

[Obsesion Primitiva](../CodeSmell/PrimitiveObsession.md)