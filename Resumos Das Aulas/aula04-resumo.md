# Síntese e Análise Comparativa — Aula 04: Plataformas CI/CD (Azure DevOps vs. GitHub Actions)

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** Faculdade de Tecnologia de Sorocaba (FATEC)  
**Docente:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Data Limite:** 5 de setembro de 2026 às 23:59  
**Referência Principal:** MANOLOV, Vladislav; GOTSEVA, Daniela; HINOV, Nikolay. *Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub*. Future Internet, v. 17, n. 4, 2025, p. 153. DOI: `10.3390/fi17040153`.

---

## 1. Contextualização e Propósito da Análise

O encontro da Aula 04 abordou em profundidade a automação do fluxo de desenvolvimento através de esteiras de Integração Contínua (CI) e Entrega/Implantação Contínua (CD). A discussão foi fundamentada no artigo de Manolov, Gotseva e Hinov (2025), o qual avalia empiricamente as capacidades técnicas, modelos arquiteturais e custos operacionais de dois dos maiores ecossistemas do mercado: **Azure DevOps** e **GitHub Actions**.

---

## 2. O Ciclo DevOps e o Elo de Ligação do CI/CD

As esteiras de automação atuam como a espinha dorsal conectando as oito etapas contínuas do ciclo de desenvolvimento de software:

- **PLAN (Planejamento):** Definição de prioridades, épicos e itens de backlog.
- **CODE (Desenvolvimento):** Construção colaborativa com controle de versão e revisões de pull request.
- **BUILD (Construção):** Resolução de pacotes e compilação em artefatos padronizados.
- **TEST (Testes):** Execução de baterias automatizadas de validação e testes de regressão.
- **RELEASE (Liberação):** Verificação de critérios de aceitação (*Quality Gates*) e versionamento.
- **DEPLOY (Implantação):** Envio dos artefatos aos nós de homologação ou produção.
- **OPERATE (Operação):** Manutenção da infraestrutura com automação e orquestração.
- **MONITOR (Observabilidade):** Coleta de telemetria, logs de falha e monitoramento de saúde do sistema.

A introdução de pipelines automatizadas encurta significativamente o tempo de resposta (*lead time*), diminui intervenções manuais propensas a erro e garante que alterações sejam validadas continuamente antes de qualquer entrega.

---

## 3. Panorama de Ferramentas Identificadas no Artigo e na Disciplina

O levantamento realizado no estudo abrange um ecossistema diversificado de soluções:

### A. Plataformas Principais de CI/CD e Gestão do Ciclo de Vida (ALM)
- **Azure DevOps (Azure Pipelines):** Solução corporativa modular abrangendo todo o ciclo de vida do software (*Application Lifecycle Management*).
- **GitHub (GitHub Actions):** Ferramenta nativa focada na experiência do desenvolvedor, disparada por eventos do repositório Git.
- **GitLab CI/CD:** Plataforma DevSecOps unificada com foco em pipelines declarativas em arquivo único.
- **Bitbucket Pipelines:** Solução integrada ao ecossistema Atlassian.
- **Jenkins:** Servidor de automação *open-source* com amplo suporte a plugins e pipelines programáveis (Groovy).
- **Outras plataformas mencionadas:** CircleCI, TeamCity, Travis CI, Bamboo, Buddy e Concourse.

### B. Gestão de Backlog e Colaboração (PLAN / CODE)
- **Azure Boards & Azure Repos:** Gerenciamento ágil corporativo (Scrum/Kanban) e hospedagem de repositórios Git.
- **GitHub Projects & GitHub Repositories:** Quadros visuais integrados nativamente a issues e pull requests.
- **Jira & Trello:** Ferramentas consagradas para acompanhamento de tarefas e sprints.

### C. Qualidade de Código, Governança e Artefatos (BUILD / TEST)
- **SonarQube:** Plataforma SAST para detecção de dívida técnica, vulnerabilidades e *code smells*.
- **GitHub Advanced Security:** Suíte nativa contendo **CodeQL** (análise semântica de vulnerabilidades), **Dependabot** (monitoramento de dependências vulneráveis) e **Secret Scanning** (bloqueio de credenciais expostas).
- **Azure Artifacts & GitHub Packages:** Repositórios centrais de pacotes (npm, NuGet, Maven, Docker).
- **Azure Test Plans:** Gestão formal de testes exploratórios e manuais integrados ao pipeline.

### D. Infraestrutura, Orquestração e Observabilidade (DEPLOY / OPERATE / MONITOR)
- **Docker & Kubernetes:** Padrão de fato para conteinerização e orquestração distribuída.
- **Helm:** Gerenciador de pacotes para arquiteturas Kubernetes.
- **Argo CD:** Mecanismo líder para implantação declarativa baseada em GitOps.
- **Ansible & Terraform:** Automação de configurações e Infraestrutura como Código (IaC).
- **Grafana & Graylog:** Visualização analítica de métricas, telemetria e gestão centralizada de logs.

---

## 4. Comparativo Analítico: Azure DevOps vs. GitHub Actions

