# Proyectos Workflow — Contracts

**Versión:** v1.0.0-alpha
**Objetivo:** Fijar contratos API (OpenAPI) y modelo de datos (DBML) para el MVP:
Cotización → Aprobaciones (2C + 1F) → Nota de Venta (NV) → Orden de Trabajo (OT).
Reglas comerciales: **PriceList LOCK** al crear proyecto; **FREEZE** de precios al aprobar cotización (vía `price_agreements`).

## Cómo usar
- Importar `openapi/proyectos_workflow.v1.yaml` en Postman/Insomnia.
- Mock rápido: `npx @stoplight/prism mock openapi/proyectos_workflow.v1.yaml`
- Linter OpenAPI: `npx @redocly/cli lint openapi/proyectos_workflow.v1.yaml`

## Convenciones rápidas
- Seguridad: `Bearer <JWT>`.
- Idempotencia (obligatoria en escritura): header `Idempotency-Key` (≤64 chars).
- Errores: RFC 7807 (`ProblemDetails`).
- Paginación: `page`, `pageSize` (máx 200). Orden: `sort=-createdAt`.

## Estructura
- `openapi/`: contratos HTTP.
- `dbml/`: esquema relacional para Postgres.
- `guidelines/`: convenciones de API y catálogo de errores.

## Versionado
- Rama `v1` para cambios retro-compatibles (`v1.x`).
- Cambios breaking → `v2`.

## Uso rápido
```bash
# 1) Instalar toolchain
npm ci

# 2) Lint + build (tipos TS, colección Postman y docs)
npm run build

# 3) Mock local de la API (Prism)
npm run mock   # expone http://localhost:4010
```

[![contracts-ci](https://github.com/chantilly-cl/proyectos-contracts/actions/workflows/contracts-ci.yml/badge.svg)](https://github.com/chantilly-cl/proyectos-contracts/actions/workflows/contracts-ci.yml)

**Docs:** https://chantilly-cl.github.io/proyectos-contracts/
**Descarga rápida (Actions → Artifacts):** `contracts-dist`
