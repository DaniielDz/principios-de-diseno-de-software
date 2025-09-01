# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo KISS en Java

Este ejemplo muestra cómo aplicar el principio KISS para obtener los nombres de usuarios activos en una lista. Se compara una versión tradicional con una versión usando streams.

---

## Antes (complejo)
```java
public List<String> getActiveUserNames(List<User> users) {
    List<String> names = new ArrayList<>();
    for (User u : users) {
        if (u.isActive()) {
            names.add(u.getName());
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
```java
public List<String> getActiveUserNames(List<User> users) {
    return users.stream()
        .filter(User::isActive)
        .map(User::getName)
        .collect(Collectors.toList());
}
```

## Ventajas de la versión KISS
- Uso de streams para expresar la intención de forma clara y concisa.
- El código se enfoca en la tarea principal.
- Más fácil de leer, mantener y modificar.

---

## ¿Cómo se aplica KISS aquí?
El principio KISS se aplica utilizando las capacidades modernas del lenguaje para simplificar la lógica y mejorar la legibilidad, evitando la sobreingeniería.

---

> "La simplicidad es la máxima sofisticación." — Leonardo da Vinci
