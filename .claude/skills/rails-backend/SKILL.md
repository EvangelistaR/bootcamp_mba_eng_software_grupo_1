---
name: rails-backend
description: >
  Boas práticas de backend Rails para Active Record, migrações, controllers,
  lógica de domínio, services, jobs, autorização, segurança, desempenho e
  código de servidor manutenível.
---

# Engenharia de Backend Rails

## Antes de implementar

- Inspecione o Gemfile, o Gemfile.lock, a versão do Rails e a arquitetura existente.
- Leia os models, controllers, rotas, policies, services e jobs relevantes.
- Identifique os testes e as convenções existentes.
- Não presuma que gems opcionais ou camadas arquiteturais existam.

## Models e Active Record

- Modele explicitamente as associações e relações de banco que fazem sentido.
- Use validações para a integridade dos dados no nível do model, quando apropriado.
- Use restrições de banco para invariantes que devem valer sob escritas concorrentes.
- Não use validações da aplicação como substituto de índices únicos.
- Evite callbacks para fluxos de negócio complexos ou efeitos colaterais ocultos.
- Use scopes e query objects apenas quando melhorarem a clareza.
- Previna consultas N+1 com *eager loading* adequado.
- Selecione apenas as colunas necessárias quando o volume de consultas ou o tamanho da resposta justificar.

## Controllers e lógica de domínio

- Mantenha os controllers focados em tratar a requisição, autorizar e responder.
- Coloque as regras de negócio no objeto de domínio apropriado.
- Introduza service objects apenas para orquestração relevante ou fluxos reutilizáveis.
- Evite abstrações genéricas criadas para uma única operação trivial.
- Preserve os formatos de resposta e a semântica HTTP já estabelecidos.
- Trate explicitamente entradas inválidas e falhas de domínio esperadas.

## Mudanças no banco de dados

- Inspecione primeiro o schema e as convenções de migração.
- Considere o tamanho da tabela, locks, índices e compatibilidade com o deploy.
- Adicione índices com base nos padrões de acesso e nos requisitos de integridade.
- Preserve os dados e considere o comportamento de *rollback*.
- Não execute operações destrutivas no banco sem autorização explícita.
- Não redefina nem modifique dados de produção.

## Segurança

- Aplique autorização em toda operação protegida no servidor.
- Valide e restrinja a entrada do usuário.
- Use *strong parameters* ou o equivalente já existente.
- Evite vulnerabilidades de *mass assignment*.
- Proteja informações sensíveis em logs e respostas de erro.
- Considere SQL injection, IDOR, CSRF e desserialização insegura.
- Nunca exponha segredos nem copie credenciais do ambiente para o código.

## Processamento em segundo plano

- Siga o framework de jobs e as convenções de retentativa existentes.
- Projete jobs idempotentes quando retentativas puderem repetir efeitos colaterais.
- Considere limites de transação, concorrência e tratamento de falhas.
- Evite passar objetos serializados grandes ou sensíveis sem necessidade.

## Desempenho

- Investigue os padrões de consulta antes de otimizar.
- Considere índices, *eager loading*, paginação e escopo de transação.
- Evite cache prematuro ou nova infraestrutura sem evidência.
- Não sacrifique a corretude por ganhos de desempenho especulativos.

## Verificação

- Adicione testes de regressão para o comportamento alterado.
- Teste autorização, entrada inválida, falhas de domínio e casos de borda quando relevante.
- Use os comandos já existentes no projeto em vez de inventar novos.
- Reporte explicitamente as verificações não executadas e seus bloqueios.
