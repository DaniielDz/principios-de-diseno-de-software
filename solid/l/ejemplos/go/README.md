# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo LSP en Go

Este ejemplo muestra cómo una subestructura puede romper el contrato de la base y cómo corregirlo para cumplir LSP.

---

## Antes (NO cumple LSP)
```go
package main

type Rectangle struct {
    Width, Height int
}

func (r *Rectangle) SetWidth(w int)  { r.Width = w }
func (r *Rectangle) SetHeight(h int) { r.Height = h }
func (r *Rectangle) Area() int       { return r.Width * r.Height }

type Square struct {
    Rectangle
}

func (s *Square) SetWidth(w int) {
    s.Width = w
    s.Height = w
}
func (s *Square) SetHeight(h int) {
    s.Width = h
    s.Height = h
}
```

**Problema:** Square no respeta el contrato de Rectangle. El comportamiento esperado se rompe.

---

## Después (Cumple LSP)
```go
package main

type Shape interface {
    Area() int
}

type Rectangle struct {
    Width, Height int
}
func (r Rectangle) Area() int { return r.Width * r.Height }

type Square struct {
    Size int
}
func (s Square) Area() int { return s.Size * s.Size }
```

**Aplicación de LSP:**
Cada tipo respeta su propio contrato y puede usarse sin romper expectativas.

---

**Resumen visual:**
- Antes: La subestructura rompe el contrato de la base.
- Después: Cada tipo respeta su contrato y puede sustituirse sin problemas.
