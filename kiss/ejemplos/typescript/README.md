# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo KISS en TypeScript

Este ejemplo muestra cómo aplicar el principio KISS para obtener los nombres de usuarios activos desde una API. Se compara una versión compleja con una versión simple y clara.

---

## Antes (complejo)
```typescript
function getActiveUserNames() {
  fetch('https://api.example.com/users')
    .then(res => res.json())
    .then(data => {
      let names = [];
      for (let i = 0; i < data.length; i++) {
        if (data[i].isActive) {
          names.push(data[i].name);
        }
      }
      console.log(names);
    });
}
```

## Problemas de la versión compleja
- Uso innecesario de bucles y lógica manual.
- Menor legibilidad y mayor probabilidad de errores.
- Difícil de mantener y modificar.

---

## Después (KISS)
```typescript
async function getActiveUserNames() {
  const res = await fetch('https://api.example.com/users');
  const users = await res.json();
  const names = users.filter(u => u.isActive).map(u => u.name);
  console.log(names);
}
```

## Ventajas de la versión KISS
- Uso de funciones de alto nivel (`filter`, `map`) y async/await para mayor claridad.
- El código se enfoca en la tarea principal.
- Más fácil de leer, mantener y modificar.

---

## ¿Cómo se aplica KISS aquí?
El principio KISS se aplica eliminando la complejidad innecesaria y utilizando las herramientas del lenguaje para expresar la intención de forma directa. El resultado es un código más limpio, eficiente y fácil de entender.

---

> "La simplicidad es la máxima sofisticación." — Leonardo da Vinci
