# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="32"/> Ejemplo DRY en PHP

Este ejemplo muestra cómo evitar duplicación de lógica en el formateo de precios para productos y servicios.

---

## Antes (NO cumple DRY)
```php
function formatPriceProduct($price) {
    return '$' . number_format($price, 2);
}

function formatPriceService($price) {
    return '$' . number_format($price, 2);
}
```

## Después (Cumple DRY)
```php
function formatPrice($price) {
    return '$' . number_format($price, 2);
}

// Uso
formatPrice(99.99);
formatPrice(150.50);
```

**Aplicación de DRY:**
La lógica de formateo de precios está centralizada en una sola función reutilizable, evitando duplicación y facilitando el mantenimiento.

---

> "La duplicación es el enemigo. Eliminarla es el primer paso hacia un buen diseño." — Robert C. Martin
