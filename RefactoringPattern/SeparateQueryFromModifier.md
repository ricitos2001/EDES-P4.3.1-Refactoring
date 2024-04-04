# Separar Consulta de Modificador

## Problema

¿Tiene un método que devuelve un valor pero también cambia algo dentro de un objeto?

![](https://refactoring.guru/images/refactoring/diagrams/Separate%20Query%20from%20Modifier%20-%20Before.png)

## Solución

Divida el método en dos métodos separados. Como era de esperar, uno de ellos debería devolver el valor y el otro
modificar el objeto.

![](https://refactoring.guru/images/refactoring/diagrams/Separate%20Query%20from%20Modifier%20-%20After.png)

## Por qué Refactorizar

Esta técnica de refactorización implementa la Segregación de Responsabilidad de Comando y Consulta. Este principio nos
dice que debemos separar el código responsable de obtener datos del código que cambia algo dentro de un objeto.<br><br>El código para obtener datos se llama consulta. El código para cambiar cosas en el estado visible de un objeto se llama
modificador. Cuando se combinan una consulta y un modificador, no hay forma de obtener datos sin hacer cambios en su
condición. En otras palabras, haces una pregunta y puedes cambiar la respuesta incluso mientras la recibes. Este
problema se vuelve aún más grave cuando la persona que llama a la consulta puede no saber acerca de los "efectos
secundarios" del método, lo que a menudo lleva a errores en tiempo de ejecución.<br><br>Pero recuerde que los efectos secundarios son peligrosos solo en el caso de los modificadores que cambian el estado
visible de un objeto. Estos podrían ser, por ejemplo, campos accesibles desde la interfaz pública de un objeto, entradas
en una base de datos, en archivos, etc. Si un modificador solo almacena en caché una operación compleja y la guarda
dentro del campo privado de una clase, difícilmente puede causar efectos secundarios.

## Beneficios

Si tiene una consulta que no cambia el estado de su programa, puede llamarla tantas veces como desee sin tener que
preocuparse por cambios no deseados en el resultado causados por el simple hecho de llamar al método.

## Desventajas

En algunos casos, es conveniente obtener datos después de realizar un comando. Por ejemplo, al eliminar algo de una base
de datos, desea saber cuántas filas se eliminaron.

## Cómo Refactorizar

1. Cree un nuevo método de consulta para devolver lo que hizo el método original.

2. Cambie el método original para que devuelva solo el resultado de llamar al nuevo método de consulta.

3. Reemplace todas las referencias al método original con una llamada al método de consulta. Inmediatamente antes de
   esta línea, coloque una llamada al método modificador. Esto lo salvará de efectos secundarios en caso de que el
   método original se use en una condición de un operador condicional o un bucle.

4. Deshágase del código de devolución de valor en el método original, que ahora se ha convertido en un método
   modificador adecuado.

## Ayuda a otras refactorizaciones
[reemplazar variables temporales con consultas.](./ReplaceTempWithQuery.md)
