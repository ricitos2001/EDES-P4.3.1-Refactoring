# Reemplazar Condiciones Anidadas con Cláusulas de Guarda

## Problema

Tiene un grupo de condiciones anidadas y es difícil determinar el flujo normal de ejecución del código.

## Solución

Aísle todas las comprobaciones especiales y casos extremos en cláusulas separadas y colóquelas antes de las 
comprobaciones principales. Idealmente, debería tener una lista "plana" de condiciones, una después de la otra.

# Antes
```java
public double getPayAmount() {
    double result;
    if (isDead){
        result = deadAmount();
    }
    else {
        if (isSeparated){
            result = separatedAmount();
        }
        else {
            if (isRetired){
                result = retiredAmount();
            }
            else{
                result = normalPayAmount();
            }
        }
    }
    return result;
}
```

# Despues
```java
public double getPayAmount() {
    if (isDead){
        return deadAmount();
    }
    if (isSeparated){
        return separatedAmount();
    }
    if (isRetired){
        return retiredAmount();
    }
    return normalPayAmount();
}
```

## Por qué Refactorizar

Identificar la "condición del infierno" es bastante fácil. Las indentaciones de cada nivel de anidamiento forman una 
flecha, apuntando hacia la derecha en la dirección del dolor y la angustia:

```
if () {
    if () {
        do {
            if () {
                if () {
                    if () {
                        ...
                    }
                }
                ...
            }
            ...
        }
        while ();
        ...
    }
    else {
    ...
    }
}
```

Es difícil entender lo que hace cada condicional y cómo lo hace, ya que el flujo "normal" de ejecución del código no es 
inmediatamente evidente. Estos condicionales indican una evolución caótica, con cada condición agregada como una medida 
temporal sin ninguna consideración para optimizar la estructura general.

Para simplificar la situación, aísle los casos especiales en condiciones separadas que finalizan inmediatamente la 
ejecución y devuelven un valor nulo si las cláusulas de guarda son verdaderas. En efecto, su misión aquí es hacer que la 
estructura sea plana.

## Cómo Refactorizar

Trate de eliminar los efectos secundarios del código - [Separar Consulta de Modificador](SeperateQueryFromModifier.md) 
puede ser útil para este propósito. Esta solución será necesaria para la reorganización descrita a continuación.

1. Aísle todas las cláusulas de guarda que llevan a llamar a una excepción o devolución inmediata de un valor del método 
. Coloque estas condiciones al principio del método.

2. Después de que se haya completado la reorganización y se hayan realizado todas las pruebas con éxito, vea si puede 
usar la [Consolidación de Expresiones Condicionales](ConsolidateConditionalExpression.md) para cláusulas de guarda que 
lleven a las mismas excepciones o valores devueltos.
