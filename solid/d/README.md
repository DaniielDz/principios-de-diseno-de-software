# Principio D: Inversión de Dependencias (DIP)

El principio de **Inversión de Dependencias** establece que los módulos de alto nivel no deben depender de módulos de bajo nivel. Ambos deben depender de abstracciones. Las abstracciones no deben depender de los detalles, sino que los detalles deben depender de las abstracciones.

---

## ¿Qué significa DIP?

- Los módulos de alto nivel no deben depender de módulos de bajo nivel.
- Ambos deben depender de abstracciones (interfaces o clases abstractas).
- Las abstracciones no deben depender de los detalles.
- Los detalles deben depender de las abstracciones.

Este principio ayuda a crear sistemas más flexibles, mantenibles y testeables al reducir el acoplamiento entre componentes.

---

## Diagrama explicativo

El Dependency Inversion Principle se puede visualizar como la inversión de las dependencias tradicionales:

```
ANTES (Violando DIP):           DESPUÉS (Cumpliendo DIP):
┌─────────────────┐             ┌─────────────────┐
│   Módulo Alto   │             │   Módulo Alto   │
│     Nivel       │             │     Nivel       │
└─────────┬───────┘             └─────────┬───────┘
          │                               │
          │ depende de                    │ depende de
          ▼                               ▼
┌─────────────────┐             ┌─────────────────┐
│   Módulo Bajo   │             │   Abstracción   │
│     Nivel       │             │   (Interfaz)    │
└─────────────────┘             └────────┬────────┘
                                         │
                                         │ implementa
                                         ▼
                                ┌─────────────────┐
                                │   Módulo Bajo   │
                                │     Nivel       │
                                └─────────────────┘
```

**Descripción:**
- **Antes:** El módulo de alto nivel depende directamente del módulo de bajo nivel, creando acoplamiento fuerte.
- **Después:** Ambos módulos dependen de una abstracción, permitiendo que el módulo de bajo nivel sea intercambiable.

---

## Ejemplo conceptual

Imagina un sistema de notificaciones donde una clase `OrderService` (alto nivel) necesita enviar notificaciones. Sin DIP, dependería directamente de `EmailService` (bajo nivel), pero con DIP, ambos dependen de la interfaz `NotificationService`.

**Anti-patrón:**
```java
class OrderService {
    private EmailService emailService = new EmailService();
    
    public void processOrder() {
        // lógica de negocio
        emailService.sendEmail("Order processed");
    }
}
```

**Aplicando DIP:**
```java
interface NotificationService {
    void send(String message);
}

class EmailService implements NotificationService {
    public void send(String message) { /* envío por email */ }
}

class OrderService {
    private NotificationService notificationService;
    
    public OrderService(NotificationService service) {
        this.notificationService = service;
    }
    
    public void processOrder() {
        // lógica de negocio
        notificationService.send("Order processed");
    }
}
```

Ahora `OrderService` puede usar cualquier implementación de `NotificationService` sin estar acoplado a una implementación específica.

---

## Ventajas de aplicar DIP

- Reduce el acoplamiento entre módulos.
- Facilita las pruebas unitarias (inyección de dependencias).
- Permite intercambiar implementaciones fácilmente.
- Mejora la flexibilidad y mantenibilidad del sistema.

---

## Riesgos de no aplicar DIP

- Acoplamiento fuerte entre módulos.
- Dificultad para realizar pruebas unitarias.
- Cambios en módulos de bajo nivel afectan módulos de alto nivel.
- Dificultad para reutilizar y extender el sistema.

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

> "Los módulos de alto nivel no deben depender de módulos de bajo nivel. Ambos deben depender de abstracciones." — Robert C. Martin
