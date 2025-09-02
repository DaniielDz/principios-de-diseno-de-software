# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo ISP en TypeScript

Este ejemplo muestra cómo pasar de una interfaz "gorda" a interfaces específicas y cohesivas.

---

## Antes (NO cumple ISP)
```typescript
interface Worker {
  work(): void;
  eat(): void;
  sleep(): void;
}

class Human implements Worker {
  work() { console.log("Trabajando..."); }
  eat() { console.log("Comiendo..."); }
  sleep() { console.log("Durmiendo..."); }
}

class Robot implements Worker {
  work() { console.log("Trabajando..."); }
  eat() { 
    throw new Error("Los robots no comen"); 
  }
  sleep() { 
    throw new Error("Los robots no duermen"); 
  }
}
```

**Problema:** La interfaz `Worker` fuerza a `Robot` a implementar métodos que no necesita (`eat` y `sleep`), violando ISP.

---

## Después (Cumple ISP)
```typescript
interface Workable {
  work(): void;
}

interface Eatable {
  eat(): void;
}

interface Sleepable {
  sleep(): void;
}

class Human implements Workable, Eatable, Sleepable {
  work() { console.log("Trabajando..."); }
  eat() { console.log("Comiendo..."); }
  sleep() { console.log("Durmiendo..."); }
}

class Robot implements Workable {
  work() { console.log("Trabajando..."); }
}
```

**Aplicación de ISP:**
Cada interfaz tiene una responsabilidad específica. Los clientes solo dependen de las interfaces que realmente necesitan.

---

**Resumen visual:**
- Antes: Una interfaz "gorda" que fuerza implementaciones innecesarias.
- Después: Interfaces específicas que solo exponen lo que cada cliente necesita.
