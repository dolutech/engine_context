# Memory Bank Dolutech – Regra Avançada para Agentes de IA em Projetos de Software

## Finalidade do Memory Bank

O objetivo do banco de memória (memory bank) é garantir que todas as informações técnicas, decisões, aprendizados, integrações e evoluções de um projeto de software sejam documentadas, organizadas e versionadas desde o início do desenvolvimento. Isso facilita auditorias, continuidade de equipes, onboarding, rastreabilidade, governança e análise de segurança, fornecendo uma base única de consulta e referência ao longo do ciclo de vida do projeto.

## Procedimento Inicial – Como o Agente Deve Atuar

1. **Ao iniciar qualquer novo projeto, crie uma pasta na raiz chamada** `memory-bank` **(sem variações de nome).**
2. Todos os arquivos criados dentro desta pasta devem ser em formato Markdown (`.md`) e seguir o padrão e os exemplos estabelecidos neste documento.
3. Cada arquivo tem um objetivo específico e sua atualização é obrigatória sempre que ocorrer um evento, mudança, decisão ou evolução relevante no projeto.
4. O agente deve garantir que os arquivos estejam sempre atualizados e alinhados, evitando informações desatualizadas ou duplicadas.
5. O memory bank deve ser tratado como parte integrante do versionamento do projeto (git, svn, etc), recebendo commits junto do código fonte.

---

## Estrutura de Arquivos do Memory Bank

### 1. `linguagens.md`

**Propósito:**

- Documentar detalhadamente todas as linguagens, frameworks, bibliotecas, SDKs, runtimes, ferramentas de build, e padrões tecnológicos adotados no projeto.
- Deve indicar a finalidade de cada tecnologia (exemplo: "React – frontend SPA", "Prisma – ORM Node.js para PostgreSQL").

**Conteúdo obrigatório:**

- Nome da linguagem/framework/ferramenta
- Versão utilizada (sempre)
- Finalidade no projeto
- Vantagens e possíveis limitações observadas

**Exemplo:**

```
- Node.js v20.3.0 – Backend principal (API REST)
- PostgreSQL v15 – Banco de dados relacional
- Prisma v5.0 – ORM para integração Node.js/PostgreSQL
- TailwindCSS v3.4 – Estilização do Frontend
- React v18 – Frontend SPA
- Express v4.18 – Framework backend
- Docker v26.0 – Orquestração de ambientes
```

---

### 2. `integracoes.md`

**Propósito:**

- Listar e descrever detalhadamente todas as integrações externas (APIs, gateways de pagamento, serviços de terceiros, provedores cloud, autenticação social, webhooks, etc).
- Descrever endpoints, métodos, autenticação, callbacks, escopos, permissões e dados sensíveis trafegados.

**Conteúdo obrigatório:**

- Nome da integração e fornecedor
- Descrição da finalidade
- Detalhes técnicos (endpoint, métodos, payloads, autenticação, callbacks)
- Pontos críticos de segurança/privacidade
- Status (ativa, deprecated, teste, homologação)

**Exemplo:**

```
- PagSeguro API (https://api.pagseguro.com) – Processamento de pagamentos. Autenticação OAuth2. Endpoints: /v1/payment, /v1/checkout. Callbacks de status em /webhook/pagseguro. Status: ativo.
- AWS S3 – Armazenamento de arquivos. Acesso via SDK AWS, uso de buckets segregados. Permissões mínimas aplicadas via IAM. Status: homologação.
- Google OAuth – Login social, autorização via OAuth2, integração frontend/backend, scopes: email, profile. Status: ativo.
```

---

### 3. `funcionalidades.md`

**Propósito:**

- Documentar cada funcionalidade do sistema, com contexto de negócio, regras implementadas, APIs envolvidas, datas de início/conclusão, responsável, status e relação com requisitos ou tarefas (ex: link para issue no Jira ou GitHub).

**Conteúdo obrigatório:**

