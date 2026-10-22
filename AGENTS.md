# AGENTS.md · v1

Harness do agente deste repositório. Vale para qualquer ferramenta (Claude Code, Copilot, Cursor, Kiro). Evolui a cada checkpoint; registre as mudanças no fim do arquivo.

## Projeto

PWA para clínicas de estética: agenda sem marcação duplicada, lembretes 24h por WhatsApp e e-mail, prontuário com anamnese e fotos, contratos com assinatura digital. Visão e escopo em [docs/produto/PRD.md](docs/produto/PRD.md).

## Fonte da verdade

1. [docs/specs/especificacao-funcional.md](docs/specs/especificacao-funcional.md): histórias (HU), regras (RN), critérios de aceite, pendências (PD).
1. [docs/produto/PRD.md](docs/produto/PRD.md): visão, público, requisitos e métricas.
1. `docs/adr/`: decisões técnicas (a partir do checkpoint 03).
1. `architecture/`: C1 e C2 em LikeC4 (a partir do checkpoint 04).

Se o código e a especificação divergirem, a especificação vence. Se a especificação não cobrir o caso, **pare e pergunte**; não invente regra de negócio.

## Stack

Definida em [ADR 0001](docs/adr/0001-stack-tecnologica.md):

- Ruby on Rails 8, monólito.
- Hotwire (Turbo + Stimulus), renderização no servidor; PWA via manifest e service worker.
- PostgreSQL. A unicidade da agenda é garantida no banco, com *exclusion constraint* (`btree_gist`).
- Solid Queue para jobs, com tarefa recorrente para lembretes e expiração de reservas.
- RSpec (`rspec-rails`) para testes.
- Bullet (só em `development` e `test`) para detectar N+1.
- RuboCop (`rubocop-rails`, `rubocop-rspec`) como linter.

Já fixado pela especificação:

- Frontend PWA, *mobile first*, instalável.
- Reserva temporária de horário por 5 minutos, com prioridade do primeiro clique e confirmação atômica.
- Tarefa agendada para os lembretes, a cada 30 ou 60 minutos.
- Integrações: WhatsApp (canal oficial), e-mail transacional, anexo de calendário `.ics`.

Ainda sem ADR (não implemente até existir): hospedagem e deploy, provedores de WhatsApp e e-mail, assinatura digital de contratos, armazenamento de fotos. Isole cada integração atrás de uma interface.

Não adicione framework, biblioteca ou serviço sem ADR aprovado pelo Tech Lead.

## Regras

- **Spec antes do código:** toda mudança parte de uma HU. O PR cita os IDs (ex.: `HU09`).
- **Testes como contrato:** cada critério Dado/Quando/Então vira teste; o nome do teste cita a HU de origem.
- **Rastreabilidade:** história → critério → PR → teste. Teste sem HU de origem não entra.
- **Fora do escopo:** itens de "Não contempla" e pontos em aberto (PA) não são implementados no MVP.
- **Pendências:** comportamento que depende de uma PD aberta fica bloqueado; sinalize no PR, não escolha sozinho.
- **Idioma:** documentação e mensagens ao usuário em português; código e identificadores em inglês.

## Segurança e LGPD

- Nunca coloque segredos no repositório: tokens, chaves, senhas, `.env`. Use variáveis de ambiente e um `.env.example` sem valores.
- Nunca use dados reais de pacientes em código, testes, *seeds* ou exemplos; só dados fictícios.
- Fotos e dados de saúde são sensíveis: acesso por perfil e criptografia, nunca em log.
- Contrato assinado é imutável: nenhum fluxo pode alterar ou excluir.

## Limites do agente

- Não faz merge nem push na `main`; todo PR é revisado por outro membro do POD.
- No máximo 2 PRs abertos ao mesmo tempo: revise antes de gerar mais.
- Não altera `docs/produto/` nem `docs/specs/` sem pedido do Product Owner.
- Não cria nem remove tags de checkpoint.
- Registra no diário (`docs/diario/`) o que fez, onde errou e onde o POD interveio.

## Estrutura

Ver a tabela de estrutura no [README.md](README.md).

## Histórico

| Versão | Checkpoint | Mudança |
|--|--|--|
| v0 | 01 | Versão inicial: fonte da verdade, regras, segurança e limites. Stack a definir. |
| v1 | 03 | Stack definida conforme ADR 0001 (Rails 8, Hotwire, PostgreSQL, Solid Queue, RSpec, Bullet, RuboCop). Pendências de ADR listadas. |
