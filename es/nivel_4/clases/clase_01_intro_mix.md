# 📦 Clase 1: Introducción a Mix

## 🎯 ¡Bienvenidos al Desarrollo Profesional!

Hoy aprenderás **Mix**, la herramienta que usan los desarrolladores Elixir profesionales para gestionar proyectos.

## 🤔 ¿Qué es Mix?

**Mix** es el gestor de proyectos de Elixir. Piénsalo como un asistente que:

- Crea estructura de proyectos
- Compila tu código
- Ejecuta tests
- Gestiona dependencias (bibliotecas externas)
- Y mucho más

**Sin Mix:** Archivos sueltos, ejecutar uno por uno  
**Con Mix:** Proyecto organizado, comandos simples

## 🚀 Tu Primer Proyecto Mix

### Paso 1: Crear el Proyecto

Abre tu terminal y ejecuta:

```bash
mix new mi_primer_proyecto
```

Verás algo como:

```
* creating README.md
* creating .formatter.exs
* creating .gitignore
* creating mix.exs
* creating lib
* creating lib/mi_primer_proyecto.ex
* creating test
* creating test/test_helper.exs
* creating test/mi_primer_proyecto_test.exs
```

¡Mix creó toda la estructura por ti!

### Paso 2: Explorar la Estructura

```bash
cd mi_primer_proyecto
ls  # o dir en Windows
```

Verás:

```
mi_primer_proyecto/
├── lib/                     # Tu código aquí
│   └── mi_primer_proyecto.ex
├── test/                    # Tests aquí
│   ├── test_helper.exs
│   └── mi_primer_proyecto_test.exs
├── mix.exs                  # Configuración del proyecto
├── README.md                # Documentación
└── .gitignore              # Para Git
```

## 📁 Archivos Importantes

### 1. mix.exs (Configuración)

Abre `mix.exs` en tu editor. Verás:

```elixir
defmodule MiPrimerProyecto.MixProject do
  use Mix.Project

  def project do
    [
      app: :mi_primer_proyecto,
      version: "0.1.0",
      elixir: "~> 1.16",
      start_permanent: Mix.env() == :prod,
      deps: deps()
    ]
  end

  def application do
    [extra_applications: [:logger]]
  end

  defp deps do
    []  # Dependencias aquí
  end
end
```

**No te preocupes por entenderlo todo ahora.** Lo importante:
- `version`: Versión de tu app
- `deps`: Dependencias (bibliotecas externas)

### 2. lib/mi_primer_proyecto.ex (Tu Código)

```elixir
defmodule MiPrimerProyecto do
  @moduledoc """
  Documentation for `MiPrimerProyecto`.
  """

  @doc """
  Hello world.

  ## Examples

      iex> MiPrimerProyecto.hello()
      :world

  """
  def hello do
    :world
  end
end
```

### 3. test/mi_primer_proyecto_test.exs (Tests)

```elixir
defmodule MiPrimerProyectoTest do
  use ExUnit.Case
  doctest MiPrimerProyecto

  test "greets the world" do
    assert MiPrimerProyecto.hello() == :world
  end
end
```

## ⚡ Comandos Mix Esenciales

### 1. Compilar

```bash
mix compile
```

Compila todo tu código. La primera vez tarda más, luego es rápido.

### 2. Ejecutar Tests

```bash
mix test
```

Ejecuta todos tus tests. Deberías ver:

```
..

Finished in 0.02 seconds
1 doctest, 1 test, 0 failures
```

¡Todos pasaron! ✅

### 3. IEx con Mix

```bash
iex -S mix
```

Abre IEx pero con tu proyecto cargado. Ahora puedes:

```elixir
iex> MiPrimerProyecto.hello()
:world
```

## 🎯 Práctica: Modificar el Proyecto

### Ejercicio 1: Añadir una Función

Edita `lib/mi_primer_proyecto.ex`:

```elixir
defmodule MiPrimerProyecto do
  @moduledoc """
  Mi primer proyecto con Mix.
  """

  def hello do
    :world
  end

  def saludar(nombre) do
    "¡Hola, #{nombre}!"
  end

  def sumar(a, b) do
    a + b
  end
end
```

**Compila:**
```bash
mix compile
```

