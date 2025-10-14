# 🛣️ Class 2: Routes and Controllers

## 🎯 MVC in Phoenix: Routes, Controllers, Views

```elixir
# router.ex
get "/hello", PageController, :hello

# page_controller.ex
def hello(conn, _params) do
  render(conn, :hello)
end
```

Learn to create routes, controllers and views in Phoenix.

---

**Web development MVC! 🛣️✨**

