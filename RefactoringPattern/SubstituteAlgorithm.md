# Algoritmo de sustitución

## Problema

Entonces, quieres sustituir el algoritmo existente por uno nuevo
```kotlin
fun foundPerson(people: Array<String>): String? {
    for (i in people.indices) {
        if (people[i] == "Don") {
            return "Don"
        }
        if (people[i] == "John") {
            return "John"
        }
        if (people[i] == "Kent") {
            return "Kent"
        }
    }
    return ""
}
```
## Solución
Reemplace el cuerpo del método que implementa el algoritmo con un nuevo algoritmo.
```kotlin
fun foundPerson(people: Array<String?>): String? {
    val candidates: List<*> = Arrays.asList(*arrayOf("Don", "John", "Kent"))
    for (i in people.indices) {
        if (candidates.contains(people[i])) {
            return people[i]
        }
    }
    return ""
}
```
## Por qué refactorizar
1. La refactorización gradual no es el único método para mejorar un programa. A veces, un método está tan repleto de problemas que es más fácil acabar con el método y empezar de nuevo. Y quizás haya encontrado un algoritmo que es mucho más simple y más eficiente. Si este es el caso, simplemente debe reemplazar el algoritmo anterior por el nuevo.

2. A medida que pasa el tiempo, es posible que su algoritmo se incorpore a una biblioteca o marco conocido y desee deshacerse de su implementación independiente para simplificar el mantenimiento.

3. Los requisitos para su programa pueden cambiar tanto que su algoritmo existente no se puede salvar para la tarea.

## Cómo refactorizar

1. Asegúrese de haber simplificado el algoritmo existente tanto como sea posible. Mueva el código sin importancia a otros métodos usando el [método de extracción](ExtractMethod.md) . Cuantas menos partes móviles tenga su algoritmo, más fácil será reemplazarlo.
2. Cree su nuevo algoritmo en un nuevo método. Reemplace el antiguo algoritmo con el nuevo y comience a probar el programa.
3. Si los resultados no coinciden, regrese a la implementación anterior y compare los resultados. Identificar las causas de la discrepancia. Si bien la causa suele ser un error en el algoritmo anterior, es más probable que se deba a que algo no funciona en el nuevo.
4. Cuando todas las pruebas se completen con éxito, ¡elimine el algoritmo anterior para siempre!
<<<<<<< HEAD

=======
>>>>>>> e3cff725a9feec5fe078c604d4f365c26bc57581
