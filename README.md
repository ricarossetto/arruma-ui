<div align="center">

# arruma-ui

**Uma skill de agente para arrumar interfaces que já existem.**

Audita antes de editar. Preserva o produto. Normaliza o sistema visual sem trocar a identidade.

[![Agent Skill](https://img.shields.io/badge/agent%20skill-SKILL.md-1f2937?style=flat-square)](skills/arruma-ui/SKILL.md)
[![License](https://img.shields.io/badge/license-MIT-b08d57?style=flat-square)](LICENSE)
[![Harnesses](https://img.shields.io/badge/works%20with-Cline%2C%20OpenCode%2C%20Claude%20Code%2C%20Codex%2C%20Cursor-1f2937?style=flat-square)](#compatibilidade)

</div>

---

## O problema

Interface feita por IA costuma cair no mesmo lugar: tudo centralizado, três cards iguais, gradiente roxo, botões de cinco alturas, foco invisível, movimento decorativo. Projeto antigo acumula o mesmo tipo de ruído por outro caminho: cada tela nasceu em um dia, com um raio, um espaçamento e um estado diferente.

O `arruma-ui` atende os dois casos sem transformar o projeto em template. Ele lê o que existe, aponta o que está inconsistente e corrige o sistema. A marca, o conteúdo e o fluxo continuam.

## O que ela faz

| Etapa | O que acontece |
|---|---|
| Lê | Tokens, tema, componentes, telas e estados atuais. |
| Audita | 13 dimensões, com nota e evidência por achado. |
| Normaliza | Botões, inputs, raios, espaçamento, foco, sombras, ícones e tipografia. |
| Remove | Ruído de IA antes de adicionar qualquer coisa nova. |
| Implementa | Em passes: tokens, layout, componentes, estados, motion. |
| Verifica | Browser em 390, 768 e 1440, claro e escuro, teclado e reduced motion. |
| Relata | Arquivos, telas, antes e depois, riscos e próximo passo. |

## Princípios

- O produto manda. A skill não troca conteúdo, fluxo ou marca.
- Auditar antes de editar.
- Remover antes de adicionar.
- Uma coisa por vez, com diff legível.
- Evidência no browser, não promessa.

## Antes e depois

| Antes | Depois |
|---|---|
| Botões com cinco alturas | 32 compacto, 40 padrão, 48 toque |
| Raios aleatórios | 6, 10, 14, 18 |
| `transition: all` | 120 a 240ms, só transform e opacity |
| Foco invisível | Anel de 2px, sempre visível |
| Card dentro de card | Uma camada de contenção |
| Texto centralizado em tudo | Hierarquia com ponto de entrada claro |
| Métrica inventada | Dado real ou nenhum |

## Como funciona

1. **Ler o ambiente.** Tokens, `DESIGN.md`, `PRODUCT.md`, componentes e as telas afetadas. Se o app roda, abre no browser. Se não, usa screenshots committed.
2. **Auditar.** Nota de 0 a 10 para hierarquia, layout, tipografia, cor, superfícies, controles, motion, estados, responsivo, acessibilidade, copy, performance e slop.
3. **Planejar.** No máximo 120 palavras: três a cinco movimentos, o que fica, arquivos e como verificar.
4. **Normalizar.** Usa os tokens do projeto. Se não existem, cria o menor conjunto possível.
5. **Implementar em passes.** Tokens, layout, componentes, estados e copy, motion. Sem reescrita de carona.
6. **Verificar no browser.** 390, 768 e 1440, claro e escuro, teclado, reduced motion. Screenshot só conta se for lido.
7. **Relatar.** O que mudou, o que ficou, evidência, riscos e um próximo passo.

## O que ela normaliza

| Token | Valores |
|---|---|
| Espaço | 4, 8, 12, 16, 24, 32, 48, 64 |
| Raio | 6 pequeno, 10 controle, 14 card, 18 shell |
| Tipo | 12, 13, 14, 16, 20, 24, 32, 40, 56 |
| Altura de controle | 32 compacto, 40 padrão, 48 toque |
| Ícone | 16, 20, 24, um peso de traço |
| Sombra | quatro níveis, com offset e blur |
| Foco | anel de 2px, offset de 2px |
| Motion | 120 a 240ms, `cubic-bezier(0.22, 1, 0.36, 1)` |
| Container | 1200 a 1440px, centralizado |

## O que ela recusa

- gradiente roxo para azul e texto com gradiente
- glass e blur como decoração genérica
- 3D, partículas e shader como enfeite padrão
- card dentro de card
- emoji como ícone
- eyebrow acima de título
- três cards iguais de ícone, título e texto
- `#000` e `#fff` puros fora dos tokens
- Inter, Roboto, Open Sans, Poppins ou Lato como fonte de display
- métrica, depoimento, logo ou case inventado
- `transition: all` e animação de width, height, top ou left
- informação essencial só no hover
- foco invisível
- movimento sem significado de estado
- nome de placeholder e clichê de startup

## Instalação

Requer Node.js 22.20 ou mais novo.

```shell
npx skills add ricarossetto/arruma-ui
```

O CLI pergunta em quais harnesses instalar. Se ele detectar o opencode e instalar sem perguntar, force o harness:

```shell
npx skills add ricarossetto/arruma-ui -a cline -g
```

Sem `-g`, instala no projeto. Com `-g`, instala para o usuário.

### Cline

1. Ative Skills em Settings → Features → Enable Skills, se a sua versão ainda tratar isso como experimental.
2. Rode o comando acima.
3. O CLI instala em `.agents/skills/arruma-ui/`. O Cline também lê `.cline/skills/arruma-ui/`.
4. Peça "arruma a UI desta tela" ou "audita essa interface".

## Compatibilidade

| Harness | Global | Projeto |
|---|---|---|
| Cline | `~/.agents/skills/` ou `~/.cline/skills/` | `.agents/skills/` ou `.cline/skills/` |
| OpenCode | `~/.config/opencode/skills/` ou `~/.agents/skills/` | `.opencode/skills/` ou `.agents/skills/` |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` |
| Codex | `~/.codex/skills/` | `.codex/skills/` |
| Cursor | `~/.cursor/skills/` | `.cursor/skills/` |

## Exemplos de pedidos

> arruma a UI da tela de checkout sem mudar o fluxo

> audita essa interface e me diz o que está inconsistente

> normaliza os botões e inputs desse projeto

> tira a cara de IA dessa landing, mas mantém a identidade

> deixa essa tela premium sem trocar a paleta

## Estrutura

```text
skills/
└── arruma-ui/
    └── SKILL.md
```

## Licença

MIT. Veja [LICENSE](LICENSE).

<div align="center">

Auditar primeiro. Editar depois.

</div>
