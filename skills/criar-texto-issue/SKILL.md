---
name: criar-texto-issue
description: Cria texto de issues detalhadas focadas em manutenção e qualidade para o GitLab, baseadas em code reviews.
---

## Como usar

Quando acionada, sua função é gerar textos prontos para serem cadastrados como issues no GitLab do time, baseando-se nos problemas identificados no code review mais recente. Execute estritamente os seguintes passos de forma autônoma:

**1. Verificação de Contexto:**
Verifique se você possui o contexto de um code review realizado imediatamente antes. Caso não encontre esse contexto na memória, pare a execução imediatamente e peça para a usuária executar a skill de code review primeiro.

**2. Geração das Issues:**
Para cada problema encontrado no code review, crie uma issue separada. Você DEVE encapsular a resposta de cada issue inteiramente dentro de um bloco de código (usando as crases ` ```markdown `) para que a usuária possa copiar o texto facilmente, preservando toda a formatação original para o GitLab.

Preencha as informações seguindo rigorosamente as instruções da tag `<template_issue>` abaixo, substituindo os textos entre colchetes `< >`:

<template_issue>
```markdown
# <Insira aqui um título claro e acionável para a issue>

## Origem da demanda

Code review

## Descrição

<Insira a descrição do problema. Explique o que deve ser feito e dê exemplos práticos de como o código deveria estar. Assuma a postura de uma desenvolvedora sênior orientando um desenvolvedor júnior. Use um tom profissional, técnico e didático. **NENHUM conceito técnico deve ser citado sem explicação, mas evite estritamente analogias lúdicas ou fora do contexto de software (como exemplos com hotéis, carros, etc).** Explique os conceitos (como falhas de segurança ou padrões de projeto) baseando-se no fluxo de dados, na arquitetura ou em cenários do próprio sistema. Se identificar variáveis com nomes genéricos, explique "Código Autodocumentado" mostrando o impacto direto na leitura do código. Justifique o *porquê* de cada mudança focando na manutenção do software em longo prazo.>

## Comportamento Esperado

<Descreva o comportamento de negócio, de arquitetura ou o fluxo de dados que o sistema deve apresentar após a correção e refatoração.>

## Passos para reproduzir (se aplicável)

<Se o problema relatado puder causar um bug reproduzível na interface ou na API, insira o passo a passo em forma de lista numerada. Caso seja puramente um problema estrutural de código ou refatoração, escreva "Não se aplica".>

## Critérios de Aceite

<Liste os requisitos necessários para garantir que o problema foi resolvido, em formato de checklist do GitLab:
- [ ] <Critério 1>
- [ ] <Critério 2>>
```
</template_issue>

**3. Limpeza de Repositório:**
Após gerar os textos, confirme que nenhum arquivo residual de análise (como .txt de diffs, relatórios soltos ou logs) foi salvo no repositório de trabalho local, mantendo o ambiente limpo.

