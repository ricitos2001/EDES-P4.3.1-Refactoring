# CADENAS DE MENSAJES

## SIGNOS Y SINTOMAS
    -En el código,podemos ver una serie de llamadas que se asemejan a $a->b()->c()->d()

## RAZONES DEL PROBLEMA
    -Una cadena de mensajes ocurre cuando un cliente solicita otro objeto, ese objeto solicita otro más, y así sucesivamente. Estas cadenas significan que el cliente depende de la navegación a lo largo de la estructura de clases. Cualquier cambio en estas relaciones requiere modificar el cliente.

## TRATAMIENTO
    - Para eliminar una cadena de mensajes, usar Hide Delegate .

    -A veces es mejor pensar por qué se usa el objeto final. Tal vez tendría sentido usar el Método de extracción para esta funcionalidad y moverlo al comienzo de la cadena, usando el Método de movimiento .


## RECOMPENSA
    -Reduce las dependencias entre las clases de una cadena.

    -Reduce la cantidad de código inflado.

## CUANDO IGNORARLO
    -La ocultación de delegados demasiado agresiva puede generar un código en el que es difícil ver dónde está ocurriendo realmente la funcionalidad. Que es otra forma de decir, evita también el olor a Midle Man .

