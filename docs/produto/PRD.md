# PRD · Gestão de Clínicas de Estética

**Versão:** v0 (esqueleto, checkpoint 01) · **Dono:** Product Owner *(a definir)*
**Detalhe:** histórias, regras e critérios completos em [especificação funcional](../specs/especificacao-funcional.md). Este PRD resume; a especificação manda em caso de divergência.

## 1. Visão e objetivo

Ser a agenda e o prontuário da clínica de estética, instalados na tela inicial do celular, sem loja de aplicativos.

O MVP resolve o fluxo central da operação diária: o paciente marca sem risco de horário duplicado, recebe lembrete 24 horas antes e confirma presença; o profissional registra anamnese e fotos e colhe a assinatura do contrato nos procedimentos invasivos.

**Problema:** marcações duplicadas, faltas, documentação clínica dispersa e insegurança jurídica em procedimentos invasivos.

## 2. Público-alvo

| Persona | Dores | Necessidade |
|--|--|--|
| Gestor(a) da clínica | Horários vazios por falta; risco jurídico em procedimento invasivo | Agenda confiável e contratos guardados com integridade |
| Profissional / esteticista | Histórico do paciente espalhado; grade bagunçada | Ver a grade do dia e o histórico com fotos em um lugar |
| Recepção | Confirmar presença um a um por telefone ou WhatsApp | Agendar pelo paciente e ver quem confirmou |
| Paciente | Esquece o horário; precisa ligar para marcar | Marcar pelo celular e receber lembrete com o compromisso na agenda |

Primeiros clientes: clínicas pequenas e médias, com mais de um profissional, que fazem procedimentos invasivos *(hipótese, validar no discovery)*.

## 3. Requisitos funcionais (MVP)

| Módulo | O produto faz | Histórias |
|--|--|--|
| Administração | Cadastra profissionais e grades, procedimentos com duração e indicação de invasivo, usuários e perfis, modelos de contrato | HU01–HU04 |
| Acesso do paciente | Instala na tela inicial, cadastro com consentimento LGPD, cadastro pela recepção | HU05–HU07 |
| Agenda | Consulta por procedimento e profissional, reserva do horário por 5 minutos, confirmação, agendamento pela recepção, grade diária, bloqueio de folga, cancelamento *(proposta)* | HU08–HU13, HU25 |
| Prontuário | Anamnese fixa com exportação em PDF, fotos Antes/Depois, histórico do paciente | HU14–HU17 |
| Contratos | Gera contrato com variáveis, assinatura por *touchscreen*, consulta do contrato assinado | HU18–HU20 |
| Comunicação | Lembrete 24h por WhatsApp com "Sim/Não" e e-mail com anexo de calendário; acompanhamento das confirmações *(proposta)* | HU21–HU24 |

**Fora do MVP:** construtor de anamnese, assinatura remota, comparador de fotos, marca d'água, *push*, cache *offline*, visões semanal e mensal, insumos por sessão (ver "Não contempla" na especificação).

## 4. Requisitos não funcionais

| Tipo | Requisito |
|--|--|
| Plataforma | PWA instalável na tela inicial, *mobile first*, carregamento rápido *(meta de tempo a definir)* |
| Concorrência | Reserva temporária de 5 minutos; em cliques simultâneos só o primeiro vence; confirmação gravada por inteiro ou não gravada |
| Disponibilidade | Alta disponibilidade para acessos simultâneos à agenda *(meta a definir)* |
| Segurança | Controle de acesso por perfil; criptografia de fotos e dados sensíveis; contrato assinado em PDF não editável |
| Privacidade | Conformidade com a LGPD e normas de dados de saúde; consentimento no cadastro |
| Pontualidade | Verificação dos lembretes a cada 30 ou 60 minutos, sem envio duplicado |

## 5. Critérios de aceite

90 critérios no formato Dado/Quando/Então estão na especificação funcional. Os que definem o fluxo principal:

1. **Dado** duas pessoas selecionando o mesmo horário ao mesmo tempo, **quando** as seleções chegarem, **então** só a primeira obtém a reserva e a segunda é avisada (HU09).
1. **Dado** uma reserva não confirmada, **quando** se passarem 5 minutos, **então** o horário volta a aparecer livre para todos (HU09).
1. **Dado** uma reserva expirada, **quando** o paciente tentar confirmar, **então** a confirmação é recusada (HU10).
1. **Dado** um agendamento confirmado, **quando** a verificação encontrar o atendimento a 24 horas ou menos, **então** o paciente recebe o WhatsApp com "Sim/Não" e o e-mail com anexo de calendário, uma única vez (HU21, HU22).
1. **Dado** um lembrete recebido, **quando** o paciente responder "Sim", **então** o agendamento passa a "Presença confirmada" (HU23).
1. **Dado** um contrato assinado, **quando** qualquer usuário tentar alterá-lo ou excluí-lo, **então** a ação não é permitida (HU20).

## 6. Métricas de sucesso

| Métrica | Tipo | Meta |
|--|--|--|
| Taxa de faltas | Principal (instrumentar no MVP) | *definir no checkpoint 02* |
| Marcações duplicadas | Guarda | 0 |
| Lembretes respondidos com "Sim" | Engajamento | *a definir* |
| Agendamentos feitos pelo próprio paciente | Adoção | *a definir* |
| Procedimentos invasivos com contrato assinado | Conformidade | 100% *(proposta)* |

## Em aberto para o PRD v1

- **IA no produto:** a regra 01 do bootcamp exige IA como parte da proposta de valor, e o escopo atual não tem IA. Candidata em [hipotese.md](hipotese.md): previsão do risco de falta. Decidir no AI Canvas (checkpoint 02).
- Pendências de definição PD01–PD11 da especificação funcional.
- Priorização MoSCoW do MVP (checkpoint 02).