- Nome da funcionalidade
- Descrição/resumo
- Data de início e conclusão
- Status (em desenvolvimento, concluída, revisada, aprovada, deprecated)
- Responsável principal
- Relacionamento com tarefa/requisito
- Componentes e módulos envolvidos

**Exemplo:**

```
- Cadastro de usuário: Permite novo usuário criar conta via email/senha. Início: 2025-07-13. Conclusão: 2025-07-14. Status: concluído. Responsável: Ana Costa. Issue: #12. Frontend (React), Backend (Express), Banco (PostgreSQL).
- Recuperação de senha: Processo de reset via token enviado por email. Início: 2025-07-15. Status: em desenvolvimento. Responsável: Rafael Lima. Issue: #19. Integração com SendGrid.
```

---

### 4. `correcoes.md`

**Propósito:**

- Registrar detalhadamente bugs encontrados, vulnerabilidades detectadas, falhas de segurança, melhorias de performance, e todo tipo de correção, informando impacto, data, commit, responsável e verificação pós-correção.

**Conteúdo obrigatório:**

- Descrição clara do problema
- Data da identificação
- Data da correção
- Referência ao commit/pull request
- Responsável pela correção
- Teste/validação aplicada
- Impacto no sistema (afeta produção? exige rollback? tem workaround?)

**Exemplo:**

```
- Bug: Erro 500 ao cadastrar usuário com email já registrado. Identificado: 2025-07-15. Corrigido: 2025-07-15. Commit: #c2a34b. Responsável: Pedro Soares. Validação: Teste automatizado. Impacto: bloqueava cadastro, não afetava produção.
- Vulnerabilidade: Falha CSRF no endpoint /api/user/update. Identificado: 2025-07-16. Corrigido: 2025-07-17. Commit: #e22ac0. Responsável: Lucas M. Testado manualmente.
```

---

### 5. `estado-projeto.md`

**Propósito:**

- Resumir o status geral do projeto: versão atual, milestones, status de módulos, principais riscos, próximos passos, pendências técnicas, ambiente de produção/homologação e saúde da infraestrutura.

**Conteúdo obrigatório:**

- Versão atual do projeto
- Último commit relevante e data
- Módulos concluídos/em andamento
- Principais pendências ou riscos
- Status de produção/homologação
- Observações gerais relevantes

**Exemplo:**

```
Versão: 1.2.1
Última atualização: 2025-07-17 (commit #da23b2)
Frontend: OK
Backend: OK
Integração PagSeguro: aguardando homologação
Pendências: ajuste de cache Redis em produção
Riscos: atraso no gateway de pagamento
```

---

### 6. `front.md`

**Propósito:**

- Documentar toda a evolução do frontend: decisões arquiteturais, rotas, componentes, padrões de estado, testes, estratégias de responsividade, comunicação com backend, integrações de SDKs, tratamento de erros, acessibilidade, padrões de UX, otimizações.

**Conteúdo obrigatório:**

- Decisões tomadas (com justificativa)
- Estrutura de pastas, principais componentes criados/alterados
- Tecnologias/ferramentas usadas (ex: Redux, Context API, Zustand)
- Integrações diretas (APIs, SDKs)
- Padrões de autenticação e autorização implementados
- Abordagem de responsividade, internacionalização, acessibilidade
- Estratégias de deploy e build

**Exemplo:**

```
- Adotado React Context para gerenciamento de autenticação. Justificativa: simplificação do fluxo global de usuário.
- Todos formulários usam validação Yup e tratamento de erros global.
- Layout adaptativo com Tailwind, breakpoints documentados em /src/styles/theme.js
- Consumo da API de autenticação via axios, uso de interceptors para refresh de token.
- Páginas protegidas com HOC AuthGuard.
```

---

### 7. `back.md`

**Propósito:**

- Detalhar toda a estrutura do backend: arquitetura, endpoints, fluxos de autenticação/autorização, modelos de dados, rotinas de background, integrações, workers, filas, cache, mecanismos de logs, middlewares e padrões de segurança.

**Conteúdo obrigatório:**

