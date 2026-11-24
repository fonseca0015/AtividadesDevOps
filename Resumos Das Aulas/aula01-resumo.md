# Síntese Teórica — Aula 01: Visão Geral de DevOps e Apresentação do Curso

**Curso:** Tecnologia em Análise e Desenvolvimento de Sistemas  
**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição de Ensino:** Faculdade de Tecnologia de Sorocaba (FATEC)  
**Professor Responsável:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  

---

## 1. Apresentação do Docente e Contexto da Disciplina

No encontro inicial, o Prof. Me. Deivison S. Takatu compartilhou seu itinerário acadêmico e profissional:
- **Trajetória Acadêmica:** Graduado em Análise e Desenvolvimento de Sistemas (2016), detentor de quatro pós-graduações lato sensu, Mestre em Ciência da Computação (2021) e em processo de especialização na área de Inteligência Artificial.
- **Atuação no Mercado e Docência:** Experiência consistente como Gerente de Projetos de TI e no ensino superior, além de liderar e orientar pesquisas em desenvolvimento web, metodologias ágeis e tecnologias interativas na Fatec.

O plano de ensino foi exposto ressaltando as competências esperadas: compreensão teórica dos pilares ágeis e aplicação prática de esteiras automatizadas de construção, testes e publicação de sistemas modernos.

---

## 2. Fundamentos de DevOps Introduzidos

A aula estabeleceu os conceitos-chave que guiarão todo o semestre:

### Gestão de Código e Versionamento
- Utilização de sistemas distribuídos (Git) para assegurar histórico, rastreabilidade e desenvolvimento concorrente por meio de branches (ramificações).
- O deploy representa o ato de disponibilizar uma versão homologada em ambiente operacional acessível ao usuário final.

### Automação de Processos e Conceito de Pipeline
- Uma pipeline consiste em uma sequência predefinida de passos automatizados (restauração de pacotes, compilação, testes automatizados, inspeção estática e implantação).
- Substitui intervenções manuais suscetíveis a falhas humanas por processos consistentes, confiáveis e repetíveis.

### Integração Contínua (CI - Continuous Integration)
- Foco em integrar alterações ao repositório central com alta frequência.
- Cada submissão engatilha rotinas automáticas de validação, permitindo identificar e solucionar incompatibilidades precocemente (*Fail Fast*).

### Garantia da Qualidade e Análise Estática
- Verificações de cobertura de código, conformidade com padrões de codificação (linters), complexidade ciclomática e vulnerabilidades de dependências antes da publicação.

### Estratégia de Testes Automatizados
- Validações em níveis complementares: testes de unidade (componentes isolados), integração (comunicação entre camadas) e testes de ponta a ponta (E2E).

### Entrega Contínua (CD - Continuous Delivery)
- O software avança pelas etapas automatizadas e permanece em estado constante de prontidão para entrada em produção mediante aprovação de negócio.
- Benefícios diretos: redução do tempo até o lançamento (*time-to-market*), maior previsibilidade e minimização de riscos operacionais.

### Conteinerização e Padrões de Deploy
- Adoção de contêineres (Docker) para eliminar variações ambientais entre estações de desenvolvimento e servidores de produção.
- Estratégias modernas de atualização sem indisponibilidade: *Rolling Update*, *Blue-Green* e *Canary Release*, que proporcionam migração gradual de tráfego e rollback simplificado.

---

## 3. Construção de Portfólio Técnico

Foi enfatizado que manter registros públicos e organizados no GitHub não atua somente como critério de avaliação acadêmica, mas serve de vitrine técnica profissional para o mercado de trabalho, evidenciando domínio prático sobre automação, engenharia de software e processos colaborativos.

---

## 4. Sistema e Critérios de Avaliação

O cálculo da média semestral é parametrizado pela fórmula:

$$\text{Média Final} = (P_1 \times 0{,}25) + (P_2 \times 0{,}25) + ((PJ + AT) \times 0{,}25)$$

- **$P_1$:** Primeira avaliação teórica/prática
- **$P_2$:** Segunda avaliação teórica/prática
- **$PJ$:** Projeto prático aplicado
- **$AT$:** Tarefas práticas e atividades contínuas

---

## 5. Diretrizes da Primeira Atividade Prática

1. Organização de grupos colaborativos de 3 a 5 discentes para atuação nas atividades do semestre.
2. Planejamento de encontros de alinhamento técnico semanais.
3. Criação de repositório central no GitHub contendo a documentação estruturada da Aula 01 em Markdown.
4. Preenchimento individual do formulário de diagnóstico pedagógico inicial.

---

## 6. Referências Bibliográficas de Apoio

- ARUNDEL, J.; DOMINGUS, J. *DevOps nativo de nuvem com Kubernetes*. São Paulo: Novatec, 2019.
- HUMBLE, J.; FARLEY, D. *Entrega Contínua: Como Entregar Software de Forma Rápida e Confiável*. Porto Alegre: Bookman, 2014.
- KIM, G. et al. *Manual de DevOps: Como Obter Agilidade, Confiabilidade e Segurança em Organizações Tecnológicas*. São Paulo: Alta Books, 2018.
- MORAES, G. *Caixa de Ferramentas DevOps*. São Paulo: Casa do Código, 2015.
- MUNIZ, A. et al. *Jornada DevOps: Unindo Cultura Ágil, Lean e Tecnologia Para Entrega De Software Com Qualidade*. São Paulo: Brasport, 2019.
- PIRES, A.; MILITÃO, J. *Integração Contínua com Jenkins*. São Paulo: Casa do Código, 2019.
- SATO, D. *DevOps na prática: entrega de software confiável e automatizada*. São Paulo: Casa do Código, 2014.
- SILVERMAN, R. E. *Git: guia prático*. São Paulo: Novatec, 2019.
- VITALINO, J. F. N.; CASTRO, M. A. N. *Descomplicando o Docker*. 2. ed. São Paulo: Brasport, 2018.
