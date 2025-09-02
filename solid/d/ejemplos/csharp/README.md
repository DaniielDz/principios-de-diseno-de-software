# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo DIP en C#

Este ejemplo muestra cómo transformar un acoplamiento directo en un diseño basado en abstracciones.

---

## Antes (NO cumple DIP)
```csharp
public class EmailService
{
    public void SendEmail(string message)
    {
        Console.WriteLine($"Enviando email: {message}");
    }
}

public class OrderService
{
    private EmailService emailService;

    public OrderService()
    {
        this.emailService = new EmailService();
    }

    public void ProcessOrder()
    {
        // Lógica de negocio
        emailService.SendEmail("Pedido procesado");
    }
}
```

**Problema:** `OrderService` (módulo de alto nivel) depende directamente de `EmailService` (módulo de bajo nivel), creando acoplamiento fuerte.

---

## Después (Cumple DIP)
```csharp
public interface INotificationService
{
    void Send(string message);
}

public class EmailService : INotificationService
{
    public void Send(string message)
    {
        Console.WriteLine($"Enviando email: {message}");
    }
}

public class SMSService : INotificationService
{
    public void Send(string message)
    {
        Console.WriteLine($"Enviando SMS: {message}");
    }
}

public class OrderService
{
    private readonly INotificationService notificationService;

    public OrderService(INotificationService notificationService)
    {
        this.notificationService = notificationService;
    }

    public void ProcessOrder()
    {
        // Lógica de negocio
        notificationService.Send("Pedido procesado");
    }
}
```

**Aplicación de DIP:**
`OrderService` ahora depende de la abstracción `INotificationService`, permitiendo intercambiar implementaciones sin modificar el código de alto nivel.

---

**Resumen visual:**
- Antes: Módulo de alto nivel acoplado directamente al de bajo nivel.
- Después: Ambos módulos dependen de una abstracción común.
