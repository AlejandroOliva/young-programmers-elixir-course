# 🔄 Clase 9: Repaso Integrador

## 🎯 Objetivos

* 📚 Consolidar recursión, terminal y procesos
* 🏆 Proyecto que combine todo
* 🌟 Prepararse para el proyecto final

## 📖 ¿Qué Hemos Aprendido?

* ✅ Recursión y casos base
* ✅ Pattern matching avanzado
* ✅ Uso del terminal e IEx
* ✅ Módulos y organización
* ✅ Procesos básicos

## 🎮 Desafío Integrador

Crea una aplicación que use:
- Recursión para algún cálculo
- Terminal para interacción
- Pattern matching en funciones
- Módulos bien organizados

## 💻 Ejemplo: Gestor de Tareas Simple

```bash
$ elixir task_manager.ex
```

```elixir
defmodule TaskManager do
  def main(tasks \\\\ []) do
    IO.puts("\n=== GESTOR DE TAREAS ===")
    IO.puts("Tareas actuales: #{length(tasks)}")

    menu(tasks)
  end

  defp menu(tasks) do
    IO.puts("""
    \n1. Ver tareas
    2. Agregar tarea
    3. Salir
    """)

    case IO.gets("Opción: ") |> String.trim() do
      "1" -> show_tasks(tasks)
      "2" -> add_task(tasks)
      "3" -> IO.puts("¡Adiós!")
      _ -> menu(tasks)
    end
  end

  defp show_tasks([]) do
    IO.puts("No hay tareas")
    menu([])
  end

  defp show_tasks(tasks) do
    Enum.each(tasks, fn task ->
      IO.puts("- #{task}")
    end)

    menu(tasks)
  end

  defp add_task(tasks) do
    task = IO.gets("Nueva tarea: ") |> String.trim()
    new_tasks = [task | tasks]
    main(new_tasks)
  end
end

TaskManager.main()
```

## 📝 Resumen

* ✅ Integración de conceptos
* ✅ Aplicación completa
* ✅ Listo para proyecto final

---

**¡Estás listo para el proyecto final! 🌟**

