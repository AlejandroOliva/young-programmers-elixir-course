# 🛣️ Clase 2: Rutas y Controladores

## 🎯 MVC en Phoenix: Routes, Controllers, Views

```elixir
# router.ex
get "/hello", PageController, :hello

# page_controller.ex
def hello(conn, _params) do
  render(conn, :hello)
end
```

Aprende a crear rutas, controladores y vistas en Phoenix.

---

**¡Web development MVC! 🛣️✨**

