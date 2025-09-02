# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo DRY en Go

Este ejemplo muestra cómo evitar duplicación de lógica en el cálculo de área para diferentes figuras.

---

## Antes (NO cumple DRY)
```go
func AreaRectangulo(base, altura float64) float64 {
    return base * altura
}

func AreaCuadrado(lado float64) float64 {
    return lado * lado
}
```

## Después (Cumple DRY)
```go
func Area(base, altura float64) float64 {
    return base * altura
}

// Uso
Area(10, 5) // rectángulo
Area(4, 4)  // cuadrado
```

**Aplicación de DRY:**
La lógica de cálculo de área está centralizada en una sola función reutilizable, evitando duplicación y facilitando el mantenimiento.

---

> "La duplicación es el enemigo. Eliminarla es el primer paso hacia un buen diseño." — Robert C. Martin
