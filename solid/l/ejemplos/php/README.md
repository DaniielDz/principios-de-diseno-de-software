# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="32"/> Ejemplo LSP en PHP

Este ejemplo muestra cómo una subclase puede romper el contrato de la clase base y cómo corregirlo para cumplir LSP.

---

## Antes (NO cumple LSP)
```php
class Rectangle {
    public $width;
    public $height;
    public function __construct($width, $height) {
        $this->width = $width;
        $this->height = $height;
    }
    public function setWidth($w) { $this->width = $w; }
    public function setHeight($h) { $this->height = $h; }
    public function getArea() { return $this->width * $this->height; }
}

class Square extends Rectangle {
    public function setWidth($w) { $this->width = $w; $this->height = $w; }
    public function setHeight($h) { $this->width = $h; $this->height = $h; }
}
```

**Problema:** Square no respeta el contrato de Rectangle. El comportamiento esperado se rompe.

---

## Después (Cumple LSP)
```php
abstract class Shape {
    abstract public function getArea();
}

class Rectangle extends Shape {
    private $width;
    private $height;
    public function __construct($width, $height) {
        $this->width = $width;
        $this->height = $height;
    }
    public function getArea() { return $this->width * $this->height; }
}

class Square extends Shape {
    private $size;
    public function __construct($size) { $this->size = $size; }
    public function getArea() { return $this->size * $this->size; }
}
```

**Aplicación de LSP:**
Cada clase respeta su propio contrato y puede usarse sin romper expectativas.

---

**Resumen visual:**
- Antes: La subclase rompe el contrato de la base.
- Después: Cada clase respeta su contrato y puede sustituirse sin problemas.
