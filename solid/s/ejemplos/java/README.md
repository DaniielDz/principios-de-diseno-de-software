# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo SRP en Java

Este ejemplo muestra cómo separar la lógica de cálculo y la lógica de impresión en una clase de factura.

---

## Antes (NO cumple SRP)
```java
public class Factura {
    public double calcularTotal(List<Producto> productos) {
        // Lógica de cálculo
        return productos.stream().mapToDouble(Producto::getPrecio).sum();
    }
    public void imprimirFactura() {
        // Lógica para imprimir la factura
    }
}
```

## Después (Cumple SRP)
```java
public class Factura {
    public double calcularTotal(List<Producto> productos) {
        return productos.stream().mapToDouble(Producto::getPrecio).sum();
    }
}

public class FacturaPrinter {
    public void imprimirFactura(Factura factura) {
        // Lógica para imprimir la factura
    }
}
```

**Aplicación de SRP:**
Cada clase tiene una única responsabilidad: `Factura` calcula el total y `FacturaPrinter` se encarga de la impresión.
