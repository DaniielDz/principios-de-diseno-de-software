# Principio KISS

El principio **KISS** en programación significa "Keep It Simple, Stupid" (Mantenlo Simple, Estúpido). Se refiere a la idea de que los sistemas y el código deben diseñarse de la forma más simple posible, evitando la complejidad innecesaria para que sean más fáciles de entender, mantener y depurar. La clave es enfocar el código en la tarea que debe realizar, descomponiendo problemas complejos en partes más pequeñas y manejables.

---

## Índice de Ejemplos por Lenguaje

- [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="24"/> TypeScript](./ejemplos/typescript/README.md)
- [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="24"/> Java](./ejemplos/java/README.md)
- [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="24"/> Python](./ejemplos/python/README.md)
- [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="24"/> C#](./ejemplos/csharp/README.md)
- [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="24"/> PHP](./ejemplos/php/README.md)
- [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="24"/> Ruby](./ejemplos/ruby/README.md)
- [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="24"/> Go](./ejemplos/go/README.md)

---

## ¿Por qué es importante el principio KISS?

- **Facilita el mantenimiento:** El código simple es más fácil de entender y modificar con el tiempo.
- **Reduce errores:** La complejidad tiende a generar más bugs, por lo que la simplicidad ayuda a evitarlos.
- **Mejora la colaboración:** Un código claro es más fácil de comprender para otros desarrolladores, mejorando el trabajo en equipo.
- **Optimiza el rendimiento:** Un código más sencillo puede ser más eficiente para la computadora, lo que mejora el rendimiento del software.

---

## ¿Cómo aplicar el principio KISS?

- **Desglosa los problemas:** Divide problemas grandes en tareas más pequeñas y maneja cada una por separado en funciones o módulos distintos.
- **Evita la sobreingeniería:** No añadas funcionalidades ni complejidad que no sean estrictamente necesarias para resolver el problema.
- **Crea código claro y directo:** Escribe el código de la forma más sencilla posible, incluso al nombrar variables y funciones.
- **Enfócate en la tarea:** Mantén las funciones y los módulos enfocados en una única responsabilidad para que sean más manejables.

---

## Ejemplo en TypeScript + React

### Antes: demasiado complejo
```typescript
function fetchAndProcessData() {
  fetch('https://api.example.com/users')
    .then(res => res.json())
    .then(data => {
      const activeUsers = data.filter(u => u.isActive);
      console.log(activeUsers.map(u => u.name));
    });
}
```

### Después: simple y claro (KISS)
```typescript
async function fetchActiveUsers() {
  const res = await fetch('https://api.example.com/users');
  const users = await res.json();
  return users.filter(u => u.isActive);
}
```

#### Uso en un componente React
```typescript
import { useEffect, useState } from 'react';

function UserList() {
  const [users, setUsers] = useState<string[]>([]);

  useEffect(() => {
    fetchActiveUsers().then(active => setUsers(active.map(u => u.name)));
  }, []);

  return (
    <ul>
      {users.map(name => <li key={name}>{name}</li>)}
    </ul>
  );
}
```

> Observa cómo en la versión KISS la función hace solo lo necesario, y el componente React está limpio y fácil de entender.

---

## Recursos recomendados

- [Principio KISS (wikipedia)](https://es.wikipedia.org/wiki/Principio_KISS)
- [El Principio KISS: mantenlo simple, estúpido](https://codeyourapps.com/el-principio-kiss-mantenlo-simple-estupido/)
- [¿Qué es el principio KISS? (con ejemplos)](https://www.quelinka.com/blog/post/principio-kiss-ejemplos)
- [KISS Principle in Software Development](https://www.geeksforgeeks.org/software-engineering/kiss-principle-in-software-development/)

---

💡 **Consejo extra:**
KISS no significa “hacer código tonto”, sino evitar complicar las cosas sin necesidad. Siempre pregúntate: “¿Esta línea o función realmente aporta valor, o la estoy haciendo más compleja de lo necesario?”
