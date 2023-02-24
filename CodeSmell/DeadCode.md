# CODIGO MUERTO

## SIGNOS Y SINTOMAS
    -Una variable, parámetro, campo, método o clase ya no se usa (generalmente porque está obsoleto).


## RAZONES DEL PROBLEMA
    -Cuando los requisitos para el software cambiaron o se hicieron correcciones, nadie tuvo tiempo de limpiar el código anterior.

    -Dicho código también podría encontrarse en condicionales complejos, cuando una de las ramas se vuelve inalcanzable (debido a un error u otras circunstancias).

## TRATAMIENTO
    -La forma más rápida de encontrar código muerto es usar un buen IDE .

    -Elimine el código no utilizado y los archivos innecesarios.

    -En el caso de una clase innecesaria, se puede aplicar Inline Class o Collapse Hierarchy si se usa una subclase o una superclase.

    -Para eliminar parámetros innecesarios, utilice Eliminar parámetro .


## RECOMPENSA
    -Tamaño de código reducido.

    -Soporte más sencillo.