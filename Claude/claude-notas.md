Notas do curso da Udemy: [Claude Code Bootcamp](https://www.udemy.com/course/claude-code-bootcamp)

Curso gratuíto oferecido pela Anthropic: https://www.anthropic.com/learn

- [1. /model](#1-model)
- [2. VSCode](#2-vscode)
  - [2.1. Carregando o VSCode a partir da pasta de uma sessão](#21-carregando-o-vscode-a-partir-da-pasta-de-uma-sessão)
  - [2.2. Selecionando arquivos de contexto](#22-selecionando-arquivos-de-contexto)
- [3. Modos de operação](#3-modos-de-operação)
- [4. /voice](#4-voice)
- [5. O arquivo CLAUDE.md](#5-o-arquivo-claudemd)
  - [5.1. Primeiros passos](#51-primeiros-passos)
  - [5.2. Importando outros arquivos](#52-importando-outros-arquivos)
  - [5.3. O que incluir (alto valor)](#53-o-que-incluir-alto-valor)
  - [5.4. O que evitar (baixo valor ou arriscado)](#54-o-que-evitar-baixo-valor-ou-arriscado)
  - [5.5. Trate o CLAUDE.md como código](#55-trate-o-claudemd-como-código)
- [6. Configurações do Claude Code](#6-configurações-do-claude-code)
  - [6.1. Abordagem 1: O comando /config (UI interativa)](#61-abordagem-1-o-comando-config-ui-interativa)
  - [6.2. Abordagem 2: Arquivos settings.json (configuração persistente)](#62-abordagem-2-arquivos-settingsjson-configuração-persistente)
    - [6.2.1. Qual configuração prevalece? (Ordem de prioridade)](#621-qual-configuração-prevalece-ordem-de-prioridade)
    - [6.2.2. Uma estrutura típica de settings.json](#622-uma-estrutura-típica-de-settingsjson)
- [7. /permissions](#7-permissions)
  - [7.1. Permissões no Claude Code](#71-permissões-no-claude-code)
    - [7.1.1. Definindo regras de permissão](#711-definindo-regras-de-permissão)
      - [7.1.1.1. Casar com tudo](#7111-casar-com-tudo)
      - [7.1.1.2. Casar com algo específico](#7112-casar-com-algo-específico)
      - [7.1.1.3. Curingas para flexibilidade](#7113-curingas-para-flexibilidade)
      - [7.1.1.4. Um exemplo do mundo real](#7114-um-exemplo-do-mundo-real)
- [8. /status](#8-status)
- [9. /usage](#9-usage)
- [10. Output Style](#10-output-style)
  - [10.1. Crie um Output Style personalizado no Claude Code](#101-crie-um-output-style-personalizado-no-claude-code)
    - [10.1.1. O que é um Output Style personalizado?](#1011-o-que-é-um-output-style-personalizado)
    - [10.1.2. Estrutura de um Output Style personalizado](#1012-estrutura-de-um-output-style-personalizado)
    - [10.1.3. Onde salvar seus arquivos de estilo](#1013-onde-salvar-seus-arquivos-de-estilo)
    - [10.1.4. Casos de uso práticos](#1014-casos-de-uso-práticos)
- [11. /effort](#11-effort)
- [12. Statelessness e a ilusão da conversa contínua](#12-statelessness-e-a-ilusão-da-conversa-contínua)
- [13. /context](#13-context)
  - [13.1. O que acontece quando o contexto enche?](#131-o-que-acontece-quando-o-contexto-enche)
- [14. /compact](#14-compact)
- [15. /clear](#15-clear)
- [16. /rename](#16-rename)
  - [16.1. Dúvida #01](#161-dúvida-01)
- [17. /resume](#17-resume)
- [18. claude --continue --fork-session](#18-claude---continue---fork-session)
  - [18.1. Como o Claude Code gerencia sessões entre branches do Git](#181-como-o-claude-code-gerencia-sessões-entre-branches-do-git)
- [19. /rewind (= desfazer)](#19-rewind--desfazer)
  - [19.1. Como fazer rewind](#191-como-fazer-rewind)
  - [19.2. O que os checkpoints NÃO rastreiam](#192-o-que-os-checkpoints-não-rastreiam)
- [20. Histórico](#20-histórico)
- [21. Os hábitos de sessão do desenvolvedor esperto](#21-os-hábitos-de-sessão-do-desenvolvedor-esperto)
- [22. Memory (Memória)](#22-memory-memória)
  - [22.1. /memory](#221-memory)
  - [22.2. Auto Memory no Claude Code](#222-auto-memory-no-claude-code)
    - [22.2.1. Dois sistemas de memória: o livro-texto vs. o caderno](#2221-dois-sistemas-de-memória-o-livro-texto-vs-o-caderno)
      - [22.2.1.1. CLAUDE.md — O livro-texto (escrito por VOCÊ)](#22211-claudemd--o-livro-texto-escrito-por-você)
      - [22.2.1.2. Auto Memory (MEMORY.md) — O caderno (escrito pelo CLAUDE)](#22212-auto-memory-memorymd--o-caderno-escrito-pelo-claude)
    - [22.2.2. Como o Auto Memory funciona por baixo dos panos](#2222-como-o-auto-memory-funciona-por-baixo-dos-panos)
    - [22.2.3. Onde o Claude armazena suas anotações?](#2223-onde-o-claude-armazena-suas-anotações)
      - [22.2.3.1. Mensagens de status](#22231-mensagens-de-status)
  - [22.3. O comando /memory](#223-o-comando-memory)
    - [22.3.1. Dizendo ao Claude o que lembrar](#2231-dizendo-ao-claude-o-que-lembrar)
  - [22.4. As três camadas de memória — o quadro completo](#224-as-três-camadas-de-memória--o-quadro-completo)
  - [22.5. Configurando o Auto Memory](#225-configurando-o-auto-memory)
    - [22.5.1. Como alternar (toggle)](#2251-como-alternar-toggle)
    - [22.5.2. Diretório de memória personalizado](#2252-diretório-de-memória-personalizado)
    - [22.5.3. Como funciona](#2253-como-funciona)
- [23. Rules (Regras)](#23-rules-regras)
  - [23.1. Rules no Claude Code](#231-rules-no-claude-code)
  - [23.2. Onde as Rules vivem?](#232-onde-as-rules-vivem)
  - [23.3. Dois tipos de regras](#233-dois-tipos-de-regras)
    - [23.3.1. Regras sempre carregadas (always-loaded)](#2331-regras-sempre-carregadas-always-loaded)
    - [23.3.2. Regras com escopo de path (path-scoped)](#2332-regras-com-escopo-de-path-path-scoped)
    - [23.3.3. Rules vs CLAUDE.md — quando usar qual](#2333-rules-vs-claudemd--quando-usar-qual)
- [24. Skills](#24-skills)
  - [24.1. Construa sua própria skill](#241-construa-sua-própria-skill)
    - [24.1.1. Passos para criar uma skill personalizada](#2411-passos-para-criar-uma-skill-personalizada)
      - [24.1.1.1. 1) Crie o diretório da skill](#24111-1-crie-o-diretório-da-skill)
      - [24.1.1.2. 2) Escreva um arquivo SKILL.md](#24112-2-escreva-um-arquivo-skillmd)
      - [24.1.1.3. 3) Teste a skill](#24113-3-teste-a-skill)
  - [24.2. Site de referência: https://code.claude.com/docs/en/skills (tem informações importantes)](#242-site-de-referência-httpscodeclaudecomdocsenskills-tem-informações-importantes)
  - [24.3. `./skills/feature-guide`: exemplo de como rodar uma skill em um sub-agente](#243-skillsfeature-guide-exemplo-de-como-rodar-uma-skill-em-um-sub-agente)
- [25. commands (deprecado)](#25-commands-deprecado)
- [26. hooks](#26-hooks)
  - [26.1. O que exatamente são hooks?](#261-o-que-exatamente-são-hooks)
  - [26.2. Determinístico](#262-determinístico)
  - [26.3. Agora, qual o propósito? Por que os hooks existem?](#263-agora-qual-o-propósito-por-que-os-hooks-existem)
    - [26.3.1. Primeiro — automação](#2631-primeiro--automação)
    - [26.3.2. Segundo — proteção](#2632-segundo--proteção)
    - [26.3.3. Terceiro — consciência (awareness)](#2633-terceiro--consciência-awareness)
  - [26.4. Sem hooks, todas as três dependem do julgamento da IA.](#264-sem-hooks-todas-as-três-dependem-do-julgamento-da-ia)
  - [26.5. O ponto de dor sem hooks](#265-o-ponto-de-dor-sem-hooks)
  - [26.6. Onde os hooks são armazenados?](#266-onde-os-hooks-são-armazenados)
  - [26.7. Criando um hook](#267-criando-um-hook)
  - [26.8. Estrutura de configuração de hook](#268-estrutura-de-configuração-de-hook)
  - [26.9. Configure seu primeiro hook](#269-configure-seu-primeiro-hook)
  - [26.10. Observação](#2610-observação)
  - [26.11. Como os hooks funcionam](#2611-como-os-hooks-funcionam)
  - [26.12. IMPORTANTE](#2612-importante)
- [27. MCP](#27-mcp)
  - [27.1. /mcp](#271-mcp)
  - [27.2. Site de referência (IMPORTANTE VER)](#272-site-de-referência-importante-ver)
  - [27.3. Exemplos de prompts que podem ser usados com Playwright (alguns com Google Chrome)](#273-exemplos-de-prompts-que-podem-ser-usados-com-playwright-alguns-com-google-chrome)
  - [27.4. Context7 MCP: o Claude recebe docs atualizadas](#274-context7-mcp-o-claude-recebe-docs-atualizadas)
    - [27.4.1. Um comando. Docs sempre frescas para o Claude.](#2741-um-comando-docs-sempre-frescas-para-o-claude)
  - [27.5. Cenários comuns com MCP](#275-cenários-comuns-com-mcp)
    - [27.5.1. Ticket → Code → PR](#2751-ticket--code--pr)
    - [27.5.2. Production Data → Code Insights](#2752-production-data--code-insights)
    - [27.5.3. Monitoring → Auto-Fix](#2753-monitoring--auto-fix)
    - [27.5.4. Cross-Tool Automation (Notion → Slack → Code)](#2754-cross-tool-automation-notion--slack--code)
- [28. loop](#28-loop)
  - [28.1. Rodando prompts em um agendamento](#281-rodando-prompts-em-um-agendamento)
  - [28.2. /loop — Rode um prompt em repetição, sem usar as mãos](#282-loop--rode-um-prompt-em-repetição-sem-usar-as-mãos)
  - [28.3. Intervalo inteligente (`/loop ...` sem tempo)](#283-intervalo-inteligente-loop--sem-tempo)
  - [28.4. O prompt de manutenção embutido](#284-o-prompt-de-manutenção-embutido)
  - [28.5. Coisas para ter em mente](#285-coisas-para-ter-em-mente)
  - [28.6. Lembretes em linguagem natural](#286-lembretes-em-linguagem-natural)
  - [28.7. Referência de tarefas agendadas](#287-referência-de-tarefas-agendadas)
- [29. Sub-Agents](#29-sub-agents)
  - [29.1. O que são Sub Agents?](#291-o-que-são-sub-agents)
  - [29.2. Por que usar Sub-Agents?](#292-por-que-usar-sub-agents)
    - [29.2.1. Janela de contexto](#2921-janela-de-contexto)
      - [29.2.1.1. Início da sessão:](#29211-início-da-sessão)
      - [29.2.1.2. No uso:](#29212-no-uso)
    - [29.2.2. Isolado](#2922-isolado)
  - [29.3. Criando um sub-agente](#293-criando-um-sub-agente)
  - [29.4. Memória persistente em Sub-Agents](#294-memória-persistente-em-sub-agents)
  - [29.5. O que acontece quando a memória está habilitada?](#295-o-que-acontece-quando-a-memória-está-habilitada)
  - [29.6. Como usar a memória de forma eficaz](#296-como-usar-a-memória-de-forma-eficaz)
  - [29.7. Delegação automática](#297-delegação-automática)
  - [29.8. Execução em foreground vs background](#298-execução-em-foreground-vs-background)
- [30. Agent teams (equipes de agentes)](#30-agent-teams-equipes-de-agentes)
- [31. Git](#31-git)
  - [31.1. Claude Code para tarefas e atividades no GitHub](#311-claude-code-para-tarefas-e-atividades-no-github)
  - [31.2. Operações Git pelo terminal](#312-operações-git-pelo-terminal)
  - [31.3. Plugin commit-commands](#313-plugin-commit-commands)
  - [31.4. Rode sessões paralelas do Claude Code com Git Worktrees](#314-rode-sessões-paralelas-do-claude-code-com-git-worktrees)
    - [31.4.1. Por que precisamos de worktrees?](#3141-por-que-precisamos-de-worktrees)
    - [31.4.2. O que é um Git Worktree?](#3142-o-que-é-um-git-worktree)
    - [31.4.3. Como o Claude usa worktrees](#3143-como-o-claude-usa-worktrees)
    - [31.4.4. Rodando múltiplas sessões](#3144-rodando-múltiplas-sessões)
    - [31.4.5. Onde os worktrees são armazenados?](#3145-onde-os-worktrees-são-armazenados)
    - [31.4.6. Criando worktrees durante uma sessão](#3146-criando-worktrees-durante-uma-sessão)
  - [31.5. Integração com GitHub Actions (o bot @claude)](#315-integração-com-github-actions-o-bot-claude)
  - [31.6. Configurando a GitHub Action — Início rápido](#316-configurando-a-github-action--início-rápido)
- [32. Status Line](#32-status-line)
  - [32.1. Como a Status Line funciona — JSON na entrada, texto na saída](#321-como-a-status-line-funciona--json-na-entrada-texto-na-saída)
  - [32.2. O caminho "eu nem escrevi um script"](#322-o-caminho-eu-nem-escrevi-um-script)
  - [32.3. O caminho manual (`~/.claude/settings.json`)](#323-o-caminho-manual-claudesettingsjson)
    - [32.3.1. O arquivo statusline-command.sh](#3231-o-arquivo-statusline-commandsh)
  - [32.4. Referência de documentação](#324-referência-de-documentação)
- [33. Comandos genéricos](#33-comandos-genéricos)


# 1. /model
Permite escolher qual modelo de LLM usar.

- **Opus 4.8**: raciocínio mais profundo, tende a resolver em menos turnos, mas com respostas e cadeias de pensamento mais longas. Melhor custo-efetividade em tarefas complexas (refactors grandes, debugging arquitetural) onde Sonnet/Haiku precisariam de várias iterações.
- **Sonnet 4.6**: equilíbrio. Para a maioria das tarefas de engenharia de software do dia a dia, gasta tokens comparáveis ao Opus, mas a 1/5 do preço.
- **Haiku 4.5**: respostas mais curtas e diretas. Excelente para tarefas determinísticas (correções de lint, renomeações, leituras simples), mas pode multiplicar turnos em tarefas ambíguas — anulando a economia.

# 2. VSCode

## 2.1. Carregando o VSCode a partir da pasta de uma sessão

Indo na pasta onde foi iniciada uma sessão do comando `claude` no terminal, é possível carregar o VSCode e, carregando a ferramenta do Claude nele, navegar pelas conversas que foram feitas no terminal, visualizando-as como uma pré-visualização Markdown.

## 2.2. Selecionando arquivos de contexto

É possível selecionar quais arquivos se deseja ter como contexto (por padrão, o que estiver aberto no momento) no chat. Caso se selecione linhas dentro do arquivo aberto, essas linhas selecionadas passam a ser o contexto na guia do chat.

# 3. Modos de operação

Modos disponíveis:

**Modo padrão (Default)**
- É o modo já ativo ao iniciar o Claude Code normalmente.
- Cada ação potencialmente destrutiva pede confirmação.

**Modo auto-accept (também chamado de Edit Mode)**
- Pressione `Shift+Tab` para alternar (toggle) o auto-accept.
- Aceita permissões automaticamente sem pedir confirmação (Create/Edit/Delete).

**Modo Plan**
- Pressione `Shift+Tab` duas vezes (cicla entre os modos).
- Ou use o comando `/plan` no chat.
- O Claude apenas planeja, não executa ações — você aprova antes de qualquer mudança.

**Modo YOLO**
- Funciona com o comando `claude --dangerously-skip-permissions` (ou no VSCode, definindo a variável de ambiente do modo bypass permissions para rodá-lo no modo Native UI).
- Além de poder fazer Create/Edit/Delete sem confirmação, também pode rodar qualquer comando de terminal sem questionar permissões (ex.: commitar, instalar pacotes, etc.).
- Bypassa completamente o sistema de permissões.
- O Claude não pergunta sobre nenhuma ação, incluindo as destrutivas.
- É o modo mais permissivo e potencialmente perigoso.
- Indicado para ambientes isolados/CI onde não há interação humana.

> **Observação:** Para interromper o processamento de qualquer modo, enquanto em execução, pressione `ESC`.

# 4. /voice

Permite usar o servidor do Claude para transcrever áudio do microfone em texto transcrito em tempo real. Não consome tokens, mas há o porém da privacidade dos dados: sobre o que não sabemos com o que é feito com o texto da narrativa.

Sugestão de alternativa grátis e sigilosa: https://handy.computer/

# 5. O arquivo CLAUDE.md

Recomendação: não passe de 300 linhas.

## 5.1. Primeiros passos

Você não precisa criar o arquivo CLAUDE.md manualmente. Em vez disso, rode `/init`. O Claude Code analisa seu codebase e gera um CLAUDE.md inicial.

Ele detecta sistemas de build, frameworks de teste e padrões de código automaticamente. Isso dá uma base sólida para refinar e personalizar. Não há formato obrigatório — mantenha-o curto, claro e legível por humanos.

## 5.2. Importando outros arquivos

Arquivos CLAUDE.md podem importar arquivos adicionais usando a sintaxe `@caminho/para/import`:

```
See @README.md for project overview
See @package.json for available commands

# Additional Instructions
  - Git workflow: @docs/git-instructions.md
  - Personal overrides: @~/.claude/my-project-instructions.md
```

Isso mantém o CLAUDE.md enxuto, ao mesmo tempo em que dá ao Claude acesso a contexto detalhado quando necessário.

| Local                              | Propósito                                                                                          |
|------------------------------------|---------------------------------------------------------------------------------------------------|
| Pasta home (`~/.claude/CLAUDE.md`) | Aplica-se globalmente a todas as suas sessões do Claude                                            |
| Raiz do projeto (`./CLAUDE.md`)    | Aplica-se a um dado projeto. Pode ser compartilhado com a equipe via Git                           |
| `./CLAUDE.local.md`                | Overrides pessoais, adicione ao `.gitignore`                                                       |
| Diretórios pais                    | Útil para monorepos onde tanto `root/CLAUDE.md` quanto `root/foo/CLAUDE.md` são carregados automaticamente |
| Diretórios filhos                  | O Claude os carrega sob demanda ao trabalhar nessas pastas                                         |

## 5.3. O que incluir (alto valor)

- Tecnologias e versões exatas usadas no projeto
- Estrutura de pastas e pelo que cada pasta é responsável
- Comandos de build, execução e teste
- Regras inegociáveis (tratamento de exceções, regras de formatação de código, padrões de segurança)
- Padrões que são explicitamente proibidos
- Como a equipe espera que as mudanças sejam feitas (branching, workflow de PR, etc.)

## 5.4. O que evitar (baixo valor ou arriscado)

- Segredos, credenciais ou chaves de API — nunca coloque isso no CLAUDE.md
- Regras de estilo já impostas por linters ou formatadores (ESLint, Prettier, Checkstyle)
- Grandes blocos de documentação que o Claude consegue consultar por conta própria
- Instruções em excesso — se o arquivo for muito longo, regras importantes se perdem no meio do ruído

## 5.5. Trate o CLAUDE.md como código

- Versione-o no Git para que toda a sua equipe possa contribuir
- Revise-o quando o Claude se comportar mal — a correção costuma estar no arquivo, não no prompt
- Pode-o regularmente — remova regras que não são mais relevantes
- Teste mudanças observando se o comportamento do Claude realmente muda
- Se o Claude continua ignorando uma regra — o arquivo provavelmente está longo demais e a regra está se perdendo
- Se o Claude continua perguntando coisas já respondidas no CLAUDE.md — a redação pode estar ambígua
- Use ênfase como "IMPORTANT" ou "YOU MUST" para regras críticas, a fim de melhorar a aderência
- O arquivo ganha valor com o tempo — quanto mais você o refina, melhor o Claude se sai

# 6. Configurações do Claude Code

As configurações do Claude Code existem para dar a desenvolvedores e organizações controle programático sobre o comportamento do Claude Code — o que ele tem permissão de fazer, do que é impedido, como interage com seu codebase e como se integra a ferramentas externas. Pense nisso como o "painel de controle" que fica entre as capacidades de IA do Claude e seu ambiente de desenvolvimento real.

## 6.1. Abordagem 1: O comando /config (UI interativa)

Esta é a forma mais amigável para iniciantes de controlar o Claude Code. Ao rodar `/config` dentro do REPL, abre-se uma interface de Configurações em abas direto no terminal — um balcão único para ver o status e alterar opções de configuração sem mexer em nenhum arquivo manualmente.

O `/config` funciona apenas no terminal (CLI). Na extensão do VSCode, ele não está disponível.

Alternativas para configurar no VSCode:

- Configurações nativas do VSCode — `Ctrl+,` → Extensions → Claude Code
- Editar diretamente o `~/.claude/settings.json` (compartilhado entre CLI e extensão)
- Digitar `/` no prompt do chat → selecionar "General Config" para abrir as configurações do VSCode

O `~/.claude/settings.json` é a forma mais universal — qualquer mudança feita lá vale tanto para o terminal quanto para a extensão do VSCode.

## 6.2. Abordagem 2: Arquivos settings.json (configuração persistente)

Referência: https://code.claude.com/docs/en/settings

Esta é a abordagem mais poderosa e mais "adequada" — arquivos JSON estruturados em diferentes escopos que persistem entre sessões. É aqui que você define sua configuração de fato. O arquivo `settings.json` é o mecanismo oficial para configurar o Claude Code por meio de configurações hierárquicas.

Os arquivos e seus escopos:

| Escopo  | Local                         | Propósito                                                                                                                                                                                                                            |
|---------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Managed | `managed-settings.json`       | Mantido dentro da pasta de instalação do Claude Code. Controlado por administradores de sistema. Aplica-se a todos na máquina. Não pode ser alterado pelos usuários. Frequentemente usado em ambientes corporativos. Pense nisso como regras de nível organizacional. |
| User    | `~/.claude/settings.json`     | Mantido dentro do diretório home do usuário. Aplica-se a todos os projetos em que você trabalha. Afeta só você. Não compartilhado com colegas. Ideal para preferências pessoais.                                                     |
| Project | `.claude/settings.json`       | Salvo dentro do diretório do projeto. Compartilhado com todos que trabalham nesse projeto. Geralmente commitado no Git. Útil quando equipes querem configurações consistentes.                                                       |
| Local   | `.claude/settings.local.json` | Salvo dentro do diretório do projeto. Existe apenas na sua máquina para um projeto específico. Não compartilhado. Automaticamente ignorado pelo Git. Perfeito para mudanças temporárias ou experimentais.                            |

### 6.2.1. Qual configuração prevalece? (Ordem de prioridade)

Quando a mesma configuração existe em vários níveis, a mais específica sempre vence. Por exemplo, se um recurso é permitido nas suas configurações pessoais, mas bloqueado nas de projeto, a regra de projeto será aplicada.

---

**Managed** — Prioridade mais alta — não pode ser sobreposta por nada

**Command Line Args** — Overrides temporários apenas para a sessão atual

**Local** — Suas regras pessoais para este repositório específico

**Project** — Regras compartilhadas pela equipe, commitadas no repositório

**User** — Prioridade mais baixa — seus padrões globais

### 6.2.2. Uma estrutura típica de settings.json

```json
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "permissions": {
    "allow": [
      "Bash(npm run lint)",
      "Bash(npm run test *)",
      "Read(~/.zshrc)"
    ],
    "deny": [
      "Bash(curl *)",
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)"
    ]
  },
  "env": {
    "CLAUDE_CODE_ENABLE_TELEMETRY": "1",
    "OTEL_METRICS_EXPORTER": "otlp"
  },
  "companyAnnouncements": [
    "🛡️ Never commit secrets, tokens, or credentials to the repository.",
    "📝 Write meaningful commit messages — future you will thank you."
  ]
}
```

# 7. /permissions

## 7.1. Permissões no Claude Code

Você pode gerenciar e revisar as permissões de ferramentas do Claude Code usando o comando `/permissions`. Esta interface exibe todas as regras de permissão junto com o arquivo `settings.json` onde elas estão definidas.

```
> /permissions

Permissions: Allow  Ask  Deny  Workspace  (←/→ or tab to cycle)

Claude Code won't ask before using allowed tools.

🔍 Search...

> 1. Add a new rule...
  2. Bash(find:*)

Press ↑↓ to navigate · Enter to select · Type to search · Esc to cancel
```

---

### 7.1.1. Definindo regras de permissão

As regras seguem um padrão simples: **Tool ou Tool(specifier)**

#### 7.1.1.1. Casar com tudo

```
Bash  →  permite todos os comandos bash
```

`Bash(*)` é equivalente a `Bash` e casa com todos os comandos Bash.

#### 7.1.1.2. Casar com algo específico

```
Bash(npm run build)         →  apenas este comando exato
Read(./.env)                →  apenas este arquivo específico
WebFetch(domain:github.com) →  apenas requisições para github.com
```

#### 7.1.1.3. Curingas para flexibilidade

```
Bash(npm run *)      →  qualquer comando npm run
Bash(git * main)     →  git checkout main, git merge main, etc.
```

#### 7.1.1.4. Um exemplo do mundo real

O Claude pode rodar testes, commitar código e checar versões — mas não pode fazer push para o remoto. Uma linha de config, imposta sempre.

```json
{
  "permissions": {
    "allow": [
      "Bash(npm run *)",
      "Bash(git commit *)",
      "Bash(* --version)"
    ],
    "deny": [
      "Bash(git push *)"
    ]
  }
}
```

# 8. /status

Mostra todas as fontes de configuração ativas e suas origens (managed, user, project). Esta é sua ferramenta de debug quando uma configuração não parece estar funcionando — ela diz exatamente qual camada está sobrepondo o quê.

Com esse comando dá para ver de qual arquivo/lugar estão sendo buscadas as configurações aplicadas à sessão atual.

# 9. /usage

Permite ver o uso consumido e o limite de uso para o dia/semana.

# 10. Output Style

Os output styles mudam a personalidade do Claude e como ele se comunica — sem afetar suas capacidades centrais. Usando o comando `/config` → `Output-style`, podemos controlar essa configuração.

```
> /config
-> Output-style

Preferred output style

This changes how Claude Code communicates with you

> 1. Default ✓   Claude completes coding tasks efficiently and provides concise responses
  2. Explanatory  Claude explains its implementation choices and codebase patterns
  3. Learning     Claude pauses and asks you to write small pieces of code for hands-on practice

Enter to confirm · Esc to cancel
```

---

| Estilo      | Comportamento                                                | Melhor para                                            |
|-------------|--------------------------------------------------------------|--------------------------------------------------------|
| Default     | Conciso, eficiente, explicações mínimas                       | Desenvolvedores experientes que querem velocidade      |
| Explanatory | Adiciona blocos "Insight" explicando por que fez certas escolhas | Entender codebases novos, aprender padrões         |
| Learning    | Deixa marcadores `TODO(human)` para você implementar pequenos trechos | Devs juniores, aprender novas linguagens, programação em par |

## 10.1. Crie um Output Style personalizado no Claude Code

### 10.1.1. O que é um Output Style personalizado?

Um output style personalizado permite controlar como o Claude responde. Você define instruções em um pequeno arquivo Markdown. Essas instruções são adicionadas automaticamente ao system prompt do Claude. Isso ajuda a manter as respostas consistentes entre sessões.

### 10.1.2. Estrutura de um Output Style personalizado

Um arquivo de estilo usa frontmatter no topo (envolto em `---`) seguido das suas instruções.

**Frontmatter** — Contém o nome e a descrição do seu estilo. É como o rótulo de um pote — diz o que tem dentro sem precisar abrir.

**Corpo (Body)** — Contém as regras e comportamentos de fato que você quer que o Claude siga. É aqui que você escreve suas instruções personalizadas em Markdown.

Abaixo, um arquivo de Output Style personalizado simples... adote esse formato nos seus arquivos de output style para que funcionem corretamente:

```
---
name: Custom
description: A short summary of what this style does, shown to the user
---

# Custom Style Instructions

You are an interactive CLI tool that helps users with software engineering tasks.

## Specific Behaviors

- Always explain in beginner-friendly language
- Focus on backend development
```

### 10.1.3. Onde salvar seus arquivos de estilo

Você pode salvar seus arquivos de estilo em dois locais:

**Nível de usuário** → `~/.claude/output-styles/`
Isso aplica o estilo em todos os seus projetos. É como uma configuração global no seu celular — funciona em todo lugar.

**Nível de projeto** → `.claude/output-styles/`
Isso aplica o estilo apenas a um projeto específico. É como uma regra que só vale dentro de uma sala de aula.

### 10.1.4. Casos de uso práticos

**Concise Reviewer** — Um estilo que diz ao Claude para dar comentários de revisão de código curtos e diretos, sem explicação extra.

**Beginner-Friendly Helper** — Um estilo em que o Claude explica tudo passo a passo usando palavras simples e analogias.

**Strict Linter** — Um estilo em que o Claude só aponta problemas de código e sugere correções, sem nenhuma conversa casual.

# 11. /effort

Define o nível de esforço para `??`.
(`max` (apenas esta sessão): Capacidade máxima com o raciocínio mais profundo)

# 12. Statelessness e a ilusão da conversa contínua

O Claude é stateless: cada requisição é independente, sem memória entre chamadas. O modelo em si não "lembra" da conversa anterior.

Para simular continuidade, a cada nova pergunta o cliente (Claude Code, app, API) reenvia toda a janela de contexto — system prompt, mensagens anteriores, respostas, resultados de ferramentas, arquivos lidos — junto com a nova pergunta.

Consequências práticas:

- O custo cresce com a conversa: cada turno reprocessa tudo que veio antes (daí o prompt caching, que reaproveita prefixos já vistos).
- O limite de contexto é finito: quando enche, partes antigas são resumidas ou descartadas.
- Sem "estado oculto": tudo que o modelo sabe sobre a conversa precisa estar visível nos tokens enviados — por isso existem mecanismos externos como arquivos de memória, CLAUDE.md e ferramentas para "lembrar" entre sessões.

Em resumo: a ilusão de diálogo contínuo é construída por reenvio, não por persistência interna do modelo.

# 13. /context

Mostra o que está usando espaço na janela de contexto no momento. Ajuda a entender por que o contexto enche rápido.

> *Resposta do Claude: Um contexto grande significa mais tokens para processar e menor eficiência — use sessões novas para manter velocidade e precisão.*

## 13.1. O que acontece quando o contexto enche?

- O Claude gerencia o espaço automaticamente.
- Primeiro, ele remove saídas de ferramentas mais antigas.
- Se precisar de mais espaço, ele resume partes da conversa usando o processo de compactação.
- Coisas importantes, como seus pedidos e trechos de código-chave, normalmente são mantidas.
- Instruções muito antigas ou detalhadas podem ser encurtadas ou perdidas.

# 14. /compact

Você pode orientar o Claude durante a compactação:

- Adicione uma seção "Compact Instructions" dentro do CLAUDE.md.
- Ou rode um comando como:

  ```
  /compact "make sure to retain security related instructions"
  ```

Isso diz ao Claude qual informação é mais importante manter.

Sempre use o CLAUDE.md para regras importantes. Não dependa apenas do histórico do chat para instruções de longo prazo. Isso garante que regras importantes permaneçam disponíveis mesmo após a compactação ou entre sessões.

Exemplos de regras persistentes: padrões de código, estrutura de pastas, convenções de nomeação e decisões de arquitetura.

# 15. /clear

Limpa os tokens da janela de contexto (`/context`) = limpa a memória de tokens para a sessão atual.

Qual a diferença entre `/clear` e começar uma sessão nova? R: Usando `/clear` preservamos as permissões fornecidas e os MCPs.

# 16. /rename

Atribui um nome à sessão atual. Ela poderá ser recarregada depois com o comando abaixo (ou, por exemplo, via CLI: `claude --resume teste-nome`).

## 16.1. Dúvida #01

Vamos supor que eu converse 300 kB de conversa contigo numa sessão. Então, chegado esse ponto, eu rodo o `/rename um-nome-de-sessao`, e continuamos conversando. Quando eu executar o `/resume um-nome-de-sessao`, vai trazer todos os 300 kB iniciais + o que conversamos depois, ou só o que conversamos depois?

R: O `/rename` apenas troca o rótulo da sessão — não corta, não bifurca, não cria uma nova sessão. A transcrição continua sendo um único arquivo JSONL contínuo no disco. Então, quando você executar `/resume um-nome-de-sessao`, virá tudo: os 300 kB iniciais + tudo que foi conversado depois do rename. O nome é só um identificador amigável para você encontrar a sessão na lista do `/resume`.

# 17. /resume

Apresenta o histórico de sessões para que você possa recarregar uma delas. (Obs.: ver comando acima: `/rename`.)

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

---

Quando você executa:

```bash
cd /home/voce/meu-app
claude
/resume
```

aparecem só as sessões **dessa pasta**. Se você estivesse em `/home/voce/outro-projeto`, não veria essas sessões.

# 18. claude --continue --fork-session

(Ver `/resume` acima.)

**Bifurque uma sessão (experimente um caminho diferente)**

E se você quiser experimentar uma abordagem diferente — sem bagunçar sua sessão atual? É isso que o fork faz.

```
claude --continue --fork-session
```

Isso cria uma nova sessão, mas copia todo o seu histórico de conversa até aquele ponto. A sessão original permanece intocada. É como fotocopiar seu caderno e escrever na cópia. A original permanece limpa. O fork segue em sua própria direção. Assim como o resume, sessões bifurcadas também não herdam permissões com escopo de sessão.

## 18.1. Como o Claude Code gerencia sessões entre branches do Git

Cada conversa do Claude Code é uma sessão atrelada ao seu diretório atual — não a uma branch ou a um arquivo.

- Toda conversa que você inicia no Claude Code está ligada à pasta em que você está trabalhando
- Quando você retoma uma sessão, o Claude só mostra as sessões daquele mesmo diretório
- Trocar de branch não inicia uma nova sessão — você permanece na mesma conversa

O Claude sempre lê os arquivos da sua branch Git ativa. Se você trocar de branch, ele imediatamente passa a trabalhar com o código da nova branch, enquanto seu histórico de conversa permanece inalterado. Isso significa que o Claude ainda lembra de tudo que vocês discutiram antes, mesmo que os arquivos subjacentes sejam diferentes.

Como as sessões são baseadas em diretório, você pode rodar várias sessões do Claude em paralelo usando Git worktrees. Worktrees criam pastas separadas para diferentes branches, permitindo que cada branch tenha sua própria sessão independente do Claude.

# 19. /rewind (= desfazer)

Ou pressione `Esc` duas vezes, quando o atalho estiver disponível. O rewind permite voltar a um ponto anterior e escolher o que fazer.

Obs.: temos essa funcionalidade disponível mesmo quando saímos do aplicativo e voltamos depois para a sessão em questão.

## 19.1. Como fazer rewind

Pressione `Esc` duas vezes ou use o comando `/rewind` para abrir o menu de rewind. Você então escolhe um checkpoint e decide o que restaurar:

- **Restore Code Only** — Reverte alterações nos arquivos, mantém a conversa. Bom quando o código deu errado mas o contexto ainda é útil.
- **Restore Conversation Only** — Volta o chat, mantém o código. Bom quando você quer re-promptar de forma diferente sem descartar alterações que gostou.
- **Restore Both** — Reset completo. Código e conversa voltam juntos.
- **Summarize from here** — Não restaura nada. Em vez disso, condensa as mensagens a partir daquele ponto enquanto mantém o contexto anterior intacto — uma alternativa cirúrgica ao `/compact` que comprime apenas a parte que está consumindo espaço.

## 19.2. O que os checkpoints NÃO rastreiam

Isso é crítico de entender: o checkpointing não rastreia arquivos modificados por comandos bash. Se o Claude executar `rm file.txt`, `mv old.txt new.txt` ou `cp source.txt dest.txt` — essas modificações não podem ser desfeitas via rewind. Apenas edições diretas feitas pelas ferramentas de edição de arquivos do Claude são rastreadas.

Além disso, alterações manuais feitas fora do Claude Code não são capturadas, e os checkpoints expiram após 30 dias.

# 20. Histórico

Dentro de:

```
~/.claude/projects
```

ficam todos os históricos das conversas/sessões em formato `.jsonl`. Daria para procurar algo com `grep` na pasta.

Obs.: após 20 dias, cada sessão individual é deletada.

# 21. Os hábitos de sessão do desenvolvedor esperto

**Hábito 1: Limpe entre tarefas**
Terminou de corrigir um bug? Prestes a começar uma nova feature? Rode `/clear` primeiro. Não deixe a conversa de correção de bug poluir seu trabalho na feature. Cada token sobrando é contexto desperdiçado.

**Hábito 2: Compacte em pontos de quebra naturais**
Não espere o autocompact entrar em ação com 80–85% de uso. Rode `/compact` quando VOCÊ decidir — depois de terminar uma subtarefa, antes de começar uma nova fase. Você pode até dar instruções: `/compact Keep only the test results and the current implementation plan`.

**Hábito 3: Nomeie suas sessões**
Digite `/rename payment-gateway-fix` assim que começar um trabalho significativo. O você do futuro vai agradecer ao você do presente quando estiver encarando uma lista de 50 sessões sem nome.

**Hábito 4: Monitore seu contexto**
Rode `/context` periodicamente. Pense nisso como checar o marcador de combustível do seu carro. Se você estiver acima de 60% e ainda tiver muito trabalho pela frente, compacte ou limpe. Você também pode configurar uma status line personalizada para sempre mostrar o uso de contexto na barra inferior.

**Hábito 5: Use o padrão Documentar & Limpar**
Para tarefas realmente grandes, peça ao Claude para escrever seu plano e progresso em um arquivo `.md`, depois `/clear`, e então comece uma nova sessão dizendo ao Claude para ler esse arquivo e continuar. Isso te dá contexto fresco com conhecimento preservado.

# 22. Memory (Memória)

## 22.1. /memory

Mostra os arquivos/pastas de configuração (ex.: CLAUDE.md, rules, ...) que estão sendo considerados no contexto atual.

## 22.2. Auto Memory no Claude Code

Imagine isto: você está trabalhando com o Claude Code no seu projeto React. Você passa 20 minutos explicando que seu projeto usa Vite, que seus testes ficam em `src/__tests__/`, que você prefere named exports a default exports, e que o servidor de dev roda na porta 5173. O Claude te ajuda lindamente.

No dia seguinte, você abre uma nova sessão... e o Claude não tem nenhuma memória de ontem. É como conversar com um colega brilhante que tem amnésia toda noite. Você está de volta à estaca zero — reexplicando as mesmas coisas de novo.

É esse o problema que o Auto Memory resolve.

Com o Auto Memory, o Claude Code silenciosamente faz anotações para si mesmo enquanto trabalha com você. Comandos de build, truques de debugging, suas preferências de estilo de código, decisões de arquitetura — ele escreve tudo isso em segundo plano. Na próxima sessão? O Claude já conhece seu projeto. Você continua exatamente de onde parou, como continuar uma conversa com um colega que realmente lembra.

|                          | CLAUDE.md                  | Auto Memory (MEMORY.md)         |
|--------------------------|----------------------------|---------------------------------|
| **Quem escreve?**        | Você (o desenvolvedor)     | O Claude (automaticamente)      |
| **O que tem nele?**      | Regras & instruções        | Aprendizados & observações      |
| **Compartilhado com a equipe?** | Sim (via Git)       | Não (local da máquina)          |
| **Analogia**             | Um livro-texto para alunos | O caderno pessoal de um aluno   |

### 22.2.1. Dois sistemas de memória: o livro-texto vs. o caderno

O Claude Code tem dois sistemas de memória complementares. Entender a diferença é a chave para usá-los bem.

#### 22.2.1.1. CLAUDE.md — O livro-texto (escrito por VOCÊ)

Pense no `CLAUDE.md` como um livro-texto que você escreve para o Claude. Ele contém suas regras, suas convenções, suas instruções de "faça desse jeito":

- "Use pnpm, não npm"
- "Siga o Airbnb React Style Guide"
- "Nunca modifique arquivos em /generated/ ou /dist/"
- "Rode testes com pnpm test --coverage"

Você o escreve, você o commita no Git, sua equipe toda compartilha.

#### 22.2.1.2. Auto Memory (MEMORY.md) — O caderno (escrito pelo CLAUDE)

O Auto Memory é como o caderno pessoal de um aluno. O Claude o escreve para si mesmo enquanto trabalha com você:

- "O comando de build deste projeto é pnpm build"
- "O hydration mismatch foi causado por usar o objeto window durante o SSR sem um guard com useEffect"
- "O usuário prefere custom hooks a render props para lógica compartilhada"
- "Os testes E2E usam Playwright e exigem o servidor de dev rodando na porta 5173"

Ele é armazenado localmente na sua máquina, nunca commitado no Git, e é único para o seu fluxo de trabalho pessoal.

### 22.2.2. Como o Auto Memory funciona por baixo dos panos

**Está LIGADO por padrão.** O Auto Memory vem habilitado por padrão. Você não precisa instalar nada nem acionar nenhum botão. O Claude simplesmente começa a lembrar.

### 22.2.3. Onde o Claude armazena suas anotações?

Cada projeto ganha seu próprio diretório de memória:

```
~/.claude/projects/<project>/memory/
├── MEMORY.md            # O índice principal — carregado a cada sessão
├── debugging.md         # Notas detalhadas sobre padrões de debugging
└── api-conventions.md   # Decisões de design de API
```

O caminho `<project>` é derivado do seu repositório git. Então, todas as branches, worktrees e subdiretórios dentro do mesmo repo compartilham um único diretório de memória. Pense nisso como um caderno por projeto, não por branch. Fora de um repo git? O Claude usa o diretório raiz do projeto em vez disso.

#### 22.2.3.1. Mensagens de status

Quando o Claude está interagindo com sua memória, você verá mensagens de status na interface do Claude Code:

- "Writing memory" — O Claude está salvando algo que aprendeu
- "Recalled memory" — O Claude está lendo de suas anotações salvas

Essas são suas pistas visuais de que o Auto Memory está funcionando em segundo plano.

## 22.3. O comando /memory

O comando `/memory` é seu painel de controle para tudo relacionado a memória no Claude Code. Digite-o dentro de qualquer sessão. Isso abre um seletor interativo que te mostra:

- Todos os arquivos `CLAUDE.md` atualmente carregados na sua sessão (project, user, rules, etc.)
- O toggle do Auto Memory — interruptor LIGA/DESLIGA
- Um link para abrir a pasta do auto memory — para você navegar pelo que o Claude salvou

Você também pode usar `/memory` para:

- Ligar ou desligar o auto memory
- Abrir qualquer arquivo de memória no seu editor
- Navegar pelas anotações salvas do Claude

### 22.3.1. Dizendo ao Claude o que lembrar

O Auto Memory não depende apenas do julgamento do próprio Claude. Você pode dizer ao Claude para lembrar de coisas explicitamente:

- "remember that we use pnpm, not npm"
- "save to memory that the API tests require a local Redis instance"
- "note that the staging environment uses port 3001"

## 22.4. As três camadas de memória — o quadro completo

O Claude Code, na verdade, tem três sistemas de memória que trabalham juntos. Pense nisso como uma hierarquia:

**Camada 1: Arquivos CLAUDE.md (suas instruções)**
*Analogia: O manual da empresa que todo funcionário deve seguir*
- Escrito por você
- Carregado no início de toda sessão
- Compartilhado com a equipe via Git

**Camada 2: Auto Memory / MEMORY.md (os aprendizados do Claude)**
*Analogia: Os post-its pessoais de um desenvolvedor no monitor*
- Escrito pelo Claude automaticamente
- As primeiras 200 linhas são carregadas no início da sessão; arquivos de tópico são lidos sob demanda
- Local da máquina, NÃO compartilhado

**Camada 3: Session Memory (continuidade da conversa)**
*Analogia: O contexto da "última conversa", como lembrar onde você parou numa reunião*
- Salva resumos em nível de conversa
- Ajuda na recuperação entre sessões dentro de conversas recentes

A configuração mais forte usa as três. O `CLAUDE.md` fornece regras autoritativas. O Auto Memory captura o que o Claude aprende enquanto trabalha. A Session Memory mantém a continuidade de conversas recentes.

## 22.5. Configurando o Auto Memory

### 22.5.1. Como alternar (toggle)

**Toggle via /memory** — A forma mais simples: abra uma sessão, digite `/memory` e acione o toggle.

**Toggle via Settings** — Nas configurações do seu projeto (`.claude/settings.json`):

```json
{
  "autoMemoryEnabled": false
}
```

**Desabilitar via variável de ambiente** — Perfeito para pipelines de CI/CD onde você não quer que o Claude acumule anotações sobre seu ambiente de build:

```bash
export CLAUDE_CODE_DISABLE_AUTO_MEMORY=1
```

### 22.5.2. Diretório de memória personalizado

Quer armazenar o auto memory em outro lugar? Defina `autoMemoryDirectory` nas suas configurações de usuário ou locais:

```json
{
  "autoMemoryDirectory": "/path/to/custom/memory"
}
```

### 22.5.3. Como funciona

Apenas as primeiras 200 linhas do `MEMORY.md` são carregadas no início de cada conversa. Qualquer coisa além disso é ignorada na inicialização. Para manter as coisas eficientes, o Claude desloca informações detalhadas para arquivos separados por tópico.

Esse limite de 200 linhas se aplica apenas ao `MEMORY.md`. Arquivos como o `CLAUDE.md` são sempre carregados, independentemente do tamanho — embora mantê-los mais curtos ajude a melhorar a precisão e a consistência.

Arquivos específicos de tópico (ex.: `debugging.md`, `patterns.md`) não são carregados por padrão. O Claude os acessa apenas quando necessário, usando suas capacidades de leitura de arquivos.

Durante uma sessão, o Claude pode ler e escrever em arquivos de memória. Quando você vê mensagens como "Writing memory" ou "Recalled memory", significa que o Claude está interagindo ativamente com arquivos localizados em `~/.claude/projects/<project>/memory/`.

# 23. Rules (Regras)

(Obs.: operação útil para essa funcionalidade: `/memory`, citado acima.)

## 23.1. Rules no Claude Code

Imagine que seu `CLAUDE.md` cresceu para 400 linhas. Ele tem regras de React, diretrizes de API, avisos de migração de banco de dados, políticas de segurança e convenções de teste — tudo misturado. Quando o Claude está editando um componente React, ele também carrega no contexto suas regras de segurança de migração de banco. Quando está escrevendo uma query SQL, carrega seus padrões de React.

Isso é o que um desenvolvedor chamou de "saturação de prioridade" — quando tudo é alta prioridade, nada é. A atenção do Claude se dilui em instruções que não se aplicam à tarefa atual.

## 23.2. Onde as Rules vivem?

```
.claude/rules/
├── code-style.md      ← Sempre carregada (sem filtro de path)
├── testing.md         ← Sempre carregada
├── security.md        ← Sempre carregada
├── api-rules.md       ← Apenas ao trabalhar em arquivos de API
├── react-rules.md     ← Apenas ao trabalhar em arquivos React
└── database/
    ├── migrations.md  ← Apenas ao trabalhar em arquivos de migração
    └── queries.md     ← Apenas ao trabalhar em arquivos SQL/query
```

Você também pode ter regras pessoais em `~/.claude/rules/`, que se aplicam a todos os seus projetos.

## 23.3. Dois tipos de regras

### 23.3.1. Regras sempre carregadas (always-loaded)

Sem frontmatter `paths`. Elas carregam na inicialização com a mesma alta prioridade do `CLAUDE.md`. Use-as para regras que se aplicam universalmente.

```markdown
# code-style.md (sem frontmatter = sempre carregada)

- Use English for all comments
- Prefer a functional approach where possible
- Use strict typing everywhere
```

### 23.3.2. Regras com escopo de path (path-scoped)

Com frontmatter `paths`. Elas carregam sob demanda apenas quando o Claude lê arquivos que casam com os padrões glob especificados.

```markdown
---
paths:
  - "src/api/**/*.ts"
  - "src/handlers/**/*.ts"
---

# API Design Rules
- Return consistent error shapes: { error: string, code: number }
- Log all requests with correlation IDs
- Rate limit headers on all routes
```

Esta regra só é ativada quando o Claude trabalha em arquivos que casam com esses paths.

### 23.3.3. Rules vs CLAUDE.md — quando usar qual

| Coloque no CLAUDE.md                       | Coloque nas Rules                                       |
|--------------------------------------------|--------------------------------------------------------|
| Visão geral do projeto / stack tecnológica | Padrões de código específicos por tipo de arquivo      |
| Comandos de build e teste                  | Diretrizes específicas de framework (React, Spring, etc.) |
| Visão geral da arquitetura                 | Regras de segurança para diretórios sensíveis          |
| Convenções universais de código            | Convenções de escrita de testes                        |
| Pegadinhas comuns que afetam tudo          | Regras de segurança de migração                        |
| Workflow Git / estratégia de branching     | Diretrizes de design de API                            |

# 24. Skills

São semelhantes a aplicativos do celular: apenas instruções básicas ficam na memória constantemente (como os ícones dos apps do celular aparecem), e todo o resto só é executado quando chamado.

Você pode criar suas próprias skills reutilizáveis adicionando arquivos Markdown em `.claude/skills/` (nível de projeto) ou `~/.claude/skills/` (pessoal).

Por exemplo, se você criar uma skill com o nome **analyze-issue \<issue #\>**, ao digitar **/analyze-issue 123** → o Claude se comportará com base nas instruções definidas no documento da skill. Por exemplo, ele vai:

- Buscar a issue #123 do seu repositório do GitHub
- Explorar o codebase relevante
- Gerar uma especificação técnica completa

## 24.1. Construa sua própria skill

### 24.1.1. Passos para criar uma skill personalizada

#### 24.1.1.1. 1) Crie o diretório da skill

Crie um diretório para a skill em `.claude/skills/analyze-issue` (nível de projeto) ou `~/.claude/skills/analyze-issue` (pessoal).

```
mkdir -p .claude/skills/analyze-issue
```

#### 24.1.1.2. 2) Escreva um arquivo SKILL.md

Toda skill requer um arquivo SKILL.md. Este arquivo tem duas seções principais:

i) Frontmatter YAML (colocado entre linhas `---`)
- Define quando e como o Claude deve usar a skill.
- O campo `name` se torna o `/comando-de-barra`.
- A `description` ajuda o Claude a entender quando carregar a skill automaticamente.

ii) Instruções em Markdown

Contém os passos e a orientação que o Claude deve seguir quando a skill roda. Por exemplo, você pode criar um arquivo de skill em `.claude/skills/analyze-issue/SKILL.md`. Esse arquivo diz ao Claude como executar a skill analyze-issue e quando ela deve ser acionada.

#### 24.1.1.3. 3) Teste a skill

Você pode testar sua skill de duas formas diferentes:

i) Deixe o Claude usá-la automaticamente

Faça uma pergunta que case com a descrição da skill, por exemplo: `Analyze the issue 123`. Se o pedido se encaixar na skill, o Claude a carregará e usará automaticamente.

ii) Rode a skill manualmente

Você também pode acionar a skill diretamente usando seu comando de barra: `/analyze-issue 123`. Isso força o Claude a executar a skill específica que você criou.

Independentemente de como a skill é acionada, o Claude Code seguirá as instruções dentro do arquivo SKILL.md — por exemplo, ele analisa a issue 123 e gera uma especificação sobre as correções propostas.

Mais detalhes podem ser encontrados em https://code.claude.com/docs/en/skills

## 24.2. Site de referência: https://code.claude.com/docs/en/skills (tem informações importantes)

Vale ver para aprofundar. Ver exemplos salvos na pasta `./skills` deste diretório.

## 24.3. `./skills/feature-guide`: exemplo de como rodar uma skill em um sub-agente

A linha abaixo:

```
context: fork
```

especifica que a skill deve rodar em isolamento. (O subagente não tem acesso ao conteúdo da conversa principal.)

Mais detalhes em: https://code.claude.com/docs/en/skills#example-research-skill-using-explore-agent

# 25. commands (deprecado)

**O que é um Command?**

Um command é simplesmente um arquivo Markdown contendo instruções em linguagem natural. Você o salva em um diretório especial, e o Claude Code o reconhece automaticamente como um comando de barra. O nome do arquivo (sem o `.md`) se torna o nome do comando.

```
.claude/commands/review.md  →  /review
.claude/commands/commit.md  →  /commit
.claude/commands/deploy.md  →  /deploy
```

É isso. Sem compilação de código, sem registro, sem arquivo de configuração para editar. Solte um arquivo markdown na pasta certa e você tem um comando.

---

**A evolução**

As skills são a próxima geração dos commands. Enquanto os commands sempre foram iniciados pelo usuário (você digita explicitamente `/command`), as skills introduzem um conceito fundamentalmente diferente — o Claude pode descobri-las e invocá-las automaticamente quando a tarefa casa com a descrição da skill.

Diferentemente dos commands (arquivos markdown únicos), uma skill é um diretório com o SKILL.md como ponto de entrada, mais arquivos de apoio opcionais.

# 26. hooks

Você já disse a alguém: "Por favor, certifique-se de trancar a porta ao sair"? A pessoa diz: "Claro, vou trancar." E na maioria dos dias, ela tranca. Mas naquele um dia, ela esquece. Agora imagine que, em vez de depender da memória dela, você instalou uma trava automática — a porta se tranca sozinha no momento em que se fecha. Sem lembrar, sem esquecer, sem torcer. Simplesmente funciona.

Essa é a diferença entre dar ao Claude Code uma instrução — e dar a ele um hook.

## 26.1. O que exatamente são hooks?

Em termos simples, hooks são comandos/scripts de shell definidos pelo usuário que rodam automaticamente em pontos específicos do ciclo de vida do Claude Code. Pense em hooks como event listeners no JavaScript — você registra um comando, e ele dispara quando um evento específico acontece.

Você define as regras, e o Claude Code as impõe — não porque a IA escolheu, mas porque o sistema está programado para executá-las. Toda vez, sem exceção.

## 26.2. Determinístico

E esta é a palavra crítica que quero que você lembre ao longo desta seção — **determinístico**. Quando você escreve algo no CLAUDE.md ou diz ao Claude "Sempre rode o formatador após editar", isso é uma sugestão. **A IA pode segui-la. Provavelmente vai. Mas não há garantia.**

Os hooks invertem isso completamente. Eles não são sugestões — são código. Eles executam com certeza, assim como um pipeline de CI roda a cada commit, lembre-se o desenvolvedor ou não.

## 26.3. Agora, qual o propósito? Por que os hooks existem?

Pense em três coisas que você gostaria de garantir ao trabalhar com um agente de codificação de IA.

### 26.3.1. Primeiro — automação
Você quer que certas ações aconteçam toda vez, como formatar o código após cada edição.

### 26.3.2. Segundo — proteção
Você quer bloquear certas ações por completo, como impedir edições nos seus arquivos de config de produção ou no seu `.env` com segredos.

### 26.3.3. Terceiro — consciência (awareness)
Você quer saber o que está acontecendo, como receber uma notificação no desktop no momento em que o Claude termina uma tarefa e está esperando seu input.

## 26.4. Sem hooks, todas as três dependem do julgamento da IA.

Com hooks, elas dependem do seu código. E código não esquece. Código não fica criativo com suas regras. Código simplesmente roda.

Então, resumindo — hooks são a ponte entre torcer para que o Claude faça a coisa certa e garantir isso. Eles transformam suas preferências em regras imponíveis.

## 26.5. O ponto de dor sem hooks

Você está trabalhando com o Claude Code. Ele acabou de editar cinco arquivos para você — brilhante. Mas agora a formatação do seu código está toda bagunçada. O Prettier não rodou. Você corrige manualmente. Da próxima vez, a mesma coisa acontece. Você pensa: "Eu queria que o Claude simplesmente rodasse o Prettier toda vez que edita um arquivo." Mas o detalhe é — o Claude é uma IA. Ele pode rodar o Prettier. Pode esquecer. Não há garantia.

Ou aqui vai outro cenário. Você tem um arquivo `.env` com segredos — chaves de API, senhas de banco de dados. Você disse ao Claude: "Não toque nesse arquivo." Mas e se ele tocar? E se, no meio de uma sessão longa, ele decidir "consertar" prestativamente seu `.env`? Você não teria uma rede de segurança.

E mais uma. O Claude termina uma tarefa, e você está fazendo café, sem olhar o terminal. Cinco minutos se passam antes de você perceber que ele está parado ali, esperando por você. Não seria bom receber uma notificação — como um toque no ombro — dizendo "Ei, terminei, volte aqui"?

Todos os três problemas têm uma coisa em comum: você está torcendo para que a IA faça a coisa certa em vez de garantir isso.

## 26.6. Onde os hooks são armazenados?

Os hooks são armazenados principalmente como configuração JSON nos seguintes locais:

- User Settings (`~/.claude/settings.json`) — Aplica-se a TODOS os projetos
- Project Settings (`.claude/settings.json`) — Aplica-se apenas àquele projeto específico
- Local settings (`.claude/settings.local.json`) — Não compartilhável e aplicado a um único projeto

## 26.7. Criando um hook

A forma mais rápida de criar um hook é pelo menu interativo `/hooks` no Claude Code. Siga os passos abaixo:

1. Abra o menu de hooks digitando `/hooks`
2. Configure o matcher
3. Selecione "+ Add new hook" e forneça seu comando de shell
4. Escolha um local de armazenamento (nível de projeto/usuário)

## 26.8. Estrutura de configuração de hook

```
{
  "hooks": {
    "<EventName>": [
      {
        "matcher": "<ToolName or Pattern>",
        "hooks": [
          {
            "type": "command",
            "command": "<shell command to execute>"
          }
        ]
      }
    ]
  }
}
```

Cada hook inclui um **type** que define como ele deve ser executado. A maioria dos hooks usa `"type": "command"`, que simplesmente roda um comando dado. Outros valores válidos incluem `"http"`, `"prompt"`, `"agent"`.

## 26.9. Configure seu primeiro hook

Em https://code.claude.com/docs/en/hooks-guide, veja "Set up your first hook".

## 26.10. Observação

Os hooks rodam isolados externamente, a custo zero, a menos que o hook retorne contexto adicional.

## 26.11. Como os hooks funcionam

Os hooks são acionados em certos pontos do fluxo de trabalho do Claude Code.

Quando um desses eventos ocorre, todos os hooks que casam com aquele evento rodam ao mesmo tempo (em paralelo). Se vários hooks contiverem o mesmo comando, o Claude Code remove automaticamente as duplicatas, de modo que o comando rode apenas uma vez.

A tabela abaixo lista os eventos comuns e explica quando cada um é acionado.

| Nome do evento       | Quando é acionado?                                                                                |
|----------------------|--------------------------------------------------------------------------------------------------|
| SessionStart         | Acionado quando uma sessão do Claude Code inicia ou é retomada                                    |
| UserPromptSubmit     | Acionado quando um usuário envia um prompt, antes de o Claude começar a processá-lo               |
| PreToolUse           | Roda antes de o Claude executar uma chamada de ferramenta. Este hook também pode bloquear a execução da ferramenta, se necessário |
| PermissionRequest    | Acionado quando o Claude exibe um diálogo de pedido de permissão                                  |
| PostToolUse          | Roda depois que uma chamada de ferramenta é concluída com sucesso                                 |
| PostToolUseFailure   | Roda quando uma chamada de ferramenta falha                                                       |
| Notification         | Acionado quando o Claude Code envia uma notificação                                               |
| SubagentStart        | Roda quando um subagente é criado                                                                 |
| SubagentStop         | Roda quando um subagente conclui sua tarefa                                                       |
| Stop                 | Acionado quando o Claude termina de gerar sua resposta                                            |
| TeammateIdle         | Roda quando um membro da equipe de agentes está prestes a ficar ocioso                            |
| TaskCompleted        | Acionado quando uma tarefa é marcada como concluída                                               |
| ConfigChange         | Roda quando um arquivo de configuração é modificado durante uma sessão                            |
| WorktreeCreate       | Acionado quando um Git worktree é criado usando `--worktree` ou configurações de isolamento       |
| WorktreeRemove       | Roda quando um worktree é removido, seja quando uma sessão termina ou quando um subagente finaliza |
| PreCompact           | Acionado antes de o Claude realizar a compactação de contexto                                     |
| SessionEnd           | Roda quando a sessão do Claude Code termina                                                       |

## 26.12. IMPORTANTE

O que citei aqui é apenas o mais geral do curso. Mais detalhes em: https://code.claude.com/docs/en/hooks-guide

# 27. MCP

## 27.1. /mcp

Apresenta a lista de servidores MCP instalados. Apresenta também se está estabelecida uma conexão. Apresenta também quais operações o MCP consegue operar com o servidor.

## 27.2. Site de referência (IMPORTANTE VER)

https://code.claude.com/docs/en/mcp

## 27.3. Exemplos de prompts que podem ser usados com Playwright (alguns com Google Chrome)

- "A user reported that clicking 'Add to Cart' on the product page sometimes shows a 500 error. Go to localhost:5173/products/123, click Add to Cart 10 times, capture network requests and console errors, and tell me what's actually happening."

- "Navigate through the main user flows of my app at localhost:5173 (signup, login, dashboard, settings). Collect every console error and warning. Then look at the source code and propose fixes for each one, ranked by severity."

- "Take screenshots of every page in my app at 1920x1080, 768x768, and 375x667. Compare against the screenshots in ./baseline/. Tell me which pages have visual regressions and what changed."

- "Walk through my checkout flow at localhost:5173 as a real user would. Record what you do, then generate a Playwright test file that covers this flow with proper assertions and waits. Save it to tests/e2e/checkout.spec.ts."

- "The tests in tests/e2e/login.spec.ts are failing. Run them, use the browser to inspect the actual current DOM at localhost:5173/login, figure out whether the test is wrong or the app is broken, and fix whichever side is actually broken."

- "Crawl every page linked from my homepage at localhost:5173 (up to 2 levels deep). For each page, capture: page title, meta description, H1, word count, broken links, and load time. Give me a table sorted by problems found."

- "Test the signup form at localhost:5173/signup with these edge cases: empty fields, SQL injection strings, extremely long inputs, unicode/emoji, passwords that don't match, already-taken emails. For each, report what happened and whether the app handled it gracefully. Fix any issues you find in the validation logic."

- "Walk through the first-time user onboarding at localhost:5173. Screenshot each step, document what the user sees and does, and produce a getting-started guide with screenshots in docs/getting-started.md."

**Sobre o MCP do Chrome DevTools**

Depende do prompt — alguns você consegue, outros não. Aqui está a distinção prática:

**O que o Chrome DevTools MCP cobre bem:**
- Capturar console errors/warnings
- Inspecionar o DOM atual
- Monitorar network requests
- Tirar screenshots
- Avaliar JavaScript na página

Então prompts como o 1º (capturar erros de rede), o 2º (coletar console errors), o 5º (inspecionar DOM) e partes do 6º (load time, título, H1) funcionam bem com ele.

**O que ele *não* faz que o Playwright faz:**
- **Automação de fluxo** — clicar, preencher formulários, navegar em sequência como um usuário real (prompts 1, 3, 4, 7, 8)
- **Screenshots multi-viewport** — redimensionar para 768px, 375px, etc. (prompt 3)
- **Gerar arquivos de teste** `.spec.ts` (prompt 4)
- **Crawling em profundidade** — seguir links automaticamente (prompt 6)
- **Edge case testing** em formulários (prompt 7)

**Resumo:** o Chrome DevTools MCP é ótimo para *observação e inspeção*, mas não para *automação e interação*. Para os prompts da lista, você precisaria do Playwright MCP (ou similar) para os cenários que envolvem agir na página como um usuário faria.

## 27.4. Context7 MCP: o Claude recebe docs atualizadas

O Claude foi treinado com dados até um certo ponto no tempo. Isso significa que, quando você pergunta ao Claude sobre uma biblioteca ou framework —

- Ele pode conhecer o React 18, mas não o React 19
- Ele pode sugerir APIs depreciadas que não existem mais
- Ele pode perder features novas lançadas no mês passado
- Ele pode, com confiança, te dar um código que não funciona mais

Isso não é descuido do Claude. É só como os LLMs funcionam. Os dados de treinamento têm um corte. O problema não é a inteligência do Claude. É que a documentação se move mais rápido do que os ciclos de treinamento.

O Context7 é um serviço de inteligência de documentação que:

- 📚 Indexa documentação oficial de milhares de bibliotecas
- 🔄 Mantém as docs continuamente atualizadas — sempre a versão mais recente
- ⚡ Serve as docs em um formato otimizado para LLMs — não para humanos
- 🎯 Puxa apenas a seção relevante — não o site de docs inteiro

Docs normais são escritas para humanos navegarem. Docs do Context7 são estruturadas para a IA usar. Pense nisso como um feed de documentação ao vivo, sempre fresco, que o Claude pode consultar sob demanda — para qualquer biblioteca, qualquer versão, agora mesmo.

### 27.4.1. Um comando. Docs sempre frescas para o Claude.

```
claude mcp add --transport http context7 --scope project https://mcp.context7.com/mcp
```

Percebeu algo diferente aqui em relação ao Playwright? Sem `npx`. Sem processo local. Este é um servidor MCP remoto — hospedado na internet. O Claude o alcança via HTTP, ao vivo.

Aqui vai um problema real que vale resolver com o Context7:

Problema: o `App.jsx` importa avidamente (eager) todos os 18 componentes de página no topo — páginas de admin, páginas de employer, tudo — tudo agrupado no chunk JS inicial. A maioria dos usuários (candidatos a emprego) nunca visita rotas de admin ou employer, mas paga o custo de carregamento mesmo assim.

Correção: faça lazy-load das rotas com `lazy()` + Suspense do React. O React Router 7 (você está na v7.8) tem padrões específicos para isso que diferem da v6.

O Context7 é a ferramenta certa aqui — a API lazy do React Router 7 mudou em relação à v6 e as docs nos darão a abordagem exata e atual.

**Prompt de exemplo:**

```
Using context7, look up the React Router DOM v7 docs for lazy-loading routes with React.lazy() and Suspense.
Then refactor src/App.jsx in this job portal to lazy-load all page components instead of eagerly importing
them. Keep the provider nesting order and route structure intact. Add a simple fallback (a centered spinner or
"Loading..." text) for the Suspense boundary. Use the exact API from the fetched docs — don't rely on v6
patterns.
```

## 27.5. Cenários comuns com MCP

### 27.5.1. Ticket → Code → PR

Ferramentas: Jira (ou Linear) + GitHub + Filesystem

Fluxo: Jira/Linear → Claude Code → GitHub MCP → PR criado

Prompt de exemplo:

```
Implemente a feature descrita no ticket ENG-4521. Leia os detalhes,
escreva o código, rode os testes, commit e abra um PR no GitHub com
descrição adequada e link de volta ao ticket.
```

Resultado esperado: feature implementada + PR criado automaticamente.

### 27.5.2. Production Data → Code Insights

Ferramentas: Postgres (ou qualquer DB) + Filesystem

Fluxo: Postgres MCP → análise cruzada com código → branch + commit

Prompt de exemplo:

```
Query o PostgreSQL dos últimos 30 dias de uso da feature X.
Cruze com os módulos relevantes do repositório. Sugira e implemente
2 otimizações baseadas nos dados. Crie uma branch e commit as mudanças.
```

Resultado esperado: mudanças guiadas por dados com evidência (query exibida).

### 27.5.3. Monitoring → Auto-Fix

Ferramentas: Sentry (ou similar) + GitHub

Fluxo: Sentry MCP → análise de stack traces → fix → PR com métricas antes/depois

Prompt de exemplo:

```
Verifique erros recentes no Sentry relacionados ao módulo de autenticação.
Analise os stack traces contra o codebase, encontre a causa raiz,
rode os testes e crie um PR com métricas de antes/depois.
```

Resultado esperado: bugs reais corrigidos ao vivo.

### 27.5.4. Cross-Tool Automation (Notion → Slack → Code)

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

# 28. loop

## 28.1. Rodando prompts em um agendamento

Muitas vezes queremos checar o status de uma tarefa externa enquanto trabalhamos com o Claude Code. Por exemplo:

- Você iniciou um deploy 10 minutos atrás. Já terminou?
- Você fez push de um PR. O CI passou? Algum comentário de revisão?
- Um build longo está rodando. Você fica voltando (Cmd+Tab) para checar.

O problema: você está ou babá do Claude Code, ou se afastou e esqueceu dele.

## 28.2. /loop — Rode um prompt em repetição, sem usar as mãos

Uma skill embutida no Claude Code que re-executa seu prompt automaticamente em um intervalo escolhido, enquanto sua sessão permanece aberta.

| O que você fornece     | Exemplo                     | O que acontece                                  |
|------------------------|-----------------------------|-------------------------------------------------|
| Intervalo + Prompt     | `/loop 5m check the deploy` | Roda seu prompt em um agendamento fixo          |
| Apenas o prompt        | `/loop check the deploy`    | O Claude escolhe o intervalo de forma inteligente a cada vez |
| Nada                   | `/loop`                     | Roda o prompt de manutenção embutido            |

Você pode até dar loop em outro comando → `/loop 20m /review-pr 1234`

## 28.3. Intervalo inteligente (`/loop ...` sem tempo)

- O Claude escolhe de 1 min a 1 hora com base no que vê
- Build ativo? Esperas curtas. PR parado? Esperas mais longas.
- Imprime o delay escolhido + o motivo após cada iteração

## 28.4. O prompt de manutenção embutido

Basta digitar `/loop` — o Claude se torna o zelador do seu projeto. Quando você não dá nada a ele, o Claude roda automaticamente uma rotina de manutenção:

- Continua qualquer trabalho não finalizado da conversa
- Cuida do PR da branch atual — comentários de revisão, CI falho, conflitos de merge
- Roda passes de limpeza — caça a bugs, simplificações — quando não há nada pendente

Importante: o Claude não inicia novas iniciativas nem faz push/delete, a menos que a conversa já tenha autorizado.

Personalize: solte um arquivo `loop.md` para definir seu próprio prompt padrão:

- `.claude/loop.md` → nível de projeto (vence se ambos existirem)
- `~/.claude/loop.md` → nível de usuário (aplica-se em todo lugar)

## 28.5. Coisas para ter em mente

Para parar um loop: pressione `Esc` enquanto ele estiver esperando a próxima iteração.

Limites importantes:

- As tarefas só disparam enquanto o Claude Code estiver rodando e ocioso — **feche o terminal e elas param**
- Tarefas recorrentes expiram automaticamente após 7 dias (um disparo final, e então acabam)
- Uma conversa nova limpa todas as tarefas com escopo de sessão
- Retome com `claude --resume` para restaurar tarefas não expiradas

Precisa de agendamento durável? Veja Routines, tarefas agendadas do Desktop ou GitHub Actions — o `/loop` é para polling dentro da sessão.

## 28.6. Lembretes em linguagem natural

Pode-se escrever uma frase em linguagem natural pedindo para o Claude relembrá-lo de algo depois de X tempo.

## 28.7. Referência de tarefas agendadas

Na página https://code.claude.com/docs/en/scheduled-tasks, podemos ver a tabela com as 3 colunas: "Cloud", "Desktop" e "/loop". Cada uma apresenta uma forma diferente de rodar o Claude, e cada uma permite a programação de tarefas conforme sua especificidade (ex.: se os agendamentos continuam sendo executados mesmo fechando o aplicativo/página, o mínimo de tempo de intervalo entre operações, como são configuradas as funcionalidades de MCP, etc.).

# 29. Sub-Agents
Pode-se pedir para o Claude executar o agente X, pedindo via prompt para que ele seja executado em background.
Página de ajuda com vários exemplos de uso: https://code.claude.com/docs/en/sub-agents

Deixa eu te perguntar uma coisa.

Você está trabalhando num codebase grande. Você pede ao Claude Code: "Rode a suíte de testes completa, explore o módulo de autenticação, busque as docs de API mais recentes e então corrija os testes que falham."

O Claude começa a trabalhar. E em minutos... sua janela de contexto está se afogando. Centenas de linhas de logs de teste. Paredes de documentação. Conteúdos de arquivos que você nunca mais vai olhar — tudo se acumulando na sua conversa principal, expulsando as coisas que de fato importam.

Soa familiar?

É exatamente esse o problema que os **Sub Agents** foram criados para resolver.

## 29.1. O que são Sub Agents?

Pense assim.

Você é o arquiteto de um projeto de construção. Você não assenta pessoalmente cada tijolo, passa cada fio e instala cada cano. Você tem especialistas — um eletricista, um encanador, um engenheiro estrutural — cada um focado em seu domínio, cada um reportando a você apenas o resumo de que você precisa.

É exatamente assim que os Sub Agents funcionam no Claude Code.

**Sub-agents** são assistentes de IA especializados aos quais o Claude Code pode delegar tarefas. Pense nisso como um líder de equipe atribuindo tarefas a especialistas — em vez de fazer tudo sozinho, o Claude Code envia tarefas específicas ao especialista certo.

Cada sub-agente:

- Tem um propósito específico e uma área de expertise
- Recebe sua própria janela de contexto separada (não polui a conversa principal)
- Pode ser configurado com ferramentas específicas que tem permissão de usar
- Segue um system prompt personalizado que guia seu comportamento

O Claude Code vem com sub-agentes embutidos como o General-Purpose Agent, o Plan Agent e o Explore Agent.

## 29.2. Por que usar Sub-Agents?

Os sub-agentes ajudam a resolver problemas comuns de workflow de IA:

**Melhor gerenciamento de contexto** — Grandes saídas ficam dentro do sub-agente em vez de poluir a conversa principal.
**Comportamento especializado** — Cada agente pode ser ajustado para uma única responsabilidade.
**Otimização de custo** — Tarefas podem ser roteadas para modelos mais rápidos ou mais baratos.
**Permissões controladas** — Você pode restringir quais ferramentas ou ações um sub-agente tem permissão de usar.
**Reusabilidade** — Sub-agentes de nível de usuário podem ser reutilizados entre projetos.

Todo Sub Agent começa do zero — seu próprio contexto fresco, isolado da sessão principal, armado apenas com as ferramentas e skills específicas que você entrega a ele.

### 29.2.1. Janela de contexto

#### 29.2.1.1. Início da sessão:
- **CLAUDE.md** — Conteúdo completo sempre no contexto e usado em todo prompt
- **Metadados das Skills** — Apenas nome e descrição são carregados
- **Servidores MCP** — Nomes das ferramentas. Schemas sob demanda

#### 29.2.1.2. No uso:
- **Skills** — Conteúdo completo carregado no contexto ao usar a skill

### 29.2.2. Isolado
- **Hooks** — Rodam externamente, custo zero a menos que o hook retorne contexto adicional
- **Subagentes** — Carregam em um contexto separado quando criados

## 29.3. Criando um sub-agente

Passo 1: Rode `/agents` no Claude Code

Passo 2: Selecione "Create New Agent" — escolha nível de projeto ou de usuário

Passo 3: Selecione "Generate with Claude (recommended)"

Passo 4: Forneça uma breve descrição do que seu sub-agente deve fazer

Passo 5: Selecione as ferramentas de que ele precisa, o modelo, a cor e outras configurações

O Claude Code gerará seu sub-agente dentro de `.claude/agents/` ou `~/.claude/agents/`. Você pode personalizá-lo ainda mais conforme seus requisitos. Alternativamente, você também pode criar o arquivo markdown diretamente dentro de `.claude/agents/` ou `~/.claude/agents/`.

---

Na seção de criação de sub-agente:

> Create new agent
> Describe what this agent should do and when it should be used (be comprehensive for best results)

Pode-se passar a descrição como abaixo (sem os ```` ``` ````), ou via uma descrição simples apenas:

```
---
name: api-documentation-helper
description: Generates clear API documentation from source code
tools: Read, Glob
model: sonnet
---

You are an API documentation specialist. When triggered, scan the
available source files and produce concise, developer-friendly
documentation that explains endpoints, request structures, and
responses.
```

O frontmatter (a seção entre `---`) contém detalhes de configuração como: o nome do subagente, uma breve descrição explicando quando ele deve ser usado, quais ferramentas ele tem permissão de acessar e o modelo em que deve rodar. O conteúdo Markdown acima age como o system prompt do subagente. Ele define o papel, o comportamento e o estilo de saída do subagente.

Quando o Claude ativa este subagente, ele recebe apenas: este system prompt e informações básicas do ambiente (como o diretório de trabalho). Ele não herda as instruções completas do assistente principal, o que mantém o subagente focado e especializado.

## 29.4. Memória persistente em Sub-Agents

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

## 29.5. O que acontece quando a memória está habilitada?

Quando um sub-agente usa memória:

- Seu system prompt inclui instruções para ler e atualizar arquivos de memória.
- As primeiras 200 linhas do MEMORY.md são automaticamente fornecidas ao agente.
- Se o arquivo crescer demais, o agente é orientado a mantê-lo conciso.
- As ferramentas Read, Write e Edit são automaticamente habilitadas para que o agente possa gerenciar sua memória.

## 29.6. Como usar a memória de forma eficaz

Você pode orientar o sub-agente com instruções simples:

- Antes de começar o trabalho → "Check your memory for similar issues before analyzing this code."
- Depois de terminar o trabalho → "Save the important findings to your memory."

Com o tempo, isso cria uma base de conhecimento crescente que melhora o desempenho do agente.

## 29.7. Delegação automática

O Claude decide quando usar um sub-agente com base em:
- A redação do seu pedido
- A descrição definida dentro do arquivo do sub-agente
- O contexto de trabalho atual

Se uma tarefa casa com o propósito de um sub-agente, o Claude pode delegar o trabalho automaticamente. Para encorajar esse comportamento, você pode adicionar frases como "use proactively" na descrição do sub-agente, para que o Claude saiba que ele deve ser selecionado sempre que for relevante.

## 29.8. Execução em foreground vs background

Sub-agentes podem rodar em dois modos diferentes, dependendo de como você quer que eles se comportem.

⏳ **Execução em foreground (bloqueante)**
A conversa principal espera até o sub-agente terminar. Quaisquer pedidos de permissão ou perguntas de esclarecimento são mostrados diretamente a você. Melhor para tarefas em que você quer visibilidade e controle totais.

⚡ **Execução em background (concorrente)**
O sub-agente roda enquanto você continua trabalhando. Antes de iniciar, o Claude pede todas as permissões de ferramenta necessárias. Após a aprovação, o sub-agente usa automaticamente apenas essas permissões.

# 30. Agent teams (equipes de agentes)

Coordene múltiplas instâncias do Claude Code trabalhando juntas como uma equipe, com tarefas compartilhadas, mensageria entre agentes e gerenciamento centralizado.

https://code.claude.com/docs/en/agent-teams

# 31. Git

## 31.1. Claude Code para tarefas e atividades no GitHub

O Claude Code se conecta ao GitHub principalmente em três níveis diferentes:

**1. Terminal (Local)** — Você fala com o Claude no seu terminal. Ele roda comandos `git` e `gh` por você. Pense nisso como programar em par com alguém que nunca esquece a sintaxe do Git.

**2. GitHub Actions (Remoto)** — O Claude vive dentro do seu repositório do GitHub como um bot. Mencione `@claude` num PR ou issue, e ele responde — revisando código, corrigindo bugs ou implementando features automaticamente.

**3. Headless / Scripting (Automatizado)** — Use a flag `-p` para rodar o Claude sem uma sessão interativa. Perfeito para scripts de build, pipelines de CI/CD e processamento em lote.

## 31.2. Operações Git pelo terminal

Quando você abre o Claude Code na pasta do seu projeto, basta pedir, em linguagem natural, que ele faça operações Git. Exemplos do que você pode dizer:

- `show me a summary of all uncommitted changes`
- `commit and push the changes with a descriptive message`
- `create a feature branch called ui-improvements and switch to it`
- `push this branch and create a PR with a summary of changes`
- `review the pull request and merge into main branch`
- `switch back to main branch and delete the ui-improvements branch both locally and remotely as I am done with the UI changes`
- `pls look at the issue 2 reported and fix the problem`
- `commit and push this fix, then close issue 2`

O Claude roda os comandos `git` e `gh` de verdade nos bastidores. Você não precisa lembrar a sintaxe exata.

## 31.3. Plugin commit-commands

O plugin Commit Commands automatiza operações git comuns, reduzindo a troca de contexto e a execução manual de comandos. Em vez de rodar vários comandos git, use um único comando de barra para lidar com todo o seu workflow.

**Instalar o plugin:** Rode o comando `/plugin` e instale o plugin commit-commands, que fornece os seguintes comandos executáveis a partir de sessões do Claude Code:

| Comando           | O que faz                                                                          |
|-------------------|------------------------------------------------------------------------------------|
| `/commit`         | Revisa suas mudanças, faz o stage dos arquivos e cria um commit com uma mensagem inteligente |
| `/commit-push-pr` | Faz tudo — commita, faz push para uma feature branch e abre um PR em um único passo |
| `/clean_gone`     | Remove branches locais que já foram deletadas no remoto                             |

## 31.4. Rode sessões paralelas do Claude Code com Git Worktrees

### 31.4.1. Por que precisamos de worktrees?

Às vezes você pode trabalhar em várias tarefas ao mesmo tempo.

Exemplo:
- Uma tarefa = construir uma nova feature
- Outra tarefa = corrigir um bug de produção

Rodar tudo na mesma pasta pode causar:
- Conflitos de arquivos
- Mudanças misturadas
- Confusão entre branches

Os Git worktrees ajudam a evitar esses problemas.

### 31.4.2. O que é um Git Worktree?

Um worktree cria uma pasta de trabalho separada a partir do mesmo repositório.

Cada worktree:
- Tem seus próprios arquivos
- Usa sua própria branch
- Compartilha o mesmo histórico Git e repositório remoto

Pense nisso como criar vários espaços de trabalho para o mesmo projeto.

### 31.4.3. Como o Claude usa worktrees

Use a opção `--worktree` (ou `-w`). Se você não fornecer um nome, o Claude gerará um aleatório.

```
claude --worktree feature-cache
```

O que acontece:
- Uma nova pasta é criada
- Uma nova branch é criada automaticamente
- O Claude inicia dentro daquele espaço de trabalho isolado

### 31.4.4. Rodando múltiplas sessões

Você pode iniciar várias sessões do Claude assim:

```
claude --worktree feature-cache
claude --worktree bugfix-performance
```

Cada sessão roda de forma independente, tem seu próprio diretório de trabalho e usa sua própria branch.

### 31.4.5. Onde os worktrees são armazenados?

O Claude cria worktrees dentro do seu repositório: `<repo>/.claude/worktrees/<nome>`
Padrão de nomeação de branch: `worktree-<nome>`

### 31.4.6. Criando worktrees durante uma sessão

Você nem sempre precisa reiniciar o Claude. Basta dizer:
- "Start a worktree"
- "Work in a worktree"

O Claude vai:
- Criar um automaticamente
- Mover seu trabalho para dentro dele

## 31.5. Integração com GitHub Actions (o bot @claude)

É aqui que as coisas ficam realmente poderosas. O Claude Code tem uma GitHub Action oficial que o transforma em um bot vivendo dentro do seu repositório. O que ele pode fazer:

- Responder perguntas sobre seu código, arquitetura e decisões de design
- Revisar PRs e sugerir melhorias
- Implementar correções simples, refatorações e até novas features
- Trabalhar com issues do GitHub — lê-las, implementar soluções, criar PRs
- Acompanhar o progresso com checkboxes visuais que atualizam em tempo real

Como é acionado: alguém menciona `@claude` em um comentário de PR ou issue, e o GitHub Actions captura isso e roda o Claude.

**Como o gatilho @claude funciona**

O processo segue um fluxo claro:

1. **Alguém marca `@claude` em um comentário de PR ou issue** — por exemplo, "@claude review this PR" ou "@claude fix this bug".
2. **O GitHub Actions acorda** — O arquivo de workflow (`claude.yml`) detecta a menção e inicia um job.
3. **O Claude lê o contexto** — Ele olha duas fontes principais: o codebase inteiro e o arquivo CLAUDE.md. Isso garante que o Claude siga as regras e padrões do seu projeto.
4. **O Claude faz o trabalho** — Pode revisar código e deixar comentários, implementar uma correção e fazer push de commits, ou criar um novo PR.
5. **Os resultados aparecem no GitHub** — Você vê a resposta do Claude como um comentário, uma revisão de código ou um novo PR — como qualquer outro membro da equipe.

## 31.6. Configurando a GitHub Action — Início rápido

A forma mais rápida de configurar é pelo próprio Claude Code no seu terminal:

**Passo 1:** Abra o Claude Code e rode `/install-github-app`

**Passo 2:** Siga os prompts — ele instala o Claude GitHub App (de https://github.com/apps/claude) no seu repositório

**Passo 3:** Ele cria um PR com um arquivo de workflow (`.github/workflows/claude.yml`). Se você usa uma assinatura Pro/Max: antes de fazer o merge, adicione sua `ANTHROPIC_API_KEY` como um GitHub Secret (Settings → Secrets and Variables → Actions)

**Passo 4:** Faça o merge do PR.

**Passo 5:** Depois do merge do PR, rode `git pull` no seu repositório. Pronto!

**Teste:** Vá a qualquer PR ou issue e digite `@claude review this PR` ou `@claude fix this bug`.

Para mais detalhes, consulte:
- https://code.claude.com/docs/en/github-actions
- https://code.claude.com/docs/en/code-review

**Obs. 1:** Se quiser que o Claude deixe comentários nos PRs e nas Issues, no `.github/workflows/claude.yml` e no `.github/workflows/claude-code-review.yml`, troque de:

```yaml
permissions:
  contents: read
  pull-requests: read
  issues: read
  id-token: write
```

para:

```yaml
permissions:
  contents: read
  pull-requests: write
  issues: write
  id-token: write
```

**Obs. 2:** No arquivo `.github/workflows/claude-code-review.yml`, abaixo de:

```yaml
claude_code_oauth_token: ${{ secrets.CLAUDE_CODE_OAUTH_TOKEN }}
```

adicione as linhas:

```yaml
github_token: ${{ github.token }}
track_progress: true
```

para que o GitHub receba do Claude Code as mensagens de status do progresso. Suba as alterações para a branch `master` do repositório no GitHub.

Agora: ao criar uma Issue ou Pull Request, ao adicionar `@claude` seguido do pedido de atuação do bot (por exemplo, inserindo um comentário numa nova issue: "@claude implement this feature"), o Claude executará a tarefa dentro do servidor do GitHub. Pode-se pedir para ele criar uma branch com um nome apropriado; do contrário, ele escolherá o nome.

**Obs. 3:** Em vez de usar o padrão do GitHub para code reviews, podemos passar nosso próprio prompt. Ex.: no arquivo `.github/workflows/claude-code-review.yml`:

```yaml
# COMENTAR_ESSA_LINHA:  plugin_marketplaces: "https://github.com/anthropics/claude-code.git"
# COMENTAR_ESSA_LINHA:  plugins: "code-review@claude-code-plugins"
# COMENTAR_ESSA_LINHA:  prompt: "/code-review:code-review ${{ github.repository }}/pull/${{ github.event.pull_request.number }}"
# ADICIONAR NO LUGAR DAS ACIMA AS LINHAS ABAIXO, CONFORME SUA ESPECIFICAÇÃO
prompt: |
  REPO: ${{ github.repository }}
  PR NUMBER: ${{ github.event.pull_request.number }}

  Please review this pull request and provide feedback on:
  - Code quality and best practices
  - Potential bugs or issues
  - Performance considerations
  - Security concerns
  - Test coverage

  Use the repository's CLAUDE.md for guidance on style and conventions. Be constructive and helpful in your feedback.

  Use `gh pr comment` with your Bash tool to leave your review as a comment on the PR.
  See https://github.com/anthropics/claude-code-action/blob/main/docs/usage.md
  or https://code.claude.com/docs/en/cli-reference for available options
```

# 32. Status Line

**Status Line — Seu painel de cockpit sempre ligado**
*(Transforme seu terminal em um dashboard do Claude Code)*

**A dor:**

Você está mergulhado numa sessão do Claude Code. Três perguntas ficam te incomodando:

- 🤔 Quanto de contexto eu já queimei?
- 💰 Quanto esta sessão custou até agora?
- 🌿 Em qual branch eu estou afinal?

Toda vez que você quer uma resposta, você quebra o fluxo — digita um comando, lê a saída, volta ao trabalho.

**A solução — uma status line personalizável:**

Uma faixa persistente na parte de baixo do Claude Code que mostra o que você quiser, sempre visível, sem levantar um dedo.

Pense nisso como o painel do seu carro. Você não pergunta "a que velocidade estou indo?" — você dá uma olhada. Velocidade, combustível, RPM, tudo ali. A status line faz a mesma coisa para sua sessão do Claude Code.

*Não é só uma status line. É a sua status line. Você decide o que aparece ali, e o Claude Code apenas roda seu script e imprime o que você mandar imprimir.*

## 32.1. Como a Status Line funciona — JSON na entrada, texto na saída

- 📨 O Claude Code envia JSON para seu script via stdin — nome do modelo, custo, % de contexto, diretório git, ID da sessão, tudo
- 🛠️ Seu script lê isso, escolhe o que importa, formata — usando bash, Python, Node.js, PowerShell, o que você preferir
- 🖼️ Seu script imprime texto no stdout — e o Claude Code o exibe na parte de baixo da tela

## 32.2. O caminho "eu nem escrevi um script"

Você não precisa escrever o script você mesmo. Apenas descreva o que você quer:

```
/statusline show model name and context percentage with a progress bar
```

O Claude Code gera o script, coloca-o em `~/.claude/`, atualiza suas configurações, e está pronto. ✨

## 32.3. O caminho manual (`~/.claude/settings.json`)

```json
{
  "statusLine": {
    "type": "command",
    "command": "~/.claude/statusline.sh",
    "padding": 2
  }
}
```

### 32.3.1. O arquivo statusline-command.sh

```bash
#!/bin/bash
input=$(cat)

MODEL=$(echo "$input" | jq -r '.model.display_name' | awk '{print $1}')
DIR=$(echo "$input" | jq -r '.workspace.current_dir')
COST=$(echo "$input" | jq -r '.cost.total_cost_usd // 0')
PCT=$(echo "$input" | jq -r '.context_window.used_percentage // 0' | cut -d. -f1)
DURATION_MS=$(echo "$input" | jq -r '.cost.total_duration_ms // 0')
RL_5H=$(echo "$input" | jq -r '.rate_limits.five_hour.used_percentage // 0' | cut -d. -f1)
RL_7D=$(echo "$input" | jq -r '.rate_limits.seven_day.used_percentage // 0' | cut -d. -f1)

CYAN='\033[36m'; GREEN='\033[32m'; YELLOW='\033[33m'; RED='\033[31m'; RESET='\033[0m'

# Pick bar color based on context usage
if [ "$PCT" -ge 90 ]; then BAR_COLOR="$RED"
elif [ "$PCT" -ge 70 ]; then BAR_COLOR="$YELLOW"
else BAR_COLOR="$GREEN"; fi

FILLED=$((PCT / 10)); EMPTY=$((10 - FILLED))
printf -v FILL "%${FILLED}s"; printf -v PAD "%${EMPTY}s"
BAR="${FILL// /█}${PAD// /░}"

MINS=$((DURATION_MS / 60000)); SECS=$(((DURATION_MS % 60000) / 1000))

BRANCH=""
git rev-parse --git-dir > /dev/null 2>&1 && BRANCH=" | 🌿 $(git branch --show-current 2>/dev/null)"

echo -e "${CYAN}[$MODEL]${RESET} 📁 ${DIR##*/}$BRANCH"
COST_FMT=$(printf '$%.2f' "$COST")
echo -e "${BAR_COLOR}${BAR}${RESET} ${PCT}% | ${YELLOW}${COST_FMT}${RESET} | ⏱️ ${MINS}m ${SECS}s | 🔋 5h ${RL_5H}% · 7d ${RL_7D}%"
```

## 32.4. Referência de documentação

https://code.claude.com/docs/en/statusline

# 33. Comandos genéricos
Ao sair da sessão do Claude com:

```
/exit
```

ele mostra:

```
claude --resume 2a0b95ed-5618-45ec-8da7-f9d7803f55cb
```

Também é possível continuar na última sessão encerrada com:

```
claude -c
```

| Comando        | Descrição                                                                  |
|----------------|----------------------------------------------------------------------------|
| `@src/main.py` | Referencia um arquivo específico — o Claude o lê instantaneamente            |
| `!git status`  | Executa um comando de shell diretamente, sem o processamento conversacional do Claude |
| `#`            | Adiciona uma nota rápida à memória do Claude para esta sessão                |

Mostrar a lista de todos os modelos de LLM suportados:

```
/model
```

ou na CLI:

```
claude --model opus
```

```
claude -p "help me to improve my skills as a Java developer"
```

A flag `-p` executa o Claude em modo não interativo (modo print): ele envia o prompt, imprime a resposta no stdout e sai — nenhuma sessão de chat é aberta. Útil para scripts e pipelines Unix.

---
