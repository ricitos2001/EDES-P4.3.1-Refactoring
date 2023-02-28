# Método largo (Long Method)

## Signos y síntomas

Un método contiene demasiadas líneas de código. En general, cualquier método de más de diez líneas debería llamarte la atención y empezar a preguntarte si puede hacerse algo para acortarlo.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-01.png?id=ba3b4a6d8ef25a8f676543cee5e1e019)

## Razones del problema

Conforme vamos realizando código, en muy común ir añadiendo cosas, pero rara vez te paras a ver si se puede eliminar algo. Dado que es más fácil escribir código que leerlo, este "olor" pasa desapercibido hasta que el método se convierte en una bestia parda de gran tamaño.

Mentalmente, es más difícil crear un nuevo método que hacer la llamada a uno ya existente: "Pero son solo dos líneas, no sirve de nada crear un método completo solo para eso..." Lo que significa que se agrega otra línea y luego otra...., dando a luz a una maraña de código espagueti.

## Tratamiento

Como regla general, si sientes la necesidad de comentar algo dentro de un método, debes tomar este código y ponerlo en un nuevo método. Incluso, a veces puede ser necesario que una sola línea puede y debe dividirse en un método separado, si requiere explicaciones. Y si el método tiene un nombre descriptivo, nadie necesitará mirar el código para ver qué hace.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-02.png?id=274350a92b305ae79848ab40b3bdb0cb)

> OJO SUSTITUYE LOS ENLACES A LAS DISTITNAS TRADUCCIONES QUE VAS HACIENOD. NO DEJES ENLACES A REFACTORING.GURU

* Para reducir la longitud del cuerpo de un método, utiliza [Extracción de método](./RefactoringPattern/ExtractMethod.md).
* Si las variables y los parámetros locales interfieren con la extracción de un método, usa [Reemplazar temporal con consulta](../RefactoringPattern/ReplaceTempwithQuery.md) , [Introducir objeto de parámetro](../RefactoringPattern/IntroduceParameterObject.md) o [Conservar todo el objeto](../RefactoringPattern/PreserveWholeObject.md) .
* Si ninguna de las recetas anteriores ayuda, intenta mover todo el método a un objeto separado a través de [Reemplazar método con objeto de método](../RefactoringPattern/ReplaceMethodWithMethodObject.md) .
* Los operadores condicionales y los bucles son una buena pista de que el código se puede mover a un método separado. Para condicionales, utiliza [Descomponer condicional](../RefactoringPattern/DecomposeConditional.md) . Si hay bucles en el camino, prueba [Extracción de método](./RefactoringPattern/ExtractMethod.md).

## Beneficios

* Entre todos los tipos de código orientado a objetos, las clases con métodos cortos viven más tiempo. Cuanto más largo es un método o función, más difícil se vuelve entenderlo y mantenerlo.
* Además, los métodos largos ofrecen el escondite perfecto para el código duplicado no deseado.

![](https://refactoring.guru/images/refactoring/content/smells/long-method-03.png?id=82ce2d388aa14bdae4e8f62b875f0259)

### Actuación

¿Un aumento en la cantidad de métodos perjudica el rendimiento, como afirman muchas personas? En casi todos los casos, el impacto es tan insignificante que ni siquiera vale la pena preocuparse.

Además, ahora que tienes un código claro y comprensible, es más probable que encuentres métodos realmente efectivos para reestructurar el código y obtener ganancias de rendimiento reales si surge la necesidad.
