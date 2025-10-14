# 🥧 Configuración en Raspberry Pi

## 🎯 Introducción

Una Raspberry Pi es una pequeña computadora de bajo costo perfecta para crear un **laboratorio educativo dedicado** a la programación. Esta opción es ideal si:

- Quieres un dispositivo dedicado exclusivamente para programar
- Trabajas con varios niños (en casa o aula)
- Buscas una solución económica y portable
- Quieres enseñar también sobre hardware y Linux
- Deseas un entorno controlado y sin distracciones

## 📋 ¿Qué Raspberry Pi Necesito?

### Modelos Recomendados

| Modelo | RAM | Rendimiento | Precio aprox. |
|--------|-----|-------------|---------------|
| **Raspberry Pi 4B (4GB)** | 4 GB | ⭐⭐⭐⭐⭐ Excelente | $55-75 USD |
| **Raspberry Pi 4B (2GB)** | 2 GB | ⭐⭐⭐⭐ Bueno | $35-45 USD |
| **Raspberry Pi 5** | 4/8 GB | ⭐⭐⭐⭐⭐ Mejor | $60-80 USD |
| Raspberry Pi 3B+ | 1 GB | ⭐⭐⭐ Funcional | $35 USD |

**Recomendación:** Raspberry Pi 4B con 4GB de RAM para mejor experiencia.

### Kit Completo Necesario

Para empezar necesitas:

**Esenciales:**
- ✅ Raspberry Pi (modelo recomendado arriba)
- ✅ Tarjeta microSD (32 GB mínimo, Clase 10 o mejor)
- ✅ Fuente de alimentación oficial (5V 3A para Pi 4)
- ✅ Cable HDMI (micro-HDMI para Pi 4/5)
- ✅ Teclado USB
- ✅ Mouse USB
- ✅ Monitor con entrada HDMI

**Opcionales pero recomendados:**
- 🔸 Carcasa/Case para proteger la Pi
- 🔸 Disipadores de calor
- 🔸 Ventilador (si usas cargas intensivas)
- 🔸 Cable Ethernet (mejor que WiFi para estabilidad)

**Costo total aproximado:** $100-150 USD con accesorios.

## 💿 Instalación del Sistema Operativo

### Opción 1: Raspberry Pi OS (Recomendado)

#### Paso 1: Descargar Raspberry Pi Imager

1. **En tu computadora principal:**
   - Ve a https://www.raspberrypi.com/software/
   - Descarga Raspberry Pi Imager para tu sistema operativo
   - Instala el programa

#### Paso 2: Preparar la Tarjeta SD

1. **Inserta la tarjeta microSD** en tu computadora (usa adaptador si es necesario)

2. **Abre Raspberry Pi Imager**

3. **Configura:**
   - **Raspberry Pi Device:** Selecciona tu modelo (ej: Raspberry Pi 4)
   - **Operating System:**
     - Raspberry Pi OS (64-bit) - Recomendado
     - O "Raspberry Pi OS (64-bit) Desktop" para interfaz gráfica completa
   - **Storage:** Selecciona tu tarjeta SD

4. **Configuración avanzada (importante):**
   - Clic en el icono de engranaje ⚙️
   - ✅ Establecer hostname: `elixirkids`
   - ✅ Habilitar SSH
   - ✅ Establecer nombre de usuario: `elixir` y contraseña (ej: `elixir123`)
   - ✅ Configurar WiFi (SSID y contraseña)
   - ✅ Establecer zona horaria y teclado
   - **Guardar configuración**

5. **Clic en "Write"**
   - Confirma (se borrarán los datos de la SD)
   - Espera 5-10 minutos

6. **Cuando termine, extrae la SD de forma segura**

#### Paso 3: Primer Arranque

1. **Inserta la tarjeta SD en la Raspberry Pi**
2. **Conecta:**
   - Monitor (HDMI)
   - Teclado y mouse (USB)
   - Ethernet (opcional pero recomendado)
   - Alimentación (último paso - se enciende automáticamente)

3. **Espera a que arranque** (primer arranque toma 2-3 minutos)

