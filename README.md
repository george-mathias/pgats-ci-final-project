# Pipeline CI com GitHub Actions - Mocha

Este projecto implementa uma pipeline de integração contínua utilizando GitHub Actions para execução de testes com Mocha.

## Funcionalidades Implementadas

### 1. **Execução por Push**
- Arquivo: `.github/workflows/ci-on-push.yml`
- Os testes são executados automaticamente sempre que há um push na branch `main`
- Relatórios são gerados e armazenados como artefactos

### 2. **Execução Manual**
- Arquivo: `.github/workflows/ci-manual.yml`
- O workflow pode ser disparado manualmente através do botão "Run workflow" na Actions tab
- Opção para gerar relatório de cobertura adicional

### 3. **Execução Agendada (Cron)**
- Arquivo: `.github/workflows/ci-scheduled.yml`
- O pipeline roda automaticamente diariamente às 02:00 horas
- Cron expression: `0 2 * * *`
- Também permite disparo manual para teste

### 4. **Geração de Relatório de Testes**
- Relatório HTML em `mochawesome-report/index.html`
- Relatório armazenado como artefacto no GitHub Actions

### 5. **Armazenamento/Publicação do Relatório**
- Relatórios armazenados como artefactos na Actions do GitHub
- Retenção de 7 dias para relatórios de testes

## Relatórios Gerados

| Tipo | Formato | Localização |
|------|---------|-----|
| HTML | mochawesome-report/index.html | `mochawesome-report/` |

## Instalação

```bash
npm install
```

## Execução de Testes Localmente

```bash
# Executar todos os testes
npm test

# Ver o relatório HTML
start coverage/mochawesome-report/index.html
```

## Workflow de CI

Os workflows são divididos em três arquivos separados:

| Arquivo | Descrição | Gatilho |
|---------|-----------|---------|
| `ci-on-push.yml` | Execução automática ao fazer push | Push na branch `main` |
| `ci-manual.yml` | Execução manual com opções | Botão "Run workflow" |
| `ci-scheduled.yml` | Execução agendada | Cron (02:00 diariamente) |

## Visualizar Relatórios

- Aceda a **GitHub Actions** para ver os relatórios
- Artfactos são retidos por **7 dias**
- Links para artefactos: `https://github.com/<user>/<repo>/actions`

## Links Úteis

- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Mocha Documentation](https://mochajs.org/)
- [Mochawesome Reporter](https://github.com/mochajs/mochawesome)

## Licença

Este projecto está sob a licença MIT.
