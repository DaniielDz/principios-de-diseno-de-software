# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo SRP en TypeScript

Este ejemplo muestra cómo separar la lógica de cálculo y la lógica de persistencia en una clase de factura.

---

## Antes (NO cumple SRP)
```typescript
class Factura {
  calcularTotal(productos: any[]): number {
    // Lógica de cálculo
    return productos.reduce((acc, p) => acc + p.precio, 0);
  }
  guardarEnBD() {
    // Lógica para guardar en base de datos
  }
}
```

## Después (Cumple SRP)
```typescript
class Factura {
  calcularTotal(productos: any[]): number {
    return productos.reduce((acc, p) => acc + p.precio, 0);
  }
}

class FacturaRepository {
  guardarEnBD(factura: Factura) {
    // Lógica para guardar en base de datos
  }
}
```

**Aplicación de SRP:**
Cada clase tiene una única responsabilidad: `Factura` calcula el total y `FacturaRepository` se encarga de la persistencia.