O quadro a seguir sintetiza os achados empíricos extraídos do estudo de Manolov et al. (2025):

| Pilar de Avaliação | Azure DevOps (Azure Pipelines) | GitHub (GitHub Actions) |
| :--- | :--- | :--- |
| **Arquitetura Base** | Estrutura corporativa clássica (ALM) com separação formal entre pipelines de *Build* e esteiras de *Release*. | Arquitetura unificada e moderna baseada no fluxo de eventos Git (*event-driven*). |
| **Sintaxe de Configuração** | Arquivos YAML hierárquicos em múltiplos estágios (*stages*, *jobs*, *steps*) ou interface visual legada (*Classic Editor*). | Arquivos YAML declarativos armazenados em `.github/workflows/`, altamente concisos e intuitivos. |
| **Reaproveitamento de Fluxos** | Suporte a *YAML Templates* corporativos e Grupos de Variáveis centralizados na organização. | *Reusable Workflows* modulares e ecossistema aberto via GitHub Marketplace. |
| **Controle de Acesso e Governança** | Gestão profunda de permissões por perfis (RBAC), auditoria avançada e aprovações manuais com políticas de compliance rígidas. | Proteção de branches, regras de ambientes (*Environments* com revisores obrigatórios) e gestão de *Secrets* por escopo. |
| **DevSecOps Integrado** | Suporte a integrações corporativas com Azure Key Vault, Service Connections com credenciais federadas e SonarQube. | Recursos de segurança embutidos (CodeQL, Dependabot e Secret Scanning) diretamente na interface do desenvolvedor. |
| **Gestão de Testes** | Ferramenta dedicada (*Azure Test Plans*) com rastreamento detalhado de casos de teste, defeitos e relatórios analíticos. | Validação em matrizes de execução paralela (*job matrix*) com relatórios exportáveis via Actions comunitárias. |
| **Experiência do Desenvolvedor** | Maior curva de aprendizado devido à complexidade de módulos e configurações organizacionais. | Elevadíssima fluidez (*Developer Experience*), mantendo código, documentação e esteira na mesma visualização. |
| **Estrutura de Faturamento** | Licenciamento por usuário (Visual Studio subscriptions), capacidade de agentes paralelos e minutos de pipeline. | Cobrança orientada a consumo de minutos de execução de *runners* e armazenamento de artefatos (gratuito para projetos públicos). |

---

## 5. Vantagens, Limitações e Cenários Recomendados

### Azure DevOps
- **Destaques:** Atende plenamente corporações com exigências estritas de conformidade regulatória, empresas fortemente ancoradas no ecossistema Microsoft e projetos que demandam gestão avançada de planos de teste e auditoria integrada de ALM.
- **Pontos de Atenção:** Curva de adoção mais lenta, interface mais segmentada e comunidade menos dinâmica em relação a soluções puramente orientadas a código aberto.

### GitHub Actions
- **Destaques:** Adoção imediata pela proximidade entre o repositório de código e as esteiras de automação, milhares de extensões prontas no Marketplace e excelente alinhamento com padrões modernos de desenvolvimento em nuvem (*Cloud Native*).
- **Pontos de Atenção:** Ambientes com dependências complexas entre dezenas de pipelines legadas podem exigir maior esforço de organização e automações adicionais de orquestração.

---

## 6. Proposta da Atividade Acadêmica (Tarefa 04)

- Realizar leitura aprofundada do artigo científico de Manolov et al. (2025).
- Mapear a totalidade de tecnologias e plataformas citadas pelos autores no texto.
- Elaborar documento comparativo contendo reflexão crítica sobre a aplicabilidade de cada ecossistema.
- Versionar e publicar a análise técnica em formato Markdown no repositório GitHub do estudante.

---

## 7. Referências Bibliográficas

- ARUNDEL, J.; DOMINGUS, J. *DevOps nativo de nuvem com Kubernetes*. São Paulo: Novatec, 2019.
- HUMBLE, J.; PRIKLANDNICKI, R. *Entrega Contínua*. São Paulo: Bookman, 2013.
- KIM, G. et al. *Manual de DevOps*. São Paulo: Alta Books, 2018.
- MANOLOV, V.; GOTSEVA, D.; HINOV, N. *Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub*. Future Internet, v. 17, n. 4, 2025, p. 153. DOI: `10.3390/fi17040153`.
- MORAES, G. *Caixa de Ferramentas DevOps*. São Paulo: Casa do Código, 2015.
- MUNIZ, A. et al. *Jornada DevOps*. São Paulo: Brasport, 2019.
- PIRES, A.; MILITÃO, J. *Integração Contínua com Jenkins*. São Paulo: Casa do Código, 2019.
- SATO, D. *DevOps na prática*. São Paulo: Casa do Código, 2014.
- SILVERMAN, R. E. *Git: guia prático*. São Paulo: Novatec, 2019.
- VITALINO, J. F. N.; CASTRO, M. A. N. *Descomplicando o Docker*. 2. ed. São Paulo: Brasport, 2018.
