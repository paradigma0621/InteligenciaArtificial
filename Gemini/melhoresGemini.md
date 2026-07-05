# Gemini CLI — Guia de referência

Um guia prático e autocontido do **Gemini CLI**, o agente de linha de comando do Google. Cobre os comandos do dia a dia, os modos de aprovação, a memória hierárquica via `GEMINI.md`, permissões, checkpointing, comandos personalizados, hooks, MCP e sub-agentes.

- [1. Visão geral](#1-visão-geral)
- [2. /stats](#2-stats)
- [3. Boas práticas](#3-boas-práticas)
- [4. Modos de aprovação](#4-modos-de-aprovação)
  - [4.1. Modo auto-edit (auto\_edit)](#41-modo-auto-edit-auto_edit)
  - [4.2. Modo YOLO](#42-modo-yolo)
  - [4.3. Interromper e sair](#43-interromper-e-sair)
- [5. Memória hierárquica (GEMINI.md)](#5-memória-hierárquica-geminimd)
  - [5.1. As camadas](#51-as-camadas)
  - [5.2. Comandos /memory](#52-comandos-memory)
  - [5.3. Regras por subdiretório (path-scoping)](#53-regras-por-subdiretório-path-scoping)
  - [5.4. Imports modulares com @](#54-imports-modulares-com-)
- [6. Permissões e ferramentas](#6-permissões-e-ferramentas)
  - [6.1. Definindo regras de permissão](#61-definindo-regras-de-permissão)
  - [6.2. Nomes das ferramentas embutidas](#62-nomes-das-ferramentas-embutidas)
- [7. Inspecionar a configuração efetiva](#7-inspecionar-a-configuração-efetiva)
- [8. /clear (limpar a tela) vs. /compress (condensar contexto)](#8-clear-limpar-a-tela-vs-compress-condensar-contexto)
- [9. Sessões: /chat save e /chat resume](#9-sessões-chat-save-e-chat-resume)
- [10. Onde ficam os artefatos de sessão](#10-onde-ficam-os-artefatos-de-sessão)
- [11. Checkpointing: /restore](#11-checkpointing-restore)
  - [11.1. Como funciona](#111-como-funciona)
  - [11.2. O que os checkpoints NÃO rastreiam](#112-o-que-os-checkpoints-não-rastreiam)
  - [11.3. Sessões e branches do Git](#113-sessões-e-branches-do-git)
- [12. Comandos personalizados (custom commands)](#12-comandos-personalizados-custom-commands)
  - [12.1. Anatomia de um comando TOML](#121-anatomia-de-um-comando-toml)
  - [12.2. Locais, namespaces e argumentos](#122-locais-namespaces-e-argumentos)
- [13. Extensions e agent skills](#13-extensions-e-agent-skills)
- [14. Hooks](#14-hooks)
  - [14.1. Onde os hooks são armazenados](#141-onde-os-hooks-são-armazenados)
  - [14.2. Como os hooks funcionam](#142-como-os-hooks-funcionam)
  - [14.3. Eventos de ciclo de vida](#143-eventos-de-ciclo-de-vida)
  - [14.4. Estrutura de configuração](#144-estrutura-de-configuração)
- [15. MCP (Model Context Protocol)](#15-mcp-model-context-protocol)
  - [15.1. /mcp](#151-mcp)
  - [15.2. Como configurar servidores MCP](#152-como-configurar-servidores-mcp)
  - [15.3. Playwright / Chrome DevTools MCP](#153-playwright--chrome-devtools-mcp)
  - [15.4. Context7 MCP: documentação sempre atualizada](#154-context7-mcp-documentação-sempre-atualizada)
  - [15.5. Cenários comuns com MCP](#155-cenários-comuns-com-mcp)
  - [15.6. Referências](#156-referências)
- [16. Sub-agentes](#16-sub-agentes)
  - [16.1. Criando um sub-agente](#161-criando-um-sub-agente)
  - [16.2. Delegação automática e explícita](#162-delegação-automática-e-explícita)
  - [16.3. Execução paralela](#163-execução-paralela)
  - [16.4. Memória persistente em sub-agentes](#164-memória-persistente-em-sub-agentes)

# 1. Visão geral

O **Gemini CLI** é um agente de codificação que roda no terminal. Você conversa com ele em linguagem natural e ele lê arquivos, edita código, roda comandos de shell, consulta a web e integra ferramentas externas via MCP — sempre sob um sistema de aprovação que você controla.

Os pilares de configuração e uso que este guia cobre:

- **`GEMINI.md`** — arquivos de memória/instruções carregados hierarquicamente (global, projeto, subdiretórios).
- **`settings.json`** — configuração em camadas (usuário e workspace) para permissões, hooks, servidores MCP e comportamento geral.
- **Comandos de barra** (`/comando`) — comandos embutidos e personalizados.
- **Extensions** — pacotes instaláveis que agrupam MCP servers, comandos, hooks e sub-agentes.

Convenções de caminho usadas ao longo do texto:

- `~/.gemini/` — configuração **global** (vale para todos os projetos).
- `<projeto>/.gemini/` — configuração de **workspace** (vale só para aquele projeto; versionável no Git).

# 2. /stats

Mostra estatísticas da sessão atual sob demanda: contagem de tokens (entrada, saída, cache), número de requisições, duração da sessão e, em alguns casos, uma estimativa de uso. É um comando puramente informativo — não altera nada, só exibe o consumo acumulado até aquele momento.

# 3. Boas práticas

**Salve e nomeie suas sessões.** Assim que começar um trabalho significativo, rode `/chat save payment-gateway-fix`. Depois retome exatamente onde parou com `/chat resume payment-gateway-fix`, e veja tudo que salvou com `/chat list`. Criar o hábito de salvar uma tag por tarefa (ou uma tag fixa como `last` antes de sair) é a forma confiável de "continuar de ontem" — ver seção [Sessões](#9-sessões-chat-save-e-chat-resume).

**Mantenha o `GEMINI.md` enxuto.** Ele é sempre carregado por inteiro; quanto mais curto e objetivo, melhor a precisão do agente. Modularize com imports `@` e regras por subdiretório em vez de inchar o arquivo raiz.

**Habilite o checkpointing.** Assim você pode reverter arquivos + conversa a um ponto seguro depois de uma edição arriscada — ver [/restore](#11-checkpointing-restore).

# 4. Modos de aprovação

Antes de executar ações que modificam o sistema (editar arquivos, rodar shell), o Gemini pede aprovação. O **modo de aprovação** define quanto ele pergunta. Pressione **`Shift+Tab`** para ciclar entre os modos dentro da sessão.

## 4.1. Modo auto-edit (auto_edit)

Aprova automaticamente **modificações de arquivos** (edições) sem perguntar, mas ainda pede confirmação para comandos de shell.

- Ativar na sessão: `Shift+Tab` até chegar no modo.
- Por config: `"general": { "defaultApprovalMode": "auto_edit" }`.

## 4.2. Modo YOLO

Auto-aprova **todas** as ações, incluindo comandos de shell (commit, instalar pacotes, etc.) — bypassa completamente o sistema de permissões.

- Toggle na sessão: **`Ctrl+Y`**.
- Na inicialização: `gemini --yolo` (ou `-y`).
- Por config: `general.defaultApprovalMode: "yolo"` (exige `security.disableYoloMode: false`).

⚠️ É o modo mais perigoso. Só deve ser usado em um *trusted workspace* isolado (ex.: ambientes de CI ou contêineres descartáveis), nunca com credenciais sensíveis à mão.

## 4.3. Interromper e sair

- **`ESC`** (uma vez) — cancela a operação atual em andamento.
- **`Ctrl+C`** (duas vezes) ou **`/quit`** — encerra o CLI.

# 5. Memória hierárquica (GEMINI.md)

O Gemini carrega instruções persistentes a partir de arquivos `GEMINI.md`. Eles são **concatenados** conforme a árvore de diretórios, do global ao mais específico, formando um único contexto de instruções para a sessão.

## 5.1. As camadas

| Local                                 | Propósito                                                                                     |
|---------------------------------------|-----------------------------------------------------------------------------------------------|
| Global (`~/.gemini/GEMINI.md`)        | Aplica-se a todas as suas sessões, em qualquer projeto.                                        |
| Raiz do projeto (`./GEMINI.md`)       | Aplica-se ao projeto. Versionável no Git e compartilhável com a equipe.                        |
| Diretórios pais / filhos              | O Gemini concatena os `GEMINI.md` da árvore — pais (útil em monorepos) e subdiretórios são carregados conforme o diretório de trabalho. |

## 5.2. Comandos /memory

`/memory` é o painel da memória hierárquica. Subcomandos:

- **`/memory show`** — mostra o conteúdo concatenado de todos os `GEMINI.md` carregados (global, projeto, subdiretórios).
- **`/memory list`** — lista os caminhos dos `GEMINI.md` ativos.
- **`/memory refresh`** — recarrega os `GEMINI.md` após você editá-los, sem reiniciar o CLI.
- **`/memory add <texto>`** — adiciona um trecho de instrução à memória.

Detalhes de comportamento:

- O `GEMINI.md` é sempre carregado por inteiro. Não há um mecanismo de "carregar sob demanda só as partes relevantes"; por isso, mantê-lo curto melhora a precisão.
- Para modularizar, use **imports `@arquivo.md`** (carregados junto — ver [5.4](#54-imports-modulares-com-)) e **regras por subdiretório** (carregadas conforme o diretório de trabalho — ver [5.3](#53-regras-por-subdiretório-path-scoping)).

## 5.3. Regras por subdiretório (path-scoping)

Como o Gemini concatena os `GEMINI.md` da árvore conforme o diretório de trabalho, você obtém "regras certas no contexto certo" colocando instruções específicas em `GEMINI.md` dentro das pastas relevantes:

```
projeto/
├── GEMINI.md                 ← Regras universais (sempre carregadas)
├── src/api/
│   └── GEMINI.md             ← Regras de API (carregadas ao trabalhar em src/api)
├── src/components/
│   └── GEMINI.md             ← Regras de React (carregadas ao trabalhar em components)
└── db/migrations/
    └── GEMINI.md             ← Regras de migração (carregadas ao trabalhar em migrations)
```

Isso evita "saturação de prioridade": as regras de migração só entram no contexto quando o agente está mexendo em `db/migrations/`. O escopo é por **subdiretório** (onde o `GEMINI.md` mora).

## 5.4. Imports modulares com @

Mantenha o `GEMINI.md` raiz enxuto e importe arquivos temáticos com `@`:

```markdown
# Regras do projeto
@./rules/code-style.md
@./rules/testing.md
@./rules/security.md
```

⚠️ Imports `@` são **sempre** carregados (não são condicionais por path). Para carregamento condicional conforme onde você está trabalhando, use a abordagem por subdiretórios ([5.3](#53-regras-por-subdiretório-path-scoping)).

# 6. Permissões e ferramentas

O controle de quais ferramentas o agente pode usar (e quais rodam sem pedir confirmação) é feito pelo bloco `tools` no `settings.json` — editável também pela UI do `/settings`.

## 6.1. Definindo regras de permissão

Chaves relevantes dentro de `tools`:

- **`tools.core`** (ou `coreTools`) — **lista branca**: restringe quais ferramentas embutidas ficam disponíveis.
- **`tools.exclude`** (ou `excludeTools`) — **lista negra**: remove ferramentas ou comandos específicos.
- **`tools.autoApprovedTools`** — ferramentas **auto-aprovadas**, executadas sem pedir confirmação. Adicionar `"shell"` aqui auto-aprova **todos** os comandos de shell (use com cautela).

## 6.2. Nomes das ferramentas embutidas

As ferramentas nativas do Gemini têm nomes como:

`read_file`, `write_file`, `replace`, `list_directory`, `run_shell_command`, `web_fetch`, `glob`, entre outras.

Use esses nomes ao montar as listas de `core`/`exclude`/`autoApprovedTools`.

# 7. Inspecionar a configuração efetiva

Não existe um único comando que liste todas as fontes de configuração com suas origens. Para depurar "de onde vem cada config", combine:

- **`/settings`** — abre o editor de configurações, mostrando os valores efetivos (resultado do merge das camadas).
- **`/memory show`** e **`/memory list`** — qual conteúdo de `GEMINI.md` está carregado e de quais caminhos.
- **`/mcp`** — quais servidores MCP estão configurados e conectados.
- **`/tools`** — as ferramentas atualmente disponíveis (reflete `core`/`exclude` aplicados).
- **`/about`** — versão e informações do ambiente.

Para inspeção de baixo nível de "qual camada venceu", abra manualmente os arquivos: `~/.gemini/settings.json` (usuário), `<projeto>/.gemini/settings.json` (workspace) e o de sistema/managed, se houver.

# 8. /clear (limpar a tela) vs. /compress (condensar contexto)

⚠️ Estes dois comandos fazem coisas diferentes — não confunda:

- **`/clear`** (atalho `Ctrl+L`) apenas **limpa a tela do terminal**. A conversa e o contexto continuam intactos.
- **`/compress`** condensa o contexto da sessão num resumo, reduzindo os tokens em uso mantendo o essencial. Use quando a sessão ficar longa e você quiser liberar janela de contexto sem perder o fio.

Para zerar de vez, **inicie uma nova sessão**. Isso preserva os servidores MCP e as configurações (que vivem no `settings.json`), pois eles não dependem do histórico do chat.

| Quero...                              | Comando                       |
|---------------------------------------|-------------------------------|
| Limpar a tela                         | `/clear` (`Ctrl+L`)           |
| Condensar o contexto da sessão        | `/compress`                   |
| Zerar completamente o contexto        | Nova sessão                   |

# 9. Sessões: /chat save e /chat resume

Salvar e retomar conversas é feito pela família de comandos `/chat`:

| Quero...                                | Comando                                              |
|-----------------------------------------|------------------------------------------------------|
| Salvar/nomear um ponto da conversa      | `/chat save <tag>`                                   |
| Listar conversas salvas                 | `/chat list`                                         |
| Retomar uma conversa específica         | `/chat resume <tag>`                                 |
| Exportar a conversa para arquivo        | `/chat share <arquivo>` (Markdown/JSON)              |

Pontos importantes:

- **Não há uma flag de inicialização** que retome automaticamente a última sessão. O fluxo é explícito: você salva pontos com `/chat save` e retoma com `/chat resume`. Para "continuar de ontem", crie o hábito de salvar uma tag antes de sair (ex.: `last`).
- **Permissões/aprovações com escopo de sessão são resetadas** ao retomar — você reaprovará ferramentas.
- Os saves ficam atrelados ao armazenamento local (em `~/.gemini/tmp/...`); use tags descritivas por projeto para não misturar.

> **Relacionado:** para retomar **junto com o estado dos arquivos** (não só a conversa), use o checkpointing — ver [/restore](#11-checkpointing-restore).

# 10. Onde ficam os artefatos de sessão

Os artefatos de sessão (logs, checkpoints, chats salvos) ficam sob:

```
~/.gemini/tmp/<project_hash>/
```

- **`checkpoints/`** — snapshots Git + histórico de conversa (ver [/restore](#11-checkpointing-restore)).
- **Logs e saves de chat** — os pontos criados por `/chat save` e os logs de sessão. O formato é JSON; dá para inspecionar/`grep` na pasta.

Observações:

- A organização é por **hash do projeto**, não por caminho legível.
- Os dados ficam em `tmp` e podem ser limpos pelo sistema ou pelo próprio CLI — **não conte com uma janela de retenção fixa**. Para preservar uma conversa importante, use `/chat save` ou exporte com `/chat share <arquivo>` para um local permanente.

# 11. Checkpointing: /restore

O **checkpointing** cria snapshots automáticos do estado do projeto + conversa, permitindo reverter a um ponto anterior.

## 11.1. Como funciona

Quando você aprova uma ferramenta que modifica o sistema de arquivos (`write_file` ou `replace`), o Gemini cria automaticamente um **checkpoint** contendo um snapshot Git (em um shadow repo) **e** o histórico da conversa. Restaurar reverte os arquivos do projeto ao estado capturado **e** restaura a conversa no CLI (é sempre "restaurar ambos" — código e conversa juntos).

- **`/restore`** — lista os checkpoints disponíveis (nomeados por timestamp + arquivo + ferramenta, ex.: `2025-06-22T10-00-00_000Z-my-file.txt-write_file`).
- **`/restore <id>`** — reverte ao checkpoint escolhido.

⚠️ **Pode ser preciso habilitar.** O checkpointing às vezes não vem ligado por padrão — ative com `gemini --checkpointing` ou pela config (`general.checkpointing.enabled: true`, ou a chave equivalente na sua versão).

Para apenas condensar o contexto (sem reverter arquivos), use `/compress` — ver [seção 8](#8-clear-limpar-a-tela-vs-compress-condensar-contexto).

## 11.2. O que os checkpoints NÃO rastreiam

O checkpointing captura apenas as edições feitas pelas **ferramentas de arquivo** do agente (`write_file`/`replace`). Portanto:

- Modificações feitas via `run_shell_command` (ex.: `rm`, `mv`, `cp`) **não** são revertíveis pelo `/restore`.
- Alterações manuais feitas fora do CLI também não são capturadas.

**Armazenamento:** todos os dados de checkpoint (snapshot Git + histórico) ficam localmente em `~/.gemini/tmp/<project_hash>/checkpoints`.

## 11.3. Sessões e branches do Git

A conversa do Gemini está atrelada ao **diretório de trabalho**, não à branch. Trocar de branch do Git não inicia uma nova conversa: o agente passa a ler os arquivos da nova branch imediatamente, mantendo o histórico de conversa.

# 12. Comandos personalizados (custom commands)

Os **custom commands** são o mecanismo principal e atual de comandos personalizados no Gemini. Um comando é um arquivo **TOML** contendo um `prompt` em linguagem natural; o nome do arquivo (sem `.toml`) vira o `/comando`.

```
.gemini/commands/review.toml   →  /review
.gemini/commands/commit.toml   →  /commit
.gemini/commands/deploy.toml   →  /deploy
```

## 12.1. Anatomia de um comando TOML

Exemplo `~/.gemini/commands/analyze-issue.toml`:

```toml
description = "Busca uma issue do GitHub, explora o codebase e gera uma especificação técnica."
prompt = """
Você é um analista de issues. Para a issue número {{args}} deste repositório:
1. Use o `gh` (via run_shell_command) para buscar os detalhes da issue.
2. Explore o codebase relevante.
3. Gere uma especificação técnica completa das correções propostas.
"""
```

Campos do TOML:

- **`prompt`** (obrigatório) — o prompt enviado ao modelo. Pode ser multilinha (`"""..."""`).
- **`description`** (opcional) — texto exibido no menu `/help`.

Aciona com **`/analyze-issue 123`** (o `{{args}}` recebe `123`).

## 12.2. Locais, namespaces e argumentos

**Locais (ordem de descoberta):**

- **User (global):** `~/.gemini/commands/` — disponível em qualquer projeto.
- **Project (local):** `<projeto>/.gemini/commands/` — específico do projeto, versionável no Git.

**Namespacing:** subpastas viram namespaces. `<projeto>/.gemini/commands/git/commit.toml` → comando `/git:commit`.

**Argumentos:** use `{{args}}` no prompt para receber o que o usuário digitar após o comando.

**Recarregar:** após criar/editar TOMLs, rode `/commands reload` para recarregar sem reiniciar.

Comandos personalizados são **acionados pelo usuário** (`/comando`). Para invocação **automática** quando uma tarefa casa com uma descrição, use **sub-agentes** ([seção 16](#16-sub-agentes)) ou **agent skills** empacotadas em extensões ([seção 13](#13-extensions-e-agent-skills)).

Referência: <https://google-gemini.github.io/gemini-cli/docs/cli/custom-commands.html>

# 13. Extensions e agent skills

**Extensions** são pacotes reutilizáveis que empacotam num formato instalável e compartilhável: *prompts, MCP servers, custom commands, themes, hooks, sub-agentes* e **agent skills**. São a forma de distribuir uma capacidade completa com um comando só.

- Instalação: `gemini extensions install <nome>`.
- O Gemini tem um **marketplace de extensões** com 90+ integrações instaláveis com um comando — quando o MCP ou a capacidade que você quer já está publicado lá, você pula a edição manual do `settings.json`.

As **agent skills** dentro de extensões permitem empacotar capacidades que o agente pode descobrir e usar automaticamente, complementando os custom commands (que são acionados pelo usuário).

Referência: <https://geminicli.com/docs/extensions/>

# 14. Hooks

O Gemini CLI tem um **sistema de hooks** (Hooks v1): scripts/programas que o CLI executa em pontos específicos do *agentic loop*, de forma **determinística** — sem depender do julgamento do modelo. Servem a três propósitos:

- **Automação** — ex.: rodar o Prettier automaticamente após cada edição.
- **Proteção** — ex.: bloquear qualquer tentativa de editar o `.env`.
- **Awareness** — ex.: enviar uma notificação quando o agente termina a resposta.

## 14.1. Onde os hooks são armazenados

Como configuração JSON no `settings.json`, com camadas que sofrem merge:

- **User settings** (`~/.gemini/settings.json`) — todos os projetos.
- **Workspace/Project settings** (`<projeto>/.gemini/settings.json`) — só aquele projeto.

## 14.2. Como os hooks funcionam

Os hooks rodam **sincronicamente** como parte do agent loop: quando um evento dispara, o Gemini CLI espera todos os hooks correspondentes terminarem antes de continuar.

## 14.3. Eventos de ciclo de vida

O Hooks v1 expõe eventos ao longo do ciclo do agente, como:

- **`BeforeModel`** — antes de a chamada ao modelo ser feita (útil para injeção de contexto e engenharia de prompt avançada).
- **`BeforeToolSelection`** — antes de o agente escolher/planejar ferramentas.
- (mais eventos são adicionados ao longo das versões — consulte a referência abaixo).

Mapeando necessidades clássicas para a abordagem no Gemini:

| Quero...                                  | Abordagem no Gemini                                          |
|-------------------------------------------|-------------------------------------------------------------|
| Formatar após editar arquivo              | Hook em evento de pós-ferramenta de edição                  |
| Bloquear edição de `.env`                 | Hook antes da seleção/uso de ferramenta + `tools.exclude`   |
| Notificar ao terminar a resposta          | Hook no fim do loop / evento de notificação                 |
| Injetar contexto no início                | `BeforeModel` (injeção de prompt)                           |

## 14.4. Estrutura de configuração

Os hooks são definidos em `settings.json` (sob uma chave `hooks`), associando um evento a um comando de shell. A forma exata do schema evolui entre versões — consulte a referência oficial para a sintaxe atual.

Referências: <https://geminicli.com/docs/hooks/> e a issue de design <https://github.com/google-gemini/gemini-cli/issues/9070>

# 15. MCP (Model Context Protocol)

O Gemini CLI tem **suporte de primeira classe a MCP** — o protocolo aberto que conecta o agente a ferramentas e fontes de dados externas (bancos de dados, GitHub, Notion, Slack, navegadores, etc.).

## 15.1. /mcp

**`/mcp`** lista os servidores MCP configurados, o status de conexão de cada um e as ferramentas que expõem. Variantes úteis:

- **`/mcp desc`** — descrições detalhadas das ferramentas MCP.
- **`/mcp schema`** — schema JSON dos parâmetros das ferramentas.

Toda ferramenta MCP descoberta recebe o prefixo `mcp_<alias-do-servidor>_` no nome totalmente qualificado.

## 15.2. Como configurar servidores MCP

Você configura os servidores no **`settings.json`**, sob a chave `mcpServers` — manualmente, pela UI do `/settings`, ou instalando uma **extensão** que já traz o MCP. Os transportes suportados incluem:

- **stdio** — processo local, via `command`/`args` (ex.: `npx ...`).
- **HTTP** — servidor remoto, via `httpUrl`.
- **SSE** — server-sent events.

## 15.3. Playwright / Chrome DevTools MCP

Servidores como o **Playwright MCP** e o **Chrome DevTools MCP** podem ser adicionados via `mcpServers` (tipicamente transporte stdio com `npx`). Eles dão ao agente a capacidade de dirigir e inspecionar um navegador.

**Exemplos de prompts** (fluxos de automação/inspeção de navegador):

- "A user reported that clicking 'Add to Cart' on the product page sometimes shows a 500 error. Go to localhost:5173/products/123, click Add to Cart 10 times, capture network requests and console errors, and tell me what's actually happening."
- "Navigate through the main user flows of my app at localhost:5173 (signup, login, dashboard, settings). Collect every console error and warning. Then look at the source code and propose fixes for each one, ranked by severity."
- "Take screenshots of every page in my app at 1920x1080, 768x768, and 375x667. Compare against the screenshots in ./baseline/. Tell me which pages have visual regressions and what changed."
- "Walk through my checkout flow at localhost:5173 as a real user would. Record what you do, then generate a Playwright test file that covers this flow with proper assertions and waits. Save it to tests/e2e/checkout.spec.ts."
- "The tests in tests/e2e/login.spec.ts are failing. Run them, use the browser to inspect the actual current DOM at localhost:5173/login, figure out whether the test is wrong or the app is broken, and fix whichever side is actually broken."
- "Crawl every page linked from my homepage at localhost:5173 (up to 2 levels deep). For each page, capture: page title, meta description, H1, word count, broken links, and load time. Give me a table sorted by problems found."
- "Test the signup form at localhost:5173/signup with these edge cases: empty fields, SQL injection strings, extremely long inputs, unicode/emoji, passwords that don't match, already-taken emails. For each, report what happened and whether the app handled it gracefully. Fix any issues you find in the validation logic."
- "Walk through the first-time user onboarding at localhost:5173. Screenshot each step, document what the user sees and does, and produce a getting-started guide with screenshots in docs/getting-started.md."

**Playwright MCP vs. Chrome DevTools MCP — qual usar:**

O **Chrome DevTools MCP** é ótimo para *observação e inspeção*:

- Capturar console errors/warnings
- Inspecionar o DOM atual
- Monitorar network requests
- Tirar screenshots
- Avaliar JavaScript na página

Prompts como o 1º (erros de rede), o 2º (console errors), o 5º (inspecionar DOM) e partes do 6º (load time, título, H1) funcionam bem com ele.

O que o Chrome DevTools MCP **não** faz e o **Playwright MCP** faz:

- **Automação de fluxo** — clicar, preencher formulários, navegar em sequência como um usuário real (prompts 1, 3, 4, 7, 8).
- **Screenshots multi-viewport** — redimensionar para 768px, 375px, etc. (prompt 3).
- **Gerar arquivos de teste** `.spec.ts` (prompt 4).
- **Crawling em profundidade** — seguir links automaticamente (prompt 6).
- **Edge case testing** em formulários (prompt 7).

**Resumo:** Chrome DevTools MCP para *observar e inspecionar*; Playwright MCP (ou similar) para *agir e interagir* na página como um usuário faria.

## 15.4. Context7 MCP: documentação sempre atualizada

Como todo LLM, o Gemini foi treinado com dados até um certo corte no tempo. Ao perguntar sobre uma biblioteca ou framework, ele pode:

- Conhecer o React 18, mas não o React 19.
- Sugerir APIs depreciadas que não existem mais.
- Perder features novas lançadas recentemente.
- Com confiança, entregar código que não funciona mais.

Não é descuido — é a natureza do treinamento com corte de dados. A documentação se move mais rápido que os ciclos de treinamento.

O **Context7** é um serviço de inteligência de documentação que:

- 📚 Indexa a documentação oficial de milhares de bibliotecas.
- 🔄 Mantém as docs continuamente atualizadas — sempre a versão mais recente.
- ⚡ Serve as docs num formato otimizado para LLMs.
- 🎯 Puxa apenas a seção relevante — não o site de docs inteiro.

Pense nele como um feed de documentação ao vivo que o agente pode consultar sob demanda, para qualquer biblioteca, qualquer versão.

**Configuração** — declare o servidor no bloco `mcpServers` do `settings.json` (workspace em `.gemini/settings.json`, ou global em `~/.gemini/settings.json`):

```json
{
  "mcpServers": {
    "context7": {
      "httpUrl": "https://mcp.context7.com/mcp"
    }
  }
}
```

Note que aqui não há `command`, `npx` nem processo local: este é um servidor MCP **remoto**, hospedado na internet. Por isso usamos a chave `httpUrl` — o Gemini o alcança via HTTP, ao vivo, sem subir nenhum processo na sua máquina.

> **Atalho pelo marketplace:** se o MCP já está publicado no marketplace de extensões, dá para pular a edição manual do `settings.json`:
>
> ```
> gemini extensions install context7
> ```
>
> A extensão registra o `mcpServers` por você. Depois, confirme que o servidor subiu com `/mcp`.

**Exemplo de uso real.** Suponha que o `App.jsx` importe avidamente (eager) todos os 18 componentes de página no topo — tudo agrupado no chunk JS inicial. A maioria dos usuários nunca visita rotas de admin ou employer, mas paga o custo de carregamento mesmo assim. A correção é fazer lazy-load das rotas com `lazy()` + Suspense do React — e a API lazy do React Router 7 difere da v6, então docs frescas fazem diferença:

```
Using context7, look up the React Router DOM v7 docs for lazy-loading routes with React.lazy() and Suspense.
Then refactor src/App.jsx in this job portal to lazy-load all page components instead of eagerly importing
them. Keep the provider nesting order and route structure intact. Add a simple fallback (a centered spinner or
"Loading..." text) for the Suspense boundary. Use the exact API from the fetched docs — don't rely on v6
patterns.
```

## 15.5. Cenários comuns com MCP

Quatro padrões de automação de ponta a ponta, combinando servidores MCP. Adicione cada MCP via `mcpServers` no `settings.json` ou instalando a extensão correspondente do marketplace.

### 15.5.1. Ticket → Code → PR

Ferramentas: Jira (ou Linear) + GitHub + Filesystem
Fluxo: Jira/Linear → Gemini CLI → GitHub MCP → PR criado

```
Implemente a feature descrita no ticket ENG-4521. Leia os detalhes,
escreva o código, rode os testes, commit e abra um PR no GitHub com
descrição adequada e link de volta ao ticket.
```

Resultado esperado: feature implementada + PR criado automaticamente.

### 15.5.2. Production Data → Code Insights

Ferramentas: Postgres (ou qualquer DB) + Filesystem
Fluxo: Postgres MCP → análise cruzada com o código → branch + commit

```
Query o PostgreSQL dos últimos 30 dias de uso da feature X.
Cruze com os módulos relevantes do repositório. Sugira e implemente
2 otimizações baseadas nos dados. Crie uma branch e commit as mudanças.
```

Resultado esperado: mudanças guiadas por dados com evidência (query exibida).

### 15.5.3. Monitoring → Auto-Fix

Ferramentas: Sentry (ou similar) + GitHub
Fluxo: Sentry MCP → análise de stack traces → fix → PR com métricas antes/depois

```
Verifique erros recentes no Sentry relacionados ao módulo de autenticação.
Analise os stack traces contra o codebase, encontre a causa raiz,
rode os testes e crie um PR com métricas de antes/depois.
```

Resultado esperado: bugs reais corrigidos ao vivo.

### 15.5.4. Cross-Tool Automation (Notion → Slack → Code)

Ferramentas: Notion + Slack + GitHub + Filesystem
Fluxo: Notion (spec) → GitHub (README + código) → Slack (#engineering) → Issue

```
Leia a spec mais recente do produto na página do Notion [link].
Atualize o README e os arquivos de código relevantes.
Poste um resumo no canal #engineering do Slack e crie um issue
de tracking no GitHub.
```

Resultado esperado: workflow completo em 4 ferramentas, zero passos manuais.

## 15.6. Referências

- MCP no Gemini: <https://geminicli.com/docs/tools/mcp-server/>
- Extensões (marketplace): <https://geminicli.com/docs/extensions/>

# 16. Sub-agentes

O Gemini CLI tem **sub-agentes**: especialistas isolados a quem o agente principal delega subtarefas, sem poluir a conversa principal. A ideia é a de um "arquiteto + especialistas": quando você dá uma tarefa ampla, o Gemini age como orquestrador estratégico e roteia subtarefas ao subagente mais relevante.

> "Subagentes são agentes especialistas que operam ao lado da sua sessão principal. Quando você dá uma tarefa ampla, o Gemini CLI age como um orquestrador estratégico, delegando subtarefas ao subagente mais relevante. Subagentes agem em isolamento, com seu próprio conjunto de ferramentas, MCP servers, instruções de sistema e janela de contexto. Toda a execução é consolidada em uma única resposta de volta ao agente principal."

Benefícios: gerenciamento de contexto (o subagente trabalha na própria janela e devolve só o resumo), especialização, otimização de custo (modelos menores para tarefas específicas), permissões controladas por agente e reusabilidade.

## 16.1. Criando um sub-agente

- Rode **`/agents`** para ver e gerenciar os subagentes configurados. As versões recentes oferecem um fluxo de criação interativo.
- Ou crie o arquivo manualmente. **Formato: Markdown (`.md`) com frontmatter YAML.**

**Locais:**

- **User (pessoal):** `~/.gemini/agents/`
- **Project (equipe):** `<projeto>/.gemini/agents/`

**Exemplo** (`~/.gemini/agents/api-documentation-helper.md`):

```markdown
---
name: api-documentation-helper
description: Generates clear API documentation from source code
tools: read_file, glob
model: gemini-2.5-flash
---

You are an API documentation specialist. When triggered, scan the
available source files and produce concise, developer-friendly
documentation that explains endpoints, request structures, and
responses.
```

O frontmatter define o nome, a descrição (usada para delegação), as ferramentas permitidas e o modelo; o corpo é o system prompt do subagente.

## 16.2. Delegação automática e explícita

- **Automática:** o orquestrador roteia tarefas ao subagente conforme a `description` e a relevância. Frases como "use proactively" na descrição ajudam a incentivar a delegação.
- **Explícita:** use a sintaxe **`@nome-do-agente`** no prompt, ex.: `@frontend-specialist revise nosso app`.
- **Ver agentes:** `/agents`.

## 16.3. Execução paralela

Múltiplos subagentes podem rodar **em paralelo** — peça explicitamente: *"Rode o frontend-specialist em cada pacote em paralelo."*

⚠️ Paralelizar acelera, mas aumenta o risco de conflitos de código e o consumo de API. A documentação foca em delegação/paralelismo; na prática, a sessão principal aguarda a resposta consolidada do subagente.

## 16.4. Memória persistente em sub-agentes

Subagentes podem ter **memória persistente** (configurável no frontmatter), de modo a aprenderem padrões, problemas recorrentes e decisões entre execuções. É o melhor caminho para dar aos seus fluxos uma memória de longo prazo que evolui com o uso.

Referência: <https://developers.googleblog.com/en/subagents-have-arrived-in-gemini-cli/>
