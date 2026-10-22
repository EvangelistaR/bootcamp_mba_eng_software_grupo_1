---
name: rails-security
description: Orientações de segurança para implementação e revisão em Ruby on Rails, incluindo autorização, autenticação, CSRF, tratamento de entrada, mass assignment, SQL injection, XSS, segredos e exposição de dados. Use em mudanças sensíveis à segurança e em revisões de backend.
---

# Segurança em Rails

## Autorização e autenticação

- Identifique os mecanismos de autenticação e autorização existentes.
- Aplique o controle de acesso no servidor em toda operação protegida.
- Verifique permissões em nível de objeto, propriedade e fronteiras de tenant.
- Não presuma que elementos ocultos na UI oferecem segurança.
- Evite alterar o comportamento de autorização sem requisitos explícitos.

## Entrada e persistência

- Use *strong parameters* e a validação de entrada já estabelecida.
- Nunca interpole valores não confiáveis em SQL.
- Use as APIs seguras de consulta do Active Record sempre que apropriado.
- Revise as fronteiras de *mass assignment*.
- Considere condições de corrida na unicidade e nas transições de estado.

## HTML e JavaScript

- Preserve o escape do Rails para conteúdo HTML não confiável.
- Evite renderizar HTML bruto sem uma estratégia de sanitização justificada e segura.
- Evite inserção insegura no DOM e interpolação em JavaScript.
- Trate valores vindos do navegador como não confiáveis.
- Nunca dependa apenas da validação no cliente como fronteira de segurança.

## Requisições e sessões

- Preserve a proteção CSRF em requisições que alteram estado.
- Siga as convenções existentes de sessão e autenticação.
- Valide destinos de redirecionamento e URLs externas quando aplicável.
- Evite introduzir comportamento cross-origin inseguro.

## Dados e segredos

- Não leia, imprima, faça commit nem exponha credenciais ou segredos.
- Não registre em log senhas, tokens, identificadores de sessão ou payloads sensíveis.
- Minimize informações sensíveis em respostas e mensagens de erro.
- Evite incluir dados de produção em testes ou na saída de depuração.

## Revisão de segurança

Nas mudanças relevantes, avalie:
- Bypass de autenticação e autorização.
- Referências diretas inseguras a objetos (IDOR).
- SQL injection e construção insegura de consultas.
- Cross-site scripting e renderização insegura de HTML.
- CSRF e redirecionamentos inseguros.
- Exposição de dados sensíveis.
- Padrões inseguros e riscos de dependências.

Reporte os achados com severidade, comportamento afetado e uma remediação
concreta. Não afirme que uma auditoria de segurança é abrangente quando
apenas uma mudança restrita foi inspecionada.
