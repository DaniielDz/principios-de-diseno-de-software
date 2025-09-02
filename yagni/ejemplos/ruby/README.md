# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo YAGNI en Ruby

Este ejemplo muestra cómo evitar agregar lógica de envío internacional si solo se requiere envío nacional.

---

## Antes (NO cumple YAGNI)
```ruby
def calcular_envio(pais)
  if pais == 'México'
    100
  elsif pais == 'EEUU'
    200
  elsif pais == 'España'
    250
  else
    300
  end
end
```

## Después (Cumple YAGNI)
```ruby
def calcular_envio
  100
end
```

**Aplicación de YAGNI:**
Solo se implementa el cálculo de envío nacional, que es lo que se requiere actualmente. Si en el futuro se necesita envío internacional, se agrega en ese momento.

---

> "No lo vas a necesitar" — Kent Beck
