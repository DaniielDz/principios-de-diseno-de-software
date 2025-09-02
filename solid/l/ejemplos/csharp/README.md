# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="32"/> Ejemplo LSP en C#

Este ejemplo muestra cómo una subclase puede romper el contrato de la clase base y cómo corregirlo para cumplir LSP.

---

## Antes (NO cumple LSP)
```csharp
public class Rectangle {
    public int Width { get; set; }
    public int Height { get; set; }
    public int GetArea() => Width * Height;
}

public class Square : Rectangle {
    public new int Width {
        set { base.Width = value; base.Height = value; }
    }
    public new int Height {
        set { base.Width = value; base.Height = value; }
    }
}
```

**Problema:** Square no respeta el contrato de Rectangle. El comportamiento esperado se rompe.

---

## Después (Cumple LSP)
```csharp
public abstract class Shape {
    public abstract int GetArea();
}

public class Rectangle : Shape {
    public int Width { get; set; }
    public int Height { get; set; }
    public override int GetArea() => Width * Height;
}

public class Square : Shape {
    public int Size { get; set; }
    public override int GetArea() => Size * Size;
}
```

**Aplicación de LSP:**
Cada clase respeta su propio contrato y puede usarse sin romper expectativas.

---

**Resumen visual:**
- Antes: La subclase rompe el contrato de la base.
- Después: Cada clase respeta su contrato y puede sustituirse sin problemas.
