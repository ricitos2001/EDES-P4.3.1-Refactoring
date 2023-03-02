# Introducir objeto nulo
## Problema
Dado que algunos métodos regresan nullen lugar de objetos reales, tiene muchas comprobaciones nullen su código.

## Solución
En lugar de null, devuelva un objeto nulo que muestre el comportamiento predeterminado.

## Por qué refactorizar
Docenas de comprobaciones para nullhacer que su código sea más largo y feo.

## Inconvenientes
El precio de deshacerse de los condicionales es crear otra nueva clase.

## Cómo refactorizar
1. A partir de la clase en cuestión, cree una subclase que desempeñará el papel de objeto nulo.

2. En ambas clases, cree el método isNull(), que devolverá truepara un objeto nulo y falsepara una clase real.

3. Encuentre todos los lugares donde el código puede regresar nullen lugar de un objeto real. Cambie el código para que devuelva un objeto nulo.

4. Encuentre todos los lugares donde se comparan las variables de la clase real null. Reemplace estos cheques con una llamada de isNull().

5. - Si los métodos de la clase original se ejecutan en estos condicionales cuando un valor no es igual a null, redefina estos métodos en la clase nula e inserte el código de la elseparte de la condición allí. Luego puede eliminar todo el comportamiento condicional y diferente se implementará a través del polimorfismo.
   - Si las cosas no son tan simples y los métodos no se pueden redefinir, vea si puede simplemente extraer los operadores que se suponía que debían realizarse en el caso de un valor nullpara los nuevos métodos del objeto nulo. Llame a estos métodos en lugar del código anterior elsecomo operaciones predeterminadas.