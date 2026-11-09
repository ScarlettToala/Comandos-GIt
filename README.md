# Comandos de Terminal (Generales de Git)

## Índice

1. [Configuración inicial](#1-configuración-inicial)
2. [Repositorio local](#2-repositorio-local)
   - [Inicializar un repositorio](#inicializar-un-repositorio)
   - [Añadir archivos (staging)](#añadir-archivos-staging)
   - [Quitar archivos del staging](#quitar-archivos-del-staging)
   - [Hacer commits](#hacer-commits)
   - [Ver el estado](#ver-el-estado)
   - [Ver el historial](#ver-el-historial)
   - [Ver diferencias](#ver-diferencias)
   - [Eliminar un archivo](#eliminar-un-archivo)
   - [Renombrar o mover un archivo](#renombrar-o-mover-un-archivo)
3. [Ramas](#3-ramas)
   - [Crear una rama](#crear-una-rama)
   - [Moverse entre ramas](#moverse-entre-ramas)
   - [Ver las ramas](#ver-las-ramas)
   - [Eliminar una rama](#eliminar-una-rama)
   - [Fusionar ramas](#fusionar-ramas)
4. [Repositorio remoto (GitHub)](#4-repositorio-remoto-github)
   - [Subir un repositorio local a remoto](#subir-un-repositorio-local-a-remoto)
   - [Otros comandos habituales](#otros-comandos-habituales)
5. [Desplegar en Vercel](#5-desplegar-en-vercel)
6. [Sintaxis Markdown](#6-sintaxis-markdown)
7. [Alias](#7-alias)
   - [Alias básicos](#alias-básicos)
   - [Alias propios de Git](#alias-propios-de-git)
   - [Alias con colores](#alias-con-colores)
   - [Colores en los listados](#colores-en-los-listados)
8. [Comodines (wildcards)](#8-comodines-wildcards)
9. [Comandos extra de terminal](#9-comandos-extra-de-terminal)
   - [Editar un archivo](#editar-un-archivo)
   - [Ver el contenido de un archivo](#ver-el-contenido-de-un-archivo)
   - [Listar el contenido del directorio](#listar-el-contenido-del-directorio)
   - [Crear el archivo .gitignore](#crear-el-archivo-gitignore)

---

## 1. Configuración inicial

Configura tu identidad (solo se hace una vez por equipo):
```bash
git config --global user.name "usuario"
git config --global user.email "correo@ejemplo.com"
git config --list
```

## 2. Repositorio local

### Inicializar un repositorio
```bash
git init
```

### Añadir archivos (staging)
```bash
git add archivo.txt   # un archivo concreto
git add .             # todos los cambios
```

### Quitar archivos del staging
Sin perder los cambios:
```bash
git reset archivo.txt
# alternativa moderna:
git restore --staged archivo.txt
```

### Hacer commits
```bash
git commit -m "Mensaje descriptivo"
```

### Ver el estado
```bash
git status
git status --short
```

### Ver el historial
```bash
git log
git log --oneline --decorate --all --graph
```

### Ver diferencias
Muestra los cambios entre el directorio de trabajo y el staging (o entre commits/ramas).
```bash
git diff                 # cambios sin añadir
git diff --staged        # cambios ya añadidos con git add
git diff rama1 rama2     # entre dos ramas
```

### Eliminar un archivo
```bash
git rm archivo.txt
```

### Renombrar o mover un archivo
```bash
git mv nombre_antiguo nombre_nuevo
```

## 3. Ramas

### Crear una rama
```bash
git branch nombre
```

### Moverse entre ramas
```bash
git checkout nombre
git switch nombre          # alternativa moderna
git checkout -b nombre     # crear y moverse a la vez
```

### Ver las ramas
La rama actual aparece marcada con `*`.
```bash
git branch --all
```

### Eliminar una rama
```bash
git branch -d nombre    # solo si ya está fusionada
git branch -D nombre    # forzar el borrado
```

### Fusionar ramas
Primero muévete a la rama que va a *recibir* los cambios (por ejemplo `main`):
```bash
git checkout main
git merge nombre
```
Si hay conflictos y quieres cancelar la fusión:
```bash
git merge --abort
```

## 4. Repositorio remoto (GitHub)

### Subir un repositorio local a remoto

> [!NOTE]
> Sigue las recomendaciones que te muestra GitHub al crear el repositorio.

```bash
git remote add origin url
git branch -M main
git push -u origin main
```

### Otros comandos habituales
```bash
git clone url      # descargar un repositorio
git pull           # traer cambios del remoto
git push           # subir commits
```

## 5. Desplegar en Vercel

[Vercel](https://vercel.com/)

1. La página web debe funcionar en local.
2. El repositorio debe estar en GitHub.
3. Elegir el repositorio desde Vercel.

> [!WARNING]
> A veces el proyecto está dividido en subcarpetas: hay que elegir la carpeta correcta (*Root Directory*) para que se visualice bien.
> Siempre debe ser uno de tus propios repositorios, no uno en el que seas colaborador.

## 6. Sintaxis Markdown

| Elemento | Sintaxis |
|:--|:--|
| Título | `# Título` (más `#` = subtítulo) |
| Nota | `> [!NOTE]` |
| Advertencia | `> [!WARNING]` |
| Código en línea | `` `código` `` |
| Bloque de código | ```` ```bash ```` … ```` ``` ```` |
| Email | `<ejemplo@gmail.com>` |
| Enlace | `[texto del enlace](url)` |

## 7. Alias

Un alias es un atajo para un comando largo. Se guardan en `~/.bashrc` (o `~/.zshrc`) y se cargan con `source ~/.bashrc`.

### Alias básicos
```bash
alias ga='git add'
alias gc='git commit -m'
alias gs='git status'
alias gss='git status --short'
alias gl='git log --oneline --decorate --all --graph'
alias gco='git checkout'
alias gb='git branch'
alias mk='mkdir'
alias t='touch'
```

Ver todos los alias definidos:
```bash
alias
```

> [!NOTE]
> El nombre de un alias no puede llevar espacios (`alias git l=...` no funciona).
> Evita `gh`, porque choca con GitHub CLI.

### Alias propios de Git
```bash
git config --global alias.l "log --oneline --decorate --all --graph"
# se usa así: git l
```

### Alias con colores
```bash
alias gs='echo -e "\e[32mGit Status:\e[0m" && git status -sb'                     # verde
alias gl='echo -e "\e[34mGit Log:\e[0m" && git log --oneline --graph --decorate'  # azul
alias gd='echo -e "\e[31mGit Diff:\e[0m" && git diff --color-words'               # rojo
```

### Colores en los listados
```bash
alias ll='ls -lh --color=auto'     # listado largo
alias la='ls -lha --color=auto'    # incluye archivos ocultos
```

## 8. Comodines (wildcards)

Sirven para seleccionar varios archivos a la vez:
```bash
git add *.temp     # todos los archivos que acaban en .temp
```

## 9. Comandos extra de terminal

### Editar un archivo
```bash
nano archivo.txt
```

### Ver el contenido de un archivo
```bash
cat archivo.txt
```

### Listar el contenido del directorio
```bash
ls
```

### Crear el archivo .gitignore
Debe ir en la raíz del repositorio, para ignorar archivos:
```bash
touch .gitignore
```
