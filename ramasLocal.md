# Trabajar con ramas en Git (en local)

Las **ramas** en Git permiten dividir el desarrollo de tu proyecto en diferentes líneas de trabajo.  
Por ejemplo, puedes tener una rama principal (`main`) y crear otras ramas para desarrollar nuevas funciones o realizar pruebas sin alterar el código estable.

---

## 1. ¿Qué es una rama?

Una **rama** es simplemente un "puntero" a un conjunto de commits.  
La rama principal suele llamarse **main**, y de ella puedes crear tantas ramas secundarias como necesites.

Ejemplo:
- `main`: versión estable del proyecto  
- `login-feature`: rama donde desarrollas el sistema de inicio de sesión  
- `bugfix-footer`: rama donde corriges un error en el pie de página  

---

## 2. Ver las ramas existentes

```bash
git branch
```
