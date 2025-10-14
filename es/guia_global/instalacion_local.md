# 💻 Instalación Local de Elixir y Livebook

## 🎯 Introducción

Esta guía te ayudará a instalar **Elixir** y **Livebook** directamente en tu computadora. Esta es la opción recomendada porque ofrece el mejor rendimiento y es ideal para uso a largo plazo.

## 📋 Requisitos Previos

- Computadora con Windows, macOS o Linux
- Conexión a internet para la instalación
- Aproximadamente 1 GB de espacio libre en disco
- Permisos de administrador en el sistema

## 🪟 Instalación en Windows

### Paso 1: Instalar Elixir

#### Opción A: Usando el Instalador Oficial (Recomendado)

1. **Descarga el instalador:**
   - Ve a https://elixir-lang.org/install.html
   - Busca la sección de Windows
   - Descarga el instalador `.exe` desde el enlace a Elixir Installer

2. **Ejecuta el instalador:**
   - Haz doble clic en el archivo descargado
   - Sigue las instrucciones del asistente
   - Acepta la ubicación por defecto
   - Espera a que termine la instalación

3. **Verifica la instalación:**
   - Abre el "Símbolo del sistema" (cmd) o PowerShell
   - Escribe: `elixir --version`
   - Deberías ver algo como: `Elixir 1.16.x (compiled with Erlang/OTP 26)`

#### Opción B: Usando Chocolatey

Si ya tienes Chocolatey instalado:

```powershell
choco install elixir
```

### Paso 2: Instalar Livebook en Windows

1. **Descarga Livebook Desktop:**
   - Ve a https://livebook.dev/#install
   - Descarga la versión para Windows (.exe)

2. **Instala Livebook:**
   - Ejecuta el instalador descargado
   - Sigue las instrucciones
   - Se creará un acceso directo en el escritorio

3. **Inicia Livebook:**
   - Haz doble clic en el icono de Livebook
   - Se abrirá automáticamente en tu navegador
   - ¡Ya puedes empezar a usar Livebook!

## 🍎 Instalación en macOS

### Paso 1: Instalar Homebrew (si no lo tienes)

Homebrew es un gestor de paquetes para macOS que facilita la instalación.

1. **Abre Terminal** (busca "Terminal" en Spotlight)

2. **Instala Homebrew:**
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

3. **Sigue las instrucciones** que aparecen en pantalla

### Paso 2: Instalar Elixir

```bash
brew install elixir
```

### Paso 3: Verifica la instalación

```bash
elixir --version
```

Deberías ver información sobre la versión de Elixir y Erlang.

### Paso 4: Instalar Livebook

#### Opción A: Livebook Desktop (Recomendado)

1. Ve a https://livebook.dev/#install
2. Descarga la versión para macOS (.dmg)
3. Abre el archivo descargado
4. Arrastra Livebook a la carpeta Aplicaciones
5. Abre Livebook desde Aplicaciones
6. La primera vez, haz clic derecho → Abrir (debido a permisos de seguridad)

#### Opción B: Usando Elixir directamente

```bash
mix do local.rebar --force, local.hex --force
mix escript.install hex livebook
```

Para ejecutar Livebook:
```bash
livebook server
```

## 🐧 Instalación en Linux

### Ubuntu/Debian

#### Paso 1: Agregar el repositorio de Erlang Solutions

```bash
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i erlang-solutions_2.0_all.deb
sudo apt-get update
```

#### Paso 2: Instalar Elixir

```bash
sudo apt-get install elixir
```

#### Paso 3: Verificar

```bash
elixir --version
```

### Fedora/CentOS/RHEL

```bash
sudo dnf install elixir
```

### Arch Linux

```bash
sudo pacman -S elixir
```

### Instalación de Livebook en Linux

#### Opción A: Livebook Desktop

1. Ve a https://livebook.dev/#install
2. Descarga la versión para Linux (.AppImage)
3. Haz el archivo ejecutable:
   ```bash
   chmod +x Livebook-*.AppImage
   ```
4. Ejecuta el archivo:
   ```bash
   ./Livebook-*.AppImage
   ```

#### Opción B: Usando Mix

```bash
mix do local.rebar --force, local.hex --force
mix escript.install hex livebook
```

Asegúrate de que `~/.mix/escripts` esté en tu PATH:

```bash
export PATH="$PATH:$HOME/.mix/escripts"
```

Para ejecutar:
```bash
livebook server
```

## ✅ Verificación de la Instalación

### Probar Elixir

1. Abre una terminal/consola
2. Ejecuta:
   ```bash
   iex
   ```
3. Deberías ver algo como:
   ```
   Erlang/OTP 26 [erts-14.2] [source] [64-bit] [smp:8:8]
   
   Interactive Elixir (1.16.0) - press Ctrl+C to exit
   iex(1)>
   ```
4. Prueba escribir:
   ```elixir
   IO.puts("¡Hola, mundo!")
   ```
5. Para salir, presiona `Ctrl+C` dos veces

### Probar Livebook

1. Abre Livebook (icono de escritorio o ejecutando `livebook server`)
2. Se abrirá una ventana del navegador
3. Haz clic en "New notebook"
4. Escribe en la primera celda:
   ```elixir
   IO.puts("¡Mi primer código en Livebook!")
   ```
5. Presiona el botón de "Evaluate" o usa `Ctrl+Enter`
6. Deberías ver el mensaje en la salida

## 🎨 Configuración Inicial de Livebook

### Primera vez que abres Livebook

