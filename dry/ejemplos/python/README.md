# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo DRY en Python

Este ejemplo muestra cómo evitar duplicación de lógica en el cálculo de comisiones para ventas y servicios.

---

## Antes (NO cumple DRY)
```python
def calcular_comision_venta(monto, porcentaje):
    comision = monto * porcentaje
    return comision

def calcular_comision_servicio(monto, porcentaje):
    comision = monto * porcentaje
    return comision
```

## Después (Cumple DRY)
```python
def calcular_comision(monto, porcentaje):
    return monto * porcentaje

# Uso
calcular_comision(500, 0.05)
calcular_comision(800, 0.08)
```

**Aplicación de DRY:**
La lógica de cálculo de comisión está centralizada en una sola función reutilizable, evitando duplicación y facilitando el mantenimiento.

---

> "La duplicación es el enemigo. Eliminarla es el primer paso hacia un buen diseño." — Robert C. Martin
