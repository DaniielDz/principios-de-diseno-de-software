# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo DRY en TypeScript

Este ejemplo muestra cómo evitar duplicación de lógica en el cálculo de descuentos para productos.

---

## Antes (NO cumple DRY)
```typescript
function calcularPrecioFinalProducto(precio: number, descuento: number): number {
  const precioConDescuento = precio - (precio * descuento);
  return precioConDescuento;
}

function calcularPrecioFinalServicio(precio: number, descuento: number): number {
  const precioConDescuento = precio - (precio * descuento);
  return precioConDescuento;
}
```

## Después (Cumple DRY)
```typescript
function calcularPrecioFinal(precio: number, descuento: number): number {
  return precio - (precio * descuento);
}

// Uso
const producto = calcularPrecioFinal(100, 0.2);
const servicio = calcularPrecioFinal(200, 0.15);
```

**Aplicación de DRY:**
La lógica de cálculo de descuento está centralizada en una sola función reutilizable, evitando duplicación y facilitando el mantenimiento.

---

> "La duplicación es el enemigo. Eliminarla es el primer paso hacia un buen diseño." — Robert C. Martin
