# Startup: *nome a definir*

Plataforma web instalável (PWA) para clínicas de estética: agenda por profissional sem marcação duplicada, lembretes automáticos que reduzem faltas, prontuário com anamnese e fotos "Antes/Depois" e contratos com assinatura digital para procedimentos invasivos.

Projeto do **Bootcamp Software Engineering Project** (MBA em Engenharia de Software, Faculdade Impacta), desenvolvido com o método AI-DLC.

- **URL do MVP:** *a definir (checkpoint 05)*
- **Hipótese:** [docs/produto/hipotese.md](docs/produto/hipotese.md)

## POD

| Integrante | Papel |
|--|--|
| Jéssica Arruda | *a definir* |
| Rafael Silva | *a definir* |
| Daniel Damascena | *a definir* |

Papéis do bootcamp (um por integrante; todos operam agentes e revisam PRs):

| Papel | Responde por |
|--|--|
| Product Owner | PRD, histórias e validação com usuários |
| Tech Lead | Harness do agente ([AGENTS.md](AGENTS.md)) e arquitetura C1/C2 |
| Quality & Ops | CI, testes, deploy e métricas |

## Hipótese de valor

> Acreditamos que uma agenda online que garante o horário a quem escolhe primeiro, com lembretes automáticos por WhatsApp e e-mail 24 horas antes e confirmação "Sim/Não", para clínicas de estética com mais de um profissional e seus pacientes, vai gerar menos faltas e nenhuma marcação duplicada. Saberemos que é verdade quando a taxa de faltas das clínicas cair e as marcações duplicadas chegarem a zero.

## Documentos

| Documento | Caminho |
|--|--|
| Lean Canvas | [docs/produto/lean-canvas.md](docs/produto/lean-canvas.md) · [versão visual](docs/produto/lean-canvas.html) |
| Hipótese | [docs/produto/hipotese.md](docs/produto/hipotese.md) |
| PRD | [docs/produto/PRD.md](docs/produto/PRD.md) |
| Especificação funcional (histórias e critérios de aceite) | [docs/specs/especificacao-funcional.md](docs/specs/especificacao-funcional.md) |
| Harness do agente | [AGENTS.md](AGENTS.md) |
| ADR 0001 · Stack tecnológica | [docs/adr/0001-stack-tecnologica.md](docs/adr/0001-stack-tecnologica.md) |

## Stack

Definida no [ADR 0001](docs/adr/0001-stack-tecnologica.md):

| Camada | Escolha |
|--|--|
| Framework | Ruby on Rails 8 (monólito) |
| Frontend | Hotwire (Turbo + Stimulus), PWA |
| Banco de dados | PostgreSQL |
| Jobs e agendamento | Solid Queue |
| Testes | RSpec |
| Qualidade | Bullet (N+1) e RuboCop |

Hospedagem, provedores de WhatsApp e e-mail, assinatura digital e armazenamento de fotos seguem pendentes de ADR.

## Estrutura do repositório

| Caminho | Conteúdo |
|--|--|
| `/README.md` | Startup, POD, papéis e URL do MVP |
| `/AGENTS.md` | Harness do agente: regras, stack e limites |
| `/docs/produto/` | Lean Canvas, AI Canvas, PRD e evidências de discovery |
| `/docs/specs/` e `/docs/adr/` | Histórias, critérios de aceite e decisões de arquitetura |
| `/docs/diario/` | Diário agêntico por checkpoint |
| `/docs/pitch/` | pitch.md, pitch.pdf e roteiro da demo |
| `/architecture/` | Modelo LikeC4 (C1 e C2) |
| `/prototype/` | Telas HTML do protótipo |
| `/evals/` | Casos de avaliação da IA e script com a taxa de acerto |
| `/src/` e `/.github/` | Código do MVP e CI com testes e eval |

## Checkpoints

| Checkpoint | Entrega | Situação |
|--|--|--|
| 01 · Times e desafio | README, Lean Canvas, hipótese, PRD com os 6 pilares, AGENTS.md v0 | Em andamento |
| 02 · Produto | Discovery, AI Canvas, MoSCoW, histórias com critérios, PRD v1 | — |
| 03 · Protótipo | Telas HTML testadas, ADR do design system, diário #1 | — |
| 04 · Design C1/C2 | LikeC4, ADRs, walking skeleton com deploy e CI | — |
| 05 · MVP | URL pública, fluxo principal, testes e eval no CI, diário #2 | — |
| 06 · Pitch | Pitch com demo e material em /docs/pitch/ | — |
