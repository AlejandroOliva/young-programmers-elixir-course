# 🧪 Clase 3: Testing Básico

## 🎯 Objetivos

* 🧪 Escribir tests con ExUnit
* ✅ Assertions y verificaciones
* 🎯 TDD básico

## 🧪 Tu Primer Test

```elixir
defmodule CalculadoraTest do
  use ExUnit.Case

  test "suma correctamente" do
    assert Calculadora.sumar(2, 2) == 4
  end

  test "resta correctamente" do
    assert Calculadora.restar(5, 3) == 2
  end
end
```

## 🎯 Describe y Context

```elixir
defmodule CalculadoraTest do
  use ExUnit.Case

  describe "sumar/2" do
    test "suma números positivos" do
      assert Calculadora.sumar(5, 3) == 8
    end

    test "suma números negativos" do
      assert Calculadora.sumar(-5, -3) == -8
    end
  end
end
```

## 🏆 Ejercicio

Crea tests para todas tus funciones con:
- Casos normales
- Casos edge
- Manejo de errores

## 📝 Resumen

* ✅ ExUnit para testing
* ✅ assert para verificar
* ✅ describe para organizar

---

**¡Escribes tests como un profesional! 🧪✨**

