---
name: gerar-merge-request
description: Ajuda a escrever o texto de um Merge Request. Use quando o usuário pedir para gerar, criar ou escrever um MR, PR, Pull Request ou documentar alterações para uma branch.
---

## Como usar

Quando o usuário acionar esta skill, execute estritamente os seguintes passos:

**1. Definir a Branch de Destino:**
Verifique se o usuário informou a branch de destino (ex: development, master ou homologacao). Se ele não informou, pergunte qual é a branch alvo antes de prosseguir.

**2. Coletar o log de Commits:**
Use sua capacidade de executar comandos para rodar o seguinte script no terminal e obter o contexto das alterações:
`git log <branch_destino>..HEAD --oneline --no-merges`

**3. Gerar o MR:**
Use o resultado do comando acima e a sua capacidade de dedução de código para gerar a resposta. Você deve retornar APENAS o texto preenchido, usando o seguinte template Markdown:

**Título sugerido:** `tipo: breve descrição da alteração` (sugira usando o padrão Conventional Commits).

## O que estava acontecendo?
[Deduza o problema ou o contexto original com base no código alterado. Se for uma melhoria ou feature nova, explique brevemente a necessidade.]

## O que foi feito?
[Liste em bullet points as implementações e soluções técnicas adotadas. Use termos simples]

## Como testar?
[Crie um passo a passo lógico para o revisor. Deixe lacunas caso precise que o usuário preencha dados específicos de teste]

**4. Limpar repositório:**
Remova os arquivos gerados nesse processo de avaliação (como txt de diffs, por exemplo), para não sujar o repositório.
