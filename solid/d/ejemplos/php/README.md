# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="32"/> Ejemplo DIP en PHP

Este ejemplo muestra cómo transformar un acoplamiento directo en un diseño basado en abstracciones.

---

## Antes (NO cumple DIP)
```php
<?php
class EmailService {
    public function sendEmail($message) {
        echo "Enviando email: $message\n";
    }
}

class OrderService {
    private $emailService;

    public function __construct() {
        $this->emailService = new EmailService();
    }

    public function processOrder() {
        // Lógica de negocio
        $this->emailService->sendEmail("Pedido procesado");
    }
}
?>
```

**Problema:** `OrderService` (módulo de alto nivel) depende directamente de `EmailService` (módulo de bajo nivel), creando acoplamiento fuerte.

---

## Después (Cumple DIP)
```php
<?php
interface NotificationService {
    public function send($message);
}

class EmailService implements NotificationService {
    public function send($message) {
        echo "Enviando email: $message\n";
    }
}

class SMSService implements NotificationService {
    public function send($message) {
        echo "Enviando SMS: $message\n";
    }
}

class OrderService {
    private $notificationService;

    public function __construct(NotificationService $notificationService) {
        $this->notificationService = $notificationService;
    }

    public function processOrder() {
        // Lógica de negocio
        $this->notificationService->send("Pedido procesado");
    }
}
?>
```

**Aplicación de DIP:**
`OrderService` ahora depende de la abstracción `NotificationService`, permitiendo intercambiar implementaciones sin modificar el código de alto nivel.

---

**Resumen visual:**
- Antes: Módulo de alto nivel acoplado directamente al de bajo nivel.
- Después: Ambos módulos dependen de una abstracción común.
