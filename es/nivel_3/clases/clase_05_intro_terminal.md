# 💻 Clase 5: Introducción al Terminal

## 🎯 ¡Bienvenidos al Mundo Profesional!

Hoy es un día especial. Vas a aprender a programar como lo hacen los desarrolladores profesionales: **usando el terminal**.

## 🤔 ¿Qué es el Terminal?

El terminal (también llamado consola o línea de comandos) es una forma de darle instrucciones a tu computadora usando solo texto.

**Sin botones. Sin clicks. Solo texto y teclado.** 💪

### ¿Por qué usarlo?

- Es más rápido una vez que lo dominas
- Tienes más control
- Así trabajan los programadores profesionales
- Te prepara para herramientas avanzadas
- ¡Te hace sentir como un hacker! 😎

## 🚀 Abriendo el Terminal

### En Windows

- Busca "cmd" o "PowerShell" en el menú inicio
- O presiona `Win + R`, escribe `cmd`, Enter

### En macOS

- Busca "Terminal" en Spotlight (`Cmd + Espacio`)
- O en Aplicaciones → Utilidades → Terminal

### En Linux

- `Ctrl + Alt + T`
- O busca "Terminal" en tus aplicaciones

## 👀 Tu Primera Vista

Cuando abres el terminal, ves algo como:

```
C:\Users\TuNombre>
```

o

```
usuario@computadora:~$
```

Esto se llama el **"prompt"** - significa que el terminal está listo para recibir comandos.

## 📂 Comandos Básicos

### 1. ¿Dónde Estoy?

**Windows:**
```bash
cd
```

**macOS/Linux:**
```bash
pwd
```

Te dice en qué carpeta (directorio) estás.

### 2. ¿Qué Hay Aquí?

**Windows:**
```bash
dir
```

**macOS/Linux:**
```bash
ls
```

Muestra todos los archivos y carpetas donde estás.

### 3. Ir a Otra Carpeta

```bash
cd nombre_de_carpeta
```

**Ejemplos:**
```bash
cd Documentos
cd Desktop
cd ..           # Subir un nivel (volver atrás)
cd ~            # Ir a tu carpeta home (macOS/Linux)
```

### 4. Limpiar la Pantalla

```bash
cls    # Windows
clear  # macOS/Linux
```

## 🎮 Práctica: Navegando

**Ejercicio 1: Explora**

1. Abre el terminal
2. Escribe `pwd` o `cd` (según tu sistema)
3. Escribe `ls` o `dir`
4. Encuentra una carpeta y entra: `cd nombre_carpeta`
5. Vuelve atrás: `cd ..`

**¡No tengas miedo! No puedes romper nada solo navegando.** 😊

## 🎨 Tu Primer Programa en Terminal

### Paso 1: Crea una Carpeta para tus Proyectos

```bash
cd Desktop            # O donde quieras
mkdir ElixirProyectos # Crear carpeta
cd ElixirProyectos    # Entrar a la carpeta
```

### Paso 2: Crea tu Primer Archivo

Abre tu editor de texto favorito (Notepad, VS Code, etc.) y crea un archivo llamado `hola.ex` con este contenido:

```elixir
# hola.ex
IO.puts("¡Hola desde el terminal!")
IO.puts("Mi nombre es [Tu Nombre]")
IO.puts("¡Y soy un programador!")
```

Guárdalo en la carpeta `ElixirProyectos`.

### Paso 3: Ejecuta tu Programa

En el terminal, asegúrate de estar en la carpeta correcta:

```bash
cd Desktop/ElixirProyectos  # Ajusta según tu ubicación
```

Luego ejecuta:

```bash
elixir hola.ex
```

**¡Boom! 🎉 Tu primer programa ejecutado desde terminal.**

## 🎯 Ejercicio: Calculadora Simple

Crea un archivo `calculadora.ex`:

```elixir
defmodule Calculadora do
  def sumar(a, b) do
    a + b
  end

  def restar(a, b) do
    a - b
  end

  def multiplicar(a, b) do
    a * b
  end
end

# Pruebas
IO.puts("5 + 3 = #{Calculadora.sumar(5, 3)}")
IO.puts("10 - 4 = #{Calculadora.restar(10, 4)}")
IO.puts("6 * 7 = #{Calculadora.multiplicar(6, 7)}")
```

