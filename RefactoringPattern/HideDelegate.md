# Ocultar Delegado
## Problema
El cliente obtiene el objeto B de un campo o método del objeto A. Luego, el cliente llama a un método del objeto B.

![](\assets\Hide Delegate-Before.png)

## Solución
Crea un nuevo método en la clase A que delegue la llamada al objeto B. Ahora el cliente no conoce ni depende de la clase B.

![](\assets\Hide Delegate-After.png)

## Por qué Refactorizar
Para empezar, veamos la terminología:

 · El servidor es el objeto al que el cliente tiene acceso directo.

 · El delegado es el objeto final que contiene la funcionalidad necesaria para el cliente.

Una cadena de llamadas aparece cuando un cliente solicita un objeto de otro objeto, luego el segundo objeto solicita otro, y así sucesivamente. Estas secuencias de llamadas involucran al cliente en la navegación a lo largo de la estructura de clases. Cualquier cambio en estas interrelaciones requerirá cambios en el lado del cliente.

## Beneficios
Oculta la delegación al cliente. Cuanto menos código del cliente necesite conocer los detalles de las relaciones entre objetos, más fácil será realizar cambios en tu programa.

## Desventajas
Si necesitas crear un número excesivo de métodos de delegación, la clase del servidor corre el riesgo de convertirse en un intermediario innecesario, lo que conduce a un exceso de "Middle Man".

## Cómo Refactorizar
 1. Para cada método de la clase delegada llamado por el cliente, crea un método en la clase del servidor que delegue la llamada a la clase delegada.

 2. Cambia el código del cliente para que llame a los métodos de la clase del servidor.

 3. Si tus cambios liberan al cliente de la necesidad de la clase delegada, puedes eliminar el método de acceso a la clase delegada de la clase del servidor (el método que originalmente se utilizaba para obtener la clase delegada).