# WHOOP

### WHOOP para Claude, ChatGPT e agentes de IA

Seus dados WHOOP no assistente, somente leitura: recovery, sono, strain, workouts, ciclos e medidas corporais via API oficial v2 (OAuth 2.0). A plataforma fornece a aplicação OAuth, você só clica em Autorizar e loga com sua conta WHOOP, sem informar senha ao assistente. Dados de wearable não substituem avaliação médica.

- 📊 **7 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `WHOOP` e **URL** `https://api.mcp.ai/p_whoop`.

### Cursor

[➕ Instalar WHOOP no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=whoop&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF93aG9vcCJ9)

### VS Code (Copilot Chat)

[➕ Instalar WHOOP no VS Code](vscode:mcp/install?name=whoop&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_whoop%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_whoop
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Como foi meu sono essa semana no WHOOP?
Qual meu recovery e HRV de hoje?
Compare o strain dos meus últimos 7 dias
```

---

## 7 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `whoop_list_accounts` | Lista as contas WHOOP vinculadas a este install (account_id, nome, email). |
| `whoop_profile` | Perfil básico do membro WHOOP (user_id, nome, email). |
| `whoop_body_measurement` | Medidas corporais do membro WHOOP: altura (m), peso (kg) e frequência cardíaca máxima. |
| `whoop_cycles` | Ciclos fisiológicos do WHOOP (dia a dia): strain (0-21), calorias (kilojoule), FC média e máxima. |
| `whoop_recovery` | Recovery do WHOOP: recovery_score (0-100%), HRV (rmssd), FC de repouso, SpO2, temperatura da pele. |
| `whoop_sleep` | Sono do WHOOP: duração, eficiência, performance (%), estágios (leve, REM, profundo), frequência respiratória. |
| `whoop_workouts` | Workouts do WHOOP: esporte, strain, FC média e máxima, zonas de FC, distância e altimetria quando disponíveis. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: WHOOP, Inc., o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_whoop`.


---

## Suporte

- 📧 [whoop@mcp.ai](mailto:whoop@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/whoop-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_whoop` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
