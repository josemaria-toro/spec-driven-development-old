# Guardarraíles: React

Guía que incluye los guardarraíles definidos para aplicaciones basadas en React.

## Pruebas obligatorias

- Las pruebas unitarias, de integración y end-to-end son obligatorias.
- Ningún merge se puede completar si las pruebas unitarias, de integración o end-to-end fallan, no se ejecutan o no existen para el código modificado.
- Estas pruebas bloquean cualquier merge en `main`.

## Cobertura de código

- Es obligatorio alcanzar una cobertura de código del 80 %.
- Si la cobertura es inferior al 80 %, se bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Información sensible

- No se permite incluir en el código contraseñas, claves, tokens ni ningún otro tipo de información sensible.
- La presencia de este tipo de información en el código bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Detección automática de secretos

- La integración continua ejecuta `gitleaks` sobre el historial del PR y `pre-commit` lo ejecuta antes de cada commit.
- Un hallazgo bloquea el merge. Si es un falso positivo, se justifica en la configuración de `gitleaks`, no se ignora el fichero.
- Este requisito aplica a cualquier merge en `main`.

## Vulnerabilidades en librerías

- La detección de una vulnerabilidad de severidad alta o crítica en una librería utilizada por el proyecto bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Tecnologías no aprobadas

- Solo se pueden usar las tecnologías incluidas en la guía de tecnologías admitidas.
- La integración continua compara las dependencias de `package.json` con la guía de tecnologías admitidas mediante un script del proyecto (`scripts/`).
- El uso de una tecnología no aprobada bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Licencias de dependencias

- Todas las dependencias, directas y transitivas, deben tener una licencia compatible con GPL v3. La integración continua lo comprueba con `license-checker-rseidelsohn`.
- Una dependencia con licencia incompatible o desconocida bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Licencia

- La licencia del proyecto debe ser la definida en la guía de licencias para React (GNU GPL versión 3).
- Si la licencia no coincide con la definida, se bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Referencias limpias y ordenadas

- Las referencias no utilizadas (importaciones, variables, espacios de nombres) se eliminan.
- Las importaciones, espacios de nombres y métodos se ordenan correctamente según las reglas definidas en la guía de desarrollo.
- Si las referencias no están limpias u ordenadas, se bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Documentación actualizada

- La documentación del proyecto debe estar actualizada en el mismo PR que el cambio de código que la afecta.
- La plantilla de PR (`.github/pull_request_template.md`) incluye una lista de comprobación de documentación que el autor debe completar y el revisor verificar.
- Si la documentación no queda actualizada, se bloquea el merge.
- Este requisito aplica a cualquier merge en `main`.

## Especificaciones de OpenSpec

- La integración continua ejecuta `openspec validate --all --strict`. Un fallo bloquea el merge.
- Un PR que implementa un cambio no puede llegar a `main` con ese cambio sin archivar en `openspec/changes/` (salvo el PR previo solo de propuesta, según [la guía de especificaciones](../development/specifications.md)).
- Este requisito aplica a cualquier merge en `main`.
