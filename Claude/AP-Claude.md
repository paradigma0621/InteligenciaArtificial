(testar pra ver se consigo fazer algo similar ao que o que foi feito pra migração: tipo um boot retroalimentado com planejamento de até consumir 100% token limit sozinho):

instalar MCP do banco de dados no BV

- [1. Auto-Aprendizado](#1-auto-aprendizado)
  - [1.1. O que acontece quando a memória está habilitada?](#11-o-que-acontece-quando-a-memória-está-habilitada)
  - [1.2. Como usar a memória de forma eficaz](#12-como-usar-a-memória-de-forma-eficaz)
  - [1.3. Delegação automática](#13-delegação-automática)
- [2. MCP](#2-mcp)
  - [2.1. Monitoring → Auto-Fix](#21-monitoring--auto-fix)
  - [2.2. Cross-Tool Automation (Notion → Slack → Code)](#22-cross-tool-automation-notion--slack--code)
    - [2.2.1. Production Data → Code Insights](#221-production-data--code-insights)
- [3. Rules](#3-rules)
- [4. /resume](#4-resume)
- [5. Como fazer rewind (ISSO PODE SER ÚTIL)](#5-como-fazer-rewind-isso-pode-ser-útil)


# 1. Auto-Aprendizado 
colocar o agente pra aprender e agir automaticamente nas minhas features dos meus apps.... aprender com os erros do macos codando pro AVP. aprender com minhas instruções de como fazer markdowns de evolução da informática mais ricos, etc

Você pode controlar onde a memória é armazenada dependendo de quão amplamente ela deve ser usada. Os valores válidos permitidos são `user`, `project`, `local`.

Obs: Os subtópicos de nível ## abaixo vieram da Seção # Sub-Agents do Claude
## 1.1. O que acontece quando a memória está habilitada?

Quando um sub-agente usa memória:

- Seu system prompt inclui instruções para ler e atualizar arquivos de memória.
- As primeiras 200 linhas do MEMORY.md são automaticamente fornecidas ao agente.
- Se o arquivo crescer demais, o agente é orientado a mantê-lo conciso.
- As ferramentas Read, Write e Edit são automaticamente habilitadas para que o agente possa gerenciar sua memória.

## 1.2. Como usar a memória de forma eficaz

Você pode orientar o sub-agente com instruções simples:

- Antes de começar o trabalho → "Check your memory for similar issues before analyzing this code."
- Depois de terminar o trabalho → "Save the important findings to your memory."

Com o tempo, isso cria uma base de conhecimento crescente que melhora o desempenho do agente.

## 1.3. Delegação automática

O Claude decide quando usar um sub-agente com base em:
- A redação do seu pedido
- A descrição definida dentro do arquivo do sub-agente
- O contexto de trabalho atual

Se uma tarefa casa com o propósito de um sub-agente, o Claude pode delegar o trabalho automaticamente. Para encorajar esse comportamento, você pode adicionar frases como "use proactively" na descrição do sub-agente, para que o Claude saiba que ele deve ser selecionado sempre que for relevante.

# 2. MCP
## 2.1. Monitoring → Auto-Fix

Ferramentas: Sentry (ou similar) + GitHub

Fluxo: Sentry MCP → análise de stack traces → fix → PR com métricas antes/depois

Prompt de exemplo:

```
Verifique erros recentes no Sentry relacionados ao módulo de autenticação.
Analise os stack traces contra o codebase, encontre a causa raiz,
rode os testes e crie um PR com métricas de antes/depois.
```

Resultado esperado: bugs reais corrigidos ao vivo.
## 2.2. Cross-Tool Automation (Notion → Slack → Code)

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


### 2.2.1. Production Data → Code Insights

Ferramentas: Postgres (ou qualquer DB) + Filesystem

Fluxo: Postgres MCP → análise cruzada com código → branch + commit

Prompt de exemplo:

```
Query o PostgreSQL dos últimos 30 dias de uso da feature X.
Cruze com os módulos relevantes do repositório. Sugira e implemente
2 otimizações baseadas nos dados. Crie uma branch e commit as mudanças.
```

Resultado esperado: mudanças guiadas por dados com evidência (query exibida).

# 3. Rules
Aplicar rules para diferenciar quando eu lanço só 1 agente (para não criar branch) e quando estou trabalhando numa pasta de só documentos texto - mesmo motivo acima

# 4. /resume

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

# 5. Como fazer rewind (ISSO PODE SER ÚTIL)
Pressione Esc duas vezes ou use o comando /rewind para abrir o menu de rewind. Você então escolhe um checkpoint e decide o que restaurar.
