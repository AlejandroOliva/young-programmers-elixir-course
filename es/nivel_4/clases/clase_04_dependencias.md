# 📦 Clase 4: Dependencias y Hex

## 🎯 Objetivos

* 📦 Usar bibliotecas externas
* 🌐 Hex.pm - repositorio de paquetes
* ⚙️ Configurar dependencias en mix.exs

## 📦 Agregar Dependencia

En `mix.exs`:

```elixir
defp deps do
  [
    {:jason, "~> 1.4"}  # Para trabajar con JSON
  ]
end
```

Luego:
```bash
mix deps.get
```

## 🎯 Usar la Dependencia

```elixir
defmodule MiApp do
  def encode_json do
    data = %{nombre: "Ana", edad: 14}
    Jason.encode!(data)
  end

  def decode_json do
    json = ~s({"nombre":"Pedro","edad":15})
    Jason.decode!(json)
  end
end
```

## 🏆 Ejercicio

Agrega y usa una dependencia en tu proyecto.

## 📝 Resumen

* ✅ Dependencias en mix.exs
* ✅ mix deps.get
* ✅ Hex.pm

---

**¡Usas bibliotecas profesionales! 📦✨**

