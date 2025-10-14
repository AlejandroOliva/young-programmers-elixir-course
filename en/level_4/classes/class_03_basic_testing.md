# 🧪 Class 3: Basic Testing

## 🎯 Objectives

* 🧪 Write tests with ExUnit
* ✅ Assertions and verifications
* 🎯 Basic TDD

## 🧪 Your First Test

```elixir
defmodule CalculatorTest do
  use ExUnit.Case

  test "adds correctly" do
    assert Calculator.add(2, 2) == 4
  end

  test "subtracts correctly" do
    assert Calculator.subtract(5, 3) == 2
  end
end
```

## 🎯 Describe and Context

```elixir
defmodule CalculatorTest do
  use ExUnit.Case

  describe "add/2" do
    test "adds positive numbers" do
      assert Calculator.add(5, 3) == 8
    end

    test "adds negative numbers" do
      assert Calculator.add(-5, -3) == -8
    end
  end
end
```

## 🏆 Exercise

Create tests for all your functions with:
- Normal cases
- Edge cases
- Error handling

## 📝 Summary

* ✅ ExUnit for testing
* ✅ assert to verify
* ✅ describe to organize

---

**You write tests like a professional! 🧪✨**

