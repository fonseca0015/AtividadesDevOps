# Síntese Teórica e Prática — Aula 05: Construção de Pipelines de Integração Contínua

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** Faculdade de Tecnologia de Sorocaba (FATEC)  
**Docente:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Base Pedagógica:** Slides da Aula 05 — Pipeline de Integração Contínua (Takatu, D. S.)  

---

## 1. Visão Geral e Objetivos do Encontro

A Aula 05 abordou a espinha dorsal da automação em ambientes DevOps: a concepção e a estruturação de **Pipelines de Integração Contínua (CI)**. O propósito fundamental consiste em estabelecer uma esteira automatizada de verificações rigorosas que conduz qualquer alteração no código-fonte até a sua compilação e teste com rapidez, previsibilidade e mínima fricção operacional. Na seção prática, utilizou-se o motor do **GitHub Actions**.

---

## 2. Pilares Arquiteturais de uma Pipeline Eficiente

Uma pipeline de CI/CD bem projetada sustenta-se sobre três regras indispensáveis:

1. **Construir apenas uma vez (*Build Once*):** O artefato gerado e empacotado na fase de compilação deve ser rigorosamente o mesmo promovido ao longo de todas as etapas subsequentes (Desenvolvimento $\rightarrow$ Homologação $\rightarrow$ Produção), garantindo integridade e paridade absoluta.
2. **Procedimento padronizado de implantação (*Consistent Deployment*):** O processo de deploy deve seguir as mesmas diretrizes automáticas, variando apenas as credenciais e configurações de ambiente de destino.
3. **Diretriz de bloqueio imediato (*Fail-Fast*):** Qualquer inconsistência detectada (falha em compilação, quebra de teste unitário ou violação de regra de segurança) deve interromper imediatamente a esteira, notificando os desenvolvedores para resolução prioritária.

---

## 3. Fases Sequenciais de uma Esteira de Integração

A execução de uma esteira divide-se em fases complementares e interdependentes:

```
[1. BUILD] ---> [2. TESTES] ---> [3. QUALIDADE & SEGURANÇA] ---> [4. ARTEFATOS] ---> [5. DEPLOY & RELEASE]
```

### A. Estágio de Compilação (Build Pipeline)
- Recupera o código-fonte, instala dependências e executa o processo de compilação da aplicação.
- Produz os artefatos executáveis ou formatos de distribuição (arquivos `.jar`, bundles de frontend, imagens Docker).

### B. Estágio de Testes Automatizados (Test Pipeline)
- Dispara suítes de validação automática logo após o build para certificar que novas implementações não introduziram regressões no comportamento esperado do sistema.

### C. Estágio de Qualidade e Segurança (Quality & Security Pipeline)
- **Inspeção de Qualidade:** Avalia padronização sintática, estilo de código (linting) e níveis mínimos de cobertura de código.
- **Análise de Segurança (DevSecOps):** Varre a base de código em busca de dependências vulneráveis conhecidas (CVEs), credenciais sensíveis expostas e configurações inadequadas.

### D. Estágio de Empacotamento de Artefatos (Package Pipeline)
- Versiona e publica os pacotes construídos em registros seguros e centralizados (registries de contêineres, Nexus, Artifactory, GitHub Packages).

### E. Estágio de Liberação e Implantação (Deploy & Release)
- Conduz os artefatos validados ao ambiente de destino e monitora o status de disponibilidade inicial pós-deploy (*smoke tests*).

---

## 4. Engenharia de Automação com GitHub Actions

O **GitHub Actions** foi destacado como o motor integrado que viabiliza a execução declarativa dessas esteiras:

- **Workflows Declarativos em YAML:** Rotinas estruturadas localizadas no diretório `.github/workflows/` que descrevem jobs, variáveis de ambiente e passos de execução.
- **Gatilhos Orientados a Eventos (*Triggers*):** A inicialização da pipeline pode ser ativada por ações no repositório, como `push`, criação de `pull_request`, geração de `release` ou agendamentos cron.
- **GitHub Marketplace:** Ecossistema que disponibiliza milhares de ações prontas e homologadas criadas pela comunidade e por fornecedores oficiais (ex.: checkout de código, configuração de runtimes, build de imagens Docker e deploy em nuvem).

---

## 5. Proposta da Atividade Prática (Tarefa 05)

1. **Seleção de Componentes:** Escolher três *Actions* distintas e complementares no catálogo do GitHub Marketplace.
2. **Construção do Workflow:** Configurar um arquivo `.yml` funcional conectando as ações escolhidas em etapas coerentes do fluxo de integração contínua (ex.: montagem de ambiente, análise de código e validação).
3. **Execução e Documentação Técnica:** Realizar commits para acionar o fluxo, validar a execução bem-sucedida de cada job e descrever em documentação o propósito técnico de cada Action implementada.

---

## 6. Referências Bibliográficas

- ARUNDEL, J.; DOMINGUS, J. *DevOps nativo de nuvem com Kubernetes*. São Paulo: Novatec, 2019.
- HUMBLE, J.; PRIKLANDNICKI, R. *Entrega Contínua*. São Paulo: Bookman, 2013.
- KIM, G. et al. *Manual de DevOps*. São Paulo: Alta Books, 2018.
- MORAES, G. *Caixa de Ferramentas DevOps*. São Paulo: Casa do Código, 2015.
- MUNIZ, A. et al. *Jornada DevOps*. São Paulo: Brasport, 2019.
- PIRES, A.; MILITÃO, J. *Integração Contínua com Jenkins*. São Paulo: Casa do Código, 2019.
- SATO, D. *DevOps na prática*. São Paulo: Casa do Código, 2014.
- SILVERMAN, R. E. *Git: guia prático*. São Paulo: Novatec, 2019.
- VITALINO, J. F. N.; CASTRO, M. A. N. *Descomplicando o Docker*. 2. ed. São Paulo: Brasport, 2018.