Ejecuta:
```bash
elixir calculadora.ex
```

## 🔥 IEx - Terminal Interactivo de Elixir

IEx es como Livebook pero en el terminal.

### Cómo Abrirlo

Simplemente escribe en el terminal:

```bash
iex
```

Verás algo como:

```
Erlang/OTP 26 [erts-14.2] [source] [64-bit]

Interactive Elixir (1.16.0) - press Ctrl+C to exit
iex(1)>
```

### Pruébalo

```elixir
iex(1)> IO.puts("¡Hola!")
¡Hola!
:ok

iex(2)> 2 + 2
4

iex(3)> nombre = "Programador"
"Programador"

iex(4)> IO.puts("Hola, #{nombre}")
Hola, Programador
:ok
```

### Salir de IEx

Presiona `Ctrl + C` dos veces.

## 🎮 Ejercicio: Interacción con Usuario

Crea `saludo.ex`:

```elixir
IO.puts("¿Cómo te llamas?")
nombre = IO.gets("Tu nombre: ") |> String.trim()

IO.puts("¿Cuántos años tienes?")
edad = IO.gets("Tu edad: ") |> String.trim() |> String.to_integer()

IO.puts("\n¡Hola, #{nombre}!")
IO.puts("Tienes #{edad} años")
IO.puts("En 5 años tendrás #{edad + 5} años")
```

Ejecuta:
```bash
elixir saludo.ex
```

Y responde las preguntas.

## 🏆 Desafío: Menú Interactivo

Crea un programa con un menú:

```elixir
defmodule Menu do
  def mostrar do
    IO.puts("""
    \n=== MENÚ PRINCIPAL ===
    1. Saludar
    2. Sumar dos números
    3. Salir
    """)

    opcion = IO.gets("Elige (1-3): ") |> String.trim()

    case opcion do
      "1" ->
        nombre = IO.gets("Tu nombre: ") |> String.trim()
        IO.puts("¡Hola, #{nombre}!")
        mostrar()  # Volver al menú

      "2" ->
        a = IO.gets("Primer número: ") |> String.trim() |> String.to_integer()
        b = IO.gets("Segundo número: ") |> String.trim() |> String.to_integer()
        IO.puts("Resultado: #{a + b}")
        mostrar()  # Volver al menú

      "3" ->
        IO.puts("¡Adiós!")

      _ ->
        IO.puts("Opción inválida")
        mostrar()  # Volver al menú
    end
  end
end

Menu.mostrar()
```

## 📝 Comandos Útiles de IEx

```elixir
h(Enum)           # Ayuda sobre Enum
h(Enum.map)       # Ayuda sobre Enum.map
c("archivo.ex")   # Compilar y cargar archivo
r(MiModulo)       # Recargar módulo
```

## 🎯 Ejercicio Final

Crea un programa que:
1. Pida tu nombre
2. Pida tu edad
3. Pida tu color favorito
4. Muestre todo en un mensaje bonito
5. Tenga un menú para repetir o salir

## 📝 Resumen

Hoy aprendiste:

* ✅ Qué es el terminal y por qué es importante
* ✅ Comandos básicos de navegación
* ✅ Ejecutar programas Elixir desde terminal
* ✅ Usar IEx (terminal interactivo)
* ✅ Crear programas con interacción de usuario
* ✅ ¡Programar como un profesional! 💻

## 💡 Consejos

**Para Terminal:**
- No tengas miedo de experimentar
- Si te pierdes, usa `pwd`/`cd` para saber dónde estás
- `cd` sin argumentos te lleva a tu carpeta home
- Tab autocompleta nombres de carpetas/archivos

**Para IEx:**
- Es tu mejor amigo para probar cosas rápido
- Presiona flecha arriba para comandos anteriores
- Usa `h()` para ayuda

## 🚀 Próxima Clase

En la próxima clase aprenderemos sobre **Módulos y Funciones** más avanzados, todo desde el terminal.

---

**¡Felicidades! Ahora eres un programador de terminal. 💻✨**

*"El terminal puede parecer intimidante al inicio, pero es tu superpoder como programador."*

