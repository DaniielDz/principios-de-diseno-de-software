# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo OCP en TypeScript

Este ejemplo muestra cómo pasar de una solución rígida a una extensible para la persistencia de facturas.

---

## Antes (NO cumple OCP)
```typescript
class InvoicePersistence {
  saveToFile(invoice: any) {
    // Lógica para guardar en archivo
  }
  saveToDatabase(invoice: any) {
    // Lógica para guardar en base de datos
  }
}
```

**Problema:** Si necesitas guardar en otro formato, debes modificar la clase y arriesgar el código existente. Cada nueva funcionalidad implica editar la clase y puede romper el sistema.

---

## Después (Cumple OCP)
```typescript
interface InvoicePersistence {
  save(invoice: any): void;
}

class FilePersistence implements InvoicePersistence {
  save(invoice: any) {
    // Lógica para guardar en archivo
  }
}

class DatabasePersistence implements InvoicePersistence {
  save(invoice: any) {
    // Lógica para guardar en base de datos
  }
}
```

**Aplicación de OCP:**
Puedes agregar nuevos tipos de persistencia sin modificar el código existente, solo creando nuevas clases que implementen la interfaz. El sistema es más seguro y escalable.

---

**Resumen visual:**
- Antes: Modificas la clase cada vez que agregas una funcionalidad.
- Después: Extiendes el sistema creando nuevas clases, sin tocar el código probado.