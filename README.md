# Mi entorno de desarrollo Linux

Configuración de mi entorno de trabajo en Linux, documentada como 
parte del curso de Configuración y Entorno en Linux (Platzi).

## Entorno

- **Shell**: Zsh
- **Gestión de versiones de Python**: pyenv
- **Entornos virtuales**: venv
- **Gestor de paquetes**: pip
- **Entornos probados**:
  - WSL2 con Ubuntu (entorno principal de trabajo diario)
  - Ubuntu en VirtualBox (máquina virtual completa)

## Comandos básicos de Linux (referencia)

### Navegación y exploración
| Comando | Función |
|---|---|
| `cd` | Cambiar de directorio |
| `ls` / `ls -la` | Listar archivos (incluyendo ocultos y detalles) |
| `pwd` | Mostrar el directorio actual |

## Instalación y configuración de herramientas de desarrollo

### Python: pip3/python3 → alias python/pip

Por defecto, Ubuntu instala Python 3 como `python3` y su gestor de 
paquetes como `pip3`, dejando los comandos `python` y `pip` sin usar 
(reservados históricamente para Python 2). Para trabajar más cómodo, 
se crean alias:

```bash
sudo apt install python3 python3-pip
sudo ln -s /usr/bin/python3 /usr/bin/python
sudo ln -s /usr/bin/pip3 /usr/bin/pip
```

Ahora `python` y `pip` apuntan directamente a las versiones de Python 3.

### pyenv (gestor de versiones de Python)

Permite instalar y alternar entre múltiples versiones de Python en el 
mismo sistema, sin conflictos entre proyectos.

```bash
curl https://pyenv.run | bash
```

Luego se agrega al `.zshrc` (o `.bashrc`):

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

Uso básico:
```bash
pyenv install 3.12.0    # instalar una versión específica
pyenv global 3.12.0     # establecerla como versión por defecto
```

### Node.js y NVM (Node Version Manager)

Al igual que pyenv para Python, NVM permite gestionar múltiples 
versiones de Node.js.

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Uso básico:
```bash
nvm install --lts      # instalar la última versión estable (LTS)
nvm use --lts          # usarla en la sesión actual
node -v                # verificar versión instalada
```

### Git: instalación y configuración inicial

```bash
sudo apt install git
```

Configuración de identidad (necesaria antes del primer commit):

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu_correo@ejemplo.com"
```

Configuración de llave SSH para autenticación con GitHub/GitLab sin 
usuario y contraseña:

```bash
ssh-keygen -t ed25519 -C "tu_correo@ejemplo.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

La llave pública (`~/.ssh/id_ed25519.pub`) se agrega luego en la 
configuración de SSH de GitHub/GitLab.

## Comandos de Linux (referencia ampliada)

### Navegación y exploración
| Comando | Función |
|---|---|
| `cd` | Cambiar de directorio |
| `ls` / `ls -la` | Listar archivos (incluyendo ocultos y detalles) |
| `pwd` | Mostrar el directorio actual |

### Gestión de archivos y carpetas
| Comando | Función |
|---|---|
| `mkdir` | Crear un directorio nuevo |
| `touch` | Crear un archivo vacío |
| `rm` | Eliminar archivos |
| `rm -rf` | Eliminar directorios completos de forma forzada y recursiva (usar con precaución) |
| `mv` | Mover o renombrar archivos/carpetas |
| `cp` | Copiar archivos o carpetas |

### Edición y visualización de contenido
| Comando | Función |
|---|---|
| `nano` | Editor de texto simple en terminal |
| `cat` | Mostrar el contenido de un archivo |
| `echo` | Imprimir texto en pantalla, o redirigir a un archivo (`echo "texto" >> archivo`) |

### Permisos y administración
| Comando | Función |
|---|---|
| `sudo` | Ejecutar un comando con privilegios de administrador |
| `apt` | Gestor de paquetes de Ubuntu/Debian (instalar, actualizar, eliminar software) |
| `apt search` | Buscar un paquete disponible en los repositorios |

### Enlaces simbólicos
| Comando | Función |
|---|---|
| `ln -s` | Crear un enlace simbólico (usado para los alias de python/pip) |

#
