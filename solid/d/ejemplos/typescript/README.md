# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo DIP en TypeScript

Este ejemplo muestra cómo pasar de un acoplamiento directo a un diseño basado en abstracciones.

---

## Antes (NO cumple DIP)
```typescript
class EmailService {
  sendEmail(message: string) {
    console.log(`Enviando email: ${message}`);
  }
}

class OrderService {
  private emailService: EmailService;

  constructor() {
    this.emailService = new EmailService();
  }

  processOrder() {
    // Lógica de negocio
    this.emailService.sendEmail("Pedido procesado");
  }
}
```

**Problema:** `OrderService` (módulo de alto nivel) depende directamente de `EmailService` (módulo de bajo nivel), creando acoplamiento fuerte.

---

## Después (Cumple DIP)
```typescript
interface NotificationService {
  send(message: string): void;
}

class EmailService implements NotificationService {
  send(message: string) {
    console.log(`Enviando email: ${message}`);
  }
}

class SMSService implements NotificationService {
  send(message: string) {
    console.log(`Enviando SMS: ${message}`);
  }
}

class OrderService {
  private notificationService: NotificationService;

  constructor(notificationService: NotificationService) {
    this.notificationService = notificationService;
  }

  processOrder() {
    // Lógica de negocio
    this.notificationService.send("Pedido procesado");
  }
}
```

**Aplicación de DIP:**
`OrderService` ahora depende de la abstracción `NotificationService`, permitiendo intercambiar implementaciones sin modificar el código de alto nivel.

---

**Resumen visual:**
- Antes: Módulo de alto nivel acoplado directamente al de bajo nivel.
- Después: Ambos módulos dependen de una abstracción común.
