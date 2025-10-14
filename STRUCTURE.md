# 📁 Repository Structure

## 🌍 Bilingual Organization

This repository is organized with parallel language versions in separate folders:

```
young-programmers-elixir-course/
│
├── 📄 README.md                    # Bilingual landing page
├── 📄 CONTRIBUTING.md              # Contribution guidelines (bilingual)
├── 📄 STRUCTURE.md                 # This file
├── 📄 .gitignore                   # Git ignore rules
│
├── 🇬🇧 en/                          # ENGLISH VERSION
│   ├── 📄 README.md                # English course introduction
│   ├── 📄 TRANSLATION_STATUS.md    # Translation progress tracker
│   ├── 📂 global_guide/            # Installation and setup guides
│   ├── 📂 level_1/                 # Ages 8-9: Visual intro with Livebook
│   ├── 📂 level_2/                 # Ages 10-11: Logic and structures
│   ├── 📂 level_3/                 # Ages 12-13: Functional programming
│   ├── 📂 level_4/                 # Ages 14-15: Professional development
│   ├── 📂 level_5/                 # Ages 16+: Phoenix and Nerves
│   └── 📄 external_resources.md    # Community resources and links
│
└── 🇪🇸 es/                          # SPANISH VERSION (COMPLETE)
    ├── 📄 README.md                # Introducción al curso en español
    ├── 📂 guia_global/             # Guías de instalación y configuración
    ├── 📂 nivel_1/                 # 8-9 años: Intro visual con Livebook
    │   ├── README.md
    │   ├── guia_mentores.md
    │   ├── prueba_final.md
    │   └── clases/                 # 10 clases completas (.livemd)
    ├── 📂 nivel_2/                 # 10-11 años: Lógica y estructuras
    │   ├── README.md
    │   ├── guia_mentores.md
    │   └── prueba_final.md
    ├── 📂 nivel_3/                 # 12-13 años: Programación funcional
    │   ├── README.md
    │   ├── guia_mentores.md
    │   └── prueba_final.md
    ├── 📂 nivel_4/                 # 14-15 años: Desarrollo profesional
    │   ├── README.md
    │   ├── guia_mentores.md
    │   └── prueba_final.md
    ├── 📂 nivel_5/                 # 16+ años: Phoenix y Nerves
    │   ├── README.md
    │   ├── guia_mentores.md
    │   └── prueba_final.md
    └── 📄 recursos_externos.md     # Recursos de la comunidad

```

## 📊 Content Status

### Spanish (es/) - ✅ Complete
- ✅ All 5 levels fully developed
- ✅ 50 classes total (10 per level)
- ✅ Global installation guides
- ✅ Mentor guides for each level
- ✅ Final assessments
- ✅ External resources
- ✅ Troubleshooting guide

### English (en/) - 🔄 In Progress
- ✅ Main structure created
- ✅ README translated
- 🔄 Guides being translated
- 🔄 Level content being translated
- See [en/TRANSLATION_STATUS.md](en/TRANSLATION_STATUS.md) for details

## 🔀 Git Workflow

### Why This Structure?

✅ **Single source of truth** - One main branch  
✅ **Synchronized changes** - Updates to both languages in same commit  
✅ **Clear history** - Easy to track what changed in each language  
✅ **Simple collaboration** - Contributors know where to work  
✅ **No merge conflicts** - No branch synchronization issues  

### Commit Convention

```bash
[EN/ES] Changes affecting both versions
[EN] English-only changes
[ES] Spanish-only changes
[BOTH] Structural changes
```

### Example Workflow

```bash
# Making changes to both versions
git checkout -b feature/new-class-level3

# Edit both language versions
vim es/nivel_3/clases/clase_06_nueva.livemd
vim en/level_3/classes/class_06_new.livemd

# Commit together
git add es/nivel_3/clases/clase_06_nueva.livemd
git add en/level_3/classes/class_06_new.livemd
git commit -m "[EN/ES] Add class 6 about advanced recursion"

# Push and create PR
git push origin feature/new-class-level3
```

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for:
- Translation guidelines
- Content improvement process
- Code of conduct
- How to report issues

## 📝 Notes

- Both versions maintain the same structure
- English folder names use underscores: `global_guide`, `level_1`
- Spanish folder names use underscores: `guia_global`, `nivel_1`
- All Livebook notebooks use `.livemd` extension
- Markdown files use `.md` extension

---

**Last updated:** January 2025

