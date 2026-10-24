# Guía de desarrollo: especificaciones

Guía para el desarrollo de especificaciones con OpenSpec. Se aplica a todos los proyectos, con independencia de su lenguaje.

## Herramienta

- Las especificaciones se escriben y gestionan con OpenSpec.
- Cada proyecto mantiene su carpeta `openspec/` en la raíz del repositorio, versionada junto con el código.
- La versión de OpenSpec se fija en el proyecto. Los comandos se ejecutan con esa versión.

## Estructura

```
openspec/
├── specs/              # Especificaciones vigentes. Fuente de verdad del comportamiento del proyecto.
└── changes/            # Cambios en curso, pendientes de implementar o de archivar.
    └── archive/        # Cambios ya implementados y archivados, con fecha.
```

Cada cambio vive en `openspec/changes/<id-cambio>/` con los siguientes ficheros:

- `proposal.md`: por qué se hace el cambio y qué alcance tiene.
- `specs/<capacidad>/spec.md`: requisitos del cambio en formato delta (`ADDED`, `MODIFIED`, `REMOVED`) con escenarios.
- `design.md`: enfoque técnico, si el cambio lo necesita.
- `tasks.md`: lista de tareas de implementación con casillas.

## Cuándo se usa

- Toda funcionalidad nueva, cambio de comportamiento o cambio de contrato (API, eventos, esquemas de datos) requiere un cambio de OpenSpec antes de escribir el código.
- Las correcciones de errores se especifican solo si cambian el comportamiento esperado. Una corrección que restaura el comportamiento ya especificado no requiere cambio.
- Los cambios puramente técnicos sin efecto en el comportamiento (formateo, renombrados, actualizaciones de dependencias) no requieren especificación.

## Flujo

1. **Proponer**: crear el cambio en `openspec/changes/<id-cambio>/` con `proposal.md`, las especificaciones delta y, si aplica, `design.md` y `tasks.md`.
2. **Validar**: comprobar que el cambio es válido con la herramienta de OpenSpec antes de revisarlo.
3. **Revisar**: el cambio se revisa en el mismo PR que el código, o en un PR previo si la especificación requiere aprobación por separado.
4. **Implementar**: se siguen las tareas de `tasks.md` en orden. Cada tarea marcada como completada cumple sus escenarios.
5. **Archivar**: al hacer merge, el cambio se archiva. Las especificaciones delta se incorporan a `openspec/specs/` y el cambio pasa a `openspec/changes/archive/` con fecha.

## Reglas

- `openspec/specs/` solo se modifica a través de un cambio archivado. No se editan especificaciones vigentes directamente.
- Cada escenario de una especificación tiene al menos una prueba que lo verifica. Las pruebas siguen las guías de pruebas del lenguaje correspondiente.
- Un PR que implementa un cambio referencia su identificador en la descripción.
- Las especificaciones se escriben en español, como el resto de la documentación. Los identificadores de cambio y capacidad se escriben en minúsculas y separados por guiones, en inglés.
- Si la implementación se aparta de la especificación, el cambio se actualiza antes del merge. El código y la especificación no pueden quedar en desacuerdo.

## Relación con otras guías

- Ramas y PR: [git.md](git.md). Las ramas de un cambio siguen el formato `feature/<id-cambio>` o `fix/<id-cambio>`.
- Documentación de proyectos: [../documentation/projects.md](../documentation/projects.md). La carpeta `openspec/` se documenta en el `README.md` del proyecto.
- Tecnologías admitidas: [../technologies/python.md](../technologies/python.md) y [../technologies/react.md](../technologies/react.md).
