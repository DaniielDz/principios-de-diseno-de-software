# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="32"/> Ejemplo SRP en PHP

Este ejemplo muestra cómo separar la lógica de cálculo y la lógica de almacenamiento en una clase de pedido.

---

## Antes (NO cumple SRP)
```php
class Pedido {
    public function calcularTotal($productos) {
        return array_sum(array_map(function($p) { return $p['precio']; }, $productos));
    }
    public function guardarEnBD() {
        // Lógica para guardar en base de datos
    }
}
```

## Después (Cumple SRP)
```php
class Pedido {
    public function calcularTotal($productos) {
        return array_sum(array_map(function($p) { return $p['precio']; }, $productos));
    }
}

class PedidoRepository {
    public function guardarEnBD($pedido) {
        // Lógica para guardar en base de datos
    }
}
```

**Aplicación de SRP:**
Cada clase tiene una única responsabilidad: `Pedido` calcula el total y `PedidoRepository` se encarga del almacenamiento.