- Descrição e diagrama dos principais módulos do backend
- Endpoints implementados (com métodos, payload, regras de negócio)
- Estratégias de autenticação/autorização (JWT, OAuth2, RBAC, ACL)
- Integração com bancos de dados, cache, filas, jobs
- Políticas de logging e monitoramento
- Controles de segurança: validação, sanitização, permissões
- Testes automatizados (cobertura, ferramentas)

**Exemplo:**

```
- Endpoint POST /api/auth/login – autenticação via JWT, validação de credenciais pelo serviço AuthService, logs em Elastic.
- ORM Prisma para manipulação de PostgreSQL, migrations versionadas, seeds documentados.
- Job assíncrono para envio de email usa BullMQ e Redis.
- Middleware de rate limiting (express-rate-limit) em todos os endpoints sensíveis.
```

---

### 8. `arquitetura.md`

**Propósito:**

- Mapear a arquitetura geral do projeto, incluindo diagramas textuais ou visuais, detalhamento de módulos, fluxos principais, dependências entre sistemas, pontos de integração, gateways, middlewares, fluxos de autenticação, controle de erros, orquestração e monitoramento.

**Conteúdo obrigatório:**

- Diagrama ou descrição textual dos fluxos
- Componentes/módulos principais e comunicação entre eles
- Pontos de integração externos
- Fluxo de autenticação/autorização (frontend, backend, terceiros)
- Estrutura de monitoramento, logging, alarmes
- Padrões de resiliência (retry, fallback, circuit breaker, etc)

**Exemplo:**

```
[Frontend (React)] <-> [API Gateway (Express)] <-> [Serviços (Auth, Pagamentos, Usuário)] <-> [Banco (PostgreSQL)]
Auth se comunica com o serviço de email externo via worker
Integração com PagSeguro protegida por firewall de aplicação
Monitoramento: Prometheus + Grafana
```

---

### 9. `comunicacao.md`

**Propósito:**

- Documentar detalhadamente como o frontend se comunica com o backend e demais serviços, protocolos utilizados, endpoints expostos, contratos de API, exemplos de requests/responses, formatos de autenticação e padrões de mensagens.

**Conteúdo obrigatório:**

- Endpoints e rotas consumidas pelo frontend
- Métodos HTTP, payloads, headers obrigatórios
- Protocolos (REST, GraphQL, WebSocket, etc)
- Padrões de autenticação usados nas comunicações
- Exemplos reais de requisições e respostas (com payloads)

**Exemplo:**

```
Frontend chama POST /api/auth/login enviando JSON { email, senha }
Resposta: 200 OK, body: { token, usuario }
Autenticação: Bearer JWT em todas as rotas protegidas
Alguns módulos usam WebSocket para atualização em tempo real
```

---

### 10. `versao.md`

**Propósito:**

- Manter o histórico detalhado de versões do projeto, datas de release, mudanças, principais features, bugfixes, status e ambiente da entrega (produção/homologação/dev).

**Conteúdo obrigatório:**

- Número/identificação da versão
- Data de liberação
- Principais mudanças (feature/correção/breaking change)
- Status (produção, homologação, dev)

**Exemplo:**

```
v1.0.0 (2025-07-13) – Estrutura inicial do backend/frontend, autenticação básica, deploy homologação.
v1.1.0 (2025-07-15) – Cadastro de usuários, integração AWS S3, deploy produção.
v1.2.0 (2025-07-17) – Sistema de pagamentos, correção CSRF, ajuste layout frontend.
```

---

### 11. `seguranca.md`

**Propósito:**

- Documentar todos os requisitos, controles e práticas de segurança aplicadas no projeto, resultados de auditorias, recomendações de frameworks de segurança utilizados, planos de resposta a incidentes, status de conformidade e registros de vulnerabilidades encontradas.

**Conteúdo obrigatório:**

