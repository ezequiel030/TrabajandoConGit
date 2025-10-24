# Guía completa para trabajar con Git y GitHub

Git es un **sistema de control de versiones** que te permite registrar los cambios que realizas en tus proyectos, colaborar con otros desarrolladores y mantener un historial ordenado del desarrollo de tu código.  
GitHub es una plataforma donde puedes **alojar tus repositorios de Git en la nube** para compartirlos o trabajar en equipo.

Esta guía te explica cómo trabajar con **Git en local** y luego cómo conectar tu proyecto con **GitHub**.

---

##  1. Instalación y configuración inicial

### Instalar Git

Descarga Git desde 👉 [https://git-scm.com](https://git-scm.com)

O usa el terminal según tu sistema operativo:

**Windows:**  
El instalador de la web te guiará paso a paso.  

**macOS:**  
```bash
brew install git
```

**Linux (Debian/Ubuntu):**
```bash
sudo apt update
sudo apt install git
```
***Solo la primera vez, configura tu nombre y correo (aparecerán en tus commits):***
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@ejemplo.com"
```
***Verifica la configuración:***
```bash
git config --list
```
## 2. Definir la rama principal “main” por defecto

***Git solía usar “master” como rama principal, pero ahora se recomienda usar main.
Para establecerla por defecto en todos tus nuevos repositorios:***
***Pero también se puede cambiar el nombre de la rama main a tu-nombre, por ejemplo***
```bash
git config --global init.defaultBranch main
```
***Verifica el cambio:***
```bash
git config --global --get init.defaultBranch
```
***Si ya tienes un repositorio con la rama master y quieres cambiarla a main:***
```bash
git branch -m master main
```
## 3. Crear un nuevo repositorio local

***Crea una carpeta para tu proyecto y entra en ella:***
```bash
mkdir mi-proyecto
cd mi-proyecto
```
***Inicializa Git:***
```bash
git init
```
## 4. Añadir archivos y hacer el primer commit

***Crea un archivo (por ejemplo, un README):***
```bash
echo "# Mi primer proyecto con Git" > README.md
```
***Agrega el archivo al área de preparación (staging area):***
```bash
git add README.md
```
***Guarda los cambios en el historial con un commit:***
```bash
git commit -m "Primer commit: agregar README"
```
## 5. Ver el estado y el historial de cambios

***Ver el estado actual del repositorio:***
```bash
git status
```
***Ver el historial completo de commits:***
```bash
git log
```
***Ver el historial resumido (un commit por línea):***
```bash
git log --oneline
```
## 6. Ramas y cambios de contexto

***Las ramas permiten trabajar en nuevas funciones sin afectar el código principal.***

***Ver las ramas existentes:***
```bash
git branch
```

***Crear una nueva rama:***
```bash
git branch nueva-funcion
```

***Cambiarte a otra rama:***
```bash
git checkout nueva-funcion
```

***👉 O con el nuevo comando moderno:***
```bash
git switch nueva-funcion
```

***Volver a la rama principal:***
```bash
git checkout main
```
## 7. Ignorar archivos con .gitignore

***El archivo .gitignore le indica a Git qué archivos o carpetas no debe rastrear (por ejemplo, archivos temporales, dependencias o contraseñas).***

***Ejemplo de .gitignore:***
```bash
# Archivos del sistema
.DS_Store
Thumbs.db

# Dependencias
node_modules/

# Archivos de entorno
.env

# Compilaciones
dist/
build/
```
***Crea este archivo en la raíz del proyecto:***
```bash
touch .gitignore
```
## 8. Flujo de trabajo básico

***Cada vez que hagas cambios:***
```bash
git status             # Ver qué cambió
git add .              # Agregar todos los archivos modificados
git commit -m "Descripción del cambio"
```
***Para revisar el historial rápidamente:***
```bash
git log --oneline
```
## 9. Conectar tu repositorio local con GitHub
***Crear un repositorio en GitHub***

***Entra a [GitHub](https://github.com)***

***Crea un nuevo repositorio (sin README si ya tienes uno local)***

***Copia la URL del repositorio (por ejemplo: https://github.com/usuario/mi-proyecto.git)***

***Conectar el repositorio local con el remoto***

***En tu proyecto local:***
```bash
git remote add origin https://github.com/usuario/mi-proyecto.git
```
***Verifica que se haya agregado correctamente:***
```bash
git remote -v
```
***Subir tu proyecto a GitHub***

***Si tu rama principal es main:***
```bash
git branch -M main
git push -u origin main
```
***A partir de ahora, cuando hagas nuevos commits, puedes subirlos con:***
```bash
git push
```
***Y si alguien hace cambios en el remoto:***
```bash
git pull
```
## 10. Comandos útiles de repaso
```bash
git status             # Ver el estado del repositorio
git add archivo.txt    # Agregar un archivo específico
git add .              # Agregar todos los cambios
git commit -m "mensaje" # Crear un commit
git log --oneline      # Ver commits de forma resumida
git checkout rama      # Cambiar de rama
git branch             # Ver ramas
git push               # Subir cambios al remoto
git pull               # Descargar cambios del remoto
```
