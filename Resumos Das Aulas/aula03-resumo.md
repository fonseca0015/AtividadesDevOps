# FACULDADE DE TECNOLOGIA DE SOROCABA — FATEC
## Curso Superior de Tecnologia em Análise e Desenvolvimento de Sistemas

---

### RELATÓRIO TÉCNICO DE CONFIGURAÇÃO E DEPLOY — TAREFA 03

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** FATEC Sorocaba  
**Docente:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Data Limite de Envio:** 29 de Agosto de 2026 às 23:59  

| INTEGRANTES DO GRUPO |
| :--- |
| Gabriel Fonseca |
| Karina de Moraes Garcia |
| Mike Willy Franguelli |
| Rafaela Mansano Fernandes |

---

## 1. Escopo e Objeto de Estudo

Este relatório descreve os procedimentos práticos executados na **Tarefa 03**, cujo escopo envolveu a gerência de configuração, versionamento distribuído e estruturação de uma esteira de entrega contínua (CD) conectada a uma aplicação web derivada de um template open-source.

A solução adotada foi o template *Landy*, uma landing page responsiva desenvolvida em **React.js**, **TypeScript** e **Node.js**. O código-fonte foi clonado, configurado no ambiente local de desenvolvimento, versionado no **GitHub** e integrado à plataforma de hospedagem em nuvem **Vercel** para implantações automatizadas baseadas em gatilhos de commit.

> **🌐 Referências do Projeto:**
> - **Repositório da Aplicação (GitHub):** [https://github.com/fonseca0015/ProjetoGitTemplate](https://github.com/fonseca0015/ProjetoGitTemplate)
> - **Ambiente em Produção (Vercel):** [https://projeto-git-template-7s74jspc2-fatec1.vercel.app](https://projeto-git-template-7s74jspc2-fatec1.vercel.app)
> - **Template Base (Repositório Original):** [https://github.com/Adrinlol/landy-react-template](https://github.com/Adrinlol/landy-react-template)

### Parâmetros e Especificações Técnicas:
- **Runtime:** Node.js (v22 LTS) e gerenciador de pacotes NPM.
- **Camada Visual:** React.js tipado com TypeScript e estilização via Styled-Components.
- **Organização de Dados:** Internacionalização descentralizada (i18n) orientada a arquivos JSON em `src/content/` e `src/locales/`.

---

## 2. Etapas de Configuração e Execução

### 2.1 Obtenção e Clonagem do Repositório Base
O código original foi clonado para a máquina local através do utilitário Git:

```bash
cd C:\Users\Gabriel\Desktop
git clone https://github.com/Adrinlol/landy-react-template.git ProjetoGitTemplate
cd ProjetoGitTemplate
code .
```

### 2.2 Resolução e Instalação de Dependências
Utilizou-se o gerenciador de pacotes NPM para download e resolução da árvore de módulos declarada no arquivo `package.json`:

```bash
npm install
```

### 2.3 Execução em Ambiente Local de Homologação
O servidor de desenvolvimento local foi inicializado para verificação de montagem dos componentes React e validação de rotas em `http://localhost:3000`:

```bash
npm start
```

### 2.4 Vinculação de Repositório Remoto e Versionamento
Configurou-se o repositório remoto sob o controle da equipe e realizou-se a publicação das alterações na branch principal (`main`):

```bash
git remote set-url origin https://github.com/fonseca0015/ProjetoGitTemplate.git
git branch -M main
git add .
git commit -m "feat: configuracao inicial da landing page a partir do template"
git push -u origin main
```

### 2.5 Configuração da Esteira de Deploy Contínuo (Vercel)
A plataforma Vercel foi conectada diretamente ao repositório GitHub. Dessa forma, qualquer nova alteração integrada à branch `main` desencadeia automaticamente o build e a publicação em ambiente de produção na nuvem.

---

## 3. Mapeamento Arquitetural de Arquivos

Abaixo encontra-se a organização estrutural do projeto após as adequações:

```text
ProjetoGitTemplate/
├── .github/              # Configurações de workflows e integrações do repositório
├── public/               # Ativos estáticos, manifesto da aplicação e index.html base
│   ├── fonts/            # Famílias tipográficas locais
│   ├── img/              # Vetores e ilustrações da interface
│   ├── favicon.ico
│   ├── index.html
│   └── manifest.json
├── src/                  # Código-fonte principal em React e TypeScript
│   ├── common/           # Componentes atômicos reaproveitáveis (botões, inputs)
│   ├── components/       # Módulos estruturais das seções do layout
│   ├── content/          # Dicionários de conteúdo e dados das seções
│   ├── locales/          # Definições de internacionalização (i18n)
│   ├── pages/            # Estrutura de visualização das páginas
│   ├── router/           # Gerenciamento de rotas e navegação
│   ├── styles/           # Folhas de estilo globais e temas
│   ├── index.tsx         # Ponto de inicialização do React
│   └── translation.ts    # Configurações do motor de tradução
├── .gitignore            # Diretrizes de exclusão do controle de versão
├── package.json          # Metadados do projeto, scripts e dependências
├── tsconfig.json         # Configuração de compilação do TypeScript
└── README.md             # Guia de introdução e instruções do projeto
```

---

## 4. Considerações Finais

A execução da Tarefa 03 consolidou a importância da Gerência de Configuração e da automação no ciclo de vida de uma aplicação. A integração contínua entre o versionamento no GitHub e o deploy automático na Vercel elimina gargalos manuais, previne falhas de sincronização e assegura que versões homologadas entrem em produção com agilidade e rastreabilidade total.
