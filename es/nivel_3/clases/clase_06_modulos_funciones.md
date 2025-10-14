# 🏗️ Clase 6: Módulos y Funciones en Terminal

## 🎯 Objetivos

* 🏗️ Organizar código en módulos
* 📁 Crear archivos .ex
* 💻 Ejecutar desde terminal

## 📁 Tu Primer Módulo en Archivo

Crea un archivo `calculadora.ex`:

```elixir
defmodule Calculadora do
  @moduledoc """
  Calculadora simple con operaciones básicas.
  """

  def sumar(a, b), do: a + b
  def restar(a, b), do: a - b
  def multiplicar(a, b), do: a * b

  def dividir(_a, 0), do: {:error, "División por cero"}
  def dividir(a, b), do: {:ok, a / b}
end

# Pruebas
IO.puts("5 + 3 = #{Calculadora.sumar(5, 3)}")
IO.puts("10 - 4 = #{Calculadora.restar(10, 4)}")

case Calculadora.dividir(10, 2) do
  {:ok, resultado} -> IO.puts("10 / 2 = #{resultado}")
  {:error, mensaje} -> IO.puts("Error: #{mensaje}")
end
```

Ejecuta:
```bash
elixir calculadora.ex
```

## 🎯 Módulos Anidados

```elixir
defmodule MiApp do
  defmodule Utilidades do
    def saludar(nombre), do: "¡Hola, #{nombre}!"
  end

  defmodule Matematicas do
    def cuadrado(n), do: n * n
  end
end

# Usa los módulos anidados
IO.puts(MiApp.Utilidades.saludar("Programador"))
IO.puts("5² = #{MiApp.Matematicas.cuadrado(5)}")
```

## 🏆 Ejercicio

Crea un archivo `juego.ex` con:
- Módulo principal
- Funciones para el juego
- Ejecútalo desde terminal

## 📝 Resumen

* ✅ Organizar código en módulos
* ✅ Archivos .ex ejecutables
* ✅ Módulos anidados

---

**¡Programas como un profesional! 🏗️✨**

