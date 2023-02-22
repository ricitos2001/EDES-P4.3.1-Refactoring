# Comentarios (Comments)

## Signos y síntomas

Un método tiene que contener una cantidad significativa de comentarios que expliquen correctamente su funcionamiento

![](https://refactoring.guru/images/refactoring/content/smells/comments-01.png?id=584958123f3b902e0ad0895d879509b9)

## Razones del problema

Los comentarios generalmente se crean con las mejores intenciones, cuando el autor se da cuenta de que su código no es intuitivo ni obvio. En tales casos, los comentarios son como un desodorante que enmascara el olor del código sospechoso que podría mejorarse.

> El mejor comentario es un buen nombre para un método o clase

Si cree que un fragmento de código no se puede entender sin comentarios, intente cambiar la estructura del código de manera que los comentarios sean innecesarios.

## Tratamiento

* Si un comentario está destinado a explicar una expresión compleja, la expresión debe ser dividida en subexpresiones comprensibles utilizando la técnica de [Extracción de variable](https://refactoring.guru/es/extract-variable).

* Si un comentario explica una sección de código, esta sección se puede convertir en un método separado mediante la técnica de [Extracción de método](./RefactoringPattern/ExtractMethod.md). El nombre del nuevo método puede ser tomado del propio texto del comentario, muy probablemente.

* Si un método ya ha sido extraído, pero aún son necesarios comentarios para explicar lo que hace el método, dale al método un nombre autoexplicativo. Usa la técnica de [Renombrar Método](https://refactoring.guru/es/rename-method) para hacerlo.

* Si necesitas afirmar reglas sobre un estado que es necesario para que el sistema funcione, utiliza la técnica de [Introducir Assercion](https://refactoring.guru/es/introduce-assertion).

## Beneficios

* El código se vuelve más intuitivo y evidente.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-03.png?id=82ce2d388aa14bdae4e8f62b875f0259)

## Cuando ignorar

Los comentarios pueden ser utiles cuando:

* Cuando se explica por qué algo se está implementando de una manera particular.

* Cuando se explican algoritmos complejos (cuando se han intentado todos los demás métodos para simplificar el algoritmo y han fallado).
