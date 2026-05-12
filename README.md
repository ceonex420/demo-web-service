# demo-web-service — ARCHIVED 2026-05-12

> **Este repositorio fue archivado el 2026-05-12 como parte del pivot estratégico de Odiseo a TypeScript monorepo (Roadmap F).**
>
> Histórico preservado por auditoría — sin desarrollo activo desde esta fecha.

## Contexto del archivado

**Sesión de pivot**: Roadmap F · Día 1 · sesión 7 (pivot 2026-05-11)

**Razón**: El stack Python/FastAPI/Cloud Run originalmente diseñado fue evaluado como no operable por el equipo actual (jona + Claude, sin dev senior 24/7). Decisión documentada en `DECISIONS.md` (D036, D037, D040) y `APORTES-DE-WHITEPAPPER.md` §0, §1, §2.

## Categoría legacy

Orquestador HTTP Python (FastAPI)

## Reemplazo en el nuevo stack

**Destino**: apps/web API routes + Inngest jobs

## Plan de rescate

La lógica de orquestación se reimplementa nativamente en TypeScript con Anthropic Agent SDK + Vercel AI SDK. No se porta código FastAPI.

## Activo de referencia

Toda la actividad de Odiseo ahora vive en el monorepo:

**https://github.com/ceonex420/odiseo-platform**

Estructura del monorepo:

```
odiseo-platform/
├── apps/
│   ├── web/              # Next.js 15 App Router (frontend + API edge)
│   └── mcp-server/       # Cloudflare Workers (MCP server, <50ms cold start)
├── packages/
│   ├── db/               # Drizzle ORM + schema + migrations
│   ├── agent-core/       # Anthropic Agent SDK wrappers + LLM Router
│   ├── ui/               # shadcn/ui + brand tokens + React Email
│   ├── lib/              # utilidades comunes
│   └── config/           # eslint + tsconfig + tailwind base
├── infra/
│   ├── vercel/           # vercel.json + edge config
│   ├── cloudflare/       # wrangler.toml + Workers KV
│   └── neon/             # branch policy + RLS scripts
└── docs/                 # Mintlify site source
```

## Para consultar este código histórico

```bash
gh repo clone ceonex420/demo-web-service
```

El repo permanece **read-only** (archived flag). No se aceptan PRs.

## Restaurar (si fuera necesario, requiere decisión explícita)

```bash
gh repo unarchive ceonex420/demo-web-service
```

Esa acción debe registrarse en `DECISIONS.md` antes de ejecutarse.

---

**Mantenedor histórico**: Javier (CTO previo, finalizó relación 2026-Q2).
**Decisión de archivado**: jona (CEO Nexus Intelligent · ceo@nexusintelligent.ai).
**Fecha de archivado**: 2026-05-12.
**Última versión productiva**: ninguna — Cloud Run deployments fueron borrados por el CTO previo al salir, este repo nunca volvió a ejecutarse en producción tras esa fecha.
