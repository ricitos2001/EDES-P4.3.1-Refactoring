# Reemplazar valor de datos por objeto

## Problema

Una clase (o grupo de clases) contiene un campo de datos. El campo tiene su propio comportamiento y datos asociados.

 ## Solución

Crear una nueva clase, colocar el antiguo campo y su comportamiento en la clase, y almacenar el objeto de la clase en la 
clase original.

Reemplazar valor de datos por objeto - Antes
![](https://refactoring.guru/images/refactoring/diagrams/Replace%20Data%20Value%20with%20Object%20-%20Before.png)

Reemplazar valor de datos por objeto - Después
![](https://refactoring.guru/images/refactoring/diagrams/Replace%20Data%20Value%20with%20Object%20-%20After.png)

## Por qué refactorizar

Esta refactorización es básicamente un caso especial de [Extraer Clase](ExtractClass.md). Lo que la hace diferente es la 
causa de la refactorización.

En [Extraer Clase](ExtractClass.md), tenemos una sola clase que es responsable de diferentes cosas y queremos dividir 
sus responsabilidades.

Con el reemplazo de un valor de datos por un objeto, tenemos un campo primitivo (número, cadena, etc.) que ya no es tan 
simple debido al crecimiento del programa y ahora tiene datos y comportamientos asociados. Por un lado, no hay nada que 
temer en estos campos en sí mismos. Sin embargo, esta familia de campos y comportamientos puede estar presente en varias 
clases simultáneamente, creando código duplicado.

Por lo tanto, creamos una nueva clase y movemos tanto el campo como los datos y comportamientos relacionados a ella.

## Beneficios

Mejora la relación dentro de las clases. Los datos y los comportamientos relevantes están dentro de una sola clase.

## Cómo refactorizar

Antes de comenzar con la refactorización, vea si hay referencias directas al campo desde dentro de la clase. Si es así, 
use [Autoencapsulamiento](SelfEncapsulateField.md) del Campo para ocultarlo en la clase original.

1. Cree una nueva clase y copie su campo y getter relevante. Además, cree un constructor que acepte el valor simple del 
campo. Esta clase no tendrá un setter ya que cada nuevo valor de campo que se envíe a la clase original creará un nuevo 
objeto de valor.

2. En la clase original, cambie el tipo de campo a la nueva clase.

3. En el getter de la clase original, invoque el getter del objeto asociado.

4. En el setter, cree un nuevo objeto de valor. Es posible que también necesite crear un nuevo objeto en el constructor si 
se habían establecido valores iniciales allí para el campo anteriormente.

## Siguientes pasos

Después de aplicar esta técnica de refactorización, es conveniente aplicar [Cambiar Valor a Referencia](ChangeValueToReference.md) en el campo que 
contiene el objeto. Esto permite almacenar una referencia a un solo objeto que corresponde a un valor en lugar de 
almacenar docenas de objetos para un mismo valor.

Con mayor frecuencia, este enfoque es necesario cuando se desea que un objeto sea responsable de un objeto del mundo 
real (como usuarios, pedidos, documentos, etc.). Al mismo tiempo, este enfoque no será útil para objetos como fechas, 
dinero, rangos, etc.

## Refacotrizaciones Similares

[Extraer Clase](ExtractClass.md)

[Introducir Objeto Parametro](IntroduceParameterObject.md)

[Reemplazar Array con Objeto](ReplaceArrayWithObject.md)

[Reemplazar Metodo con Objeto Metodo](ReplaceMethodWithMethodObject.md)

## Eliminar Olores

[Codigo Duplicado](../CodeSmell/DuplicateCode.md)
