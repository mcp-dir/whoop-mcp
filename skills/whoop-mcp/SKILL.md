---
name: whoop-mcp
description: Skill da REST API do WHOOP na MCP.AI: 7 endpoints em /api/whoop. Seus dados WHOOP no assistente, somente leitura: recovery, sono, strain, workouts, ciclos e medidas corporais via API oficial v2 (OAuth 2.0). A plataforma fornece a aplicação OAuth, você só clica em Autorizar e loga com sua conta WHOOP, sem informar senha ao assistente. Dados de wearable não substituem avaliação médica. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# WHOOP — REST API skill

Você tem acesso à **WHOOP** REST API na MCP.AI.

> Seus dados WHOOP no assistente, somente leitura: recovery, sono, strain, workouts, ciclos e medidas corporais via API oficial v2 (OAuth 2.0). A plataforma fornece a aplicação OAuth, você só clica em Autorizar e loga com sua conta WHOOP, sem informar senha ao assistente. Dados de wearable não substituem avaliação médica.

## Base URL

```
https://api.mcp.ai/api/whoop
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/whoop/body/measurement \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/whoop/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (7)

#### `whoop_body_measurement`

Medidas corporais do membro WHOOP: altura (m), peso (kg) e frequência cardíaca máxima. _(POST /api/whoop/body/measurement)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando o install tem mais de uma conta WHOOP: account_id, nome, email ou parcial. Ver whoop_list_accounts. |

#### `whoop_cycles`

Ciclos fisiológicos do WHOOP (dia a dia): strain (0-21), calorias (kilojoule), FC média e máxima. _(POST /api/whoop/cycles)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `limit` | integer | Não | Registros por página (default do WHOOP: 10, máx 25). |
| `start` | string | Não | Início do intervalo, ISO 8601 (ex.: 2026-07-01T00:00:00.000Z). |
| `end` | string | Não | Fim do intervalo, ISO 8601. |
| `next_token` | string | Não | Token da próxima página (campo next_token da resposta anterior). |
| `cycle_ids` | string[] | Não | Busca ciclos específicos por id (ignora paginação). |
| `account` | string | Não | Quando o install tem mais de uma conta WHOOP: account_id, nome, email ou parcial. Ver whoop_list_accounts. |

#### `whoop_list_accounts`

Lista as contas WHOOP vinculadas a este install (account_id, nome, email). _(POST /api/whoop/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando o install tem mais de uma conta WHOOP: account_id, nome, email ou parcial. Ver whoop_list_accounts. |

#### `whoop_profile`

Perfil básico do membro WHOOP (user_id, nome, email). _(POST /api/whoop/profile)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando o install tem mais de uma conta WHOOP: account_id, nome, email ou parcial. Ver whoop_list_accounts. |

#### `whoop_recovery`

Recovery do WHOOP: recovery_score (0-100%), HRV (rmssd), FC de repouso, SpO2, temperatura da pele. _(POST /api/whoop/recovery)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `limit` | integer | Não | Registros por página (default do WHOOP: 10, máx 25). |
| `start` | string | Não | Início do intervalo, ISO 8601 (ex.: 2026-07-01T00:00:00.000Z). |
| `end` | string | Não | Fim do intervalo, ISO 8601. |
| `next_token` | string | Não | Token da próxima página (campo next_token da resposta anterior). |
| `cycle_ids` | string[] | Não | Busca o recovery de ciclos específicos (ignora paginação). |
| `account` | string | Não | Quando o install tem mais de uma conta WHOOP: account_id, nome, email ou parcial. Ver whoop_list_accounts. |

#### `whoop_sleep`

Sono do WHOOP: duração, eficiência, performance (%), estágios (leve, REM, profundo), frequência respiratória. _(POST /api/whoop/sleep)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `limit` | integer | Não | Registros por página (default do WHOOP: 10, máx 25). |
| `start` | string | Não | Início do intervalo, ISO 8601 (ex.: 2026-07-01T00:00:00.000Z). |
| `end` | string | Não | Fim do intervalo, ISO 8601. |
| `next_token` | string | Não | Token da próxima página (campo next_token da resposta anterior). |
| `sleep_ids` | string[] | Não | Busca registros de sono específicos por UUID (ignora paginação). |
| `account` | string | Não | Quando o install tem mais de uma conta WHOOP: account_id, nome, email ou parcial. Ver whoop_list_accounts. |

#### `whoop_workouts`

Workouts do WHOOP: esporte, strain, FC média e máxima, zonas de FC, distância e altimetria quando disponíveis. _(POST /api/whoop/workouts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `limit` | integer | Não | Registros por página (default do WHOOP: 10, máx 25). |
| `start` | string | Não | Início do intervalo, ISO 8601 (ex.: 2026-07-01T00:00:00.000Z). |
| `end` | string | Não | Fim do intervalo, ISO 8601. |
| `next_token` | string | Não | Token da próxima página (campo next_token da resposta anterior). |
| `workout_ids` | string[] | Não | Busca workouts específicos por UUID (ignora paginação). |
| `account` | string | Não | Quando o install tem mais de uma conta WHOOP: account_id, nome, email ou parcial. Ver whoop_list_accounts. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_whoop` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
