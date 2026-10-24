# spec-driven-development

Repositorio plantilla para crear aplicaciones utilizando agentes de inteligencia artificial, siguiendo el estándar Spec Driven Development.

## Herramientas de desarrollo

- **OpenSpec 1.14.3**: versión fijada del proyecto para gestionar las especificaciones de `openspec/`.
- **Node.js**: la guía exige Node.js 22 LTS. El equipo inicial trabaja con Node.js 20.19.2, desviación aceptada hasta que se actualice el entorno.

## Estructura del repositorio

```
.
├── .claude/          # Comandos y skills de OpenSpec para Claude Code
├── .github/          # Plantillas de issues y configuración de Dependabot
├── .harness/         # Guías obligatorias para agentes y desarrolladores
│   ├── architecture/     # Arquitectura de backend (Python) y frontend (React)
│   ├── development/      # Git, especificaciones y desarrollo por lenguaje
│   ├── documentation/    # Guía de documentación de proyectos
│   ├── guardrails/       # Guardarraíles por lenguaje
│   ├── licenses/         # Licencias por lenguaje
│   ├── security/         # Seguridad por lenguaje
│   └── technologies/     # Tecnologías admitidas por lenguaje
├── CLAUDE.md         # Instrucciones para Claude Code
├── LICENSE
├── openspec/         # Especificaciones: specs/ (vigentes) y changes/ (en curso y archivados)
└── README.md
```
