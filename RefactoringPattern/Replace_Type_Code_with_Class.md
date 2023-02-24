# Replace Type Code with Class

El type code sucede cuando tienes un conjunto de números o strings que forman parte de los valores de una entidad.Normalmente a esos datos se le suele dejar un nombre entendible por lo que no se le hace nada.

## ¿Cuál es el problema?

El type code no son usados en las condiciones del operador y no afectan al comportamiento del problema

Normalmente cuando se usa el type code es porque se trabaja con bases de datos, más concretamente cuando una base de datos tiene algún campo complejo como un número o una cadena. El problema con esto es que los configuradores de campo no siempren envían la información que deberían lo que puede conllevar a muchos problemas.

## ¿Cómo solucionarlo?

La idea generar para solucionarlo es agrupar el type code en una clase, por aquí voy a dejar una serie de pasos a seguir:

1. Crear una clase con un nombre correspondiente al type code.
2. Copiar el campo que contenga el type code y hacerlo privado, el constructor de la clase dará el valor al campo
3. Para cada valor del coded type crea un método estático en la clase que hemos creado
4. En la clase original cambiar el campo por la clase que hemos creado
5. Cambia cualquier mención a los valores del coded type con llamadas a los métodos estáticos de la clase que hemos creado
6. Quitar las constantes que sean necesarias

## Beneficios

* Conviertes el type code en clases, añadiendo todas las ventajas de la programación orientada a objetos
* Al reemplazar el código el IDE nos podrá avisar cuando haya algo mal o algo que se pueda mejorar.
* De este módo puedes manipular de manera mucho más sencilla los datos al estar dentro de una o varias clases

## Ejemplo

```
class aula(val numAula:Int,var cantidadAlumnos:Int){
    val nombreDelegado: String 
}
```

```
class Aula(val numAula:Int,var cantidadAlumnos:Int){
    val nombreDelegado = Alumno("pepito lópez").darNombre()
}
class Alumno(val nombre_alumno: String){
    fun darNombre(){
        return nombre_alumno
    }
}
```
