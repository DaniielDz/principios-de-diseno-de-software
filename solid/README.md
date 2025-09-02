# Principios SOLID

Los principios **SOLID** son un conjunto de cinco reglas fundamentales para el diseño de software orientado a objetos. Ayudan a crear sistemas más flexibles, mantenibles y escalables, facilitando el trabajo en equipo y la evolución del código.

![SOLID](https://www.freecodecamp.org/news/content/images/size/w600/2020/08/solid.png)
---

## ¿Qué significa SOLID?

- **S**: Single Responsibility Principle (Responsabilidad Única)
- **O**: Open/Closed Principle (Abierto/Cerrado)
- **L**: Liskov Substitution Principle (Sustitución de Liskov)
- **I**: Interface Segregation Principle (Segregación de Interfaces)
- **D**: Dependency Inversion Principle (Inversión de Dependencias)

Cada principio aborda un aspecto clave del diseño orientado a objetos y juntos forman una guía para escribir código limpio y robusto.

---

## ¿Por qué son importantes los principios SOLID?

- **Facilitan la mantenibilidad:** El código es más fácil de modificar y extender sin romper funcionalidades existentes.
- **Mejoran la escalabilidad:** Permiten agregar nuevas características sin grandes refactorizaciones.
- **Reducen el acoplamiento:** Fomentan la independencia entre módulos y clases.
- **Promueven la reutilización:** El diseño modular facilita el uso de componentes en diferentes contextos.
- **Favorecen el trabajo en equipo:** Un código claro y bien estructurado es más fácil de entender y compartir.

---

## Índice de Principios SOLID

1. [S: Responsabilidad Única (SRP)](./s/README.md)
2. [O: Abierto/Cerrado (OCP)](./o/README.md)
3. [L: Sustitución de Liskov (LSP)](./l/README.md)
4. [I: Segregación de Interfaces (ISP)](./i/README.md)
5. [D: Inversión de Dependencias (DIP)](./d/README.md)

Cada principio tiene su propio README con explicación detallada y ejemplos prácticos en distintos lenguajes.

---

## Ejemplo general de SOLID

Imagina un sistema de facturación. Si aplicas SOLID:
- Cada clase tiene una única responsabilidad (SRP).
- Puedes agregar nuevos tipos de facturas sin modificar las clases existentes (OCP).
- Las subclases pueden sustituir a sus clases base sin alterar el funcionamiento (LSP).
- Las interfaces están bien definidas y no obligan a implementar métodos innecesarios (ISP).
- Las dependencias se gestionan mediante abstracciones, no implementaciones concretas (DIP).

---

## Cómo aplicar SOLID en la práctica

### 1. **Empieza con SRP**
- Identifica clases que hacen más de una cosa
- Separa responsabilidades en clases diferentes
- Cada clase debe tener una única razón para cambiar

### 2. **Aplica OCP gradualmente**
- Usa interfaces y clases abstractas
- Extiende funcionalidad sin modificar código existente
- Aplica el patrón Strategy o Template Method

### 3. **Verifica LSP en herencias**
- Asegúrate de que las subclases respeten el contrato de la clase base
- Evita sobrescribir métodos de manera que cambien el comportamiento esperado

### 4. **Segrega interfaces grandes**
- Divide interfaces "gordas" en interfaces más pequeñas y específicas
- Los clientes solo deben depender de lo que realmente usan

### 5. **Invierte las dependencias**
- Depende de abstracciones, no de implementaciones concretas
- Usa inyección de dependencias
- Aplica el patrón Dependency Injection

---

## Recursos recomendados

- [SOLID (wikipedia)](https://es.wikipedia.org/wiki/SOLID)
- [Los principios SOLID de programación orientada a objetos explicados en Español sencillo](https://www.freecodecamp.org/espanol/news/los-principios-solid-explicados-en-espanol/)
- [Principios SOLID: 5 claves para tu desarrollo de software](https://www.hackio.com/blog/principios-solid)
- [SOLID: los 5 principios que te ayudarán a desarrollar software de calidad](https://profile.es/blog/principios-solid-desarrollo-software-calidad/)

---

> "El buen diseño de software es aquel que puede cambiar fácilmente sin romper nada." — Robert C. Martin