# Levantar Campo

## Problema

Dos clases tienen el mismo campo.

![](https://refactoring.guru/images/refactoring/diagrams/Pull%20Up%20Field%20-%20Before.png)

## Solución

Elimine el campo de las subclases y muévalo a la superclase.

![](https://refactoring.guru/images/refactoring/diagrams/Pull%20Up%20Field%20-%20After.png)

## Por qué Refactorizar

Las subclases crecieron y se desarrollaron por separado, lo que provocó la aparición de campos y métodos idénticos (o 
casi idénticos).

## Beneficios

* Elimina la duplicación de campos en las subclases.

* Facilita la posterior reubicación de métodos duplicados, si existen, de las subclases a una superclase.

## Cómo Refactorizar

1. Asegúrese de que los campos se utilizan para las mismas necesidades en las subclases.

2. Si los campos tienen nombres diferentes, déles el mismo nombre y reemplace todas las referencias a los campos en el 
código existente.

3. Cree un campo con el mismo nombre en la superclase. Tenga en cuenta que si los campos eran privados, el campo de la 
superclase debería ser protegido.

4. Elimine los campos de las subclases.

5. Es posible que desee considerar el uso de Encapsulate Field [Autoencapsulamiento](SelfEncapsulateField.md) para el 
nuevo campo, con el fin de ocultarlo detrás de los métodos de acceso.

## Anti-Refactorizar

[Bajar Campo](PushDownField.md)

## Refactoring Similar

[Levantar Metodo](PullUpMethod.md)

## Eliminar Olor

[Codigo Duplicado](../CodeSmell/DuplicateCode.md)