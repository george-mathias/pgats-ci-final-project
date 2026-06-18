# Pipeline CI com GitHub Actions - Mocha

Este projeto implementa uma pipeline de integração contínua utilizando **GitHub Actions** para execução de testes automatizados com **Mocha**,  
contemplando três modos de execução: por push, manual e agendada, com geração e publicação de relatórios de testes.


## Dependências

| Pacote | Versão | Descrição |
|--------|--------|-----------|
| Git | ^2.52.0 | Versionamento de código |
| Node.js | >= 24.x | Ambiente de execução JavaScript |
| mocha | ^11.7.6 | Framework de teste JavaScript |
| GitHub Test Reporter | ~0.0.11 | Gerador de relatórios JSON para Mocha |


## Instalação

1. Instale o [git](https://git-scm.com)
2. Instale o [nodejs](https://nodejs.org/)
3. Faça o download do projeto
   ```
   git clone https://github.com/george-mathias/pgats-ci-final-project.git
   ```
4. Entre na pasta do projeto
   ```shell
   pgats-ci-final-project
   ```
4. Instale as dependências
   ```shell
   npm install
   ```
5. Execute os testes
   ```nodejs
   npx mocha
   ```


## Funcionalidades Implementadas

### 1. **Execução por Push**
Os testes são executados automaticamente sempre que há um push na branch `main`.

### 2. **Execução Manual**
O workflow pode ser disparado manualmente através do botão "Run workflow" na aba Actions do GitHub.

### 3. **Execução Agendada (Schedule)**
O pipeline roda automaticamente diariamente às 05:00 horas.

### 4. **Geração de Relatório de Testes**
Relatórios JSON de testes são gerados e armazenados como artefactos na pipeline.

### 5. **Publicação do Relatório**
Relatórios armazenados como artefactos na Actions do GitHub, com retenção de 7 dias.


## Relatórios

- Acesse a aba **[Actions](https://github.com/george-mathias/pgats-ci-final-project/actions)** no GitHub
- Selecione o workflow desejado
- Seleicone uma execução para visualizar o reslatório
- Relatório disponível para download **ctrf-report.json**


## Estrutura dos Workflows

O projeto utiliza **três workflows separados**, cada um com suas obrigações:

### Workflow 1: [CI - Execução por Push](https://github.com/george-mathias/pgats-ci-final-project/actions/workflows/ci-on-push.yml)
- **Arquivo:** `.github/workflows/ci-on-push.yml`
- **Gatilho:** Push na branch `main`  
- **Funcionalidade:** Execução automática de testes após cada commit
- **Commit vazio para executar o workflow:** git commit --allow-empty -m "ci: disparo do workflow por push"

### Workflow 2: [CI - Execução Manual](https://github.com/george-mathias/pgats-ci-final-project/actions/workflows/ci-manual.yml)
- **Arquivo:** `.github/workflows/ci-manual.yml`
- **Gatilho:** Botão "Run workflow" na aba Actions
- **Funcionalidade:** Permite executar testes manualmente sob demanda

### Workflow 3: [CI - Execução Agendada](https://github.com/george-mathias/pgats-ci-final-project/actions/workflows/ci-scheduled.yml)
- **Arquivo:** `.github/workflows/ci-scheduled.yml`
- **Gatilho:** Cron expression `0 5 * * *` (todas as 05:00)
- **Funcionalidade:** Execução agendada automática de testes (com a possibilidade de ser executada manualmente)


## Conceitos Utilizados e Links Úteis

### [GitHub Actions](https://docs.github.com/en/actions)
- **Actions:** Fluxos de trabalho automatizados no GitHub
- **Workflows:** Conjuntos de ações que executam em sequência
- **Triggers:** Gatilhos que iniciam os workflows (push, schedule, manual)
- **Artifacts:** Arquivos gerados durante a execução e armazenados para download

### [GitHub Test Reporter](https://github.com/marketplace/actions/github-test-reporter)
- Ação que gera relatórios HTML de testes
- Integração com frameworks de teste como Mocha, Jest, Karma
- Publicação de relatórios diretamente na UI do GitHub

### [Mocha Documentation](https://mochajs.org/)
- Framework de teste JavaScript
- Suporte a async/await, beforeEach, afterEach
- Múltiplos reporters (JUnit, HTML, JSON, etc.)
