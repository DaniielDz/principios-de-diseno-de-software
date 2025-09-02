# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo ISP en Ruby

Este ejemplo muestra cómo transformar una interfaz "gorda" en interfaces específicas y cohesivas.

---

## Antes (NO cumple ISP)
```ruby
module Worker
  def work
    raise NotImplementedError
  end
  
  def eat
    raise NotImplementedError
  end
  
  def sleep
    raise NotImplementedError
  end
end

class Human
  include Worker
  
  def work
    puts "Trabajando..."
  end
  
  def eat
    puts "Comiendo..."
  end
  
  def sleep
    puts "Durmiendo..."
  end
end

class Robot
  include Worker
  
  def work
    puts "Trabajando..."
  end
  
  def eat
    raise "Los robots no comen"
  end
  
  def sleep
    raise "Los robots no duermen"
  end
end
```

**Problema:** El módulo `Worker` fuerza a `Robot` a implementar métodos que no necesita (`eat` y `sleep`), violando ISP.

---

## Después (Cumple ISP)
```ruby
module Workable
  def work
    raise NotImplementedError
  end
end

module Eatable
  def eat
    raise NotImplementedError
  end
end

module Sleepable
  def sleep
    raise NotImplementedError
  end
end

class Human
  include Workable, Eatable, Sleepable
  
  def work
    puts "Trabajando..."
  end
  
  def eat
    puts "Comiendo..."
  end
  
  def sleep
    puts "Durmiendo..."
  end
end

class Robot
  include Workable
  
  def work
    puts "Trabajando..."
  end
end
```

**Aplicación de ISP:**
Cada módulo tiene una responsabilidad específica. Los clientes solo dependen de los módulos que realmente necesitan.

---

**Resumen visual:**
- Antes: Un módulo "gordo" que fuerza implementaciones innecesarias.
- Después: Módulos específicos que solo exponen lo que cada cliente necesita.
