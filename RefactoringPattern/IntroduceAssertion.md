# Introducir una afirmación

##  Problema

Para que una porción de código funcione correctamente, ciertas condiciones o valores deben ser verdaderos.

```Java
double getExpenseLimit() {
// Debe tener límite de gastos o
// un proyecto principal.
return (expenseLimit != NULL_EXPENSE) ?
expenseLimit :
primaryProject.getMemberExpenseLimit();
}
```

## Solución

Reemplace estas suposiciones con comprobaciones de afirmación específicas.

```Java
double getExpenseLimit() {
Assert.isTrue(expenseLimit != NULL_EXPENSE || primaryProject != null);

return (expenseLimit != NULL_EXPENSE) ?
expenseLimit:
primaryProject.getMemberExpenseLimit();
}
```

## Por qué refactorizar

Supongamos que una porción de código asume algo acerca de, por ejemplo, la condición actual de un objeto o el valor de un parámetro o variable local. Por lo general, esta suposición siempre será cierta excepto en caso de un error.

Haga que estas suposiciones sean obvias agregando comprobaciones de afirmación correspondientes. Al igual que con las sugerencias de tipos en los parámetros de los métodos, estas afirmaciones pueden actuar como documentación en vivo para su código.

Como guía para ver dónde se necesitan afirmaciones en su código, busque comentarios que describan las condiciones bajo las cuales funcionará un método en particular.

## Beneficios

Si una suposición no es verdadera y, por lo tanto, el código da el resultado incorrecto, es mejor detener la ejecución antes de que esto cause consecuencias fatales y la corrupción de datos. Esto también significa que se descuidó escribir una prueba necesaria al idear formas de realizar pruebas del programa.

## Desventajas

A veces, una excepción es más apropiada que una simple afirmación. Puede seleccionar la clase necesaria de la excepción y dejar que el código restante la maneje correctamente.

¿Cuándo es mejor una excepción que una simple afirmación? Si la excepción puede ser causada por acciones del usuario o del sistema y puede manejar la excepción. Por otro lado, las excepciones ordinarias no nombradas y no controladas son básicamente equivalentes a afirmaciones simples: no las maneja y se producen exclusivamente como resultado de un error del programa que nunca debería haber ocurrido.

## Cómo refactorizar

Cuando vea que se supone una condición, agregue una afirmación para esta condición para asegurarse.

Agregar la afirmación no debería cambiar el comportamiento del programa.

No exagere el uso de afirmaciones para todo en su código. Verifique solo las condiciones que son necesarias para el correcto funcionamiento del código. Si su código funciona normalmente incluso cuando una afirmación en particular es falsa, puede eliminarla de manera segura.

## Elimina olor

[Comments](../CodeSmell/Comments.md)