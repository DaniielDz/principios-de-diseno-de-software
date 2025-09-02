# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo YAGNI en Go

Este ejemplo muestra cómo evitar agregar lógica de logging avanzado si solo se requiere imprimir mensajes simples.

---

## Antes (NO cumple YAGNI)
```go
func Log(mensaje string, nivel string) {
    if nivel == "info" {
        // Lógica para info
    } else if nivel == "error" {
        // Lógica para error
    } else if nivel == "debug" {
        // Lógica para debug
    }
    // ...
    fmt.Println(mensaje)
}
```

## Después (Cumple YAGNI)
```go
func Log(mensaje string) {
    fmt.Println(mensaje)
}
```

**Aplicación de YAGNI:**
Solo se implementa la impresión simple de mensajes, que es lo que se requiere actualmente. Si en el futuro se necesita logging avanzado, se agrega en ese momento.

---

> "No lo vas a necesitar" — Kent Beck
