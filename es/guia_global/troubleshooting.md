# 🔧 Solución de Problemas Comunes (Troubleshooting)

## 🎯 Introducción

Esta guía te ayudará a resolver los problemas más comunes que pueden surgir durante el curso. Los problemas están organizados por categoría para facilitar la búsqueda.

---

## 📑 Índice Rápido

1. [Problemas de Instalación](#-problemas-de-instalación)
2. [Problemas con Livebook](#-problemas-con-livebook)
3. [Errores de Código Elixir](#-errores-de-código-elixir)
4. [Problemas con Kino](#-problemas-con-kino)
5. [Problemas de Rendimiento](#-problemas-de-rendimiento)
6. [Problemas de Red](#-problemas-de-red)
7. [Problemas con Mix y Dependencias](#-problemas-con-mix-y-dependencias)
8. [Problemas Específicos por Sistema Operativo](#-problemas-específicos-por-sistema-operativo)
9. [Preguntas Frecuentes](#-preguntas-frecuentes)

---

## 🔨 Problemas de Instalación

### "Command 'elixir' not found" o "elixir no es reconocido como comando"

**Problema:** El sistema no encuentra Elixir después de instalarlo.

**Solución:**

**En Windows:**
1. Cierra y reabre la terminal/PowerShell
2. Si persiste:
   - Busca "Variables de entorno" en el menú Inicio
   - Edita las variables de entorno del sistema
   - Verifica que la ruta de Elixir esté en PATH
   - Típicamente: `C:\Program Files\Elixir\bin`
3. Reinicia la computadora

**En macOS/Linux:**
```bash
# Verifica dónde está instalado Elixir
which elixir

# Si no muestra nada, verifica la instalación
# macOS con Homebrew:
brew list elixir

# Linux:
dpkg -l | grep elixir

# Agrega al PATH (ajusta la ruta según tu instalación)
echo 'export PATH="$PATH:/usr/local/bin"' >> ~/.bashrc
source ~/.bashrc
```

### Mix no está disponible

**Problema:** Error "Mix is not available" o "mix: command not found"

**Solución:**
```bash
# Instala Hex (gestor de paquetes)
mix local.hex --force

# Instala Rebar (herramienta de compilación)
mix local.rebar --force

# Si persiste, reinstala Elixir
```

### Error durante la instalación: "Erlang not found"

**Problema:** Elixir no puede instalarse porque falta Erlang.

**Solución:**

**Windows:**
- Descarga el instalador que incluye Erlang desde https://elixir-lang.org/install.html
- O instala Erlang primero desde https://www.erlang.org/downloads

**macOS:**
```bash
brew install erlang
brew install elixir
```

**Linux (Ubuntu/Debian):**
```bash
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i erlang-solutions_2.0_all.deb
sudo apt-get update
sudo apt-get install esl-erlang elixir
```

---

## 📓 Problemas con Livebook

### Livebook no abre en el navegador

**Problema:** Ejecutas Livebook pero no se abre el navegador automáticamente.

**Solución:**
1. Busca en la terminal un mensaje como:
   ```
   [Livebook] Application running at http://localhost:8080/?token=abcd1234
   ```
2. Copia toda esa URL (incluyendo el token)
3. Ábrela manualmente en tu navegador

### Error "Port 8080 already in use"

**Problema:** El puerto 8080 ya está siendo usado por otra aplicación.

**Solución:**

**Opción A: Cambiar el puerto de Livebook**
```bash
livebook server --port 9090
```

**Opción B: Encontrar y detener el proceso que usa el puerto**

En Linux/macOS:
```bash
# Ver qué usa el puerto 8080
lsof -i :8080

# Detener el proceso (reemplaza PID con el número mostrado)
kill -9 PID
```

En Windows:
```powershell
# Ver qué usa el puerto
netstat -ano | findstr :8080

# Nota el PID y deténlo en el Administrador de Tareas
```

### Livebook se cierra inesperadamente

**Problema:** Livebook Desktop se cierra solo sin mensaje de error.

**Solución:**
1. Verifica que tienes suficiente memoria RAM (mínimo 2GB libres)
2. Cierra otros programas que consuman recursos
3. Actualiza a la última versión de Livebook Desktop
4. Si usas la versión de terminal, revisa los logs de error

### Las celdas no se ejecutan

**Problema:** Al presionar "Evaluate", no pasa nada.

**Solución:**
1. Verifica que el Runtime está conectado:
   - Mira la esquina superior derecha
   - Debe decir "Connected" en verde
2. Si dice "Disconnected":
   - Runtime → Reconnect
   - O Runtime → Configure → Reinicia
3. Revisa si hay errores de sintaxis en celdas anteriores
4. Ejecuta las celdas en orden desde el principio

### No se guardan los cambios

**Problema:** Los notebooks no guardan los cambios realizados.

**Solución:**
1. Presiona `Ctrl+S` (o `Cmd+S` en Mac) manualmente
2. Verifica permisos de escritura en la carpeta:
   ```bash
   # Linux/macOS
   ls -la carpeta_notebooks
   chmod u+w carpeta_notebooks
   ```
3. En Docker, asegúrate de usar el parámetro `-v` correctamente:
   ```bash
   -v $(pwd)/notebooks:/data
   ```

### Error "Failed to start runtime"

**Problema:** No se puede iniciar el runtime de Elixir.

**Solución:**
1. Cierra y reabre Livebook
2. Runtime → Configure
3. Selecciona "Elixir standalone"
4. Si tienes problemas de memoria:
   - Runtime → Configure → Advanced
   - Reduce "Maximum memory" si está configurado

---

## 💻 Errores de Código Elixir

### ** (CompileError) undefined function

**Problema:**
```elixir
** (CompileError) undefined function suma/2
```

**Causa:** Intentas usar una función que no existe o no está definida.

**Solución:**
1. Verifica que la función esté definida:
   ```elixir
   def suma(a, b) do
     a + b
   end
   ```
2. Asegúrate de que las celdas se ejecuten en orden
3. Si la función está en otro módulo:
   ```elixir
   MiModulo.suma(1, 2)
   ```

### ** (ArithmeticError) bad argument in arithmetic expression

**Problema:**
```elixir
iex> "5" + 3
** (ArithmeticError) bad argument in arithmetic expression
```

**Causa:** Intentas hacer operaciones matemáticas con tipos incompatibles.

**Solución:**
```elixir
# Convertir string a número
String.to_integer("5") + 3  # => 8

# O usar interpolación
"5" <> "3"  # => "53" (concatenación de strings)
```

### ** (FunctionClauseError) no function clause matching

**Problema:**
```elixir
** (FunctionClauseError) no function clause matching in MiModulo.saludo/1
```

**Causa:** La función no tiene una cláusula que maneje el argumento dado.

**Solución:**
```elixir
# Asegúrate de tener una cláusula por defecto
def saludo(nombre) when is_binary(nombre) do
  "Hola, #{nombre}"
end

def saludo(_) do
  "Hola, desconocido"
end
```

### ** (SyntaxError) syntax error before: 'end'

**Problema:** Error de sintaxis, generalmente por olvidar `do` o tener `end` de más/menos.

**Solución:**
1. Revisa que cada `do` tenga su correspondiente `end`:
   ```elixir
   # Correcto
   if condicion do
     accion
   end
   
   # Incorrecto (falta 'do')
   if condicion
     accion
   end
   ```
2. Verifica el anidamiento de funciones y bloques
3. Usa un editor con resaltado de sintaxis

### ** (MatchError) no match of right hand side value

**Problema:**
```elixir
iex> {:ok, valor} = {:error, "algo falló"}
** (MatchError) no match of right hand side value: {:error, "algo falló"}
```

**Causa:** El pattern matching falla porque los valores no coinciden.

**Solución:**
```elixir
# Usa case para manejar diferentes casos
case funcion() do
  {:ok, valor} -> 
    IO.puts("Éxito: #{valor}")
  {:error, razon} -> 
    IO.puts("Error: #{razon}")
end
```

### Variables sin usar (warnings)

**Problema:**
```elixir
warning: variable "x" is unused
```

**Causa:** Definiste una variable pero no la usas.

**Solución:**
```elixir
# Si la variable es intencional pero no se usa, prefija con _
_x = 5

# O usa _ directamente si no la necesitas
_ = funcion_con_efecto_secundario()
```

---

## 🎨 Problemas con Kino

### Kino no está disponible

**Problema:**
```elixir
** (UndefinedFunctionError) function Kino.Input.text/1 is undefined (module Kino.Input is not available)
```

**Causa:** Kino no está instalado o no se cargó correctamente.

**Solución:**
En la primera celda del notebook:
```elixir
Mix.install([
  {:kino, "~> 0.12.0"}
])
```

Ejecuta esta celda y espera a que termine antes de usar Kino en otras celdas.

### Los widgets de Kino no aparecen

**Problema:** Las celdas con `Kino.Input` o `Kino.render` no muestran nada.

**Solución:**
1. Asegúrate de que estás ejecutando en Livebook (no en iex terminal)
2. Reinicia el runtime:
   - Runtime → Reconnect
3. Vuelve a ejecutar la celda con `Mix.install`
4. Luego ejecuta las celdas con Kino

### Error al leer input de Kino

**Problema:** `Kino.Input.read(input)` devuelve un valor inesperado.

**Solución:**
```elixir
# Asegúrate de crear el input primero
input = Kino.Input.text("Tu nombre")

# Muestra el widget (importante!)
input

# En otra celda, lee el valor
nombre = Kino.Input.read(input)
IO.puts("Hola, #{nombre}")
```

**Nota:** El input debe mostrarse (estar al final de una celda o usar `Kino.render/1`) antes de poder leerlo.

### Kino.animate no funciona

**Problema:** Las animaciones no se muestran o se congelan.

**Solución:**
```elixir
# Asegúrate de devolver el frame correctamente
Kino.animate(0, fn contador ->
  frame = "Contador: #{contador}"
  
  # Espera 1 segundo
  Process.sleep(1000)
  
  # Devuelve {frame, nuevo_estado}
  {:cont, frame, contador + 1}
end)
```

---

## 🐌 Problemas de Rendimiento

### Livebook está muy lento

**Problema:** La interfaz responde lentamente, hay lag al escribir.

**Solución:**
1. **Cierra notebooks que no estés usando**
2. **Reinicia el runtime:**
   - Runtime → Disconnect and reconnect
3. **Limita la salida de datos:**
   ```elixir
   # En lugar de imprimir 10000 elementos
   Enum.take(lista_grande, 10)
   ```
4. **Cierra pestañas del navegador que no uses**
5. **Asigna más memoria si usas Docker/VM**

### El código tarda mucho en ejecutarse

**Problema:** Una celda está ejecutándose indefinidamente.

**Solución:**
1. **Cancela la ejecución:**
   - Botón "Cancel evaluation" en la celda
   - O Runtime → Interrupt
2. **Verifica bucles infinitos:**
   ```elixir
   # Malo: bucle infinito
   defmodule Mal do
     def loop, do: loop()
   end
   
   # Bueno: con condición de parada
   defmodule Bien do
     def loop(0), do: :ok
     def loop(n), do: loop(n - 1)
   end
   ```
3. **Optimiza código recursivo:**
   ```elixir
   # Agrega límite de recursión
   def cuenta(n) when n > 1_000_000, do: :limite_alcanzado
   def cuenta(n), do: cuenta(n + 1)
   ```

### Problemas de memoria

**Problema:** Error "Out of memory" o Livebook se congela.

**Solución:**
1. **Reduce el tamaño de datos:**
   ```elixir
   # Malo: genera lista enorme
   lista = Enum.to_list(1..10_000_000)
   
   # Bueno: usa streams (lazy evaluation)
   stream = Stream.iterate(1, &(&1 + 1))
   ```
2. **Libera memoria:**
   ```elixir
   # Después de usar datos grandes
   lista = nil
   :erlang.garbage_collect()
   ```
3. **Reinicia el runtime**
4. **Aumenta memoria disponible (Docker/VM)**

---

## 🌐 Problemas de Red

### No hay conexión a internet en la VM/Docker

**Problema:** No puedes instalar paquetes o acceder a internet desde el entorno.

**Solución:**

**Docker:**
```bash
# Verifica conexión del contenedor
docker exec -it CONTAINER_ID ping google.com

# Si falla, verifica configuración de red
docker network ls
docker inspect CONTAINER_ID
```

**VM (VirtualBox):**
1. Configuración → Red
2. Adaptador 1: NAT (para internet básico)
3. O "Puente" (Bridge) para red completa
4. Reinicia la VM

**General:**
```bash
# Prueba conectividad
ping google.com

# Ver configuración de red
ip addr show  # Linux
ifconfig      # macOS
ipconfig      # Windows
```

### No puedo acceder a Livebook desde otro dispositivo

**Problema:** Livebook corre en la Raspberry Pi / servidor pero no puedes acceder desde tu laptop.

**Solución:**
1. **Inicia Livebook con IP 0.0.0.0:**
   ```bash
   livebook server --ip 0.0.0.0
   ```

2. **Encuentra la IP del servidor:**
   ```bash
   # Linux/macOS/Raspberry Pi
   hostname -I
   
   # Windows
   ipconfig
   ```

3. **Accede desde otro dispositivo:**
   ```
   http://192.168.1.XXX:8080
   ```

4. **Verifica firewall:**
   ```bash
   # Linux: permite puerto 8080
   sudo ufw allow 8080
   
   # Windows: Agregar regla en Firewall de Windows
   ```

---

## 📦 Problemas con Mix y Dependencias

### "Could not find Hex"

**Problema:** Error al intentar usar Mix.

**Solución:**
```bash
mix local.hex --force
```

### Error al instalar dependencias

**Problema:**
```
** (Mix) Could not download dependency...
```

**Solución:**
1. Verifica conexión a internet
2. Limpia cache de Mix:
   ```bash
   mix deps.clean --all
   mix deps.get
   ```
3. Actualiza Hex:
   ```bash
   mix local.hex --force
   ```

### Conflictos de versiones

**Problema:**
```
** (Mix) Incompatible version specifications...
```

**Solución:**
```elixir
# En Mix.install o mix.exs, especifica versiones compatibles
Mix.install([
  {:kino, "~> 0.12.0"},       # ~> permite actualizaciones menores
  {:vega_lite, "~> 0.1.8"}
])
```

### "Module ... is not available"

**Problema:** Intentas usar un módulo de una dependencia que no se cargó.

**Solución:**
1. Ejecuta primero la celda con `Mix.install`
2. Espera a que termine completamente
3. Luego ejecuta las celdas que usan las dependencias
4. Si usas Mix project:
   ```bash
   mix deps.get
   mix compile
   ```

---

## 🖥️ Problemas Específicos por Sistema Operativo

### Windows: "OpenSSL not found"

**Problema:** Error relacionado con OpenSSL al instalar o ejecutar.

**Solución:**
1. Descarga el instalador de Elixir que incluye todas las dependencias
2. O instala OpenSSL desde: https://slproweb.com/products/Win32OpenSSL.html

### macOS: "Permission denied" al instalar

**Problema:** Errores de permisos al instalar con Homebrew.

**Solución:**
```bash
# Arregla permisos de Homebrew
sudo chown -R $(whoami) /usr/local/Cellar
sudo chown -R $(whoami) /usr/local/Homebrew

# Reinstala Elixir
brew reinstall elixir
```

### macOS: "xcrun: error: invalid active developer path"

**Problema:** Error al instalar dependencias que requieren compilación.

**Solución:**
```bash
# Instala Command Line Tools
xcode-select --install
```

### Linux: "erl_exec: permission denied"

**Problema:** No tienes permisos para ejecutar Erlang.

**Solución:**
```bash
# Da permisos de ejecución
chmod +x $(which erl)
chmod +x $(which elixir)

# O reinstala con permisos correctos
sudo apt-get install --reinstall elixir
```

---

## ❓ Preguntas Frecuentes

### ¿Por qué mi código funciona en una celda pero no en otra?

**Respuesta:** Las celdas en Livebook deben ejecutarse en orden. Una celda solo puede usar variables y funciones definidas en celdas anteriores que ya se hayan ejecutado.

**Solución:** Usa el botón "Evaluate all" para ejecutar todas las celdas en orden.

### ¿Cómo limpio todo y empiezo de nuevo?

**Respuesta:** 
- Runtime → Disconnect and connect
- Esto reinicia el entorno pero mantiene el código

### ¿Puedo usar bibliotecas externas sin Mix.install?

**Respuesta:** En Livebook, `Mix.install` es la forma estándar. En proyectos Mix (niveles 4-5), usas `mix.exs`.

### ¿Qué hago si Livebook no encuentra un archivo?

**Respuesta:**
```elixir
# Ver directorio actual
File.cwd!()

# Listar archivos
File.ls!()

# Usar ruta absoluta
File.read!("/ruta/completa/al/archivo.txt")

# O cambiar directorio de trabajo en Livebook:
# Settings → System environment → Working directory
```

### ¿Cómo veo qué versión de Elixir tengo?

**Respuesta:**
```elixir
# En Livebook o iex
System.version()

# En terminal
elixir --version
```

### ¿Es normal que la primera ejecución sea lenta?

**Respuesta:** Sí, especialmente al instalar dependencias con `Mix.install`. Las ejecuciones siguientes serán mucho más rápidas porque usa caché.

---

## 🆘 Cuando Nada Funciona

Si has probado todo y sigues teniendo problemas:

### 1. Reinstalación Limpia

**Opción A: Livebook Desktop**
1. Desinstala completamente Livebook
2. Descarga la última versión
3. Instala de nuevo

**Opción B: Instalación local**
```bash
# Desinstala
# Windows: Usar "Agregar o quitar programas"
# macOS: brew uninstall elixir && brew cleanup
# Linux: sudo apt-get remove --purge elixir

# Limpia configuración
rm -rf ~/.mix
rm -rf ~/.hex

# Reinstala siguiendo la guía de instalación
```

**Opción C: Docker (empezar fresco)**
```bash
# Elimina contenedores e imágenes
docker rm -f $(docker ps -a -q)
docker rmi livebook/livebook

# Descarga imagen nueva
docker pull livebook/livebook:latest

# Inicia de nuevo
docker run -p 8080:8080 --pull always livebook/livebook
```

### 2. Buscar Ayuda

**Foros y Comunidades:**
1. [Elixir Forum](https://elixirforum.com) - Muy amigable
2. [Stack Overflow con tag elixir](https://stackoverflow.com/questions/tagged/elixir)
3. [Reddit r/elixir](https://reddit.com/r/elixir)
4. [Discord de Elixir](https://discord.gg/elixir)

**Al pedir ayuda, incluye:**
- ✅ Sistema operativo y versión
- ✅ Versión de Elixir (`elixir --version`)
- ✅ Qué estabas intentando hacer
- ✅ Código que reproduce el error
- ✅ Mensaje de error completo
- ✅ Qué has intentado ya

### 3. Alternativas Temporales

**Si no puedes hacer que funcione localmente:**
1. **Usa Livebook en la nube (temporal):**
   - Algunos servicios ofrecen Livebook online
   - Busca "Livebook online playground"
   
2. **Prueba en otro dispositivo:**
   - A veces el problema es específico del hardware/OS
   
3. **Usa una VM o Docker:**
   - Puede ser más fácil que resolver problemas de instalación nativa

---

## 📊 Códigos de Error Comunes

| Error | Significado | Solución Rápida |
|-------|-------------|-----------------|
| `** (UndefinedFunctionError)` | Función no existe | Verifica el nombre y que esté definida |
| `** (ArgumentError)` | Argumento inválido | Revisa tipos de datos |
| `** (MatchError)` | Pattern matching falló | Usa `case` o ajusta el pattern |
| `** (ArithmeticError)` | Error matemático | Verifica tipos (string vs número) |
| `** (CompileError)` | Error de sintaxis | Revisa `do`/`end`, comas, paréntesis |
| `** (RuntimeError)` | Error en tiempo de ejecución | Lee el mensaje específico |
| `** (FunctionClauseError)` | No hay cláusula que maneje el caso | Agrega cláusula catch-all |

---

## 🎓 Recursos Adicionales

Para problemas más específicos, consulta:

- **[Documentación oficial de Livebook](https://hexdocs.pm/livebook)**
- **[Elixir Getting Started](https://elixir-lang.org/getting-started/introduction.html)**
- **[Guía de instalación local](instalacion_local.md)**
- **[Recursos de apoyo](recursos_de_apoyo.md)**

---

## 💡 Consejos para Prevenir Problemas

1. **Guarda frecuentemente:** `Ctrl+S` es tu amigo
2. **Ejecuta celdas en orden:** No saltes celdas
3. **Lee los errores completos:** Contienen información valiosa
4. **Empieza simple:** Prueba código básico primero
5. **Usa Git para versionar:** Puedes volver atrás si algo se rompe
6. **Mantén actualizado:** Actualiza Elixir y Livebook regularmente
7. **Haz backups:** Copia tus notebooks regularmente

---

## 🚑 Comandos de Emergencia

```bash
# Ver procesos de Elixir corriendo
ps aux | grep elixir

# Matar todos los procesos de Elixir (último recurso)
pkill -9 elixir
pkill -9 beam.smp

# Limpiar caché de Mix
rm -rf _build
rm -rf deps
rm -rf ~/.mix

# Reiniciar servicios (Raspberry Pi/Linux)
sudo systemctl restart livebook

# Ver logs de errores (Linux)
journalctl -xe | grep elixir

# Verificar salud del sistema
elixir -e "IO.puts('Elixir funciona!')"
```

---

**¿Encontraste un problema no listado aquí? Por favor repórtalo para que podamos agregarlo y ayudar a otros. 🙏**

**¡No te rindas! La programación implica resolver problemas, y cada error es una oportunidad de aprender. 💪🚀**

