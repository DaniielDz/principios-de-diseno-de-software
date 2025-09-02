# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo OCP en C#

Este ejemplo muestra cómo transformar una clase rígida en un sistema extensible para la persistencia de facturas.

---

## Antes (NO cumple OCP)
```csharp
public class InvoicePersistence {
    public void SaveToFile(Invoice invoice) {
        // Lógica para guardar en archivo
    }
    public void SaveToDatabase(Invoice invoice) {
        // Lógica para guardar en base de datos
    }
}
```

**Problema:** Cada vez que necesitas guardar en un nuevo formato, debes modificar la clase y arriesgar el código existente. Esto dificulta la escalabilidad y el mantenimiento.

---

## Después (Cumple OCP)
```csharp
public interface IInvoicePersistence {
    void Save(Invoice invoice);
}

public class FilePersistence : IInvoicePersistence {
    public void Save(Invoice invoice) {
        // Lógica para guardar en archivo
    }
}

public class DatabasePersistence : IInvoicePersistence {
    public void Save(Invoice invoice) {
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