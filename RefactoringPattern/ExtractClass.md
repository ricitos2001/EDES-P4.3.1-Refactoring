# Extracción de clases (Extract Class)

## Problema

Cuando una clase realiza el trabajo de dos, el resultado es confuso.

![](./assets/Extract%20Class%20-%20Before.png)

## Solución

Crea una nueva clase y mueve a ella los campos y métodos que tengan una funcionalidad relevante en la misma.

![](./assets/Extract%20Class%20-%20After.png)

## Por qué refactorizar

Las clases deben ser claras y fáciles de leer, ocupándose de una única función sin meterse en el trabajo de otras clases. A medida que el programa avanza, algunas clases terminan desempeñando más funcionalidades de las debidas, y entonces hay que refactorizar.

## Beneficios

* Este método de refactorización ayuda a mantener el ***principio de responsabilidad única***. El código de tus clases será más obvio y comprensible.
* Las clases de responsabilidad única son más confiables y tolerantes a los cambios. Si una clase se ocupa de diez cosas, al cambiar una de ellas corres el riesgo de romper las otras nueve.

## Inconvenientes

* Si te excedes, tendrás que recurrir al método ["***Inline Class***"](/RefactoringPattern/InlineClass.md) de refactorización.

## Cómo refactorizar

Antes de comenzar, decide cómo quieres dividir exactamente las responsabilidades de la clase.

1. Crea una nueva clase para contener la funcionalidad relevante.
2. Crea una relación entre la clase antigua y la nueva, siendo preferentemente unidireccional de forma que se pueda reutilizar la segunda clase sin problema. Si fuera necesario, se puede configurar para que sea bidireccional.
3. Utiliza ["***Move field***"](/RefactoringPattern/MoveField.md) y ["***Move method***"](/RefactoringPattern/MoveMethod.md) para cada campo y método que decidas mover a la nueva clase. Comienza con los métodos privados para reducir el riesgo de cometer una gran cantidad de errores. Trata de reubicarlo poco a poco y prueba los resultados después de cada movimiento, para evitar una acumulación de corrección de errores al final.
   Una vez terminado, revisa por si debe renombrarse la antigua clase para mayor claridad y revisa una vez más por si puede deshacerse las relaciones bidireccionales en caso de haberlas.
4. Piensa también en la accesibilidad de la nueva clase. Puede ocultarla del cliente haciéndola privada a través de los campos de la clase anterior o puede hacerla pública al permitir que el cliente cambie los valores directamente. Su decisión aquí depende de qué tan seguro sea para el comportamiento de la clase anterior cuando se realizan cambios directos inesperados en los valores de la nueva clase.
