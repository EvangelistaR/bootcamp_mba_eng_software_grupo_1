---
name: code-review
description: >
  Revisa diffs de implementação quanto a corretude, regressões, segurança,
  convenções do Rails, riscos de banco de dados, desempenho, integração com
  Hotwire, qualidade dos testes e manutenibilidade, sem modificar arquivos.
---

# Revisão de Código

## Objetivo da revisão

Encontrar defeitos e riscos acionáveis introduzidos pela mudança atual.
Priorize corretude e prevenção de regressões sobre preferências de estilo.

## Procedimento

1. Inspecione a árvore de trabalho e o diff relevante.
2. Leia a implementação ao redor e os testes existentes.
3. Compare a mudança com os critérios de aceite.
4. Rastreie os caminhos de execução importantes e os cenários de falha.
5. Inspecione as fronteiras afetadas de banco de dados, autorização e UI.
6. Verifique se os testes protegem adequadamente o novo comportamento.
7. Reporte os achados com referência a arquivo e linha sempre que possível.

## Categorias de revisão

### Corretude
- Premissas incorretas, ramos ausentes e transições de estado inválidas.
- Tratamento de erro ou comportamento de resposta incorretos.
- Casos de borda e condições de corrida.

### Segurança
- Falta de autorização ou de verificação de acesso em nível de objeto.
- Tratamento inseguro de parâmetros ou *mass assignment*.
- Riscos de injeção, exposição de dados sensíveis e renderização insegura de HTML.

### Banco de dados e desempenho
- Consultas N+1 e consultas repetidas evitáveis.
- Falta de restrições de integridade ou migrações arriscadas.
- Limites de transação e premissas de concorrência incorretos.

### Rails e Hotwire
- Lógica de negócio vazando para as views.
- Abstrações desnecessárias ou callbacks complexos.
- Alvos de Turbo, respostas de frame ou ações de stream incorretos.
- Problemas de ciclo de vida e de tratamento de eventos no Stimulus.
- Regressões de acessibilidade.

### Testes
- Falta de testes para o comportamento alterado.
- Asserções que não verificam o contrato pretendido.
- Excesso de *mocks* que esconde defeitos de integração.
- Testes que passam sem exercitar o caminho relevante.

## Formato dos achados

Para cada achado, inclua:
- Severidade: crítica, alta, média ou baixa.
- Local: arquivo e linha, quando disponível.
- Problema: o que está incorreto ou arriscado.
- Impacto: um cenário concreto de falha.
- Recomendação: uma correção específica.

Reporte apenas achados acionáveis, sustentados pelo código ou por evidência
disponível. Não invente defeitos nem apresente preferências pessoais como bugs.

## Limites da revisão

- Não edite, crie nem exclua arquivos.
- Não faça stage, commit, push nem reescreva o histórico do Git.
- Não afirme que os testes passaram sem ter verificado a execução.
- Se não houver achados, diga isso explicitamente e mencione as limitações
  da revisão.
