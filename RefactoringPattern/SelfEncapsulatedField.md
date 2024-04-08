# Autoencapsular Campo

## Problema
Utilizas acceso directo a campos privados dentro de una clase.

```Kotlin
class Range {
  fun includes(arg: Int): Boolean {
    return arg >= low && arg <= high
  }
}
```

## Solución
Crea un getter y un setter para el campo y utiliza solo estos métodos para acceder al campo.


```Kotlin
class Range {
    fun includes(arg: Int): Boolean {
        return arg >= low && arg <= high
    }

    fun getLow(): Int {
        return low
    }

    fun getHigh(): Int {
        return high
    }
}
```


## ¿Por qué Refactorizar?
A veces, acceder directamente a un campo privado dentro de una clase no es lo suficientemente flexible. Quieres poder inicializar un valor de campo cuando se realiza la primera consulta o realizar ciertas operaciones en los nuevos valores del campo cuando se asignan, o tal vez hacer todo esto de varias formas en las subclases.

## Beneficiós
* El acceso indirecto a los campos es cuando se actúa sobre un campo a través de métodos de acceso (getters y setters). Este enfoque es mucho más flexible que el acceso directo a los campos.

** En primer lugar, puede realizar operaciones complejas cuando se establecen o reciben datos en el campo. La inicialización diferida y la validación de los valores de campo se implementan fácilmente dentro de los captadores y establecedores de campos.

** En segundo lugar, y lo que es más importante, puede redefinir getters y setters en subclases.

* Tiene la opción de no implementar un establecedor para un campo en absoluto. El valor del campo se especificará solo en el constructor, lo que hará que el campo sea inalterable durante toda la vida útil del objeto.

## Inconvenientes
Cuando se utiliza el acceso directo a los campos, el código parece más sencillo y presentable, aunque la flexibilidad disminuye.

## Cómo Refactorizar
 1. Cree un captador (y un establecedor opcional) para el campo. Deben ser o `protected` o `public`.

 2. Busque todas las invocaciones directas del campo y reemplácelas por llamadas getter y setter.
