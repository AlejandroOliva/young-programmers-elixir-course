# 🏆 Prueba Final - Nivel 3

## 🎯 Demostración de Habilidades Avanzadas

¡Felicidades por llegar hasta aquí! Este nivel te ha llevado de Livebook al terminal, y de conceptos básicos a programación funcional real.

## 📋 El Proyecto: "Aplicación CLI Completa"

Vas a crear una **aplicación de línea de comandos** que combine todos tus conocimientos.

### Requisitos Obligatorios

✅ **1. Recursión** (al menos una función recursiva)  
✅ **2. Pattern matching** avanzado  
✅ **3. Estructuras de datos** (maps o tuplas)  
✅ **4. Pipe operator** (`|>`)  
✅ **5. Ejecutable desde terminal** (archivo .ex)  
✅ **6. Interacción con usuario** (IO.gets o similar)  
✅ **7. Modularización** (al menos 2 módulos)

### Opciones de Proyectos

#### 💰 Opción 1: Gestor de Finanzas Personal

Un programa que:
- Registra ingresos y gastos
- Calcula balance
- Muestra historial
- Guarda datos (lista en memoria)
- Categoriza transacciones
- Genera reportes simples

#### 📚 Opción 2: Sistema de Biblioteca

- Agregar libros (título, autor, año)
- Buscar por título o autor (recursión)
- Prestar/devolver libros
- Listar disponibles
- Sistema de usuarios simple

#### 🎮 Opción 3: Juego de Aventura Textual

- Navegación por ubicaciones (maps)
- Inventario de items
- Sistema de combate simple
- Guardar/cargar progreso
- Múltiples finales

#### 📝 Opción 4: To-Do List Avanzada

- Agregar/eliminar tareas
- Marcar como completadas
- Prioridades (alta, media, baja)
- Filtrar por estado
- Estadísticas (recursión para contar)

#### 🤖 Opción 5: Tu Idea

¡Crea algo único! Asegúrate de cumplir todos los requisitos.

## 🎯 Criterios de Evaluación

### ⭐ Nivel Funcional

- Incluye 5 de 7 requisitos
- Funciona sin errores críticos
- Se puede ejecutar desde terminal
- Código organizado básicamente

### ⭐⭐ Nivel Competente

- Incluye todos los 7 requisitos
- Funciona correctamente
- Código bien organizado
- Buen uso de recursión y pattern matching
- Interacción clara con usuario

### ⭐⭐⭐ Nivel Experto

- Todos los requisitos + extras
- Código limpio y comentado
- Manejo de errores
- Funcionalidades adicionales
- Documentación de uso
- Tests básicos (opcional)

## 🛠️ Estructura Sugerida

```elixir
# mi_proyecto.ex

defmodule MiProyecto do
  @moduledoc """
  [Descripción de qué hace tu proyecto]
  """

  def main do
    mostrar_bienvenida()
    menu_principal()
  end

  defp mostrar_bienvenida do
    IO.puts("\n=== BIENVENIDO A [TU PROYECTO] ===\n")
  end

  defp menu_principal do
    IO.puts("""
    1. Opción 1
    2. Opción 2
    3. Salir
    """)

    opcion = IO.gets("Elige una opción: ") |> String.trim()

    case opcion do
      "1" -> # tu código
      "2" -> # tu código
      "3" -> IO.puts("¡Adiós!")
      _ -> 
        IO.puts("Opción inválida")
        menu_principal()
    end
  end
end

# Módulo auxiliar
defmodule MiProyecto.Helpers do
  # Funciones de ayuda aquí
end

# Para ejecutar
MiProyecto.main()
```

## 💻 Cómo Ejecutar

```bash
# Desde terminal
$ elixir mi_proyecto.ex

# O desde IEx
$ iex mi_proyecto.ex
iex> MiProyecto.main()
```

## 📝 Documentación Requerida

Crea un archivo `README.md` para tu proyecto:

```markdown
# [Nombre del Proyecto]

## Descripción
[Qué hace tu proyecto]

## Cómo Usarlo
```bash
$ elixir nombre_archivo.ex
```

## Opciones del Menú
1. [Opción 1] - [Qué hace]
2. [Opción 2] - [Qué hace]
...

## Ejemplos
[Capturas o ejemplos de uso]

## Autor
[Tu nombre]
```

## 🆘 Si Te Atascas

1. **Empieza simple** - Versión básica primero
2. **Prueba por partes** - Cada función independiente
3. **Usa IEx** - Para probar funciones rápido
4. **Revisa clases** - Especialmente recursión y pattern matching
5. **Pide ayuda** - Tu mentor está para ayudarte

## 🎯 Rúbrica Detallada

| Criterio | Básico | Competente | Experto |
|----------|--------|------------|---------|
| Recursión | Intenta usar | Usa correctamente | Múltiples usos elegantes |
| Pattern Matching | Básico | Avanzado | Muy sofisticado |
| Terminal | Ejecuta | Usa bien | Dominio completo |
| Código | Funciona | Organizado | Limpio y documentado |
| Creatividad | Sigue ejemplo | Personaliza | Única y original |

## 🎉 Al Completar

Has demostrado que puedes:

✅ Pensar recursivamente  
✅ Usar pattern matching avanzado  
✅ Trabajar en terminal profesionalmente  
✅ Organizar código en módulos  
✅ Crear aplicaciones completas  
✅ Programar como desarrollador junior

**Esto es INCREÍBLE. 🌟**

## 🚀 Próximos Pasos

### Nivel 4: Mix y Proyectos Reales

Si estás listo, el Nivel 4 te enseñará:
- Mix (gestor de proyectos Elixir)
- Dependencias y bibliotecas
- Testing
- Proyectos estructurados
- ¡Y mucho más!

### Seguir Practicando

- Exercism.org (ejercicios intermedios-avanzados)
- Mejora tu proyecto
- Crea más aplicaciones CLI
- Explora bibliotecas de Hex

---

## 💝 Mensaje Final

> Comenzaste este nivel en Livebook, con interfaces visuales y botones.
> 
> Terminas dominando el terminal, recursión, y creando aplicaciones completas desde cero.
> 
> Esa transformación es ENORME.
> 
> Ya no eres un principiante. Eres un programador con habilidades reales.
> 
> El código que escribes podría resolver problemas reales. Podría ayudar a otros. Podría ser el inicio de algo grande.
> 
> **Sigue creando. Sigue aprendiendo. El cielo es el límite.** 🚀
> 
> **¡Adelante, desarrollador! 💻✨**

---

**¡Éxito con tu proyecto final! 🎓🏆**

