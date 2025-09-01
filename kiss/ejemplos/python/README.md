# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo KISS en Python

Este ejemplo muestra cómo aplicar el principio KISS para obtener los nombres de usuarios activos en una lista de diccionarios. Se compara una versión tradicional con una versión usando list comprehensions.

---

## Antes (complejo)
```python
def get_active_user_names(users):
    names = []
    for u in users:
        if u['is_active']:
            names.append(u['name'])
    return names
```

## Problemas de la versión compleja
- Uso manual de bucles y lógica repetitiva.
- Menor legibilidad y mayor probabilidad de errores.
- Difícil de mantener y modificar.

---

## Después (KISS)
```python
def get_active_user_names(users):
    return [u['name'] for u in users if u['is_active']]
```

## Ventajas de la versión KISS
- Uso de list comprehensions para mayor claridad y simplicidad.
- El código se enfoca en la tarea principal.
- Más fácil de leer, mantener y modificar.

---

## ¿Cómo se aplica KISS aquí?
El principio KISS se aplica utilizando las herramientas del lenguaje para expresar la lógica de forma directa y eficiente, evitando la complejidad innecesaria.

---

> "La simplicidad es la máxima sofisticación." — Leonardo da Vinci
