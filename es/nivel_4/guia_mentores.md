# 👨‍👩‍👧‍👦 Guía para Mentores - Nivel 4

## 🎯 Visión General

**Público:** 14-15 años  
**Enfoque:** Desarrollo profesional con herramientas reales  
**Duración:** 10 clases de 1 hora

Este nivel marca la transición de "estudiante de programación" a "desarrollador junior".

## 🎓 Objetivos Pedagógicos

### Objetivo Principal

> Dominar herramientas y prácticas de desarrollo profesional, creando aplicaciones escalables y mantenibles con testing, dependencias y arquitectura apropiada.

### Competencias Clave

**Técnicas:**
- Mix para gestión de proyectos
- Testing automatizado con ExUnit
- Uso de dependencias externas
- Debugging sistemático
- Documentación de código

**Profesionales:**
- Organización de código
- Control de versiones (Git básico)
- Code review
- Mejores prácticas
- Trabajo en proyectos multi-archivo

**Metacognitivas:**
- Planificación de arquitectura
- Refactoring
- Optimización
- Aprendizaje autónomo

## 🔧 Mix: La Herramienta Central

### Por Qué Mix es Importante

Mix es el estándar de la industria para Elixir. Aprenderlo es esencial para:
- Proyectos reales
- Colaboración
- Deployment
- Integración con ecosistema

### Estructura de Proyecto Mix

```
mi_proyecto/
├── lib/
│   └── mi_proyecto.ex
├── test/
│   └── mi_proyecto_test.exs
├── mix.exs
├── README.md
└── .gitignore
```

Enseña cada parte gradualmente:
1. `lib/` - código fuente
2. `test/` - tests
3. `mix.exs` - configuración
4. Documentación

## 🧪 Testing

### Por Qué Enseñar Testing Temprano

- Es práctica profesional estándar
- Ayuda a pensar en casos edge
- Confidence al refactorizar
- Documentación ejecutable

### Progresión de Testing

**Clase 3:** Tests básicos
```elixir
test "suma dos números" do
  assert MiModulo.sumar(2, 2) == 4
end
```

**Clase 5:** Tests más complejos
```elixir
describe "calculadora" do
  test "maneja números negativos"
  test "maneja división por cero"
  test "redondea correctamente"
end
```

**Clase 9:** TDD (Test-Driven Development)
- Escribir test primero
- Ver fallar (red)
- Implementar (green)
- Refactorizar

## 🌐 Exercism Integration

Exercism es recurso fundamental en este nivel:

### Cómo Usar

1. **Ejercicios complementarios:** Uno por semana
2. **Mentoría:** Animar a pedir reviews
3. **Code reading:** Ver soluciones de otros
4. **Progresión:** Del track de Elixir

### Ejercicios Recomendados

- Two Fer
- Resistor Color
- RNA Transcription
- Protein Translation
- Robot Simulator
- Bank Account

## 📊 Evaluación

### Indicadores de Progreso

**Domina Mix:**
- Crea proyectos estructurados
- Configura dependencias
- Ejecuta comandos mix correctamente

**Escribe Tests:**
- Tests que verifican comportamiento
- Entiende assertions
- Identifica qué testear

**Organiza Código:**
- Módulos bien estructurados
- Separación de responsabilidades
- Código legible

**Trabaja Profesionalmente:**
- Commits significativos (si usa Git)
- Documentación clara
- Código limpio

### Listo para Nivel 5

✅ Domina Mix completamente  
✅ Escribe tests consistentemente  
✅ Crea proyectos multi-módulo  
✅ Entiende dependencias y Hex  
✅ Quiere aprender Phoenix/Nerves

## 💡 Recursos Adicionales

### Libros

- "Programming Elixir" - Dave Thomas
- "Elixir in Action" - Saša Jurić
- Documentación oficial de Mix

### Online

- Elixir School (sección Mix)
- ElixirCasts.io
- Exercism mentorship

### Herramientas

- VS Code con ElixirLS
- Credo (linter)
- Dialyzer (type checking)

## ✅ Checklist del Mentor

### Preparación

- [ ] Instalación de Mix verificada
- [ ] Editor con soporte Elixir
- [ ] Git básico configurado (opcional)
- [ ] Cuenta en Exercism creada

### Durante el Nivel

- [ ] Estudiante usa Mix regularmente
- [ ] Escribe tests para su código
- [ ] Organiza proyectos profesionalmente
- [ ] Completa ejercicios de Exercism

### Al Finalizar

- [ ] Portfolio de proyectos Mix
- [ ] Tests en todos los proyectos
- [ ] Código bien documentado
- [ ] Listo para frameworks (Phoenix)

## 💪 Mensaje para Mentores

> "Nivel 4 es donde los estudiantes se convierten en desarrolladores. Las herramientas son profesionales, las expectativas son más altas, y los proyectos son reales. Tu papel es mantener el entusiasmo mientras introduces rigor profesional. Balance entre 'libertad creativa' y 'mejores prácticas' es clave."

---

**¡Forma desarrolladores excepcionales! 🎓⚡**

