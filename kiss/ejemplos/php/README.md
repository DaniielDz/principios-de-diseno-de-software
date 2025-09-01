# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="32"/> Ejemplo KISS en PHP

Este ejemplo muestra cómo aplicar el principio KISS para obtener los nombres de usuarios activos en un arreglo. Se compara una versión tradicional con una versión usando funciones de alto nivel.

---

## Antes (complejo)
```php
function getActiveUserNames($users) {
    $names = array();
    foreach ($users as $u) {
        if ($u['is_active']) {
            $names[] = $u['name'];
        }
    }
    return $names;
}
```

## Problemas de la versión compleja
- Uso manual de bucles y lógica repetitiva.
- Menor legibilidad y mayor probabilidad de errores.
- Difícil de mantener y modificar.

---

## Después (KISS)
```php
function getActiveUserNames($users) {
    return array_map(function($u) {
        return $u['name'];
    }, array_filter($users, function($u) {
        return $u['is_active'];
    }));
}
```

## Ventajas de la versión KISS
- Uso de funciones de alto nivel (`array_map`, `array_filter`) para mayor claridad.
- El código se enfoca en la tarea principal.
- Más fácil de leer, mantener y modificar.

---

## ¿Cómo se aplica KISS aquí?
El principio KISS se aplica utilizando las herramientas del lenguaje para expresar la lógica de forma directa y eficiente, evitando la complejidad innecesaria.

---

> "La simplicidad es la máxima sofisticación." — Leonardo da Vinci
