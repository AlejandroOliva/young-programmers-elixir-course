# 💻 Class 7: Mini CLI Project

## 🎯 Objectives

* 💻 Create complete console application
* 🎮 Interactive menu
* 📊 Manage state

## 🎮 CLI Application with Menu

Create `my_app.ex`:

```elixir
defmodule MyApp do
  def main do
    IO.puts("\n=== MY APPLICATION ===\n")
    menu()
  end

  defp menu do
    IO.puts("""
    1. Calculator
    2. Message generator
    3. Exit
    """)

    option = IO.gets("Choose (1-3): ") |> String.trim()

    case option do
      "1" -> calculator()
      "2" -> generator()
      "3" -> IO.puts("Goodbye!")
      _ ->
        IO.puts("Invalid option")
        menu()
    end
  end

  defp calculator do
    a = IO.gets("First number: ") |> String.trim() |> String.to_integer()
    b = IO.gets("Second number: ") |> String.trim() |> String.to_integer()

    IO.puts("Sum: #{a + b}")
    IO.puts("Product: #{a * b}")

    menu()
  end

  defp generator do
    name = IO.gets("Your name: ") |> String.trim()
    IO.puts("\nHello #{name}! You're amazing.\n")

    menu()
  end
end

MyApp.main()
```

Execute:
```bash
elixir my_app.ex
```

## 🏆 Your Project

Create your own CLI application with menu.

## 📝 Summary

* ✅ CLI applications
* ✅ Interactive menus
* ✅ Recursion for loops

---

**You created a professional app! 💻✨**

