# 📦 Class 4: Dependencies and Hex

## 🎯 Objectives

* 📦 Use external libraries
* 🌐 Hex.pm - package repository
* ⚙️ Configure dependencies in mix.exs

## 📦 Add Dependency

In `mix.exs`:

```elixir
defp deps do
  [
    {:jason, "~> 1.4"}  # For working with JSON
  ]
end
```

Then:
```bash
mix deps.get
```

## 🎯 Use the Dependency

```elixir
defmodule MyApp do
  def encode_json do
    data = %{name: "Ana", age: 14}
    Jason.encode!(data)
  end

  def decode_json do
    json = ~s({"name":"Peter","age":15})
    Jason.decode!(json)
  end
end
```

## 🏆 Exercise

Add and use a dependency in your project.

## 📝 Summary

* ✅ Dependencies in mix.exs
* ✅ mix deps.get
* ✅ Hex.pm

---

**You use professional libraries! 📦✨**

