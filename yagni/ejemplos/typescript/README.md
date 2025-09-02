# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo YAGNI en TypeScript

Este ejemplo muestra cómo evitar agregar lógica de paginación en una API cuando solo se requiere mostrar los primeros 10 resultados.

---

## Antes (NO cumple YAGNI)
```typescript
class ProductoService {
  obtenerProductos(pagina: number, tamanio: number): Producto[] {
    // Lógica de paginación innecesaria
    // ...
    return productos;
  }
}
```

## Después (Cumple YAGNI)
```typescript
class ProductoService {
  obtenerPrimerosProductos(): Producto[] {
    // Retorna los primeros 10 productos
    // ...
    return productos.slice(0, 10);
  }
}
```

**Aplicación de YAGNI:**
Solo se implementa la funcionalidad requerida actualmente (mostrar primeros 10 productos). Si en el futuro se necesita paginación, se agrega en ese momento.

---

> "No lo vas a necesitar" — Kent Beck
