# ⚡ Class 7: Basic Concurrency

## 🎯 Task and async/await

```elixir
# Execute tasks in parallel
task1 = Task.async(fn -> heavy_computation_1() end)
task2 = Task.async(fn -> heavy_computation_2() end)

result1 = Task.await(task1)
result2 = Task.await(task2)
```

## GenServer Introduction

Simple server that maintains state.

---

**Concurrent programming! ⚡✨**

