# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo ISP en Python

Este ejemplo muestra cómo transformar una interfaz "gorda" en interfaces específicas y cohesivas.

---

## Antes (NO cumple ISP)
```python
from abc import ABC, abstractmethod

class Worker(ABC):
    @abstractmethod
    def work(self):
        pass
    
    @abstractmethod
    def eat(self):
        pass
    
    @abstractmethod
    def sleep(self):
        pass

class Human(Worker):
    def work(self):
        print("Trabajando...")
    
    def eat(self):
        print("Comiendo...")
    
    def sleep(self):
        print("Durmiendo...")

class Robot(Worker):
    def work(self):
        print("Trabajando...")
    
    def eat(self):
        raise NotImplementedError("Los robots no comen")
    
    def sleep(self):
        raise NotImplementedError("Los robots no duermen")
```

**Problema:** La clase abstracta `Worker` fuerza a `Robot` a implementar métodos que no necesita (`eat` y `sleep`), violando ISP.

---

## Después (Cumple ISP)
```python
from abc import ABC, abstractmethod

class Workable(ABC):
    @abstractmethod
    def work(self):
        pass

class Eatable(ABC):
    @abstractmethod
    def eat(self):
        pass

class Sleepable(ABC):
    @abstractmethod
    def sleep(self):
        pass

class Human(Workable, Eatable, Sleepable):
    def work(self):
        print("Trabajando...")
    
    def eat(self):
        print("Comiendo...")
    
    def sleep(self):
        print("Durmiendo...")

class Robot(Workable):
    def work(self):
        print("Trabajando...")
```

**Aplicación de ISP:**
Cada clase abstracta tiene una responsabilidad específica. Los clientes solo dependen de las interfaces que realmente necesitan.

---

**Resumen visual:**
- Antes: Una interfaz "gorda" que fuerza implementaciones innecesarias.
- Después: Interfaces específicas que solo exponen lo que cada cliente necesita.