4. **Inicia sesión:**
   - Usuario: `elixir`
   - Contraseña: la que configuraste

5. **Completa el asistente de bienvenida** si aparece

### Opción 2: Ubuntu para Raspberry Pi

Si prefieres Ubuntu (más similar a instalación VM):

1. En Raspberry Pi Imager, selecciona:
   - **Operating System → Other general-purpose OS → Ubuntu**
   - Ubuntu Desktop 22.04 LTS (64-bit)
2. Sigue los mismos pasos de configuración

## 📦 Instalar Elixir y Livebook

### Paso 1: Actualizar el Sistema

Abre la terminal y ejecuta:

```bash
sudo apt update
sudo apt upgrade -y
```

Esto puede tomar 10-15 minutos en el primer arranque.

### Paso 2: Instalar Dependencias

```bash
sudo apt install -y curl git build-essential
```

### Paso 3: Instalar Erlang y Elixir

```bash
# Agregar repositorio de Erlang Solutions
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i erlang-solutions_2.0_all.deb
sudo apt update

# Instalar Erlang y Elixir
sudo apt install -y esl-erlang elixir
```

**Nota:** La instalación en Raspberry Pi puede tomar 15-20 minutos.

### Paso 4: Verificar Instalación

```bash
elixir --version
```

Deberías ver:
```
Erlang/OTP 26 [erts-14.x] [source] [64-bit] [smp:4:4]

Elixir 1.16.x (compiled with Erlang/OTP 26)
```

### Paso 5: Instalar Livebook

```bash
# Configurar Mix
mix local.hex --force
mix local.rebar --force

# Instalar Livebook
mix escript.install hex livebook

# Agregar al PATH
echo 'export PATH="$PATH:$HOME/.mix/escripts"' >> ~/.bashrc
source ~/.bashrc
```

### Paso 6: Crear Script de Inicio

```bash
# Crear directorio para el curso
mkdir -p ~/ElixirKidsCourse

# Crear script de inicio
cat > ~/start-livebook.sh << 'EOF'
#!/bin/bash

echo "🚀 Iniciando Livebook para Elixir Kids..."
echo "📱 Accede en el navegador a: http://localhost:8080"
echo "🛑 Para detener: Ctrl+C"
echo ""

cd ~/ElixirKidsCourse
livebook server --ip 0.0.0.0
EOF

# Hacerlo ejecutable
chmod +x ~/start-livebook.sh
```

### Paso 7: Crear Acceso Directo en Escritorio

```bash
cat > ~/Desktop/Livebook.desktop << 'EOF'
[Desktop Entry]
Version=1.0
Type=Application
Name=Livebook Elixir
Comment=Abrir Livebook para programar en Elixir
Exec=lxterminal -e /home/elixir/start-livebook.sh
Icon=/home/elixir/livebook-icon.png
Terminal=false
Categories=Development;Education;
EOF

chmod +x ~/Desktop/Livebook.desktop
```

## ✅ Probar la Instalación

### Iniciar Livebook

**Opción A: Desde escritorio**
- Doble clic en el icono "Livebook Elixir"

**Opción B: Desde terminal**
```bash
~/start-livebook.sh
```

### Acceder desde el Navegador

1. Abre Chromium (navegador de la Pi)
2. Ve a: `http://localhost:8080`
3. Ingresa el token que aparece en la terminal (si se solicita)

### Probar que Funciona

1. Clic en "New notebook"
2. Escribe en una celda:
   ```elixir
   IO.puts("¡Hola desde mi Raspberry Pi!")
   System.version()
   ```
3. Ejecuta con Ctrl+Enter

Si ves el mensaje y la versión de Elixir, ¡todo funciona! 🎉

## 🌐 Acceso desde Otros Dispositivos (Opcional)

### Configurar Acceso en Red Local

Esto permite que otros dispositivos en tu red (tablets, laptops) accedan a Livebook:

1. **Encuentra la IP de tu Raspberry Pi:**
   ```bash
   hostname -I
   ```
   Ejemplo: `192.168.1.100`

2. **Inicia Livebook con IP 0.0.0.0:**
   ```bash
   livebook server --ip 0.0.0.0
   ```

