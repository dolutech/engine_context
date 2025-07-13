# Regra de Tasks e Planejamento – Padrão Dolutech para Agentes de IA

## Objetivo

Esta regra garante que, para todo prompt ou solicitação recebida, o agente de IA trabalhe em dois modos estruturados: **Modo Planejar** e **Modo Execução**. O agente deve sempre gerar um detalhamento de tasks, explicações do método e um plano de execução para aprovação do usuário antes de implementar qualquer solução.

---

## Modos de Operação

### 1. Modo Planejar

**Sempre que receber um novo prompt ou solicitação de projeto:**

- O agente deve **analisar a solicitação** e decompor a solução em uma lista de tasks lógicas e acionáveis.
- Para cada task, o agente deve explicar:
  - **O que** será feito
  - **Como** será realizado (ferramentas, métodos, etapas)
  - **Qual o resultado esperado** ou entrega prevista
- O agente deve organizar todas as tasks em um **plano de execução passo a passo** (lista ordenada ou tabela), incluindo dependências se aplicável.
- O agente deve apresentar o plano de execução completo ao usuário, solicitando revisão, validação ou aprovação antes de prosseguir.

**Exemplo de estrutura:**

```
## Plano de Execução para [Prompt/Nome do Projeto]

1. **Nome da Task**
   - Descrição: Explique resumidamente o que será feito.
   - Abordagem: Detalhe ferramentas, frameworks ou técnicas que serão utilizadas.
   - Dependências: [se houver]
   - Resultado Esperado: Descreva a entrega ou o resultado previsto.

2. **Próxima Task**
   ...
```

- Ao final, inclua uma solicitação ao usuário:
  - “**Por favor, revise o plano de execução e indique quais tasks aprova para execução ou sugira alterações se necessário.**”

---

### 2. Modo Execução

- Somente após aprovação explícita do usuário, o agente avança para o **Modo Execução**.
- O agente executa as tasks aprovadas passo a passo, documentando o progresso, resultados, decisões e eventuais obstáculos.
- Caso surja complexidade imprevista ou novas subtasks, o agente deve pausar, retornar ao Modo Planejar e atualizar o plano para nova aprovação.

---

## Documentação das Tasks

- Para cada prompt ou projeto, crie ou atualize um arquivo na pasta `memory-bank` chamado `tasks_[nome-do-prompt].md`.
- Documente neste arquivo:
  - O pedido original do usuário
  - O plano de execução proposto
  - Aprovação/comentários do usuário
  - Progresso das tasks, notas de conclusão e entregáveis finais
  - Links, referências ou artefatos relevantes

---

## Fluxo de Aprovação do Usuário

- O agente **nunca avança para execução** ou entrega de código, scripts, documentação ou qualquer ação sem antes apresentar o plano e obter aprovação explícita do usuário.
- Isso garante rastreabilidade, alinhamento de expectativas e total transparência no fluxo de trabalho.

---

## Boas Práticas

- Sempre forneça explicações claras, concisas e acionáveis para cada task.
- Relacione as tasks ao contexto do negócio e aos objetivos do projeto quando possível.
- Incentive o feedback e a colaboração do usuário durante o planejamento.
- Atualize o plano de execução e a documentação sempre que houver mudanças de escopo, requisitos ou preferências do usuário.

---

## Exemplo de Fluxo

1. **Prompt do Usuário:** “Criar uma API de cadastro de usuário segura em Node.js”
2. **Modo Planejar do Agente:** Decompõe a solução em tasks (ex: definir modelo de dados, configurar autenticação JWT, implementar validação de entradas, documentar a API, escrever testes).
3. **Agente Apresenta o Plano:** Detalha cada task com abordagem, dependências, resultado esperado; solicita aprovação do usuário.
4. **Usuário Aprova:** O usuário pode aprovar, rejeitar ou solicitar alterações nas tasks.
5. **Modo Execução do Agente:** Executa as tasks aprovadas, documentando o progresso no respectivo arquivo `tasks_[nome-do-prompt].md` dentro do memory bank.

---

## Resumo

**Com esta regra ativa, o agente sempre opera de forma transparente, colaborativa e orientada por aprovação, separando Planejamento da Execução. Todas as soluções são documentadas e as tasks rastreadas, garantindo clareza, alinhamento e controle total para o usuário.**

---

**FIM DO ARQUIVO**

