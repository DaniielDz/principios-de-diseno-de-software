# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo LSP en Java

Este ejemplo muestra cómo una subclase puede romper el contrato de la clase base y cómo corregirlo para cumplir LSP.

---

## Antes (NO cumple LSP)
```java
public class Rectangle {
    protected int width, height;
    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }
    public void setWidth(int w) { this.width = w; }
    public void setHeight(int h) { this.height = h; }
    public int getArea() { return width * height; }
}

public class Square extends Rectangle {
    public Square(int size) { super(size, size); }
    @Override
    public void setWidth(int w) { this.width = w; this.height = w; }
    @Override
    public void setHeight(int h) { this.width = h; this.height = h; }
}
```

**Problema:** Square no respeta el contrato de Rectangle. El comportamiento esperado se rompe.

---

## Después (Cumple LSP)
```java
public abstract class Shape {
    public abstract int getArea();
}

public class Rectangle extends Shape {
    private int width, height;
    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }
    public int getArea() { return width * height; }
}

public class Square extends Shape {
    private int size;
    public Square(int size) { this.size = size; }
    public int getArea() { return size * size; }
}
```

**Aplicación de LSP:**
Cada clase respeta su propio contrato y puede usarse sin romper expectativas.

---

**Resumen visual:**
- Antes: La subclase rompe el contrato de la base.
- Después: Cada clase respeta su contrato y puede sustituirse sin problemas.
