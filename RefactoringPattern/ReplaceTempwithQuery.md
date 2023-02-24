# Replace Temp with Query

## Problema
Colocas el resultado de una expresión en una variable local para su uso posterior en su código.

``` Python
def calculateTotal():
    basePrice = quantity * itemPrice
    if basePrice > 1000:
        return basePrice * 0.95
    else:
        return basePrice * 0.98
```

## Solución
Mueva la expresión completa a un método separado y devuelva el resultado.
Consulta el método en lugar de usar una variable. Incorpore el nuevo método en otros métodos, si es necesario.

``` Python
def calculateTotal():
    if basePrice() > 1000:
        return basePrice() * 0.95
    else:
        return basePrice() * 0.98

def basePrice():
    return quantity * itemPrice

```



## Por qué refactorizar
Esta refactorización puede sentar las bases para aplicar el [Extrac Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/ExtractMethod.md) para una parte de un método muy largo.

A veces, la misma expresión también se puede encontrar en otros métodos, lo cual es una razón para considerar la creación de un método común.

## Beneficios
Legibilidad del código. Es mucho más fácil entender la funcion del método getTax() que la línea orderPrice() * 0.2.

Código más legible a través de la deduplicación, si la línea que se reemplaza se usa en varios métodos.

## Bueno saber
### Actuación
Esta refactorización puede generar la pregunta de si este enfoque puede causar un impacto en el rendimiento.
La respuesta honesta es: sí, lo es, ya que el código resultante puede verse afectado por la consulta de un nuevo método. 
Pero con las rápidas CPU de hoy en día y los excelentes compiladores, la carga casi siempre será mínima. Por el contrario, 
el código legible y la capacidad de reutilizar este método en otros lugares del código del programa, gracias a este enfoque de
refactorización, son beneficios muy notables.

No obstante, si su variable temporal se usa para almacenar en caché el resultado de una expresión que realmente consume mucho tiempo,
es posible que desee detener esta refactorización después de extraer la expresión a un nuevo método.

## Cómo refactorizar
1. Asegúrese de que se asigna un valor a la variable una vez y solo una vez dentro del método. De lo contrario, use [Split Temporary Variable](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/SplitTemporaryVariable.md)
para asegurarse de que la variable se use solo para almacenar el resultado de su expresión.

2. Utilice [Extract Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/ExtractMethod.md) para colocar la 
expresión de interés en un nuevo método. Asegúrese de que este método solo devuelva un valor y no cambie el estado del objeto. Si el método afecta 
el estado visible del objeto, use [Separate Query from Modifier](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPatter/SeparateQueryfromModifier.md) .

3. Reemplace la variable con una consulta a su nuevo método.