**Prueba en IEx:**
```bash
iex -S mix
```

```elixir
iex> MiPrimerProyecto.saludar("Ana")
"¡Hola, Ana!"

iex> MiPrimerProyecto.sumar(5, 3)
8
```

### Ejercicio 2: Añadir Tests

Edita `test/mi_primer_proyecto_test.exs`:

```elixir
defmodule MiPrimerProyectoTest do
  use ExUnit.Case
  doctest MiPrimerProyecto

  test "greets the world" do
    assert MiPrimerProyecto.hello() == :world
  end

  test "saluda a una persona" do
    assert MiPrimerProyecto.saludar("Ana") == "¡Hola, Ana!"
  end

  test "suma dos números" do
    assert MiPrimerProyecto.sumar(5, 3) == 8
  end
end
```

**Ejecuta tests:**
```bash
mix test
```

Deberías ver:

```
...

Finished in 0.03 seconds
1 doctest, 3 tests, 0 failures
```

¡Todos pasaron! 🎉

## 🏗️ Proyecto: Calculadora

Vamos a crear un proyecto más completo.

### Paso 1: Crear Proyecto

```bash
mix new calculadora
cd calculadora
```

### Paso 2: Implementar (lib/calculadora.ex)

```elixir
defmodule Calculadora do
  @moduledoc """
  Calculadora simple con operaciones básicas.
  """

  @doc """
  Suma dos números.
  """
  def sumar(a, b), do: a + b

  @doc """
  Resta dos números.
  """
  def restar(a, b), do: a - b

  @doc """
  Multiplica dos números.
  """
  def multiplicar(a, b), do: a * b

  @doc """
  Divide dos números.
  Retorna {:error, :division_por_cero} si b es 0.
  """
  def dividir(_a, 0), do: {:error, :division_por_cero}
  def dividir(a, b), do: {:ok, a / b}
end
```

### Paso 3: Tests (test/calculadora_test.exs)

```elixir
defmodule CalculadoraTest do
  use ExUnit.Case
  doctest Calculadora

  describe "sumar/2" do
    test "suma dos números positivos" do
      assert Calculadora.sumar(5, 3) == 8
    end

    test "suma números negativos" do
      assert Calculadora.sumar(-5, -3) == -8
    end
  end

  describe "dividir/2" do
    test "divide correctamente" do
      assert Calculadora.dividir(10, 2) == {:ok, 5.0}
    end

    test "maneja división por cero" do
      assert Calculadora.dividir(10, 0) == {:error, :division_por_cero}
    end
  end
end
```

### Paso 4: Probar

```bash
mix test
```

## 📝 Comandos Mix Adicionales

```bash
# Formatear código (hace que se vea bonito)
mix format

# Limpiar compilación
mix clean

# Ver dependencias
mix deps

# Generar documentación
mix docs  # (requiere instalar ex_doc)

# Ejecutar script
mix run script.exs
```

## 🎯 Ejercicio Final: Tu Proyecto

Crea un proyecto Mix para:

**Opción A: Conversor de Unidades**
- Temperatura (C ↔ F)
- Distancia (km ↔ millas)
- Peso (kg ↔ libras)

**Opción B: Gestor de Tareas Simple**
- Añadir tareas
- Listar tareas
- Marcar como completadas

**Requisitos:**
1. Usar Mix
2. Al menos 3 funciones
3. Tests para cada función
4. Documentación en cada función

## 📝 Resumen

Hoy aprendiste:

* ✅ Qué es Mix y por qué es importante
* ✅ Crear proyectos con `mix new`
* ✅ Estructura de un proyecto Mix
* ✅ Compilar con `mix compile`
* ✅ Tests con `mix test`
* ✅ IEx con proyecto cargado `iex -S mix`
* ✅ Escribir tests básicos con ExUnit

## 🚀 Próxima Clase

En la próxima clase aprenderemos sobre **Módulos y Organización** - cómo estructurar proyectos más grandes con múltiples módulos.

---

**¡Bienvenido al desarrollo profesional con Mix! 📦✨**

*"Mix es tu nuevo mejor amigo. Aprende a usarlo bien y tu vida como desarrollador será mucho más fácil."*

