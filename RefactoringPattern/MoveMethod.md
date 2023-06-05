# Move Method
## Problema
* Un método se usa más en otra clase que en su propia clase.

![](https://refactoring.guru/images/refactoring/diagrams/Move%20Method%20-%20Before.png)
## Solución
* Cree un nuevo método en la clase que más utilice el método y, a continuación, mueva el código del método anterior 
allí. Convierta el código del método original en una referencia al nuevo método en la otra clase o elimínelo por
completo.

![](https://refactoring.guru/images/refactoring/diagrams/Move%20Method%20-%20After.png)
## Por qué refactorizar
1. Desea mover un método a una clase que contiene la mayoría de los datos utilizados por el método. Esto hace que las 
clases sean más coherentes internamente.
2. Desea mover un método para reducir o eliminar la dependencia de la clase que llama al método en la clase en la que
se encuentra. Esto puede ser útil si la clase que llama ya depende de la clase a la que planea mover el método.
Esto reduce la dependencia entre clases.
## Como refactorizar
1. Verifique todas las funciones utilizadas por el método anterior en su clase. Puede ser una buena idea moverlos también. Como regla general, si una característica es utilizada solo por el método en consideración, ciertamente debe mover la característica a él. Si la característica también es utilizada por otros métodos, también debe mover estos métodos. A veces es mucho más fácil mover una gran cantidad de métodos que establecer relaciones entre ellos en diferentes clases.

    Asegúrese de que el método no esté declarado en superclases y subclases. Si este es el caso, deberá abstenerse de moverse o implementar una especie de polimorfismo en la clase receptora para garantizar la funcionalidad variable de un método dividido entre las clases donantes.
2. Declare el nuevo método en la clase del destinatario. Es posible que desee dar un nuevo nombre al método que sea más apropiado para él en la nueva clase.
3. Decida cómo se referirá a la clase receptora. Es posible que ya tenga un campo o método que devuelva un objeto apropiado, pero si no es así, deberá escribir un nuevo método o campo para almacenar el objeto de la clase receptora. 

    Ahora tiene una forma de referirse al objeto destinatario y un nuevo método en su clase. Con todo esto en su haber, puede convertir el antiguo método en una referencia al nuevo método.

4. Eche un vistazo: ¿puede eliminar el método anterior por completo? Si es así, coloque una referencia al nuevo método en todos los lugares que usan el anterior.