# Reemplazar Condicional por Polimorfismo

## Problema

Tiene una condicional que realiza varias acciones según el tipo de objeto o sus propiedades.

```
class Ave {
// ...
double getVelocidad() {
switch (tipo) {
case EUROPEO:
return obtenerVelocidadBase();
case AFRICANO:
return obtenerVelocidadBase() - obtenerFactorCarga() * numeroCocos;
case LORO_NORUEGO:
return (estaClavado) ? 0 : obtenerVelocidadBase(voltaje);
}
throw new RuntimeException("No debería ser alcanzable");
}
}
```

## Solución

Cree subclases que coincidan con las ramas de la condicional. En ellas, cree un método compartido y mueva el código de 
la rama correspondiente de la condicional a él. Luego, reemplace la condicional con la llamada al método relevante. El 
resultado es que la implementación adecuada se logrará a través del polimorfismo según la clase del objeto.

```
abstract class Ave {
    // ...
    abstract double getVelocidad();
}

class Europeo extends Ave {
    double getVelocidad() {
    return obtenerVelocidadBase();
    }
}
class Africano extends Ave {
    double getVelocidad() {
        return obtenerVelocidadBase() - obtenerFactorCarga() * numeroCocos;
    }
}
class LoroNoruego extends Ave {
    double getVelocidad() {
        return (estaClavado) ? 0 : obtenerVelocidadBase(voltaje);
    }
}

// En algún lugar del código del cliente
velocidad = ave.getVelocidad();
```

## Por qué Refactorizar

Esta técnica de refactorización puede ayudar si su código contiene operadores que realizan varias tareas que varían 
según:

* Clase del objeto o la interfaz que implementa

* Valor de un campo de objeto

* Resultado de llamar a uno de los métodos de un objeto

Si aparece una nueva propiedad u objeto, deberá buscar y agregar código en todas las condicionales similares. Por lo 
tanto, el beneficio de esta técnica se multiplica si hay varias condicionales dispersas en todos los métodos de un 
objeto.

## Beneficios

* Esta técnica se adhiere al principio Dime, no preguntes: en lugar de preguntarle a un objeto sobre su estado y luego 
realizar acciones basadas en esto, es mucho más fácil simplemente decirle al objeto lo que necesita hacer y permitirle 
decidir por sí mismo cómo hacerlo.

* Elimina código duplicado. Te deshaces de muchas condicionales casi idénticas.

* Si necesita agregar una nueva variante de ejecución, todo lo que necesita hacer es agregar una nueva subclase sin tocar 
el código existente (Principio Abierto/Cerrado).

## Cómo Refactorizar

### Preparándose para Refactorizar

Para esta técnica de refactorización, deberá tener una jerarquía lista de clases que contengan comportamientos 
alternativos. Si no tiene una jerarquía como esta, cree una. Otras técnicas ayudarán a que esto suceda:

* [Reemplazar Código de Tipo con Subclases](ReplaceTypeCodewithSubclasses.md). Se crearán subclases para todos 
los valores de una propiedad particular del objeto. Este enfoque es simple pero menos flexible, ya que no puede crear 
subclases para las otras propiedades del objeto.

* [Reemplazar Código Tipo con Estado/Estrategia](ReplaceTypeCodeWithStateStrategy.md). Se creará una clase dedicada a 
una propiedad particular del objeto y se crearán subclases de ella para cada valor de la propiedad. La clase actual 
contendrá referencias a los objetos de este tipo y delegará la ejecución en ellos.

Los siguientes pasos asumen que ya ha creado la jerarquía.

## Pasos para la refactorización

1. Si la condición está en un método que realiza otras acciones, realice [Metodo de Extraccion](ExtractMethod.md).

2. Para cada subclase de la jerarquía, redefina el método que contiene la condición y copie el código de la rama 
condicional correspondiente a esa ubicación.

3. Elimine esta rama de la condición.

4. Repita el reemplazo hasta que la condición esté vacía. Luego, elimine la condición y declare el método abstracto.

## Elimina Olor

[Switch Statements](../CodeSmell/SwitchStatements.md)