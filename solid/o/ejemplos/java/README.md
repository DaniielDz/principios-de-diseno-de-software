# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo OCP en Java

Este ejemplo muestra cómo transformar una clase rígida en un sistema extensible para la persistencia de facturas.

---

## Antes (NO cumple OCP)
```java
public class InvoicePersistence {
    public void saveToFile(Invoice invoice) {
        // Lógica para guardar en archivo
    }
    public void saveToDatabase(Invoice invoice) {
        // Lógica para guardar en base de datos
    }
}
```

**Problema:** Cada vez que necesitas guardar en un nuevo formato, debes modificar la clase y arriesgar el código existente. Esto dificulta la escalabilidad y el mantenimiento.

---

## Después (Cumple OCP)
```java
public interface InvoicePersistence {
    void save(Invoice invoice);
}

public class FilePersistence implements InvoicePersistence {
    public void save(Invoice invoice) {
        // Lógica para guardar en archivo
    }
}

public class DatabasePersistence implements InvoicePersistence {
    public void save(Invoice invoice) {
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