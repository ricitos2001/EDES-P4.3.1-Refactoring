# Renombrar Método (Rename Method)

## Problema

El nombre de un método no explica lo que hace el método.

![](https://refactoring.guru/images/refactoring/diagrams/Rename%20Method%20-%20Before.png?id=7943798ae9db6b5b232860eed6262462)

## Solución

Renombrar el método para que quede más claro que realiza dicho método.

![](https://refactoring.guru/images/refactoring/diagrams/Rename%20Method%20-%20After.png?id=62b4e6747951bbbacba3ede379fef200)

## Por qué Refactorizar
Tal vez un método fue mal nombrado desde el principio, por ejemplo, 
alguien creó el método a toda prisa y no prestó el cuidado adecuado a nombrarlo bien.

O tal vez el método estaba bien nombrado al principio, 
pero a medida que su funcionalidad creció, el nombre del método dejó de ser un buen descriptor.

## Beneficios

Legibilidad del código. Intente darle al nuevo método un nombre que refleje lo que hace. 
Algo así como createOrder(), renderCustomerInfo(), etc.

## Cómo refactorizar

1. Vea si el método está definido en una superclase o subclase. 
Si es así, también debe repetir todos los pasos de estas clases.

2. El siguiente método es importante para mantener la funcionalidad del programa durante el proceso de refactorización. 
Cree un nuevo método con un nombre nuevo. Copie el código del método antiguo en él. 
Elimine todo el código del método antiguo y, en su lugar, inserte una llamada para el nuevo método.

3. Busque todas las referencias al método antiguo y reemplácelas con referencias al nuevo.

4. Elimine el método anterior. Si el método antiguo forma parte de una interfaz pública, no realice este paso. 
En su lugar, marque el método antiguo como obsoleto.