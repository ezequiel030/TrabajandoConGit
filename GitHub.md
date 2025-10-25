<div align = "center">

## Trabajar con Git y un repositorio remoto en GitHub
</div>

GitHub es una plataforma que te permite **alojar tus repositorios de Git en la nube**, compartir tu código y colaborar con otros desarrolladores.  
Una vez que tengas tu proyecto local funcionando con Git, puedes conectarlo a un repositorio remoto en GitHub para subir tu trabajo.

---
<div align = "center">

## 1. Crear un repositorio en GitHub
</div>

1. Inicia sesión en [https://github.com](https://github.com)
2. Haz clic en el botón **“New repository”** o **“Nuevo repositorio”**  
3. Escribe un nombre para tu repositorio (por ejemplo: `mi-proyecto`)
4. Puedes agregar una descripción si quieres
5. Selecciona si será público o privado
6. **⚠️ No marques la opción de “Add a README”** si ya tienes uno en tu proyecto local
7. Haz clic en **“Create repository”**

GitHub te mostrará una URL del tipo:
***https://github.com/tuusuario/mi-proyecto.git***

Guarda esa URL, la necesitarás para vincular tu repositorio local.

---
<div align = "center">

## 2. Conectar el repositorio local con GitHub
</div>

Ve a la carpeta de tu proyecto local (ya inicializado con `git init`) y agrega el repositorio remoto:

```bash
git remote add origin https://github.com/tuusuario/mi-proyecto.git
```
Verifica que se haya agregado correctamente:
```bash
git remote -v
```

Deberías ver algo como:
```bash
origin  https://github.com/tuusuario/mi-proyecto.git (fetch)
origin  https://github.com/tuusuario/mi-proyecto.git (push)
```
<div align = "center">

## 3. Asegurar que tu rama principal sea main
</div>

Si tu rama actual se llama master, cámbiala a main:
```bash
git branch -M main
```
<div align = "center">

## 4. Subir tu proyecto local a GitHub
</div>

Sube tu rama main al repositorio remoto por primera vez:
```bash
git push -u origin main
```

La opción -u vincula la rama local main con la rama main remota, de modo que luego puedas usar simplemente:
```bash
git push
```

para subir los cambios futuros.
<div align = "center">

## 5. Descargar cambios del remoto (pull)
</div>

Si trabajas con otras personas o haces cambios directamente en GitHub, puedes traer los cambios a tu equipo local con:
```bash
git pull
```

Esto sincroniza tu repositorio local con el remoto.
<div align = "center">

## 6. Clonar un repositorio de GitHub
</div>

Si en lugar de crear un nuevo proyecto, quieres descargar uno existente de GitHub:
```bash
git clone https://github.com/usuario/nombre-del-repo.git
```

Esto crea una carpeta con el proyecto y su historial de Git completo.
<div align = "center">

## 7. Trabajar con ramas remotas
</div>

Puedes crear una nueva rama en local y subirla a GitHub:

Crear y cambiar a una nueva rama
```bash
git checkout -b feature/login
```
Subirla al remoto
```bash
git push -u origin feature/login
```

Si alguien más crea una rama en GitHub y tú quieres traerla:
```bash
git fetch
git checkout nombre-de-la-rama
```
<div align = "center">

## 8. Fusionar ramas en GitHub (Pull Request)
</div>

Una vez que termines una funcionalidad en una rama, lo ideal es fusionarla a main mediante un Pull Request.

- Sube tu rama al remoto (git push)

- Entra al repositorio en GitHub

- Verás un botón que dice “Compare & pull request”

- Haz clic, revisa los cambios y crea el Pull Request

- Otro colaborador (o tú mismo) puede aprobar y hacer Merge

Esto mantiene un flujo de trabajo limpio y controlado.
<div align = "center">

## 9. Eliminar ramas remotas
</div>

Si ya fusionaste una rama y quieres eliminarla del remoto:
```bash
git push origin --delete nombre-de-la-rama
```

***Ejemplo:***
```bash
git push origin --delete feature/login
```
<div align = "center">

## 10. Comandos más usados con repositorios remotos
</div>

```bash
git remote -v                     # Ver repositorios remotos configurados
git remote add origin URL         # Conectar un repositorio remoto
git branch -M main                # Cambiar nombre de la rama principal
git push -u origin main           # Subir la rama principal
git push                          # Subir cambios al remoto
git pull                          # Descargar cambios del remoto
git fetch                         # Obtener referencias sin fusionar
git clone URL                     # Clonar un repositorio existente
git push origin --delete rama     # Eliminar rama remota
```
---

<p align="center">
  <a href="ramasLocal.md">⬅️ Anterior</a> |
  <a href="README.md">🏠 Índice</a> |
  <a href="colaborativa.md">➡️ Siguiente</a>
</p>
