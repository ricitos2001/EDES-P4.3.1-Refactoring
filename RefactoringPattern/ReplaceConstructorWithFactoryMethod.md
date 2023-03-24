# Reemplazar Constructor con Método de Fábrica

## Problema

Tienes un constructor complejo que hace algo más que simplemente establecer valores de parámetros en campos de objeto.

```Java
class Empleado {
Empleado(int tipo) {
this.tipo = tipo;
}
// ...
}
```

## Solución

Crea un método de fábrica y úsalo para reemplazar las llamadas al constructor.

```Java
class Empleado {
static Empleado crear(int tipo) {
empleado = new Empleado(tipo);
// hacer algo complejo.
return empleado;
}
// ...
}
```

## Por qué Refactorizar

La razón más obvia para usar esta técnica de refactorización está relacionada con la técnica [Reemplazar Código de Tipo con Subclases](../RefactoringPattern/ReplaceTypeCodeWithClass.md).

Tienes código en el que se crea un objeto y se le pasa el valor del tipo codificado. Después de usar el método de refactorización, han aparecido varias subclases y de ellas necesitas crear objetos dependiendo del valor del tipo codificado. Cambiar el constructor original para que devuelva objetos de subclase es imposible, por lo que en su lugar se crea un método de fábrica estático que devolverá objetos de las clases necesarias, después de lo cual reemplaza todas las llamadas al constructor original.

Los métodos de fábrica también se pueden usar en otras situaciones, cuando los constructores no son adecuados para la tarea. Pueden ser importantes al intentar [Cambiar Valor por Referencia](../RefactoringPattern/ChangeValueToReference.md). También se pueden utilizar para establecer varios modos de creación que van más allá del número y tipos de parámetros.

## Ventajas

Un método de fábrica no necesariamente devuelve un objeto de la clase en la que se llamó. A menudo, pueden ser sus subclases, seleccionadas en función de los argumentos dados al método.

Un método de fábrica puede tener un nombre mejor que describa qué y cómo devuelve lo que hace, por ejemplo ''Java Troops::GetCrew(miTanque).'''

Un método de fábrica puede devolver un objeto que ya se ha creado, a diferencia de un constructor, que siempre crea una nueva instancia.

## Cómo Refactorizar

1. Crea un método de fábrica. Coloca una llamada al constructor actual en él.

2. Reemplaza todas las llamadas al constructor con llamadas al método de fábrica.

3. Declara el constructor como privado.

4. Investiga el código del constructor e intenta aislar el código que no está directamente relacionado con la construcción de un objeto de la clase actual, moviendo dicho código al método de fábrica

## Ayuda otras refactorizaciones

[Cambiar valor por referencia](../RefactoringPattern/ChangeValueToReference.md)

[Reemplazar Codigo Tipo con Subclasses](../RefactoringPattern/ReplaceTypeCodeWithSubClass.md)

## Implementa Patron de Diseno

[Metodo Fabrica](https://refactoring.guru/es/design-patterns/factory-method)
