# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo LSP en Ruby

Este ejemplo muestra cómo una subclase puede romper el contrato de la clase base y cómo corregirlo para cumplir LSP.

---

## Antes (NO cumple LSP)
```ruby
class Rectangle
  attr_accessor :width, :height
  def initialize(width, height)
    @width = width
    @height = height
  end
  def set_width(w)
    @width = w
  end
  def set_height(h)
    @height = h
  end
  def area
    @width * @height
  end
end

class Square < Rectangle
  def set_width(w)
    @width = w
    @height = w
  end
  def set_height(h)
    @width = h
    @height = h
  end
end
```

**Problema:** Square no respeta el contrato de Rectangle. El comportamiento esperado se rompe.

---

## Después (Cumple LSP)
```ruby
class Shape
  def area
    raise NotImplementedError
  end
end

class Rectangle < Shape
  def initialize(width, height)
    @width = width
    @height = height
  end
  def area
    @width * @height
  end
end

class Square < Shape
  def initialize(size)
    @size = size
  end
  def area
    @size * @size
  end
end
```

**Aplicación de LSP:**
Cada clase respeta su propio contrato y puede usarse sin romper expectativas.

---

**Resumen visual:**
- Antes: La subclase rompe el contrato de la base.
- Después: Cada clase respeta su contrato y puede sustituirse sin problemas.
