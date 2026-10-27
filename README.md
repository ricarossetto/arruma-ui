# arruma-ui

Skill de agente para arrumar, auditar e normalizar interfaces existentes. Funciona com Cline, OpenCode, Claude Code, Codex, Cursor e qualquer harness que leia o padrão Agent Skills (`SKILL.md`).

Ela não é um gerador de landing page. O foco é o que já existe: ler tokens, componentes e telas, achar o que está inconsistente e corrigir sem quebrar produto, conteúdo ou fluxo.

## O que ela faz

- lê tokens, tema, componentes e as telas afetadas antes de editar
- audita hierarquia, layout, tipografia, cor, superfícies, controles, estados, motion, responsivo, acessibilidade, copy e performance
- normaliza alturas de botões e inputs, raios, espaçamento, foco, sombras e ícones
- remove padrões de "cara de IA" antes de adicionar coisa nova
- implementa em passes, com diff legível
- verifica no browser em 390, 768 e 1440, claro e escuro, teclado e reduced motion
- entrega um relatório curto com arquivos, telas e evidência

## Instalar

Requer Node.js 22.20 ou mais novo.

```shell
npx skills add ricarossetto/arruma-ui
```

O CLI pergunta em quais harnesses instalar. Para ir direto no Cline:

```shell
npx skills add ricarossetto/arruma-ui -a cline -g
```

Sem `-g`, instala no projeto atual. Com `-g`, instala para o usuário.

### Cline

1. Ative Skills em Settings → Features → Enable Skills, se a sua versão ainda tratar isso como experimental.
2. Rode o comando acima.
3. O CLI instala no padrão cross-agent `.agents/skills/arruma-ui/`. O Cline também lê `.cline/skills/arruma-ui/`, então as duas pastas funcionam.
4. No chat, peça "arruma a UI desta tela" ou "audita essa interface".

### OpenCode

```shell
npx skills add ricarossetto/arruma-ui -a opencode -g
```

A skill fica em `~/.config/opencode/skills/arruma-ui/SKILL.md` ou `~/.agents/skills/arruma-ui/SKILL.md`, dependendo do modo de instalação.

### Manual

Copie a pasta `skills/arruma-ui` para o diretório de skills do seu harness.

| Harness | Global | Projeto |
|---|---|---|
| Cline | `~/.agents/skills/` ou `~/.cline/skills/` | `.agents/skills/` ou `.cline/skills/` |
| OpenCode | `~/.config/opencode/skills/` ou `~/.agents/skills/` | `.opencode/skills/` ou `.agents/skills/` |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` |
| Codex | `~/.codex/skills/` | `.codex/skills/` |
| Cursor | `~/.cursor/skills/` | `.cursor/skills/` |

## Estrutura

```text
skills/
└── arruma-ui/
    └── SKILL.md
```

## Licença

MIT.
