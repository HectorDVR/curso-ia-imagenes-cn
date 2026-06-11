# Introducción a Git y GitHub

Material de apoyo para el curso **Inteligencia Artificial Aplicada al Análisis de Imágenes en Ciencias Naturales y Ambientales** — Universidad Nacional de Colombia, Sede de La Paz.

Este repositorio te guiará desde la creación de tu cuenta de GitHub hasta los primeros pasos en el control de versiones. Al finalizar habrás hecho un *fork* de este repositorio, clonado tu copia en tu computador y practicado el flujo básico de trabajo con Git.

---

## Contenido

1. [¿Qué es Git y para qué sirve?](#1-qué-es-git-y-para-qué-sirve)
2. [Crear una cuenta en GitHub](#2-crear-una-cuenta-en-github)
3. [Conceptos básicos](#3-conceptos-básicos)
4. [Instalar Git en tu computador](#4-instalar-git-en-tu-computador)
5. [Configurar Git por primera vez](#5-configurar-git-por-primera-vez)
6. [Ejercicio 1 — Fork y clonación](#ejercicio-1--fork-y-clonación)
7. [Ejercicio 2 — Tu primer commit](#ejercicio-2--tu-primer-commit)
8. [Ejercicio 3 — Push y Pull Request](#ejercicio-3--push-y-pull-request)
9. [Referencia rápida de comandos](#referencia-rápida-de-comandos)

---

## 1. ¿Qué es Git y para qué sirve?

Imagina que trabajas en un informe de campo y guardas versiones como `informe_v1.docx`, `informe_v2.docx`, `informe_final.docx`, `informe_final_ESTE.docx`. Git hace exactamente eso, pero de forma ordenada y automática para cualquier tipo de archivo de texto (código, notebooks, archivos de configuración).

Con Git puedes:

- Guardar un historial completo de cambios con fecha, autor y descripción.
- Volver a cualquier versión anterior si algo sale mal.
- Trabajar en paralelo con otras personas sin pisarse los cambios.
- Colaborar en proyectos de análisis de imágenes o modelos de IA con tu equipo.

**GitHub** es una plataforma en la nube que almacena repositorios Git y facilita la colaboración. Es el estándar para compartir código científico y proyectos de inteligencia artificial.

---

## 2. Crear una cuenta en GitHub

1. Ve a [https://github.com](https://github.com) y haz clic en **Sign up**.
2. Ingresa tu correo electrónico, elige una contraseña y un nombre de usuario.
   - El nombre de usuario será visible en tus proyectos; elige algo profesional (por ejemplo, `agonzales-unal`).
3. Verifica tu correo electrónico con el código que GitHub te envía.
4. En el plan selecciona **Free** (es suficiente para el curso y para la mayoría de proyectos de investigación).
5. Listo: ya tienes tu cuenta en [https://github.com/tu-usuario](https://github.com/tu-usuario).

> **Tip:** si usas tu correo institucional (@unal.edu.co) puedes solicitar el plan **GitHub Education** de forma gratuita, que incluye repositorios privados y herramientas extra.

---

## 3. Conceptos básicos

| Término | Significado sencillo |
|---|---|
| **Repositorio (repo)** | Carpeta del proyecto con todo su historial de cambios. |
| **Commit** | Foto instantánea del estado del proyecto en un momento dado, con un mensaje que describe qué cambió. |
| **Branch (rama)** | Línea de trabajo paralela. La rama principal suele llamarse `main`. |
| **Clone** | Descargar una copia completa de un repositorio en tu computador. |
| **Fork** | Crear tu propia copia de un repositorio ajeno en tu cuenta de GitHub, para modificarlo libremente. |
| **Push** | Subir tus commits locales al repositorio en GitHub. |
| **Pull** | Descargar los cambios del repositorio en GitHub hacia tu computador. |
| **Pull Request (PR)** | Propuesta formal para incorporar los cambios de tu fork o rama al repositorio original. |

---

## 4. Instalar Git en tu computador

### Windows

1. Descarga el instalador desde [https://git-scm.com/download/win](https://git-scm.com/download/win).
2. Ejecuta el instalador y acepta las opciones por defecto.
3. Al finalizar, abre **Git Bash** desde el menú de inicio y verifica la instalación:

```bash
git --version
```

### macOS

```bash
git --version
```

Si Git no está instalado, el sistema ofrecerá instalarlo automáticamente a través de las herramientas de desarrollo de Xcode.

### Linux (Ubuntu/Debian)

```bash
sudo apt update && sudo apt install git
```

---

## 5. Configurar Git por primera vez

Antes de hacer cualquier commit debes decirle a Git quién eres. Abre una terminal (o Git Bash en Windows) y ejecuta:

```bash
git config --global user.name "Tu Nombre Apellido"
git config --global user.email "tu_correo@ejemplo.com"
```

Usa el mismo correo con el que creaste tu cuenta en GitHub. Puedes verificar la configuración con:

```bash
git config --list
```

---

## Ejercicio 1 — Fork y clonación

**Objetivo:** obtener tu propia copia del repositorio del curso en GitHub y descargarla en tu computador.

### Paso 1 — Hacer un fork

1. Asegúrate de estar autenticado en GitHub.
2. Ve a [https://github.com/CV4EUnal/intro_git](https://github.com/CV4EUnal/intro_git).
3. Haz clic en el botón **Fork** (esquina superior derecha).
4. En la pantalla siguiente deja los valores por defecto y haz clic en **Create fork**.

Ahora tienes una copia en `https://github.com/tu-usuario/intro_git`. Esa copia es tuya: puedes modificarla libremente sin afectar el repositorio original.

### Paso 2 — Clonar tu fork

En la página de **tu** fork (no la del repositorio original) haz clic en el botón verde **Code** y copia la URL HTTPS.

Luego, en tu terminal:

```bash
git clone https://github.com/tu-usuario/intro_git.git
cd intro_git
```

Ahora tienes el repositorio en tu computador. Comprueba que apunta a tu fork:

```bash
git remote -v
```

Deberías ver algo como:

```
origin  https://github.com/tu-usuario/intro_git.git (fetch)
origin  https://github.com/tu-usuario/intro_git.git (push)
```

---

## Ejercicio 2 — Tu primer commit

**Objetivo:** crear un archivo con información sobre ti y registrar ese cambio en el historial del repositorio.

### Paso 1 — Crear tu archivo de presentación

Dentro de la carpeta `participantes/` crea un archivo de texto con tu nombre de usuario como nombre de archivo, por ejemplo `participantes/agonzales.md`, con el siguiente contenido:

```markdown
# Tu Nombre

- **Disciplina:** (biología, ecología, agronomía, ingeniería forestal, etc.)
- **Institución:** 
- **¿Por qué tomaste este curso?:** 
- **Una especie, cultivo o ecosistema con el que trabajas:** 
```

> Si la carpeta `participantes/` no existe, créala.

### Paso 2 — Revisar el estado del repositorio

```bash
git status
```

Git te mostrará que hay un archivo nuevo que aún no está registrado.

### Paso 3 — Agregar el archivo al área de preparación (*staging*)

```bash
git add participantes/agonzales.md
```

### Paso 4 — Crear el commit

```bash
git commit -m "Agrego presentación de agonzales"
```

El mensaje del commit debe ser corto y descriptivo. Puedes verificar que el commit quedó guardado con:

```bash
git log --oneline
```

---

## Ejercicio 3 — Push y Pull Request

**Objetivo:** subir tus cambios a GitHub y proponer que sean incorporados al repositorio del curso.

### Paso 1 — Subir tus cambios a GitHub

```bash
git push origin main
```

GitHub puede pedirte que te autentiques. La forma más sencilla en la actualidad es usando un **Personal Access Token**:

1. En GitHub ve a **Settings → Developer settings → Personal access tokens → Tokens (classic)**.
2. Haz clic en **Generate new token**, selecciona el alcance `repo` y genera el token.
3. Copia el token y úsalo como contraseña cuando Git lo solicite.

> Alternativamente puedes configurar autenticación por SSH siguiendo la guía oficial de GitHub.

### Paso 2 — Crear un Pull Request

1. Ve a tu fork en GitHub: `https://github.com/tu-usuario/intro_git`.
2. Verás un aviso que dice **"This branch is 1 commit ahead of CV4EUnal:main"**. Haz clic en **Contribute → Open pull request**.
3. Revisa los cambios y escribe un título claro, por ejemplo: *"Presentación de agonzales"*.
4. Haz clic en **Create pull request**.

El instructor revisará los Pull Requests y los incorporará al repositorio del curso. Al final del ejercicio podrás ver las presentaciones de todos los participantes en la carpeta `participantes/`.

---

## Referencia rápida de comandos

```bash
# Clonar un repositorio
git clone <url>

# Ver el estado de los archivos
git status

# Agregar archivos al área de preparación
git add <archivo>          # un archivo específico
git add .                  # todos los archivos modificados

# Crear un commit
git commit -m "Mensaje descriptivo"

# Ver el historial de commits
git log --oneline

# Subir cambios al repositorio remoto
git push origin main

# Descargar cambios del repositorio remoto
git pull origin main

# Ver los remotos configurados
git remote -v
```

---

## Recursos adicionales

- [Documentación oficial de Git](https://git-scm.com/doc)
- [GitHub Docs en español](https://docs.github.com/es)
- [Pro Git (libro gratuito)](https://git-scm.com/book/es/v2)
- [GitHub Skills — cursos interactivos](https://skills.github.com/)

---

*Repositorio del curso: [https://github.com/CV4EUnal/intro_git](https://github.com/CV4EUnal/intro_git)*
