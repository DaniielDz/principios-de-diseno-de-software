# Principios de Diseño de Software

Bienvenido a este repositorio, donde encontrarás ejemplos y explicaciones sobre los principales **principios de diseño de software**: SOLID, KISS, DRY y YAGNI.

---

## ¿Qué son los Principios de Diseño de Software?

Son un conjunto de reglas y buenas prácticas que ayudan a los desarrolladores a crear software fácil de entender, escalar, mantener y modificar. Estos principios son fundamentales para lograr un código limpio, robusto y sostenible a lo largo del tiempo.

A continuación, una breve descripción de cada uno:

- **SOLID:** Conjunto de cinco principios que promueven la creación de sistemas flexibles y fáciles de mantener. Incluye: Responsabilidad Única, Abierto/Cerrado, Sustitución de Liskov, Segregación de Interfaces y Principio de Inversión de Dependencias.
- **KISS (Keep It Simple, Stupid):** Recomienda mantener el diseño y la implementación lo más simple posible, evitando la complejidad innecesaria.
- **DRY (Don't Repeat Yourself):** Busca evitar la duplicidad de código y lógica, promoviendo la reutilización y la centralización de la funcionalidad.
- **YAGNI (You Aren't Gonna Need It):** Advierte contra la implementación de funcionalidades que no son necesarias en el momento, ayudando a mantener el enfoque y la simplicidad.

Aplicar estos principios mejora la calidad del software, facilita su evolución y reduce el riesgo de errores, permitiendo que los equipos trabajen de manera más eficiente y colaborativa.

---

## Índice

1. [SOLID](solid/README.md)
   - [S: Responsabilidad Única (SRP)](solid/s/README.md)
   - [O: Abierto/Cerrado (OCP)](solid/o/README.md)
   - [L: Sustitución de Liskov (LSP)](solid/l/README.md)
   - [I: Segregación de Interfaces (ISP)](solid/i/README.md)
   - [D: Inversión de Dependencias (DIP)](solid/d/README.md)
2. [KISS](kiss/README.md)
   - [Ejemplos por lenguaje](kiss/ejemplos/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="20"/> TypeScript](kiss/ejemplos/typescript/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="20"/> Java](kiss/ejemplos/java/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="20"/> Python](kiss/ejemplos/python/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="20"/> C#](kiss/ejemplos/csharp/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="20"/> PHP](kiss/ejemplos/php/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="20"/> Ruby](kiss/ejemplos/ruby/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="20"/> Go](kiss/ejemplos/go/README.md)
3. [DRY](dry/README.md)
   - [Ejemplos por lenguaje](dry/ejemplos/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="20"/> TypeScript](dry/ejemplos/typescript/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="20"/> Java](dry/ejemplos/java/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="20"/> Python](dry/ejemplos/python/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="20"/> C#](dry/ejemplos/csharp/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="20"/> PHP](dry/ejemplos/php/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="20"/> Ruby](dry/ejemplos/ruby/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="20"/> Go](dry/ejemplos/go/README.md)
4. [YAGNI](yagni/README.md)
   - [Ejemplos por lenguaje](yagni/ejemplos/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="20"/> TypeScript](yagni/ejemplos/typescript/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="20"/> Java](yagni/ejemplos/java/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="20"/> Python](yagni/ejemplos/python/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" width="20"/> C#](yagni/ejemplos/csharp/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="20"/> PHP](yagni/ejemplos/php/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg" width="20"/> Ruby](yagni/ejemplos/ruby/README.md)
     - [<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="20"/> Go](yagni/ejemplos/go/README.md)

Cada principio tiene:

- Un `README.md` con la explicación y ejemplos del principio.
- Una carpeta `ejemplos` con subcarpetas por lenguaje, cada una con su propio `README.md` y ejemplos de código.

---

## ¿Cómo usar este repositorio?

Explora cada principio, revisa los ejemplos y lee las explicaciones para comprender cómo aplicarlos en tus proyectos. ¡La práctica y el aprendizaje continuo son clave para mejorar como desarrollador!

---

## Recursos recomendados

- [Principios de diseño de software - Institute of Data](https://www.institutedata.com/blog/software-design-principles-creating-improved-system-designs/)
- [Principios de diseño de software que todo programador debería conocer](https://medium.com/@peterlee2068/software-design-principles-every-programmer-should-know-c164a83c6f87)
- [6 principios de diseño de software utilizados por ingenieros exitosos](https://swimm.io/learn/system-design/6-software-design-principles-used-by-successful-engineers)

---

¡Contribuciones y sugerencias son bienvenidas!
