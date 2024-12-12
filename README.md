# Comandos Terminal (Generales de GIT)

**Inicializar repositorios Git**
```bash
git init
```
**Añadir archivos**
```bash
git add
```
**Eliminar archivo del git add**
```bash
git reset 
```
**Hacer commits**
```bash
git commit -m "Commit"
```
**Ver el estado**
```bash
git status
git status –short
```
**Ver el historial**
```bash
git log
git log --oneline --decorate --all --graph
```

**Crear ramas** 
```bash
git branch nombre
```
**Moverse entre ramas**
```bash
git checkout nombre
```
**Eliminar una rama**
```bash
git branch -d nombre
```
**Ver todas las ramas y que rama estas**
```bash
git branch --all 
```

**Para unir todas las ramas**
```bash
git merge 
```

**Subir un repositorio de local a remoto.**

>[!NOTE]
> Seguir las recomendaciones de git
```bash
git remote add origin url
git branch -M main
git push -u origin main
```

**Desplegar en Vercel y que se visualice correctamente.**

 Vercel [Link](https://vercel.com/)
1. La página web debe funcionar localmente.
2. El repositorio debe estar en Git Hub.
3. Eligir el repositorio.

>[!WARNING]
> Recordar que a veces esta dividido en subcarpetas y hay que elegir una para que se muestre.
> Simpre será uno de tus mismos repositorios no colaboradores

**Saber aplicar nomenclatura Markdown.**

|          NOMBRE          |               Formación               |
|:------------------------:|:-------------------------------------:|
|          Titulo          |                   #                   |
|          Notas           |                [!NOTE]                |
|         Warning          |              [!WARNING]               |
|     Destaque codigo      |             `codigo`(``)              |
|          email           | <<nombreArroba_>> <ejemplo@gmail.com> |
| contenido en bloque copy |          ```bash git ash```           |
|           Link           |     explicación[nombrelink](url)      |





**Saber reconocer un alias**

```bash
alias ga='git add'
alias gh='git log'
alias gs='git status'
alias gss='git status --short'
alias git l ='git log --oneline --decorate --all --graph'
alias gc='git commit -m'
alias git che='git checkout'
alias gb='git branch'
alias mk='mkdir'
alias t='touch' 
```
**Expresiones regulares básicas.**
>Para seleccionar todos los archivos en con elcomando _*.temp_ -> todos los archvos acabados en ese final 

### Comandos extras
Comandos para iniciar sesión en git desde el local terminal. 
```bash
git config --global user.name "usuario"
git config --global user.email "correo@id.com"
git config --list
```

Comando que modifica el contendio.
```bash
nano arhivo.formato
```

Para conocer el contenido.
```bash
cat arc.format
```


Comando para conocer el contenido del directorio.
```bash
ls 
```

Para crear el archivo de git ignore
```bash
touch ~/.gitignore 
```
