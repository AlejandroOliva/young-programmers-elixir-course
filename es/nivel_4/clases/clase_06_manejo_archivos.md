# 📁 Clase 6: Manejo de Archivos

## 🎯 Objetivos: File I/O, JSON, persistencia

```elixir
# Leer archivo
{:ok, content} = File.read("file.txt")

# Escribir archivo
File.write("output.txt", "Contenido")

# JSON
json = Jason.encode!(%{data: "value"})
File.write("data.json", json)
```

---

**¡Persistes datos! 📁✨**