3. **Desde otro dispositivo en la misma red:**
   - Abre un navegador
   - Ve a: `http://192.168.1.100:8080`
   - Usa el token que muestra la terminal de la Pi

### Configurar Contraseña (Seguridad)

Para proteger el acceso:

```bash
# Editar el script de inicio
nano ~/start-livebook.sh

# Cambiar la última línea a:
livebook server --ip 0.0.0.0 --password elixirkids
```

Ahora para acceder necesitas la contraseña: `elixirkids`

## 🎨 Optimización para Raspberry Pi

### Ajustes de Rendimiento

#### 1. Overclock Seguro (Pi 4)

Edita el archivo de configuración:

```bash
sudo nano /boot/config.txt
```

Agrega al final:
```
# Overclock moderado
over_voltage=2
arm_freq=1750
```

Guarda (Ctrl+O, Enter) y sal (Ctrl+X). Reinicia:
```bash
sudo reboot
```

#### 2. Liberar Memoria

```bash
# Reducir memoria de GPU (si no usas gráficos pesados)
sudo nano /boot/config.txt

# Agrega:
gpu_mem=64
```

#### 3. Deshabilitar Servicios Innecesarios

```bash
# Deshabilitar Bluetooth si no lo usas
sudo systemctl disable bluetooth
sudo systemctl disable hciuart
```

### Mejorar la Experiencia Visual

```bash
# Instalar tipografías mejores
sudo apt install fonts-firacode fonts-roboto

# Ajustar apariencia
# Menú → Preferencias → Apariencia → Personalizar
```

## 🔧 Configuración Educativa

### Modo Kiosko (Solo Livebook)

Para que la Pi arranque directamente en Livebook (ideal para aulas):

1. **Crear script de autoarranque:**
   ```bash
   mkdir -p ~/.config/autostart
   
   cat > ~/.config/autostart/livebook.desktop << 'EOF'
   [Desktop Entry]
   Type=Application
   Name=Livebook Autostart
   Exec=/home/elixir/start-livebook.sh
   Terminal=true
   EOF
   ```

2. **Configurar navegador para abrir automáticamente:**
   ```bash
   cat > ~/.config/autostart/livebook-browser.desktop << 'EOF'
   [Desktop Entry]
   Type=Application
   Name=Livebook Browser
   Exec=/bin/bash -c "sleep 10 && chromium-browser --kiosk http://localhost:8080"
   EOF
   ```

### Control Parental

```bash
# Bloquear sitios distractivos
sudo nano /etc/hosts

# Agregar:
127.0.0.1 youtube.com
127.0.0.1 www.youtube.com
127.0.0.1 facebook.com
127.0.0.1 twitter.com
```

## 💾 Backup y Mantenimiento

### Backup de Notebooks

#### Opción 1: USB

```bash
# Insertar USB y copiar
cp -r ~/ElixirKidsCourse /media/elixir/NOMBRE_USB/backup-$(date +%Y%m%d)
```

#### Opción 2: Git (Recomendado)

```bash
cd ~/ElixirKidsCourse
git init
git add .
git commit -m "Backup de notebooks"

# Subir a GitHub (opcional)
git remote add origin https://github.com/tu-usuario/elixir-kids.git
git push -u origin main
```

### Backup de Imagen Completa de la SD

Desde tu computadora principal (no la Pi):

**Linux/macOS:**
```bash
# Insertar la SD en tu computadora
# Identificar el dispositivo (ej: /dev/sdb)
sudo fdisk -l

# Crear imagen
sudo dd if=/dev/sdb of=~/elixir-kids-backup.img bs=4M status=progress
```

**Windows:**
- Usa [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/)
- Read desde la SD a un archivo .img

### Restaurar desde Backup

Usa Raspberry Pi Imager o `dd` para escribir la imagen de vuelta a una SD.

## 🚧 Solución de Problemas

### La Pi no arranca

**Problema:** LED rojo encendido, pantalla negra.

**Solución:**
1. Verifica la fuente de alimentación (debe ser 5V 3A oficial)
2. Reescribe la imagen en la SD
3. Prueba con otra tarjeta SD (puede estar dañada)

