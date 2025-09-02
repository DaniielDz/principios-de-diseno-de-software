# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo DRY en C#

Este ejemplo muestra cómo evitar duplicación de lógica en el cálculo de total con impuestos para productos y servicios.

---

## Antes (NO cumple DRY)
```csharp
decimal CalcularTotalProducto(decimal precio, decimal impuesto) {
    decimal total = precio + (precio * impuesto);
    return total;
}

decimal CalcularTotalServicio(decimal precio, decimal impuesto) {
    decimal total = precio + (precio * impuesto);
    return total;
}
```

## Después (Cumple DRY)
```csharp
decimal CalcularTotal(decimal precio, decimal impuesto) {
    return precio + (precio * impuesto);
}

// Uso
CalcularTotal(100, 0.16);
CalcularTotal(200, 0.10);
```

**Aplicación de DRY:**
La lógica de cálculo de total con impuestos está centralizada en un solo método reutilizable, evitando duplicación y facilitando el mantenimiento.

---

> "La duplicación es el enemigo. Eliminarla es el primer paso hacia un buen diseño." — Robert C. Martin
