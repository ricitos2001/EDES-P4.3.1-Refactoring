# Data Class

Las data class, como su nombre indica, son clases que solo contiene datos que otras clases usarán y no contienen ninguna funcionalidad y no pueden gestionar por si mismo sus propios datos.

## ¿Por qué son un problema?

Algunos consideran un problema las data class porque consideran que las clases deberían de gestionar sus propios datos y tener más funcionalidad más allá de solo guardar datos.

Cabe comentar que no todas las personas consideran las data class como una mala práctica,pues consideran que son bastante útiles para trabajar.[Aquí dejo un enlace sobre esto](https://softwareengineering.stackexchange.com/questions/338195/why-are-data-classes-considered-a-code-smell)

## ¿Cómo solucionarlo?

Si consideras que las data class son algo que hay que exterminar, asegurate de que la funcionalidad relevante para los datos se implementa en métodos de la clase, y que los datos se almacenan en la clase más apropiada para ello.

También puedes usar técnicas de refactorización como [Encapsulate Collection](https://refactoring.guru/es/encapsulate-collection) para que guardes los datos en colecciones,[Encapsulate Field](https://refactoring.guru/es/encapsulate-field) para evitar el acceso directo a los datos,[Move Method](https://refactoring.guru/es/move-method) y [Extract Method](https://refactoring.guru/es/extract-method) para añadir métodos que van mejor en la data class que en el sitio donde estén, [Hide Method](https://refactoring.guru/es/hide-method) y [Remove Setting Method](https://refactoring.guru/es/remove-setting-method) para eliminar métodos que dan un acceso demasiado amplio a una data class.
