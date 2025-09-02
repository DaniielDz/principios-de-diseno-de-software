# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo DIP en Go

Este ejemplo muestra cómo transformar un acoplamiento directo en un diseño basado en abstracciones.

---

## Antes (NO cumple DIP)
```go
package main

import "fmt"

type EmailService struct{}

func (e EmailService) SendEmail(message string) {
    fmt.Printf("Enviando email: %s\n", message)
}

type OrderService struct {
    emailService EmailService
}

func NewOrderService() OrderService {
    return OrderService{
        emailService: EmailService{},
    }
}

func (o OrderService) ProcessOrder() {
    // Lógica de negocio
    o.emailService.SendEmail("Pedido procesado")
}
```

**Problema:** `OrderService` (módulo de alto nivel) depende directamente de `EmailService` (módulo de bajo nivel), creando acoplamiento fuerte.

---

## Después (Cumple DIP)
```go
package main

import "fmt"

type NotificationService interface {
    Send(message string)
}

type EmailService struct{}

func (e EmailService) Send(message string) {
    fmt.Printf("Enviando email: %s\n", message)
}

type SMSService struct{}

func (s SMSService) Send(message string) {
    fmt.Printf("Enviando SMS: %s\n", message)
}

type OrderService struct {
    notificationService NotificationService
}

func NewOrderService(service NotificationService) OrderService {
    return OrderService{
        notificationService: service,
    }
}

func (o OrderService) ProcessOrder() {
    // Lógica de negocio
    o.notificationService.Send("Pedido procesado")
}
```

**Aplicación de DIP:**
`OrderService` ahora depende de la abstracción `NotificationService`, permitiendo intercambiar implementaciones sin modificar el código de alto nivel.

---

**Resumen visual:**
- Antes: Módulo de alto nivel acoplado directamente al de bajo nivel.
- Después: Ambos módulos dependen de una abstracción común.
