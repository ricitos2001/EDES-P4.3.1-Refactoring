# Preservar Objeto Completo

## Problema

Obtienes varios valores de un objeto y luego los pasas como parámetros a un método.

```Java
int low = daysTempRange.getLow();
int high = daysTempRange.getHigh();
boolean withinPlan = plan.withinRange(low, high);
```

## Solución

En su lugar, intenta pasar el objeto completo.

```Java
boolean withinPlan = plan.withinRange(daysTempRange);
```

## Por qué refactorizar

El problema es que cada vez que se llama al método, se deben llamar a los métodos del objeto futuro del parámetro. Si estos métodos o la cantidad de datos obtenidos para el método cambian, deberás buscar cuidadosamente una docena de lugares en el programa e implementar estos cambios en cada uno de ellos.

Después de aplicar esta técnica de refactorización, el código para obtener todos los datos necesarios se almacenará en un solo lugar: el propio método.

## Beneficios

En lugar de una mezcolanza de parámetros, se ve un solo objeto con un nombre comprensible.

Si el método necesita más datos de un objeto, no necesitarás reescribir todos los lugares donde se utiliza el método, sino solo dentro del método en sí.

## Desventajas

A veces, esta transformación hace que un método sea menos flexible: antes el método podía obtener datos de muchas fuentes diferentes, pero ahora, debido a la refactorización, estamos limitando su uso solo a objetos con una interfaz particular.

## Cómo Refactorizar

Crea un parámetro en el método para el objeto del cual puedes obtener los valores necesarios.

Ahora comienza a eliminar los antiguos parámetros del método uno por uno, reemplazándolos con llamadas a los métodos relevantes del objeto de parámetro. Prueba el programa después de cada reemplazo de parámetro.

Elimina el código getter del objeto de parámetro que había precedido a la llamada del método.

## Refactorizaciones similar

[Introducir Objeto de Parametro](../RefactoringPattern/IntroduceParameterObject.md)

[Reemplazar Parametro con Llamada a Metodo](../RefactoringPattern/ReplaceParameterWithMethodCall.md)

## Elimina olor

[Obsesion Primitiva](../CodeSmell/PrimitiveObsession.md)

[List de Parametros Largos](../CodeSmell/LongParameterList.md)

[Metodo Largo](../CodeSmell/LongMethod.md)

[Grupo de Data](../CodeSmell/DataClumps.md)