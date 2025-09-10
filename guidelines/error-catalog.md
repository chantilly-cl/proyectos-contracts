# Catálogo de Errores (MVP)

| Código | title                         | detail (ejemplo)                                          | Nota                                   |
|-------:|-------------------------------|-----------------------------------------------------------|----------------------------------------|
| 400    | Invalid Request               | Campo `items[0].quantity` debe ser > 0                    | Validación sintáctica                  |
| 401    | Unauthorized                  | Token inválido o expirado                                 | JWT                                    |
| 403    | Forbidden                     | Rol sin permiso para aprobar `financial_1`                | RBAC                                   |
| 404    | Not Found                     | Quote `6b2…` no existe                                    |                                        |
| 409    | Business Rule Violation       | `price_list_id` es inmutable para el proyecto             | LOCK                                   |
| 409    | Workflow Guard Failed         | No se puede emitir NV sin approvals completos             | Guard de workflow                      |
| 422    | Unprocessable Entity          | Items inconsistentes con PriceAgreement vigente           | Semántico                              |
| 500    | Internal Server Error         | Error inesperado                                          |                                        |
| 503    | Service Unavailable           | Dependencia de pricing no disponible                      | retry-after (si aplica)                |
|-------:|-------------------------------|-----------------------------------------------------------|----------------------------------------|
