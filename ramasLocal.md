<div align = "center">

# Trabajar con ramas en Git (en local)
</div>

Las **ramas** en Git permiten dividir el desarrollo de tu proyecto en diferentes líneas de trabajo.  
Por ejemplo, puedes tener una rama principal (`main`) y crear otras ramas para desarrollar nuevas funciones o realizar pruebas sin alterar el código estable.

---
<div align = "center">

## 1. ¿Qué es una rama?
</div>

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
***La rama actual se mostrará con un asterisco *.***

***Ejemplo:***
```bash
* main
  login-feature
  bugfix-footer
```

## 3. Crear una nueva rama

***Para crear una nueva rama:***
```bash
git branch nombre-de-la-rama
```
***Ejemplo:***
```bash
git branch nueva-funcion
```
***Esto crea la rama, pero no te cambia a ella todavía.***

## 4. Cambiar de rama

***Para moverte a otra rama:***
```bash
git checkout nombre-de-la-rama
```
***Ejemplo:***
```bash
git checkout nueva-funcion
```
***👉 Con versiones modernas de Git, también puedes usar:***
```bash
git switch nombre-de-la-rama
```
## 5. Crear y cambiar de rama en un solo paso
```bash
git checkout -b nombre-de-la-rama
```
***Ejemplo:***
```bash
git checkout -b login-feature
```
***Esto crea la rama y te cambia a ella al mismo tiempo.***

## 6. Hacer commits en una rama

***Mientras estés en una rama, los commits se guardan solo ahí:***
```bash
git add .
git commit -m "Agregar nueva funcionalidad de login"
```
***Esto no afectará a la rama main hasta que las fusiones.***

## 7. Fusionar una rama con la principal

***Cuando termines de trabajar en una rama y quieras integrar los cambios a main:***

***Primero, cambia a la rama principal:***
```bash
git checkout main
```
***Luego, fusiona la otra rama:***
```bash
git merge nombre-de-la-rama
```
***Ejemplo:***
```bash
git merge login-feature
```
***Si no hay conflictos, Git combinará los cambios automáticamente ✅***

## 8. Resolver conflictos de fusión (merge conflicts)

***A veces Git no puede fusionar automáticamente porque hubo cambios en las mismas líneas de código en ambas ramas.
Git marcará los archivos en conflicto con símbolos como estos:***

```bash
<<<<<<< HEAD
Código de la rama main
=======
Código de la rama login-feature
>>>>>>> login-feature
```

***Tú deberás editar manualmente esos archivos para decidir qué versión conservar.
Luego marcas el conflicto como resuelto:***
```bash
git add archivo-conflictivo.txt
git commit -m "Resolver conflicto de merge"
```
## 9. Eliminar una rama (después de fusionar)

***Cuando una rama ya no se necesita:***
```bash
git branch -d nombre-de-la-rama
```
***Ejemplo:***
```bash
git branch -d login-feature
```

***Si la rama no ha sido fusionada aún y quieres eliminarla de todos modos:***
```bash
git branch -D nombre-de-la-rama
```
## 10. Ver todas las ramas (locales y remotas)

***Para ver solo las ramas locales:***
```bash
git branch
```

***Para ver también las ramas remotas (si ya conectaste con GitHub):***
```bash
git branch -a
```
