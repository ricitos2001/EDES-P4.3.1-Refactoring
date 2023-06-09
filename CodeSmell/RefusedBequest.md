# Herencia Rechazada

## Signos y Síntomas

Si una subclase utiliza solo algunos de los métodos y propiedades heredados de sus padres, la jerarquía está desequilibrada. Los métodos no necesarios pueden quedar sin usar o ser redefinidos y generar excepciones.

## Razones del Problema

Alguien se motivó a crear herencia entre clases únicamente por el deseo de reutilizar el código en una superclase. Pero la superclase y la subclase son completamente diferentes.

## Tratamiento

Si la herencia no tiene sentido y la subclase realmente no tiene nada en común con la superclase, elimina la herencia a favor de Reemplazar Herencia con Delegación.

Si la herencia es apropiada, elimina los campos y métodos no necesarios en la subclase. Extrae todos los campos y métodos necesarios por la subclase de la clase padre, colócalos en una nueva superclase y establece que ambas clases hereden de ella (Extraer Superclase).

## Beneficios

Mejora la claridad y organización del código. Ya no tendrás que preguntarte por qué la clase "Perro" hereda de la clase "Silla" (aunque ambas tengan 4 patas).