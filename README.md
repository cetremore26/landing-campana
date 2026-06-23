[![Mi Primer Workflow de Práctica](https://github.com/cetremore26/landing-campana/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/cetremore26/landing-campana/actions/workflows/ci.yml)

# Landing Page - Campaña Política

## Descripción
Landing page ficticia para la campaña política de Alejandro Vargas Mora,
candidato a la Alcaldía de Medellín. Proyecto desarrollado como ejercicio
práctico de desarrollo web.

## Tecnologías
- HTML5
- CSS3
- JavaScript

## Estructura
landing-campana/
├── index.html
├── CSS/
│   └── style.css
├── js/
│   └── script.js
└── img/

## Gobernanza y Flujo Profesional

### 1. Diagnóstico del repositorio
- **Estructura:** proyecto frontend simple (HTML/CSS/JS) sin build ni dependencias, fácil de auditar.
- **Flujo actual (antes de esta actividad):** se trabajaba con ramas `feature/*` por funcionalidad (navbar, botón, propuestas, footer) que luego se fusionaban a `main`. Ya existe un workflow de CI (`.github/workflows/ci.yml`) que valida la existencia de los archivos clave en cada push/PR a `main`.
- **Riesgos identificados:**
  - `main` no tenía protección de rama: era posible hacer push directo o mergear sin revisión.
  - No existían plantillas de Issue ni de Pull Request, por lo que los cambios carecían de trazabilidad (motivo, evidencias, checklist).
  - No había roles definidos explícitamente para el equipo.
- **Oportunidades de mejora:** aprovechar el CI ya existente como *status check* obligatorio, formalizar GitHub Flow, e introducir plantillas y protección de rama para controlar calidad y seguridad.

### 2. Flujo de trabajo: GitHub Flow
Se adopta **GitHub Flow** para todo cambio sobre el proyecto:

1. Crear un **Issue** describiendo la tarea (usando la plantilla de `.github/ISSUE_TEMPLATE/`).
2. Crear una **rama** a partir de `main` con prefijo `feature/`, `fix/` o `docs/`:
   ```
   git switch -c feature/nombre-funcionalidad
   ```
3. Hacer **commits** atómicos y descriptivos.
4. Hacer **push** de la rama al repositorio remoto.
5. Abrir un **Pull Request** hacia `main` (usando la plantilla de PR).
6. Esperar **Review** de al menos un revisor y que pasen los **status checks** del CI.
7. Hacer **Merge** a `main` y eliminar la rama.

### 3. Roles del equipo
| Rol | Responsabilidad |
|---|---|
| **Líder Técnico** | Define la arquitectura, aprueba y mergea Pull Requests a `main`, administra la protección de ramas. |
| **Desarrollador** | Implementa funcionalidades en ramas `feature/*`, abre Pull Requests siguiendo la plantilla. |
| **Revisor** | Revisa el código y el checklist del PR, valida criterios de aceptación del Issue antes de aprobar. |

### 4. Políticas de protección de rama (`main`)
Configuradas en *Settings → Branches → Branch protection rules*:
- ✅ Require a pull request before merging (no se permite push directo a `main`).
- ✅ Require approvals (mínimo 1 revisor) antes de mergear.
- ✅ Require status checks to pass before merging (workflow `ci.yml`).
- ✅ No permitir force-push ni eliminar la rama `main`.

## Publicación oficial
- Versión estable: **v1.0.0**
- Tag: `v1.0.0`
- Release automático: se generará en GitHub al empujar el tag `v1.0.0`.
- Archivo de cambios: `CHANGELOG.md`.
- GitHub Pages: `https://cetremore26.github.io/landing-campana`

### Qué se agregó para esta entrega
- `CHANGELOG.md` con la primera versión estable.
- Workflow de GitHub Actions para crear release desde un tag semántico (`.github/workflows/release.yml`).
- Workflow de GitHub Actions para desplegar GitHub Pages desde `main` (`.github/workflows/pages.yml`).

### Verificación de publicación
1. El repositorio principal se mantiene en `main` con la versión estable.
2. El tag `v1.0.0` estará presente en GitHub.
3. El Release se generará automáticamente desde el workflow al empujar el tag.
4. La página estará publicada en la URL de GitHub Pages del repositorio.

### 5. Plantillas
- Issue: [`.github/ISSUE_TEMPLATE/tarea.md`](.github/ISSUE_TEMPLATE/tarea.md) — Título, Descripción, Prioridad, Responsable, Criterios de aceptación.
- Pull Request: [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) — Descripción, Cambios realizados, Evidencias, Checklist.

### 6. Evidencias del flujo completo
Flujo aplicado: **Issue → Branch (`feature/gobernanza-flujo`) → Commit → Push → Pull Request → Review → Merge**, documentado con capturas de pantalla entregadas al instructor (branch protection, plantillas, PR y review).

### Reflexión final
1. **¿Por qué es importante proteger la rama principal?** Porque `main` representa el código en producción/listo para publicar; protegerla evita que cambios sin revisar, rotos o inseguros lleguen directamente, y obliga a pasar por revisión y CI.
2. **¿Qué ventajas ofrece GitHub Flow?** Es simple, basado en ramas cortas y Pull Requests, favorece la integración continua, facilita la revisión de código y mantiene `main` siempre desplegable.
3. **¿Cómo ayudan los templates?** Estandarizan la información mínima necesaria (descripción, prioridad, responsable, evidencias, checklist), reducen ambigüedad y mejoran la trazabilidad de cambios e incidencias.
4. **¿Qué políticas implementarías en una empresa?** Protección de rama obligatoria, revisión por al menos un par, CI/CD con pruebas automáticas, firma de commits, control de versiones semántico y registro de incidentes/auditoría de despliegues.   
