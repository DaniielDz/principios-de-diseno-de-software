# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo SRP en Ruby

Este ejemplo muestra cómo separar la lógica de cálculo y la lógica de impresión en una clase de factura.

---

## Antes (NO cumple SRP)
```ruby
class Factura
  def calcular_total(productos)
    productos.map { |p| p[:precio] }.sum
  end
  def imprimir_factura
    # Lógica para imprimir la factura
  end
end
```

## Después (Cumple SRP)
```ruby
class Factura
  def calcular_total(productos)
    productos.map { |p| p[:precio] }.sum
  end
end

class FacturaPrinter
  def imprimir_factura(factura)
    # Lógica para imprimir la factura
  end
end
```

**Aplicación de SRP:**
Cada clase tiene una única responsabilidad: `Factura` calcula el total y `FacturaPrinter` se encarga de la impresión.
