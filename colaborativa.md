<div align = "center">

# Trabajar colaborativamente con *forks* y Pull Requests en GitHub
</div>

Cuando contribuyes a un proyecto en GitHub y no tienes permisos de escritura sobre el repositorio original, el flujo habitual es **hacer un fork**, trabajar en tu copia (fork), y enviar un **Pull Request (PR)** al repositorio original para pedir que acepten tus cambios.

---
<div align = "center">

## 1. Hacer fork del repositorio (UI de GitHub)
</div>

1. Ve al repositorio original en GitHub (por ejemplo `https://github.com/propietario/proyecto.git`).  
2. Haz clic en **Fork** (arriba a la derecha).  
3. GitHub creará una copia del repositorio en tu cuenta: `https://github.com/tuusuario/proyecto.git`.

---
<div align = "center">

## 2. Clonar tu fork a tu máquina local
</div>

Puedes clonar usando HTTPS o SSH.

**HTTPS:**
```bash
git clone https://github.com/tuusuario/proyecto.git
```
SSH:
```bash
git clone git@github.com:tuusuario/proyecto.git
```

Entra en la carpeta:
```bash
cd proyecto
```
<div align = "center">

## 3. Añadir el repositorio original como upstream
</div>

Para poder sincronizar los cambios del proyecto original (mantener tu fork actualizado) añade el remoto upstream:

HTTPS:
```bash
git remote add upstream https://github.com/propietario/proyecto.git
```

SSH:
```bash
git remote add upstream git@github.com:propietario/proyecto.git
```

Comprueba los remotos:
```bash
git remote -v
```

Deberías ver origin (tu fork) y upstream (el original).
<div align = "center">

## 4. Crear una rama para tu cambio (nunca trabajes en main directamente)
</div>

Crea una rama con un nombre descriptivo:
```bash
git checkout -b feature/descripcion-corta
```

Buenas prácticas de nombres:

feature/nueva-funcionalidad

fix/correccion-bug

docs/mejoras-readme
<div align = "center">

## 5. Hacer tus cambios, añadir y commitear
</div>

Haz los cambios en tu editor, luego:
```bash
git status
git add .
git commit -m "feat: descripción clara y corta del cambio"
```

Consejo: escribe mensajes de commit claros y en imperativo.
<div align = "center">

## 6. Subir la rama a tu fork (origin)
</div>

Empuja la rama a tu fork en GitHub:
```bash
git push -u origin feature/descripcion-corta
```

La opción -u establece el tracking entre la rama local y la remota.
<div align = "center">

## 7. Abrir el Pull Request en GitHub
</div>

- Ve a tu fork en GitHub. Verás un botón que sugiere crear un Compare & pull request para la rama que acabas de subir.

- O ve directamente al repositorio original y haz clic en New pull request, seleccionando como base la rama main (o la rama objetivo) del repositorio original y como compare tu rama en tuusuario/proyecto.

- Rellena el título y la descripción del PR: explica qué hiciste, por qué y cualquier paso para reproducir o probar los cambios.

- Selecciona reviewers, labels, proyecto o milestone si corresponde.

- Crea el Pull Request.
<div align = "center">

## 8. Mantener tu fork sincronizado con el repositorio original
</div>

Antes de empezar a trabajar y antes de crear un PR, sincroniza para evitar conflictos:

# Obtener cambios del original
```bash
git fetch upstream
```
# Cambiar a tu main local
```bash
git checkout main
```
# Traer los cambios de upstream/main y fusionarlos en tu main
```bash
git merge upstream/main
```
# O alternativamente hacer rebase si prefieres historial lineal
```bash
git rebase upstream/main
```
# Subir los cambios sincronizados a tu fork en GitHub
```bash
git push origin main
```

Si trabajas en una rama de trabajo y necesitas traer los últimos cambios de upstream/main a tu rama:
```bash
git checkout feature/descripcion-corta
git fetch upstream
git merge upstream/main
```
# o
```bash
git rebase upstream/main
```

<div align = "center">

## 9. Actualizar tu rama si el PR muestra conflictos
</div>

Si tu PR muestra conflictos o si el repositorio original ha cambiado, actualiza tu rama local y vuelve a empujar:

# desde tu rama de trabajo
```bash
git fetch upstream
git merge upstream/main   # o git rebase upstream/main
```
# resolver conflictos si aparecen:
# editar archivos conflictivos, luego:
```bash
git add archivo-resuelto
git commit -m "Resolver conflictos con upstream/main"
```
# empujar la rama actualizada a tu fork
```bash
git push origin feature/descripcion-corta
```

Si usaste rebase, puede que necesites forzar el push (solo en tu fork y en tu rama):
```bash
git push --force-with-lease origin feature/descripcion-corta
```

--force-with-lease es más seguro que --force.

<div align = "center">

## 10. Después de aceptar el Pull Request
</div>

Cuando el PR sea mergeado en el repositorio original:

Borra la rama remota de tu fork si ya no la necesitas:
```bash
git push origin --delete feature/descripcion-corta
```

Borra la rama local:
```bash
git branch -d feature/descripcion-corta
```

Sincroniza tu main con upstream (ver sección 8).
<div align = "center">

## 11. Resumen de comandos útiles
</div>

# Clonar tu fork
```bash
git clone URL_DE_TU_FORK
cd proyecto
```
# Añadir upstream (original)
```bash
git remote add upstream URL_DEL_REPO_ORIGINAL
git remote -v
```
# Mantener fork sincronizado
```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```
# Flujo para contribuir
```bash
git checkout -b feature/nombre
```
# ... editar ...
```bash
git add .
git commit -m "feat: descripción"
git push -u origin feature/nombre
```
# Abrir PR en GitHub

# Actualizar rama y resolver conflictos
```bash
git fetch upstream
git merge upstream/main   # o git rebase upstream/main
```
# resolver conflictos
```bash
git push origin feature/nombre
```
# Limpiar ramas
```bash
git branch -d feature/nombre
git push origin --delete feature/nombre
```
