# 🗄️ Clase 4: Base de Datos con Ecto

## 🎯 Persistencia con Ecto y PostgreSQL

```bash
mix phx.gen.schema User users name:string email:string age:integer
mix ecto.migrate
```

```elixir
# Crear usuario
{:ok, user} = Repo.insert(%User{name: "Ana", email: "ana@example.com", age: 16})

# Consultar
users = Repo.all(User)
```

---

**¡Bases de datos profesionales! 🗄️✨**

