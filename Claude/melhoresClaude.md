- [1. Geral](#1-geral)
  - [1.1. Curso gratuito oferecido pela Anthropic](#11-curso-gratuito-oferecido-pela-anthropic)
  - [1.2. Sonnet 5](#12-sonnet-5)
  - [1.3. CLAUDE.md](#13-claudemd)
  - [1.4. /usage](#14-usage)
  - [1.5. /effort](#15-effort)
  - [1.6. /context](#16-context)
- [2. Como fazer rewind (ISSO PODE SER ÚTIL)](#2-como-fazer-rewind-isso-pode-ser-útil)
- [3. Git](#3-git)
  - [3.1. Plugin commit-commands](#31-plugin-commit-commands)
- [4. Sub-Agents](#4-sub-agents)
  - [4.1. Memória persistente em Sub-Agents](#41-memória-persistente-em-sub-agents)
  - [4.2. O que acontece quando a memória está habilitada?](#42-o-que-acontece-quando-a-memória-está-habilitada)
  - [4.3. Como usar a memória de forma eficaz](#43-como-usar-a-memória-de-forma-eficaz)
  - [4.4. Delegação automática](#44-delegação-automática)
- [5. MCP](#5-mcp)
  - [5.1. Ticket → Code → PR](#51-ticket--code--pr)
  - [5.2. Production Data → Code Insights](#52-production-data--code-insights)
  - [5.3. Monitoring → Auto-Fix](#53-monitoring--auto-fix)
  - [5.4. Cross-Tool Automation (Notion → Slack → Code)](#54-cross-tool-automation-notion--slack--code)
- [6. Os hábitos de sessão do desenvolvedor esperto](#6-os-hábitos-de-sessão-do-desenvolvedor-esperto)
- [7. /rename](#7-rename)
- [8. /resume](#8-resume)
- [9. /export](#9-export)

# 1. Geral
## 1.1. Curso gratuito oferecido pela Anthropic
https://www.anthropic.com/learn
## 1.2. Sonnet 5
Equilíbrio entre custo e capacidade. Em boa parte das tarefas de engenharia de software do dia a dia entrega qualidade próxima à do Opus por um preço menor: **US$ 3 / US$ 15** por milhão de tokens (entrada/saída) contra **US$ 5 / US$ 25** do Opus 4.8 — cerca de **60% do custo**. (Preço introdutório de US$ 2 / US$ 10 vigente até 2026-08-31.)

## 1.3. CLAUDE.md
Use `IMPORTANT` ou `YOU MUST` para reforçar diretrizes que o Claude deve seguir à risca — por exemplo: commitar com mensagens em inglês e nunca mencionar que o commit foi feito por uma IA.

## 1.4. /usage
Permite ver o uso consumido e o limite de uso para o dia/semana.

## 1.5. /effort
Define o nível de esforço da sessão, escolhendo entre os níveis disponíveis (do mais econômico ao mais capaz). O nível máximo entrega a maior capacidade com o raciocínio mais profundo, ao custo de mais tokens e maior latência.

## 1.6. /context
Mostra quanto da janela de contexto está em uso na sessão atual. Rode periodicamente — pense nele como o marcador de combustível: se estiver alto e ainda houver muito trabalho pela frente, compacte (`/compact`) ou limpe (`/clear`). Dá também para configurar uma status line personalizada que exibe o uso de contexto o tempo todo na barra inferior.

# 2. Como fazer rewind (ISSO PODE SER ÚTIL)
Pressione `Esc` duas vezes ou use o comando `/rewind` para abrir o menu de rewind. Você então escolhe um checkpoint e decide o que restaurar:

- **Código e conversa** — reverte os arquivos do projeto e o histórico da conversa juntos ao ponto escolhido.
- **Apenas a conversa** — volta o histórico do chat, mas mantém os arquivos como estão agora.
- **Apenas o código** — reverte os arquivos do projeto, mas preserva a conversa atual.

> ⚠️ O rewind rastreia as edições feitas pelas ferramentas do Claude. Mudanças feitas por fora (comandos de shell como `rm`/`mv`, ou edições manuais no editor) não são revertidas.

# 3. Git
## 3.1. Plugin commit-commands

O plugin Commit Commands automatiza operações git comuns, reduzindo a troca de contexto e a execução manual de comandos. Em vez de rodar vários comandos git, use um único comando de barra para lidar com todo o seu workflow.

**Instalar o plugin:** Rode o comando `/plugin` e instale o plugin commit-commands, que fornece os seguintes comandos executáveis a partir de sessões do Claude Code:

| Comando           | O que faz                                                                          |
|-------------------|------------------------------------------------------------------------------------|
| `/commit`         | Cria um commit git das mudanças atuais                                             |
| `/commit-push-pr` | Faz commit, push e abre um Pull Request                                            |
| `/clean_gone`     | Remove branches locais que já foram deletadas no remoto (e as worktrees associadas) |

# 4. Sub-Agents
## 4.1. Memória persistente em Sub-Agents

Sub-agentes podem receber memória persistente, o que lhes permite lembrar informações entre conversas diferentes. Quando a memória está habilitada, o agente armazena conhecimento útil como:

- Padrões comuns no codebase
- Problemas recorrentes que descobre
- Decisões de design importantes
- Insights úteis de debugging

Isso torna o sub-agente mais inteligente com o tempo, porque ele aprende com tarefas anteriores.

Exemplo de sub-agente com memória habilitada:

```markdown
---
name: test-analysis-agent
description: Analyzes test cases and tracks recurring failures
memory: user
---

You are a testing specialist. While reviewing test files, record repeated
failures, flaky tests, and common patterns into your agent memory so you
can recognize them in future reviews.
```

Você pode controlar onde a memória é armazenada dependendo de quão amplamente ela deve ser usada. Os valores válidos permitidos são `user`, `project`, `local`.

## 4.2. O que acontece quando a memória está habilitada?

Quando um sub-agente usa memória:

- Seu system prompt inclui instruções para ler e atualizar arquivos de memória.
- As primeiras 200 linhas do MEMORY.md são automaticamente fornecidas ao agente.
- Se o arquivo crescer demais, o agente é orientado a mantê-lo conciso.
- As ferramentas Read, Write e Edit são automaticamente habilitadas para que o agente possa gerenciar sua memória.

## 4.3. Como usar a memória de forma eficaz

Você pode orientar o sub-agente com instruções simples:

- Antes de começar o trabalho → "Check your memory for similar issues before analyzing this code."
- Depois de terminar o trabalho → "Save the important findings to your memory."

Com o tempo, isso cria uma base de conhecimento crescente que melhora o desempenho do agente.

## 4.4. Delegação automática

O Claude decide quando usar um sub-agente com base em:
- A redação do seu pedido
- A descrição definida dentro do arquivo do sub-agente
- O contexto de trabalho atual

Se uma tarefa casa com o propósito de um sub-agente, o Claude pode delegar o trabalho automaticamente. Para encorajar esse comportamento, você pode adicionar frases como "use proactively" na descrição do sub-agente, para que o Claude saiba que ele deve ser selecionado sempre que for relevante.

# 5. MCP

O Claude Code tem suporte a **MCP (Model Context Protocol)** — o protocolo aberto que conecta o agente a ferramentas e fontes de dados externas (bancos de dados, GitHub, Jira, Sentry, Notion, Slack, etc.). Você adiciona servidores com `claude mcp add ...` e os inspeciona com `/mcp`. A seguir, quatro cenários comuns que combinam servidores MCP de ponta a ponta.

## 5.1. Ticket → Code → PR

Ferramentas: Jira (ou Linear) + GitHub + Filesystem

Fluxo: Jira/Linear → Claude Code → GitHub MCP → PR criado

Prompt de exemplo:

```
Implemente a feature descrita no ticket ENG-4521. Leia os detalhes,
escreva o código, rode os testes, commit e abra um PR no GitHub com
descrição adequada e link de volta ao ticket.
```

Resultado esperado: feature implementada + PR criado automaticamente.

## 5.2. Production Data → Code Insights

Ferramentas: Postgres (ou qualquer DB) + Filesystem

Fluxo: Postgres MCP → análise cruzada com código → branch + commit

Prompt de exemplo:

```
Query o PostgreSQL dos últimos 30 dias de uso da feature X.
Cruze com os módulos relevantes do repositório. Sugira e implemente
2 otimizações baseadas nos dados. Crie uma branch e commit as mudanças.
```

Resultado esperado: mudanças guiadas por dados com evidência (query exibida).

## 5.3. Monitoring → Auto-Fix

Ferramentas: Sentry (ou similar) + GitHub

Fluxo: Sentry MCP → análise de stack traces → fix → PR com métricas antes/depois

Prompt de exemplo:

```
Verifique erros recentes no Sentry relacionados ao módulo de autenticação.
Analise os stack traces contra o codebase, encontre a causa raiz,
rode os testes e crie um PR com métricas de antes/depois.
```

Resultado esperado: bugs reais corrigidos ao vivo.

## 5.4. Cross-Tool Automation (Notion → Slack → Code)

Ferramentas: Notion + Slack + GitHub + Filesystem

Fluxo: Notion (spec) → GitHub (README + código) → Slack (#engineering) → Issue

Prompt de exemplo:

```
Leia a spec mais recente do produto na página do Notion [link].
Atualize o README e os arquivos de código relevantes.
Poste um resumo no canal #engineering do Slack e crie um issue
de tracking no GitHub.
```

Resultado esperado: workflow completo em 4 ferramentas, zero passos manuais.

# 6. Os hábitos de sessão do desenvolvedor esperto
**Hábito 1: Nomeie suas sessões**
Digite `/rename payment-gateway-fix` assim que começar um trabalho significativo. O você do futuro vai agradecer ao você do presente quando estiver encarando uma lista de 50 sessões sem nome.

**Hábito 2: Monitore seu contexto**
Rode `/context` periodicamente. Pense nisso como checar o marcador de combustível do seu carro. Se você estiver acima de 60% e ainda tiver muito trabalho pela frente, compacte ou limpe. Você também pode configurar uma status line personalizada para sempre mostrar o uso de contexto na barra inferior.

**Hábito 3: Use o padrão Documentar & Limpar**
Para tarefas realmente grandes, peça ao Claude para escrever seu plano e progresso em um arquivo `.md`, depois `/clear`, e então comece uma nova sessão dizendo ao Claude para ler esse arquivo e continuar. Isso te dá contexto fresco com conhecimento preservado.

# 7. /rename

Atribui um nome à sessão atual. Ela poderá ser recarregada depois com o comando abaixo (`/resume`)

# 8. /resume

Apresenta o histórico de sessões para que você possa recarregar uma delas.

**Retome uma sessão (continue de onde parou)**

Fechou o terminal por engano? Precisa continuar o debugging de ontem?

| Comando                            | O que faz                          |
|------------------------------------|------------------------------------|
| `claude --continue` ou `claude -c` | Retoma sua sessão mais recente     |
| `claude --resume <session-id>`     | Retoma uma sessão passada específica |

**Quando você retoma:**

- Você recupera todo o seu histórico de conversa
- Novas mensagens são adicionadas à mesma sessão
- Mas as permissões com escopo de sessão são resetadas — você precisará reaprová-las

Pense nisso como reabrir o mesmo caderno — todas as suas anotações estão lá, mas os "crachás de acesso" expiraram.

# 9. /export

Exporta a conversa atual. Sem argumento, abre um menu que permite **copiar para o clipboard** ou **salvar em um arquivo**. Com argumento (`/export transcript.txt`), pula o menu e grava direto no arquivo indicado.

- **Formato:** texto plano legível (o transcript renderizado), não JSON nem Markdown estruturado.
- **Não** gera link compartilhável em nuvem — a saída é só clipboard ou arquivo local.
- Se precisar de JSON para script, use `claude -p --resume <session-id> --output-format json`.
