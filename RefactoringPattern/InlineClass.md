# Inline Class
## Problema
* Una clase no hace casi nada y no es responsable de nada, y no se planean responsabilidades adicionales para ella.

![](https://refactoring.guru/images/refactoring/diagrams/Inline%20Class%20-%20Before.png)
## Solución
* Mueva todas las características de la clase a otra.

![](https://refactoring.guru/images/refactoring/diagrams/Inline%20Class%20-%20After.png)
## Por qué refactorizar
A menudo, esta técnica es necesaria después de que las características de una clase se "transplantan" a otras clases, dejando a esa clase con poco que hacer.
## Beneficios
La eliminación de clases innecesarias libera memoria operativa en la computadora y ancho de banda en su cabeza.
## Como refactorizar
1. En la clase receptora, cree los campos y métodos públicos presentes en la clase donante. Los métodos deben hacer referencia a los métodos equivalentes de la clase donante.
2. Reemplace todas las referencias a la clase donante con referencias a los campos y métodos de la clase receptora.
3. Ahora pruebe el programa y asegúrese de que no se hayan agregado errores. Si las pruebas muestran que todo funciona correctamente, comience a usar [Move Method](https://refactoring.guru/es/move-method) y [Move Field](https://refactoring.guru/es/move-field) para trasplantar por completo todas las funciones a la clase receptora desde la original. Continúe haciéndolo hasta que la clase original esté completamente vacía.
4. Elimina la clase original.