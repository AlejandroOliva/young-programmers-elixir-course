# ⚡ Class 3: Basic LiveView

## 🎯 Interactivity without JavaScript

LiveView enables interactive apps without writing JS.

```elixir
defmodule MyAppWeb.CounterLive do
  use MyAppWeb, :live_view

  def mount(_params, _session, socket) do
    {:ok, assign(socket, count: 0)}
  end

  def handle_event("inc", _, socket) do
    {:noreply, assign(socket, count: socket.assigns.count + 1)}
  end
end
```

---

**Real-time web apps! ⚡✨**

