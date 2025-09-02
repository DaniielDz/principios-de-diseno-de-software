# Principio L: Sustitución de Liskov (LSP)

El principio de **Sustitución de Liskov** establece que los objetos de una clase derivada deben poder sustituir a los de la clase base sin alterar el funcionamiento del programa. Es decir, las subclases deben respetar el contrato de la clase base.

---

## ¿Qué significa LSP?

- Las subclases pueden usarse en lugar de la clase base sin efectos inesperados.
- No se deben romper las expectativas del usuario de la clase base.

Este principio ayuda a evitar errores sutiles y facilita la extensibilidad y el mantenimiento del software orientado a objetos.

---

## Diagrama explicativo

<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*wk3Txs5r-0CZXYR-Ec0RYw.png" width="400"/>

**Descripción:**
- En lugar de tener una sola jerarquía mal diseñada (por ejemplo, una clase Vehicle con métodos que no aplican a todos), aquí se divide la jerarquía en interfaces especializadas.
- Así se evita que una clase deba implementar métodos que no le corresponden (ejemplo: una bicicleta nunca debería tener startEngine()).
- Este diseño respeta el principio de Liskov, porque cualquier clase que implemente Vehicle puede usarse sin romper el contrato esperado: todos saben iniciarse y moverse, aunque cada uno lo haga de manera distinta.

---

## Ejemplo conceptual

Imagina un sistema de gráficos donde tienes una clase base `Rectangulo` y una subclase `Cuadrado`. El sistema espera que cualquier `Rectangulo` permita modificar su ancho y alto independientemente. Si el `Cuadrado` fuerza que ambos sean iguales, rompe el contrato y puede causar errores en funciones que esperan un `Rectangulo` estándar.

**Anti-patrón:**
```java
Rectangulo r = new Cuadrado();
r.setWidth(5);
r.setHeight(10);
System.out.println(r.getArea()); // Esperado: 50, pero devuelve 100
```

**Aplicando LSP:**
Para cumplir LSP, se debe evitar que la subclase altere el comportamiento esperado. Una solución es separar los conceptos:

```java
abstract class Figura {
    abstract int getArea();
}
class Rectangulo extends Figura {
    int width, height;
    // ...
    int getArea() { return width * height; }
}
class Cuadrado extends Figura {
    int size;
    // ...
    int getArea() { return size * size; }
}
```

Ahora cada clase respeta su propio contrato y puede usarse sin romper expectativas en el sistema.

---

## Ventajas de aplicar LSP

- Menos errores inesperados en el uso de herencia.
- Facilita la reutilización y extensión de clases.
- Mejora la robustez y confiabilidad del sistema.

---

## Riesgos de no aplicar LSP

- Bugs difíciles de detectar.
- Comportamientos inesperados al usar subclases.
- Dificultad para mantener y extender el sistema.

---

## Ejemplos por lenguaje

Consulta los ejemplos prácticos en distintos lenguajes en la carpeta [`ejemplos`](./ejemplos/README.md).

---

## Recursos y lecturas recomendadas

- [SOLID Principles explicados (Wikipedia)](https://es.wikipedia.org/wiki/SOLID)
- [SOLID Principles en FreeCodeCamp](https://www.freecodecamp.org/news/solid-principles-explained-in-plain-english/)
- Robert C. Martin – “Clean Architecture”
- [Design Principles and Design Patterns (Uncle Bob)](http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf)

---

> "Las subclases deben poder sustituir a sus clases base sin alterar el funcionamiento del programa." — Barbara Liskov
