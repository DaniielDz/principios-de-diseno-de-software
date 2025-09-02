# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo ISP en C#

Este ejemplo muestra cómo transformar una interfaz "gorda" en interfaces específicas y cohesivas.

---

## Antes (NO cumple ISP)
```csharp
public interface IWorker
{
    void Work();
    void Eat();
    void Sleep();
}

public class Human : IWorker
{
    public void Work() => Console.WriteLine("Trabajando...");
    public void Eat() => Console.WriteLine("Comiendo...");
    public void Sleep() => Console.WriteLine("Durmiendo...");
}

public class Robot : IWorker
{
    public void Work() => Console.WriteLine("Trabajando...");
    public void Eat() => throw new NotImplementedException("Los robots no comen");
    public void Sleep() => throw new NotImplementedException("Los robots no duermen");
}
```

**Problema:** La interfaz `IWorker` fuerza a `Robot` a implementar métodos que no necesita (`Eat` y `Sleep`), violando ISP.

---

## Después (Cumple ISP)
```csharp
public interface IWorkable
{
    void Work();
}

public interface IEatable
{
    void Eat();
}

public interface ISleepable
{
    void Sleep();
}

public class Human : IWorkable, IEatable, ISleepable
{
    public void Work() => Console.WriteLine("Trabajando...");
    public void Eat() => Console.WriteLine("Comiendo...");
    public void Sleep() => Console.WriteLine("Durmiendo...");
}

public class Robot : IWorkable
{
    public void Work() => Console.WriteLine("Trabajando...");
}
```

**Aplicación de ISP:**
Cada interfaz tiene una responsabilidad específica. Los clientes solo dependen de las interfaces que realmente necesitan.

---

**Resumen visual:**
- Antes: Una interfaz "gorda" que fuerza implementaciones innecesarias.
- Después: Interfaces específicas que solo exponen lo que cada cliente necesita.
