# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo DIP en Python

Este ejemplo muestra cómo transformar un acoplamiento directo en un diseño basado en abstracciones.

---

## Antes (NO cumple DIP)
```python
class EmailService:
    def send_email(self, message):
        print(f"Enviando email: {message}")

class OrderService:
    def __init__(self):
        self.email_service = EmailService()

    def process_order(self):
        # Lógica de negocio
        self.email_service.send_email("Pedido procesado")
```

**Problema:** `OrderService` (módulo de alto nivel) depende directamente de `EmailService` (módulo de bajo nivel), creando acoplamiento fuerte.

---

## Después (Cumple DIP)
```python
from abc import ABC, abstractmethod

class NotificationService(ABC):
    @abstractmethod
    def send(self, message):
        pass

class EmailService(NotificationService):
    def send(self, message):
        print(f"Enviando email: {message}")

class SMSService(NotificationService):
    def send(self, message):
        print(f"Enviando SMS: {message}")

class OrderService:
    def __init__(self, notification_service):
        self.notification_service = notification_service

    def process_order(self):
        # Lógica de negocio
        self.notification_service.send("Pedido procesado")
```

**Aplicación de DIP:**
`OrderService` ahora depende de la abstracción `NotificationService`, permitiendo intercambiar implementaciones sin modificar el código de alto nivel.

---

**Resumen visual:**
- Antes: Módulo de alto nivel acoplado directamente al de bajo nivel.
- Después: Ambos módulos dependen de una abstracción común.
