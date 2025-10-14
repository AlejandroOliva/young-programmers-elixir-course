# 🏆 Prueba Final - Nivel 1

## 🎯 ¡Hora de Brillar!

¡Felicidades por llegar hasta aquí! Esta prueba es tu oportunidad para demostrar todo lo increíble que has aprendido.

**🌟 Recuerda:** Esta no es un examen para aprobar o reprobar. Es una celebración de tus logros. ¡Diviértete creando!

---

## 📋 ¿Qué Vamos a Hacer?

Vas a crear **tu propio programa especial** que combine todo lo que aprendiste:

- ✨ Colores y visuales
- 💬 Mensajes y textos
- 📦 Variables que guardan información
- 🎮 Interactividad con el usuario
- 🎨 Creatividad y personalización

---

## 🎨 El Proyecto: "Mi Mundo Interactivo"

### Descripción

Vas a crear un programa que:
1. Te saluda por tu nombre
2. Te pregunta cosas sobre ti
3. Muestra información con colores
4. Crea un dibujo o patrón visual
5. Te cuenta una mini historia

### Requisitos (Lo que DEBE tener)

✅ **1. Saludo personalizado** (Clase 4)
- Pedir el nombre del usuario
- Mostrar un mensaje de bienvenida

✅ **2. Preguntas interactivas** (Clase 5)
- Al menos 3 preguntas al usuario
- Ejemplos: color favorito, edad, animal favorito, etc.
- Guardar las respuestas en variables

✅ **3. Mostrar con colores** (Clase 3)
- Usar Kino para mostrar algo con colores
- Al menos 3 colores diferentes

✅ **4. Crear un dibujo** (Clase 8)
- Dibujar algo con caracteres (ASCII art)
- Puede ser simple: una casa, un árbol, una cara, etc.

✅ **5. Mini historia** (Clase 7)
- Usar la información que pediste
- Crear un mensaje o historia personalizada
- Ejemplo: "Hola [nombre], tu color favorito es [color] y tienes [edad] años..."

---

## 🎯 Instrucciones Paso a Paso

### Paso 1: Preparación (5 minutos)

1. Abre Livebook
2. Crea un nuevo notebook
3. Nómbralo: "Mi Mundo Interactivo - [Tu Nombre]"
4. ¡Respira y sonríe! Vas a hacerlo genial.

### Paso 2: Instalar Kino (5 minutos)

En la primera celda, escribe:

```elixir
Mix.install([
  {:kino, "~> 0.12.0"}
])
```

Ejecuta y espera a que termine.

### Paso 3: Crear tu programa (30-40 minutos)

Sigue estos pasos, ¡pero siéntete libre de cambiar el orden o agregar más!

#### Celda 1: Saludo Inicial
```elixir
# Tu código aquí
# Ejemplo: IO.puts("¡Bienvenido a mi mundo!")
```

#### Celda 2: Pedir información
```elixir
# Crear inputs para preguntar
# Ejemplo:
nombre_input = Kino.Input.text("¿Cómo te llamas?")
# ... más inputs ...
```

#### Celda 3: Mostrar los inputs
```elixir
# Mostrar los inputs para que el usuario pueda escribir
nombre_input
# ... más inputs ...
```

#### Celda 4: Leer las respuestas
```elixir
# Guardar lo que escribió el usuario
nombre = Kino.Input.read(nombre_input)
# ... leer más respuestas ...
```

#### Celda 5: Mostrar con colores
```elixir
# Usar Kino para mostrar colores
# Ejemplo:
Kino.Markdown.new("# ¡Hola #{nombre}! 🌟") |> Kino.render()
# ... tu creatividad aquí ...
```

#### Celda 6: Dibujo ASCII
```elixir
# Crear tu dibujo
# Ejemplo:
IO.puts("  ^  ")
IO.puts(" /_\\ ")
IO.puts("/___\\")
```

#### Celda 7: Historia personalizada
```elixir
# Combinar toda la información en un mensaje o historia
# Usa #{nombre}, #{color_favorito}, etc.
```

