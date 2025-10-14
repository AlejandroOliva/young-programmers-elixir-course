# 🗄️ Class 4: Database with Ecto

## 🎯 Persistence with Ecto and PostgreSQL

```bash
mix phx.gen.schema User users name:string email:string age:integer
mix ecto.migrate
```

```elixir
# Create user
{:ok, user} = Repo.insert(%User{name: "Ana", email: "ana@example.com", age: 16})

# Query
users = Repo.all(User)
```

---

**Professional databases! 🗄️✨**

