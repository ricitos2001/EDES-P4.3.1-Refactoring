# Pull Up Method
## Problema
* Sus subclases tienen métodos que realizan un trabajo similar.

![](https://refactoring.guru/images/refactoring/diagrams/Pull%20Up%20Method%20-%20Before.png)

## Solución
* Haga que los métodos sean idénticos y luego muévalos a la superclase relevante.

![](https://refactoring.guru/images/refactoring/diagrams/Pull%20Up%20Method%20-%20After.png)
## Por qué refactorizar
Las subclases crecieron y se desarrollaron independientemente unas de otras, dando lugar a campos y métodos idénticos (o casi idénticos).
## Beneficios
* Elimina el código duplicado. Si necesita realizar cambios en un método, es mejor hacerlo en un solo lugar que tener que buscar todos los duplicados del método en las subclases.
* Esta técnica de refactorización también se puede usar si, por alguna razón, una subclase redefine un método de superclase pero realiza esencialmente el mismo trabajo.


## Como refactorizar
1. Investigue métodos similares en superclases. Si no son idénticos, formatéelos para que coincidan entre sí.
2. Si los métodos usan un conjunto diferente de parámetros, coloque los parámetros en la forma que desea ver en la superclase.
3. Copie el método a la superclase. Aquí puede encontrar que el código del método usa campos y métodos que existen solo en las subclases y, por lo tanto, no están disponibles en la superclase. Para solucionar esto, puedes:
    * Para los campos: use el [Pull Up Field](https://refactoring.guru/es/pull-up-field) o el Self-[Encapsulate Field](https://refactoring.guru/es/encapsulate-field) para crear captadores y definidores en subclases; luego declare estos captadores de forma abstracta en la superclase.
    * Para los metodos: use el [Pull Up Method](https://refactoring.guru/es/pull-up-method) o declarar métodos abstractos para ellos en la superclase (tenga en cuenta que su clase se volverá abstracta si no lo era anteriormente).
4. Elimina los métodos de las subclases.
5. Compruebe las ubicaciones en las que se llama al método. En algunos lugares, es posible que pueda reemplazar el uso de una subclase con la superclase.