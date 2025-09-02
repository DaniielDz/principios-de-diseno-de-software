# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo DRY en Ruby

Este ejemplo muestra cómo evitar duplicación de lógica en la generación de mensajes de bienvenida para usuarios y administradores.

---

## Antes (NO cumple DRY)
```ruby
def welcome_user(name)
  "Bienvenido, #{name}!"
end

def welcome_admin(name)
  "Bienvenido, #{name}!"
end
```

## Después (Cumple DRY)
```ruby
def welcome(name)
  "Bienvenido, #{name}!"
end

# Uso
welcome('Daniel')
welcome('María')
```

**Aplicación de DRY:**
La lógica de generación de mensajes está centralizada en un solo método reutilizable, evitando duplicación y facilitando el mantenimiento.

---

> "La duplicación es el enemigo. Eliminarla es el primer paso hacia un buen diseño." — Robert C. Martin
