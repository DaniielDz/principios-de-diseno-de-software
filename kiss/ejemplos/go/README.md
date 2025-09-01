# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="32"/> Ejemplo KISS en Go

Este ejemplo muestra cómo aplicar el principio KISS para obtener los nombres de usuarios activos en un slice. Go no tiene funciones de alto nivel como otros lenguajes, pero se puede simplificar la lógica y evitar pasos innecesarios.

---

## Antes (complejo)
```go
func GetActiveUserNames(users []User) []string {
    names := []string{}
    for _, u := range users {
        if u.IsActive {
            names = append(names, u.Name)
        }
    }
    return names
}
```

## Problemas de la versión compleja
- Uso manual de bucles y lógica repetitiva.
- Menor legibilidad y mayor probabilidad de errores.
- Difícil de mantener y modificar.

---

## Después (KISS)
```go
func GetActiveUserNames(users []User) []string {
    var names []string
    for _, u := range users {
        if u.IsActive {
            names = append(names, u.Name)
        }
    }
    return names
}
```

## Ventajas de la versión KISS
- El código se enfoca en la tarea principal y elimina pasos innecesarios.
- Más fácil de leer, mantener y modificar.

---

## ¿Cómo se aplica KISS aquí?
El principio KISS se aplica simplificando la lógica y evitando la sobreingeniería, incluso en lenguajes con menos herramientas de alto nivel.

---

> "La simplicidad es la máxima sofisticación." — Leonardo da Vinci
