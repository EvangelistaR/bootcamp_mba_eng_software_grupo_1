# ADR 0001 · Stack tecnológica

- **Status:** Aprovada
- **Data:** 2026-10-21
- **Checkpoint:** 03/04

## Contexto

O `AGENTS.md` deixa a stack em aberto e proíbe adicionar framework, biblioteca ou serviço sem ADR aprovado. Requisitos já fixados pelo projeto:

- PWA *mobile first* e instalável.
- Agenda sem marcação duplicada, com reserva temporária de 5 minutos, prioridade do primeiro clique e confirmação atômica.
- Tarefa agendada para lembretes, a cada 30 ou 60 minutos.
- Integrações: WhatsApp (canal oficial), e-mail transacional e anexo `.ics`.
- Fotos e dados de saúde sensíveis (LGPD): acesso por perfil e criptografia.
- Time pequeno (3 pessoas) operando agentes de IA, com MVP público no checkpoint 05.

Os agentes e skills já versionados em `.claude/` assumem Rails + Hotwire.

## Decisão

| Camada | Escolha |
|--|--|
| Framework | Ruby on Rails 8, monólito |
| Frontend | Hotwire (Turbo + Stimulus), renderização no servidor, PWA via manifest e service worker |
| Banco de dados | PostgreSQL |
| Jobs e agendamento | Solid Queue, com tarefa recorrente para lembretes e expiração de reservas |
| Testes | RSpec (`rspec-rails`); o nome de cada exemplo cita a HU de origem, ex.: `describe "HU09 ..."` |
| Detecção de N+1 | Bullet, apenas nos grupos `development` e `test`; alertas fazem os testes falharem |
| Linter | RuboCop (com `rubocop-rails` e `rubocop-rspec`), executado localmente e no CI |

### Reserva sem duplicidade

A garantia de "zero marcação duplicada" fica **no banco**, não só na aplicação: uma *exclusion constraint* do PostgreSQL (`btree_gist`) sobre `profissional` e intervalo de tempo impede sobreposição, mesmo sob concorrência. A confirmação da reserva roda em transação. O primeiro clique vence porque o segundo `INSERT` falha na constraint.

### Fora desta decisão (pendências)

- **Hospedagem e deploy:** provedor não definido. Responsável: Quality & Ops. Requisito: PostgreSQL gerenciado, HTTPS e deploy a partir do CI.
- **WhatsApp (canal oficial) e e-mail transacional:** provedores a escolher em ADR própria. Até lá, a aplicação deve isolar cada integração atrás de uma interface.
- **Assinatura digital de contratos:** abordagem a definir em ADR própria, após a especificação.
- **Armazenamento de fotos:** serviço e criptografia a definir em ADR própria (Active Storage é o candidato natural).

## Alternativas consideradas

| Alternativa | Por que não |
|--|--|
| Next.js + API | Duas camadas para um time de 3; exigiria reescrever agentes e skills. |
| Django + HTMX | Boa opção, mas sem ganho que compense reescrever o harness já existente. |
| SQLite | Sem *exclusion constraint*; a unicidade dependeria só da aplicação. |
| MySQL | Também sem *exclusion constraint* nativa. |
| Minitest | Padrão do Rails, mas a sintaxe `describe`/`context` do RSpec mapeia melhor os critérios Dado/Quando/Então e já é o que o `tech-lead` e as skills assumem. |
| Sem Bullet (revisão manual de N+1) | Depende de atenção humana; o Bullet detecta N+1 e *eager loading* desnecessário automaticamente nos testes. |
| Standard Ruby no lugar do RuboCop | Menos configurável; o RuboCop com extensões cobre regras de Rails e RSpec. |
| Redis + Sidekiq | Serviço extra para operar; Solid Queue usa o próprio banco e basta para a carga do MVP. |

## Consequências

**Positivas**

- Um único deploy e uma única linguagem; menos superfície para o time operar.
- Integridade da agenda garantida pelo banco.
- Convenções do Rails reduzem decisões e favorecem o trabalho dos agentes.

**Negativas e riscos**

- Rails depende de `btree_gist`, ou seja, o provedor de hospedagem precisa oferecer PostgreSQL com essa extensão.
- Solid Queue no mesmo banco pode competir por conexões; reavaliar se a carga crescer.
- PWA com service worker em Hotwire exige cuidado com cache offline de dados sensíveis (não cachear dados de pacientes).
- RSpec não vem no Rails por padrão: `rspec-rails` entra como dependência de desenvolvimento e teste, coberta por esta ADR.
- Bullet só pode rodar em `development` e `test`; nunca em produção. Com alertas quebrando os testes, falsos positivos exigem exceções explícitas e justificadas.
- RuboCop e suas extensões (`rubocop-rails`, `rubocop-rspec`) entram como dependências de desenvolvimento; a configuração (`.rubocop.yml`) deve ser enxuta para não gerar ruído.
- Time pode ter menos familiaridade com Ruby: risco a validar com o POD.

## Aprovação

| Papel | Nome | Data | Decisão |
|--|--|--|--|
| Tech Lead | *a definir* | 2026-10-21 | Aprovada |
