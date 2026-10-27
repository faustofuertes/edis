# CLAUDE.md — Estándares base Laburen (template de proyecto Delta)

> Este archivo es el **contexto canónico** del repo. Claude Code, Cursor/Codex (`AGENTS.md`) y Gemini (`GEMINI.md`) leen este mismo contenido vía symlink. La IA lo auto-lee: los estándares de acá se cumplen sin que nadie los recuerde.
>
> **Qué es este repo:** el template estándar de un proyecto Delta — el **sistema de carpetas** canónico + los estándares base. Se consume vía superdeltas para arrancar un proyecto. Ver `README.md` para el uso.
>
> **Proceso (cómo/cuándo trabajar):** NO vive en este repo. Vive en las skills de **superdeltas**. Este repo define **estructura** y **estándares**, nada más.

---

## Innegociables (zero tolerance)

Aplican en todo el código: producción, tests, scripts, config. Sin excepciones.

- **Nada hardcodeado.** Credenciales por env/headers, nunca en el código. Comportamiento por-cliente vía **config**, nunca por ramas hardcodeadas por cliente. Multi-tenant safe: ningún dato de un cliente cruza a otro.
- **Escalable y prolijo.** Archivos chicos y con una responsabilidad. Nada de "lo dejo así por ahora".
- **TypeScript siempre, nunca JavaScript.** Todo código de este repo se escribe en TypeScript, y estricto: `strict: true` + `noUncheckedIndexedAccess: true` + `noImplicitReturns: true`. Un `.js` en `src/` es un error, no una excepción.
- **Prohibido `any`, `@ts-ignore`, `eslint-disable`.** Usá `unknown` + Zod / type guards, tipos específicos, o generics.
- **Validación en los bordes con Zod.** Todo input que cruza una frontera de confianza (body HTTP, respuesta de API externa, contenido de archivo, env en runtime) se valida con Zod antes de usarse.
- **Todo código custom de Cloudflare reporta a la ingesta de telemetría** con `@laburen/delta-sdk`. Vale para el worker de un cliente y para un MCP compartido, y no es opcional. El detalle está en el handbook, sección **Cloudflare**.
- **Nunca `--no-verify`.** Si un hook o `pnpm check` falla, se arregla el error de fondo.

## Convenciones de código

### tsconfig (mínimo)

```jsonc
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "ESNext",
    "moduleResolution": "bundler",
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true
  }
}
```

### Reglas

- **No `any`** → `unknown` o tipos específicos.
- **Siempre `async/await`** → nada de cadenas `.then()`.
- **Paralelizar** operaciones independientes con `Promise.all` / `Promise.allSettled`.
- **Early returns** → evitar anidamiento profundo.
- **Errores tipados** → clases con `code` y `statusCode`.
- **Orden de imports:** 1) built-ins de Node, 2) deps externas, 3) internos `@/`, 4) relativos, 5) types.

### Naming

| Tipo | Convención | Ejemplo |
|------|------------|---------|
| Archivos | kebab-case | `format-tarifa.ts` |
| Clases / Interfaces / Types | PascalCase | `PedidoCreateInput` |
| Funciones / variables | camelCase | `getUserById` |
| Constantes | UPPER_SNAKE | `MAX_RETRIES` |
| Schemas Zod | PascalCase + `Schema` | `PedidoCreateSchema` |

### Estructura de funciones

- Parámetros requeridos primero, opcionales después (o un objeto de opciones).
- Early returns antes que anidar.

### Manejo de errores

```typescript
class AppError extends Error {
  constructor(
    message: string,
    public readonly code: string,
    public readonly statusCode: number = 500,
  ) {
    super(message);
    this.name = 'AppError';
  }
}
```

Try-catch específico: capturá lo que sabés manejar, re-throw el resto.

### Comentarios — cuándo comentar

- APIs públicas.
- Lógica compleja no obvia.
- Workarounds temporales (con `TODO` + referencia al ticket).
- Decisiones de arquitectura.

### Comentarios — cuándo NO comentar

```typescript
// Mal — el código es obvio
// Incrementa el contador
counter++;

// Bien — explica el POR QUÉ, no el qué
// Workaround para bug en API de WhatsApp que duplica mensajes
// TODO: remover cuando Meta lo arregle (ticket #123)
const mensajesUnicos = [...new Set(mensajes)];
```

### Prettier

```json
{ "semi": true, "singleQuote": true, "tabWidth": 2, "trailingComma": "es5", "printWidth": 100 }
```

### Linting

ESLint + Prettier; formatear al guardar. Chequeo pre-commit (cada uno debe dar CERO resultados):

```bash
grep -rn ": any" src/ tests/
grep -rn "@ts-ignore" src/ tests/
grep -rn "eslint-disable" .
```

---

## El prompt: el repo es la fuente de verdad

El prompt versionado vive en `agentes/<agente>/prompts/<version>/`. El dashboard de Laburen es **deploy**, no fuente de verdad.

- Un cambio de prompt se hace **en el archivo**, se commitea, y **recién después** se pega en la app.
- **Nunca al revés.** Editar en el dashboard y no tocar el repo deja el repo mintiendo, y con él se van la historia, el review y los evals asociados a esa versión.

Esto no lo fuerza ninguna herramienta: es disciplina. Si encontrás que el dashboard y el repo difieren, la corrección es traer el cambio al repo — no actualizar la foto.

---

## Delta a cargo

<!-- Lo completa superdeltas en Stage 0 (o adopting). Se auto-lee cada sesión para calibrar
     cuánto explica la IA (nuevo → proactivo; con know-how → on-demand). -->

- **Nombre:** Fausto Fuertes
- **Nivel de conocimiento de Laburen:** con know-how

---

## Mapa de agentes

Un renglón por agente. Al scaffoldear un cliente real se reemplaza este ejemplo.

- `interview-prep` — genera ejercicios de práctica de Python estilo LeetCode, en inglés, para preparar a los alumnos de Eddis para assessments técnicos (CoderPad y similares) de empresas del exterior → [`agentes/interview-prep/CLAUDE.md`](agentes/interview-prep/CLAUDE.md)

---

## Repos del cliente

<!-- Sólo para clientes legacy. Cada fila es deuda declarada, no una opción de diseño:
     en un cliente nuevo esta sección no existe. -->

| Repo | Rama de verdad | Qué contiene | Por qué está afuera |
|------|----------------|--------------|---------------------|
| `Laburen/eddis-api-worker` | <a confirmar> | fuera de alcance del agente interview-prep por ahora | ya existía antes de la casa; worker deployado desde su propio repo |

---

## Dónde vive cada cosa (routing)

- **Hecho** sobre cómo es Laburen / dónde está algo → **handbook**.
- **Proceso** (cómo/cuándo) → **superdeltas** (skills).
- **Estructura de archivos** → **este template repo**.
- **Estándar a hacer cumplir** (convenciones, innegociables) → **este archivo** (`CLAUDE.md`), porque la IA lo auto-lee.
