# Obsesión Primitiva

## Signos y Síntomas

· Uso de primitivos en vez de objetos pequeños para tareas simples (como divisas, rangos, cadenas especiales para números de teléfono, etc.) 

· Uso de constantes para codificar información (cómo USER_ADMIN_ROLE = 1 para referirse a usuarios con derechos de administrador).

· Uso de constantes cadenas para usar como nombres de campos en matrices de datos.

## Razones del Problema
 
Al igual que la mayoría de los olores, las obsesiones primitivas nacen en momentos de debilidad. "¡Solo un campo para almacenar algunos datos!", dijo el programador. Crear un campo primitivo es mucho más fácil que crear una clase completamente nueva, ¿verdad? Y así se hizo. Luego se necesitó otro campo y se agregó de la misma manera. ¡He aquí que la clase se volvió enorme e inmanejable!

A menudo, los primitivos se usan para "simular" tipos. En lugar de tener un tipo de datos separado, tienes un conjunto de números o cadenas que forman la lista de valores permitidos para alguna entidad. Luego se les asignan nombres fáciles de entender a estos números y cadenas específicos mediante constantes, por eso se encuentran dispersos por todas partes.

Otro ejemplo de un mal uso de los primitivos es la simulación de campos. La clase contiene una gran variedad de datos y constantes de cadenas (que se especifican en la clase) se utilizan como índices de matriz para obtener estos datos.

## Tratamiento

· Si tienes una gran variedad de campos primitivos, puede ser posible agrupar lógicamente algunos de ellos en su propia clase. Incluso mejor, mueve también el comportamiento asociado a estos datos dentro de la clase. Para esta tarea, intenta Reemplazar el Valor de Datos con un Objeto.

· Si los valores de los campos primitivos se utilizan en los parámetros de los métodos, utiliza Introduce Parameter Object o Preserve Whole Object.

· Cuando datos complicados se codifican en variables, utiliza Replace Type Code with Class, Replace Type Code with Subclasses o Replace Type Code with State/Strategy.

· Si hay arreglos entre las variables, utiliza Replace Array with Object.

## Beneficios

· El código se vuelve más flexible gracias al uso de objetos en lugar de primitivas.

· Mejora la comprensibilidad y organización del código. Las operaciones en datos específicos se encuentran en el mismo lugar, en lugar de estar dispersas. Ya no hay que adivinar la razón de todas estas constantes extrañas y por qué están en un arreglo.

· Es más fácil encontrar código duplicado.