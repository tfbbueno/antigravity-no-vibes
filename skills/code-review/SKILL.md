---
name: code-review-didatico
description: Realiza um code review detalhado do repositório aberto, avaliando Clean Code, SOLID, Segurança, Tratamento de Exceções, Boas Práticas Ágeis e Padrões de Nomenclatura (Código e Commits). Explica os conceitos do zero de forma didática para iniciantes, sugere melhorias imediatas, issues futuras e fornece feedback positivo.
---

## Como usar

Quando a usuária acionar esta skill solicitando um code review, execute estritamente os seguintes passos de forma autônoma:

**1. Definir a Branch de Destino:**
Verifique se a usuária informou a branch alvo (ex: development, master ou homologacao). Se ela não informou, pergunte qual é a branch antes de prosseguir.

**2. Coletar o Diff de Código e Histórico de Commits:**
Use sua capacidade de executar comandos no terminal para rodar os scripts abaixo. 
Para obter as alterações exatas (diff) da usuária:
`git diff <branch_destino>...HEAD -w`
Para obter o histórico de commits dessa entrega:
`git log <branch_destino>..HEAD --no-merges --pretty=format:"%h - %s"`

**3. Análise Multidimensional (O que avaliar):**
Analise o diff e os commits, identifique o ecossistema e avalie as seguintes categorias:
* **Padrões de Nomenclatura (Naming Conventions):** Variáveis e atributos devem ser substantivos claros (ex: `dadosCliente` em vez de `d`, `data` ou `obj`). Métodos devem ser verbos de ação (ex: `calcularTotal` em vez de `total`). Respeito ao padrão do ecossistema (camelCase, PascalCase, snake_case).
* **Histórico de Commits (Semantic Commits):** Avalie se as mensagens seguem convenções (ex: `feat:`, `fix:`, `chore:`), se descrevem claramente *o que* foi feito e o *motivo*, e se usam o tempo verbal adequado (imperativo).
* **Clean Code:** Métodos pequenos, responsabilidade única, evitar "magic numbers" ou strings hardcoded.
* **SOLID & Arquitetura:** Alto acoplamento, classes "faz-tudo" (ferindo o SRP), ou lógicas engessadas.
* **Pragmatismo (KISS, DRY, YAGNI):** Lógicas desnecessariamente complexas, código duplicado que poderia virar um método utilitário, ou superengenharia.
* **Segurança (OWASP):** Riscos de injeção (ex: concatenação de SQL), senhas/chaves hardcoded, ou falta de validação de dados de entrada.
* **Resiliência & Testabilidade:** Blocos `try-catch` que engolem erros silenciosamente, uso genérico de `Exception`, ou métodos impossíveis de testar isoladamente.
* **Fluxo Ágil (Tamanho do MR):** Avalie o volume de arquivos alterados e a quantidade de commits. Entregas gigantes geram gargalos na Sprint e dificultam a revisão da equipe.
* **Usabilidade**: Avalie a usabilidade nas telas desenvolvidas.
* **SonarQube**: Avalie os arquivos conforme padrões do SonarQube

**4. Regra de Ouro da Comunicação (Mentoria Didática):**
Você assumirá a postura de uma mentora sênior ensinando uma iniciante. **NENHUM conceito técnico deve ser citado sem explicação.** Se você identificar um nome de variável ruim, explique o conceito de "Código Autodocumentado" usando analogias simples. Justifique o *porquê* de cada mudança com foco na facilidade de leitura para o resto da equipe e na vida útil do software.

**5. Gerar o Relatório:**
Sua resposta deve ser formatada em Markdown, contendo EXATAMENTE as seções abaixo:

### Code Smells, Nomenclatura e Melhorias Imediatas (Pré-Merge)
[Liste os problemas críticos de Clean Code, Nomenclatura de variáveis/métodos, Segurança ou Exceções que DEVEM ser corrigidos agora. Para cada um, forneça:]
* **O Conceito:** (Explique a teoria de forma simples e analógica).
* **Onde está:** (Indique o arquivo e o trecho).
* **Por que melhorar:** (O impacto negativo a longo prazo na legibilidade).
* **Sugestão de correção:** (Bloco de código ANTES e DEPOIS).

### Arquitetura e Pragmatismo (SOLID, DRY, KISS)
[Liste problemas estruturais ou repetições. Mostre como simplificar a lógica ou desacoplar as classes, sempre explicando o princípio por trás da sugestão. Para cada problema, forneça:]
* **O Conceito:** (Explique a teoria de forma simples e analógica).
* **Onde está:** (Indique o arquivo e o trecho).
* **Por que melhorar:** (O impacto negativo a longo prazo).
* **Sugestão de correção:** (Bloco de código ANTES e DEPOIS).
* **Essa é uma melhoria fora de escopo?:** (Informar se deve fazer essa melhoria de imediato ou não).

### Avaliação dos Commits
[Analise as mensagens de commit coletadas feitas no diff. Forneça feedback didático se os commits carecem de clareza, se estão muito genéricos (ex: "ajustes", "commit final") ou se não seguem padrões semânticos. Dê exemplos de como a mensagem poderia ser reescrita para gerar um histórico legível.]

### Melhorias Fora de Escopo (Criar Issues)
[Liste refatorações maiores que atrasariam a entrega atual se fossem feitas agora. Sugira que a usuária crie um card/issue de melhoria técnica (Débito Técnico) no backlog para não travar o fluxo da Sprint.]

### Feedback de Fluxo Ágil
[Comente brevemente sobre o tamanho deste Merge Request. Se estiver muito grande, explique didaticamente por que quebrar as entregas em lotes menores ajuda a equipe a revisar mais rápido e evita conflitos de código.]
Se houver itens não commitados, sugira o texto do commit usando Conventional Commits

### O que ficou bom 
[Identifique lógicas inteligentes, bons nomes escolhidos de forma clara, bons commits, bom uso de recursos da linguagem ou modularização correta. Explique *por que* aquelas escolhas são exemplos de um código de alta qualidade.]

**6. Limpar repositório:**
Remova todos os arquivos gerados nesse processo de avaliação (como txt de diffs, commits ou logs), para não sujar o repositório da usuária.