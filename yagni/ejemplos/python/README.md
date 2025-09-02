# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="32"/> Ejemplo YAGNI en Python

Este ejemplo muestra cómo evitar agregar soporte multilenguaje en una aplicación que solo se usará en español.

---

## Antes (NO cumple YAGNI)
```python
def mostrar_mensaje(idioma):
    mensajes = {
        'es': 'Bienvenido',
        'en': 'Welcome',
        'fr': 'Bienvenue'
    }
    print(mensajes.get(idioma, 'Bienvenido'))
```

## Después (Cumple YAGNI)
```python
def mostrar_mensaje():
    print('Bienvenido')
```

**Aplicación de YAGNI:**
Solo se implementa el mensaje en español, que es lo que se requiere actualmente. Si en el futuro se necesita multilenguaje, se agrega en ese momento.

---

> "No lo vas a necesitar" — Kent Beck
