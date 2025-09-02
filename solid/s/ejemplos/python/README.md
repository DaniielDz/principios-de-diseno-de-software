# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo SRP en Python

Este ejemplo muestra cómo separar la lógica de cálculo y la lógica de envío de correos en una clase de pedido.

---

## Antes (NO cumple SRP)
```python
class Pedido:
    def calcular_total(self, productos):
        return sum(p['precio'] for p in productos)
    def enviar_confirmacion(self, email):
        # Lógica para enviar correo
        pass
```

## Después (Cumple SRP)
```python
class Pedido:
    def calcular_total(self, productos):
        return sum(p['precio'] for p in productos)

class EmailService:
    def enviar_confirmacion(self, email):
        # Lógica para enviar correo
        pass
```

**Aplicación de SRP:**
Cada clase tiene una única responsabilidad: `Pedido` calcula el total y `EmailService` se encarga del envío de correos.
