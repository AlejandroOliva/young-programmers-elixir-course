# 🐳 Configuración con Docker/Podman

## 🎯 Introducción

Docker (o Podman [[memory:8735666]]) proporciona una forma simple y portable de ejecutar Elixir y Livebook sin necesidad de instalar dependencias en tu sistema. Esta es una excelente opción si:

- Quieres un entorno aislado y reproducible
- Tienes dificultades con la instalación local
- Quieres probar el curso antes de instalarlo permanentemente
- Trabajas en múltiples computadoras

## 📋 Requisitos Previos

- Computadora con Windows, macOS o Linux
- Al menos 4 GB de RAM disponible
- 2-3 GB de espacio libre en disco
- Conexión a internet (solo para la primera configuración)

## 🔧 Instalación de Docker/Podman

### Opción A: Docker Desktop (Recomendado para principiantes)

#### Windows y macOS

1. **Descarga Docker Desktop:**
   - Ve a https://www.docker.com/products/docker-desktop
   - Descarga la versión para tu sistema operativo
   - Tamaño aproximado: 400-500 MB

2. **Instala Docker Desktop:**
   - Ejecuta el instalador descargado
   - Sigue las instrucciones del asistente
   - Reinicia la computadora si se solicita

3. **Inicia Docker Desktop:**
   - Abre la aplicación Docker Desktop
   - Acepta los términos de servicio
   - Espera a que Docker se inicie completamente (icono verde en la bandeja del sistema)

4. **Verifica la instalación:**
   - Abre una terminal/PowerShell
   - Ejecuta:
     ```bash
     docker --version
     ```
   - Deberías ver algo como: `Docker version 24.0.x`

#### Linux

```bash
# Ubuntu/Debian
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER
# Cierra sesión y vuelve a iniciar para aplicar cambios

# Fedora
sudo dnf install docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
sudo usermod -aG docker $USER

# Arch Linux
sudo pacman -S docker
sudo systemctl start docker
sudo usermod -aG docker $USER
```

### Opción B: Podman (Alternativa open-source)

Podman es una alternativa compatible con Docker, sin daemon y con mejor seguridad.

#### Linux

```bash
# Ubuntu/Debian
sudo apt-get install podman

# Fedora (viene preinstalado en versiones recientes)
sudo dnf install podman

# Arch Linux
sudo pacman -S podman
```

#### macOS

```bash
brew install podman
podman machine init
podman machine start
```

#### Windows

1. Descarga desde: https://github.com/containers/podman/releases
2. Instala el archivo `.msi`
3. Abre PowerShell y ejecuta:
   ```powershell
   podman machine init
   podman machine start
   ```

**Nota:** En el resto de esta guía, si usas Podman, simplemente reemplaza `docker` por `podman` en todos los comandos.

## 🚀 Configuración de Livebook con Docker

### Método 1: Usar la Imagen Oficial de Livebook (Más simple)

#### Ejecutar Livebook

```bash
docker run -p 8080:8080 -p 8081:8081 --pull always \
  -v $(pwd):/data \
  livebook/livebook
```

**En Windows PowerShell:**
```powershell
docker run -p 8080:8080 -p 8081:8081 --pull always -v ${PWD}:/data livebook/livebook
```

**Explicación de los parámetros:**
- `-p 8080:8080`: Expone el puerto de Livebook
- `-p 8081:8081`: Puerto adicional para comunicación
- `--pull always`: Asegura tener la última versión
- `-v $(pwd):/data`: Monta tu directorio actual para guardar notebooks
- `livebook/livebook`: La imagen oficial

#### Acceder a Livebook

1. Después de ejecutar el comando, verás un mensaje en la terminal
2. Busca una línea como: `Access Livebook at http://localhost:8080/?token=...`
3. Copia esa URL completa
4. Ábrela en tu navegador
5. ¡Ya puedes usar Livebook!

#### Detener Livebook

- Presiona `Ctrl + C` en la terminal

### Método 2: Docker Compose (Recomendado para uso frecuente)

#### Crear archivo de configuración

1. Crea una carpeta para el curso:
   ```bash
   mkdir ElixirKidsCourse
   cd ElixirKidsCourse
   ```

2. Crea un archivo llamado `docker-compose.yml`:

