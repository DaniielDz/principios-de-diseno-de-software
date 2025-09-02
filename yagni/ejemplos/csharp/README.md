# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo YAGNI en C#

Este ejemplo muestra cómo evitar crear interfaces y clases abstractas cuando solo hay una implementación concreta.

---

## Antes (NO cumple YAGNI)
```csharp
public interface INotificador {
    void Notificar(string mensaje);
}

public class EmailNotificador : INotificador {
    public void Notificar(string mensaje) {
        // Enviar email
    }
}
```

## Después (Cumple YAGNI)
```csharp
public class Notificador {
    public void Notificar(string mensaje) {
        // Enviar email
    }
}
```

**Aplicación de YAGNI:**
Solo se implementa la clase concreta necesaria. Si en el futuro se requieren más tipos de notificación, se puede agregar una interfaz o clase abstracta en ese momento.

---

> "No lo vas a necesitar" — Kent Beck
