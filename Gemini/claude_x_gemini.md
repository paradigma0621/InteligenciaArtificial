> **Sobre este documento:** este arquivo é a versão "paralela" das notas do
> Claude Code. Para cada tópico, há uma seção **(Claude)** com o conteúdo
> original e uma seção **(Gemini)** mostrando como alcançar o mesmo resultado
> usando o **Gemini CLI** — o agente de terminal open-source do Google
> (`npm install -g @google/gemini-cli`), o equivalente mais próximo do Claude
> Code. Quando o Gemini CLI **não** tem um recurso equivalente, isso é dito
> explicitamente, junto com o workaround mais próximo.

No que se refere às notas do Claude, as mesmas foram formuladas/extraídas do curso da Udemy: [Claude Code Bootcamp](https://www.udemy.com/course/claude-code-bootcamp)

- [1. /model (Claude)](#1-model-claude)
- [2. /model (Gemini)](#2-model-gemini)
- [3. VSCode (Claude)](#3-vscode-claude)
  - [3.1. Carregando o VSCode a partir da pasta de uma sessão](#31-carregando-o-vscode-a-partir-da-pasta-de-uma-sessão)
  - [3.2. Selecionando arquivos de contexto](#32-selecionando-arquivos-de-contexto)
- [4. VSCode (Gemini)](#4-vscode-gemini)
  - [4.1. Instalando e ativando a integração](#41-instalando-e-ativando-a-integração)
  - [4.2. Recursos da integração (análogos aos do Claude)](#42-recursos-da-integração-análogos-aos-do-claude)
  - [4.3. Selecionando contexto](#43-selecionando-contexto)
- [5. Modos de operação (Claude)](#5-modos-de-operação-claude)
- [6. Modos de operação (Gemini)](#6-modos-de-operação-gemini)
- [7. /voice (Claude)](#7-voice-claude)
- [8. /voice (Gemini)](#8-voice-gemini)
- [9. O arquivo CLAUDE.md → GEMINI.md (Claude)](#9-o-arquivo-claudemd--geminimd-claude)
  - [9.1. Primeiros passos](#91-primeiros-passos)
  - [9.2. Importando outros arquivos](#92-importando-outros-arquivos)
  - [9.3. O que incluir (alto valor)](#93-o-que-incluir-alto-valor)
  - [9.4. O que evitar (baixo valor ou arriscado)](#94-o-que-evitar-baixo-valor-ou-arriscado)
  - [9.5. Trate o CLAUDE.md como código](#95-trate-o-claudemd-como-código)
- [10. O arquivo CLAUDE.md → GEMINI.md (Gemini)](#10-o-arquivo-claudemd--geminimd-gemini)
  - [10.1. Primeiros passos](#101-primeiros-passos)
  - [10.2. Importando outros arquivos](#102-importando-outros-arquivos)
  - [10.3. Hierarquia (memória hierárquica)](#103-hierarquia-memória-hierárquica)
  - [10.4. O que incluir / o que evitar / tratar como código](#104-o-que-incluir--o-que-evitar--tratar-como-código)
- [11. Configurações do Claude Code (Claude)](#11-configurações-do-claude-code-claude)
  - [11.1. Abordagem 1: O comando /config (UI interativa)](#111-abordagem-1-o-comando-config-ui-interativa)
  - [11.2. Abordagem 2: Arquivos settings.json (configuração persistente)](#112-abordagem-2-arquivos-settingsjson-configuração-persistente)
    - [11.2.1. Qual configuração prevalece? (Ordem de prioridade)](#1121-qual-configuração-prevalece-ordem-de-prioridade)
    - [11.2.2. Uma estrutura típica de settings.json](#1122-uma-estrutura-típica-de-settingsjson)
- [12. Configurações do Gemini CLI (Gemini)](#12-configurações-do-gemini-cli-gemini)
  - [12.1. Abordagem 1: O comando /settings (UI interativa)](#121-abordagem-1-o-comando-settings-ui-interativa)
  - [12.2. Abordagem 2: Arquivos settings.json (configuração persistente)](#122-abordagem-2-arquivos-settingsjson-configuração-persistente)
    - [12.2.1. Qual configuração prevalece? (Ordem de prioridade)](#1221-qual-configuração-prevalece-ordem-de-prioridade)
    - [12.2.2. Uma estrutura típica de settings.json](#1222-uma-estrutura-típica-de-settingsjson)
- [13. /permissions (Claude)](#13-permissions-claude)
  - [13.1. Permissões no Claude Code](#131-permissões-no-claude-code)
    - [13.1.1. Definindo regras de permissão](#1311-definindo-regras-de-permissão)
      - [13.1.1.1. Casar com tudo](#13111-casar-com-tudo)
      - [13.1.1.2. Casar com algo específico](#13112-casar-com-algo-específico)
      - [13.1.1.3. Curingas para flexibilidade](#13113-curingas-para-flexibilidade)
      - [13.1.1.4. Um exemplo do mundo real](#13114-um-exemplo-do-mundo-real)
- [14. /permissions (Gemini)](#14-permissions-gemini)
  - [14.1. Definindo regras de permissão no Gemini](#141-definindo-regras-de-permissão-no-gemini)
      - [14.1.0.1. Casar com algo específico (allow/deny por comando de shell)](#14101-casar-com-algo-específico-allowdeny-por-comando-de-shell)
      - [14.1.0.2. Exemplo do mundo real (o mesmo do Claude)](#14102-exemplo-do-mundo-real-o-mesmo-do-claude)
      - [14.1.0.3. Aprovação dinâmica na sessão](#14103-aprovação-dinâmica-na-sessão)
- [15. /status (Claude)](#15-status-claude)
- [16. /status (Gemini)](#16-status-gemini)
- [17. /usage (Claude)](#17-usage-claude)
- [18. /usage (Gemini)](#18-usage-gemini)
- [19. Output Style (Claude)](#19-output-style-claude)
  - [19.1. Crie um Output Style personalizado no Claude Code](#191-crie-um-output-style-personalizado-no-claude-code)
    - [19.1.1. O que é um Output Style personalizado?](#1911-o-que-é-um-output-style-personalizado)
    - [19.1.2. Estrutura de um Output Style personalizado](#1912-estrutura-de-um-output-style-personalizado)
    - [19.1.3. Onde salvar seus arquivos de estilo](#1913-onde-salvar-seus-arquivos-de-estilo)
    - [19.1.4. Casos de uso práticos](#1914-casos-de-uso-práticos)
- [20. Output Style (Gemini)](#20-output-style-gemini)
  - [20.1. Via GEMINI.md (a forma mais simples e portável)](#201-via-geminimd-a-forma-mais-simples-e-portável)
  - [20.2. Via override do system prompt (`GEMINI_SYSTEM_MD`)](#202-via-override-do-system-prompt-gemini_system_md)
    - [20.2.1. Onde guardar seus "estilos"](#2021-onde-guardar-seus-estilos)
- [21. /effort (Claude)](#21-effort-claude)
- [22. /effort (Gemini)](#22-effort-gemini)
- [23. Statelessness e a ilusão da conversa contínua (Claude)](#23-statelessness-e-a-ilusão-da-conversa-contínua-claude)
- [24. Statelessness e a ilusão da conversa contínua (Gemini)](#24-statelessness-e-a-ilusão-da-conversa-contínua-gemini)
- [25. /context (Claude)](#25-context-claude)
  - [25.1. O que acontece quando o contexto enche?](#251-o-que-acontece-quando-o-contexto-enche)
- [26. /context (Gemini)](#26-context-gemini)
  - [26.1. O que acontece quando o contexto enche?](#261-o-que-acontece-quando-o-contexto-enche)
- [27. /compact (Claude)](#27-compact-claude)
- [28. /compact → /compress (Gemini)](#28-compact--compress-gemini)
- [29. /clear (Claude)](#29-clear-claude)
- [30. /clear (Gemini)](#30-clear-gemini)
- [31. /rename (Claude)](#31-rename-claude)
  - [31.1. Dúvida #01](#311-dúvida-01)
- [32. /rename → /chat save (Gemini)](#32-rename--chat-save-gemini)
  - [32.1. Diferença em relação ao `/rename` do Claude](#321-diferença-em-relação-ao-rename-do-claude)
- [33. /resume (Claude)](#33-resume-claude)
- [34. /resume → /chat resume (Gemini)](#34-resume--chat-resume-gemini)
- [35. claude --continue --fork-session (Claude)](#35-claude---continue---fork-session-claude)
  - [35.1. Como o Claude Code gerencia sessões entre branches do Git](#351-como-o-claude-code-gerencia-sessões-entre-branches-do-git)
- [36. fork de sessão → conversational branching (Gemini)](#36-fork-de-sessão--conversational-branching-gemini)
  - [36.1. Sessões e branches do Git no Gemini](#361-sessões-e-branches-do-git-no-gemini)
- [37. /rewind → /restore (Claude)](#37-rewind--restore-claude)
  - [37.1. Como fazer rewind](#371-como-fazer-rewind)
  - [37.2. O que os checkpoints NÃO rastreiam](#372-o-que-os-checkpoints-não-rastreiam)
- [38. /rewind → /restore (Gemini)](#38-rewind--restore-gemini)
  - [38.1. Como funciona](#381-como-funciona)
  - [38.2. Diferença em relação ao `/rewind`](#382-diferença-em-relação-ao-rewind)
  - [38.3. O que os checkpoints NÃO rastreiam](#383-o-que-os-checkpoints-não-rastreiam)
- [39. Histórico (Claude)](#39-histórico-claude)
- [40. Histórico (Gemini)](#40-histórico-gemini)
- [41. Os hábitos de sessão do desenvolvedor esperto (Claude)](#41-os-hábitos-de-sessão-do-desenvolvedor-esperto-claude)
- [42. Os hábitos de sessão do desenvolvedor esperto (Gemini)](#42-os-hábitos-de-sessão-do-desenvolvedor-esperto-gemini)
- [43. Memory (Memória) (Claude)](#43-memory-memória-claude)
  - [43.1. /memory](#431-memory)
  - [43.2. Auto Memory no Claude Code](#432-auto-memory-no-claude-code)
    - [43.2.1. Dois sistemas de memória: o livro-texto vs. o caderno](#4321-dois-sistemas-de-memória-o-livro-texto-vs-o-caderno)
      - [43.2.1.1. CLAUDE.md — O livro-texto (escrito por VOCÊ)](#43211-claudemd--o-livro-texto-escrito-por-você)
      - [43.2.1.2. Auto Memory (MEMORY.md) — O caderno (escrito pelo CLAUDE)](#43212-auto-memory-memorymd--o-caderno-escrito-pelo-claude)
    - [43.2.2. Como o Auto Memory funciona por baixo dos panos](#4322-como-o-auto-memory-funciona-por-baixo-dos-panos)
    - [43.2.3. Onde o Claude armazena suas anotações?](#4323-onde-o-claude-armazena-suas-anotações)
      - [43.2.3.1. Mensagens de status](#43231-mensagens-de-status)
  - [43.3. O comando /memory](#433-o-comando-memory)
    - [43.3.1. Dizendo ao Claude o que lembrar](#4331-dizendo-ao-claude-o-que-lembrar)
  - [43.4. As três camadas de memória — o quadro completo](#434-as-três-camadas-de-memória--o-quadro-completo)
  - [43.5. Configurando o Auto Memory](#435-configurando-o-auto-memory)
    - [43.5.1. Como alternar (toggle)](#4351-como-alternar-toggle)
    - [43.5.2. Diretório de memória personalizado](#4352-diretório-de-memória-personalizado)
    - [43.5.3. Como funciona](#4353-como-funciona)
- [44. Memory (Memória) (Gemini)](#44-memory-memória-gemini)
  - [44.1. /memory](#441-memory)
  - [44.2. ⚠️ Diferença central: NÃO há "Auto Memory" automática](#442-️-diferença-central-não-há-auto-memory-automática)
  - [44.3. Mapeando as três camadas de memória](#443-mapeando-as-três-camadas-de-memória)
  - [44.4. Diretório de memória / como funciona](#444-diretório-de-memória--como-funciona)
- [45. Rules (Regras) (Claude)](#45-rules-regras-claude)
  - [45.1. Rules no Claude Code](#451-rules-no-claude-code)
  - [45.2. Onde as Rules vivem?](#452-onde-as-rules-vivem)
  - [45.3. Dois tipos de regras](#453-dois-tipos-de-regras)
    - [45.3.1. Regras sempre carregadas (always-loaded)](#4531-regras-sempre-carregadas-always-loaded)
    - [45.3.2. Regras com escopo de path (path-scoped)](#4532-regras-com-escopo-de-path-path-scoped)
    - [45.3.3. Rules vs CLAUDE.md — quando usar qual](#4533-rules-vs-claudemd--quando-usar-qual)
- [46. Rules (Regras) (Gemini)](#46-rules-regras-gemini)
  - [46.1. GEMINI.md hierárquico por subdiretório (o análogo mais próximo do path-scoping)](#461-geminimd-hierárquico-por-subdiretório-o-análogo-mais-próximo-do-path-scoping)
  - [46.2. Imports modulares no GEMINI.md](#462-imports-modulares-no-geminimd)
  - [46.3. Extensões com regras/contexto](#463-extensões-com-regrascontexto)
    - [46.3.1. Quando usar qual (mesma lógica do Claude)](#4631-quando-usar-qual-mesma-lógica-do-claude)
- [47. Skills (Claude)](#47-skills-claude)
  - [47.1. Construa sua própria skill](#471-construa-sua-própria-skill)
    - [47.1.1. Passos para criar uma skill personalizada](#4711-passos-para-criar-uma-skill-personalizada)
      - [47.1.1.1. 1) Crie o diretório da skill](#47111-1-crie-o-diretório-da-skill)
      - [47.1.1.2. 2) Escreva um arquivo SKILL.md](#47112-2-escreva-um-arquivo-skillmd)
      - [47.1.1.3. 3) Teste a skill](#47113-3-teste-a-skill)
  - [47.2. Site de referência: https://code.claude.com/docs/en/skills (tem informações importantes)](#472-site-de-referência-httpscodeclaudecomdocsenskills-tem-informações-importantes)
  - [47.3. `./skills/feature-guide`: exemplo de como rodar uma skill em um sub-agente](#473-skillsfeature-guide-exemplo-de-como-rodar-uma-skill-em-um-sub-agente)
- [48. Skills (Gemini)](#48-skills-gemini)
  - [48.1. Reproduzindo a skill "analyze-issue"](#481-reproduzindo-a-skill-analyze-issue)
  - [48.2. Diferenças em relação às Skills do Claude](#482-diferenças-em-relação-às-skills-do-claude)
- [49. commands (deprecado) (Claude)](#49-commands-deprecado-claude)
- [50. commands (Gemini)](#50-commands-gemini)
- [51. hooks (Claude)](#51-hooks-claude)
  - [51.1. O que exatamente são hooks?](#511-o-que-exatamente-são-hooks)
  - [51.2. Determinístico](#512-determinístico)
  - [51.3. Agora, qual o propósito? Por que os hooks existem?](#513-agora-qual-o-propósito-por-que-os-hooks-existem)
    - [51.3.1. Primeiro — automação](#5131-primeiro--automação)
    - [51.3.2. Segundo — proteção](#5132-segundo--proteção)
    - [51.3.3. Terceiro — consciência (awareness)](#5133-terceiro--consciência-awareness)
  - [51.4. Sem hooks, todas as três dependem do julgamento da IA.](#514-sem-hooks-todas-as-três-dependem-do-julgamento-da-ia)
  - [51.5. O ponto de dor sem hooks](#515-o-ponto-de-dor-sem-hooks)
  - [51.6. Onde os hooks são armazenados?](#516-onde-os-hooks-são-armazenados)
  - [51.7. Criando um hook](#517-criando-um-hook)
  - [51.8. Estrutura de configuração de hook](#518-estrutura-de-configuração-de-hook)
  - [51.9. Configure seu primeiro hook](#519-configure-seu-primeiro-hook)
  - [51.10. Observação](#5110-observação)
  - [51.11. Como os hooks funcionam](#5111-como-os-hooks-funcionam)
  - [51.12. IMPORTANTE](#5112-importante)
- [52. hooks (Gemini)](#52-hooks-gemini)
  - [52.1. Onde os hooks são armazenados?](#521-onde-os-hooks-são-armazenados)
  - [52.2. Como os hooks funcionam](#522-como-os-hooks-funcionam)
  - [52.3. Eventos de ciclo de vida](#523-eventos-de-ciclo-de-vida)
  - [52.4. Estrutura de configuração](#524-estrutura-de-configuração)
- [53. MCP (Claude)](#53-mcp-claude)
  - [53.1. /mcp](#531-mcp)
  - [53.2. Site de referência (IMPORTANTE VER)](#532-site-de-referência-importante-ver)
  - [53.3. Exemplos de prompts que podem ser usados com Playwright (alguns com Google Chrome)](#533-exemplos-de-prompts-que-podem-ser-usados-com-playwright-alguns-com-google-chrome)
  - [53.4. Context7 MCP: o Claude recebe docs atualizadas](#534-context7-mcp-o-claude-recebe-docs-atualizadas)
    - [53.4.1. Um comando. Docs sempre frescas para o Claude.](#5341-um-comando-docs-sempre-frescas-para-o-claude)
  - [53.5. Cenários comuns com MCP](#535-cenários-comuns-com-mcp)
    - [53.5.1. Ticket → Code → PR](#5351-ticket--code--pr)
    - [53.5.2. Production Data → Code Insights](#5352-production-data--code-insights)
    - [53.5.3. Monitoring → Auto-Fix](#5353-monitoring--auto-fix)
    - [53.5.4. Cross-Tool Automation (Notion → Slack → Code)](#5354-cross-tool-automation-notion--slack--code)
- [54. MCP (Gemini)](#54-mcp-gemini)
  - [54.1. /mcp](#541-mcp)
  - [54.2. Como configurar servidores MCP](#542-como-configurar-servidores-mcp)
    - [54.2.1. Context7 no Gemini — docs sempre frescas](#5421-context7-no-gemini--docs-sempre-frescas)
    - [54.2.2. Playwright / Chrome DevTools MCP](#5422-playwright--chrome-devtools-mcp)
  - [54.3. Cenários comuns com MCP](#543-cenários-comuns-com-mcp)
- [55. loop (Claude)](#55-loop-claude)
  - [55.1. Rodando prompts em um agendamento](#551-rodando-prompts-em-um-agendamento)
  - [55.2. /loop — Rode um prompt em repetição, sem usar as mãos](#552-loop--rode-um-prompt-em-repetição-sem-usar-as-mãos)
  - [55.3. Intervalo inteligente (`/loop ...` sem tempo)](#553-intervalo-inteligente-loop--sem-tempo)
  - [55.4. O prompt de manutenção embutido](#554-o-prompt-de-manutenção-embutido)
  - [55.5. Coisas para ter em mente](#555-coisas-para-ter-em-mente)
  - [55.6. Lembretes em linguagem natural](#556-lembretes-em-linguagem-natural)
  - [55.7. Referência de tarefas agendadas](#557-referência-de-tarefas-agendadas)
- [56. loop (Gemini)](#56-loop-gemini)
  - [56.1. Headless mode + shell loop (o análogo mais direto)](#561-headless-mode--shell-loop-o-análogo-mais-direto)
  - [56.2. Cron / agendador do SO (agendamento durável)](#562-cron--agendador-do-so-agendamento-durável)
  - [56.3. GitHub Actions (durável, no servidor)](#563-github-actions-durável-no-servidor)
  - [56.4. Mapeamento](#564-mapeamento)
- [57. Sub-Agents (Claude)](#57-sub-agents-claude)
  - [57.1. Sub-Agents](#571-sub-agents)
  - [57.2. O que são Sub Agents?](#572-o-que-são-sub-agents)
  - [57.3. Por que usar Sub-Agents?](#573-por-que-usar-sub-agents)
    - [57.3.1. Janela de contexto](#5731-janela-de-contexto)
      - [57.3.1.1. Início da sessão:](#57311-início-da-sessão)
      - [57.3.1.2. No uso:](#57312-no-uso)
    - [57.3.2. Isolado](#5732-isolado)
  - [57.4. Criando um sub-agente](#574-criando-um-sub-agente)
  - [57.5. Memória persistente em Sub-Agents](#575-memória-persistente-em-sub-agents)
  - [57.6. O que acontece quando a memória está habilitada?](#576-o-que-acontece-quando-a-memória-está-habilitada)
  - [57.7. Como usar a memória de forma eficaz](#577-como-usar-a-memória-de-forma-eficaz)
  - [57.8. Delegação automática](#578-delegação-automática)
  - [57.9. Execução em foreground vs background](#579-execução-em-foreground-vs-background)
- [58. agents (agentes) (Gemini)](#58-agents-agentes-gemini)
  - [58.1. Criando um sub-agente](#581-criando-um-sub-agente)
  - [58.2. Delegação automática e explícita](#582-delegação-automática-e-explícita)
  - [58.3. Execução paralela / background](#583-execução-paralela--background)
  - [58.4. Memória persistente em sub-agentes](#584-memória-persistente-em-sub-agentes)
- [59. Agent teams (equipes de agentes) (Claude)](#59-agent-teams-equipes-de-agentes-claude)
- [60. Agent teams (equipes de agentes) (Gemini)](#60-agent-teams-equipes-de-agentes-gemini)
- [61. Git (Claude)](#61-git-claude)
  - [61.1. Claude Code para tarefas e atividades no GitHub](#611-claude-code-para-tarefas-e-atividades-no-github)
  - [61.2. Operações Git pelo terminal](#612-operações-git-pelo-terminal)
  - [61.3. Plugin commit-commands](#613-plugin-commit-commands)
  - [61.4. Rode sessões paralelas do Claude Code com Git Worktrees](#614-rode-sessões-paralelas-do-claude-code-com-git-worktrees)
    - [61.4.1. Por que precisamos de worktrees?](#6141-por-que-precisamos-de-worktrees)
    - [61.4.2. O que é um Git Worktree?](#6142-o-que-é-um-git-worktree)
    - [61.4.3. Como o Claude usa worktrees](#6143-como-o-claude-usa-worktrees)
    - [61.4.4. Rodando múltiplas sessões](#6144-rodando-múltiplas-sessões)
    - [61.4.5. Onde os worktrees são armazenados?](#6145-onde-os-worktrees-são-armazenados)
    - [61.4.6. Criando worktrees durante uma sessão](#6146-criando-worktrees-durante-uma-sessão)
  - [61.5. Integração com GitHub Actions (o bot @claude)](#615-integração-com-github-actions-o-bot-claude)
  - [61.6. Configurando a GitHub Action — Início rápido](#616-configurando-a-github-action--início-rápido)
- [62. Git (Gemini)](#62-git-gemini)
  - [62.1. Operações Git pelo terminal](#621-operações-git-pelo-terminal)
  - [62.2. Plugin commit-commands → custom commands no Gemini](#622-plugin-commit-commands--custom-commands-no-gemini)
  - [62.3. Sessões paralelas com Git Worktrees](#623-sessões-paralelas-com-git-worktrees)
  - [62.4. Integração com GitHub Actions (o bot @gemini-cli)](#624-integração-com-github-actions-o-bot-gemini-cli)
  - [62.5. Configurando a GitHub Action — Início rápido](#625-configurando-a-github-action--início-rápido)
- [63. Status Line (Claude)](#63-status-line-claude)
  - [63.1. Como a Status Line funciona — JSON na entrada, texto na saída](#631-como-a-status-line-funciona--json-na-entrada-texto-na-saída)
  - [63.2. O caminho "eu nem escrevi um script"](#632-o-caminho-eu-nem-escrevi-um-script)
  - [63.3. O caminho manual (`~/.claude/settings.json`)](#633-o-caminho-manual-claudesettingsjson)
    - [63.3.1. O arquivo statusline-command.sh](#6331-o-arquivo-statusline-commandsh)
  - [63.4. Referência de documentação](#634-referência-de-documentação)
- [64. Status Line (Gemini)](#64-status-line-gemini)
- [65. Comandos genéricos (Claude)](#65-comandos-genéricos-claude)
- [66. Comandos genéricos (Gemini)](#66-comandos-genéricos-gemini)
  - [66.1. Apêndice: tabela-resumo Claude ↔ Gemini](#661-apêndice-tabela-resumo-claude--gemini)



# 1. /model (Claude)
Permite escolher qual modelo de LLM usar.

- **Opus 4.8**: raciocínio mais profundo, tende a resolver em menos turnos, mas com respostas e cadeias de pensamento mais longas. Melhor custo-efetividade em tarefas complexas (refactors grandes, debugging arquitetural) onde Sonnet/Haiku precisariam de várias iterações.
- **Sonnet 4.6**: equilíbrio. Para a maioria das tarefas de engenharia de software do dia a dia, gasta tokens comparáveis ao Opus, mas a 1/5 do preço.
- **Haiku 4.5**: respostas mais curtas e diretas. Excelente para tarefas determinísticas (correções de lint, renomeações, leituras simples), mas pode multiplicar turnos em tarefas ambíguas — anulando a economia.

# 2. /model (Gemini)
O Gemini CLI também permite escolher o modelo, mas com algumas diferenças importantes.

**Comando `/model`:** desde nov/2025, o Gemini CLI tem o comando `/model` (digitado dentro do REPL) para trocar o modelo da sessão atual sem reiniciar. Antes disso, a troca era feita apenas via flag de inicialização.

**Flag de inicialização:** `gemini --model <nome>` (ou `-m`). Aceita tanto *aliases* amigáveis quanto nomes concretos de modelo:

```bash
gemini --model gemini-2.5-flash
gemini -m gemini-2.5-pro
```

**Famílias de modelo disponíveis (análogo a Opus/Sonnet/Haiku):**

- **Gemini 3 Pro / Gemini 2.5 Pro** (≈ "Opus"): raciocínio mais profundo, melhor para tarefas complexas, refactors grandes e debugging arquitetural. O 2.5 Pro tem janela de contexto de **1 milhão de tokens**.
- **Gemini 3 Flash / Gemini 2.5 Flash** (≈ "Haiku/Sonnet"): respostas rápidas e baratas, ótimas para tarefas determinísticas e de alto volume.
- **Auto (model routing)**: diferente do Claude, o Gemini CLI tem **roteamento automático de modelo** — ele decide sozinho entre Flash (perguntas simples) e Pro (tarefas complexas) com base na complexidade da tarefa. Configurável; veja https://geminicli.com/docs/cli/model-routing/.

**Diferença de filosofia:** no Claude você escolhe explicitamente o modelo e ele permanece. No Gemini, o padrão pode rotear/rebaixar automaticamente para Flash sob carga ou conforme a complexidade — algo a ter em mente se quiser garantir Pro em todos os turnos (fixe com `--model` ou na config).

# 3. VSCode (Claude)

## 3.1. Carregando o VSCode a partir da pasta de uma sessão

Indo na pasta onde foi iniciada uma sessão do comando `claude` no terminal, é possível carregar o VSCode e, carregando a ferramenta do Claude nele, navegar pelas conversas que foram feitas no terminal, visualizando-as como uma pré-visualização Markdown.

## 3.2. Selecionando arquivos de contexto

É possível selecionar quais arquivos se deseja ter como contexto (por padrão, o que estiver aberto no momento) no chat. Caso se selecione linhas dentro do arquivo aberto, essas linhas selecionadas passam a ser o contexto na guia do chat.

# 4. VSCode (Gemini)

O Gemini CLI integra com o VS Code (e editores compatíveis, como o Antigravity) através da extensão **Gemini CLI Companion**.

## 4.1. Instalando e ativando a integração

- **Automático:** ao rodar `gemini` dentro do terminal integrado de um editor suportado, ele detecta o ambiente e pergunta se você quer conectar. Respondendo "Yes", ele instala a extensão companion e habilita a conexão automaticamente.
- **Manual:** instale a extensão "Gemini CLI Companion" no Marketplace do VS Code (ou no Open VSX) e depois rode `/ide enable` no CLI para ativar a integração. Use `/ide install` para instalar a partir do próprio CLI.

## 4.2. Recursos da integração (análogos aos do Claude)

- **Native diffing:** o Gemini CLI mostra as edições propostas como um diff nativo dentro do VS Code, que você aceita ou rejeita visualmente.
- **Comandos da Command Palette** (`Ctrl+Shift+P` / `Cmd+Shift+P`):
  - **Gemini CLI: Run** — inicia uma nova sessão no terminal integrado.
  - **Gemini CLI: Accept Diff** — aceita as mudanças no diff ativo.
  - **Gemini CLI: Close Diff Editor** — rejeita as mudanças e fecha o diff.

## 4.3. Selecionando contexto

Assim como no Claude, a integração é "context-aware": o arquivo aberto e o texto selecionado no editor são compartilhados com o CLI como contexto. Você também pode injetar arquivos manualmente com a sintaxe `@caminho/arquivo` no prompt.

Referência: https://google-gemini.github.io/gemini-cli/docs/ide-integration/

# 5. Modos de operação (Claude)

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

# 6. Modos de operação (Gemini)

O Gemini CLI tem "approval modes" análogos, controlados por `general.defaultApprovalMode` no `settings.json` ou alternados por atalho.

**Modo padrão (`default`)**
- Modo ativo ao iniciar o `gemini` normalmente.
- Cada ação que modifica arquivos ou roda shell pede confirmação.

**Modo auto-edit (`auto_edit`)** — análogo ao auto-accept/Edit Mode do Claude
- Pressione `Shift+Tab` para ciclar entre os modos de aprovação.
- Aprova automaticamente modificações de arquivos (file edits) sem perguntar.
- Configurável com `"general": { "defaultApprovalMode": "auto_edit" }`.

**Modo Plan**
- ⚠️ **O Gemini CLI não tem um "Plan mode" embutido idêntico ao do Claude** (onde o agente só planeja e não toca em nada até aprovação).
- Workaround para obter o mesmo resultado: rode o modo padrão (que já pede aprovação em cada ação destrutiva) e/ou peça explicitamente no prompt: *"Apenas elabore um plano detalhado, passo a passo, e NÃO execute nenhuma alteração até eu aprovar."* Você também pode usar um sub-agente "planner" (ver seção *agents (Gemini)*) com ferramentas somente de leitura.

**Modo YOLO** — equivalente direto
- Toggle dentro da sessão: pressione **`Ctrl+Y`**.
- Na inicialização: `gemini --yolo` (ou `-y`).
- Por config: `general.defaultApprovalMode: "yolo"` (e `security.disableYoloMode: false`).
- Auto-aprova **todas** as ações, incluindo comandos de shell (commit, instalar pacotes, etc.) — bypassa completamente o sistema de permissões.
- ⚠️ Só pode ser usado em um *trusted workspace*. É o modo mais perigoso; indicado para ambientes isolados/CI.

> **Observação:** Para interromper o processamento, pressione `ESC` (uma vez cancela a operação atual). Para sair, `Ctrl+C` duas vezes ou `/quit`.

# 7. /voice (Claude)

Permite usar o servidor do Claude para transcrever áudio do microfone em texto transcrito em tempo real. Não consome tokens, mas há o porém da privacidade dos dados.

Sugestão de alternativa grátis e sigilosa: https://handy.computer/

# 8. /voice (Gemini)

⚠️ **O Gemini CLI não tem um comando de voz/transcrição embutido** equivalente ao `/voice` do Claude. Ele é puramente texto no terminal.

Para alcançar o mesmo resultado (ditar por voz no terminal), use uma ferramenta de transcrição externa do sistema operacional, que digita o texto transcrito em qualquer campo — inclusive no prompt do `gemini`:

- **Alternativa grátis e local (sigilosa):** https://handy.computer/ (a mesma sugerida para o Claude) — roda offline, sem enviar áudio para nenhum servidor.
- **Ditado nativo do SO:** ditado por voz do macOS, Windows Speech Recognition, ou ferramentas Linux (ex.: `nerd-dictation`).

Como essas ferramentas operam no nível do SO e apenas "digitam" o texto, elas funcionam igualmente bem com o Gemini CLI e com o Claude Code.

# 9. O arquivo CLAUDE.md → GEMINI.md (Claude)

Recomendação: não passe de 300 linhas.

## 9.1. Primeiros passos

Você não precisa criar o arquivo CLAUDE.md manualmente. Em vez disso, rode `/init`. O Claude Code analisa seu codebase e gera um CLAUDE.md inicial.

Ele detecta sistemas de build, frameworks de teste e padrões de código automaticamente. Isso dá uma base sólida para refinar e personalizar. Não há formato obrigatório — mantenha-o curto, claro e legível por humanos.

## 9.2. Importando outros arquivos

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

## 9.3. O que incluir (alto valor)

- Tecnologias e versões exatas usadas no projeto
- Estrutura de pastas e pelo que cada pasta é responsável
- Comandos de build, execução e teste
- Regras inegociáveis (tratamento de exceções, regras de formatação de código, padrões de segurança)
- Padrões que são explicitamente proibidos
- Como a equipe espera que as mudanças sejam feitas (branching, workflow de PR, etc.)

## 9.4. O que evitar (baixo valor ou arriscado)

- Segredos, credenciais ou chaves de API — nunca coloque isso no CLAUDE.md
- Regras de estilo já impostas por linters ou formatadores (ESLint, Prettier, Checkstyle)
- Grandes blocos de documentação que o Claude consegue consultar por conta própria
- Instruções em excesso — se o arquivo for muito longo, regras importantes se perdem no meio do ruído

## 9.5. Trate o CLAUDE.md como código

- Versione-o no Git para que toda a sua equipe possa contribuir
- Revise-o quando o Claude se comportar mal — a correção costuma estar no arquivo, não no prompt
- Pode-o regularmente — remova regras que não são mais relevantes
- Teste mudanças observando se o comportamento do Claude realmente muda
- Se o Claude continua ignorando uma regra — o arquivo provavelmente está longo demais e a regra está se perdendo
- Se o Claude continua perguntando coisas já respondidas no CLAUDE.md — a redação pode estar ambígua
- Use ênfase como "IMPORTANT" ou "YOU MUST" para regras críticas, a fim de melhorar a aderência
- O arquivo ganha valor com o tempo — quanto mais você o refina, melhor o Claude se sai

# 10. O arquivo CLAUDE.md → GEMINI.md (Gemini)

No Gemini CLI o arquivo equivalente é o **`GEMINI.md`** (o "context file" / hierarchical memory). O conceito é praticamente idêntico: instruções em Markdown carregadas automaticamente em toda conversa.

Recomendação igual: mantenha curto, claro e legível por humanos.

## 10.1. Primeiros passos

Também não é preciso criar manualmente. Rode **`/init`** dentro do `gemini` — ele analisa o codebase e gera um `GEMINI.md` inicial sob medida, detectando build, testes e padrões.

## 10.2. Importando outros arquivos

O `GEMINI.md` suporta imports com a mesma sintaxe `@caminho/para/arquivo`:

```
See @README.md for project overview
See @package.json for available commands

# Additional Instructions
  - Git workflow: @docs/git-instructions.md
  - Personal overrides: @~/.gemini/my-project-instructions.md
```

## 10.3. Hierarquia (memória hierárquica)

| Local                               | Propósito                                                                                      |
|-------------------------------------|-----------------------------------------------------------------------------------------------|
| Home global (`~/.gemini/GEMINI.md`) | Aplica-se globalmente a todas as suas sessões do Gemini                                        |
| Raiz do projeto (`./GEMINI.md`)     | Aplica-se ao projeto. Pode ser compartilhado com a equipe via Git                             |
| Diretórios pais / filhos            | O Gemini concatena os `GEMINI.md` da árvore — pais (monorepo) e subdiretórios carregados conforme o diretório de trabalho |

- Use **`/memory show`** para ver o conteúdo concatenado de todos os `GEMINI.md` carregados.
- Use **`/memory refresh`** depois de editar um `GEMINI.md` para recarregá-lo sem reiniciar.
- Use **`/memory list`** para ver os caminhos dos `GEMINI.md` ativos.
- O nome do arquivo é configurável via `context.fileName` (ou `contextFileName`) no `settings.json`, caso queira usar outro nome.

> **Override pessoal (≈ `CLAUDE.local.md`):** o Gemini não tem um `GEMINI.local.md` oficial, mas você obtém o mesmo efeito colocando overrides no `~/.gemini/GEMINI.md` (nível usuário) ou adicionando um `GEMINI.md` local ao `.gitignore`.

## 10.4. O que incluir / o que evitar / tratar como código

As mesmas listas valem **integralmente** para o `GEMINI.md`:

- **Incluir (alto valor):** stack e versões exatas, estrutura de pastas, comandos de build/run/test, regras inegociáveis, padrões proibidos, workflow de branching/PR.
- **Evitar:** segredos/credenciais (nunca!), regras já impostas por linters, blocos enormes de docs que o agente pode consultar sozinho, excesso de instruções.
- **Tratar como código:** versionar no Git, revisar quando o agente se comporta mal, podar regras obsoletas, usar ênfase ("IMPORTANT"/"YOU MUST") para regras críticas. O arquivo ganha valor com o refino contínuo.

# 11. Configurações do Claude Code (Claude)

As configurações do Claude Code existem para dar a desenvolvedores e organizações controle programático sobre o comportamento do Claude Code — o que ele tem permissão de fazer, do que é impedido, como interage com seu codebase e como se integra a ferramentas externas. Pense nisso como o "painel de controle" que fica entre as capacidades de IA do Claude e seu ambiente de desenvolvimento real.

## 11.1. Abordagem 1: O comando /config (UI interativa)

Esta é a forma mais amigável para iniciantes de controlar o Claude Code. Ao rodar `/config` dentro do REPL, abre-se uma interface de Configurações em abas direto no terminal — um balcão único para ver o status e alterar opções de configuração sem mexer em nenhum arquivo manualmente.

O `/config` funciona apenas no terminal (CLI). Na extensão do VSCode, ele não está disponível.

Alternativas para configurar no VSCode:

- Configurações nativas do VSCode — `Ctrl+,` → Extensions → Claude Code
- Editar diretamente o `~/.claude/settings.json` (compartilhado entre CLI e extensão)
- Digitar `/` no prompt do chat → selecionar "General Config" para abrir as configurações do VSCode

O `~/.claude/settings.json` é a forma mais universal — qualquer mudança feita lá vale tanto para o terminal quanto para a extensão do VSCode.

## 11.2. Abordagem 2: Arquivos settings.json (configuração persistente)

Referência: https://code.claude.com/docs/en/settings

Esta é a abordagem mais poderosa e mais "adequada" — arquivos JSON estruturados em diferentes escopos que persistem entre sessões. É aqui que você define sua configuração de fato. O arquivo `settings.json` é o mecanismo oficial para configurar o Claude Code por meio de configurações hierárquicas.

Os arquivos e seus escopos:

| Escopo  | Local                         | Propósito                                                                                                                                                                                                                            |
|---------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Managed | `managed-settings.json`       | Mantido dentro da pasta de instalação do Claude Code. Controlado por administradores de sistema. Aplica-se a todos na máquina. Não pode ser alterado pelos usuários. Frequentemente usado em ambientes corporativos. Pense nisso como regras de nível organizacional. |
| User    | `~/.claude/settings.json`     | Mantido dentro do diretório home do usuário. Aplica-se a todos os projetos em que você trabalha. Afeta só você. Não compartilhado com colegas. Ideal para preferências pessoais.                                                     |
| Project | `.claude/settings.json`       | Salvo dentro do diretório do projeto. Compartilhado com todos que trabalham nesse projeto. Geralmente commitado no Git. Útil quando equipes querem configurações consistentes.                                                       |
| Local   | `.claude/settings.local.json` | Salvo dentro do diretório do projeto. Existe apenas na sua máquina para um projeto específico. Não compartilhado. Automaticamente ignorado pelo Git. Perfeito para mudanças temporárias ou experimentais.                            |

### 11.2.1. Qual configuração prevalece? (Ordem de prioridade)

Quando a mesma configuração existe em vários níveis, a mais específica sempre vence. Por exemplo, se um recurso é permitido nas suas configurações pessoais, mas bloqueado nas de projeto, a regra de projeto será aplicada.

---

**Managed** — Prioridade mais alta — não pode ser sobreposta por nada

**Command Line Args** — Overrides temporários apenas para a sessão atual

**Local** — Suas regras pessoais para este repositório específico

**Project** — Regras compartilhadas pela equipe, commitadas no repositório

**User** — Prioridade mais baixa — seus padrões globais

### 11.2.2. Uma estrutura típica de settings.json

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

# 12. Configurações do Gemini CLI (Gemini)

A mesma ideia de "painel de controle" existe no Gemini CLI, com escopos hierárquicos de `settings.json` em pastas `.gemini/`.

## 12.1. Abordagem 1: O comando /settings (UI interativa)

Equivalente direto do `/config`. Rode **`/settings`** dentro do REPL para abrir um editor de configurações amigável no terminal, que altera o `.gemini/settings.json` por você sem editar JSON na mão. Controla tema, modo de aprovação, MCP, telemetria, etc.

## 12.2. Abordagem 2: Arquivos settings.json (configuração persistente)

Referência: https://google-gemini.github.io/gemini-cli/docs/get-started/configuration.html

Arquivos JSON estruturados em diferentes escopos. Os escopos do Gemini (note os nomes ligeiramente diferentes):

| Escopo (Gemini) | Local                                | Propósito                                                                                                  |
|-----------------|--------------------------------------|------------------------------------------------------------------------------------------------------------|
| System / Managed| `/etc/gemini-cli/settings.json` (ou caminho de instalação gerenciado) | Controlado por administradores; aplica-se a todos na máquina. Regras de nível organizacional. |
| User            | `~/.gemini/settings.json`            | Suas preferências pessoais, válidas em todos os projetos.                                                  |
| Workspace/Project | `<projeto>/.gemini/settings.json`  | Compartilhado com a equipe, geralmente commitado no Git.                                                   |

> ⚠️ **Diferença em relação ao Claude:** o Gemini CLI usa o termo **workspace** em vez de "project", e não tem por padrão um arquivo `settings.local.json` separado e auto-ignorado pelo Git (como o `.claude/settings.local.json`). Para overrides locais não compartilhados, mantenha o `~/.gemini/settings.json` (nível usuário) ou adicione o `.gemini/settings.json` ao `.gitignore`.

### 12.2.1. Qual configuração prevalece? (Ordem de prioridade)

Mesma lógica do Claude: a camada mais específica vence, e o Gemini faz **merge** das camadas (system → user → workspace), com argumentos de linha de comando como overrides temporários da sessão:

- **System/Managed** — prioridade mais alta, não pode ser sobreposta.
- **Command Line Args** (`--yolo`, `--model`, etc.) — overrides temporários da sessão.
- **Workspace** — regras do projeto, commitadas no repositório.
- **User** — prioridade mais baixa, seus padrões globais.

### 12.2.2. Uma estrutura típica de settings.json

```json
{
  "general": {
    "defaultApprovalMode": "default"
  },
  "ui": {
    "theme": "Default"
  },
  "tools": {
    "autoApprovedTools": ["read_file", "list_directory"],
    "exclude": ["run_shell_command(rm -rf)"]
  },
  "mcpServers": {
    "context7": {
      "httpUrl": "https://mcp.context7.com/mcp"
    }
  },
  "telemetry": {
    "enabled": false
  }
}
```

(As chaves exatas mudam entre versões; consulte a referência de configuração linkada acima.)

# 13. /permissions (Claude)

## 13.1. Permissões no Claude Code

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

### 13.1.1. Definindo regras de permissão

As regras seguem um padrão simples: **Tool ou Tool(specifier)**

#### 13.1.1.1. Casar com tudo

```
Bash  →  permite todos os comandos bash
```

`Bash(*)` é equivalente a `Bash` e casa com todos os comandos Bash.

#### 13.1.1.2. Casar com algo específico

```
Bash(npm run build)         →  apenas este comando exato
Read(./.env)                →  apenas este arquivo específico
WebFetch(domain:github.com) →  apenas requisições para github.com
```

#### 13.1.1.3. Curingas para flexibilidade

```
Bash(npm run *)      →  qualquer comando npm run
Bash(git * main)     →  git checkout main, git merge main, etc.
```

#### 13.1.1.4. Um exemplo do mundo real

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

# 14. /permissions (Gemini)

⚠️ **O Gemini CLI não tem um comando `/permissions` interativo idêntico.** O gerenciamento de permissões é feito principalmente pelo bloco `tools` no `settings.json` (editável também pela UI do `/settings`).

## 14.1. Definindo regras de permissão no Gemini

O equivalente prático usa estas chaves dentro de `tools`:

- **`tools.core`** (ou `coreTools`) — lista branca: restringe quais ferramentas embutidas ficam disponíveis.
- **`tools.exclude`** (ou `excludeTools`) — lista negra: remove ferramentas/comandos específicos (equivalente ao `deny` do Claude).
- **`tools.autoApprovedTools`** — ferramentas auto-aprovadas sem pedir confirmação (equivalente ao `allow` do Claude). Adicionar `"shell"` aqui auto-aprova **todos** os comandos de shell.

As ferramentas embutidas têm nomes como `read_file`, `write_file`, `replace`, `list_directory`, `run_shell_command`, `web_fetch`, etc. (em vez de `Bash`, `Read`, `WebFetch` do Claude).

#### 14.1.0.1. Casar com algo específico (allow/deny por comando de shell)

O Gemini permite restringir comandos de shell por prefixo/argumento dentro de `run_shell_command(...)`:

```json
{
  "tools": {
    "autoApprovedTools": [
      "run_shell_command(npm run)",
      "run_shell_command(git commit)",
      "read_file",
      "list_directory"
    ],
    "exclude": [
      "run_shell_command(git push)",
      "run_shell_command(curl)",
      "run_shell_command(rm -rf)"
    ]
  }
}
```

#### 14.1.0.2. Exemplo do mundo real (o mesmo do Claude)

"Pode rodar testes e commitar, mas nunca dar push": coloque `run_shell_command(npm run)` e `run_shell_command(git commit)` em `autoApprovedTools` e `run_shell_command(git push)` em `exclude`.

#### 14.1.0.3. Aprovação dinâmica na sessão

Quando o Gemini pede confirmação para uma ferramenta, o diálogo costuma oferecer "Yes, always for this command" — escolher isso adiciona a regra de auto-aprovação dali em diante (análogo a aceitar no diálogo do Claude). Veja também a discussão sobre auto-allow: https://github.com/google-gemini/gemini-cli/discussions/26966

# 15. /status (Claude)

Mostra todas as fontes de configuração ativas e suas origens (managed, user, project). Esta é sua ferramenta de debug quando uma configuração não parece estar funcionando — ela diz exatamente qual camada está sobrepondo o quê.

Com esse comando dá para ver de qual arquivo/lugar estão sendo buscadas as configurações aplicadas à sessão atual.

# 16. /status (Gemini)

⚠️ **O Gemini CLI não tem um `/status` único** que liste todas as fontes de configuração com suas origens (managed/user/workspace). Para alcançar o mesmo resultado de debug "de onde vem cada config", combine alguns comandos:

- **`/settings`** — abre o editor de configurações, mostrando os valores efetivos (resultado do merge das camadas).
- **`/memory show`** e **`/memory list`** — mostram qual conteúdo de `GEMINI.md` está carregado e de quais arquivos/caminhos.
- **`/mcp`** — mostra quais servidores MCP estão configurados e conectados.
- **`/tools`** — lista as ferramentas atualmente disponíveis (reflete allow/exclude aplicados).
- **`/about`** — versão e informações do ambiente.

Para inspeção de baixo nível de "qual camada venceu", abra manualmente os três arquivos: `~/.gemini/settings.json` (user), `<projeto>/.gemini/settings.json` (workspace) e o de sistema/managed.

# 17. /usage (Claude)

Permite ver o uso consumido e o limite de uso para o dia/semana.

# 18. /usage (Gemini)

O equivalente mais próximo é **`/stats`**, que mostra o uso de tokens da sessão, economia obtida por cache de tokens e a duração da sessão.

⚠️ **Diferenças importantes:**
- O `/stats` é focado na **sessão atual**, não em limites diários/semanais de plano como o `/usage` do Claude.
- Os limites de quota do Gemini dependem do método de autenticação (login Google gratuito, chave de API paga via Google AI Studio, ou Vertex AI) e não são exibidos por um comando único de "uso vs. limite". Para acompanhamento agregado de tokens/custos entre sessões, existem utilitários da comunidade, como o *Gemini CLI Token Usage Tracker* (https://github.com/rmedranollamas/geminiusage), que fazem parsing dos logs de sessão.

# 19. Output Style (Claude)

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

## 19.1. Crie um Output Style personalizado no Claude Code

### 19.1.1. O que é um Output Style personalizado?

Um output style personalizado permite controlar como o Claude responde. Você define instruções em um pequeno arquivo Markdown. Essas instruções são adicionadas automaticamente ao system prompt do Claude. Isso ajuda a manter as respostas consistentes entre sessões.

### 19.1.2. Estrutura de um Output Style personalizado

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

### 19.1.3. Onde salvar seus arquivos de estilo

Você pode salvar seus arquivos de estilo em dois locais:

**Nível de usuário** → `~/.claude/output-styles/`
Isso aplica o estilo em todos os seus projetos. É como uma configuração global no seu celular — funciona em todo lugar.

**Nível de projeto** → `.claude/output-styles/`
Isso aplica o estilo apenas a um projeto específico. É como uma regra que só vale dentro de uma sala de aula.

### 19.1.4. Casos de uso práticos

**Concise Reviewer** — Um estilo que diz ao Claude para dar comentários de revisão de código curtos e diretos, sem explicação extra.

**Beginner-Friendly Helper** — Um estilo em que o Claude explica tudo passo a passo usando palavras simples e analogias.

**Strict Linter** — Um estilo em que o Claude só aponta problemas de código e sugere correções, sem nenhuma conversa casual.

# 20. Output Style (Gemini)

⚠️ **O Gemini CLI não tem um seletor de "Output Styles" embutido** (Default/Explanatory/Learning) como o Claude. Mas você alcança o mesmo resultado — controlar a "personalidade" e o modo de comunicação — de duas formas:

## 20.1. Via GEMINI.md (a forma mais simples e portável)

Coloque as instruções de estilo no seu `GEMINI.md` (global em `~/.gemini/GEMINI.md` para valer em todos os projetos, ou no projeto para um estilo específico). Como o `GEMINI.md` é injetado em toda conversa, ele funciona exatamente como um output style persistente:

```markdown
# Estilo de comunicação

- Sempre explique em linguagem amigável para iniciantes, passo a passo, com analogias.
- Foque em desenvolvimento backend.
- Para revisões de código: seja conciso e direto, sem conversa casual.
```

Para reproduzir os três estilos do Claude:
- **Default (conciso):** "Seja conciso e eficiente, com explicações mínimas."
- **Explanatory:** "Após cada mudança, adicione um bloco curto 'Insight' explicando por que fez aquelas escolhas."
- **Learning:** "Em vez de implementar trechos pequenos, deixe marcadores `TODO(human)` e peça para eu preencher."

## 20.2. Via override do system prompt (`GEMINI_SYSTEM_MD`)

O Gemini CLI permite **substituir totalmente o system prompt** apontando a variável de ambiente `GEMINI_SYSTEM_MD` para um arquivo Markdown:

```bash
export GEMINI_SYSTEM_MD=~/.gemini/system-prompts/concise-reviewer.md
```

Isso é o análogo mais próximo de "salvar um arquivo de output style e ativá-lo" — você mantém vários arquivos de estilo e alterna trocando a variável. Diferente do Claude (que *adiciona* o estilo ao system prompt), aqui você *substitui* o prompt de sistema, então inclua as instruções essenciais de comportamento de agente no próprio arquivo.

### 20.2.1. Onde guardar seus "estilos"

- **Nível de usuário:** `~/.gemini/GEMINI.md` ou arquivos em `~/.gemini/system-prompts/`.
- **Nível de projeto:** `<projeto>/.gemini/GEMINI.md`.

# 21. /effort (Claude)

Define o nível de esforço para `??`.
(`max` (apenas esta sessão): Capacidade máxima com o raciocínio mais profundo)

# 22. /effort (Gemini)

⚠️ **O Gemini CLI não tem um comando `/effort`.** O análogo de "quanto raciocínio aplicar" é controlado de duas maneiras:

- **Escolha de modelo:** use um modelo Pro (Gemini 3 Pro / 2.5 Pro) para raciocínio mais profundo — equivalente a "effort alto" — e um Flash para respostas rápidas/baratas. Troque com `/model` ou `--model`.
- **Thinking budget (orçamento de raciocínio):** os modelos Gemini suportam "thinking"/reasoning configurável. Onde exposto, isso é ajustado nas configurações do modelo/API (ex.: parâmetro de thinking budget) — é o equivalente mais próximo do `max`/effort do Claude. Não há, porém, um seletor de "max só nesta sessão" tão direto quanto o `/effort`.

# 23. Statelessness e a ilusão da conversa contínua (Claude)

O Claude é stateless: cada requisição é independente, sem memória entre chamadas. O modelo em si não "lembra" da conversa anterior.

Para simular continuidade, a cada nova pergunta o cliente (Claude Code, app, API) reenvia toda a janela de contexto — system prompt, mensagens anteriores, respostas, resultados de ferramentas, arquivos lidos — junto com a nova pergunta.

Consequências práticas:

- O custo cresce com a conversa: cada turno reprocessa tudo que veio antes (daí o prompt caching, que reaproveita prefixos já vistos).
- O limite de contexto é finito: quando enche, partes antigas são resumidas ou descartadas.
- Sem "estado oculto": tudo que o modelo sabe sobre a conversa precisa estar visível nos tokens enviados — por isso existem mecanismos externos como arquivos de memória, CLAUDE.md e ferramentas para "lembrar" entre sessões.

Em resumo: a ilusão de diálogo contínuo é construída por reenvio, não por persistência interna do modelo.

# 24. Statelessness e a ilusão da conversa contínua (Gemini)

**Isso vale igualmente para o Gemini** — não é um detalhe do Claude, e sim de como LLMs funcionam. O Gemini também é stateless: cada chamada à API reenvia toda a janela de contexto (system prompt + `GEMINI.md` + histórico + resultados de ferramentas + arquivos lidos) junto com a nova pergunta.

Consequências práticas idênticas, com nuances do Gemini:

- **Custo cresce com a conversa:** o Gemini CLI usa **context caching** (cache de tokens) para reaproveitar prefixos já vistos — o `/stats` mostra a economia obtida com cache.
- **Limite de contexto finito, porém grande:** os modelos Pro têm janela de **1 milhão de tokens**, bem maior que o típico do Claude; ainda assim, quando aperta, o Gemini comprime (via `/compress` ou auto-compressão) o histórico antigo.
- **Sem estado oculto:** tudo precisa estar nos tokens enviados — daí os mecanismos externos `GEMINI.md`, `/memory`, `/chat save` e checkpointing para "lembrar" entre sessões.

# 25. /context (Claude)

Mostra o que está usando espaço na janela de contexto no momento. Ajuda a entender por que o contexto enche rápido.

> *Resposta do Claude: Um contexto grande significa mais tokens para processar e menor eficiência — use sessões novas para manter velocidade e precisão.*

## 25.1. O que acontece quando o contexto enche?

- O Claude gerencia o espaço automaticamente.
- Primeiro, ele remove saídas de ferramentas mais antigas.
- Se precisar de mais espaço, ele resume partes da conversa usando o processo de compactação.
- Coisas importantes, como seus pedidos e trechos de código-chave, normalmente são mantidas.
- Instruções muito antigas ou detalhadas podem ser encurtadas ou perdidas.

# 26. /context (Gemini)

⚠️ **O Gemini CLI não tem um comando `/context`** que detalhe o que ocupa a janela de contexto. O equivalente prático:

- O **rodapé (footer)** do Gemini CLI exibe continuamente a contagem/percentual de tokens usados — é o seu "medidor de contexto" sempre visível.
- **`/stats`** mostra uso de tokens, cache e duração da sessão — o resumo numérico mais próximo do `/context`.
- **`/memory show`** revela quanto contexto vem dos arquivos `GEMINI.md` (uma fonte comum de "contexto cheio").

## 26.1. O que acontece quando o contexto enche?

Comportamento análogo:
- O Gemini gerencia o espaço automaticamente e, ao se aproximar do limite, **comprime** o histórico antigo em um resumo (mesma ideia da compactação do Claude — ver `/compress`).
- Seus pedidos e trechos de código-chave tendem a ser preservados; instruções muito antigas podem ser encurtadas.
- Recomendação igual: inicie sessões novas (ou `/compress`) para manter velocidade e precisão.

# 27. /compact (Claude)

Você pode orientar o Claude durante a compactação:

- Adicione uma seção "Compact Instructions" dentro do CLAUDE.md.
- Ou rode um comando como:

  ```
  /compact "make sure to retain security related instructions"
  ```

Isso diz ao Claude qual informação é mais importante manter.

Sempre use o CLAUDE.md para regras importantes. Não dependa apenas do histórico do chat para instruções de longo prazo. Isso garante que regras importantes permaneçam disponíveis mesmo após a compactação ou entre sessões.

Exemplos de regras persistentes: padrões de código, estrutura de pastas, convenções de nomeação e decisões de arquitetura.

# 28. /compact → /compress (Gemini)

O equivalente direto é **`/compress`**: ele substitui todo o contexto do chat por um resumo de alto nível, economizando tokens para tarefas futuras enquanto preserva o que aconteceu.

⚠️ **Diferença:** diferente do `/compact "instruções..."` do Claude, o `/compress` do Gemini **não aceita, por padrão, instruções customizadas** de "o que manter". Para obter o mesmo efeito:

- Antes de comprimir, garanta que as regras importantes estejam no **`GEMINI.md`** (não dependa só do histórico do chat) — assim elas sobrevivem à compressão e às trocas de sessão. Exemplos: padrões de código, estrutura de pastas, convenções de nomeação, decisões de arquitetura.
- Opcionalmente, peça em linguagem natural um resumo focado *antes* de comprimir: *"Resuma o estado atual mantendo apenas os resultados de teste e o plano de implementação"* — e então rode `/compress`.

# 29. /clear (Claude)

Limpa os tokens da janela de contexto (`/context`) = limpa a memória de tokens para a sessão atual.

Qual a diferença entre `/clear` e começar uma sessão nova? R: Usando `/clear` preservamos as permissões fornecidas e os MCPs.

# 30. /clear (Gemini)

⚠️ **Atenção: o `/clear` do Gemini é diferente do `/clear` do Claude!**

- No **Gemini**, **`/clear`** (atalho `Ctrl+L`) apenas **limpa a tela do terminal** — ele **não** apaga o contexto/histórico da conversa. A conversa continua intacta.
- Para de fato "limpar a memória de tokens da sessão" (o que o `/clear` do Claude faz), use **`/compress`** (condensa o contexto num resumo) ou **inicie uma nova sessão**.

Resumo do mapeamento:

| Quero...                                   | Claude     | Gemini                         |
|--------------------------------------------|------------|--------------------------------|
| Limpar a tela                              | —          | `/clear` (`Ctrl+L`)            |
| Zerar/condensar o contexto da sessão       | `/clear`   | `/compress` ou nova sessão     |

Assim como no Claude, **iniciar uma nova sessão preserva MCPs e configurações** (que vivem no `settings.json`), pois eles não dependem do histórico do chat.

# 31. /rename (Claude)

Atribui um nome à sessão atual. Ela poderá ser recarregada depois com o comando abaixo (ou, por exemplo, via CLI: `claude --resume teste-nome`).

## 31.1. Dúvida #01

Vamos supor que eu converse 300 kB de conversa contigo numa sessão. Então, chegado esse ponto, eu rodo o `/rename um-nome-de-sessao`, e continuamos conversando. Quando eu executar o `/resume um-nome-de-sessao`, vai trazer todos os 300 kB iniciais + o que conversamos depois, ou só o que conversamos depois?

R: O `/rename` apenas troca o rótulo da sessão — não corta, não bifurca, não cria uma nova sessão. A transcrição continua sendo um único arquivo JSONL contínuo no disco. Então, quando você executar `/resume um-nome-de-sessao`, virá tudo: os 300 kB iniciais + tudo que foi conversado depois do rename. O nome é só um identificador amigável para você encontrar a sessão na lista do `/resume`.

# 32. /rename → /chat save (Gemini)

O equivalente para "dar um nome a uma sessão para recarregar depois" é **`/chat save <tag>`**, que salva o estado atual da conversa sob uma tag identificadora. Você recarrega com **`/chat resume <tag>`** e lista os pontos salvos com **`/chat list`** (e remove com `/chat delete <tag>`).

## 32.1. Diferença em relação ao `/rename` do Claude

⚠️ A semântica é um pouco diferente: o `/chat save` cria um **checkpoint nomeado** (snapshot) da conversa naquele instante, e não apenas "renomeia o arquivo contínuo da sessão".

Respondendo à mesma **Dúvida #01** no mundo Gemini: se você conversa 300 kB, roda `/chat save um-nome`, continua conversando e depois faz `/chat resume um-nome`, você volta ao estado **no momento do save** (os 300 kB), e não necessariamente ao que veio depois — a menos que você salve novamente. Pense no `/chat save` como "marcar um ponto de restauração nomeado", enquanto o `/rename` do Claude é só um rótulo amigável para uma transcrição única e contínua.

Para apenas continuar de onde parou (sem nomear), veja a seção `/resume (Gemini)` abaixo.

# 33. /resume (Claude)

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

# 34. /resume → /chat resume (Gemini)

No Gemini, retomar uma conversa é feito por **`/chat`** (não por uma flag `--continue`):

| Quero...                                | Claude                       | Gemini                          |
|-----------------------------------------|------------------------------|---------------------------------|
| Salvar/nomear ponto da conversa         | `/rename`                    | `/chat save <tag>`              |
| Listar conversas salvas                 | `/resume` (lista)            | `/chat list`                    |
| Retomar uma conversa específica         | `claude --resume <id>`       | `/chat resume <tag>`            |
| Continuar a última sessão               | `claude -c` / `--continue`   | `/chat resume <tag>` (use uma tag fixa, ex. `last`) |

⚠️ **Diferenças:**
- O Gemini **não tem** uma flag `--continue`/`-c` de inicialização equivalente que retome automaticamente a última sessão. O fluxo é: você salva pontos com `/chat save` e retoma com `/chat resume`. Para "continuar de ontem", crie o hábito de salvar uma tag antes de sair.
- **Permissões/aprovações com escopo de sessão também são resetadas** ao retomar — você reaprovará ferramentas, igual ao Claude.
- Os saves de `/chat` ficam atrelados ao seu armazenamento local do Gemini (em `~/.gemini/tmp/...`); a separação rígida "só vejo sessões desta pasta" do Claude não é garantida da mesma forma — use tags descritivas por projeto.

> **Relacionado (checkpointing):** para retomar **junto com o estado dos arquivos** (não só a conversa), veja o `/restore` na seção `/rewind (Gemini)`.

# 35. claude --continue --fork-session (Claude)

(Ver `/resume` acima.)

**Bifurque uma sessão (experimente um caminho diferente)**

E se você quiser experimentar uma abordagem diferente — sem bagunçar sua sessão atual? É isso que o fork faz.

```
claude --continue --fork-session
```

Isso cria uma nova sessão, mas copia todo o seu histórico de conversa até aquele ponto. A sessão original permanece intocada. É como fotocopiar seu caderno e escrever na cópia. A original permanece limpa. O fork segue em sua própria direção. Assim como o resume, sessões bifurcadas também não herdam permissões com escopo de sessão.

## 35.1. Como o Claude Code gerencia sessões entre branches do Git

Cada conversa do Claude Code é uma sessão atrelada ao seu diretório atual — não a uma branch ou a um arquivo.

- Toda conversa que você inicia no Claude Code está ligada à pasta em que você está trabalhando
- Quando você retoma uma sessão, o Claude só mostra as sessões daquele mesmo diretório
- Trocar de branch não inicia uma nova sessão — você permanece na mesma conversa

O Claude sempre lê os arquivos da sua branch Git ativa. Se você trocar de branch, ele imediatamente passa a trabalhar com o código da nova branch, enquanto seu histórico de conversa permanece inalterado. Isso significa que o Claude ainda lembra de tudo que vocês discutiram antes, mesmo que os arquivos subjacentes sejam diferentes.

Como as sessões são baseadas em diretório, você pode rodar várias sessões do Claude em paralelo usando Git worktrees. Worktrees criam pastas separadas para diferentes branches, permitindo que cada branch tenha sua própria sessão independente do Claude.

# 36. fork de sessão → conversational branching (Gemini)

O Gemini chama esse recurso de **"conversational branching"** e o implementa via `/chat save` + `/chat resume`:

**Como bifurcar (experimentar um caminho diferente):**
1. No ponto a partir do qual quer ramificar, rode `/chat save base`.
2. Continue explorando a abordagem A.
3. Para tentar a abordagem B do mesmo ponto, rode `/chat resume base` (volta ao ponto salvo) e siga noutra direção.

Cada save é como uma "fotocópia do caderno": você pode partir do mesmo ponto várias vezes, sem bagunçar as outras ramificações. Igual ao Claude, conversas retomadas/bifurcadas **não herdam** permissões com escopo de sessão.

⚠️ **Diferença:** não há flag `--fork-session` de inicialização; o fork é feito dentro do REPL pelos saves nomeados.

## 36.1. Sessões e branches do Git no Gemini

O modelo é parecido: a conversa do Gemini está atrelada ao diretório de trabalho, não à branch. Trocar de branch do Git não inicia uma nova conversa, e o agente passa a ler os arquivos da nova branch imediatamente, mantendo o histórico de conversa.

⚠️ **Worktrees:** diferente do Claude (que tem a flag `--worktree`/`-w`), o Gemini CLI **não tem um gerenciamento de worktrees embutido**. Para rodar sessões paralelas por branch, crie os worktrees manualmente com `git worktree add ../feature-x feature-x` e rode um `gemini` em cada pasta. Veja a seção *Git (Gemini)*.

# 37. /rewind → /restore (Claude)

Ou pressione `Esc` duas vezes, quando o atalho estiver disponível. O rewind permite voltar a um ponto anterior e escolher o que fazer.

Obs.: temos essa funcionalidade disponível mesmo quando saímos do aplicativo e voltamos depois para a sessão em questão.

## 37.1. Como fazer rewind

Pressione `Esc` duas vezes ou use o comando `/rewind` para abrir o menu de rewind. Você então escolhe um checkpoint e decide o que restaurar:

- **Restore Code Only** — Reverte alterações nos arquivos, mantém a conversa. Bom quando o código deu errado mas o contexto ainda é útil.
- **Restore Conversation Only** — Volta o chat, mantém o código. Bom quando você quer re-promptar de forma diferente sem descartar alterações que gostou.
- **Restore Both** — Reset completo. Código e conversa voltam juntos.
- **Summarize from here** — Não restaura nada. Em vez disso, condensa as mensagens a partir daquele ponto enquanto mantém o contexto anterior intacto — uma alternativa cirúrgica ao `/compact` que comprime apenas a parte que está consumindo espaço.

## 37.2. O que os checkpoints NÃO rastreiam

Isso é crítico de entender: o checkpointing não rastreia arquivos modificados por comandos bash. Se o Claude executar `rm file.txt`, `mv old.txt new.txt` ou `cp source.txt dest.txt` — essas modificações não podem ser desfeitas via rewind. Apenas edições diretas feitas pelas ferramentas de edição de arquivos do Claude são rastreadas.

Além disso, alterações manuais feitas fora do Claude Code não são capturadas, e os checkpoints expiram após 30 dias.

# 38. /rewind → /restore (Gemini)

O equivalente é o **checkpointing** do Gemini CLI, acionado pelo comando **`/restore`**.

## 38.1. Como funciona

Quando você aprova uma ferramenta que modifica o sistema de arquivos (`write_file` ou `replace`), o Gemini cria automaticamente um **checkpoint** contendo um snapshot Git (em um shadow repo) **e** o histórico da conversa. Restaurar reverte os arquivos do projeto ao estado capturado **e** restaura a conversa no CLI.

- Rode **`/restore`** para ver a lista de checkpoints disponíveis (nomeados por timestamp + arquivo + ferramenta, ex.: `2025-06-22T10-00-00_000Z-my-file.txt-write_file`).
- Rode **`/restore <id>`** para reverter ao checkpoint escolhido.

⚠️ **Pode ser preciso habilitar:** o checkpointing às vezes não vem ligado por padrão — habilite com `gemini --checkpointing` ou pela config (`general.checkpointing.enabled: true` / chave equivalente na sua versão).

## 38.2. Diferença em relação ao `/rewind`

- O `/restore` do Gemini é essencialmente **"Restore Both"** (código + conversa juntos). Ele **não** oferece, num menu único, as opções separadas do Claude:
  - *Restore Code Only* / *Restore Conversation Only* — não há toggles dedicados; o restore é combinado.
  - *Summarize from here* — não existe como opção do restore; use **`/compress`** para o efeito de condensar.
- O atalho "Esc duas vezes" abre o menu de rewind no Claude; no Gemini, use o comando `/restore`.

## 38.3. O que os checkpoints NÃO rastreiam

A mesma limitação crítica vale: o checkpointing captura apenas as edições feitas pelas **ferramentas de arquivo** do agente (`write_file`/`replace`). Modificações feitas via `run_shell_command` (ex.: `rm`, `mv`, `cp`) **não** são revertíveis pelo `/restore`, e alterações manuais fora do CLI também não são capturadas.

**Armazenamento:** todos os dados de checkpoint (snapshot Git + histórico) ficam localmente em `~/.gemini/tmp/<project_hash>/checkpoints`.

# 39. Histórico (Claude)

Dentro de:

```
~/.claude/projects
```

ficam todos os históricos das conversas/sessões em formato `.jsonl`. Daria para procurar algo com `grep` na pasta.

Obs.: após 20 dias, cada sessão individual é deletada.

# 40. Histórico (Gemini)

No Gemini CLI, os artefatos de sessão (logs, checkpoints, chats salvos) ficam sob:

```
~/.gemini/tmp/<project_hash>/
```

- **`checkpoints/`** — snapshots Git + histórico de conversa (ver `/restore`).
- **Logs/saves de chat** — os pontos criados por `/chat save` e os logs de sessão. O formato é JSON; dá para inspecionar/`grep` na pasta.

⚠️ **Diferenças:**
- O Gemini organiza por **hash do projeto**, não por caminho legível como `~/.claude/projects/<projeto>`.
- A política de retenção/expiração não é necessariamente "20 dias" como no Claude — os dados ficam em `tmp` e podem ser limpos pelo sistema ou pelo próprio CLI; não conte com uma janela fixa. Para preservar uma conversa importante, use `/chat save` (ou `/chat share <arquivo>` para exportar para Markdown/JSON num local permanente).

# 41. Os hábitos de sessão do desenvolvedor esperto (Claude)

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

# 42. Os hábitos de sessão do desenvolvedor esperto (Gemini)

Os mesmos hábitos, com os comandos do Gemini:

**Hábito 1: Limpe/condense entre tarefas**
Terminou um bug, vai começar uma feature? Rode **`/compress`** (não o `/clear`, que no Gemini só limpa a tela) — ou inicie uma sessão nova. Não deixe a conversa antiga poluir a próxima tarefa.

**Hábito 2: Comprima em pontos de quebra naturais**
Não espere a auto-compressão. Rode **`/compress`** quando VOCÊ decidir — após terminar uma subtarefa, antes de uma nova fase. (Lembre: o `/compress` não aceita instruções customizadas; antes dele, peça um resumo focado em linguagem natural se quiser direcionar o que manter.)

**Hábito 3: Salve/nomeie suas sessões**
Use **`/chat save payment-gateway-fix`** assim que começar um trabalho significativo, e retome com `/chat resume payment-gateway-fix`. Liste tudo com `/chat list`.

**Hábito 4: Monitore seu contexto**
Olhe o **rodapé** (mostra tokens usados) e rode **`/stats`** periodicamente. Acima de ~60% com muito trabalho pela frente? Comprima ou inicie nova sessão. (O Gemini não tem status line scriptável como o Claude — ver seção *Status Line (Gemini)*.)

**Hábito 5: Use o padrão Documentar & Limpar**
Para tarefas grandes, peça ao Gemini para escrever plano e progresso num arquivo `.md`, rode **`/compress`** (ou nova sessão), e então comece dizendo para ler esse `.md` e continuar. Contexto fresco com conhecimento preservado.

# 43. Memory (Memória) (Claude)

## 43.1. /memory

Mostra os arquivos/pastas de configuração (ex.: CLAUDE.md, rules, ...) que estão sendo considerados no contexto atual.

## 43.2. Auto Memory no Claude Code

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

### 43.2.1. Dois sistemas de memória: o livro-texto vs. o caderno

O Claude Code tem dois sistemas de memória complementares. Entender a diferença é a chave para usá-los bem.

#### 43.2.1.1. CLAUDE.md — O livro-texto (escrito por VOCÊ)

Pense no `CLAUDE.md` como um livro-texto que você escreve para o Claude. Ele contém suas regras, suas convenções, suas instruções de "faça desse jeito":

- "Use pnpm, não npm"
- "Siga o Airbnb React Style Guide"
- "Nunca modifique arquivos em /generated/ ou /dist/"
- "Rode testes com pnpm test --coverage"

Você o escreve, você o commita no Git, sua equipe toda compartilha.

#### 43.2.1.2. Auto Memory (MEMORY.md) — O caderno (escrito pelo CLAUDE)

O Auto Memory é como o caderno pessoal de um aluno. O Claude o escreve para si mesmo enquanto trabalha com você:

- "O comando de build deste projeto é pnpm build"
- "O hydration mismatch foi causado por usar o objeto window durante o SSR sem um guard com useEffect"
- "O usuário prefere custom hooks a render props para lógica compartilhada"
- "Os testes E2E usam Playwright e exigem o servidor de dev rodando na porta 5173"

Ele é armazenado localmente na sua máquina, nunca commitado no Git, e é único para o seu fluxo de trabalho pessoal.

### 43.2.2. Como o Auto Memory funciona por baixo dos panos

**Está LIGADO por padrão.** O Auto Memory vem habilitado por padrão. Você não precisa instalar nada nem acionar nenhum botão. O Claude simplesmente começa a lembrar.

### 43.2.3. Onde o Claude armazena suas anotações?

Cada projeto ganha seu próprio diretório de memória:

```
~/.claude/projects/<project>/memory/
├── MEMORY.md            # O índice principal — carregado a cada sessão
├── debugging.md         # Notas detalhadas sobre padrões de debugging
└── api-conventions.md   # Decisões de design de API
```

O caminho `<project>` é derivado do seu repositório git. Então, todas as branches, worktrees e subdiretórios dentro do mesmo repo compartilham um único diretório de memória. Pense nisso como um caderno por projeto, não por branch. Fora de um repo git? O Claude usa o diretório raiz do projeto em vez disso.

#### 43.2.3.1. Mensagens de status

Quando o Claude está interagindo com sua memória, você verá mensagens de status na interface do Claude Code:

- "Writing memory" — O Claude está salvando algo que aprendeu
- "Recalled memory" — O Claude está lendo de suas anotações salvas

Essas são suas pistas visuais de que o Auto Memory está funcionando em segundo plano.

## 43.3. O comando /memory

O comando `/memory` é seu painel de controle para tudo relacionado a memória no Claude Code. Digite-o dentro de qualquer sessão. Isso abre um seletor interativo que te mostra:

- Todos os arquivos `CLAUDE.md` atualmente carregados na sua sessão (project, user, rules, etc.)
- O toggle do Auto Memory — interruptor LIGA/DESLIGA
- Um link para abrir a pasta do auto memory — para você navegar pelo que o Claude salvou

Você também pode usar `/memory` para:

- Ligar ou desligar o auto memory
- Abrir qualquer arquivo de memória no seu editor
- Navegar pelas anotações salvas do Claude

### 43.3.1. Dizendo ao Claude o que lembrar

O Auto Memory não depende apenas do julgamento do próprio Claude. Você pode dizer ao Claude para lembrar de coisas explicitamente:

- "remember that we use pnpm, not npm"
- "save to memory that the API tests require a local Redis instance"
- "note that the staging environment uses port 3001"

## 43.4. As três camadas de memória — o quadro completo

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

## 43.5. Configurando o Auto Memory

### 43.5.1. Como alternar (toggle)

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

### 43.5.2. Diretório de memória personalizado

Quer armazenar o auto memory em outro lugar? Defina `autoMemoryDirectory` nas suas configurações de usuário ou locais:

```json
{
  "autoMemoryDirectory": "/path/to/custom/memory"
}
```

### 43.5.3. Como funciona

Apenas as primeiras 200 linhas do `MEMORY.md` são carregadas no início de cada conversa. Qualquer coisa além disso é ignorada na inicialização. Para manter as coisas eficientes, o Claude desloca informações detalhadas para arquivos separados por tópico.

Esse limite de 200 linhas se aplica apenas ao `MEMORY.md`. Arquivos como o `CLAUDE.md` são sempre carregados, independentemente do tamanho — embora mantê-los mais curtos ajude a melhorar a precisão e a consistência.

Arquivos específicos de tópico (ex.: `debugging.md`, `patterns.md`) não são carregados por padrão. O Claude os acessa apenas quando necessário, usando suas capacidades de leitura de arquivos.

Durante uma sessão, o Claude pode ler e escrever em arquivos de memória. Quando você vê mensagens como "Writing memory" ou "Recalled memory", significa que o Claude está interagindo ativamente com arquivos localizados em `~/.claude/projects/<project>/memory/`.

# 44. Memory (Memória) (Gemini)

## 44.1. /memory

No Gemini CLI, **`/memory`** é o painel da memória hierárquica baseada em `GEMINI.md`. Subcomandos:

- **`/memory show`** — mostra o conteúdo concatenado de todos os `GEMINI.md` carregados (project, user, subdirs).
- **`/memory list`** — lista os caminhos dos `GEMINI.md` ativos.
- **`/memory refresh`** — recarrega os `GEMINI.md` após edição.
- **`/memory add <texto>`** — adiciona um trecho de instrução à memória.

## 44.2. ⚠️ Diferença central: NÃO há "Auto Memory" automática

Esta é a maior diferença em relação ao Claude. O Claude Code tem **Auto Memory** — ele faz anotações *sozinho* em segundo plano (`MEMORY.md`), capturando aprendizados, decisões e preferências sem você pedir, com mensagens "Writing memory"/"Recalled memory".

**O Gemini CLI não tem esse sistema de auto-anotação automática.** A memória do Gemini é, na prática, **manual e dirigida pelo usuário**:

- `/memory add "usamos pnpm, não npm"` adiciona um fato explicitamente.
- Ou peça em linguagem natural: *"adicione ao GEMINI.md que os testes de API exigem uma instância local do Redis"* e o agente edita o `GEMINI.md`.

Como reproduzir o benefício do Auto Memory no Gemini:
- **Hábito manual:** ao fim de uma sessão, peça: *"Resuma o que aprendemos hoje (comandos de build, gotchas, preferências) e acrescente ao GEMINI.md."* Assim, na próxima sessão, o conhecimento é recarregado automaticamente (porque o `GEMINI.md` é sempre injetado).
- **Sub-agente com memória persistente:** o Gemini tem sub-agentes que podem manter memória própria entre execuções (ver seção *agents (Gemini)*) — o equivalente mais próximo de "um agente que aprende com o tempo".

## 44.3. Mapeando as três camadas de memória

| Camada (Claude)                  | Equivalente no Gemini                                                                 |
|----------------------------------|---------------------------------------------------------------------------------------|
| **CLAUDE.md** (suas instruções)  | **GEMINI.md** (hierárquico: user `~/.gemini/GEMINI.md` + project + subdirs). Compartilhado via Git. |
| **Auto Memory / MEMORY.md** (auto) | ⚠️ Sem equivalente automático. Aproxime com `/memory add` manual e memória de sub-agentes. |
| **Session Memory** (continuidade)| `/chat save`/`/chat resume` e checkpointing (`/restore`) cobrem a continuidade entre sessões. |

A configuração mais forte no Gemini: `GEMINI.md` bem mantido (regras autoritativas) + hábito de salvar aprendizados manualmente nele + `/chat save` para continuidade.

## 44.4. Diretório de memória / como funciona

- O `GEMINI.md` é sempre carregado (sem limite de 200 linhas como o `MEMORY.md` do Claude), mas mantê-lo curto melhora precisão.
- Diferente do Claude, não há "primeiras 200 linhas + arquivos de tópico carregados sob demanda" para a memória do agente. Para modularizar, use **imports `@arquivo.md`** dentro do `GEMINI.md` (carregados junto) e divida instruções por subdiretório (carregadas conforme o diretório de trabalho).
- Não há `CLAUDE_CODE_DISABLE_AUTO_MEMORY` correspondente, simplesmente porque não há auto memory para desabilitar.

# 45. Rules (Regras) (Claude)

(Obs.: operação útil para essa funcionalidade: `/memory`, citado acima.)

## 45.1. Rules no Claude Code

Imagine que seu `CLAUDE.md` cresceu para 400 linhas. Ele tem regras de React, diretrizes de API, avisos de migração de banco de dados, políticas de segurança e convenções de teste — tudo misturado. Quando o Claude está editando um componente React, ele também carrega no contexto suas regras de segurança de migração de banco. Quando está escrevendo uma query SQL, carrega seus padrões de React.

Isso é o que um desenvolvedor chamou de "saturação de prioridade" — quando tudo é alta prioridade, nada é. A atenção do Claude se dilui em instruções que não se aplicam à tarefa atual.

## 45.2. Onde as Rules vivem?

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

## 45.3. Dois tipos de regras

### 45.3.1. Regras sempre carregadas (always-loaded)

Sem frontmatter `paths`. Elas carregam na inicialização com a mesma alta prioridade do `CLAUDE.md`. Use-as para regras que se aplicam universalmente.

```markdown
# code-style.md (sem frontmatter = sempre carregada)

- Use English for all comments
- Prefer a functional approach where possible
- Use strict typing everywhere
```

### 45.3.2. Regras com escopo de path (path-scoped)

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

### 45.3.3. Rules vs CLAUDE.md — quando usar qual

| Coloque no CLAUDE.md                       | Coloque nas Rules                                       |
|--------------------------------------------|--------------------------------------------------------|
| Visão geral do projeto / stack tecnológica | Padrões de código específicos por tipo de arquivo      |
| Comandos de build e teste                  | Diretrizes específicas de framework (React, Spring, etc.) |
| Visão geral da arquitetura                 | Regras de segurança para diretórios sensíveis          |
| Convenções universais de código            | Convenções de escrita de testes                        |
| Pegadinhas comuns que afetam tudo          | Regras de segurança de migração                        |
| Workflow Git / estratégia de branching     | Diretrizes de design de API                            |

# 46. Rules (Regras) (Gemini)

⚠️ **O Gemini CLI não tem um sistema de "Rules" com frontmatter `paths` (path-scoped) embutido** como o Claude (a pasta `.claude/rules/` com regras carregadas por glob). Mas há duas formas de obter o mesmo benefício de "regras certas no contexto certo":

## 46.1. GEMINI.md hierárquico por subdiretório (o análogo mais próximo do path-scoping)

O Gemini concatena os `GEMINI.md` da árvore conforme o diretório de trabalho. Então, coloque regras específicas em `GEMINI.md` dentro das pastas relevantes:

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

Isso resolve a "saturação de prioridade" do mesmo jeito: as regras de migração só entram no contexto quando o agente está mexendo em `db/migrations/`. A diferença é que o escopo é por **subdiretório** (onde o `GEMINI.md` mora), não por **glob de padrões de arquivo** como o `paths:` do Claude.

## 46.2. Imports modulares no GEMINI.md

Mantenha o `GEMINI.md` raiz enxuto e importe arquivos temáticos com `@`:

```markdown
# Regras do projeto
@./rules/code-style.md
@./rules/testing.md
@./rules/security.md
```

⚠️ Note: imports `@` são sempre carregados (não são condicionais por path). Para condicionalidade, use a abordagem nº 1 (subdiretórios).

## 46.3. Extensões com regras/contexto

Extensões do Gemini podem empacotar contexto e instruções; para times, uma extensão compartilhada pode distribuir um conjunto de "regras" reutilizável (ver seção *Skills (Gemini)*).

### 46.3.1. Quando usar qual (mesma lógica do Claude)

| Coloque no GEMINI.md raiz                  | Coloque em GEMINI.md de subpasta / imports             |
|--------------------------------------------|--------------------------------------------------------|
| Visão geral do projeto / stack             | Padrões específicos por área de código                 |
| Comandos de build e teste                  | Diretrizes de framework (React, Spring, etc.)          |
| Visão geral da arquitetura                 | Regras de segurança para diretórios sensíveis          |
| Convenções universais de código            | Convenções de testes                                   |
| Workflow Git / branching                   | Diretrizes de design de API / migração                 |

# 47. Skills (Claude)

São semelhantes a aplicativos do celular: apenas instruções básicas ficam na memória constantemente (como os ícones dos apps do celular aparecem), e todo o resto só é executado quando chamado.

Você pode criar suas próprias skills reutilizáveis adicionando arquivos Markdown em `.claude/skills/` (nível de projeto) ou `~/.claude/skills/` (pessoal).

Por exemplo, se você criar uma skill com o nome **analyze-issue \<issue #\>**, ao digitar **/analyze-issue 123** → o Claude se comportará com base nas instruções definidas no documento da skill. Por exemplo, ele vai:

- Buscar a issue #123 do seu repositório do GitHub
- Explorar o codebase relevante
- Gerar uma especificação técnica completa

## 47.1. Construa sua própria skill

### 47.1.1. Passos para criar uma skill personalizada

#### 47.1.1.1. 1) Crie o diretório da skill

Crie um diretório para a skill em `.claude/skills/analyze-issue` (nível de projeto) ou `~/.claude/skills/analyze-issue` (pessoal).

```
mkdir -p .claude/skills/analyze-issue
```

#### 47.1.1.2. 2) Escreva um arquivo SKILL.md

Toda skill requer um arquivo SKILL.md. Este arquivo tem duas seções principais:

i) Frontmatter YAML (colocado entre linhas `---`)
- Define quando e como o Claude deve usar a skill.
- O campo `name` se torna o `/comando-de-barra`.
- A `description` ajuda o Claude a entender quando carregar a skill automaticamente.

ii) Instruções em Markdown

Contém os passos e a orientação que o Claude deve seguir quando a skill roda. Por exemplo, você pode criar um arquivo de skill em `.claude/skills/analyze-issue/SKILL.md`. Esse arquivo diz ao Claude como executar a skill analyze-issue e quando ela deve ser acionada.

#### 47.1.1.3. 3) Teste a skill

Você pode testar sua skill de duas formas diferentes:

i) Deixe o Claude usá-la automaticamente

Faça uma pergunta que case com a descrição da skill, por exemplo: `Analyze the issue 123`. Se o pedido se encaixar na skill, o Claude a carregará e usará automaticamente.

ii) Rode a skill manualmente

Você também pode acionar a skill diretamente usando seu comando de barra: `/analyze-issue 123`. Isso força o Claude a executar a skill específica que você criou.

Independentemente de como a skill é acionada, o Claude Code seguirá as instruções dentro do arquivo SKILL.md — por exemplo, ele analisa a issue 123 e gera uma especificação sobre as correções propostas.

Mais detalhes podem ser encontrados em https://code.claude.com/docs/en/skills

## 47.2. Site de referência: https://code.claude.com/docs/en/skills (tem informações importantes)

Vale ver para aprofundar. Ver exemplos salvos na pasta `./skills` deste diretório.

## 47.3. `./skills/feature-guide`: exemplo de como rodar uma skill em um sub-agente

A linha abaixo:

```
context: fork
```

especifica que a skill deve rodar em isolamento. (O subagente não tem acesso ao conteúdo da conversa principal.)

Mais detalhes em: https://code.claude.com/docs/en/skills#example-research-skill-using-explore-agent

# 48. Skills (Gemini)

O Gemini CLI tem dois conceitos que, juntos, cobrem o que o Claude chama de "Skills":

1. **Custom commands** (comandos personalizados) — o análogo direto do "skill acionada por `/comando`" (ver também a seção *commands (Gemini)*).
2. **Extensions** (extensões) — pacotes reutilizáveis que empacotam *prompts, MCP servers, custom commands, themes, hooks, sub-agents e "agent skills"* num formato instalável e compartilhável. As versões mais recentes do Gemini CLI inclusive suportam **"agent skills"** dentro de extensões.

## 48.1. Reproduzindo a skill "analyze-issue"

No Gemini, você cria um **custom command** (arquivo TOML), não um diretório `SKILL.md`. Exemplo `~/.gemini/commands/analyze-issue.toml` (ou no projeto, `<projeto>/.gemini/commands/`):

```toml
description = "Busca uma issue do GitHub, explora o codebase e gera uma especificação técnica."
prompt = """
Você é um analista de issues. Para a issue número {{args}} deste repositório:
1. Use o `gh` (via run_shell_command) para buscar os detalhes da issue.
2. Explore o codebase relevante.
3. Gere uma especificação técnica completa das correções propostas.
"""
```

- Aciona com **`/analyze-issue 123`** (o `{{args}}` recebe `123`).
- O nome do arquivo vira o nome do comando; subpastas viram namespaces (ex.: `commands/git/commit.toml` → `/git:commit`).
- Após criar/editar, rode **`/commands reload`** para recarregar sem reiniciar.

## 48.2. Diferenças em relação às Skills do Claude

- **Formato:** Gemini usa **TOML** (`commands/*.toml`) com campos `description` e `prompt`; Claude usa um **diretório com `SKILL.md`** e frontmatter YAML.
- **Descoberta automática:** as **Skills do Claude** podem ser invocadas *automaticamente* quando o pedido casa com a `description`. Os **custom commands do Gemini são acionados pelo usuário** (`/comando`). Para "descoberta automática" no Gemini, o caminho é via **sub-agentes** (que o orquestrador delega automaticamente conforme a descrição — ver *agents (Gemini)*) ou via "agent skills" empacotadas em extensões.
- **Rodar isolado (`context: fork`):** o equivalente de rodar a tarefa num contexto isolado é delegar a um **sub-agente** do Gemini (ele roda com janela de contexto e ferramentas próprias e devolve só o resumo).

Referências:
- Custom commands: https://google-gemini.github.io/gemini-cli/docs/cli/custom-commands.html
- Extensions: https://geminicli.com/docs/extensions/

# 49. commands (deprecado) (Claude)

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

# 50. commands (Gemini)

⚠️ **Importante:** no Claude, os "commands" são considerados **deprecados** (substituídos por Skills). No **Gemini CLI, os custom commands NÃO são deprecados** — são o mecanismo principal e atual de comandos personalizados.

**O que é um custom command no Gemini?**

Um arquivo **TOML** (não Markdown) contendo um `prompt` em linguagem natural, salvo numa pasta de comandos. O nome do arquivo (sem `.toml`) vira o `/comando`.

```
.gemini/commands/review.toml   →  /review
.gemini/commands/commit.toml   →  /commit
.gemini/commands/deploy.toml   →  /deploy
```

**Locais (ordem de descoberta):**
- **User (global):** `~/.gemini/commands/` — disponível em qualquer projeto.
- **Project (local):** `<projeto>/.gemini/commands/` — específico do projeto, versionável no Git.

**Campos do TOML:**
- `prompt` (obrigatório) — o prompt enviado ao modelo. Pode ser multilinha (`"""..."""`).
- `description` (opcional) — texto exibido no menu `/help`.

**Namespacing:** `<projeto>/.gemini/commands/git/commit.toml` → comando `/git:commit`.

**Argumentos:** use `{{args}}` no prompt para receber o que o usuário digitar após o comando.

**Recarregar:** após criar/editar TOMLs, rode `/commands reload`.

**Evolução / descoberta automática:** assim como no Claude, comandos são *acionados pelo usuário*. O "próximo nível" (invocação automática quando a tarefa casa com uma descrição) no Gemini vem dos **sub-agentes** e das **agent skills** em extensões — ver seções *agents (Gemini)* e *Skills (Gemini)*.

Referência: https://cloud.google.com/blog/topics/developers-practitioners/gemini-cli-custom-slash-commands

# 51. hooks (Claude)

Você já disse a alguém: "Por favor, certifique-se de trancar a porta ao sair"? A pessoa diz: "Claro, vou trancar." E na maioria dos dias, ela tranca. Mas naquele um dia, ela esquece. Agora imagine que, em vez de depender da memória dela, você instalou uma trava automática — a porta se tranca sozinha no momento em que se fecha. Sem lembrar, sem esquecer, sem torcer. Simplesmente funciona.

Essa é a diferença entre dar ao Claude Code uma instrução — e dar a ele um hook.

## 51.1. O que exatamente são hooks?

Em termos simples, hooks são comandos/scripts de shell definidos pelo usuário que rodam automaticamente em pontos específicos do ciclo de vida do Claude Code. Pense em hooks como event listeners no JavaScript — você registra um comando, e ele dispara quando um evento específico acontece.

Você define as regras, e o Claude Code as impõe — não porque a IA escolheu, mas porque o sistema está programado para executá-las. Toda vez, sem exceção.

## 51.2. Determinístico

E esta é a palavra crítica que quero que você lembre ao longo desta seção — **determinístico**. Quando você escreve algo no CLAUDE.md ou diz ao Claude "Sempre rode o formatador após editar", isso é uma sugestão. **A IA pode segui-la. Provavelmente vai. Mas não há garantia.**

Os hooks invertem isso completamente. Eles não são sugestões — são código. Eles executam com certeza, assim como um pipeline de CI roda a cada commit, lembre-se o desenvolvedor ou não.

## 51.3. Agora, qual o propósito? Por que os hooks existem?

Pense em três coisas que você gostaria de garantir ao trabalhar com um agente de codificação de IA.

### 51.3.1. Primeiro — automação
Você quer que certas ações aconteçam toda vez, como formatar o código após cada edição.

### 51.3.2. Segundo — proteção
Você quer bloquear certas ações por completo, como impedir edições nos seus arquivos de config de produção ou no seu `.env` com segredos.

### 51.3.3. Terceiro — consciência (awareness)
Você quer saber o que está acontecendo, como receber uma notificação no desktop no momento em que o Claude termina uma tarefa e está esperando seu input.

## 51.4. Sem hooks, todas as três dependem do julgamento da IA.

Com hooks, elas dependem do seu código. E código não esquece. Código não fica criativo com suas regras. Código simplesmente roda.

Então, resumindo — hooks são a ponte entre torcer para que o Claude faça a coisa certa e garantir isso. Eles transformam suas preferências em regras imponíveis.

## 51.5. O ponto de dor sem hooks

Você está trabalhando com o Claude Code. Ele acabou de editar cinco arquivos para você — brilhante. Mas agora a formatação do seu código está toda bagunçada. O Prettier não rodou. Você corrige manualmente. Da próxima vez, a mesma coisa acontece. Você pensa: "Eu queria que o Claude simplesmente rodasse o Prettier toda vez que edita um arquivo." Mas o detalhe é — o Claude é uma IA. Ele pode rodar o Prettier. Pode esquecer. Não há garantia.

Ou aqui vai outro cenário. Você tem um arquivo `.env` com segredos — chaves de API, senhas de banco de dados. Você disse ao Claude: "Não toque nesse arquivo." Mas e se ele tocar? E se, no meio de uma sessão longa, ele decidir "consertar" prestativamente seu `.env`? Você não teria uma rede de segurança.

E mais uma. O Claude termina uma tarefa, e você está fazendo café, sem olhar o terminal. Cinco minutos se passam antes de você perceber que ele está parado ali, esperando por você. Não seria bom receber uma notificação — como um toque no ombro — dizendo "Ei, terminei, volte aqui"?

Todos os três problemas têm uma coisa em comum: você está torcendo para que a IA faça a coisa certa em vez de garantir isso.

## 51.6. Onde os hooks são armazenados?

Os hooks são armazenados principalmente como configuração JSON nos seguintes locais:

- User Settings (`~/.claude/settings.json`) — Aplica-se a TODOS os projetos
- Project Settings (`.claude/settings.json`) — Aplica-se apenas àquele projeto específico
- Local settings (`.claude/settings.local.json`) — Não compartilhável e aplicado a um único projeto

## 51.7. Criando um hook

A forma mais rápida de criar um hook é pelo menu interativo `/hooks` no Claude Code. Siga os passos abaixo:

1. Abra o menu de hooks digitando `/hooks`
2. Configure o matcher
3. Selecione "+ Add new hook" e forneça seu comando de shell
4. Escolha um local de armazenamento (nível de projeto/usuário)

## 51.8. Estrutura de configuração de hook

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

## 51.9. Configure seu primeiro hook

Em https://code.claude.com/docs/en/hooks-guide, veja "Set up your first hook".

## 51.10. Observação

Os hooks rodam isolados externamente, a custo zero, a menos que o hook retorne contexto adicional.

## 51.11. Como os hooks funcionam

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

## 51.12. IMPORTANTE

O que citei aqui é apenas o mais geral do curso. Mais detalhes em: https://code.claude.com/docs/en/hooks-guide

# 52. hooks (Gemini)

Boa notícia: o Gemini CLI também tem um **sistema de hooks** (Hooks v1), com a mesma filosofia **determinística** — scripts/programas que o CLI executa em pontos específicos do *agentic loop*, para automação, proteção e consciência (awareness), sem depender do "julgamento da IA".

A analogia da "trava automática da porta", os três propósitos (automação / proteção / awareness) e os pontos de dor (rodar Prettier sempre, proteger o `.env`, notificar ao terminar) valem **igualmente** para o Gemini.

## 52.1. Onde os hooks são armazenados?

Como configuração JSON no `settings.json`, com as mesmas camadas (merge entre elas):

- User settings (`~/.gemini/settings.json`) — todos os projetos.
- Workspace/Project settings (`<projeto>/.gemini/settings.json`) — só aquele projeto.

## 52.2. Como os hooks funcionam

Os hooks rodam **sincronicamente** como parte do agent loop: quando um evento dispara, o Gemini CLI espera todos os hooks correspondentes terminarem antes de continuar. (No Claude, eles rodam em paralelo entre si; verifique a semântica exata da sua versão do Gemini.)

## 52.3. Eventos de ciclo de vida

⚠️ **Os nomes dos eventos são diferentes** dos do Claude. O Hooks v1 do Gemini introduz eventos como:

- **`BeforeModel`** — antes de a chamada ao modelo ser feita (útil para engenharia de prompt avançada).
- **`BeforeToolSelection`** — antes de o agente escolher/planejar ferramentas.
- (mais eventos do ciclo são adicionados ao longo das versões — consulte a referência abaixo).

Não há um mapeamento 1:1 com a tabela do Claude (`PreToolUse`, `PostToolUse`, `Stop`, `SessionStart`, etc.); a granularidade e os nomes diferem. Para os casos clássicos:

| Quero...                                  | Claude (evento)        | Gemini (abordagem)                                  |
|-------------------------------------------|------------------------|-----------------------------------------------------|
| Formatar após editar arquivo              | `PostToolUse`          | Hook pós-ferramenta de edição (evento de pós-tool)  |
| Bloquear edição de `.env`                 | `PreToolUse` (bloqueia)| Hook antes da seleção/uso de ferramenta + `tools.exclude` |
| Notificar ao terminar a resposta          | `Stop`/`Notification`  | Hook no fim do loop / evento de notificação         |
| Injetar contexto no início                | `SessionStart`         | `BeforeModel` (injeção de prompt)                   |

## 52.4. Estrutura de configuração

Os hooks são definidos em `settings.json` (sob uma chave `hooks`), associando um evento a um comando de shell. A forma exata do schema evolui — consulte a referência oficial para a sintaxe atual.

Referência: https://geminicli.com/docs/hooks/ e a issue de design https://github.com/google-gemini/gemini-cli/issues/9070

# 53. MCP (Claude)

## 53.1. /mcp

Apresenta a lista de servidores MCP instalados. Apresenta também se está estabelecida uma conexão. Apresenta também quais operações o MCP consegue operar com o servidor.

## 53.2. Site de referência (IMPORTANTE VER)

https://code.claude.com/docs/en/mcp

## 53.3. Exemplos de prompts que podem ser usados com Playwright (alguns com Google Chrome)

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

## 53.4. Context7 MCP: o Claude recebe docs atualizadas

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

### 53.4.1. Um comando. Docs sempre frescas para o Claude.

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

## 53.5. Cenários comuns com MCP

### 53.5.1. Ticket → Code → PR

Ferramentas: Jira (ou Linear) + GitHub + Filesystem

Fluxo: Jira/Linear → Claude Code → GitHub MCP → PR criado

Prompt de exemplo:

```
Implemente a feature descrita no ticket ENG-4521. Leia os detalhes,
escreva o código, rode os testes, commit e abra um PR no GitHub com
descrição adequada e link de volta ao ticket.
```

Resultado esperado: feature implementada + PR criado automaticamente.

### 53.5.2. Production Data → Code Insights

Ferramentas: Postgres (ou qualquer DB) + Filesystem

Fluxo: Postgres MCP → análise cruzada com código → branch + commit

Prompt de exemplo:

```
Query o PostgreSQL dos últimos 30 dias de uso da feature X.
Cruze com os módulos relevantes do repositório. Sugira e implemente
2 otimizações baseadas nos dados. Crie uma branch e commit as mudanças.
```

Resultado esperado: mudanças guiadas por dados com evidência (query exibida).

### 53.5.3. Monitoring → Auto-Fix

Ferramentas: Sentry (ou similar) + GitHub

Fluxo: Sentry MCP → análise de stack traces → fix → PR com métricas antes/depois

Prompt de exemplo:

```
Verifique erros recentes no Sentry relacionados ao módulo de autenticação.
Analise os stack traces contra o codebase, encontre a causa raiz,
rode os testes e crie um PR com métricas de antes/depois.
```

Resultado esperado: bugs reais corrigidos ao vivo.

### 53.5.4. Cross-Tool Automation (Notion → Slack → Code)

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

# 54. MCP (Gemini)

O Gemini CLI tem **suporte de primeira classe a MCP** — o mesmo protocolo aberto (Model Context Protocol). Praticamente tudo desta seção vale, com pequenas diferenças de comando.

## 54.1. /mcp

**`/mcp`** lista os servidores MCP configurados e seu status de conexão, mais as ferramentas que cada um expõe. Variantes úteis:
- **`/mcp desc`** — descrições detalhadas das ferramentas MCP.
- **`/mcp schema`** — schema JSON dos parâmetros das ferramentas.

Toda ferramenta MCP descoberta recebe o prefixo `mcp_<alias-do-servidor>_` no nome totalmente qualificado.

## 54.2. Como configurar servidores MCP

Diferente do Claude (que tem o subcomando `claude mcp add ...`), no Gemini você configura no **`settings.json`**, sob `mcpServers` (ou via UI do `/settings`, ou instalando uma **extensão** que já traz o MCP). Os transportes suportados incluem stdio (processo local via `command`), HTTP (`httpUrl`) e SSE.

### 54.2.1. Context7 no Gemini — docs sempre frescas

Toda a motivação do Context7 (corte de treinamento, APIs depreciadas, docs que mudam mais rápido que o treino) vale **igualmente** para o Gemini. O Context7 é um servidor MCP remoto (HTTP), então funciona direto:

```json
{
  "mcpServers": {
    "context7": {
      "httpUrl": "https://mcp.context7.com/mcp"
    }
  }
}
```

(Coloque em `<projeto>/.gemini/settings.json` para escopo de projeto.) Sem `npx`, sem processo local — o Gemini o alcança via HTTP, ao vivo. O **mesmo prompt de exemplo** do React Router 7 funciona: basta dizer *"Using context7, look up ..."* — o Gemini chamará a ferramenta `mcp_context7_*`.

### 54.2.2. Playwright / Chrome DevTools MCP

Os **mesmos servidores MCP** (Playwright MCP, Chrome DevTools MCP) podem ser adicionados ao Gemini via `mcpServers` (transporte stdio com `npx ...`). Todos os **8 prompts de exemplo** e a distinção "Playwright (automação/interação) vs Chrome DevTools (observação/inspeção)" valem identicamente — é o servidor MCP que determina a capacidade, não o agente.

## 54.3. Cenários comuns com MCP

Os **quatro cenários** (Ticket→Code→PR, Production Data→Insights, Monitoring→Auto-Fix, Cross-Tool Notion→Slack→Code) funcionam igualmente no Gemini, com os mesmos servidores MCP (Jira/Linear, GitHub, Postgres, Sentry, Notion, Slack, Filesystem) e os **mesmos prompts de exemplo**. Diferença operacional: você adiciona cada MCP via `mcpServers` no `settings.json` (ou via extensão do **marketplace de extensões** do Gemini, que tem 90+ integrações instaláveis com um comando), em vez de `claude mcp add`.

Referências:
- MCP no Gemini: https://geminicli.com/docs/tools/mcp-server/
- Extensões (marketplace): https://geminicli.com/docs/extensions/

# 55. loop (Claude)

## 55.1. Rodando prompts em um agendamento

Muitas vezes queremos checar o status de uma tarefa externa enquanto trabalhamos com o Claude Code. Por exemplo:

- Você iniciou um deploy 10 minutos atrás. Já terminou?
- Você fez push de um PR. O CI passou? Algum comentário de revisão?
- Um build longo está rodando. Você fica voltando (Cmd+Tab) para checar.

O problema: você está ou babá do Claude Code, ou se afastou e esqueceu dele.

## 55.2. /loop — Rode um prompt em repetição, sem usar as mãos

Uma skill embutida no Claude Code que re-executa seu prompt automaticamente em um intervalo escolhido, enquanto sua sessão permanece aberta.

| O que você fornece     | Exemplo                     | O que acontece                                  |
|------------------------|-----------------------------|-------------------------------------------------|
| Intervalo + Prompt     | `/loop 5m check the deploy` | Roda seu prompt em um agendamento fixo          |
| Apenas o prompt        | `/loop check the deploy`    | O Claude escolhe o intervalo de forma inteligente a cada vez |
| Nada                   | `/loop`                     | Roda o prompt de manutenção embutido            |

Você pode até dar loop em outro comando → `/loop 20m /review-pr 1234`

## 55.3. Intervalo inteligente (`/loop ...` sem tempo)

- O Claude escolhe de 1 min a 1 hora com base no que vê
- Build ativo? Esperas curtas. PR parado? Esperas mais longas.
- Imprime o delay escolhido + o motivo após cada iteração

## 55.4. O prompt de manutenção embutido

Basta digitar `/loop` — o Claude se torna o zelador do seu projeto. Quando você não dá nada a ele, o Claude roda automaticamente uma rotina de manutenção:

- Continua qualquer trabalho não finalizado da conversa
- Cuida do PR da branch atual — comentários de revisão, CI falho, conflitos de merge
- Roda passes de limpeza — caça a bugs, simplificações — quando não há nada pendente

Importante: o Claude não inicia novas iniciativas nem faz push/delete, a menos que a conversa já tenha autorizado.

Personalize: solte um arquivo `loop.md` para definir seu próprio prompt padrão:

- `.claude/loop.md` → nível de projeto (vence se ambos existirem)
- `~/.claude/loop.md` → nível de usuário (aplica-se em todo lugar)

## 55.5. Coisas para ter em mente

Para parar um loop: pressione `Esc` enquanto ele estiver esperando a próxima iteração.

Limites importantes:

- As tarefas só disparam enquanto o Claude Code estiver rodando e ocioso — **feche o terminal e elas param**
- Tarefas recorrentes expiram automaticamente após 7 dias (um disparo final, e então acabam)
- Uma conversa nova limpa todas as tarefas com escopo de sessão
- Retome com `claude --resume` para restaurar tarefas não expiradas

Precisa de agendamento durável? Veja Routines, tarefas agendadas do Desktop ou GitHub Actions — o `/loop` é para polling dentro da sessão.

## 55.6. Lembretes em linguagem natural

Pode-se escrever uma frase em linguagem natural pedindo para o Claude relembrá-lo de algo depois de X tempo.

## 55.7. Referência de tarefas agendadas

Na página https://code.claude.com/docs/en/scheduled-tasks, podemos ver a tabela com as 3 colunas: "Cloud", "Desktop" e "/loop". Cada uma apresenta uma forma diferente de rodar o Claude, e cada uma permite a programação de tarefas conforme sua especificidade (ex.: se os agendamentos continuam sendo executados mesmo fechando o aplicativo/página, o mínimo de tempo de intervalo entre operações, como são configuradas as funcionalidades de MCP, etc.).

# 56. loop (Gemini)

⚠️ **O Gemini CLI não tem um comando `/loop` embutido** que re-execute um prompt em intervalos dentro da sessão. Para alcançar o mesmo resultado (polling de status de deploy/CI/build sem ficar de babá), use abordagens externas:

## 56.1. Headless mode + shell loop (o análogo mais direto)

O Gemini roda em modo não interativo com `-p` (ver seção *Comandos genéricos*). Combine com um loop de shell:

```bash
# Checa o CI a cada 5 minutos, imprimindo o veredito do Gemini
while true; do
  gemini -p "Cheque o status do CI do PR atual com 'gh pr checks' e me diga em uma linha se passou, falhou ou ainda está rodando."
  sleep 300
done
```

Pressione `Ctrl+C` para parar (equivalente a "Esc enquanto espera").

## 56.2. Cron / agendador do SO (agendamento durável)

Para "continua mesmo fechando o terminal", use `cron` (Linux/macOS) ou o Agendador de Tarefas (Windows) chamando `gemini -p "..."` — o equivalente das *Routines*/*scheduled tasks* do Claude.

## 56.3. GitHub Actions (durável, no servidor)

Para o caso "cuidar do PR / CI / review automaticamente", use a GitHub Action **`run-gemini-cli`** (ver seção *Git (Gemini)*) — o equivalente ao "Cloud" da tabela de tarefas agendadas do Claude.

## 56.4. Mapeamento

| Recurso do `/loop` (Claude)                | Equivalente no Gemini                                  |
|--------------------------------------------|--------------------------------------------------------|
| `/loop 5m <prompt>` (intervalo fixo)       | `while true; do gemini -p "<prompt>"; sleep 300; done` |
| `/loop <prompt>` (intervalo inteligente)   | Sem equivalente; defina o `sleep` você mesmo           |
| `/loop` (manutenção embutida)              | Sem equivalente; escreva o prompt de manutenção        |
| Agendamento durável (Routines/Cloud)       | `cron`/Task Scheduler + `gemini -p`, ou GitHub Actions |
| Lembrete em linguagem natural              | Sem equivalente embutido; use `cron`/`at` + `gemini -p`|

# 57. Sub-Agents (Claude)

Pode-se pedir para o Claude executar o agente X, pedindo via prompt para que ele seja executado em background.

Página de ajuda com vários exemplos de uso: https://code.claude.com/docs/en/sub-agents

## 57.1. Sub-Agents

Deixa eu te perguntar uma coisa.

Você está trabalhando num codebase grande. Você pede ao Claude Code: "Rode a suíte de testes completa, explore o módulo de autenticação, busque as docs de API mais recentes e então corrija os testes que falham."

O Claude começa a trabalhar. E em minutos... sua janela de contexto está se afogando. Centenas de linhas de logs de teste. Paredes de documentação. Conteúdos de arquivos que você nunca mais vai olhar — tudo se acumulando na sua conversa principal, expulsando as coisas que de fato importam.

Soa familiar?

É exatamente esse o problema que os **Sub Agents** foram criados para resolver.

## 57.2. O que são Sub Agents?

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

## 57.3. Por que usar Sub-Agents?

Os sub-agentes ajudam a resolver problemas comuns de workflow de IA:

**Melhor gerenciamento de contexto** — Grandes saídas ficam dentro do sub-agente em vez de poluir a conversa principal.
**Comportamento especializado** — Cada agente pode ser ajustado para uma única responsabilidade.
**Otimização de custo** — Tarefas podem ser roteadas para modelos mais rápidos ou mais baratos.
**Permissões controladas** — Você pode restringir quais ferramentas ou ações um sub-agente tem permissão de usar.
**Reusabilidade** — Sub-agentes de nível de usuário podem ser reutilizados entre projetos.

Todo Sub Agent começa do zero — seu próprio contexto fresco, isolado da sessão principal, armado apenas com as ferramentas e skills específicas que você entrega a ele.

### 57.3.1. Janela de contexto

#### 57.3.1.1. Início da sessão:
- **CLAUDE.md** — Conteúdo completo sempre no contexto e usado em todo prompt
- **Metadados das Skills** — Apenas nome e descrição são carregados
- **Servidores MCP** — Nomes das ferramentas. Schemas sob demanda

#### 57.3.1.2. No uso:
- **Skills** — Conteúdo completo carregado no contexto ao usar a skill

### 57.3.2. Isolado
- **Hooks** — Rodam externamente, custo zero a menos que o hook retorne contexto adicional
- **Subagentes** — Carregam em um contexto separado quando criados

## 57.4. Criando um sub-agente

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

## 57.5. Memória persistente em Sub-Agents

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

## 57.6. O que acontece quando a memória está habilitada?

Quando um sub-agente usa memória:

- Seu system prompt inclui instruções para ler e atualizar arquivos de memória.
- As primeiras 200 linhas do MEMORY.md são automaticamente fornecidas ao agente.
- Se o arquivo crescer demais, o agente é orientado a mantê-lo conciso.
- As ferramentas Read, Write e Edit são automaticamente habilitadas para que o agente possa gerenciar sua memória.

## 57.7. Como usar a memória de forma eficaz

Você pode orientar o sub-agente com instruções simples:

- Antes de começar o trabalho → "Check your memory for similar issues before analyzing this code."
- Depois de terminar o trabalho → "Save the important findings to your memory."

Com o tempo, isso cria uma base de conhecimento crescente que melhora o desempenho do agente.

## 57.8. Delegação automática

O Claude decide quando usar um sub-agente com base em:
- A redação do seu pedido
- A descrição definida dentro do arquivo do sub-agente
- O contexto de trabalho atual

Se uma tarefa casa com o propósito de um sub-agente, o Claude pode delegar o trabalho automaticamente. Para encorajar esse comportamento, você pode adicionar frases como "use proactively" na descrição do sub-agente, para que o Claude saiba que ele deve ser selecionado sempre que for relevante.

## 57.9. Execução em foreground vs background

Sub-agentes podem rodar em dois modos diferentes, dependendo de como você quer que eles se comportem.

⏳ **Execução em foreground (bloqueante)**
A conversa principal espera até o sub-agente terminar. Quaisquer pedidos de permissão ou perguntas de esclarecimento são mostrados diretamente a você. Melhor para tarefas em que você quer visibilidade e controle totais.

⚡ **Execução em background (concorrente)**
O sub-agente roda enquanto você continua trabalhando. Antes de iniciar, o Claude pede todas as permissões de ferramenta necessárias. Após a aprovação, o sub-agente usa automaticamente apenas essas permissões.

# 58. agents (agentes) (Gemini)

**Boa notícia: o Gemini CLI tem sub-agentes** (lançados oficialmente), com a mesma motivação — delegar tarefas a especialistas isolados que não poluem a conversa principal. Toda a analogia do "arquiteto + especialistas" e os benefícios (gerenciamento de contexto, especialização, otimização de custo, permissões controladas, reusabilidade) valem igualmente.

> "Subagents são agentes especialistas que operam ao lado da sua sessão principal. Quando você dá uma tarefa ampla, o Gemini CLI age como um orquestrador estratégico, delegando subtarefas ao subagente mais relevante. Subagentes agem em isolamento, com seu próprio conjunto de ferramentas, MCP servers, instruções de sistema e janela de contexto. Toda a execução é consolidada em uma única resposta de volta ao agente principal."

## 58.1. Criando um sub-agente

- Rode **`/agents`** dentro do `gemini` para ver/gerenciar os subagentes configurados (análogo ao `/agents` do Claude). As versões recentes oferecem um fluxo de criação interativo.
- Ou crie o arquivo manualmente. **Formato: Markdown (`.md`) com frontmatter YAML** — igual ao Claude.

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

O frontmatter define nome, descrição (usada para delegação), ferramentas permitidas e modelo; o corpo é o system prompt do subagente. ⚠️ Note que os **nomes das ferramentas são os do Gemini** (`read_file`, `glob`, `run_shell_command`, ...), não os do Claude (`Read`, `Glob`).

## 58.2. Delegação automática e explícita

- **Automática:** o orquestrador roteia tarefas ao subagente conforme a `description` e a relevância (mesma ideia do Claude; frases como "use proactively" ajudam).
- **Explícita:** use a sintaxe **`@nome-do-agente`** no prompt, ex.: `@frontend-specialist revise nosso app`. (No Claude você pede em linguagem natural; no Gemini há essa sintaxe `@agent` direta.)
- **Ver agentes:** `/agents`.

## 58.3. Execução paralela / background

- Múltiplos subagentes podem rodar **em paralelo** — peça explicitamente: *"Rode o frontend-specialist em cada pacote em paralelo."* (acelera, mas aumenta o risco de conflitos de código e o consumo de API).
- ⚠️ A documentação do Gemini foca em delegação/paralelismo; a distinção formal **foreground (bloqueante) vs. background (concorrente)** com pré-aprovação de permissões, como no Claude, não é exposta da mesma maneira. Na prática, a sessão principal aguarda a resposta consolidada do subagente.

## 58.4. Memória persistente em sub-agentes

O Gemini também permite subagentes com **memória persistente** (configurável no frontmatter), de modo que aprendam padrões, problemas recorrentes e decisões entre execuções — o análogo do `memory: user|project|local` do Claude. É, inclusive, o melhor caminho para reproduzir o benefício do "Auto Memory" que falta no fluxo principal do Gemini (ver *Memory (Gemini)*).

Referência: https://developers.googleblog.com/en/subagents-have-arrived-in-gemini-cli/

# 59. Agent teams (equipes de agentes) (Claude)

Coordene múltiplas instâncias do Claude Code trabalhando juntas como uma equipe, com tarefas compartilhadas, mensageria entre agentes e gerenciamento centralizado.

https://code.claude.com/docs/en/agent-teams

# 60. Agent teams (equipes de agentes) (Gemini)

⚠️ **O Gemini CLI não tem um recurso oficial de "Agent Teams"** (múltiplas instâncias coordenadas, com tarefas compartilhadas, mensageria entre agentes e gerenciamento centralizado) equivalente ao do Claude.

Como chegar perto do mesmo resultado:

- **Sub-agentes em paralelo:** a forma nativa mais próxima — um orquestrador delega a vários subagentes especialistas que rodam em paralelo e consolidam respostas (ver *agents (Gemini)*). É "um líder + especialistas", não "vários pares coordenados".
- **Múltiplas sessões + Git worktrees:** rode várias instâncias do `gemini` em pastas/worktrees diferentes, cada uma numa subtarefa, coordenando manualmente (via arquivos compartilhados, branches, ou um `GEMINI.md` comum).
- **Orquestração externa:** padrões da comunidade montam "multi-agente" só com prompts e scripts (ex.: https://aipositive.substack.com/p/how-i-turned-gemini-cli-into-a-multi), mas sem mensageria entre agentes embutida.

# 61. Git (Claude)

## 61.1. Claude Code para tarefas e atividades no GitHub

O Claude Code se conecta ao GitHub principalmente em três níveis diferentes:

**1. Terminal (Local)** — Você fala com o Claude no seu terminal. Ele roda comandos `git` e `gh` por você. Pense nisso como programar em par com alguém que nunca esquece a sintaxe do Git.

**2. GitHub Actions (Remoto)** — O Claude vive dentro do seu repositório do GitHub como um bot. Mencione `@claude` num PR ou issue, e ele responde — revisando código, corrigindo bugs ou implementando features automaticamente.

**3. Headless / Scripting (Automatizado)** — Use a flag `-p` para rodar o Claude sem uma sessão interativa. Perfeito para scripts de build, pipelines de CI/CD e processamento em lote.

## 61.2. Operações Git pelo terminal

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

## 61.3. Plugin commit-commands

O plugin Commit Commands automatiza operações git comuns, reduzindo a troca de contexto e a execução manual de comandos. Em vez de rodar vários comandos git, use um único comando de barra para lidar com todo o seu workflow.

**Instalar o plugin:** Rode o comando `/plugin` e instale o plugin commit-commands, que fornece os seguintes comandos executáveis a partir de sessões do Claude Code:

| Comando           | O que faz                                                                          |
|-------------------|------------------------------------------------------------------------------------|
| `/commit`         | Revisa suas mudanças, faz o stage dos arquivos e cria um commit com uma mensagem inteligente |
| `/commit-push-pr` | Faz tudo — commita, faz push para uma feature branch e abre um PR em um único passo |
| `/clean_gone`     | Remove branches locais que já foram deletadas no remoto                             |

## 61.4. Rode sessões paralelas do Claude Code com Git Worktrees

### 61.4.1. Por que precisamos de worktrees?

Às vezes você pode trabalhar em várias tarefas ao mesmo tempo.

Exemplo:
- Uma tarefa = construir uma nova feature
- Outra tarefa = corrigir um bug de produção

Rodar tudo na mesma pasta pode causar:
- Conflitos de arquivos
- Mudanças misturadas
- Confusão entre branches

Os Git worktrees ajudam a evitar esses problemas.

### 61.4.2. O que é um Git Worktree?

Um worktree cria uma pasta de trabalho separada a partir do mesmo repositório.

Cada worktree:
- Tem seus próprios arquivos
- Usa sua própria branch
- Compartilha o mesmo histórico Git e repositório remoto

Pense nisso como criar vários espaços de trabalho para o mesmo projeto.

### 61.4.3. Como o Claude usa worktrees

Use a opção `--worktree` (ou `-w`). Se você não fornecer um nome, o Claude gerará um aleatório.

```
claude --worktree feature-cache
```

O que acontece:
- Uma nova pasta é criada
- Uma nova branch é criada automaticamente
- O Claude inicia dentro daquele espaço de trabalho isolado

### 61.4.4. Rodando múltiplas sessões

Você pode iniciar várias sessões do Claude assim:

```
claude --worktree feature-cache
claude --worktree bugfix-performance
```

Cada sessão roda de forma independente, tem seu próprio diretório de trabalho e usa sua própria branch.

### 61.4.5. Onde os worktrees são armazenados?

O Claude cria worktrees dentro do seu repositório: `<repo>/.claude/worktrees/<nome>`
Padrão de nomeação de branch: `worktree-<nome>`

### 61.4.6. Criando worktrees durante uma sessão

Você nem sempre precisa reiniciar o Claude. Basta dizer:
- "Start a worktree"
- "Work in a worktree"

O Claude vai:
- Criar um automaticamente
- Mover seu trabalho para dentro dele

## 61.5. Integração com GitHub Actions (o bot @claude)

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

## 61.6. Configurando a GitHub Action — Início rápido

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

# 62. Git (Gemini)

O Gemini CLI também opera no GitHub nos mesmos **três níveis**:

**1. Terminal (Local)** — Igual ao Claude: você pede em linguagem natural e o Gemini roda `git` e `gh` por você (via a ferramenta `run_shell_command`). Programação em par sem decorar sintaxe.

**2. GitHub Actions (Remoto)** — O Gemini vive no repositório via a Action **`run-gemini-cli`**. O gatilho de menção costuma ser **`@gemini-cli`** (em vez de `@claude`).

**3. Headless / Scripting (Automatizado)** — `gemini -p "..."` para rodar sem sessão interativa (ver *Comandos genéricos*).

## 62.1. Operações Git pelo terminal

**Todos os exemplos** em linguagem natural valem identicamente (`commit and push...`, `create a feature branch...`, `review the PR and merge...`, `fix the problem in issue 2`, etc.). O Gemini executa `git`/`gh` nos bastidores. ⚠️ Garanta que o uso do shell esteja autorizado (modo `default` pedirá confirmação; `auto_edit`/`yolo` ou `autoApprovedTools: ["run_shell_command(git)", "run_shell_command(gh)"]` reduzem prompts).

## 62.2. Plugin commit-commands → custom commands no Gemini

⚠️ **O Gemini não tem o plugin `commit-commands` da Anthropic.** Reproduza-o com **custom commands** (TOML). Exemplos:

`~/.gemini/commands/commit.toml`:
```toml
description = "Revisa mudanças, faz stage e cria um commit com mensagem inteligente."
prompt = "Revise o diff com 'git diff', faça stage do que for relevante e crie um commit com uma mensagem descritiva no estilo Conventional Commits."
```

`~/.gemini/commands/commit-push-pr.toml`:
```toml
description = "Commita, faz push de uma feature branch e abre um PR."
prompt = "Crie uma feature branch adequada, commit as mudanças, faça push e abra um PR no GitHub com 'gh pr create', incluindo um resumo das mudanças."
```

Aciona com `/commit`, `/commit-push-pr`, etc. (Ver seção *commands (Gemini)*.)

## 62.3. Sessões paralelas com Git Worktrees

⚠️ **O Gemini não tem a flag `--worktree`/`-w`** nem cria worktrees automaticamente em `<repo>/.claude/worktrees/`. A motivação (evitar conflitos rodando tarefas paralelas) é a mesma; o processo é **manual**:

```bash
git worktree add ../feature-cache feature-cache
cd ../feature-cache && gemini

# em outro terminal
git worktree add ../bugfix-performance bugfix-performance
cd ../bugfix-performance && gemini
```

Cada `gemini` roda na sua pasta/branch, isolado. Você também pode pedir ao próprio Gemini, em linguagem natural, que rode os comandos `git worktree` por você.

## 62.4. Integração com GitHub Actions (o bot @gemini-cli)

O análogo da GitHub Action oficial do Claude é a **`google-github-actions/run-gemini-cli`** (beta, "AI coding teammate" sem custo no plano gratuito). Capacidades equivalentes: responder perguntas sobre o código, revisar PRs, implementar correções/refactors, trabalhar com issues, triagem.

**Como é acionado:** alguém menciona **`@gemini-cli`** num comentário de PR ou issue (ex.: `@gemini-cli review this PR`, `@gemini-cli fix this bug`); o GitHub Actions detecta e roda o Gemini, que lê o codebase e o **`GEMINI.md`** para seguir as regras do projeto, e devolve comentário/revisão/PR.

## 62.5. Configurando a GitHub Action — Início rápido

⚠️ **Não há um `/install-github-app` equivalente no CLI.** A configuração é mais "mão na massa":

1. Copie um workflow de exemplo de `google-github-actions/run-gemini-cli` (pasta `examples/workflows/`) para `.github/workflows/` (ex.: triagem de issues, review de PR).
2. Adicione um secret com sua chave: **`GEMINI_API_KEY`** (do Google AI Studio) em Settings → Secrets and Variables → Actions. (Equivalente ao `ANTHROPIC_API_KEY`/`CLAUDE_CODE_OAUTH_TOKEN` do Claude.)
3. Ajuste `permissions:` no YAML para `pull-requests: write` e `issues: write` se quiser que o bot comente/edite — **mesma observação (Obs. 1)** do Claude.
4. Faça commit/merge do workflow.

**Prompt customizado de review (≈ Obs. 3):** os workflows da `run-gemini-cli` também aceitam um `prompt:` customizado e usam comandos TOML como `gemini-review.toml`. O mesmo prompt de exemplo (qualidade de código, bugs, performance, segurança, cobertura de testes, usar o `GEMINI.md`, comentar via `gh pr comment`) funciona — só troque "CLAUDE.md" por "GEMINI.md".

Referências:
- Action: https://github.com/google-github-actions/run-gemini-cli
- Anúncio: https://blog.google/technology/developers/introducing-gemini-cli-github-actions/

# 63. Status Line (Claude)

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

## 63.1. Como a Status Line funciona — JSON na entrada, texto na saída

- 📨 O Claude Code envia JSON para seu script via stdin — nome do modelo, custo, % de contexto, diretório git, ID da sessão, tudo
- 🛠️ Seu script lê isso, escolhe o que importa, formata — usando bash, Python, Node.js, PowerShell, o que você preferir
- 🖼️ Seu script imprime texto no stdout — e o Claude Code o exibe na parte de baixo da tela

## 63.2. O caminho "eu nem escrevi um script"

Você não precisa escrever o script você mesmo. Apenas descreva o que você quer:

```
/statusline show model name and context percentage with a progress bar
```

O Claude Code gera o script, coloca-o em `~/.claude/`, atualiza suas configurações, e está pronto. ✨

## 63.3. O caminho manual (`~/.claude/settings.json`)

```json
{
  "statusLine": {
    "type": "command",
    "command": "~/.claude/statusline.sh",
    "padding": 2
  }
}
```

### 63.3.1. O arquivo statusline-command.sh

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

## 63.4. Referência de documentação

https://code.claude.com/docs/en/statusline

# 64. Status Line (Gemini)

⚠️ **O Gemini CLI não tem uma "status line" scriptável** (um script que recebe JSON via stdin e imprime uma faixa customizada) como o `/statusline` do Claude.

O que o Gemini oferece para responder às mesmas três perguntas ("quanto de contexto?", "qual o custo/uso?", "qual branch?"):

- **Rodapé embutido (não customizável por script):** o Gemini CLI já exibe na parte de baixo informações como modelo atual, contagem/percentual de tokens (contexto) e diretório/branch. É um dashboard fixo, não programável.
- **Tema/aparência:** ajuste a aparência com `/theme` e a chave `ui.theme` no `settings.json` — mas isso é estética, não conteúdo customizado de status.
- **`/stats`:** para custo/uso de tokens sob demanda.

Como obter uma status line de verdade (workaround):
- Personalize o **prompt do seu shell** (PS1 do bash/zsh, ou Starship/Powerline) para mostrar a branch do Git e infos do ambiente — isso aparece acima do prompt do `gemini`. Não terá o custo/tokens em tempo real do Gemini, mas cobre branch/diretório/estado do repo de forma persistente.
- Para acompanhamento de tokens/custo, use utilitários da comunidade como o *Gemini CLI Token Usage Tracker* (TUI), citado em *Usage (Gemini)*.

Resumo: a parte "sempre visível" você tem (rodapé embutido + prompt do shell), mas a parte "você decide exatamente o que aparece, via script" **não existe** no Gemini.

# 65. Comandos genéricos (Claude)

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

# 66. Comandos genéricos (Gemini)

Equivalentes no Gemini CLI:

**Sair da sessão:** use **`/quit`** ou **`/exit`** (ou `Ctrl+C` duas vezes). ⚠️ O Gemini não imprime automaticamente um comando `--resume <id>` ao sair; para retomar, você precisa ter salvo um ponto com `/chat save <tag>` e usar `/chat resume <tag>` (ver *Resume (Gemini)*). Não há um `claude -c` equivalente de inicialização.

| Recurso                         | Claude            | Gemini                                                       |
|---------------------------------|-------------------|--------------------------------------------------------------|
| Referenciar um arquivo          | `@src/main.py`    | `@src/main.py` (mesma sintaxe; injeta o conteúdo no prompt)  |
| Executar shell direto           | `!git status`     | `!git status` (mesma sintaxe; `!` sozinho entra/sai do shell mode) |
| Nota rápida à memória da sessão | `#`               | ⚠️ Sem o atalho `#`. Use **`/memory add <texto>`** ou peça em linguagem natural para anotar no `GEMINI.md` |

**Listar/trocar modelos:**

```
/model
```
ou na CLI:
```
gemini --model gemini-2.5-pro     # (ou -m)
```

**Modo não interativo (print/headless):**

```
gemini -p "help me to improve my skills as a Java developer"
```

A flag **`-p`** (ou `--prompt`) roda o Gemini sem sessão interativa: envia o prompt, imprime no stdout e sai — útil para scripts, CI/CD e pipelines Unix. (Idêntico ao `-p` do Claude.) Você também pode passar o prompt via stdin: `echo "..." | gemini`.

---

## 66.1. Apêndice: tabela-resumo Claude ↔ Gemini

| Tópico / Recurso              | Claude Code                        | Gemini CLI                                               |
|-------------------------------|------------------------------------|----------------------------------------------------------|
| Trocar modelo                 | `/model`, `--model`                | `/model`, `--model`/`-m` (+ model routing automático)    |
| Integração IDE                | extensão Claude Code               | Gemini CLI Companion + `/ide enable`                     |
| Auto-aceitar edições          | `Shift+Tab` (Edit Mode)            | `Shift+Tab` (`auto_edit`)                                |
| Plan mode                     | `Shift+Tab×2` / `/plan`            | ⚠️ Sem equivalente (peça plano no prompt / subagente)    |
| YOLO                          | `--dangerously-skip-permissions`   | `--yolo` / `Ctrl+Y`                                      |
| Voz                           | `/voice`                           | ⚠️ Externo (Handy, ditado do SO)                         |
| Arquivo de contexto/regras    | `CLAUDE.md`                        | `GEMINI.md`                                              |
| Gerar contexto inicial        | `/init`                            | `/init`                                                  |
| UI de config                  | `/config`                          | `/settings`                                              |
| Permissões                    | `/permissions`, `allow`/`deny`     | `tools.autoApprovedTools`/`exclude` (sem `/permissions`) |
| Debug de config               | `/status`                          | `/settings` + `/memory list` + `/mcp` + `/tools`         |
| Uso/limites                   | `/usage`                           | `/stats` (sessão; sem limites de plano)                  |
| Output styles                 | `/config → Output-style`           | ⚠️ Via `GEMINI.md` / `GEMINI_SYSTEM_MD`                  |
| Esforço de raciocínio         | `/effort`                          | ⚠️ Escolha de modelo Pro/Flash + thinking budget         |
| Ver contexto                  | `/context`                         | rodapé + `/stats`                                        |
| Compactar contexto            | `/compact "..."`                   | `/compress` (sem instruções customizadas)               |
| Limpar contexto da sessão     | `/clear`                           | `/compress` ou nova sessão (`/clear` = só limpa tela)    |
| Nomear sessão                 | `/rename`                          | `/chat save <tag>`                                       |
| Retomar sessão                | `--resume`, `-c`                   | `/chat resume <tag>`, `/chat list`                       |
| Bifurcar sessão               | `--fork-session`                   | branching via `/chat save`+`/chat resume`                |
| Desfazer (rewind)             | `/rewind`, `Esc Esc`               | `/restore` (checkpointing)                               |
| Memória manual                | `/memory`, "remember..."           | `/memory add`, editar `GEMINI.md`                        |
| Auto Memory                   | `MEMORY.md` (automático)           | ⚠️ Sem equivalente (use subagente c/ memória)            |
| Rules path-scoped             | `.claude/rules/` (`paths:`)        | ⚠️ `GEMINI.md` por subdiretório / imports                |
| Skills                        | `.claude/skills/SKILL.md`          | custom commands TOML + extensions + agent skills         |
| Commands                      | `.claude/commands/*.md` (deprec.)  | `.gemini/commands/*.toml` (atual)                        |
| Hooks                         | `/hooks` (eventos `PreToolUse`...) | Hooks v1 (`BeforeModel`, `BeforeToolSelection`...)       |
| MCP                           | `/mcp`, `claude mcp add`           | `/mcp`, `mcpServers` no `settings.json` / extensões      |
| Loop / agendamento            | `/loop`                            | ⚠️ shell loop + `gemini -p` / cron / GitHub Actions      |
| Sub-agentes                   | `/agents`, `.claude/agents/*.md`   | `/agents`, `.gemini/agents/*.md`, `@agent`               |
| Agent teams                   | Agent Teams                        | ⚠️ Sem equivalente (subagentes paralelos / múltiplas sessões) |
| Worktrees                     | `--worktree`/`-w`                  | ⚠️ Manual (`git worktree add`)                           |
| Bot no GitHub                 | `@claude` + `claude.yml`           | `@gemini-cli` + `run-gemini-cli`                          |
| Instalar app no GitHub        | `/install-github-app`              | ⚠️ Manual (copiar workflow + secret `GEMINI_API_KEY`)    |
| Plugin de commit              | `/commit`, `/commit-push-pr`       | custom commands TOML equivalentes                        |
| Status line scriptável        | `/statusline` + script             | ⚠️ Sem equivalente (rodapé fixo + prompt do shell)       |
| Referenciar arquivo / shell   | `@arquivo`, `!cmd`                 | `@arquivo`, `!cmd`                                       |
| Nota rápida à memória         | `#`                                | ⚠️ `/memory add`                                         |
| Modo headless                 | `claude -p`                        | `gemini -p`                                              |

---