```yaml
version: '3.8'

services:
  livebook:
    image: livebook/livebook:latest
    ports:
      - "8080:8080"
      - "8081:8081"
    environment:
      - LIVEBOOK_PASSWORD=elixirkids
      - LIVEBOOK_HOME=/data
    volumes:
      - ./notebooks:/data
    restart: unless-stopped
```

3. Crea la carpeta para notebooks:
   ```bash
   mkdir notebooks
   ```

#### Iniciar Livebook

```bash
docker-compose up -d
```

El parámetro `-d` ejecuta Livebook en segundo plano.

#### Acceder a Livebook

1. Abre tu navegador
2. Ve a: http://localhost:8080
3. Ingresa la contraseña: `elixirkids`
4. ¡Listo para programar!

#### Comandos útiles

```bash
# Ver logs
docker-compose logs -f

# Detener Livebook
docker-compose down

# Reiniciar Livebook
docker-compose restart

# Ver estado
docker-compose ps
```

## 🎨 Configuración Personalizada

### Cambiar el puerto

Si el puerto 8080 ya está en uso, modifica el archivo `docker-compose.yml`:

```yaml
ports:
  - "9090:8080"  # Cambia 9090 por el puerto que prefieras
  - "9091:8081"
```

Luego accede a: http://localhost:9090

### Configurar memoria

Si Livebook necesita más memoria:

```yaml
services:
  livebook:
    # ... configuración anterior ...
    deploy:
      resources:
        limits:
          memory: 2G
        reservations:
          memory: 1G
```

### Persistir datos

Para asegurar que tus notebooks no se pierdan:

```yaml
volumes:
  - ./notebooks:/data  # Notebooks y archivos
  - livebook_deps:/root/.mix  # Dependencias de Elixir
  
volumes:
  livebook_deps:
```

## 🔍 Verificación

### Probar que funciona

1. Accede a Livebook en tu navegador
2. Haz clic en "New notebook"
3. Escribe en la primera celda:
   ```elixir
   IO.puts("¡Docker funciona perfectamente!")
   System.version()
   ```
4. Presiona "Evaluate" o `Ctrl+Enter`
5. Deberías ver el mensaje y la versión de Elixir

### Probar Kino

En una nueva celda:

```elixir
Mix.install([
  {:kino, "~> 0.12.0"}
])

Kino.Input.text("¿Cómo te llamas?")
```

Si ves un campo de texto interactivo, ¡todo funciona correctamente!

## 🛠️ Script de Inicio Rápido

### Para Linux/macOS

Crea un archivo `start-livebook.sh`:

```bash
#!/bin/bash

# Colores para output
GREEN='\033[0;32m'
BLUE='\033[0;34m'
NC='\033[0m' # No Color

echo -e "${BLUE}🚀 Iniciando Livebook...${NC}"

# Verificar si Docker está corriendo
if ! docker info > /dev/null 2>&1; then
    echo "Error: Docker no está corriendo. Por favor, inicia Docker Desktop."
    exit 1
fi

# Crear directorio de notebooks si no existe
mkdir -p notebooks

# Iniciar Livebook
docker run -d \
  --name elixir-kids-livebook \
  -p 8080:8080 \
  -p 8081:8081 \
  -e LIVEBOOK_PASSWORD=elixirkids \
  -v $(pwd)/notebooks:/data \
  livebook/livebook:latest

echo -e "${GREEN}✅ Livebook iniciado correctamente${NC}"
echo -e "📱 Accede en: ${BLUE}http://localhost:8080${NC}"
echo -e "🔑 Contraseña: elixirkids"
echo ""
echo "Para detener Livebook, ejecuta: docker stop elixir-kids-livebook"
```

Hazlo ejecutable:
```bash
chmod +x start-livebook.sh
./start-livebook.sh
```

### Para Windows

Crea un archivo `start-livebook.bat`:

```batch
@echo off
echo Iniciando Livebook...

REM Verificar si Docker está corriendo
docker info >nul 2>&1
if errorlevel 1 (
    echo Error: Docker no esta corriendo. Por favor, inicia Docker Desktop.
    pause
    exit /b 1
)

REM Crear directorio de notebooks
if not exist notebooks mkdir notebooks

REM Iniciar Livebook
docker run -d ^
  --name elixir-kids-livebook ^
  -p 8080:8080 ^
  -p 8081:8081 ^
  -e LIVEBOOK_PASSWORD=elixirkids ^
  -v %cd%/notebooks:/data ^
  livebook/livebook:latest

echo Livebook iniciado correctamente
echo Accede en: http://localhost:8080
echo Contrasena: elixirkids
echo.
echo Para detener Livebook, ejecuta: docker stop elixir-kids-livebook
pause
```

