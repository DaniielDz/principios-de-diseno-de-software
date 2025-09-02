# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="32"/> Ejemplo LSP en TypeScript

Este ejemplo muestra cómo una subclase puede romper el contrato de la clase base y cómo corregirlo para cumplir LSP.

---

## Antes (NO cumple LSP)
```typescript
class Rectangle {
  constructor(public width: number, public height: number) {}
  setWidth(w: number) { this.width = w; }
  setHeight(h: number) { this.height = h; }
  getArea() { return this.width * this.height; }
}

class Square extends Rectangle {
  setWidth(w: number) {
    this.width = w;
    this.height = w;
  }
  setHeight(h: number) {
    this.width = h;
    this.height = h;
  }
}
```

**Problema:** Square no respeta el contrato de Rectangle. El comportamiento esperado se rompe.

---

## Después (Cumple LSP)
```typescript
class Shape {
  getArea(): number { throw new Error('Not implemented'); }
}

class Rectangle extends Shape {
  constructor(public width: number, public height: number) { super(); }
  getArea() { return this.width * this.height; }
}

class Square extends Shape {
  constructor(public size: number) { super(); }
  getArea() { return this.size * this.size; }
}
```

**Aplicación de LSP:**
Cada clase respeta su propio contrato y puede usarse sin romper expectativas.

---

**Resumen visual:**
- Antes: La subclase rompe el contrato de la base.
- Después: Cada clase respeta su contrato y puede sustituirse sin problemas.
