# Principio DRY

El principio **DRY** significa "Don't Repeat Yourself" (No te repitas), y se refiere a la idea de que cada pieza de conocimiento o lógica debe existir en un solo lugar en el código. Si algo se repite en varios lugares, se vuelve difícil de mantener y propenso a errores.

La clave es identificar patrones repetidos y abstraerlos en funciones, componentes, clases o módulos reutilizables.

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

## ¿Por qué es importante el principio DRY?

- **Reduce errores:** Si tienes la misma lógica en varios lugares, cambiarla en uno pero olvidar otro puede generar bugs.
- **Facilita el mantenimiento:** Actualizar código repetido en un solo lugar es mucho más fácil y rápido.
- **Mejora la legibilidad:** Código más corto y modular es más fácil de entender.
- **Promueve la reutilización:** Funciones y componentes reutilizables hacen que el proyecto crezca de manera más ordenada.

---

## ¿Cómo aplicar el principio DRY?

- **Identifica duplicaciones:** Revisa tu código y busca bloques repetidos, patrones similares o cálculos que se repiten.
- **Abstrae la lógica:** Convierte los bloques repetidos en funciones, hooks, componentes o utilidades.
- **Usa componentes y módulos reutilizables:** En React, crea componentes o hooks que puedan usarse en varios lugares sin duplicar código.
- **Evita duplicar datos o configuraciones:** Mantén valores compartidos en constantes, archivos de configuración o contextos.

---

## Ejemplo en TypeScript + React

### Antes: lógica duplicada
```typescript
function WelcomeUser1() {
  const name = "Daniel";
  return <p>Hola, {name}!</p>;
}
function WelcomeUser2() {
  const name = "María";
  return <p>Hola, {name}!</p>;
}
```

### Después: aplicando DRY
```typescript
interface WelcomeProps {
  name: string;
}

function Welcome({ name }: WelcomeProps) {
  return <p>Hola, {name}!</p>;
}

// Uso
function App() {
  return (
    <>
      <Welcome name="Daniel" />
      <Welcome name="María" />
    </>
  );
}
```

> Observa que ahora solo tenemos un componente para mostrar un saludo, y podemos reutilizarlo para cualquier nombre sin repetir código.

---

## Bibliografía recomendada

- Robert C. Martin – “Clean Code” (capítulo sobre duplicación)
- Steve McConnell – “Code Complete”
- Martin Fowler – “Refactoring”
- Documentación y guías de React y TypeScript sobre componentes reutilizables y hooks

---

💡 **Consejo extra:**
DRY no significa eliminar todo tipo de repetición trivial; a veces, una pequeña duplicación consciente es mejor que una abstracción forzada que complique el código.