Ejecuta haciendo doble clic en el archivo.

## 🔄 Actualización

### Actualizar la imagen de Livebook

```bash
docker pull livebook/livebook:latest
```

O con docker-compose:
```bash
docker-compose pull
docker-compose up -d
```

## 🚧 Solución de Problemas

### Docker Desktop no inicia

**Problema:** Docker Desktop se queda cargando.

**Solución:**
1. Reinicia la computadora
2. Desactiva temporalmente el antivirus
3. En Windows, verifica que la virtualización esté habilitada en la BIOS

### Puerto 8080 ya en uso

**Problema:** Error "port is already allocated"

**Solución:**
```bash
# Ver qué usa el puerto
# Linux/macOS
lsof -i :8080

# Windows
netstat -ano | findstr :8080

# Cambiar el puerto en docker-compose.yml o usar:
docker run -p 9090:8080 ... livebook/livebook
```

### No puedo acceder a Livebook

**Problema:** El navegador no carga localhost:8080

**Solución:**
1. Verifica que el contenedor está corriendo:
   ```bash
   docker ps
   ```
2. Verifica los logs:
   ```bash
   docker logs elixir-kids-livebook
   ```
3. Intenta acceder a: http://127.0.0.1:8080

### Los notebooks no se guardan

**Problema:** Al reiniciar Docker, los notebooks desaparecen.

**Solución:**
Asegúrate de usar el parámetro `-v`:
```bash
-v $(pwd)/notebooks:/data
```

Verifica que la carpeta `notebooks` existe en tu directorio actual.

### Error "Cannot connect to Docker daemon"

**Problema:** Docker no responde.

**Solución:**
- **Linux:** `sudo systemctl start docker`
- **macOS/Windows:** Inicia Docker Desktop manualmente

### Livebook muy lento

**Problema:** El rendimiento es bajo.

**Solución:**
1. Asigna más recursos a Docker:
   - Docker Desktop → Settings → Resources
   - Aumenta CPU y memoria (mínimo 2 CPU, 4GB RAM)
2. Cierra otros contenedores:
   ```bash
   docker ps
   docker stop <contenedor-no-necesario>
   ```

## 💡 Ventajas de usar Docker

✅ **Aislamiento:** No interfiere con otras instalaciones en tu sistema

✅ **Portabilidad:** Funciona igual en Windows, macOS y Linux

✅ **Simplicidad:** No requiere instalar dependencias manualmente

✅ **Reproducibilidad:** Mismo entorno para todos los estudiantes

✅ **Fácil de limpiar:** Eliminar el contenedor limpia todo

## ⚠️ Consideraciones

❗ **Rendimiento:** Ligeramente más lento que instalación nativa

❗ **Recursos:** Requiere Docker Desktop corriendo (usa memoria)

❗ **Complejidad inicial:** Curva de aprendizaje para entender Docker

❗ **Actualización:** Hay que actualizar la imagen manualmente

## 📁 Organización Recomendada

```
ElixirKidsCourse/
├── docker-compose.yml
├── start-livebook.sh (o .bat)
└── notebooks/
    ├── nivel_1/
    ├── nivel_2/
    ├── nivel_3/
    ├── mis_proyectos/
    └── ejercicios_extra/
```

## 🔄 Backup de Notebooks

### Copia de seguridad manual

```bash
# Copiar todos los notebooks
cp -r notebooks notebooks-backup-$(date +%Y%m%d)
```

### Backup automático

Agrega esto al `docker-compose.yml`:

```yaml
services:
  livebook:
    # ... configuración anterior ...
    volumes:
      - ./notebooks:/data
      - ./backups:/backups
```

## 📞 Próximos Pasos

1. ✅ Verifica que Docker/Livebook funciona correctamente
2. ✅ Crea la estructura de carpetas para los notebooks
3. ✅ Descarga los notebooks del [Nivel 1](../nivel_1/README.md)
4. ✅ Configura backups automáticos
5. ✅ ¡Comienza a programar!

## 🎓 Recursos Adicionales

- [Documentación oficial de Docker](https://docs.docker.com/)
- [Documentación de Livebook](https://hexdocs.pm/livebook/)
- [Podman Documentation](https://docs.podman.io/)

---

**¡Listo para programar con Docker! 🐳🚀**

