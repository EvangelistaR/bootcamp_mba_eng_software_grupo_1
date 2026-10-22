---
name: rails-testing
description: >
  Estratégia de testes para aplicações Rails, incluindo testes de model,
  request, controller, job, service, view, system, Turbo, Stimulus e regressão.
---

# Estratégia de Testes em Rails

## Descubra a stack de testes

- Inspecione o Gemfile, o Gemfile.lock, `test/`, `spec/` e a configuração de testes existente.
- Determine se o projeto usa RSpec, Minitest ou outra configuração estabelecida.
- Reaproveite factories, fixtures, shared examples, helpers e módulos de suporte existentes.
- Não adicione dependência de teste sem justificativa.

## Desenho dos testes

- Derive os testes dos critérios de aceite e do comportamento observável.
- Prefira testes que falhem quando o comportamento pretendido regredir.
- Cubra o comportamento de sucesso, as entradas inválidas relevantes e os casos de borda importantes.
- Evite asserções sobre detalhes de implementação, a menos que protejam um contrato relevante.
- Mantenha o setup dos testes explícito e minimize *mocks* desnecessários.
- Use *verifying doubles* quando o framework de testes existente os suportar.
- Evite testes que apenas duplicam a lógica da implementação.

## Escolha o nível de teste adequado

- Testes de model: validações, associações, scopes e invariantes de domínio.
- Testes de request: roteamento, autenticação, autorização, parâmetros e respostas.
- Testes de service: orquestração e comportamento de negócio relevante.
- Testes de job: comportamento independente do agendamento, retentativas e efeitos colaterais.
- Testes de view: renderização importante, quando suportado pelas convenções do projeto.
- Testes de sistema: fluxos críticos de ponta a ponta e interações visíveis ao usuário.
- Testes de JavaScript: comportamento do Stimulus quando o projeto tiver ferramental adequado.

## Hotwire e Stimulus

- Verifique a resposta esperada de Turbo Frame ou Turbo Stream.
- Asserte as mudanças relevantes no DOM quando a stack de testes existente permitir.
- Cubra erros de formulário e atualizações bem-sucedidas.
- Teste o comportamento do Stimulus com as ferramentas de JavaScript ou de testes de sistema já estabelecidas.
- Evite depender exclusivamente de testes de backend para interações críticas de UI.

## Execução das verificações

1. Rode primeiro o teste mais restrito e relevante.
2. Rode os testes de regressão relacionados.
3. Rode verificações mais amplas quando apropriado e viável.
4. Use os comandos documentados no repositório, na configuração de CI ou nos scripts do projeto.
5. Registre o status de saída real e as falhas.
6. Distinga os testes que passaram dos que não foram executados.

## Relatório

Em toda tarefa, reporte:
- Testes adicionados ou modificados.
- Comandos executados.
- Resultados reais.
- Lacunas de cobertura conhecidas e comportamentos não verificados.

Nunca fabrique resultados de testes nem afirme cobertura completa sem evidência.
