# Principio O: Abierto/Cerrado (OCP)

El principio de **Abierto/Cerrado** establece que las entidades de software (clases, módulos, funciones) deben estar abiertas para su extensión, pero cerradas para su modificación. Es decir, deberías poder agregar nuevas funcionalidades sin modificar el código existente.

---

## ¿Qué significa OCP?

- **Abierto para extensión:** Puedes agregar nuevos comportamientos.
- **Cerrado para modificación:** No necesitas cambiar el código probado y existente.

Este principio fomenta la creación de sistemas flexibles y robustos, donde los cambios futuros no ponen en riesgo la estabilidad del software.

---

## Diagrama explicativo

El Open/Closed Principle se puede visualizar como la extensión sin modificación:

```
ANTES (Violando OCP):           DESPUÉS (Cumpliendo OCP):
┌─────────────────┐             ┌─────────────────┐
│ FacturaPersistence│             │ FacturaPersistence│
│   (MODIFICABLE)  │             │   (INTERFAZ)    │
│                 │             │                 │
│ • saveToFile()  │             │ • save()        │
│ • saveToDB()    │             └─────────┬───────┘
│ • saveToCloud() │                       │
└─────────────────┘                       │ implementa
         │                               │
         │ MODIFICA                      ▼
         ▼                       ┌─────────────────┐
┌─────────────────┐             │  FilePersistence │
│   NUEVA FUNC.   │             │                 │
│                 │             │ • save()        │
│ • saveToAPI()   │             └─────────────────┘
└─────────────────┘                       │
                                         │
                                         ▼
                                ┌─────────────────┐
                                │DatabasePersistence│
                                │                 │
                                │ • save()        │
                                └─────────────────┘
```

**Descripción:**
- **Antes:** Para agregar nueva funcionalidad, se modifica la clase existente, violando OCP.
- **Después:** Se extiende mediante nuevas implementaciones de la interfaz, sin modificar código existente.

---

## Ejemplo conceptual

Supón que tienes una clase que guarda facturas en un archivo. Si luego necesitas guardar en una base de datos, no deberías modificar la clase original, sino extenderla:

**Anti-patrón:**
```java
class FacturaPersistence {
    void saveToFile(Factura f) { /* ... */ }
    void saveToDatabase(Factura f) { /* ... */ }
}
```
**Aplicando OCP:**
```java
interface FacturaPersistence {
    void save(Factura f);
}
class FilePersistence implements FacturaPersistence {
    void save(Factura f) { /* ... */ }
}
class DatabasePersistence implements FacturaPersistence {
    void save(Factura f) { /* ... */ }
}
```

---

## Ventajas de aplicar OCP

- **Menos riesgo de bugs:** El código probado no se modifica.
- **Facilita la escalabilidad:** Puedes agregar nuevas funcionalidades fácilmente.
- **Mejor mantenimiento:** El sistema es más robusto ante cambios.

---

## Riesgos de no aplicar OCP

- Modificar código existente puede introducir errores.
- Dificultad para agregar nuevas funcionalidades.
- Mayor esfuerzo de testing y revisión.

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

## Contexto histórico

El OCP fue formulado por Bertrand Meyer y popularizado por Robert C. Martin. Es esencial para sistemas extensibles y seguros ante cambios.

---

> "Las entidades de software deben estar abiertas para su extensión, pero cerradas para su modificación." — Bertrand Meyer