### Livebook muy lento

**Problema:** La interfaz responde lentamente.

**Solución:**
1. Cierra pestañas innecesarias del navegador
2. Reinicia la Pi: `sudo reboot`
3. Aplica overclock (ver sección de optimización)
4. Usa una tarjeta SD más rápida (Clase 10 o UHS-I)

### No hay conexión WiFi

**Problema:** La Pi no se conecta a WiFi.

**Solución:**
```bash
# Reconfigurar WiFi
sudo raspi-config
# 1 System Options → S1 Wireless LAN → Ingresar SSID y contraseña

# O manualmente:
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

# Agregar:
network={
    ssid="TU_WIFI"
    psk="TU_CONTRASEÑA"
}

# Reiniciar servicio
sudo systemctl restart dhcpcd
```

### Temperatura alta

**Problema:** Advertencias de temperatura (>80°C).

**Solución:**
1. Instala disipadores de calor
2. Agrega un ventilador
3. Mejora la ventilación de la carcasa
4. Reduce el overclock

```bash
# Monitorear temperatura
vcgencmd measure_temp
```

### Error de espacio en disco

**Problema:** "No space left on device"

**Solución:**
```bash
# Ver uso de espacio
df -h

# Limpiar paquetes
sudo apt autoremove
sudo apt clean

# Expandir filesystem (si no se hizo automáticamente)
sudo raspi-config
# 6 Advanced Options → A1 Expand Filesystem
```

## 🎯 Configuración para Múltiples Estudiantes

### Crear Usuarios Individuales

```bash
# Crear usuario para cada estudiante
sudo adduser estudiante1
sudo adduser estudiante2

# Agregar al grupo necesario
sudo usermod -aG sudo estudiante1
```

### Escritorios Separados

Cada usuario tendrá su propio espacio y notebooks.

```bash
# Como cada usuario:
su - estudiante1
mkdir ~/ElixirKidsCourse
~/start-livebook.sh
```

## 💡 Ventajas de Usar Raspberry Pi

✅ **Dedicación:** Dispositivo solo para programar

✅ **Económico:** Inversión inicial baja ($100-150)

✅ **Portable:** Fácil de mover y transportar

✅ **Sin distracciones:** Entorno controlado

✅ **Educativo:** También aprenden sobre hardware y Linux

✅ **Múltiples usuarios:** Varios niños pueden compartirla

✅ **Durabilidad:** Resistente y fácil de reparar

## ⚠️ Consideraciones

❗ **Rendimiento:** Más lento que PC moderna (pero suficiente)

❗ **Configuración inicial:** Requiere más pasos técnicos

❗ **Periféricos:** Necesitas monitor, teclado, mouse

❗ **Tarjeta SD:** Puede corromperse (hacer backups)

## 📁 Organización Recomendada

```
/home/elixir/
├── ElixirKidsCourse/
│   ├── nivel_1/
│   ├── nivel_2/
│   ├── nivel_3/
│   ├── nivel_4/
│   ├── nivel_5/
│   └── mis_proyectos/
├── start-livebook.sh
└── backups/
```

## 📞 Próximos Pasos

1. ✅ Verifica que todo funciona correctamente
2. ✅ Configura backup automático
3. ✅ Descarga los notebooks del [Nivel 1](../nivel_1/README.md)
4. ✅ Personaliza el escritorio para hacerlo más amigable
5. ✅ ¡Comienza a programar!

## 🎓 Recursos Adicionales

- [Documentación oficial Raspberry Pi](https://www.raspberrypi.com/documentation/)
- [Foro de Raspberry Pi](https://forums.raspberrypi.com/)
- [Raspberry Pi para Educación](https://www.raspberrypi.org/education/)
- [Elixir on ARM](https://github.com/nerves-project/nerves)

---

**¡Tu laboratorio educativo está listo! 🥧🚀**

*La Raspberry Pi no solo te sirve para este curso: después puedes usarla para proyectos con Nerves (IoT), servidor casero, consola de juegos retro, ¡y mucho más!*

