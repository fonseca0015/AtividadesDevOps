# Síntese Teórica e Atividade — Aula 02: Fundamentos de CI/CD, Versionamento, Git e Deploys

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** Faculdade de Tecnologia de Sorocaba (FATEC)  
**Docente:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Data Limite:** 22 de Agosto de 2026 às 23:59  

---

## 1. Transformação Cultural: O Paradigma Pré e Pós-DevOps

### O Cenário Tradicional (Silos e Processos Fragmentados)
Historicamente, as áreas de Desenvolvimento (Dev) e Operações (Ops) atuavam de forma desconectada:
- **Barreiras Departamentais:** Desenvolvedores priorizavam novas funcionalidades rapidamente, enquanto Operações buscava estabilidade e temia alterações.
- **Intervenções Manuais:** Procedimentos manuais para compilação, testes e deploys geravam morosidade, gargalos e alta incidência de falhas operacionais.
- **Divergência de Ambientes:** Diferenças entre o ambiente local do desenvolvedor e os servidores finais geravam o tradicional problema do *"na minha máquina funciona"*.

### A Abordagem DevOps (Colaboração e Automação Contínua)
- **Unificação de Responsabilidades:** Integração cultural de pessoas, automação e ferramentas para fornecer valor com segurança.
- **Pipelines Confiáveis de CI/CD:** Rotinas automáticas que validam o código desde o commit até a publicação final.
- **Deploys Previsíveis:** Entregas frequentes em lotes menores, reduzindo a complexidade de cada liberação e viabilizando reversões imediatas em caso de anomalias.

---

## 2. O Ciclo de Vida Contínuo DevOps

O ecossistema DevOps é estruturado como um fluxo contínuo e infinito de atividades:

```
[PLAN] -> [CODE] -> [BUILD] -> [TEST] -> [RELEASE] -> [DEPLOY] -> [OPERATE] -> [MONITOR]
   ^                                                                                |
   +--------------------------------------------------------------------------------+
```

1. **PLAN (Planejamento):** Definição de escopo, backlog e refinamento de requisitos via práticas ágeis (Jira, GitHub Projects, Trello).
2. **CODE (Codificação):** Escrita e estruturação de código com controle de versão, boas práticas e revisões por pares.
3. **BUILD (Compilação/Construção):** Resolução de dependências e geração de pacotes executáveis imutáveis (JAR, imagens Docker, bundles web).
4. **TEST (Testes Automatizados):** Execução de suítes de validação rápida para assegurar que funcionalidades existentes permaneçam íntegras.
5. **RELEASE (Governança e Liberação):** Verificação de critérios de qualidade (*Quality Gates*) e marcação da versão semântica.
6. **DEPLOY (Implantação):** Envio dos artefatos validados aos ambientes de homologação ou produção de forma automatizada.
7. **OPERATE (Operação e Manutenção):** Sustentação de infraestrutura resiliente, provisionamento declarativo (IaC) e suporte à alta disponibilidade.
8. **MONITOR (Monitoramento e Observabilidade):** Coleta sistemática de logs, métricas e tracing (Grafana, Graylog, Prometheus) para retroalimentar o próximo ciclo.

---

## 3. Diferenciação Essencial: CI, Continuous Delivery e Continuous Deployment

| Modalidade | Definição | Gatilho para Produção |
| :--- | :--- | :--- |
| **Integração Contínua (CI)** | Prática de integrar o trabalho dos desenvolvedores várias vezes ao dia, executando builds e testes automáticos a cada commit. | Nenhum (foco em validação interna) |
| **Entrega Contínua (CD - Continuous Delivery)** | O artefato é compilado, testado e empacotado automaticamente, permanecendo em estado permanente de liberação pronta. | **Manual** (depende de validação humana de negócio) |
| **Deploy Contínuo (CD - Continuous Deployment)** | Extensão total da entrega contínua na qual todo código aprovado na pipeline é publicado diretamente em produção sem intervenção manual. | **Totalmente Automatizado** |

---

## 4. Versionamento e Semantic Versioning (SemVer)

### Papel do Controle de Versão
- Manter o histórico de todas as alterações feitas no projeto.
- Viabilizar trabalho colaborativo simultâneo sem sobrescrita involuntária de código.
- Garantir capacidade de auditoria e recuperação rápida de pontos estáveis (*rollback*).

### Especificação SemVer (`MAJOR.MINOR.PATCH`)
- **MAJOR (Quebra de Compatibilidade):** Alterações na API pública que exigem mudanças pelos clientes consumidores (ex.: `1.4.0` $\rightarrow$ `2.0.0`).
- **MINOR (Nova Funcionalidade):** Adição de novos recursos de maneira retrocompatível (ex.: `1.4.0` $\rightarrow$ `1.5.0`).
- **PATCH (Correções):** Ajustes de bugs e pequenas correções internas que não introduzem novas funcionalidades (ex.: `1.4.0` $\rightarrow$ `1.4.1`).

---

## 5. Fundamentos de Git, Tags e Plataformas de Hospedagem

### O que é o Git?
Criado por Linus Torvalds, o Git é um sistema de controle de versão distribuído no qual cada clone local armazena o histórico completo do repositório, permitindo commits rápidos, trabalho desconectado e operações eficientes de ramificação (*branches*).

### Marcadores de Versão (Tags no Git)
Tags são referências fixas a commits específicos para sinalizar versões estáveis:
- **Leve (Lightweight):** Ponteiro simples associado a um determinado commit.
- **Anotada (Annotated):** Objeto com informações completas (autor, data, mensagem explicativa e assinatura criptográfica opcional).

### Plataformas de Hospedagem e Deploy Contínuo (Vercel)
A Vercel destaca-se pelo deploy automatizado de aplicações front-end e estáticas a partir de integrações nativas com o GitHub: cada push ou merge na branch `main` desencadeia build e publicação imediata na borda (*edge*).

---

## 6. Roteiro Prático Executado (Tarefa 02)

1. Instalação e configuração inicial do VS Code e da ferramenta de linha de comando Git.
2. Parametrização da identidade do autor via `git config --global user.name` e `git config --global user.email`.
3. Desenvolvimento de projeto web simples composto por `index.html`, `style.css` e `script.js`.
4. Inicialização do repositório local (`git init`) e conexão com o repositório remoto no GitHub.
5. Realização de commits semânticos e publicação de tags de versão (`v1.0.0`, `v1.1.0`).
6. Validação do repositório e entrega acadêmica.

---

## 7. Repositório e Artefatos da Atividade

- **Repositório da Atividade:** [https://github.com/fonseca0015/Tarefa03DevOps](https://github.com/fonseca0015/Tarefa03DevOps)
- **Documentação Técnica:** Inclusa no repositório do projeto.

---

## 8. Integrantes da Equipe

- Gabriel Fonseca
- Rafaela Mansano
- Karina de Moraes

---

## 9. Referências Bibliográficas

- ARUNDEL, J.; DOMINGUS, J. *DevOps nativo de nuvem com Kubernetes*. São Paulo: Novatec, 2019.
- HUMBLE, J.; PRIKLANDNICKI, R. *Entrega Contínua: Como Entregar Software de Forma Rápida e Confiável*. São Paulo: Bookman, 2013.
- KIM, G. et al. *Manual de DevOps*. São Paulo: Alta Books, 2018.
- MORAES, G. *Caixa de Ferramentas DevOps*. São Paulo: Casa do Código, 2015.
- MUNIZ, A. et al. *Jornada DevOps*. São Paulo: Brasport, 2019.
- SILVERMAN, R. E. *Git: guia prático*. São Paulo: Novatec, 2019.
