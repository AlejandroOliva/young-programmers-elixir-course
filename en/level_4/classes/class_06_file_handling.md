# 📁 Class 6: File Handling

## 🎯 Objectives: File I/O, JSON, persistence

```elixir
# Read file
{:ok, content} = File.read("file.txt")

# Write file
File.write("output.txt", "Content")

# JSON
json = Jason.encode!(%{data: "value"})
File.write("data.json", json)
```

---

**You persist data! 📁✨**

