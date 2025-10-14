# 🖥️ Configuración con Máquina Virtual

## 🎯 Introducción

Una máquina virtual (VM) proporciona un entorno completamente aislado para ejecutar Elixir y Livebook. Esta opción es ideal si:

- Quieres un entorno dedicado sin tocar tu sistema operativo principal
- Necesitas replicar el mismo entorno en múltiples computadoras
- Quieres experimentar sin riesgo de afectar tu sistema
- Trabajas en un entorno educativo con múltiples estudiantes

## 📋 Requisitos Previos

- Computadora con al menos 8 GB de RAM (para asignar 2-4 GB a la VM)
- 20-30 GB de espacio libre en disco
- Procesador con soporte de virtualización (Intel VT-x o AMD-V)
- Sistema operativo host: Windows, macOS o Linux

## 🛠️ Herramientas de Virtualización

### Opción A: VirtualBox (Recomendado - Gratuito)

**Ventajas:**
- ✅ Gratuito y open-source
- ✅ Funciona en Windows, macOS y Linux
- ✅ Interfaz amigable
- ✅ Bien documentado

### Opción B: VMware Workstation Player (Windows/Linux)

**Ventajas:**
- ✅ Mejor rendimiento
- ✅ Versión gratuita para uso personal
- ✅ Integración más fluida

### Opción C: VMware Fusion (macOS)

**Ventajas:**
- ✅ Optimizado para macOS
- ✅ Excelente rendimiento
- ⚠️ De pago (con trial gratuito)

## 📥 Instalación de VirtualBox

### Paso 1: Descargar e Instalar VirtualBox

1. **Descarga VirtualBox:**
   - Ve a https://www.virtualbox.org/wiki/Downloads
   - Descarga la versión para tu sistema operativo
   - Tamaño aproximado: 100-150 MB

2. **Instala VirtualBox:**
   - Ejecuta el instalador descargado
   - Sigue las instrucciones del asistente
   - Acepta la instalación de los drivers de red si se solicita
   - Reinicia si es necesario

3. **Verifica la instalación:**
   - Abre VirtualBox
   - Deberías ver la interfaz principal

### Paso 2: Habilitar Virtualización en BIOS

Si VirtualBox muestra errores sobre virtualización:

1. **Reinicia tu computadora**
2. **Entra a la BIOS/UEFI:**
   - Presiona F2, F10, F12, o DEL durante el arranque (depende del fabricante)
3. **Busca opciones de virtualización:**
   - Intel: "Intel VT-x" o "Intel Virtualization Technology"
   - AMD: "AMD-V" o "SVM Mode"
4. **Habilita la opción**
5. **Guarda y sal (F10)**

## 💿 Crear la Máquina Virtual

### Opción 1: Usar Ubuntu (Recomendado para principiantes)

#### Descargar Ubuntu

1. Ve a https://ubuntu.com/download/desktop
2. Descarga Ubuntu 22.04 LTS (versión estable)
3. Tamaño: ~4 GB

#### Crear la VM en VirtualBox

1. **Abre VirtualBox**
2. **Clic en "Nueva" (New)**
3. **Configura:**
   - **Nombre:** ElixirKids
   - **Tipo:** Linux
   - **Versión:** Ubuntu (64-bit)
   - **Clic en "Siguiente"**

4. **Memoria RAM:**
   - Asigna **2048 MB (2 GB)** mínimo
   - Recomendado: **4096 MB (4 GB)**
   - No asignes más del 50% de tu RAM total

5. **Disco duro:**
   - Selecciona "Crear un disco duro virtual ahora"
   - Clic en "Crear"
   - Tipo: **VDI (VirtualBox Disk Image)**
   - Almacenamiento: **Dinámicamente asignado**
   - Tamaño: **20 GB** mínimo, **30 GB** recomendado

6. **Clic en "Crear"**

#### Configurar la VM

1. **Selecciona la VM "ElixirKids"**
2. **Clic en "Configuración"**
3. **Sistema:**
   - **Procesador:** Asigna 2 CPUs mínimo
   - **Habilitar PAE/NX**
   - **Habilitar Nested VT-x/AMD-V** (si está disponible)

4. **Pantalla:**
   - **Memoria de video:** 128 MB
   - **Habilitar aceleración 3D**

5. **Almacenamiento:**
   - Clic en el icono de CD (vacío)
   - Clic en el icono de disco azul a la derecha
   - Selecciona "Elegir archivo de disco..."
   - Selecciona el archivo ISO de Ubuntu descargado

6. **Red:**
   - **Adaptador 1:** NAT (por defecto)

