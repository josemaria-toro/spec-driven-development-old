# Instrucciones para agentes

Este repositorio es Spec Driven Development, un repositorio que sirve como plantilla para crear aplicaciones utilizando agentes de inteligencia artificial, siguiendo el estandar Spec Driven Development.

## Primera ejecución

Antes de cualquier otra tarea, cuenta los commits con `git rev-list --count --all`. Si devuelve `0` o `1`, sigue el procedimiento de [onboarding](.harness/development/onboarding.md). Si hay más, ya se hizo y no se ejecuta.

## Guías obligatorias

Antes de escribir, modificar o revisar código, lee las guías correspondientes en `.harness/` y aplícalas. Las guías son la fuente de verdad. Si una instrucción de este fichero contradice una guía, avisa al usuario y sigue la guía.

- Código Python: `.harness/development/python.md`, `.harness/security/python.md`, `.harness/technologies/python.md`, `.harness/guardrails/python.md`.
- Código React: `.harness/development/react.md`, `.harness/security/react.md`, `.harness/technologies/react.md`, `.harness/guardrails/react.md`.
- Arquitectura de backend (DDD, hexagonal y Clean Architecture): `.harness/architecture/python.md`.
- Arquitectura de frontend (por funcionalidad): `.harness/architecture/react.md`.
- Documentación de proyectos: `.harness/documentation/projects.md`.
- Ramas, commits y PR: `.harness/development/git.md`.
- Especificaciones (flujo OpenSpec `propose`, `apply`, `archive`): `.harness/development/specifications.md`.
- Despliegues: `.harness/development/deployment.md`.
- Licencias: `.harness/licenses/`.
- Primera ejecución: `.harness/development/onboarding.md`.

Si una tecnología no aparece en la guía de tecnologías admitidas, no la uses. Pregunta al usuario antes de incorporarla.

## Reglas clave

- Los guardarraíles de `.harness/guardrails/` bloquean el merge si se incumplen. Compruébalos antes de dar un cambio por listo.
- Las funcionalidades nuevas y los cambios de comportamiento se especifican con OpenSpec antes de implementarlos, sin omitir fases.
- No hagas commits directos en `main` ni cambies el autor de los commits. No hagas push sin confirmación del usuario.
- Nunca escribas contraseñas, claves, tokens ni otra información sensible en código, documentación o ejemplos.

## Antes de terminar una tarea

1. Ejecuta las comprobaciones del proyecto: formateo, linter, tipos, pruebas y cobertura.
2. Revisa los guardarraíles aplicables. Si hay un cambio de OpenSpec asociado, confirma que ha pasado por `propose` y `apply`, que está validado, que sus tareas y escenarios están cubiertos y que está archivado con `archive`.
3. Actualiza la documentación afectada.
4. Resume al usuario qué has cambiado y qué comprobaciones has ejecutado. Si alguna no se ha podido ejecutar, dilo.
