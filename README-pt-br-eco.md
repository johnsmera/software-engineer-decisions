# Estabilizando um Projeto React Sob Pressão de Prazo

Este repositório documenta uma intervenção real em um projeto React que estava próximo do lançamento e apresentava sinais claros de risco estrutural.

Não é um tutorial nem um guia de boas práticas.
É um relato técnico sobre tomada de decisão sob pressão, dinâmica de equipe e trade-offs entre qualidade técnica e continuidade do negócio.

> 🇺🇸 Versão em inglês: [README.md](./README.md)

---

## Contexto

O projeto era um sistema interno desenvolvido durante a bolha de investimentos da pandemia.
A empresa contratou vários desenvolvedores em um curto espaço de tempo para construir uma aplicação em React com prazo fechado.

Entrei no projeto já em estágio avançado, quando o sistema estava próximo do lançamento.

Na primeira análise técnica, ficou claro que o maior risco não era atrasar a entrega, mas lançar um sistema que se tornaria instável e difícil de manter logo após o go-live.

---

## Estado Inicial

A base de código apresentava uma combinação de problemas que, juntos, elevavam significativamente o risco técnico:

- Ausência de TypeScript (aceitável dado o contexto, mas relevante)
- Nenhum uso de ESLint ou análise estática
- Padrões de código inconsistentes
- Uso excessivo de props e dependências implícitas
- Efeitos colaterais declarados após a lógica de renderização
- `console.log` espalhados em código de produção
- Ausência total de testes automatizados
- Arquitetura fraca, vagamente inspirada em MVC

Nenhum desses pontos, isoladamente, justificaria uma reescrita completa.
No entanto, em conjunto, indicavam alta probabilidade de falhas no pós-lançamento.

---

## Restrições

- O prazo não podia ser alterado
- Reescrever o sistema não era uma opção
- O time já estava emocionalmente envolvido com o código existente
- As mudanças precisavam reduzir risco, não criar novos

O objetivo não era “embelezar o código”.
Era reduzir a probabilidade real de colapso do sistema após o lançamento.

---

## Decisões-Chave

### 1. Introdução do ESLint como Ferramenta de Diagnóstico

Em vez de discutir qualidade de código de forma subjetiva, o ESLint foi utilizado para tornar os problemas estruturais visíveis.

A primeira execução revelou uma grande quantidade de violações, deslocando a discussão do campo da opinião para fatos observáveis.

Cada regra foi analisada com o time:
- por que ela existe
- qual risco mitiga
- se fazia sentido naquele contexto específico

Regras que geravam atrito sem benefício claro não foram adotadas.

---

### 2. Padronização Antes da Evolução Funcional

Antes do desenvolvimento de novas funcionalidades, o time alinhou:
- estrutura de componentes
- uso de hooks
- convenções de nomenclatura
- organização de arquivos

Isso reduziu a carga cognitiva e tornou o sistema mais previsível de evoluir.

---

### 3. Disciplina Básica de Git

Foram estabelecidas práticas simples, porém essenciais:
- estratégia clara de branches
- commits com intenção técnica
- pull requests focados em entendimento, não apenas em entrega

Mais do que processo, isso ajudou a criar um modelo mental compartilhado do sistema.

---

### 4. Evitar Abstrações Prematuras

Dadas as restrições de tempo, abstrações só foram introduzidas quando:
- eliminavam duplicação real
- reduziam risco técnico

Refatorações arquiteturais amplas foram deliberadamente evitadas.

---

## Resultado

- O sistema foi entregue dentro do prazo
- Não houve incidentes relevantes após o lançamento
- A base de código permaneceu estável com a adição de novas funcionalidades
- O time manteve e internalizou as práticas adotadas

Desde então, outros sistemas foram desenvolvidos seguindo princípios semelhantes, todos em produção sem degradação estrutural.

---

## Impacto no Negócio

Além da estabilização técnica, a intervenção teve impacto direto no negócio.

Com base em estimativas internas, a prevenção de falhas no pós-lançamento evitou um prejuízo potencial próximo de R$ 500.000, considerando:
- indisponibilidade do sistema
- retrabalho emergencial
- penalidades contratuais
- perda de produtividade do time

Além disso, a estabilização permitiu manter o time completo durante uma fase crítica do projeto, evitando rotatividade e perda de conhecimento.

---

## Por Que Este Caso Importa

Grande parte dos problemas em engenharia de software não vem da falta de conhecimento técnico, mas de:
- decisões técnicas mal temporizadas
- desconsideração da dinâmica de equipe
- aplicação dogmática de “boas práticas”

Este caso demonstra como intervenções pequenas e bem delimitadas podem reduzir riscos de longo prazo sem comprometer a entrega.

---

## Escopo e Limitações

Este repositório não contém código proprietário.
O foco está no raciocínio, nas decisões e nos trade-offs — não em detalhes de implementação.

A intenção é compartilhar uma forma de pensar sobre estabilização de sistemas, não prescrever soluções universais.

---

## Sobre

Este caso reflete minha abordagem em engenharia de software:
criar sistemas que crescem em complexidade sem se tornarem legados ingovernáveis.
