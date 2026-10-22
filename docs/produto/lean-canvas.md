# Lean Canvas

Versão visual: [lean-canvas.html](lean-canvas.html). Itens marcados com *(hipótese)* não constam nas fontes e precisam ser validados no discovery. Referências (HU, PA, PD) apontam para a [especificação funcional](../specs/especificacao-funcional.md).

| Bloco | Conteúdo |
|--|--|
| **1. Problema** | Marcações duplicadas quando duas pessoas escolhem o mesmo horário ao mesmo tempo · Faltas: o paciente esquece ou não confirma presença · Anamnese e fotos de evolução dispersas, sem histórico único · Insegurança jurídica em procedimentos invasivos sem contrato assinado e guardado · Dados de saúde e imagens exigem tratamento conforme a LGPD |
| **Alternativas existentes** | Agenda em papel, planilha ou conversa de WhatsApp *(hipótese)* · Termos de consentimento em papel *(hipótese)* · Aplicativos que exigem download em loja |
| **2. Segmentos de clientes** | Clínicas de estética (quem contrata: gestor ou administrador) · Profissionais e esteticistas · Recepção · Pacientes |
| **Primeiros clientes** | Clínicas pequenas e médias, com mais de um profissional, que fazem procedimentos invasivos *(hipótese)* |
| **3. Proposta única de valor** | Agenda sem marcação dupla, lembretes que reduzem faltas e prontuário com contrato assinado, num app que o paciente instala sem loja. |
| **Conceito de alto nível** | A agenda e o prontuário da clínica de estética na tela inicial do celular. |
| **4. Solução** | Horário reservado por 5 minutos para quem clicou primeiro (HU09) · Lembrete 24h antes por WhatsApp com "Sim/Não" e por e-mail com anexo de calendário (HU21–23) · Histórico do paciente com anamnese em PDF e fotos Antes/Depois (HU14–17) · Contrato com variáveis, assinado na tela e guardado em PDF não editável (HU18–20) |
| **5. Canais** | Link do PWA, instalável na tela inicial sem loja (HU05) · Lembretes por WhatsApp e e-mail como contato recorrente · Link de agendamento divulgado pela clínica nas redes sociais *(hipótese)* · Venda direta e indicação entre clínicas *(hipótese)* |
| **6. Fontes de receita** | Assinatura mensal por clínica ou por profissional *(hipótese)* · Pacote de mensagens WhatsApp por volume *(hipótese)* · Plano superior com as entregas futuras (PA01–17) *(hipótese)* |
| **7. Estrutura de custos** | Desenvolvimento e manutenção · Hospedagem com alta disponibilidade · Armazenamento criptografado de fotos e documentos · Custo por mensagem no canal oficial do WhatsApp (PA07) · E-mail transacional · Jurídico e DPO: contratos, termos LGPD e validade da assinatura (PD07–09) · Suporte e implantação *(hipótese)* |
| **8. Métricas-chave** | Taxa de faltas antes e depois da adoção · Marcações duplicadas: meta zero · % de lembretes respondidos com "Sim" · % de agendamentos feitos pelo próprio paciente · % de procedimentos invasivos com contrato assinado · Reservas expiradas sem confirmação · Clínicas ativas e retenção mensal *(hipótese)* |
| **9. Vantagem injusta** | Agenda, prontuário e contrato ligados ao mesmo atendimento · Histórico de evolução acumulado por paciente, que dificulta a troca de sistema *(hipótese)* · Atenção: trava de horário e lembretes são copiáveis; a vantagem real ainda precisa ser validada |
