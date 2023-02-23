#Eliminar intermediario

##Problema

Una clase tiene demasiados métodos que simplemente delegan a otros objetos.

##Solución

Elimine estos métodos y obligue al cliente a llamar directamente a los métodos finales.

Quitar intermediario - Antes

Quitar intermediario - Después

##Por qué refactorizar

Para describir esta técnica, usaremos los términos de Hide Delegate , que son:

El servidor es el objeto al que el cliente tiene acceso directo.

Delegado es el objeto final que contiene la funcionalidad que necesita el cliente.

Hay dos tipos de problemas:

- La clase de servidor no hace nada por sí misma y simplemente crea una complejidad innecesaria. En este caso, piense si esta clase es necesaria en absoluto.

- Cada vez que se agrega una nueva función al delegado , debe crear un método de delegación para ello en la clase de servidor . Si se realizan muchos cambios, esto será bastante tedioso.

##Cómo refactorizar

Cree un captador para acceder al objeto de clase delegado desde el objeto de clase de servidor .

Reemplace las llamadas a los métodos de delegación en la clase de servidor con llamadas directas a los métodos en la clase de delegado .
