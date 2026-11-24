# Síntese Teórica e Prática — Aula 07: Testes Automatizados no Pipeline de CI

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** Faculdade de Tecnologia de Sorocaba (FATEC)  
**Docente:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Base Pedagógica:** Slides da Aula 07 — Testes Automatizados (Takatu, D. S.)  

---

## 1. Fundamentos Teóricos da Aula 07

A Aula 07 explorou a aplicação estratégica de **Testes Automatizados** como pilar indispensável nas esteiras de Integração Contínua (CI). A premissa central é que a qualidade do software não deve ser uma verificação tardia antes do lançamento, mas sim um processo constante e automatizado que blinda o repositório contra regressões e inconsistências.

### Vantagens Competitivas dos Testes em Pipelines
- **Substituição de Validações Manuais:** Eliminação de checagens manuais repetitivas e naturalmente sujeitas a equívocos humanos.
- **Velocidade de Feedback:** Execução simultânea de dezenas ou centenas de cenários em poucos minutos.
- **Detecção Imediata (*Fail Fast*):** Notificação em tempo real sobre quebras de funcionalidade logo após o envio do código via `git push`.
- **Prevenção Contínua de Regressões:** Certeza de que alterações recentes não degradaram comportamentos previamente homologados.

---

## 2. Estrutura de Testes e Inspeção de Qualidade

Uma esteira equilibrada de validação divide-se em camadas funcionais:

- **Pipeline de Testes Funcionais:** Executada após a fase de compilação, testa o sistema em múltiplos níveis (isolado, integrado e sob demanda operacional).
- **Pipeline de Qualidade e Padronização (Linting):** Realiza inspeção estática no código (ex.: regras de **ESLint** para detectar variáveis sem uso como `no-unused-vars`, estruturas mal formatadas ou convenções ignoradas).
- **Mecanismo de Interrupção Crítica:** Caso um teste falhe ou uma regra estática seja violada, o pipeline interrompe imediatamente a execução, impedindo que artefatos defeituosos avancem para fases de empacotamento ou deploy.

---

## 3. Estudo de Caso Prático: Motor de Descontos Web

Para vivenciar a dinâmica real de um pipeline de validação, foi utilizado o projeto prático `projeto-pipeline-testes`, uma aplicação em React e JavaScript voltada ao cálculo comercial de descontos em compras:

### Regras de Negócio Implementadas
- Compras com valor total estritamente **inferior a R$ 100,00** recebem taxa de **10% de desconto**.
- Compras com valor total **igual ou superior a R$ 100,00** recebem taxa de **5% de desconto**.

### Componentização e Organização Modular (`src/`)
- `components/DiscountDashboard.jsx`: Interface visual interativa com campos de entrada e exibição de resultados.
- `services/discountService.js`: Módulo com as regras puras de cálculo e fórmulas de negócio.
- `tests/unit/`, `tests/integration/`, `tests/performance/`: Divisão clara das suítes de validação conforme a finalidade do teste.

---

## 4. Os Três Níveis de Validação Aplicados

### A. Testes Unitários (`tests/unit/`)
- **Foco:** Validar isoladamente as funções e regras puras do serviço de cálculo (`discountService.js`).
- **Simulação de Falha:** Alteração arbitrária da regra de negócio (ex.: aplicar 15% em vez de 10%), gerando quebra imediata na asserção esperada do teste.

### B. Testes de Integração (`tests/integration/`)
- **Foco:** Testar o fluxo conjunto entre os componentes visuais da UI e a camada de serviços, garantindo que botões e eventos respondam corretamente.
- **Simulação de Falha:** Modificação do rótulo de um elemento no formulário ou alteração no seletor de um botão de ação, quebrando o fluxo de interação automatizado.

### C. Testes de Desempenho / Carga (`tests/performance/`)
- **Foco:** Medir a latência média das operações e assegurar conformidade com os Acordos de Nível de Serviço (SLAs).
- **Simulação de Falha:** Configuração de um limiar rígido de resposta irreal (ex.: tempo máximo de execução inferior a $1\text{ms}$), gerando rejeição pelo pipeline por tempo estourado.

---

## 5. Matriz Comparativa dos Modos de Teste

| Categoria do Teste | Objeto de Inspeção | Objetivo Principal | Cenário Típico de Quebra no CI |
| :--- | :--- | :--- | :--- |
| **Unitário** | Funções atômicas e cálculos (`discountService.js`) | Garantir correção matemática e conformidade das regras isoladas | Divergência no percentual aplicado no cálculo |
| **Integração** | Interação entre interface (UI) e regras de serviço | Certificar o funcionamento do fluxo completo do usuário | Mudança em IDs/classes de botões impedindo o disparo da ação |
| **Performance** | Tempo de resposta e consumo computacional | Assegurar escalabilidade e cumprimento de limites de latência | Resposta que ultrapassa a cota limite de tempo estipulada |
| **Análise Estática (Lint)** | Estrutura e sintaxe do código-fonte (ESLint) | Manter legibilidade, padrões uniformes e evitar bugs silenciosos | Variáveis declaradas e nunca invocadas (`no-unused-vars`) |

---

## 6. Considerações Finais

A Aula 07 estabelece que uma esteira de Integração Contínua moderna atua como o principal guardião da saúde do repositório. A sincronização de análises estáticas de qualidade com baterias abrangentes de testes unitários, integrados e de performance no GitHub Actions garante que nenhuma alteração instável chegue aos ambientes produtivos.
