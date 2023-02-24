# Cambiar valor a referencia

## Problema

Hay muchas instancias idénticas de una sola clase que necesita reemplazar con un solo objeto.

## Solución

Convierta los objetos idénticos en un solo objeto de referencia.

![Alt text](https://refactoring.guru/images/refactoring/diagrams/Change%20Value%20to%20Reference%20-%20Before.png?id%3Db2e65e5bb87366e8195bab6933c15250)

![Alt text](https://refactoring.guru/images/refactoring/diagrams/Change%20Value%20to%20Reference%20-%20After.png?id%3D20d3bdea32264097859011bacb4ff19f)

## Por qué refactorizar

En muchos sistemas, los objetos se pueden clasificar como valores o referencias.

· Referencias : cuando un objeto del mundo real corresponde a un solo objeto en el programa. Las referencias suelen ser usuario/pedido/producto/etc. objetos.

· Valores : un objeto del mundo real corresponde a múltiples objetos en el programa. Estos objetos pueden ser fechas, números de teléfono, direcciones, colores y similares.

La selección de referencia frente a valor no siempre es clara. A veces hay un valor simple con una pequeña cantidad de datos que no cambian. Entonces se vuelve necesario agregar datos modificables y pasar estos cambios cada vez que se accede al objeto. En este caso se hace necesario convertirlo en una referencia.

## Beneficios

Un objeto contiene toda la información más actual sobre una entidad en particular. Si el objeto se cambia en una parte del programa, estos cambios son accesibles desde las otras partes del programa que hacen uso del objeto.

## Inconvenientes

Las referencias son mucho más difíciles de implementar.

## Cómo refactorizar

1.Utilice Reemplazar constructor con el método de fábrica en la clase a partir de la cual se generarán las referencias.

2.Determine qué objeto será responsable de proporcionar acceso a las referencias. En lugar de crear un nuevo objeto, cuando necesite uno, debe obtenerlo de un objeto de almacenamiento o un campo de diccionario estático.

3.Determine si las referencias se crearán por adelantado o dinámicamente según sea necesario. Si los objetos se crean con anticipación, asegúrese de cargarlos antes de usarlos.

4.Cambie el método de fábrica para que devuelva una referencia. Si los objetos se crean con anticipación, decida cómo manejar los errores cuando se solicite un objeto inexistente. Es posible que también deba usar Rename Method para informar que el método solo devuelve objetos existentes.