# API Conventions

## Autenticación
- `Authorization: Bearer <JWT>`.

## Idempotencia
- **Requerida** en POST/PATCH: `Idempotency-Key` (≤64 chars).
- Persistir `key + hash(request)` para devolver la misma respuesta por 24h.

## Errores (RFC 7807)
- 400 Validación, 401 Auth, 403 RBAC, 404 No existe,
- 409 Regla de negocio (p.ej., intentar cambiar `price_list_id` del proyecto),
- 422 Error semántico, 500/503 Infra.
- Respuesta: `ProblemDetails` con `type`, `title`, `status`, `detail`, `instance`, `errors` (opcional).

## Paginación / Orden
- `page` (≥1), `pageSize` (1..200), `sort` (p.ej., `-createdAt`).

## Moneda y montos
- Siempre enteros (`*_cents`) y `currency` ISO-4217 (ej.: CLP).

## Auditoría
- Toda transición de workflow y decisión de approval escribe en `audit_logs`.

## Regla comercial clave
- **LOCK**: `projects.price_list_id` es inmutable tras crear el proyecto.
- **FREEZE**: al aprobar la cotización final, se escribe `price_agreements` para fijar precios.
