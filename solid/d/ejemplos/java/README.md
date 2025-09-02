# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo DIP en Java

Este ejemplo muestra cómo transformar un acoplamiento directo en un diseño basado en abstracciones.

---

## Antes (NO cumple DIP)
```java
public class EmailService {
    public void sendEmail(String message) {
        System.out.println("Enviando email: " + message);
    }
}

public class OrderService {
    private EmailService emailService;

    public OrderService() {
        this.emailService = new EmailService();
    }

    public void processOrder() {
        // Lógica de negocio
        emailService.sendEmail("Pedido procesado");
    }
}
```

**Problema:** `OrderService` (módulo de alto nivel) depende directamente de `EmailService` (módulo de bajo nivel), creando acoplamiento fuerte.

---

## Después (Cumple DIP)
```java
public interface NotificationService {
    void send(String message);
}

public class EmailService implements NotificationService {
    public void send(String message) {
        System.out.println("Enviando email: " + message);
    }
}

public class SMSService implements NotificationService {
    public void send(String message) {
        System.out.println("Enviando SMS: " + message);
    }
}

public class OrderService {
    private NotificationService notificationService;

    public OrderService(NotificationService notificationService) {
        this.notificationService = notificationService;
    }

    public void processOrder() {
        // Lógica de negocio
        notificationService.send("Pedido procesado");
    }
}
```

**Aplicación de DIP:**
`OrderService` ahora depende de la abstracción `NotificationService`, permitiendo intercambiar implementaciones sin modificar el código de alto nivel.

---

**Resumen visual:**
- Antes: Módulo de alto nivel acoplado directamente al de bajo nivel.
- Después: Ambos módulos dependen de una abstracción común.
