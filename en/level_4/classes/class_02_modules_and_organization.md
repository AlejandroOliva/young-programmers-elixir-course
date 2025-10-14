# 🏗️ Class 2: Modules and Organization

## 🎯 Objectives

* 🏗️ Organize code in multiple modules
* 📁 Project architecture
* 🎯 Separation of responsibilities

## 📁 Project Structure

```
my_project/
├── lib/
│   ├── my_project.ex          # Main module
│   └── my_project/
│       ├── calculator.ex      # Specific module
│       └── utils.ex           # Helper functions
```

## 🎯 Create Separate Module

`lib/my_project/calculator.ex`:

```elixir
defmodule MyProject.Calculator do
  def add(a, b), do: a + b
  def subtract(a, b), do: a - b
end
```

`lib/my_project.ex`:

```elixir
defmodule MyProject do
  alias MyProject.Calculator

  def demo do
    IO.puts("5 + 3 = #{Calculator.add(5, 3)}")
  end
end
```

## 🚀 Exercise

Create a project with:
- Main module
- 2-3 secondary modules
- Tests for each module

## 📝 Summary

* ✅ Multiple modules
* ✅ Alias for short names
* ✅ Professional organization

---

**You organize code like a professional! 🏗️✨**

