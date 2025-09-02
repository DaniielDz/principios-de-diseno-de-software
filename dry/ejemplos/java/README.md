# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="32"/> Ejemplo DRY en Java

Este ejemplo muestra cómo evitar duplicación de lógica en el cálculo de salario neto para empleados y contratistas.

---

## Antes (NO cumple DRY)
```java
public double calcularSalarioNetoEmpleado(double salario, double descuento) {
    double neto = salario - (salario * descuento);
    return neto;
}

public double calcularSalarioNetoContratista(double salario, double descuento) {
    double neto = salario - (salario * descuento);
    return neto;
}
```

## Después (Cumple DRY)
```java
public double calcularSalarioNeto(double salario, double descuento) {
    return salario - (salario * descuento);
}

// Uso
calcularSalarioNeto(1000, 0.1);
calcularSalarioNeto(2000, 0.15);
```

**Aplicación de DRY:**
La lógica de cálculo de salario neto está centralizada en un solo método reutilizable, evitando duplicación y facilitando el mantenimiento.

---

> "La duplicación es el enemigo. Eliminarla es el primer paso hacia un buen diseño." — Robert C. Martin
