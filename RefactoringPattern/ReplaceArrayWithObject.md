# Reemplazar matriz con objeto

Esta técnica de refactorización es un caso especial de Reemplazar valor de datos con objeto .

## Problema 

Tenemos una matriz que contiene varios tipos de datos.

val row = arrayOfNulls<String>(2)
row[0] = "Liverpool"
row[1] = "15"

## Solución

Reemplazar la matriz con un objeto que tendrá campos separados para cada elemento.

val row = Performance()
row.name = "Liverpool"
row.wins = "15"

## Por qué refactorizar

Las matrices son una excelente herramienta para almacenar datos y colecciones de un solo tipo. Pero si usa una matriz como apartados postales, almacenando el nombre de usuario en el cuadro 1 y la dirección del usuario en el cuadro 14, algún día se sentirá muy infeliz por haberlo hecho. Este enfoque conduce a fallas catastróficas cuando alguien coloca algo en la "caja" incorrecta y también requiere su tiempo para averiguar qué datos se almacenan y dónde.

## Beneficios

· En la clase resultante, puede colocar todos los comportamientos asociados que se almacenaron previamente en la clase principal o en otro lugar.

· Los campos de una clase son mucho más fáciles de documentar que los elementos de una matriz.

## Cómo refactorizar

1.Cree la nueva clase que contendrá los datos de la matriz. Coloque la matriz en sí misma en la clase como un campo público.

2.Cree un campo para almacenar el objeto de esta clase en la clase original. No olvide crear también el objeto mismo en el lugar donde inició la matriz de datos.

3.En la nueva clase, cree métodos de acceso uno por uno para cada uno de los elementos de la matriz. Déles nombres que se expliquen por sí mismos y que indiquen lo que hacen. Al mismo tiempo, reemplace cada uso de un elemento de matriz en el código principal con el método de acceso correspondiente.

4.Cuando se hayan creado métodos de acceso para todos los elementos, haga que la matriz sea privada.

5.Para cada elemento de la matriz, cree un campo privado en la clase y luego cambie los métodos de acceso para que usen este campo en lugar de la matriz.

6.Cuando se hayan movido todos los datos, elimine la matriz.