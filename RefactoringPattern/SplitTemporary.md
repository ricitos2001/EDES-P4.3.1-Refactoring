# Dividir Temporalmente (Split Temporary)

## Problema

Tienes una variable local que se usa para almacenar varios valores intermedios dentro de un método (excepto las variables de ciclo).

```Kotlin (esta en java)
temperatura  doble =  2  *  ( alto  +  ancho ) ;sistema _ fuera _ println ( temp ) ;
temperatura = alto * ancho ; sistema _ fuera _ println ( temp ) ;

}
```

## Solución

Usa diferentes variables para diferentes valores. Cada variable debe ser responsable de una sola cosa en particular.

```Kotlin (esta en java)
 doble  perímetro  final =  2  *  ( alto  +  ancho ) ;sistema _ fuera _ println ( perímetro ) ;
 área doble final = alto * ancho ; sistema _ fuera _ println ( área ) ;

}
```

## Por qué refactorizar

Si estas escatimando en la cantidad de variables dentro de una función y reutilizándolas para varios propósitos no relacionados, seguramente encontraras problemas tan rapido como necesites realizar cambios en el código que contiene las variables.
Tendras que volver a comprobar cada caso de uso de variables para asegurarte de que se utilizan los valores correctos.

## Beneficios

- Cada componente del código del programa debe ser responsable de una sola cosa. Esto hace que sea mucho más fácil mantener el código, ya que puedes reemplazar fácilmente cualquier cosa en particular sin temor a efectos no deseados.

- El código se vuelve más legible. Si una variable se creó hace mucho tiempo con prisa, probablemente tenga un nombre que no explique nada: k, a2, value, etc. Pero puede solucionar esta situación nombrando las nuevas variables de una manera comprensible y autoexplicativa. Dichos nombres pueden parecerse a , customerTaxValuey similares.cityUnemploymentRateclientSalutationString

- Esta técnica de refactorización es útil si preves utilizar el método de extracción más adelante.

## Cómo refactorizar

1. Encuentra el primer lugar en el código donde se da un valor a la variable. Aquí debe cambiar el nombre de la variable con un nombre que corresponda al valor que se le está asignando.

2. Utiliza el nuevo nombre en lugar del antiguo en los lugares donde se utilice este valor de la variable.

3. Repite según sea necesario para los lugares donde a la variable se le asigna un valor diferente.
