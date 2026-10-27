# `docs/` — sistema de documentación del agente

Estas carpetas son la **estructura** de la documentación de un agente Delta. El **contenido** lo genera superdeltas (pipeline SP1 + gates), usando sus propias plantillas (`superdeltas/templates/`). Acá no hay plantillas de llenado — el template repo define **dónde va cada cosa**, no **cómo se escribe** (eso es proceso → superdeltas).

| Ruta | Qué contiene | Convención de nombre | Lo genera |
|------|--------------|----------------------|-----------|
| `relevamiento.md` | Entendimiento del negocio del agente | archivo único | superdeltas — `understanding-the-relevamiento` |
| `requerimientos/` | Requerimientos crudos del cliente (+ `extra-cliente/`) | `YYYY-MM-DD-...` | superdeltas — `initializing-the-project` |
| `specs/` | Specs, **una por tool/feature** | `<slug-feature>-spec.md` | superdeltas — `writing-the-spec` |
| `adr/` | Decisiones de arquitectura, **una por archivo** | `NNNN-slug.md` | superdeltas — gate de ADRs |
| `backlog/` | HUs + tareas `T-XXX-NNN` por sprint | `sprint-N.md` | superdeltas — `creating-technical-tasks` |
| `plans/` | Plan de implementación por sprint | `sprint-N-plan.md` | superdeltas — `writing-the-implementation-plan` |
| `evals/` | Evidencia de validación (eval runs) | `eval-run-N.md` | superdeltas / eval-app |
| `TRACEABILITY.md` | Matriz tarea → HU → SPEC § → relevamiento | archivo único | superdeltas |
| `tech-notes/` | Notas técnicas del handbook (punteros, no copias) | `handbook-context.md` | Delta / superdeltas |

