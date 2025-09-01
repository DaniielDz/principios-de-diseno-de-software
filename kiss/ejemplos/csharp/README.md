# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo KISS en C#

Este ejemplo muestra cómo aplicar el principio KISS para obtener los nombres de usuarios activos en una lista. Se compara una versión tradicional con una versión usando LINQ.

---

## Antes (complejo)
```csharp
List<string> GetActiveUserNames(List<User> users)
{
    List<string> names = new List<string>();
    foreach (var u in users)
    {
        if (u.IsActive)
        {
            names.Add(u.Name);
        }
    }
    return names;
}
```

## Problemas de la versión compleja
- Uso manual de bucles y lógica repetitiva.
- Menor legibilidad y mayor probabilidad de errores.
- Difícil de mantener y modificar.

---

## Después (KISS)
```csharp
List<string> GetActiveUserNames(List<User> users)
{
    return users.Where(u => u.IsActive).Select(u => u.Name).ToList();
}
```

## Ventajas de la versión KISS
- Uso de LINQ para expresar la intención de forma clara y concisa.
- El código se enfoca en la tarea principal.
- Más fácil de leer, mantener y modificar.

---

## ¿Cómo se aplica KISS aquí?
El principio KISS se aplica utilizando las capacidades modernas del lenguaje para simplificar la lógica y mejorar la legibilidad, evitando la sobreingeniería.

---

> "La simplicidad es la máxima sofisticación." — Leonardo da Vinci
