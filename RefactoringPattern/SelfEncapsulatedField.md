# Autoencapsular Campo

## Problema
Utilizas acceso directo a campos privados dentro de una clase.

``` Java
class Range {
  private int low, high;
  boolean includes(int arg) {
    return arg >= low && arg <= high;
  }
}
```

## Solución
Crea un getter y un setter para el campo y utiliza solo estos métodos para acceder al campo.

``` Java
class Range {
  private int low, high;
  boolean includes(int arg) {
    return arg >= getLow() && arg <= getHigh();
  }
  int getLow() {
    return low;
  }
  int getHigh() {
    return high;
  }
}
```

## Por qué Refactorizar
A veces, acceder directamente a un campo privado dentro de una clase no es lo suficientemente flexible. Quieres poder inicializar un valor de campo cuando se realiza la primera consulta o realizar ciertas operaciones en los nuevos valores del campo cuando se asignan, o tal vez hacer todo esto de varias formas en las subclases.

## Beneficios
 - El acceso indirecto a los campos se refiere a cuando se actúa sobre un campo a través de métodos de acceso (getters y setters). Este enfoque es mucho más flexible que el acceso directo a los campos.

   - En primer lugar, puedes realizar operaciones complejas cuando se establece o se recibe datos en el campo. La inicialización diferida y la validación de los valores del campo se pueden implementar fácilmente dentro de los getters y setters del campo.

   - En segundo lugar, y más importante aún, puedes redefinir los getters y setters en las subclases.

 - Tienes la opción de no implementar un setter para un campo en absoluto. El valor del campo se especificará solo en el constructor, lo que hace que el campo sea inmutable durante toda la vida útil del objeto.

## Desventajas
Cuando se utiliza el acceso directo a los campos, el código parece más simple y presentable, aunque la flexibilidad se ve disminuida.

## Cómo Refactorizar
 1. Crea un getter (y un setter opcional) para el campo. Estos deben ser protegidos o públicos.

 2. Encuentra todas las invocaciones directas del campo y reemplázalas por llamadas a los getters y setters.