---

## 💡 Ideas y Ejemplos

### Temas que puedes elegir:

🏡 **Mi Casa Virtual**
- Pregunta: color de la casa, número de ventanas, mascotas
- Dibujo: una casa
- Historia: "Esta es tu casa [color]..."

🐾 **Mi Mascota Imaginaria**
- Pregunta: tipo de mascota, nombre, color
- Dibujo: el animal
- Historia: aventuras con la mascota

🚀 **Mi Viaje Espacial**
- Pregunta: planeta favorito, nave espacial, alien amigo
- Dibujo: cohete o planeta
- Historia: tu aventura en el espacio

🎨 **Mi Galería de Arte**
- Pregunta: colores favoritos, formas preferidas
- Dibujo: varios patrones
- Historia: descripción de tu arte

🏰 **Mi Castillo Mágico**
- Pregunta: nombre del castillo, color de banderas, dragón o unicornio
- Dibujo: castillo
- Historia: qué pasa en tu castillo

### Inspiración de Dibujos

```
Casa:
  /\
 /  \
/____\
|    |
|____|

Árbol:
  🌳
  /|\
 / | \
   |

Cara Feliz:
 ^  ^
  ^^
 \__/

Sol:
 \ | /
  \|/
 --☀--
  /|\
 / | \

Estrella:
   *
  ***
   *
```

---

## 🎯 Criterios de Evaluación

No hay "aprobado" o "reprobado", pero puedes autoevaluarte:

### ⭐ Nivel Exploradora/Explorador
- Completé al menos 3 de los 5 requisitos
- Mi programa funciona (aunque tenga errores pequeños)
- Pedí ayuda cuando la necesité
- Me divertí haciéndolo

### ⭐⭐ Nivel Programadora/Programador
- Completé los 5 requisitos
- Mi programa funciona sin errores
- Personalicé con mis propias ideas
- Estoy orgulloso de mi creación

### ⭐⭐⭐ Nivel Maga/Mago del Código
- Completé los 5 requisitos con extras creativos
- Mi programa es interactivo y divertido
- Agregué cosas que no estaban en las instrucciones
- Quiero mostrarlo a todos

**¡Cualquier nivel es genial! Lo importante es que lo intentaste y aprendiste.** 🌟

---

## ⏰ Tiempo Sugerido

- **Opción 1:** 1 sesión de 1 hora
  - Para hacer un proyecto simple pero completo

- **Opción 2:** 2 sesiones de 1 hora
  - Primera sesión: planear y empezar
  - Segunda sesión: completar y perfeccionar

- **Opción 3:** En casa durante una semana
  - Trabajar un poco cada día
  - Pedir ayuda cuando lo necesites

---

## 🆘 Si Te Atascas

### Estrategias:

1. **Respira profundo** 🧘
   - Los mejores programadores se atascan todo el tiempo
   
2. **Lee el mensaje de error** 👀
   - A veces dice exactamente qué está mal
   
3. **Busca en clases anteriores** 📚
   - Revisa notebooks de clases que ya hiciste
   - Copia y adapta código que funcionó
   
4. **Simplifica** ✂️
   - Si algo es muy complicado, hazlo más simple
   - Puedes agregar complejidad después
   
5. **Pide ayuda** 🙋
   - Tu mentor está para ayudarte
   - Explicar el problema a alguien a veces lo resuelve

### ¿Dónde buscar ayuda?

- Notebooks de clases 1-10
- Guía para mentores (tu mentor la tiene)
- Pregunta a tu mentor
- Busca en ejemplos del curso

---

## 🎁 Después de Terminar

### Guarda tu trabajo:

1. **Guarda el notebook:**
   - `Ctrl+S` (o `Cmd+S` en Mac)
   - Ponle un nombre claro

2. **Haz capturas de pantalla:**
   - De tu código
   - De tu programa funcionando
   - Para recordar tu logro

3. **Muéstralo:**
   - A tu familia
   - A tus amigos
   - A otros compañeros del curso

