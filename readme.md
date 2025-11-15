 1. Introdução

Este documento apresenta o processo completo de análise estática e refatoração de um trecho de código HTML baseado na página inicial da documentação do Bootstrap.
O objetivo é identificar problemas relacionados a acessibilidade, segurança, desempenho e manutenibilidade, propondo e aplicando melhorias sem alterar o comportamento funcional do sistema.

 2. Objetivos da Atividade

- Realizar análise estática do código fornecido.
- Identificar más práticas, vulnerabilidades e oportunidades de melhoria.
- Propor um plano de refatoração consistente e justificado.
- Implementar a refatoração diretamente no HTML.
- Gerar um relatório final consolidando o processo.

 3. Descrição do Projeto Selecionado

- O código analisado corresponde a uma página HTML integrada a Jekyll, contendo:
- Seção principal (hero) com imagem e botões de navegação.
- Três seções informativas ("follow-up cards"): Instalação, BootstrapCDN e Temas Oficiais.
- Inclusões do Jekyll ({% include %}), variáveis do Jekyll ({{ site.* }}) e blocos de destaque ({% highlight %}).
- Embora visualmente completo, o código apresentava problemas estruturais comuns em projetos de front-end, especialmente relacionados à acessibilidade, organização e segurança.

 4. Relatório de Análise Estática

- A análise foi conduzida manualmente, considerando critérios das seguintes ferramentas:
- SonarQube (qualidade de código e vulnerabilidades)
- HTMLHint (linting de HTML)
- Lighthouse (performance e acessibilidade)
- axe-core (acessibilidade)
- Boas práticas do W3C

 Problemas Identificados
4.1 Acessibilidade (A11Y)

- alt vazio ou pouco descritivo em imagens.
- Falta de landmarks ARIA para navegação assistiva.
- Ausência de aria-label em alguns elementos interativos.
- Imagens grandes sem atributos loading="lazy" e decoding="async".

4.2 Segurança

- Uso de onclick inline → viola boas práticas de CSP.
- Links externos sem rel="noopener noreferrer".

4.3 Performance

- Imagens grandes sem srcset ou <picture>.
- Scripts carregados sem defer.

4.4 Organização e Manutenibilidade

- Estruturas repetidas nos três cards (violação indireta de DRY).
- Classes redundantes do Bootstrap.
- Uso misto de responsabilidades (markup + lógica).

 5. Plano de Refatoração

Com base nos problemas identificados, o plano consiste em quatro frentes:

5.1 Acessibilidade

- Criar textos alternativos adequados.
- Adicionar landmarks ARIA e associações semânticas (aria-labelledby).
- Garantir melhor navegação por teclado.

5.2 Segurança

- Remover todos os eventos inline (onclick).
- Adicionar atributos rel="noopener noreferrer".

5.3 Performance

- Aplicar loading="lazy" e decoding="async" às imagens.
- Criar imagens responsivas com <picture> e srcset.
- Adicionar defer nos scripts CDN.

5.4 Organização do Código

- Eliminar classes redundantes.
- Sugerir modularização via includes para trechos repetidos.
- Separar a lógica de rastreamento (data-ga-*) para um script externo.

 6. Implementação da Refatoração

As melhorias foram aplicadas exclusivamente no HTML, atendendo ao requisito do trabalho. Os principais ajustes incluem:

- Melhoria dos textos alternativos (alt) com descrições relevantes.
- Substituição de onclick por atributos data-*. 
- Inclusão de <picture> com srcset e sizes.
- Inclusão de loading="lazy" e decoding="async".
- Adoção de landmarks ARIA.
- Ajustes semânticos (IDs, headings ocultos, roles).
- Links externos atualizados para uso seguro.
- Remoção de classes redundantes.

 7. Resultados Obtidos com a Refatoração
! Acessibilidade!

- Melhor navegação para leitores de tela.
- Document outline mais claro.
- Elementos com descrição apropriada.

 !Segurança!

- Melhoria de compatibilidade com políticas CSP.
- Prevenção de ataques via window.opener.

 !Performance!

- Redução do carregamento inicial das imagens.
- Melhor pontuação em métricas como Largest Contentful Paint.
- Manutenibilidade
- Código mais limpo, padronizado e modularizável.
- Mais fácil de manter e evoluir.

 8. Conclusão

O processo de análise e refatoração permitiu elevar significativamente a qualidade do HTML fornecido. O código final está mais:

- acessível
- seguro
- performático
- organizado
- aderente a boas práticas modernas de desenvolvimento front-end

As melhorias foram aplicadas sem alterar o comportamento visual ou funcional do conteúdo original.