7. **Clic en "Aceptar"**

#### Instalar Ubuntu

1. **Selecciona la VM "ElixirKids"**
2. **Clic en "Iniciar"**
3. **Instalación de Ubuntu:**
   - Idioma: Español (o el que prefieras)
   - Clic en "Instalar Ubuntu"
   - Distribución del teclado: Selecciona la tuya
   - Actualizaciones: "Instalación normal"
   - ✅ Descargar actualizaciones
   - ✅ Instalar software de terceros
   - Tipo de instalación: "Borrar disco e instalar Ubuntu"
   - **No te preocupes, solo afecta la VM, no tu computadora real**
   - Zona horaria: Selecciona la tuya
   - Crea tu usuario:
     - Nombre: Tu nombre
     - Usuario: elixirkids
     - Contraseña: (algo simple como "elixir123")

4. **Espera a que termine la instalación** (10-20 minutos)
5. **Reinicia cuando se solicite**
6. **Quita el ISO:**
   - En VirtualBox, Dispositivos → Unidades ópticas → Quitar disco

### Opción 2: Usar Linux Mint (Alternativa amigable)

Similar a Ubuntu pero con interfaz más similar a Windows.

1. Descarga desde: https://linuxmint.com/download.php
2. Sigue los mismos pasos que Ubuntu

## 📦 Instalar Elixir y Livebook en la VM

Una vez que tengas Ubuntu corriendo:

### Paso 1: Actualizar el Sistema

Abre la terminal (Ctrl+Alt+T) y ejecuta:

```bash
sudo apt update
sudo apt upgrade -y
```

### Paso 2: Instalar Elixir

```bash
# Agregar repositorio de Erlang Solutions
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i erlang-solutions_2.0_all.deb
sudo apt update

# Instalar Elixir
sudo apt install elixir -y
```

### Paso 3: Verificar Instalación

```bash
elixir --version
```

Deberías ver información sobre Elixir y Erlang.

### Paso 4: Instalar Livebook

```bash
# Instalar dependencias
mix local.hex --force
mix local.rebar --force

# Instalar Livebook
mix escript.install hex livebook

# Agregar al PATH
echo 'export PATH="$PATH:$HOME/.mix/escripts"' >> ~/.bashrc
source ~/.bashrc
```

### Paso 5: Crear Script de Inicio

```bash
# Crear archivo de inicio
cat > ~/start-livebook.sh << 'EOF'
#!/bin/bash
echo "🚀 Iniciando Livebook..."
livebook server --ip 0.0.0.0
EOF

# Hacerlo ejecutable
chmod +x ~/start-livebook.sh
```

### Paso 6: Probar Livebook

```bash
~/start-livebook.sh
```

Abre Firefox dentro de la VM y ve a: http://localhost:8080

## 🔧 Guest Additions (Recomendado)

Mejora la integración entre tu sistema y la VM:

### Instalar VirtualBox Guest Additions

1. **Con la VM corriendo, en el menú de VirtualBox:**
   - Dispositivos → Insertar imagen de CD de las Guest Additions

2. **En la VM, abre terminal:**
   ```bash
   sudo apt install build-essential dkms linux-headers-$(uname -r)
   cd /media/*/VBox*
   sudo ./VBoxLinuxAdditions.run
   ```

3. **Reinicia la VM:**
   ```bash
   sudo reboot
   ```

### Funciones Habilitadas

✅ **Portapapeles compartido:** Copiar/pegar entre host y VM

✅ **Carpetas compartidas:** Acceder archivos del host desde la VM

✅ **Mejor resolución:** Pantalla completa y redimensionable

✅ **Drag & Drop:** Arrastrar archivos entre host y VM

### Configurar Carpeta Compartida

1. **En VirtualBox (con VM apagada):**
   - Configuración → Carpetas compartidas
   - Clic en el icono de agregar carpeta
   - Ruta: Selecciona una carpeta en tu host (ej: `C:\ElixirKidsCourse`)
   - Nombre: `ElixirKids`
   - ✅ Auto-montar
   - ✅ Hacer permanente

2. **En la VM (después de iniciar):**
   ```bash
   sudo usermod -aG vboxsf $(whoami)
   ```

3. **Reinicia la VM**

4. **Accede a la carpeta compartida:**
   ```bash
   cd /media/sf_ElixirKids
   ```

## 🎨 Optimización

### Mejorar Rendimiento

1. **Más CPUs:**
   - Configuración → Sistema → Procesador → 2-4 CPUs

2. **Más RAM:**
   - Configuración → Sistema → Memoria → 4 GB si es posible

