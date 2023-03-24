# Reemplaza el Type Code por subclases

## ¿Qué es el Type Code?

> El código de tipo ocurre cuando, en lugar de un tipo de datos separado, tienes un conjunto de números o 
cadenas que forman una lista de valores permitidos para alguna entidad. A menudo, estos números y cadenas 
específicos se nombran de manera comprensible mediante constantes, lo que explica por qué se encuentra tanto
el código de tipo.

## Problema
Tienes un tipo codificado que afecta directamente el comportamiento del programa
(los valores de este campo activan varios códigos en las condiciones).

![Reemplazar código de tipo por subclases - antes](https://refactoring.guru/images/refactoring/diagrams/Replace%20Type%20Code%20with%20Subclasses%20-%20Before.png)

## Solución
Crea subclases para cada valor del tipo codificado. Luego extrae los comportamientos relevantes de la 
clase original a estas subclases. Reemplaza el código de control de flujo con polimorfismo.


![Reemplazar código de tipo por subclases - después](https://refactoring.guru/images/refactoring/diagrams/Replace%20Type%20Code%20with%20Subclasses%20-%20After.png)

## ¿Por qué refactorizar?
Esta técnica de refactorización es una variación más complicada de [Replace Type Code with Class]().

Al igual que en el primer método de refactorización, tienes un conjunto de valores simples que constituyen todos los 
valores permitidos para un campo. Aunque estos valores a menudo se especifican como constantes y tienen nombres 
comprensibles, su uso hace que tu código sea propenso a errores ya que siguen siendo primitivos en efecto.
Por ejemplo, tienes un método que acepta uno de estos valores en los parámetros. En cierto momento, en lugar de la
constante USER_TYPE_ADMIN con el valor "ADMIN", el método recibe la misma cadena en minúsculas ("admin"), lo que 
causará la ejecución de algo que el autor (tú) no pretendía.

Aquí estamos lidiando con código de control de flujo como las condiciones if, switch y ?:, es decir, los campos con
valores codificados (como $user->type === self::USER_TYPE_ADMIN) se usan dentro de las condiciones
de estos operadores. Si usáramos [Replace Type Code with Class](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/Replace_Type_Code_with_Class.md) 
aquí, todas estas construcciones de control de flujo serían mejor movidas a una clase responsable del tipo de datos.
En última instancia, esto, por supuesto, crearía una clase de tipo muy similar a la original, con los mismos problemas también.

## Beneficios
Elimine el código de flujo de control. En lugar de un interruptor voluminoso en la clase original, mueva el código a 
las subclases apropiadas. Esto mejora la adherencia al Principio de Responsabilidad Única y hace que el programa sea 
más legible en general.

Si necesita agregar un nuevo valor para un tipo codificado, todo lo que necesita hacer es agregar una nueva subclase 
sin tocar el código existente (cf. el Principio Abierto/Cerrado).

Al reemplazar el código de tipo con clases, abrimos el camino para sugerencias de tipos para métodos y campos a nivel 
del lenguaje de programación. Esto no sería posible utilizando valores numéricos o de cadena simples contenidos en un 
tipo codificado.

## Cuándo no usar
Esta técnica no es aplicable si ya tiene una jerarquía de clases. No se puede crear una jerarquía dual a través de la
herencia en la programación orientada a objetos. Aún así, puede reemplazar el código de tipo a través de la composición 
en lugar de la herencia. Para hacerlo, use [Replace Type Code with State/Strategy]().

Si los valores del código de tipo pueden cambiar después de que se crea un objeto, evite esta técnica. Tendríamos que 
reemplazar de alguna manera la clase del objeto en sí sobre la marcha, lo cual no es posible. Aún así, una alternativa 
en este caso también sería [Replace Type Code with State/Strategy]().

## Cómo refactorizar
1. Use [Self Encapsulate Field](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/104-refactoring-organizing-data-encapsulate-field/RefactoringPattern/OrganizingDataEncapsulateField.md) para crear un getter para el campo que contiene el código de tipo.

2. Haga que el constructor de la superclase sea privado. Cree un método de fábrica estático con los mismos parámetros
que el constructor de la superclase. Debe contener el parámetro que tomará los valores iniciales del tipo codificado. 
Dependiendo de este parámetro, el método de fábrica creará objetos de varias subclases. Para hacerlo, en su código debe
crear una gran condición, pero al menos será la única cuando sea realmente necesario; de lo contrario, las subclases y
el polimorfismo lo harán.

3. Cree una subclase única para cada valor del tipo codificado. En ella, redefina el getter del tipo codificado para
que devuelva el valor correspondiente del tipo codificado.

4. Elimine el campo con código de tipo de la superclase. Haga que su getter sea abstracto.

5. Ahora que tiene subclases, puede comenzar a mover los campos y métodos desde la superclase a las subclases 
correspondientes (con la ayuda de [Push Down Field](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/PushDownField.md) 
y [Push Down Method](https://github.com/IES-Rafael-Alberti/EDES-P4.3.1-Refactoring/blob/main/RefactoringPattern/PushDownMethod.md).

6. Cuando se haya movido todo lo posible, use [Replace Conditional with Polymorphism]() para deshacerse de las condiciones 
que utilizan el código de tipo de una vez por todas.