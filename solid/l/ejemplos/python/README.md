# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo LSP en Python

Este ejemplo muestra cómo una subclase puede romper el contrato de la clase base y cómo corregirlo para cumplir LSP.

---

## Antes (NO cumple LSP)
```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
    def set_width(self, w):
        self.width = w
    def set_height(self, h):
        self.height = h
    def get_area(self):
        return self.width * self.height

class Square(Rectangle):
    def set_width(self, w):
        self.width = w
        self.height = w
    def set_height(self, h):
        self.width = h
        self.height = h
```

**Problema:** Square no respeta el contrato de Rectangle. El comportamiento esperado se rompe.

---

## Después (Cumple LSP)
```python
class Shape:
    def get_area(self):
        raise NotImplementedError

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    def get_area(self):
        return self.width * self.height

class Square(Shape):
    def __init__(self, size):
        self.size = size
    def get_area(self):
        return self.size * self.size
```

**Aplicación de LSP:**
Cada clase respeta su propio contrato y puede usarse sin romper expectativas.

---

**Resumen visual:**
- Antes: La subclase rompe el contrato de la base.
- Después: Cada clase respeta su contrato y puede sustituirse sin problemas.
