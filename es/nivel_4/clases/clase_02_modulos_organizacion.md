# 🏗️ Clase 2: Módulos y Organización

## 🎯 Objetivos

* 🏗️ Organizar código en múltiples módulos
* 📁 Arquitectura de proyectos
* 🎯 Separación de responsabilidades

## 📁 Estructura de Proyecto

```
mi_proyecto/
├── lib/
│   ├── mi_proyecto.ex          # Módulo principal
│   └── mi_proyecto/
│       ├── calculadora.ex      # Módulo específico
│       └── utilidades.ex       # Funciones de ayuda
```

## 🎯 Crear Módulo Separado

`lib/mi_proyecto/calculadora.ex`:

```elixir
defmodule MiProyecto.Calculadora do
  def sumar(a, b), do: a + b
  def restar(a, b), do: a - b
end
```

`lib/mi_proyecto.ex`:

```elixir
defmodule MiProyecto do
  alias MiProyecto.Calculadora

  def demo do
    IO.puts("5 + 3 = #{Calculadora.sumar(5, 3)}")
  end
end
```

## 🚀 Ejercicio

Crea un proyecto con:
- Módulo principal
- 2-3 módulos secundarios
- Tests para cada módulo

## 📝 Resumen

* ✅ Múltiples módulos
* ✅ Alias para nombres cortos
* ✅ Organización profesional

---

**¡Organizas código como un profesional! 🏗️✨**