1. **Pantalla de bienvenida:**
   - Verás una interfaz limpia con opciones para crear notebooks
   - Familiarízate con la interfaz

2. **Crear una carpeta para el curso:**
   - En tu sistema, crea una carpeta llamada `ElixirKidsCourse`
   - Dentro de Livebook, usa "Open" para navegar a esa carpeta
   - Guarda los notebooks del curso aquí

3. **Instalar Kino (necesario para Niveles 1-3):**
   - Abre un nuevo notebook
   - En la primera celda, escribe:
     ```elixir
     Mix.install([
       {:kino, "~> 0.12.0"}
     ])
     ```
   - Ejecuta la celda
   - Kino se instalará automáticamente

### Atajos de Teclado Útiles en Livebook

- `Ctrl + Enter` o `Cmd + Enter`: Ejecutar celda actual
- `Shift + Enter`: Ejecutar celda y mover a la siguiente
- `Ctrl + S` o `Cmd + S`: Guardar notebook
- `Escape`: Salir del modo edición
- `Enter`: Entrar en modo edición

## 🔧 Solución de Problemas Comunes

### "elixir no es reconocido como comando"

**Problema:** El sistema no encuentra Elixir después de instalarlo.

**Solución:**
1. Cierra y vuelve a abrir la terminal
2. Verifica que Elixir esté en el PATH:
   - Windows: Busca "Variables de entorno" en el menú Inicio
   - macOS/Linux: Verifica el archivo `.bashrc` o `.zshrc`

### Livebook no abre en el navegador

**Problema:** Al ejecutar Livebook, no se abre el navegador automáticamente.

**Solución:**
1. Busca en la terminal un mensaje como: `Access Livebook at http://localhost:8080/...`
2. Copia esa URL completa
3. Ábrela manualmente en tu navegador

### Error "Mix is not available"

**Problema:** Al intentar instalar paquetes, aparece este error.

**Solución:**
```bash
mix local.hex --force
mix local.rebar --force
```

### Livebook se cierra inesperadamente

**Problema:** Livebook Desktop se cierra solo.

**Solución:**
1. Verifica que tengas suficiente memoria RAM disponible (mínimo 2GB libres)
2. Cierra otros programas que consuman muchos recursos
3. Intenta ejecutar Livebook desde terminal para ver mensajes de error

### Errores de permisos en Linux/macOS

**Problema:** Mensajes de "Permission denied" al instalar.

**Solución:**
- No uses `sudo` para instalar paquetes de Elixir con Mix
- Si es necesario, cambia los permisos de tu directorio home:
  ```bash
  sudo chown -R $USER ~/.mix
  ```

### No aparecen los botones interactivos de Kino

**Problema:** Los ejemplos con Kino no muestran elementos visuales.

**Solución:**
1. Asegúrate de haber ejecutado `Mix.install([{:kino, "~> 0.12.0"}])` al inicio del notebook
2. Reinicia el runtime: En Livebook, ve a "Runtime" → "Reconnect"
3. Vuelve a ejecutar todas las celdas desde el inicio

## 🚀 Optimización y Mejoras

### Mejorar el rendimiento

1. **Aumentar la memoria disponible:**
   - Cierra aplicaciones no necesarias durante las sesiones
   - Considera aumentar la RAM del sistema si es muy lento

2. **Usar un SSD:**
   - Si tu computadora tiene disco duro tradicional, considera actualizar a SSD
   - Mejora significativamente la velocidad de carga

### Instalar extensiones útiles

#### VS Code con Elixir (opcional para Niveles 4-5)

Si quieres usar un editor de código avanzado:

1. Instala [Visual Studio Code](https://code.visualstudio.com/)
2. Instala las extensiones:
   - "ElixirLS"
   - "Elixir Formatter"
3. Configura ElixirLS siguiendo su documentación

## 📁 Organización Recomendada

Crea esta estructura en tu computadora:

```
Documentos/
└── ElixirKidsCourse/
    ├── nivel_1/
    │   ├── clase_01.livemd
    │   ├── clase_02.livemd
    │   └── ...
    ├── nivel_2/
    │   └── ...
    ├── proyectos/
    │   └── mis_creaciones/
    └── ejercicios_extra/
```

## 🔄 Actualización

### Actualizar Elixir

**Windows (con Chocolatey):**
```powershell
choco upgrade elixir
```

**macOS:**
```bash
brew upgrade elixir
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get update
sudo apt-get upgrade elixir
```

### Actualizar Livebook

#### Livebook Desktop:
1. Descarga la nueva versión desde https://livebook.dev
2. Instala sobre la versión anterior

#### Livebook desde Mix:
```bash
mix escript.install hex livebook --force
```

## 📞 Próximos Pasos

Una vez que tengas todo instalado y verificado:

1. ✅ Familiarízate con la interfaz de Livebook
2. ✅ Crea la estructura de carpetas para el curso
3. ✅ Descarga los notebooks del [Nivel 1](../nivel_1/README.md)
4. ✅ ¡Comienza la primera clase!

## 💡 Consejos Finales

- **Guarda frecuentemente:** Livebook autoguarda, pero usa `Ctrl+S` por costumbre
- **Experimenta sin miedo:** Puedes cerrar y reabrir notebooks sin perder el progreso guardado
- **Usa nombres descriptivos:** Nombra tus notebooks de forma clara
- **Consulta la [guía de troubleshooting](troubleshooting.md)** si encuentras problemas

---

**¿Listo para programar? ¡Vamos allá! 🚀**

