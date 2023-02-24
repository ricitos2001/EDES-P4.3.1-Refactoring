# Renombrar Método (Rename Method)

## Problema

Un método no es utilizado por otras clases o solamente se utiliza dentro de su propia jerarquía de clases.

![](https://refactoring.guru/images/refactoring/diagrams/Hide%20Method%20-%20Before.png?id=598219cd5a4b26974b091534b2dc89ae)

## Solución

Cambiar la forma del método para que este privada (private) o protegida (protected)

![](https://refactoring.guru/images/refactoring/diagrams/Hide%20Method%20-%20After.png?id=2f7f1435a959a0a611778513e5bc4365)

## Por qué Refactorizar
Muy a menudo, la necesidad de ocultar métodos para obtener y establecer valores se debe al desarrollo de una interfaz más rica que proporciona un comportamiento adicional, 
especialmente si comenzó con una clase que agregó poco más allá de la mera encapsulación de datos.

A medida que se incorpora un nuevo comportamiento en la clase, es posible que descubra que los métodos públicos de captador y setter ya no son necesarios y se pueden ocultar. 
Si hace que los métodos getter o setter sean privados y aplica acceso directo a las variables, puede eliminar el método.

## Beneficios

Ocultar métodos facilita la evolución del código. Cuando cambia un método privado, solo necesita preocuparse por cómo no romper la clase actual, 
ya que sabe que el método no se puede usar en ningún otro lugar.

Al hacer que los métodos sean privados, subraya la importancia de la interfaz pública de la clase y de los métodos que siguen siendo públicos.

## Cómo refactorizar

1. Trate regularmente de encontrar métodos que puedan hacerse privados. 
El análisis de código estático y una buena cobertura de pruebas unitarias pueden ofrecer una gran ventaja.
2. Haga que cada método sea lo más privado posible.