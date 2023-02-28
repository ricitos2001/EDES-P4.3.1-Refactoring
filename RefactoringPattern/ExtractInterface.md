# Extraer interfaz

## Problema

Múltiples clientes están usando la misma parte de la interfaz de una clase. Otro caso: parte de la interfaz en dos clases es la misma.

![](https://refactoring.guru/images/refactoring/diagrams/Extract%20Interface%20-%20Before.png)

## Solución

Mover esta porción idéntica a su propia interfaz.

![](https://refactoring.guru/images/refactoring/diagrams/Extract%20Interface%20-%20After.png)

## Por qué refactorizar

1. Las interfaces son muy apropiadas cuando las clases juegan roles especiales en diferentes situaciones. Use [Extraer interfaz] para indicar explícitamente qué papel.

2. Otro caso conveniente surge cuando es necesario describir las operaciones que una clase realiza en su servidor. Si se planea permitir el uso de servidores de múltiples tipos, todos los servidores deben implementar la interfaz.

## Bueno saber

Hay cierta similitud entre [Extraer superclase](../RefactoringPattern/ExtractSuperclass.md) y [Extraer interfaz].

Extraer una interfaz permite aislar solo las interfaces comunes, no el código común. En otras palabras, si las clases contienen [Código duplicado](../CodeSmell/DuplicateCode.md), extraer la interfaz no le ayudará a eliminar la duplicación.

De todas formas, este problema se puede mitigar aplicando [Extraer clase](../RefactoringPattern/ExtractClass.md) para mover el comportamiento que contiene la duplicación a un componente separado y delegar todo el trabajo a él. Si el comportamiento común es grande en tamaño, siempre se puede usar [Extraer superclase](../RefactoringPattern/ExtractSuperclass.md). Esto es aún más fácil, por supuesto, pero recuerde que si toma este camino solo obtendrá una clase principal.

## Cómo refactorizar

1. Cree una interfaz vacía.

2. Declarar las operaciones comunes en la interfaz.

3. Declarar las clases necesarias como implementando la interfaz.

4. Cambiar las declaraciones de tipo en el código del cliente para usar la nueva interfaz.

## Refactorizacion similar

[Extraer Superclase](../RefactoringPattern/ExtractSuperclass.md)