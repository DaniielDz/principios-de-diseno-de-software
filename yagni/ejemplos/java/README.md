# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo YAGNI en Java

Este ejemplo muestra cómo evitar agregar paginación en una API cuando solo se requiere mostrar los primeros 10 resultados.

---

## Antes (NO cumple YAGNI)
```java
public class ProductoService {
    public List<Producto> obtenerProductos(int pagina, int tamaño) {
        // Lógica de paginación
        // ...
        return productos;
    }
}
```

## Después (Cumple YAGNI)
```java
public class ProductoService {
    public List<Producto> obtenerPrimerosProductos() {
        // Retorna los primeros 10 productos
        // ...
        return productos.subList(0, 10);
    }
}
```

**Aplicación de YAGNI:**
Solo se implementa la funcionalidad requerida actualmente (mostrar primeros 10 productos). Si en el futuro se necesita paginación, se agrega en ese momento.

---

> "No lo vas a necesitar" — Kent Beck
