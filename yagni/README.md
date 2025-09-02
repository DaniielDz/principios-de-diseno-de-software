# Principio YAGNI

El principio **YAGNI** significa "You Aren’t Gonna Need It" (No lo vas a necesitar), y se refiere a la idea de no implementar funcionalidades ni complejidad que no sean estrictamente necesarias en el momento.

La clave es concentrarse en los requerimientos actuales, evitando sobreingeniería o anticipar problemas futuros que quizás nunca ocurran.

---

## ¿Por qué es importante el principio YAGNI?

- **Reduce complejidad innecesaria:** Menos código significa menos posibilidades de errores y menos mantenimiento.
- **Acelera el desarrollo:** Al enfocarte en lo que realmente se necesita, terminas las tareas más rápido.
- **Facilita el mantenimiento:** No hay código “fantasma” que nadie entiende o usa.
- **Evita sobreingeniería:** No se agregan abstracciones ni funcionalidades que nunca se usarán.

---

## ¿Cómo aplicar el principio YAGNI?

- **Implementa solo lo que se necesita ahora:** Evita crear funcionalidades “por si acaso” o pensando en casos futuros.
- **Refactoriza cuando sea necesario:** Si surge un requerimiento nuevo, crea la funcionalidad en ese momento, no antes.
- **Mantén el código simple y directo:** No compliques el diseño con anticipación; sigue KISS y DRY junto a YAGNI.
- **Valida los requerimientos:** Pregunta siempre: “¿Realmente necesitamos esto ahora, o podemos implementarlo más adelante si hace falta?”

---

## Ejemplo en TypeScript

### Antes: sobreingeniería (YAGNI ignorado)
```typescript
class Reporte {
  mostrar(datos: any[]) {
    // Mostrar datos en pantalla
  }
  exportarPDF(datos: any[]) {
    // Lógica para exportar a PDF
  }
  exportarExcel(datos: any[]) {
    // Lógica para exportar a Excel
  }
}
```

### Después: aplicando YAGNI
```typescript
class Reporte {
  mostrar(datos: any[]) {
    // Mostrar datos en pantalla
  }
}
```

> Observa cómo solo se implementa la funcionalidad requerida actualmente (mostrar datos). Si en el futuro se necesita exportar, se agrega en ese momento.

---

## Recursos recomendados

- [YAGNI (wikipedia)](https://es.wikipedia.org/wiki/YAGNI)
- [Principio YAGNI: no vas a necesitarlo](https://codeyourapps.com/principio-yagni-no-vas-a-necesitarlo/)
- [Principio YAGNI: evita la sobreingeniería](https://www.arsys.es/blog/principio-yagni-evita-la-sobreingenieria)
- [YAGNI (You Aren't Gonna Need It) Principle Helps Devs Stay Efficient](https://builtin.com/software-engineering-perspectives/yagni)

---

💡 **Consejo extra:**
YAGNI funciona mejor cuando lo combinas con KISS y DRY: mantener el código simple, evitar duplicación y no implementar lo que no se necesita.
