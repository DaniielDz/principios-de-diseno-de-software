# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="32"/> Ejemplo YAGNI en PHP

Este ejemplo muestra cómo evitar agregar lógica de descuentos por temporada si solo se requiere precio fijo.

---

## Antes (NO cumple YAGNI)
```php
function calcularPrecio($precio, $temporada = null) {
    if ($temporada === 'verano') {
        return $precio * 0.9;
    } elseif ($temporada === 'invierno') {
        return $precio * 0.95;
    }
    return $precio;
}
```

## Después (Cumple YAGNI)
```php
function calcularPrecio($precio) {
    return $precio;
}
```

**Aplicación de YAGNI:**
Solo se implementa el cálculo de precio fijo, que es lo que se requiere actualmente. Si en el futuro se necesitan descuentos por temporada, se agrega en ese momento.

---

> "No lo vas a necesitar" — Kent Beck
