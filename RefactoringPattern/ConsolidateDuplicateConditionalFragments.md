# Consolidar fragmentos condicionales duplicados (Consolidate Duplicate Conditional Fragment)

## Problema

Se puede encontrar un código idéntico en todas las ramas de un condicional.

```Kotlin
if (isSpecialDeal()) {
  total = price * 0.95
  send()
}
else {
  total = price * 0.98
  send()
}
```

## Solución

Mueva el código fuera de la condicional.

```Kotlin
if (isSpecialDeal()) {
  total = price * 0.95
}
else {
  total = price * 0.98
}
send()
```

## Por qué refactorizar

El código duplicado se encuentra dentro de todas las ramas de un condicional, a menudo como resultado de la evolución del código dentro de las ramas condicionales.

## Beneficios

* Deduplicación de código.

## Cómo refactorizar

1. Si el código duplicado está al comienzo de las ramas condicionales, mueve el código a un lugar antes del condicional.
2. Si el código se ejecuta al final de las ramas, colóquelo después del condicional.
3. Si el código duplicado se encuentra aleatoriamente dentro de las ramas, primero intente mover el código al principio o al final de la rama, dependiendo de si cambia el resultado del código posterior.
4. Si corresponde y el código duplicado tiene más de una línea, intente usar el [***método de extracción***](/RefactoringPattern/ExtractMethod.md).
