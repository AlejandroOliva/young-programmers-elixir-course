# 👨‍👩‍👧‍👦 Guía para Mentores - Nivel 3

## 🎯 Visión General

**Público:** 12-13 años  
**Prerrequisitos:** Nivel 2 completo  
**Particularidad:** Transición de Livebook a terminal

### Características Cognitivas (12-13 años)

- Pensamiento abstracto más desarrollado
- Pueden manejar conceptos recursivos
- Mayor capacidad de planificación
- Pueden trabajar con herramientas profesionales
- Empiezan a interesarse en "cómo funciona realmente"

## 🎓 Objetivos Pedagógicos

### Objetivo Principal

> Desarrollar pensamiento funcional avanzado y autonomía técnica mediante recursión, pattern matching y transición al entorno de desarrollo profesional.

### Objetivos Específicos

**Conocimientos:**
- Recursión y casos base
- Pattern matching avanzado
- Pipe operator `|>`
- Procesos y concurrencia básica
- Uso de terminal y IEx
- Organización de código en módulos

**Habilidades:**
- Resolver problemas recursivamente
- Usar terminal con confianza
- Crear programas ejecutables
- Debuggear sin interfaz visual
- Leer mensajes de error de terminal

**Actitudes:**
- Transición de "niño que programa" a "programador joven"
- Comodidad con herramientas profesionales
- Orgullo por dominar terminal
- Perseverancia con conceptos abstractos

## 🔄 La Transición al Terminal

### Por Qué es Importante

Livebook es excelente para aprender, pero:
- La mayoría del desarrollo real usa terminal
- Terminal da más control y poder
- Es importante saber usar ambas herramientas
- Prepara para Nivel 4 (Mix projects)

### Cómo Gestionar la Transición

**Semanas 1-2 (Clases 1-4):**
- Todavía en Livebook
- Conceptos más avanzados pero entorno familiar
- Prepara mentalmente para el cambio

**Semana 3 (Clase 5):**
- **Momento clave:** Introducción al terminal
- Hacer que sea emocionante, no intimidante
- "Ahora programas como los profesionales"
- Mucho acompañamiento

**Semanas 4-5 (Clases 6-10):**
- Práctica mixta
- Algunos conceptos se ven mejor en Livebook
- Algunos proyectos se hacen en terminal
- Gradualmente más autonomía

### Desafíos Comunes y Soluciones

**"El terminal me asusta"**
- Normal. Es diferente.
- Empezar con cosas muy simples
- Éxito temprano construye confianza
- Enseñar comandos básicos uno a la vez

**"Extraño los botones de Livebook"**
- Válido. Livebook es más amigable visualmente.
- Mostrar ventajas del terminal (rapidez, control)
- Pueden seguir usando Livebook cuando quieran
- Terminal para cosas nuevas, Livebook para experimentar

**"Los errores se ven diferentes"**
- Enseñar a leer stacktraces
- Práctica con errores intencionales
- Normalizar: todos leen errores constantemente

## 🔄 Recursión

### Por Qué es Difícil

Recursión require pensar de forma no lineal:
- La función se llama a sí misma
- Hay que confiar que "eventualmente termina"
- Casos base no son intuitivos al inicio

### Estrategias de Enseñanza

**1. Analogía de Muñecas Rusas**
- Cada muñeca contiene una más pequeña
- Hasta llegar a la más pequeña (caso base)
- Luego todo se "cierra" de vuelta

**2. Visualización**
- Dibujar el "call stack"
- Mostrar cada llamada con flechas
- Ver cómo se "desenrolla"

**3. Ejemplos Graduales**
```elixir
# Muy simple: cuenta regresiva
def cuenta(0), do: IO.puts("¡Despegue!")
def cuenta(n) do
  IO.puts(n)
  cuenta(n - 1)
end

# Más complejo: suma de lista
def suma([]), do: 0
def suma([cabeza | cola]), do: cabeza + suma(cola)

# Avanzado: fibonacci
def fib(0), do: 0
def fib(1), do: 1
def fib(n), do: fib(n - 1) + fib(n - 2)
```

**4. Debugging Juntos**
- Agregar IO.puts para ver qué pasa
- Seguir la ejecución paso a paso
- Identificar casos base

### Ejercicios Recomendados

Progresión natural:
1. Cuenta regresiva (más simple)
2. Sumar números de 1 a n
3. Longitud de lista
4. Suma de elementos de lista
5. Revertir lista
6. Fibonacci
7. Factorial

## 💻 Terminal Básico

### Comandos Esenciales

Enseña estos gradualmente:

```bash
# Navegación
pwd           # Dónde estoy
ls            # Qué hay aquí
cd directorio # Ir a directorio
cd ..         # Subir un nivel

# Elixir
iex           # Abrir consola interactiva
elixir archivo.ex  # Ejecutar archivo
```

### IEx Básico

```elixir
# En IEx
h(Enum.map)   # Ayuda sobre función
r(MiModulo)   # Recargar módulo
c "archivo.ex"  # Compilar archivo
```

### Flujo de Trabajo

1. Escribir código en editor (VS Code, etc.)
2. Guardar archivo (.ex)
3. Ejecutar en terminal
4. Ver resultado
5. Corregir y repetir

## 📊 Evaluación

### Señales de Progreso

**Comprende recursión:**
- Puede explicar caso base
- Identifica cuándo usar recursión
- Puede escribir función recursiva simple

**Usa terminal:**
- Navega directorios sin miedo
- Ejecuta código desde terminal
- Lee errores de terminal

**Pattern matching:**
- Usa en funciones
- Entiende orden de cláusulas
- Puede hacer matching en estructuras

### Listo para Nivel 4

- ✅ Domina conceptos de Nivel 3
- ✅ Cómodo con terminal
- ✅ Puede crear programas completos sin Livebook
- ✅ Entiende organización de código
- ✅ Quiere aprender Mix y proyectos reales

## 💡 Recursos Adicionales

### Recursión

- Visualizadores online de recursión
- Diagramas de call stack
- Videos sobre "cómo piensa recursivamente"

### Terminal

- Cheatsheet de comandos
- Tutorial interactivo de terminal
- Práctica con juegos de terminal

### Exercism

Ejercicios recomendados:
- Recursion (track)
- List Ops
- Sum of Multiples
- RNA Transcription
- Roman Numerals

## ✅ Checklist del Mentor

### Antes del Nivel

- [ ] El estudiante domina Nivel 2
- [ ] Terminal disponible y funcional
- [ ] Editor de texto configurado
- [ ] Probé la transición yo mismo

### Durante Nivel

- [ ] Estudiante entiende recursión básica
- [ ] Se siente cómodo con terminal
- [ ] Puede ejecutar código sin Livebook
- [ ] Mantiene motivación con el cambio

### Al Finalizar

- [ ] Completó proyecto final mixto
- [ ] Usa terminal regularmente
- [ ] Entiende cuándo usar cada herramienta
- [ ] Listo para Mix (Nivel 4)

## 💪 Mensaje para Mentores

> "Nivel 3 es transformacional. Los estudiantes pasan de 'usar herramientas educativas' a 'usar herramientas profesionales'. Esta transición puede ser intimidante, pero también es increíblemente empoderadora. Tu rol es hacer que se sientan como programadores 'de verdad', porque lo son. La paciencia con la curva de aprendizaje del terminal, combinada con emoción por su progreso, hace toda la diferencia."

---

**¡Adelante con la transición! 🚀💻**

