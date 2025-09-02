# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo OCP en Go

Este ejemplo muestra cómo transformar una estructura rígida en un sistema extensible para la persistencia de facturas.

---

## Antes (NO cumple OCP)
```go
package main

type InvoicePersistence struct{}

func (ip InvoicePersistence) SaveToFile(invoice string) {
    // Lógica para guardar en archivo
}
func (ip InvoicePersistence) SaveToDatabase(invoice string) {
    // Lógica para guardar en base de datos
}
```

**Problema:** Cada vez que necesitas guardar en un nuevo formato, debes modificar la estructura y arriesgar el código existente. Esto dificulta la escalabilidad y el mantenimiento.

---

## Después (Cumple OCP)
```go
package main

type InvoicePersistence interface {
    Save(invoice string)
}

type FilePersistence struct{}
func (fp FilePersistence) Save(invoice string) {
    // Lógica para guardar en archivo
}

type DatabasePersistence struct{}
func (dp DatabasePersistence) Save(invoice string) {
    // Lógica para guardar en base de datos
}
```

**Aplicación de OCP:**
Puedes agregar nuevos tipos de persistencia sin modificar el código existente, solo creando nuevas estructuras que implementen la interfaz. El sistema es más seguro y escalable.

---

**Resumen visual:**
- Antes: Modificas la estructura cada vez que agregas una funcionalidad.
- Después: Extiendes el sistema creando nuevas estructuras, sin tocar el código probado.