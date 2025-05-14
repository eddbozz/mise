¡Excelente idea! Aquí tienes un "Cheat Sheet" de Mise en formato Markdown. Está diseñado para ser una referencia rápida a los comandos y conceptos más comunes.

# Mise (antes rtx) - Cheat Sheet Rápido 🚀

Mise es un gestor de versiones de herramientas políglota, rápido y moderno. Te ayuda a gestionar las versiones de Node.js, Python, Ruby, Go, Terraform, kubectl, y muchas más herramientas por proyecto o globalmente.

## 📋 Conceptos Clave

*   **Plugins:** Definen cómo Mise instala una herramienta específica (Node, Python, etc.). Compatible con plugins de `asdf`.
*   **`.mise.toml`:** Archivo de configuración principal por proyecto (o global). Define herramientas, versiones, variables de entorno y tareas.
*   **`.tool-versions`:** Archivo de configuración compatible con `asdf`, también leído por Mise.
*   **Activación Automática:** Mise puede cambiar automáticamente las versiones de las herramientas al entrar/salir de un directorio con un archivo de configuración.

---

## 🛠️ Instalación y Configuración Inicial

**Instalación:**
*   **Homebrew (macOS/Linux):**
    ```bash
    brew install mise
    ```
*   **Script (Linux/macOS):**
    ```bash
    curl https://mise.run | sh
    ```
*   **Otras plataformas:** Consulta la [documentación oficial](https://mise.jdx.dev/getting-started.html).

**Integración con Shell (¡Muy Importante!):**
Añade esto al final de tu archivo de configuración de shell (`.bashrc`, `.zshrc`, `config.fish`, etc.):
*   **Bash:** `echo 'eval "$(mise activate bash)"' >> ~/.bashrc`
*   **Zsh:** `echo 'eval "$(mise activate zsh)"' >> ~/.zshrc`
*   **Fish:** `echo 'mise activate fish | source' >> ~/.config/fish/config.fish`
Luego, reinicia tu terminal o ejecuta `source ~/.bashrc` (o el archivo correspondiente).

**Verificar Instalación:**
```bash
mise --version


Actualizar Mise:

mise self-update
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
🧩 Gestión de Plugins

Añadir un plugin:

mise plugins add <nombre_plugin>
# Ejemplos:
mise plugins add node
mise plugins add python
mise plugins add terraform
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Listar plugins instalados:

mise plugins ls
# Alias: mise p ls
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Actualizar un plugin específico:

mise plugins update <nombre_plugin>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Actualizar todos los plugins:

mise plugins update --all
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Eliminar un plugin:

mise plugins remove <nombre_plugin>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
⚙️ Gestión de Versiones de Herramientas

Instalar una versión específica de una herramienta:

mise install <herramienta>@<version>
# Ejemplos:
mise install node@20.10.0
mise install python@3.11.6
mise install terraform@latest # Instala la última versión estable
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Instalar herramientas definidas en .mise.toml o .tool-versions del directorio actual:

mise install
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Establecer una versión global por defecto:

mise use --global <herramienta>@<version>
# Ejemplo:
mise use --global node@lts # Usa la última LTS de Node
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Establecer una versión local (crea/actualiza .mise.toml o .tool-versions):

mise use --local <herramienta>@<version>
# O edita directamente el archivo .mise.toml
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Ver versiones activas actualmente:

mise current
# Alias: mise c
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Listar versiones instaladas de una herramienta:

mise ls <herramienta>
# Ejemplo: mise ls node
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Listar versiones remotas disponibles de una herramienta:

mise ls-remote <herramienta>
# Ejemplo: mise ls-remote python
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Mostrar la ruta del ejecutable de la herramienta activa:

mise which <herramienta>
# Ejemplo: mise which node
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Desinstalar una versión específica:

mise uninstall <herramienta>@<version>
# Ejemplo: mise uninstall node@18.0.0
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
📄 Archivo de Configuración .mise.toml

Ejemplo de estructura:

# .mise.toml

# Definición de herramientas y sus versiones
[tools]
node = "20" # Puede ser una versión mayor, específica o 'lts'
python = "3.11.6"
terraform = "1.6.0"
# go = "ref:go1.21" # Para versiones que no son semver exactas

# Variables de entorno específicas del proyecto
[env]
# MY_API_KEY = "supersecret" # NO comitear secretos, usar .env o gestor de secretos
NODE_ENV = "development"
AWS_REGION = "us-east-1"

# Tareas (Task Runner integrado)
[tasks.lint]
description = "Ejecuta el linter"
run = "eslint ."
# depends_on = ["npm_install"] # Para dependencias entre tareas

[tasks.npm_install]
run = "npm install"
# sources = ["package-lock.json"] # Archivos que, si cambian, invalidan la caché de la tarea
# outputs = ["node_modules"]      # Archivos/directorios que produce la tarea
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Toml
IGNORE_WHEN_COPYING_END

Mise también lee archivos .tool-versions para compatibilidad con asdf.

# .tool-versions
nodejs 20.10.0
python 3.11.6
terraform 1.6.0
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
IGNORE_WHEN_COPYING_END
🏃 Task Runner (mise run)

Listar tareas disponibles (definidas en [tasks] de .mise.toml):

mise tasks
# o
mise run --list
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Ejecutar una tarea:

mise run <nombre_tarea>
# Ejemplo: mise run lint
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Ejecutar una tarea en modo "dry run" (muestra qué haría):

mise run --dry-run <nombre_tarea>
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END
🌐 Variables de Entorno

Establecer variables de entorno globales (en ~/.config/mise/config.toml):

# ~/.config/mise/config.toml
[env_vars]
GLOBAL_VAR = "SoyGlobal"
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Toml
IGNORE_WHEN_COPYING_END

Establecer variables de entorno locales (en .mise.toml del proyecto):

# .mise.toml
[env]
PROJECT_SPECIFIC_VAR = "SoyDelProyecto"
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Toml
IGNORE_WHEN_COPYING_END

Mise también carga archivos .env automáticamente si existen en el directorio del proyecto.

✨ Comandos Útiles Adicionales

Mostrar ayuda general o de un comando específico:

mise help
mise help <comando> # Ej: mise help install
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Diagnosticar problemas de configuración:

mise doctor
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Confiar/Desconfiar en un archivo de configuración (para seguridad):

mise trust
mise untrust
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Ejecutar un comando con un entorno específico sin activar globalmente:

mise x -- node@18 --version # Ejecuta node --version usando Node 18 temporalmente
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

🔗 Recursos Oficiales:

Documentación: https://mise.jdx.dev/

GitHub: https://github.com/jdx/mise

Esperamos que este cheat sheet te sea útil. ¡Feliz codeo!

Puedes guardar este contenido como un archivo `.md` (por ejemplo, `mise-cheatsheet.md`) y consultarlo cuando lo necesites. ¡Espero que te sirva!
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
IGNORE_WHEN_COPYING_END
