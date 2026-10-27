# interview-prep — CLAUDE.md (contexto del agente)

> 🤖 Contexto canónico de **este agente** para la IA. `AGENTS.md`/`GEMINI.md` son symlinks a este archivo.
> 📅 Última actualización: {YYYY-MM-DD}
> 📚 Estándares base del repo: [`../../CLAUDE.md`](../../CLAUDE.md) — **no se re-copian acá.**
> 🧭 Proceso (cómo/cuándo trabajar): skills de **superdeltas**, no archivos in-repo.
>
> **Este archivo es un skeleton.** Al scaffoldear un cliente real, superdeltas reemplaza `interview-prep` y completa los placeholders `<...>`.

---

## Qué hace este agente

{1-3 frases: qué resuelve, quién lo usa, valor de negocio. Placeholder.}

## Flujo de conversación (macro)

```
{Diagrama ASCII del flujo principal: actores → eventos → decisiones → efectos. Placeholder.}
```

## Tools que usa este agente (grafo de handoff)

> Esta tabla es lo que permite retomar el agente. Por cada tool, linkeá a su doc.

| Tool | Tipo | Dónde está documentada |
|------|------|------------------------|
| `<tool>` | MCP custom de este repo | [`mcp/README.md`](mcp/README.md) → doc de la tool |
| `<tool>` | MCP reutilizable (ej. Odoo) | Repo compartido `<odoo-mcp-server>` — este cliente usa: `<tool_a>`, `<tool_b>`. Docs: `<link>` |
| `<tool>` | HTTP tool / nativa del dashboard | `<link al handbook o al dashboard>` |

Cadena de handoff: **este archivo explica el flujo → linkea a las tools → si la tool es de un `mcp/` custom, linkea a su doc → si es de un MCP reutilizable, dice qué tools de ese MCP usa este cliente y dónde están documentadas.**

## Documentos canónicos de este agente

| Orden | Ruta | Para qué | Quién lo genera |
|-------|------|----------|-----------------|
| 1 | `CLAUDE.md` (este archivo) | Flujo, tools, punteros | Delta + superdeltas |
| 2 | `docs/relevamiento.md` | Qué hace el agente y por qué (negocio) | superdeltas (SP1) |
| 3 | `docs/specs/*.md` | Qué se construye (uno por tool/feature) | superdeltas (SP1) |
| 4 | `docs/adr/NNNN-*.md` | Por qué se decidió X (uno por archivo) | superdeltas (gate ADR) |
| 5 | `docs/backlog/sprint-N.md` | HUs + tareas `T-XXX-NNN` | superdeltas (SP1) |
| 6 | `docs/plans/sprint-N-plan.md` | Cómo se implementa cada tarea | superdeltas (GATE 5) |
| 7 | `docs/TRACEABILITY.md` | Tarea → HU → SPEC § → relevamiento | superdeltas |

## Prompts

Versionados en `prompts/<version>/`. La estructura estándar de prompt vive en el handbook (`ai-engineering/estructura-prompt.md`) — ver `prompts/<version>/system-prompt.md`. Si es multi-agente, los subagentes van en `prompts/<version>/subagentes/`.

## Estándares

Se heredan de [`../../CLAUDE.md`](../../CLAUDE.md). No se duplican acá. Reglas específicas de **este** agente van abajo.

### Reglas específicas del agente

{Reglas únicas de este agente — formato de IDs, políticas de validación, fuente de verdad de datos. Placeholder / borrar si no aplica.}

## Bugs recurrentes / lecciones aprendidas

<!-- Plantilla de entrada:
### {YYYY-MM-DD} — {título}
**Dónde:** {...}  **Síntoma:** {...}  **Causa raíz:** {...}  **Fix:** {...}  **❌ No hacer:** {...}  **✅ Hacer:** {...}
-->
