# 🔌 Class 7: Hardware with Nerves

## 🎯 LEDs, Sensors and Actuators

```elixir
# Control LED
Circuits.GPIO.open(18, :output)
Circuits.GPIO.write(18, 1)  # Turn on

# Read sensor
{:ok, temp} = BMP280.read_temperature()
```

Projects: Monitoring system, home automation, robot.

---

**You program hardware! 🔌✨**

