# Reemplazar Temp por Query

## Problema
El resultado de una expresión se coloca en una variable local para su uso posterior en el código.Colocas el resultado de una expresión en una variable local para su uso posterior en su código.

``` Python
def calculateTotal():
    basePrice = quantity * itemPrice
    if basePrice > 1000:
        return basePrice * 0.95
    else:
        return basePrice * 0.98
```

## Solución
Mueva toda la expresión a un método independiente y devuelva el resultado de ella. 
Consulte el método en lugar de usar una variable. Incorpore el nuevo método en otros métodos, si es necesario.

``` Python
def calculateTotal():
    if basePrice() > 1000:
        return basePrice() * 0.95
    else:
        return basePrice() * 0.98

def basePrice():
    return quantity * itemPrice

```



## ¿Por qué Refactorizar?
Esta refactorización puede sentar las bases para aplicar el [método de extracción](./ExtractMethod.md) para una parte de un método muy largo.<br>A veces, la misma expresión también se puede encontrar en otros métodos, lo cual es una razón para considerar la creación de un método común.

## Beneficios
Legibilidad del código. Es mucho más fácil entender el propósito del método que la línea .```getTax()orderPrice() * 0.2```<br>Simplifica el código a través de la deduplicación, si la línea que se reemplaza se utiliza en varios métodos.

## Es bueno saberlo
### Rendimiento
Esta refactorización puede plantear la cuestión de si este enfoque puede provocar un impacto en el rendimiento. La respuesta honesta es: sí, lo es, ya que el código resultante puede verse sobrecargado por la consulta de un nuevo método. Pero con las CPU rápidas y los excelentes compiladores de hoy en día, la carga casi siempre será mínima. Por el contrario, el código legible y la capacidad de reutilizar este método en otros lugares del código del programa, gracias a este enfoque de refactorización, son beneficios muy notables.<br>No obstante, si la variable temporal se usa para almacenar en caché el resultado de una expresión que realmente consume mucho tiempo, es posible que desee detener esta refactorización después de extraer la expresión en un nuevo método.

## Cómo refactorizar
1. Asegúrese de que se asigna un valor a la variable una vez y solo una vez dentro del método. Si no es así, utilice [Dividir variable temporal](./SplitTemporary.md) para asegurarse de que la variable se utilizará solo para almacenar el resultado de la expresión.

2.Utilice el método de extracción para colocar la expresión de interés en un nuevo método. Asegúrese de que este método solo devuelve un valor y no cambia el estado del objeto. Si el método afecta al estado visible del objeto, utilice [Separar consulta del modificador](./SeparateQueryfromModifier.md).

3.   Reemplace la variable por una consulta al nuevo método.
