# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo ISP en Java

Este ejemplo muestra cómo transformar una interfaz "gorda" en interfaces específicas y cohesivas.

---

## Antes (NO cumple ISP)
```java
public interface Worker {
    void work();
    void eat();
    void sleep();
}

public class Human implements Worker {
    public void work() { System.out.println("Trabajando..."); }
    public void eat() { System.out.println("Comiendo..."); }
    public void sleep() { System.out.println("Durmiendo..."); }
}

public class Robot implements Worker {
    public void work() { System.out.println("Trabajando..."); }
    public void eat() { 
        throw new UnsupportedOperationException("Los robots no comen"); 
    }
    public void sleep() { 
        throw new UnsupportedOperationException("Los robots no duermen"); 
    }
}
```

**Problema:** La interfaz `Worker` fuerza a `Robot` a implementar métodos que no necesita (`eat` y `sleep`), violando ISP.

---

## Después (Cumple ISP)
```java
public interface Workable {
    void work();
}

public interface Eatable {
    void eat();
}

public interface Sleepable {
    void sleep();
}

public class Human implements Workable, Eatable, Sleepable {
    public void work() { System.out.println("Trabajando..."); }
    public void eat() { System.out.println("Comiendo..."); }
    public void sleep() { System.out.println("Durmiendo..."); }
}

public class Robot implements Workable {
    public void work() { System.out.println("Trabajando..."); }
}
```

**Aplicación de ISP:**
Cada interfaz tiene una responsabilidad específica. Los clientes solo dependen de las interfaces que realmente necesitan.

---

**Resumen visual:**
- Antes: Una interfaz "gorda" que fuerza implementaciones innecesarias.
- Después: Interfaces específicas que solo exponen lo que cada cliente necesita.
