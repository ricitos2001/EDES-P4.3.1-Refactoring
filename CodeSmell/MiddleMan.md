# Intermediarios (Middle Man)

## Síntomas y signos

Si una clase realiza solo una acción, delegando el trabajo a otra clase, entonces ¿Por qué existe?

![](https://refactoring.guru/images/refactoring/content/smells/middle-man-01.png?id=14c65845c4e0cf03e7e9e48108090c98![img.png](img.png))

## Razones del problema

Este Code Smell puede ser el resultado de la eliminación excesiva de las cadenas de mensajes.

En otros casos, puede ser el resultado del trabajo útil de una clase que se mueve gradualmente a otras clases.
La clase permanece como una cáscara vacía que no hace otra cosa que delegar.

## Tratamiento

Si la mayoría de las clases de un método delegan a otra clase, Quitar intermediario está entre ellos.

![](https://refactoring.guru/images/refactoring/content/smells/middle-man-02.png?id=f507c0fd9a7bde8df8c22b9027d0a404)

## Recompensa

El código se vuelve menos voluminoso.

## Cuando ignorar

No elimine los intermediarios que se hayan creado por estos motivos:

Si se ha agregado un intermediario para evitar dependencias entre clases.

Algunos patrones de diseño crean intermediarios a propósito (como Proxy o Decorator).