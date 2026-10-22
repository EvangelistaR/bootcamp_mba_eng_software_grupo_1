---
name: rails-hotwire-ui
description: >
  Desenvolvimento de interface em Rails com ERB, partials, Turbo Drive,
  Turbo Frames, Turbo Streams, Stimulus, HTML acessível, formulários,
  melhoria progressiva e padrões de interação no frontend.
---

# UI com Rails, Hotwire e Stimulus

## Antes de implementar

- Inspecione as versões e convenções de Rails, Hotwire, Stimulus, CSS e JavaScript.
- Revise as views, layouts, partials, rotas e controllers relevantes.
- Inspecione o registro dos controllers Stimulus e o carregamento de assets.
- Entenda a resposta do servidor antes de desenhar uma nova interação.

## ERB e renderização

- Prefira HTML semântico e as convenções de layout existentes.
- Extraia partials quando o reuso ou a clareza justificar.
- Mantenha a lógica de negócio fora dos templates.
- Evite renderização condicional excessiva e marcação duplicada.
- Escape conteúdo controlado pelo usuário e evite renderização insegura de HTML.
- Preserve o retorno de validação dos formulários e os rótulos acessíveis.

## Turbo Drive

- Preserve a navegação normal, a menos que outra interação seja necessária.
- Considere o histórico do navegador, redirecionamentos e envios de formulário.
- Evite criar lógica de `fetch` própria para comportamentos que o Turbo já suporta.

## Turbo Frames

- Defina identificadores de frame estáveis e significativos.
- Garanta que as respostas contenham o frame esperado quando a navegação do frame exigir.
- Trate estados vazios, falhas de validação e limites de navegação.
- Evite frames profundamente aninhados sem um requisito claro.

## Turbo Streams

- Identifique o elemento alvo exato e a operação pretendida.
- Use append, prepend, replace, update, remove ou outras ações suportadas
  conforme o comportamento desejado.
- Garanta que as respostas de stream renderizadas no servidor e os alvos do DOM coincidam.
- Considere envios repetidos, conteúdo desatualizado e atualizações duplicadas.
- Verifique se o formato da resposta corresponde ao comportamento real do formulário ou link.

## Stimulus

- Mantenha os controllers focados em uma interação coerente.
- Use values, targets e actions para interfaces explícitas dos controllers.
- Mantenha regras de domínio e autorização no servidor.
- Evite controllers grandes com responsabilidades não relacionadas.
- Desconecte observers, listeners e outros recursos quando necessário.
- Trate deliberadamente targets ausentes e elementos opcionais.
- Evite estado global desnecessário e duplicação do estado do servidor.

## Acessibilidade e UX

- Use elementos semânticos, rótulos e atributos ARIA apropriados.
- Preserve a navegação por teclado e o comportamento de foco.
- Forneça mensagens úteis de validação e de erro.
- Considere os estados de carregamento, vazio, sucesso e falha.
- Evite tornar funcionalidades essenciais dependentes de JavaScript quando a
  melhoria progressiva for viável.
- Siga as convenções visuais e responsivas já existentes na aplicação.

## Verificação

- Adicione ou atualize testes para as interações importantes do usuário.
- Teste as atualizações do Turbo e o comportamento do Stimulus com as ferramentas já existentes no projeto.
- Não presuma que um framework específico de teste de navegador esteja instalado.
- Reporte os comportamentos de navegador que não puderam ser verificados.
