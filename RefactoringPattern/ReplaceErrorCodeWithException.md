# Reemplazar los códigos de error con excepciones (Replace Error Code with Exception)

## Problema

Un método devuelve un valor especial que indica un error

```Kotlin
fun retirar(monto: Int): Int {
    if (monto > balance) {
        return -1
    } else {
        balance -= monto
    }
    return 0
}
```

## Solución

Lanzar una excepción en su lugar.

```Kotlin
fun retirar(monto: Int) {
    if (monto > balance) {
        throw BalanceException()
    }
    balance -= monto
}
```

## Por qué refactorizar

La devolución de códigos de error es un vestigio obsoleto de la programación procedimental. En la programación moderna, el manejo de errores lo realizan clases especiales, que se denominan excepciones. Si se produce un problema, "lanza" un error, que luego es "capturado" por uno de los controladores de excepciones. El código especial de manejo de errores, que se ignora en condiciones normales, se activa para responder.

## Beneficios

* Libera al código de una gran cantidad de condiciones para verificar varios códigos de error. Los controladores de excepciones son una forma mucho más corta de diferenciar las rutas de ejecución normales de las anormales.
* Las clases de excepción pueden implementar sus propios métodos, por lo que contienen parte de la funcionalidad de manejo de errores (como para enviar mensajes de error).
* A diferencia de las excepciones, los códigos de error no se pueden usar en un constructor, ya que un constructor debe devolver solo un objeto.
