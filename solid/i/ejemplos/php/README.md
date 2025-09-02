# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="32"/> Ejemplo ISP en PHP

Este ejemplo muestra cómo transformar una interfaz "gorda" en interfaces específicas y cohesivas.

---

## Antes (NO cumple ISP)
```php
<?php
interface Worker {
    public function work();
    public function eat();
    public function sleep();
}

class Human implements Worker {
    public function work() { echo "Trabajando...\n"; }
    public function eat() { echo "Comiendo...\n"; }
    public function sleep() { echo "Durmiendo...\n"; }
}

class Robot implements Worker {
    public function work() { echo "Trabajando...\n"; }
    public function eat() { 
        throw new Exception("Los robots no comen"); 
    }
    public function sleep() { 
        throw new Exception("Los robots no duermen"); 
    }
}
?>
```

**Problema:** La interfaz `Worker` fuerza a `Robot` a implementar métodos que no necesita (`eat` y `sleep`), violando ISP.

---

## Después (Cumple ISP)
```php
<?php
interface Workable {
    public function work();
}

interface Eatable {
    public function eat();
}

interface Sleepable {
    public function sleep();
}

class Human implements Workable, Eatable, Sleepable {
    public function work() { echo "Trabajando...\n"; }
    public function eat() { echo "Comiendo...\n"; }
    public function sleep() { echo "Durmiendo...\n"; }
}

class Robot implements Workable {
    public function work() { echo "Trabajando...\n"; }
}
?>
```

**Aplicación de ISP:**
Cada interfaz tiene una responsabilidad específica. Los clientes solo dependen de las interfaces que realmente necesitan.

---

**Resumen visual:**
- Antes: Una interfaz "gorda" que fuerza implementaciones innecesarias.
- Después: Interfaces específicas que solo exponen lo que cada cliente necesita.