3. **Aceleración 3D:**
   - Configuración → Pantalla → ✅ Habilitar aceleración 3D

### Snapshots (Puntos de Restauración)

Crea snapshots antes de cambios importantes:

1. **Con la VM apagada:**
   - Clic derecho en la VM → Instantáneas
   - Clic en "Tomar" instantánea
   - Nombre: "Elixir Instalado" o "Estado Limpio"

2. **Para restaurar:**
   - Selecciona la instantánea
   - Clic en "Restaurar"

## 🚧 Solución de Problemas

### La VM está muy lenta

**Solución:**
1. Asigna más RAM (mínimo 2 GB, recomendado 4 GB)
2. Asigna más CPUs (2-4)
3. Habilita aceleración 3D
4. Instala Guest Additions
5. Cierra programas del host que consuman recursos

### Error de virtualización

**Solución:**
1. Habilita VT-x/AMD-V en BIOS
2. En Windows, desactiva Hyper-V:
   ```powershell
   bcdedit /set hypervisorlaunchtype off
   ```
3. Reinicia la computadora

### No puedo copiar/pegar

**Solución:**
1. Instala Guest Additions
2. Dispositivos → Portapapeles compartido → Bidireccional
3. Reinicia la VM

### La pantalla está muy pequeña

**Solución:**
1. Instala Guest Additions
2. Ver → Pantalla completa (Host+F)
3. Ver → Escala al modo ventana
4. En Ubuntu: Configuración → Pantalla → Ajustar resolución

### No hay internet en la VM

**Solución:**
1. Configuración → Red → Adaptador 1 → NAT
2. Reinicia la VM
3. En la VM:
   ```bash
   sudo systemctl restart NetworkManager
   ```

## 📸 Exportar/Importar VM

### Exportar la VM (para compartir)

1. **Con la VM apagada:**
   - Archivo → Exportar servicio virtualizado
   - Selecciona "ElixirKids"
   - Formato: OVA
   - Ubicación y nombre del archivo
   - Clic en "Exportar"

2. **Compartir:**
   - El archivo .ova puede copiarse a USB o subirse a la nube
   - Otros pueden importarlo en su VirtualBox

### Importar VM

1. **Archivo → Importar servicio virtualizado**
2. **Selecciona el archivo .ova**
3. **Ajusta configuración si es necesario**
4. **Clic en "Importar"**

## 💡 Ventajas de Usar VM

✅ **Aislamiento total:** No afecta tu sistema principal

✅ **Snapshots:** Puedes volver atrás si algo sale mal

✅ **Portabilidad:** Exporta/importa en diferentes computadoras

✅ **Entorno consistente:** Mismo setup para todos los estudiantes

✅ **Seguridad:** Experimenta sin riesgos

## ⚠️ Consideraciones

❗ **Recursos:** Requiere RAM y CPU dedicadas

❗ **Rendimiento:** Más lento que instalación nativa

❗ **Complejidad:** Más pasos de configuración inicial

❗ **Espacio:** Ocupa 20-30 GB de disco

## 📁 Organización Recomendada

Dentro de la VM:

```
/home/elixirkids/
├── ElixirKidsCourse/
│   ├── nivel_1/
│   ├── nivel_2/
│   ├── nivel_3/
│   ├── nivel_4/
│   ├── nivel_5/
│   └── mis_proyectos/
└── start-livebook.sh
```

## 🔄 Backup

### Backup de Notebooks

Usa la carpeta compartida para guardar notebooks en tu host automáticamente.

### Backup de toda la VM

1. **Exporta la VM** como .ova periódicamente
2. **O copia el archivo .vdi:**
   - Ubicación en Windows: `C:\Users\<usuario>\VirtualBox VMs\ElixirKids\`
   - Ubicación en macOS: `~/VirtualBox VMs/ElixirKids/`
   - Ubicación en Linux: `~/VirtualBox VMs/ElixirKids/`

## 📞 Próximos Pasos

1. ✅ Verifica que Elixir y Livebook funcionan
2. ✅ Configura Guest Additions y carpeta compartida
3. ✅ Crea un snapshot del estado limpio
4. ✅ Descarga los notebooks del [Nivel 1](../nivel_1/README.md)
5. ✅ ¡Comienza a programar!

## 🎓 Recursos Adicionales

- [Documentación de VirtualBox](https://www.virtualbox.org/manual/)
- [Guía de Ubuntu](https://help.ubuntu.com/)
- [VMware Workstation Player](https://www.vmware.com/products/workstation-player.html)

---

**¡Tu entorno virtual está listo! 🖥️🚀**

