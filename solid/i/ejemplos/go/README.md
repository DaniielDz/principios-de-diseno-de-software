# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo ISP en Go

Este ejemplo muestra cómo transformar una interfaz "gorda" en interfaces específicas y cohesivas.

---

## Antes (NO cumple ISP)
```go
package main

import "fmt"

type Worker interface {
    Work()
    Eat()
    Sleep()
}

type Human struct{}

func (h Human) Work() { fmt.Println("Trabajando...") }
func (h Human) Eat() { fmt.Println("Comiendo...") }
func (h Human) Sleep() { fmt.Println("Durmiendo...") }

type Robot struct{}

func (r Robot) Work() { fmt.Println("Trabajando...") }
func (r Robot) Eat() { panic("Los robots no comen") }
func (r Robot) Sleep() { panic("Los robots no duermen") }
```

**Problema:** La interfaz `Worker` fuerza a `Robot` a implementar métodos que no necesita (`Eat` y `Sleep`), violando ISP.

---

## Después (Cumple ISP)
```go
package main

import "fmt"

type Workable interface {
    Work()
}

type Eatable interface {
    Eat()
}

type Sleepable interface {
    Sleep()
}

type Human struct{}

func (h Human) Work() { fmt.Println("Trabajando...") }
func (h Human) Eat() { fmt.Println("Comiendo...") }
func (h Human) Sleep() { fmt.Println("Durmiendo...") }

type Robot struct{}

func (r Robot) Work() { fmt.Println("Trabajando...") }
```

**Aplicación de ISP:**
Cada interfaz tiene una responsabilidad específica. Los clientes solo dependen de las interfaces que realmente necesitan.

---

**Resumen visual:**
- Antes: Una interfaz "gorda" que fuerza implementaciones innecesarias.
- Después: Interfaces específicas que solo exponen lo que cada cliente necesita.
