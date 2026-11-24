# Síntese e Estudo Prático — Aula 06: Engenharia de Pipelines e Inspeção de Repositórios Reais

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** Faculdade de Tecnologia de Sorocaba (FATEC)  
**Docente:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Base de Apoio:** Slides da Aula 06 — Revisão de Ferramentas e Pipelines (Takatu, D. S.)  

---

## 1. Fundamentação Teórica da Aula 06

A Aula 06 revisou a cultura DevOps como uma filosofia colaborativa contínua que conecta as frentes de **Desenvolvimento (DEV)** e **Operações (OPS)**, superando divisões organizacionais para garantir fluxos de lançamento velozes, previsíveis e de alta qualidade.

### O Ciclo Contínuo de 8 Fases
O fluxo de desenvolvimento e operação organiza-se em etapas interligadas:

1. **PLAN:** Gestão orientada a valor, priorização de épicos e itens de trabalho (Jira, Trello, Azure Boards).
2. **CODE:** Produção e refatoração de código com revisão sistemática por pares via Pull Requests (Git, GitHub, GitLab).
3. **BUILD:** Compilação dos fontes e resolução de pacotes gerando artefatos imutáveis (Gradle, Maven, Docker, npm).
4. **TEST:** Execução automatizada de testes para assegurar integridade estrutural e regressão zero.
5. **RELEASE:** Homologação formal, validação de *Quality Gates* e atribuição de SemVer (`vMajor.Minor.Patch`).
6. **DEPLOY:** Distribuição automatizada em ambientes de produção com estratégias de zero downtime (ex.: rolling updates em clusters Kubernetes).
7. **OPERATE:** Manutenção da infraestrutura através de práticas declarativas de Infraestrutura como Código (Ansible, Terraform).
8. **MONITOR:** Observabilidade integrada por meio da tríade de **Métricas**, **Logs** e **Tracing** (Grafana, Graylog, Prometheus).

---

### Diretrizes Centrais para Construção de Pipelines
- **Imutabilidade do Build:** O mesmo binário/imagem empacotado no build transita por testes, homologação e produção sem recompilação.
- **Padronização do Deploy:** Os scripts e rotinas de implantação mantêm a mesma estrutura lógica em todos os níveis.
- **Interrupção Imediata (*Fail-Fast*):** Qualquer irregularidade detectada em uma etapa impede o avanço das fases posteriores.

---

## 2. Análise Prática: Pipelines de CI em Grandes Repositórios Open-Source

Em atendimento à atividade da Aula 06, foram analisadas as esteiras de três renomados projetos abertos no GitHub que utilizam **GitHub Actions** acionadas por eventos de `push` na branch principal:

### 1. Vue.js Core (`vuejs/core`)
- **Ecossistema:** JavaScript / TypeScript.
- **Proposta Técnica:** Framework progressivo para construção de interfaces reativas de usuário.
- **Estrutura da Pipeline:**
  - Checagem rigorosa de tipos estáticos através do compilador TypeScript.
  - Execução de baterias de testes unitários e de integração com a ferramenta Vitest.
  - Auditoria estática de conformidade sintática e estilo via ESLint.
  - Monitoramento contínuo do tamanho final do pacote compilado (*bundle size*).
- **Gatilhos de Execução:** Disparos automáticos em eventos de `push` na branch `main`, em novos `pull_request` e rotinas agendadas (cron diário).
- **Maturidade Técnica:** Pipeline altamente veloz e otimizada com cache de dependências, garantindo estabilidade para milhões de aplicações que consomem o framework.

---

### 2. Spring Boot (`spring-projects/spring-boot`)
- **Ecossistema:** Java / Gradle / Maven.
- **Proposta Técnica:** Framework de referência corporativa para construção de microsserviços e APIs robustas.
- **Estrutura da Pipeline:**
  - Compilação do código com verificação de compatibilidade em matriz de versões do Java (JDK 17 e JDK 21 LTS).
  - Execução de suítes de testes de integração profunda com múltiplos bancos de dados e serviços externos.
  - Inspeção estática de padrões e formatação via Checkstyle.
  - Publicação automática de artefatos de build intermediários (`SNAPSHOT`) no registro central do Nexus.
- **Gatilhos de Execução:** Ativação em eventos de `push` na `main` e branches estáveis (`3.3.x`), validação de PRs e disparos manuais (`workflow_dispatch`).
- **Maturidade Técnica:** Governança enterprise com bloqueio absoluto de avanço caso qualquer teste da matriz falhe.

---

### 3. NestJS (`nestjs/nest`)
- **Ecossistema:** Node.js / TypeScript.
- **Proposta Técnica:** Framework opinado para arquiteturas escaláveis de backend utilizando injeção de dependências.
- **Estrutura da Pipeline:**
  - Compilação modular de múltiplos pacotes em estrutura de monorepo.
  - Execução de testes de unidade e suítes completas de ponta a ponta (E2E) com o framework Jest.
  - Formatação e conferência estética de código através do Prettier.
  - Integração com o serviço Codecov para auditoria de métricas de cobertura de código.
- **Gatilhos de Execução:** Execução automática a cada `push` na branch `master` e em todos os pull requests submetidos.
- **Maturidade Técnica:** Foco em fornecer feedback rápido aos contribuidores externos da comunidade antes da integração de novas alterações.

---

## 3. Matriz Comparativa dos Projetos Mapeados

| Repositório | Stack Principal | Fases Relevantes da Esteira | Gatilhos de Ativação |
| :--- | :--- | :--- | :--- |
| **`vuejs/core`** | TypeScript / Vue | TypeScript Check, Vitest, ESLint, Bundle Size | `push` (main), `pull_request`, cron |
| **`spring-projects/spring-boot`** | Java / Gradle | Compilação em Matriz JDK (17/21), Checkstyle, Nexus Publish | `push` (main/branches), `pull_request` |
| **`nestjs/nest`** | Node.js / TypeScript | Monorepo Build, Jest (Unit/E2E), Prettier, Codecov | `push` (master), `pull_request` |

---

## 4. Conclusão

A investigação prática comprova que sistemas modernos de grande porte dependem criticamente de pipelines automatizadas no branch principal para assegurar qualidade e governança. O encadeamento de linting, testes em matriz e bloqueio imediato contra falhas viabiliza lançamentos ágeis e mantém a confiança da comunidade técnica no ecossistema.
