# 💻 Clase 7: Mini Proyecto CLI

## 🎯 Objetivos

* 💻 Crear aplicación de consola completa
* 🎮 Menú interactivo
* 📊 Gestionar estado

## 🎮 Aplicación CLI con Menú

Crea `mi_app.ex`:

```elixir
defmodule MiApp do
  def main do
    IO.puts("\n=== MI APLICACIÓN ===\n")
    menu()
  end

  defp menu do
    IO.puts("""
    1. Calculadora
    2. Generador de mensajes
    3. Salir
    """)

    opcion = IO.gets("Elige (1-3): ") |> String.trim()

    case opcion do
      "1" -> calculadora()
      "2" -> generador()
      "3" -> IO.puts("¡Adiós!")
      _ ->
        IO.puts("Opción inválida")
        menu()
    end
  end

  defp calculadora do
    a = IO.gets("Primer número: ") |> String.trim() |> String.to_integer()
    b = IO.gets("Segundo número: ") |> String.trim() |> String.to_integer()

    IO.puts("Suma: #{a + b}")
    IO.puts("Producto: #{a * b}")

    menu()
  end

  defp generador do
    nombre = IO.gets("Tu nombre: ") |> String.trim()
    IO.puts("\n¡Hola #{nombre}! Eres increíble.\n")

    menu()
  end
end

MiApp.main()
```

Ejecuta:
```bash
elixir mi_app.ex
```

## 🏆 Tu Proyecto

Crea tu propia aplicación CLI con menú.

## 📝 Resumen

* ✅ Aplicaciones CLI
* ✅ Menús interactivos
* ✅ Recursión para loops

---

**¡Creaste una app profesional! 💻✨**

