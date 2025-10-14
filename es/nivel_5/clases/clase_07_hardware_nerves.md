# 🔌 Clase 7: Hardware con Nerves

## 🎯 LEDs, Sensores y Actuadores

```elixir
# Controlar LED
Circuits.GPIO.open(18, :output)
Circuits.GPIO.write(18, 1)  # Encender

# Leer sensor
{:ok, temp} = BMP280.read_temperature()
```

Proyectos: Sistema monitoreo, home automation, robot.

---

**¡Programas hardware! 🔌✨**

