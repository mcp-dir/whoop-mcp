# WHOOP

### WHOOP for Claude, ChatGPT and AI agents

Your WHOOP data in the assistant, read-only: recovery, sleep, strain, workouts, cycles and body measurements via the official v2 API (OAuth 2.0). The platform provides the OAuth app, just click Authorize and log into your WHOOP account, no password shared with the assistant. Wearable data is not a substitute for medical advice.

- 📊 **7 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `WHOOP`, URL `https://api.mcp.ai/p_whoop`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=whoop&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF93aG9vcCJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=whoop&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_whoop%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_whoop
```

---

## 7 tools

| Tool | Description |
|---|---|
| `whoop_list_accounts` | Lista as contas WHOOP vinculadas a este install (account_id, nome, email). |
| `whoop_profile` | Perfil básico do membro WHOOP (user_id, nome, email). |
| `whoop_body_measurement` | Medidas corporais do membro WHOOP: altura (m), peso (kg) e frequência cardíaca máxima. |
| `whoop_cycles` | Ciclos fisiológicos do WHOOP (dia a dia): strain (0-21), calorias (kilojoule), FC média e máxima. |
| `whoop_recovery` | Recovery do WHOOP: recovery_score (0-100%), HRV (rmssd), FC de repouso, SpO2, temperatura da pele. |
| `whoop_sleep` | Sono do WHOOP: duração, eficiência, performance (%), estágios (leve, REM, profundo), frequência respiratória. |
| `whoop_workouts` | Workouts do WHOOP: esporte, strain, FC média e máxima, zonas de FC, distância e altimetria quando disponíveis. |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_whoop` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
