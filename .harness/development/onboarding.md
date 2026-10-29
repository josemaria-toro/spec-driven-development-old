# Guía de desarrollo: primera ejecución (onboarding)

Procedimiento que sigue el agente la primera vez que se ejecuta en el repositorio.

## Cuándo se ejecuta

Antes de cualquier otra tarea, cuenta los commits del repositorio en todas sus ramas, locales y remotas, con `git rev-list --count --all`. Si el repositorio no tiene commits (el comando devuelve `0`) o solo tiene el commit inicial (devuelve `1`), es la primera vez que se ejecuta un agente en este repositorio. En ese caso, sigue este procedimiento en orden antes de cualquier otra tarea.

Si hay más de un commit, el onboarding ya se ha hecho y no se ejecuta.

## 1. Saludo

Saluda al usuario, explica en pocas líneas los pasos que vas a seguir y pregunta lo que necesites para continuar.

## 2. Descripción del repositorio

- Pide al usuario una descripción del repositorio: qué es, para quién es y qué objetivo tiene.
- Espera su respuesta antes de continuar.
- Con esa descripción, actualiza `README.md` (la descripción y la estructura del repositorio) y `AGENTS.md` (la primera línea y cualquier dato de contexto que haya cambiado). No añadas contenido que el usuario no haya indicado.

## 3. Identidad de git

- Pide el nombre y el correo del usuario. No los supongas a partir del contexto de la sesión.
- Configúralos en el repositorio, de forma local: `git config --local user.name` y `git config --local user.email`.
- Verifica los valores con `git config --local --get`.
- Si ya hay valores locales, muéstralos y confirma antes de cambiarlos.

## 4. OpenSpec

- Comprueba si OpenSpec está instalado (`openspec --version`) y si el proyecto está inicializado (existe la carpeta `openspec/`).
- Si no está instalado, instálalo. Requiere Node.js 20 o superior. Si Node.js no está disponible, indícalo y pide al usuario que lo instale o autoriza su instalación (ver "Permisos y credenciales").
- Si no está inicializado, inicialízalo siguiendo la documentación oficial de la versión instalada y [la guía de especificaciones](specifications.md).
- Fija la versión de OpenSpec en el proyecto, como indica esa guía.

## 5. Estructura de ramas

- Lee [la guía de estrategia de ramas](git.md) y comprueba las ramas locales y remotas.
- Si falta `main`, indícalo al usuario y créala desde el HEAD actual.
- Si existen otras ramas permanentes de estrategias anteriores (por ejemplo, `develop` o `pre-release`), indícalo al usuario. No las elimines sin su confirmación.
- Cambia a `main`. Es el punto de partida de todo el trabajo.
- Si hay cambios sin commitear que impedirían el cambio de rama, para y pregunta al usuario qué hacer con ellos. No los descartes ni los incluyas en un commit sin confirmación.
- No hagas push de ninguna rama sin confirmación del usuario. Las reglas de protección de ramas en el remoto no se pueden configurar desde el repositorio local. Indícalas en el resumen como pendientes si no están configuradas.

## 6. Contexto del proyecto

Pregunta qué contendrá el repositorio. Puede ser más de un tipo.

- **Backend**: pide las tecnologías que quiere usar. Crea el scaffolding de backend según [la guía de arquitectura de Python](../architecture/python.md), [las tecnologías admitidas de Python](../technologies/python.md) y [los guardarraíles de Python](../guardrails/python.md). Se crea en `backend/`.
- **Frontend**: pide las tecnologías que quiere usar. Crea el scaffolding de frontend según [la guía de arquitectura de React](../architecture/react.md), [las tecnologías admitidas de React](../technologies/react.md) y [los guardarraíles de React](../guardrails/react.md). Se crea en `frontend/`.
- **Otro tipo de proyecto**: pide el tipo, el nombre y las tecnologías que quiere usar. No hay scaffolding automático para este tipo todavía.

Para todos los proyectos, pide las tecnologías al usuario, aunque el scaffolding automático solo admita Python (backend) y React (frontend). Compáralas con la guía de tecnologías admitidas del lenguaje correspondiente. Si una tecnología no está admitida, no la incorpores hasta que el usuario lo apruebe. Si no hay scaffolding automático para el tipo de proyecto, no crees la estructura hasta tener las tecnologías definidas y validadas.

## 7. Scaffolding

- Trabaja en una rama `chore/scaffolding-inicial` creada desde `main`. No hagas commits directos en `main`.
- Crea la estructura de cada proyecto siguiendo sus guías. Incluye la configuración de herramientas (formateo, linter, tipos, pruebas con cobertura mínima del 80 %, pre-commit), el `README.md` según [la guía de documentación de proyectos](../documentation/projects.md) y un `.gitignore` acorde a la tecnología.
- Incluye al menos una prueba de humo por proyecto, para que las comprobaciones se puedan ejecutar desde el primer momento.
- No crees código de negocio. El scaffolding solo contiene la estructura, la configuración y los ejemplos mínimos necesarios.
- Haz commits con la identidad configurada en el paso 3, siguiendo [la guía de commits](git.md).

## 8. Resumen del scaffolding

Muestra al usuario un resumen con:
- Los proyectos creados y su ubicación.
- Las tecnologías de cada proyecto.
- La estructura de carpetas creada.
- Las ramas creadas o corregidas y la rama actual.
- Los pasos pendientes, como el push o la protección de ramas.

## 9. Instalación de tecnologías

- Instala las tecnologías de cada proyecto: intérpretes, herramientas de gestión de dependencias, dependencias del proyecto, entornos virtuales y hooks de pre-commit. Por ejemplo, `uv` y `.venv` en backend, y `pnpm` en frontend.
- Ejecuta las comprobaciones del proyecto (formateo, linter, tipos, pruebas y cobertura) y confirma que pasan.
- Si una instalación falla, indica el error exacto y no lo ocultes.

## 10. Permisos y credenciales

- Si una instalación necesita permisos elevados, como `sudo`, pide al usuario que ejecute el comando con el prefijo `!` para que la contraseña no pase por el chat. Si no es posible, pídela directamente.
- Usa las credenciales solo para ese comando concreto. Olvídalas inmediatamente después.
- Nunca las guardes ni las recuerdes: no las escribas en ficheros, variables de entorno, configuración, memoria, logs, commits, documentación ni resúmenes.
- Si necesitas permisos de nuevo, pídelos otra vez.

## 11. Cierre

- Muestra al usuario un resumen final: identidad configurada, estado de OpenSpec, ramas, scaffolding creado, tecnologías instaladas, comprobaciones ejecutadas y pendientes.
