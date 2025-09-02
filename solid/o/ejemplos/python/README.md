# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo OCP en Python

Este ejemplo muestra cómo transformar una clase rígida en un sistema extensible para la persistencia de facturas.

---

## Antes (NO cumple OCP)
```python
class InvoicePersistence:
    def save_to_file(self, invoice):
        # Lógica para guardar en archivo
        pass
    def save_to_database(self, invoice):
        # Lógica para guardar en base de datos
        pass
```

**Problema:** Cada vez que necesitas guardar en un nuevo formato, debes modificar la clase y arriesgar el código existente. Esto dificulta la escalabilidad y el mantenimiento.

---

## Después (Cumple OCP)
```python
from abc import ABC, abstractmethod

class InvoicePersistence(ABC):
    @abstractmethod
    def save(self, invoice):
        pass

class FilePersistence(InvoicePersistence):
    def save(self, invoice):
        # Lógica para guardar en archivo
        pass

class DatabasePersistence(InvoicePersistence):
    def save(self, invoice):
        # Lógica para guardar en base de datos
        pass
```

**Aplicación de OCP:**
Puedes agregar nuevos tipos de persistencia sin modificar el código existente, solo creando nuevas clases que implementen la interfaz. El sistema es más seguro y escalable.

---

**Resumen visual:**
- Antes: Modificas la clase cada vez que agregas una funcionalidad.
- Después: Extiendes el sistema creando nuevas clases, sin tocar el código probado.