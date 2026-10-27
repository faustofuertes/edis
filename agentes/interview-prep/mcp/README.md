# `mcp/` — Worker Cloudflare custom (Capa 2)

Este es el **hueco** para el compute custom del agente. Acá NO hay worker todavía: cuando este agente realmente necesite un MCP custom, se construye con el **skill correspondiente** (ver abajo). Este README documenta la convención para que la IA sepa cómo se maneja, aunque el worker no esté creado.

## Cuándo aparece un `mcp/` acá

Solo si la tool necesita compute propio **y es custom de este cliente** (Capa 2). Si la tool fuera **reutilizable/multi-cliente**, NO va acá: va a un repo MCP compartido (forma `odoo-mcp-server`). superdeltas decide preguntando.

## Cómo se construye (proceso → skill, no este repo)

El worker MCP lo arma el **skill de creación de MCP/Worker de Laburen**. Si el skill no está instalado, la IA debe **ir a buscarlo/instalarlo** antes de crear el `mcp/`. El how-to de "cómo creo un MCP" también vive en el handbook.

<!-- Cuando el skill esté auditado (follow-up §10 del spec), poné acá su nombre/ruta exacta. -->

## Flujo de deploy (conceptual — del §4 del spec)

```
código del mcp/  →  wrangler deploy (idealmente por GitHub Action)
                 →  hosteado en una cuenta de Cloudflare
                 →  expone una URL de MCP server
                 →  esa URL se conecta en el dashboard de Laburen (su MCP client consume las tools)
```

Cloudflare es solo hosting.

> ⚠️ **El cableado uniforme del CI/deploy (qué cuenta de Cloudflare, el `.yml` estándar) es un follow-up: Eje 5 del spec.** Todavía NO está estandarizado. Por eso este template no trae un `.yml` de deploy — lo arma el skill cuando se instancia el `mcp/`.

## Estructura esperada (la crea el skill, no está acá)

Cuando se instancie, el `mcp/` tendrá: `src/` (una tool por archivo, función pura + Zod), `wrangler.jsonc`, tests, y `docs/tools/*.md` (una doc por tool = nodos del grafo de handoff que linkea el `CLAUDE.md` del agente). Estándares de código: `../../../CLAUDE.md`.
