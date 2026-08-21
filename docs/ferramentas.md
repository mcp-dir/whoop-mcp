# Ferramentas

WHOOP expõe 7 ferramentas (todas somente leitura).

### 1. `whoop_list_accounts`
**Input**: `account` (opcional)

Lista as contas WHOOP vinculadas a este install (account_id, nome, email).

### 2. `whoop_profile`
**Input**: `account` (opcional)

Perfil básico do membro WHOOP (user_id, nome, email).

### 3. `whoop_body_measurement`
**Input**: `account` (opcional)

Medidas corporais do membro WHOOP: altura (m), peso (kg) e frequência cardíaca máxima.

### 4. `whoop_cycles`
**Input**: `limit` (opcional), `start` (opcional), `end` (opcional), `next_token` (opcional), `cycle_ids` (opcional), `account` (opcional)

Ciclos fisiológicos do WHOOP (dia a dia): strain (0-21), calorias (kilojoule), FC média e máxima.

### 5. `whoop_recovery`
**Input**: `limit` (opcional), `start` (opcional), `end` (opcional), `next_token` (opcional), `cycle_ids` (opcional), `account` (opcional)

Recovery do WHOOP: recovery_score (0-100%), HRV (rmssd), FC de repouso, SpO2, temperatura da pele.

### 6. `whoop_sleep`
**Input**: `limit` (opcional), `start` (opcional), `end` (opcional), `next_token` (opcional), `sleep_ids` (opcional), `account` (opcional)

Sono do WHOOP: duração, eficiência, performance (%), estágios (leve, REM, profundo), frequência respiratória.

### 7. `whoop_workouts`
**Input**: `limit` (opcional), `start` (opcional), `end` (opcional), `next_token` (opcional), `workout_ids` (opcional), `account` (opcional)

Workouts do WHOOP: esporte, strain, FC média e máxima, zonas de FC, distância e altimetria quando disponíveis.

## Prompts de exemplo

```
Como foi meu sono essa semana no WHOOP?
Qual meu recovery e HRV de hoje?
Compare o strain dos meus últimos 7 dias
```
