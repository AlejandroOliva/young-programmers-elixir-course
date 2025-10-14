# 🔄 Class 9: Integrating Review

## 🎯 Objectives

* 📚 Consolidate recursion, terminal and processes
* 🏆 Project combining everything
* 🌟 Prepare for final project

## 📖 What Have We Learned?

* ✅ Recursion and base cases
* ✅ Advanced pattern matching
* ✅ Terminal and IEx use
* ✅ Modules and organization
* ✅ Basic processes

## 🎮 Integrating Challenge

Create an application that uses:
- Recursion for some calculation
- Terminal for interaction
- Pattern matching in functions
- Well-organized modules

## 💻 Example: Simple Task Manager

```bash
$ elixir task_manager.ex
```

```elixir
defmodule TaskManager do
  def main(tasks \\\\ []) do
    IO.puts("\n=== TASK MANAGER ===")
    IO.puts("Current tasks: #{length(tasks)}")

    menu(tasks)
  end

  defp menu(tasks) do
    IO.puts("""
    \n1. View tasks
    2. Add task
    3. Exit
    """)

    case IO.gets("Option: ") |> String.trim() do
      "1" -> show_tasks(tasks)
      "2" -> add_task(tasks)
      "3" -> IO.puts("Goodbye!")
      _ -> menu(tasks)
    end
  end

  defp show_tasks([]) do
    IO.puts("No tasks")
    menu([])
  end

  defp show_tasks(tasks) do
    Enum.each(tasks, fn task ->
      IO.puts("- #{task}")
    end)

    menu(tasks)
  end

  defp add_task(tasks) do
    task = IO.gets("New task: ") |> String.trim()
    new_tasks = [task | tasks]
    main(new_tasks)
  end
end

TaskManager.main()
```

## 📝 Summary

* ✅ Integration of concepts
* ✅ Complete application
* ✅ Ready for final project

---

**You're ready for the final project! 🌟**

