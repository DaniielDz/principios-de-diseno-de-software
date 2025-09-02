# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo OCP en Ruby

Este ejemplo muestra cómo transformar una clase rígida en un sistema extensible para la persistencia de facturas.

---

## Antes (NO cumple OCP)
```ruby
class InvoicePersistence
  def save_to_file(invoice)
    # Lógica para guardar en archivo
  end
  def save_to_database(invoice)
    # Lógica para guardar en base de datos
  end
end
```

**Problema:** Cada vez que necesitas guardar en un nuevo formato, debes modificar la clase y arriesgar el código existente. Esto dificulta la escalabilidad y el mantenimiento.

---

## Después (Cumple OCP)
```ruby
class InvoicePersistence
  def save(invoice)
    raise NotImplementedError
  end
end

class FilePersistence < InvoicePersistence
  def save(invoice)
    # Lógica para guardar en archivo
  end
end

class DatabasePersistence < InvoicePersistence
  def save(invoice)
    # Lógica para guardar en base de datos
  end
end
```

**Aplicación de OCP:**
Puedes agregar nuevos tipos de persistencia sin modificar el código existente, solo creando nuevas clases que extienden la base. El sistema es más seguro y escalable.

---

**Resumen visual:**
- Antes: Modificas la clase cada vez que agregas una funcionalidad.
- Después: Extiendes el sistema creando nuevas clases, sin tocar el código probado.