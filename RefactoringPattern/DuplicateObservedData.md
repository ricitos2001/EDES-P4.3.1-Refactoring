# Datos observados duplicados

## Problema
¿Los datos de dominio se almacenan en clases responsables de la GUI?

![](https://refactoring.guru/images/refactoring/diagrams/Duplicate%20Observed%20Data%20-%20Before.png?id=bd26ed6d7d9921504165fd46b7f6124c)

## Solución
Entonces es una buena idea separar los datos en clases separadas, asegurando la conexión y sincronización entre la clase de dominio y la GUI.

![](https://refactoring.guru/images/refactoring/diagrams/Duplicate%20Observed%20Data%20-%20After.png?id=b86fa0ff2f9ff7c76d4a183607153458)

Datos observados duplicados: antes
Datos observados duplicados: después
Por qué refactorizar
Desea tener múltiples vistas de interfaz para los mismos datos (por ejemplo, tiene una aplicación de escritorio y una aplicación móvil). Si no puede separar la GUI del dominio, tendrá muchas dificultades para evitar la duplicación de código y una gran cantidad de errores.

## Beneficios
Divide la responsabilidad entre las clases de lógica empresarial y las clases de presentación (cf. el Principio de responsabilidad única ), lo que hace que su programa sea más legible y comprensible.

Si necesita agregar una nueva vista de interfaz, cree nuevas clases de presentación; no necesita tocar el código de la lógica empresarial (cf. el Principio Abierto/Cerrado ).

Ahora diferentes personas pueden trabajar en la lógica empresarial y las interfaces de usuario.

## Cuándo no usar
Esta técnica de refactorización, que en su forma clásica se realiza mediante la plantilla de Observer , no se aplica a las aplicaciones web, donde todas las clases se recrean entre consultas al servidor web.

De todos modos, el principio general de extraer la lógica empresarial en clases separadas también se puede justificar para las aplicaciones web. Pero esto se implementará usando diferentes técnicas de refactorización dependiendo de cómo esté diseñado su sistema.

## Cómo refactorizar
Oculte el acceso directo a los datos del dominio en la clase GUI . Para esto, es mejor usar Self Encapsulate Field . Así que crea los getters y setters para estos datos.

En los controladores para eventos de clase GUI , use setters para establecer nuevos valores de campo. Esto le permitirá pasar estos valores al objeto de dominio asociado .

Cree una clase de dominio y copie los campos necesarios de la clase GUI . Cree getters y seters para todos estos campos.

Cree un patrón de observador para estas dos clases:

En la clase de dominio , cree una matriz para almacenar objetos de observador ( objetos GUI ), así como métodos para registrarlos, eliminarlos y notificarlos.

En la clase GUI , cree un campo para almacenar referencias a la clase de dominio , así como al update()método, que reaccionará a los cambios en el objeto y actualizará los valores de los campos en la clase GUI . Tenga en cuenta que las actualizaciones de valores deben establecerse directamente en el método para evitar la recurrencia.

En el constructor de clases de GUI , cree una instancia de clase de dominio y guárdela en el campo que ha creado. Registre el objeto GUI como observador en el objeto de dominio .

En los campos configuradores de clase de dominio , llame al método para notificar al observador (en otras palabras, método para actualizar en la clase GUI ), para pasar los nuevos valores a la GUI.

Cambie los configuradores de los campos de clase de GUI para que establezcan nuevos valores en el objeto de dominio directamente. Tenga cuidado para asegurarse de que los valores no se establezcan a través de un setter de clase de dominio ; de lo contrario, se producirá una recursividad infinita.