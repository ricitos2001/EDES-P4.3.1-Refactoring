# Codigo Duplicado (Duplicate Code)

## Síntomas y signos

Dos fragmentos de código parecen casi idénticos

![](https://refactoring.guru/images/refactoring/content/smells/duplicate-code-01.png?id=16fe591195fa50073551852b3d44844e)

## Razones del problema

La duplicación suele ocurrir cuando varios programadores trabajan en diferentes partes del mismo programa al mismo tiempo. Dado que están trabajando en tareas diferentes, pueden no ser conscientes de que su colega ya ha escrito código similar que podría reutilizarse para sus propias necesidades.

También existe una duplicación más sutil, cuando partes específicas del código parecen diferentes pero en realidad realizan el mismo trabajo. Este tipo de duplicación puede ser difícil de detectar y solucionar.

A veces, la duplicación es intencional. Cuando se está apurado por cumplir plazos y el código existente es "casi correcto" para el trabajo, los programadores novatos pueden no resistir la tentación de copiar y pegar el código relevante. Y en algunos casos, el programador simplemente es demasiado perezoso para despejar el código.

## Tratamiento

* Si se encuentra el mismo código en dos o más métodos dentro de la misma clase: se debe utilizar la técnica de refactorización [Extract Method](https://refactoring.guru/es/extract-method) y colocar llamadas al nuevo método en ambos lugares.

![](https://refactoring.guru/images/refactoring/content/smells/duplicate-code-02.png?id=50d92af3defe2c2688f66cde102c9c09)

Si se encuentra el mismo código en dos subclases del mismo nivel:

- Utilice la técnica de refactorización [Extract Method](https://refactoring.guru/es/extract-method) para ambas clases, seguida de [Pull Up Field](https://refactoring.guru/es/pull-up-field) para los campos utilizados en el método que se está extrayendo.

- Si el código duplicado está dentro de un constructor, utilice [Pull Up Constructor Body](https://refactoring.guru/es/pull-up-constructor-body).

- Si el código duplicado es similar pero no completamente idéntico, utilice [Form Template Method](https://refactoring.guru/es/form-template-method).

- Si dos métodos hacen lo mismo pero usan diferentes algoritmos, seleccione el mejor algoritmo y aplique [Substitute Algorithm](https://refactoring.guru/es/substitute-algorithm).

Si se encuentra código duplicado en dos clases diferentes:

- Si las clases no forman parte de una jerarquía, se debe utilizar la técnica de refactorización [Extract Superclass](https://refactoring.guru/es/extract-superclass) para crear una superclase única para estas clases que mantenga toda la funcionalidad anterior.

- Si es difícil o imposible crear una superclase, se debe utilizar [Extract Class](https://refactoring.guru/es/extract-class) en una de las clases y utilizar el nuevo componente en la otra.

Si hay un gran número de expresiones condicionales presentes y realizan el mismo código (diferenciándose solo en sus condiciones), se debe utilizar la técnica de refactorización [Consolidate Conditional Expression](https://refactoring.guru/es/consolidate-conditional-expression) para fusionar estos operadores en una sola condición y utilizar [Extract Method](https://refactoring.guru/es/extract-method) para colocar la condición en un método separado con un nombre fácil de entender.

Si el mismo código se realiza en todas las ramas de una expresión condicional: se debe colocar el código idéntico fuera del árbol de condición utilizando la técnica de refactorización [Consolidate Duplicate Conditional Fragments](https://refactoring.guru/es/consolidate-duplicate-conditional-fragments).

Estas técnicas de refactorización pueden ser útiles para simplificar y optimizar el código que contiene muchas expresiones condicionales y mejorar su legibilidad y mantenibilidad.

## Recompensa

La fusión de código duplicado simplifica la estructura del código y lo hace más corto.

Simplificación + brevedad = código más fácil de simplificar y más económico de mantener.

![](https://refactoring.guru/images/refactoring/content/smells/duplicate-code-03.png?id=bd88b98ff5e5e1b5a4019cb0a50df9f5)

## Cuando Ignorar

En casos muy raros, fusionar dos fragmentos idénticos de código puede hacer que el código sea menos intuitivo y obvio.