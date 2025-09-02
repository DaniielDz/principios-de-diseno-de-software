# Principio S: Responsabilidad Única (SRP)

El principio de **Responsabilidad Única** establece que una clase, módulo o función debe tener una sola razón para cambiar, es decir, debe encargarse de una única tarea o responsabilidad dentro del sistema.

Aplicar SRP ayuda a que el código sea más fácil de mantener, probar y extender, ya que cada componente tiene un propósito claro y definido.

---

## ¿Por qué es importante SRP?

- **Facilita el mantenimiento:** Si una clase tiene una sola responsabilidad, los cambios futuros serán más sencillos y localizados.
- **Mejora la legibilidad:** El código es más claro y fácil de entender.
- **Reduce el acoplamiento:** Las dependencias entre componentes se minimizan.
- **Favorece la reutilización:** Las clases y funciones pueden usarse en diferentes contextos sin efectos secundarios.

---

## Diagrama explicativo

El Single Responsibility Principle se puede visualizar como la separación de responsabilidades en clases específicas:

```
ANTES (Violando SRP):           DESPUÉS (Cumpliendo SRP):
┌─────────────────┐             ┌─────────────────┐  ┌─────────────────┐
│     Factura     │             │     Factura     │  │  ServicioCorreo │
│   (MÚLTIPLES    │             │   (UNA SOLA     │  │   (UNA SOLA     │
│ RESPONSABILIDADES)│             │ RESPONSABILIDAD) │  │ RESPONSABILIDAD) │
│                 │             │                 │  │                 │
│ • calcularTotal │             │ • calcularTotal │  │ • enviarCorreo  │
│ • enviarCorreo  │             └─────────────────┘  └─────────────────┘
│ • validarDatos  │                     │                     │
│ • guardarBD     │                     └─────────────────────┘
└─────────────────┘                           │
         │                                   │
         └───────────────────────────────────┘
```

**Descripción:**
- **Antes:** Una clase con múltiples responsabilidades, violando SRP.
- **Después:** Clases separadas, cada una con una única responsabilidad específica.

---

## Ejemplo conceptual

Imagina una clase `Factura` que calcula el total y también envía correos de confirmación. Si separas la lógica de cálculo y la de envío en dos clases distintas, cada una tendrá una única responsabilidad y será más fácil de mantener.

**Anti-patrón:**

```java
class Factura {
    void calcularTotal() { /* ... */ }
    void enviarCorreo() { /* ... */ }
}
```

**Aplicando SRP:**

```java
class Factura {
    void calcularTotal() { /* ... */ }
}
class ServicioCorreo {
    void enviarCorreo() { /* ... */ }
}
```

---

## Ventajas de aplicar SRP

- **Facilita el mantenimiento:** Si una clase tiene una sola responsabilidad, los cambios futuros serán más sencillos y localizados.
- **Mejora la legibilidad:** El código es más claro y fácil de entender.
- **Reduce el acoplamiento:** Las dependencias entre componentes se minimizan.
- **Favorece la reutilización:** Las clases y funciones pueden usarse en diferentes contextos sin efectos secundarios.
- **Menos conflictos en equipos:** Menos razones para modificar la misma clase, menos conflictos en control de versiones.

---

## Riesgos de no aplicar SRP

- Clases monolíticas difíciles de mantener.
- Cambios en una funcionalidad pueden romper otras.
- Mayor probabilidad de errores y bugs.
- Dificultad para realizar pruebas unitarias.

---

## Ejemplos por lenguaje

Consulta los ejemplos prácticos en distintos lenguajes en la carpeta [`ejemplos`](./ejemplos/README.md).

---

> "Una clase debe tener una, y solo una, razón para cambiar." — Robert C. Martin