- Frameworks e padrões de segurança adotados (ex: OWASP Top 10, ASVS)
- Políticas de senhas, autenticação, criptografia
- Resultados de auditoria, pentests, scans automatizados
- Vulnerabilidades identificadas e tratadas
- Plano de resposta a incidentes
- Status de conformidade (PCI DSS, LGPD, GDPR, etc)

**Exemplo:**

```
Adotado OWASP ASVS Nível 2 para backend, Nível 1 para frontend
Senhas com mínimo de 12 caracteres, bcrypt 12 rounds
Pentest externo realizado em 2025-07-18, 2 vulnerabilidades críticas corrigidas
Projeto aderente à LGPD, dados sensíveis segregados
```

---

### 12. `testes.md`

**Propósito:**

- Documentar a estratégia de testes (unitários, integração, end-to-end, smoke, stress, fuzzing), cobertura, ferramentas, automação CI/CD, principais cenários e métricas de qualidade.

**Conteúdo obrigatório:**

- Estratégia e tipos de testes adotados
- Cobertura de testes (percentual por módulo)
- Ferramentas utilizadas (Jest, Cypress, Postman, etc)
- Status dos pipelines de CI/CD
- Principais bugs encontrados por testes
- Testes manuais x automáticos

**Exemplo:**

```
- Testes unitários (Jest) para todos serviços do backend, cobertura > 85%
- Testes e2e Cypress, 16 cenários críticos do frontend
- Pipeline CI executa lint, testes, build e scan de segurança a cada PR
- Teste de carga: 100 req/s durante 10 minutos sem falhas
```

---

### 13. `index-memory-bank.md`

**Propósito:**

- Servir como índice central do banco de memória, listando todos os arquivos obrigatórios, descritivo da função de cada um, exemplos de uso, instruções de atualização e periodicidade mínima de manutenção de cada documento.
- Deve ser atualizado toda vez que um novo arquivo relevante for adicionado ou removido do memory-bank.

**Conteúdo obrigatório:**

- Listagem de todos arquivos obrigatórios e opcionais do memory-bank
- Breve descrição da função de cada arquivo
- Instruções resumidas de alimentação/atualização
- Periodicidade mínima recomendada de atualização (por exemplo: "funcionalidades.md: atualizar ao criar nova feature; seguranca.md: após cada auditoria ou pentest")

**Exemplo:**

```
# Índice Memory Bank

- linguagens.md: Tecnologias, frameworks e ferramentas do projeto
- integracoes.md: Integrações externas, provedores, APIs
- funcionalidades.md: Funcionalidades desenvolvidas, status, responsáveis
- correcoes.md: Bugs, vulnerabilidades, melhorias aplicadas
- estado-projeto.md: Status geral, pendências, riscos
- front.md: Estrutura e evolução do frontend
- back.md: Estrutura e evolução do backend
- arquitetura.md: Arquitetura, diagramas, fluxos
- comunicacao.md: Comunicação entre módulos, APIs, padrões
- versao.md: Controle de versões e releases
- seguranca.md: Controles, auditorias, práticas e incidentes de segurança
- testes.md: Estratégia, cobertura e ferramentas de testes

**Instruções Gerais:**
- Atualize cada arquivo sempre que houver evolução ou evento relevante relacionado
- Não omita problemas, riscos ou limitações
- O índice deve ser revisado após cada novo arquivo criado ou excluído
- Todos os arquivos devem ter data da última atualização no topo
```

---

## Observações e Recomendações para o Agente

- O agente é responsável por garantir atualização contínua, rastreabilidade e precisão documental de todo o memory bank.
- A documentação deve ser objetiva, precisa, sempre com data e responsável identificado.
- Registre links para tarefas, issues, pull requests, diagrama, imagens e quaisquer artefatos relevantes no contexto de cada item.
- O memory bank é fundamental para governança, continuidade, transferências de times, compliance e auditorias futuras.
- Não deixe de atualizar documentos após correções, auditorias, entregas e decisões críticas.
- Promova a cultura de documentação colaborativa, incentivando todo o time a participar do memory bank.

---

**FIM DO ARQUIVO**

