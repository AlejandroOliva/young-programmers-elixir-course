# 🏗️ Class 6: Modules and Functions in Terminal

## 🎯 Objectives

* 🏗️ Organize code in modules
* 📁 Create .ex files
* 💻 Execute from terminal

## 📁 Your First Module in a File

Create a file `calculator.ex`:

```elixir
defmodule Calculator do
  @moduledoc """
  Simple calculator with basic operations.
  """

  def add(a, b), do: a + b
  def subtract(a, b), do: a - b
  def multiply(a, b), do: a * b

  def divide(_a, 0), do: {:error, "Division by zero"}
  def divide(a, b), do: {:ok, a / b}
end

# Tests
IO.puts("5 + 3 = #{Calculator.add(5, 3)}")
IO.puts("10 - 4 = #{Calculator.subtract(10, 4)}")

case Calculator.divide(10, 2) do
  {:ok, result} -> IO.puts("10 / 2 = #{result}")
  {:error, message} -> IO.puts("Error: #{message}")
end
```

Execute:
```bash
elixir calculator.ex
```

## 🎯 Nested Modules

```elixir
defmodule MyApp do
  defmodule Utils do
    def greet(name), do: "Hello, #{name}!"
  end

  defmodule Math do
    def square(n), do: n * n
  end
end

# Use nested modules
IO.puts(MyApp.Utils.greet("Programmer"))
IO.puts("5² = #{MyApp.Math.square(5)}")
```

## 🏆 Exercise

Create a file `game.ex` with:
- Main module
- Game functions
- Execute it from terminal

## 📝 Summary

* ✅ Organize code in modules
* ✅ Executable .ex files
* ✅ Nested modules

---

**You program like a professional! 🏗️✨**

