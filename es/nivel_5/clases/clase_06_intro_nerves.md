# 🤖 Clase 6: Introducción a Nerves

## 🎯 IoT con Elixir

Nerves permite programar hardware con Elixir.

```bash
export MIX_TARGET=rpi4
mix nerves.new mi_firmware
mix deps.get
mix firmware
mix burn  # Grabar en SD
```

Programa Raspberry Pi, controla LEDs, lee sensores.

---

**¡IoT con Elixir! 🤖✨**

