# Hipótese de valor

> **Acreditamos que** uma agenda online que garante o horário a quem escolhe primeiro, com lembretes automáticos por WhatsApp e e-mail 24 horas antes e confirmação "Sim/Não",
> **para** clínicas de estética com mais de um profissional e seus pacientes,
> **vai gerar** menos faltas e nenhuma marcação duplicada.
> **Saberemos que é verdade quando** a taxa de faltas das clínicas cair e as marcações duplicadas chegarem a zero.

## Como medir

| Métrica | Como se calcula | Linha de base | Meta |
|--|--|--|--|
| Taxa de faltas (métrica principal) | Atendimentos sem comparecimento ÷ atendimentos agendados, por mês | *levantar no discovery* | *definir no checkpoint 02* |
| Marcações duplicadas | Horários do mesmo profissional com mais de um agendamento confirmado | *levantar no discovery* | 0 |
| Confirmação pelo lembrete | Lembretes respondidos com "Sim" ÷ lembretes enviados | — | *definir no checkpoint 02* |

## Como testar

- **Discovery (checkpoint 02):** entrevistar clínicas para levantar a taxa de faltas atual e como a agenda é feita hoje.
- **Protótipo (checkpoint 03):** pacientes e recepcionistas navegam no fluxo de agendamento e de confirmação pelo lembrete.

## Ponto de atenção: IA no produto

A regra 01 do bootcamp exige **IA como parte da proposta de valor**. A hipótese acima ainda não depende de IA. Variante proposta para discutir no POD e registrar no AI Canvas:

> Acreditamos que **prever o risco de falta de cada agendamento com IA**, e agir antes (reforçar o lembrete, pedir confirmação à recepção, oferecer o horário à lista de espera), para clínicas de estética, vai gerar menos horários vazios. Saberemos que é verdade quando a taxa de faltas cair mais nas clínicas que usam a previsão do que nas que só recebem o lembrete.

*(proposta: ainda não validada nem incluída no escopo da especificação funcional)*
