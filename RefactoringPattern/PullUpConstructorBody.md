# Pull Up Constructor Body

## Problema
Tus subclases tienen constructores con código que es principalmente idéntico.

```  Java
class Manager extends Employee {
  public Manager(String name, String id, int grade) {
    this.name = name;
    this.id = id;
    this.grade = grade;
  }
  // ...
}

```
## Solución
Cree un constructor de superclase y mueva el código que es igual en las subclases a él. Llame al constructor de la superclase en los constructores de la subclase.

``` Java 
class Manager extends Employee {
  public Manager(String name, String id, int grade) {
    super(name, id);
    this.grade = grade;
  }
  // ...
}
```

## ¿Por qué Refactorizar?
### ¿Cómo se diferencia esta técnica de Refactorización del método [Pull Up](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/123-refactoring-dealing-with-generalization-pull-up-method/RefactoringPattern/Pull-up-Method.md)?

En Java, las subclases no pueden heredar un constructor, por lo que no se puede simplemente aplicar el método [Pull Up](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/123-refactoring-dealing-with-generalization-pull-up-method/RefactoringPattern/Pull-up-Method.md) al constructor de la subclase y eliminarlo después de eliminar todo el código del constructor a la superclase. Además de crear un constructor en la superclase, es necesario tener constructores en las subclases con una simple delegación al constructor de la superclase.

En C++ y Java (si no se llama explícitamente al constructor de la superclase), el constructor de la superclase se llama automáticamente antes del constructor de la subclase, lo que hace necesario mover el código común solo desde el principio de los constructores de la subclase (ya que no se podrá llamar al constructor de la superclase desde cualquier lugar en un constructor de la subclase).

En la mayoría de los lenguajes de programación, un constructor de una subclase puede tener su propia lista de parámetros diferente de los parámetros de la superclase. Por lo tanto, debe crear un constructor de superclase solo con los parámetros que realmente necesita.

## Cómo Refactorizar

1. Crear un constructor en una superclase.
2. Extraer el código común del principio del constructor de cada subclase al constructor de la superclase. Antes de hacerlo, intente mover tanto código común como sea posible al principio del constructor.
3. Colocar la llamada al constructor de la superclase en la primera línea de los constructores de la subclase.
