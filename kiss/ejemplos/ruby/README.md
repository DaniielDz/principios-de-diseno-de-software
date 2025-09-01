# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="32"/> Ejemplo KISS en Ruby

Este ejemplo muestra cómo aplicar el principio KISS para obtener los nombres de usuarios activos en un arreglo. Se compara una versión tradicional con una versión usando métodos de alto nivel.

---

## Antes (complejo)
```ruby
def get_active_user_names(users)
  names = []
  users.each do |u|
    names << u[:name] if u[:is_active]
  end
  names
end
```

## Problemas de la versión compleja
- Uso manual de bucles y lógica repetitiva.
- Menor legibilidad y mayor probabilidad de errores.
- Difícil de mantener y modificar.

---

## Después (KISS)
```ruby
def get_active_user_names(users)
  users.select { |u| u[:is_active] }.map { |u| u[:name] }
end
```

## Ventajas de la versión KISS
- Uso de métodos de alto nivel (`select`, `map`) para mayor claridad.
- El código se enfoca en la tarea principal.
- Más fácil de leer, mantener y modificar.

---

## ¿Cómo se aplica KISS aquí?
El principio KISS se aplica utilizando las herramientas del lenguaje para expresar la lógica de forma directa y eficiente, evitando la complejidad innecesaria.

---

> "La simplicidad es la máxima sofisticación." — Leonardo da Vinci
