# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo SRP en C#

Este ejemplo muestra cómo separar la lógica de cálculo y la lógica de notificación en una clase de orden.

---

## Antes (NO cumple SRP)
```csharp
public class Orden {
    public decimal CalcularTotal(List<Producto> productos) {
        return productos.Sum(p => p.Precio);
    }
    public void NotificarCliente(string email) {
        // Lógica para notificar al cliente
    }
}
```

## Después (Cumple SRP)
```csharp
public class Orden {
    public decimal CalcularTotal(List<Producto> productos) {
        return productos.Sum(p => p.Precio);
    }
}

public class Notificador {
    public void NotificarCliente(string email) {
        // Lógica para notificar al cliente
    }
}
```

**Aplicación de SRP:**
Cada clase tiene una única responsabilidad: `Orden` calcula el total y `Notificador` se encarga de la notificación.
