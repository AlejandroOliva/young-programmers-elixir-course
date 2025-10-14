# ⚡ Clase 7: Concurrencia Básica

## 🎯 Task y async/await

```elixir
# Ejecutar tareas en paralelo
task1 = Task.async(fn -> heavy_computation_1() end)
task2 = Task.async(fn -> heavy_computation_2() end)

result1 = Task.await(task1)
result2 = Task.await(task2)
```

## GenServer Introducción

Servidor simple que mantiene estado.

---

**¡Programación concurrente! ⚡✨**

