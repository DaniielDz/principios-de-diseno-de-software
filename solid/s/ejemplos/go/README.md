# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo SRP en Go

Este ejemplo muestra cómo separar la lógica de cálculo y la lógica de almacenamiento en una estructura de pedido.

---

## Antes (NO cumple SRP)
```go
type Pedido struct {}

func CalcularTotal(productos []Producto) float64 {
    var total float64
    for _, p := range productos {
        total += p.Precio
    }
    return total
}

func GuardarEnBD(pedido Pedido) {
    // Lógica para guardar en base de datos
}
```

## Después (Cumple SRP)
```go
type Pedido struct {}

func CalcularTotal(productos []Producto) float64 {
    var total float64
    for _, p := range productos {
        total += p.Precio
    }
    return total
}

func GuardarEnBD(pedido Pedido) {
    // Lógica para guardar en base de datos
}
// Ahora cada función está en su propio paquete o módulo según la responsabilidad.
```

**Aplicación de SRP:**
Cada función o paquete tiene una única responsabilidad: cálculo o almacenamiento.
