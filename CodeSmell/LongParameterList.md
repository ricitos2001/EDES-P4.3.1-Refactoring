# LISTA LARGA DE PARAMETROS

## SIGNOS Y SINTOMAS
    -Más de tres o cuatro parámetros para un mismo método.


## RAZONES DEL PROBLEMA
    -Una larga lista de parámetros puede ocurrir después de fusionar varios tipos de algoritmos en un solo método. Es posible que se haya creado una larga lista para controlar qué algoritmo se ejecutará y cómo.

    -Las largas listas de parámetros también pueden ser el subproducto de los esfuerzos por hacer que las clases sean más independientes entre sí. Por ejemplo, el código para crear objetos específicos necesarios en un método se movió del método al código para llamar al método, pero los objetos creados se pasan al método como parámetros. Por lo tanto, la clase original ya no conoce las relaciones entre los objetos y la dependencia ha disminuido. Pero si se crean varios de estos objetos, cada uno de ellos requerirá su propio parámetro, lo que significa una lista de parámetros más larga.

    -Es difícil entender este tipo de listas, que se vuelven contradictorias y difíciles de usar a medida que crecen. En lugar de una larga lista de parámetros, un método puede usar los datos de su propio objeto. Si el objeto actual no contiene todos los datos necesarios, se puede pasar otro objeto (que obtendrá los datos necesarios) como parámetro de método.

## TRATAMIENTO
    -Compruebe qué valores se pasan a los parámetros. Si algunos de los argumentos son solo resultados de llamadas a métodos de otro objeto, use Reemplazar parámetro con llamada a método . Este objeto puede colocarse en el campo de su propia clase o pasarse como un parámetro de método.

    -En lugar de pasar un grupo de datos recibidos de otro objeto como parámetros, pase el objeto mismo al método, usando Preserve Whole Object .

    -Si hay varios elementos de datos no relacionados, a veces puede fusionarlos en un solo objeto de parámetro a través de Introducir objeto de parámetro .


## RECOMPENSA
    -Código más legible y más corto.

    -La refactorización puede revelar código duplicado que antes no se había detectado.

## CUANDO IGNORAR
    -No se deshaga de los parámetros si hacerlo causaría una dependencia no deseada entre las clases.