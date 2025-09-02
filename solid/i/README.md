# Principio I: Segregación de Interfaces (ISP)

El principio de **Segregación de Interfaces** establece que los clientes no deben ser forzados a depender de interfaces que no usan. Es decir, es mejor tener muchas interfaces específicas que una interfaz general con muchos métodos.

---

## ¿Qué significa ISP?

- Los clientes no deben depender de métodos que no utilizan.
- Es mejor tener interfaces pequeñas y cohesivas que una interfaz "gorda".
- Cada interfaz debe tener una responsabilidad específica.

Este principio ayuda a evitar acoplamientos innecesarios y facilita el mantenimiento y la extensibilidad del software.

---

## Diagrama explicativo

El Interface Segregation Principle se puede visualizar como la diferencia entre una "interfaz gorda" y múltiples "interfaces delgadas":

```
ANTES (Violando ISP):           DESPUÉS (Cumpliendo ISP):
┌─────────────────┐             ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│   Interfaz      │             │ Interfaz A  │  │ Interfaz B  │  │ Interfaz C  │
│   "GORDA"       │             │ (delgada)   │  │ (delgada)   │  │ (delgada)   │
│                 │             │             │  │             │  │             │
│ • método1()     │             │ • método1() │  │ • método2() │  │ • método3() │
│ • método2()     │             └─────────────┘  └─────────────┘  └─────────────┘
│ • método3()     │                     │               │               │
│ • método4()     │                     └───────────────┼───────────────┘
│ • método5()     │                                     │
└─────────────────┘                                     │
         │                                               │
         └───────────────────────────────────────────────┘
```

**Descripción:**
- **Antes:** Una interfaz "gorda" que contiene muchos métodos, forzando a los clientes a implementar funcionalidades que no necesitan.
- **Después:** Múltiples interfaces "delgadas" y específicas, donde cada cliente solo implementa lo que realmente necesita.

---

## Ejemplo conceptual

Imagina un sistema donde tienes una interfaz `Worker` que incluye métodos para trabajar, comer y dormir. Un robot implementa esta interfaz pero no necesita comer ni dormir, por lo que debe lanzar excepciones o implementar métodos vacíos.

**Anti-patrón:**
```java
interface Worker {
    void work();
    void eat();
    void sleep();
}

class Robot implements Worker {
    public void work() { /* lógica */ }
    public void eat() { throw new UnsupportedOperationException(); }
    public void sleep() { throw new UnsupportedOperationException(); }
}
```

**Aplicando ISP:**
Para cumplir ISP, se deben separar las responsabilidades en interfaces específicas:

```java
interface Workable {
    void work();
}
interface Eatable {
    void eat();
}
interface Sleepable {
    void sleep();
}

class Human implements Workable, Eatable, Sleepable {
    // implementa todos los métodos
}
class Robot implements Workable {
    // solo implementa work()
}
```

Ahora cada clase solo implementa las interfaces que realmente necesita.

---

## Ventajas de aplicar ISP

- Reduce el acoplamiento entre clases.
- Facilita la implementación de interfaces específicas.
- Mejora la flexibilidad y mantenibilidad del código.

---

## Riesgos de no aplicar ISP

- Clases que implementan métodos que no necesitan.
- Acoplamiento innecesario entre componentes.
- Dificultad para mantener y extender el sistema.

---

## Ejemplos por lenguaje

Consulta los ejemplos prácticos en distintos lenguajes en la carpeta [`ejemplos`](./ejemplos/README.md).

---

## Recursos y lecturas recomendadas

- [SOLID Principles explicados (Wikipedia)](https://es.wikipedia.org/wiki/SOLID)
- [SOLID Principles en FreeCodeCamp](https://www.freecodecamp.org/news/solid-principles-explained-in-plain-english/)
- Robert C. Martin – "Clean Architecture"
- [Design Principles and Design Patterns (Uncle Bob)](http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf)

---

> "Los clientes no deben ser forzados a depender de interfaces que no usan." — Robert C. Martin