# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo DIP en Ruby

Este ejemplo muestra cómo transformar un acoplamiento directo en un diseño basado en abstracciones.

---

## Antes (NO cumple DIP)
```ruby
class EmailService
  def send_email(message)
    puts "Enviando email: #{message}"
  end
end

class OrderService
  def initialize
    @email_service = EmailService.new
  end

  def process_order
    # Lógica de negocio
    @email_service.send_email("Pedido procesado")
  end
end
```

**Problema:** `OrderService` (módulo de alto nivel) depende directamente de `EmailService` (módulo de bajo nivel), creando acoplamiento fuerte.

---

## Después (Cumple DIP)
```ruby
module NotificationService
  def send(message)
    raise NotImplementedError
  end
end

class EmailService
  include NotificationService
  
  def send(message)
    puts "Enviando email: #{message}"
  end
end

class SMSService
  include NotificationService
  
  def send(message)
    puts "Enviando SMS: #{message}"
  end
end

class OrderService
  def initialize(notification_service)
    @notification_service = notification_service
  end

  def process_order
    # Lógica de negocio
    @notification_service.send("Pedido procesado")
  end
end
```

**Aplicación de DIP:**
`OrderService` ahora depende de la abstracción `NotificationService`, permitiendo intercambiar implementaciones sin modificar el código de alto nivel.

---

**Resumen visual:**
- Antes: Módulo de alto nivel acoplado directamente al de bajo nivel.
- Después: Ambos módulos dependen de una abstracción común.
