# Obsesión Primitiva

## Signos y Síntomas

· Uso de primitivos en vez de objetos pequeños para tareas simples (como divisas, rangos, cadenas especiales para números de teléfono, etc.) 

· Uso de constantes para codificar información (cómo USER_ADMIN_ROLE = 1 para referirse a usuarios con derechos de administrador).

· Uso de constantes como nombres de campos en matrices de datos.

## Razones del Problema
 
Al igual que la mayoría de los olores, la obsesión por los tipos primitivos (Int, Long, Double, String, etc.) nacen en momentos de debilidad. "¡Solo un campo para almacenar un dato!", dijo el programador. Crear una variable de tipo primitivo es mucho más fácil que crear una clase completamente nueva, ¿verdad? Y así se hizo. Luego se necesitó otro campo y se agregó de la misma manera. ¡Al final tenemos una clase enorme e inmanejable!

A menudo, los primitivos se usan para "simular" una clase. En lugar de tener un tipo de dato separado, tienes un conjunto de números o cadenas que forman la lista de valores permitidos para alguna entidad. Luego, mediante constantes, se les asignan nombres fáciles de entender a estos números y cadenas, por eso se encuentran dispersos por todas partes.

Otro ejemplo de un mal uso de los primitivos es la simulación de campos. La clase contiene una gran variedad de datos y constantes (declaradas en la clase) que se utilizan como índices de matriz para obtener estos datos: `matriz[NOMBRE]`, `matriz` almacena los datos y la constante `NOMBRE` indica el indice donde se almacena un dato.

## Tratamiento

· Si tienes una gran variedad de campos primitivos, puede ser posible agrupar lógicamente algunos de ellos en su propia clase. Incluso mejor, mueve también el comportamiento asociado a estos datos dentro de la clase. Para esta tarea, intenta reemplazar los datos con un Objeto.

· Si los valores de los campos primitivos se utilizan en los parámetros de los métodos, utiliza Introduce Parameter Object o Preserve Whole Object.

· Cuando datos complicados se codifican en variables, utiliza Replace Type Code with Class, Replace Type Code with Subclasses o Replace Type Code with State/Strategy.

· Si hay arreglos entre las variables, utiliza Replace Array with Object.

## Beneficios

· El código se vuelve más flexible gracias al uso de objetos en lugar de primitivas.

· Mejora la comprensibilidad y organización del código. Las operaciones en datos específicos se encuentran en el mismo lugar, en lugar de estar dispersas. Ya no hay que adivinar la razón de todas estas constantes extrañas y por qué están en un arreglo.

· Es más fácil encontrar código duplicado.