### Reflexiona:

**Pregúntate:**
- ¿Qué fue lo más divertido?
- ¿Qué fue lo más difícil?
- ¿De qué estoy más orgulloso?
- ¿Qué agregaría si tuviera más tiempo?

**Escribe tus respuestas:**
Puedes crear una celda de Markdown en tu notebook:

```markdown
# Reflexión

## Lo más divertido:
[tu respuesta]

## Lo más difícil:
[tu respuesta]

## De lo que estoy orgulloso:
[tu respuesta]

## Qué agregaría:
[tu respuesta]
```

---

## 🎉 ¡Felicitaciones!

### Al completar esta prueba:

✅ **Demostraste que sabes:**
- Usar Livebook
- Escribir código en Elixir
- Crear programas interactivos
- Usar variables y funciones
- Hacer programas con colores
- Crear dibujos con código
- Personalizar y crear tus propias cosas

✅ **Desarrollaste:**
- Pensamiento lógico
- Creatividad
- Resolución de problemas
- Perseverancia
- Orgullo en tus logros

---

## 🚀 ¿Qué Sigue?

### Opciones:

**🎨 Mejora tu proyecto:**
- Agrega más preguntas
- Más colores y dibujos
- Una historia más larga
- Efectos de sonido (si aprendiste)

**🎮 Crea nuevos proyectos:**
- Un juego diferente
- Una calculadora especial
- Un generador de historias
- Lo que imagines

**📚 Continúa aprendiendo:**
- **[Nivel 2](../nivel_2/README.md)** si estás listo
- Más ejercicios de las clases
- Explora Exercism.org
- Inventa tus propios programas

---

## 💝 Mensaje Final

> **¡LO LOGRASTE!** 🎊
>
> Empezaste sin saber nada de programación, y ahora puedes crear programas interactivos con colores, dibujos, y que hablan contigo. Eso es INCREÍBLE.
>
> Recuerda: cada gran programador empezó exactamente donde estás tú ahora. La diferencia es que siguieron practicando, siguieron siendo curiosos, y siguieron creando.
>
> **Eres capaz de cosas asombrosas. ¡Sigue creando, sigue aprendiendo, sigue brillando!** ✨
>
> Con orgullo,
> Tu Curso de Elixir

---

## 📸 Comparte Tu Logro

**¡Queremos ver qué creaste!**

Comparte:
- Una captura de pantalla de tu proyecto
- Tu código
- Tu historia de qué aprendiste

Con:
- Tu mentor
- Tu familia
- Tus amigos
- (Opcional) En comunidades de Elixir con permiso de tus padres

---

**🌟 ¡A programar tu prueba final! ¡Tú puedes! 🚀**

---

## 👨‍👩‍👧‍👦 Nota para Mentores

**Evaluación y Feedback:**

Esta prueba es formativa, no sumativa. El objetivo es:
- ✅ Consolidar aprendizajes
- ✅ Construir confianza
- ✅ Celebrar logros
- ✅ Identificar áreas de mejora para futuro

**Al evaluar:**
- Enfócate en el esfuerzo más que en perfección
- Celebra la creatividad y personalización
- Identifica qué conceptos necesitan refuerzo
- Provee feedback específico y positivo

**Ejemplos de feedback:**
- "Me encantó cómo usaste [color/concepto], muy creativo"
- "Tu dibujo de [cosa] está genial, puedes ver tu progreso"
- "Noté que [concepto] te costó un poco, podemos repasarlo juntos"
- "La historia que creaste es muy divertida, tienes mucha imaginación"

**Si el estudiante está listo:**
- Prepara transición al Nivel 2
- Celebra oficialmente la graduación del Nivel 1
- Comparte esta prueba con familia/amigos

**Si necesita más tiempo:**
- Está bien, no hay prisa
- Repasa conceptos específicos que causen dificultad
- Más práctica con ejercicios similares
- Reconoce el progreso, no la falta de perfección

---

**¡Éxito! 🎓**

