Repositório com testes de performance automatizados desenvolvidos com k6 e JavaScript, voltados para avaliação de uma API bancária.  

🔗 [Acesse o repositório](https://github.com/Nayrasz/banco-api-performance)

# 📊 Testes de Performance com k6 - Banco API

## 📌 Introdução

Este repositório contém scripts de testes de performance desenvolvidos
em JavaScript utilizando a ferramenta k6. O objetivo é avaliar o
comportamento e a estabilidade de uma API bancária sob diferentes
condições de carga, permitindo identificar gargalos, falhas e
oportunidades de melhoria.

Os testes foram estruturados de forma organizada e parametrizável,
permitindo fácil adaptação para diferentes ambientes através do uso de
variáveis de ambiente.

------------------------------------------------------------------------

## 🚀 Tecnologias Utilizadas

-   JavaScript (ES6+)
-   k6 --- ferramenta de testes de carga e performance
-   JSON --- arquivos de configuração
-   Variáveis de ambiente para configuração dinâmica (ex: `BASE_URL`)

------------------------------------------------------------------------

## 📁 Estrutura do Repositório

    banco-api-performance/
    │
    ├── config/
    │   └── config.local.json
    │
    ├── fixtures/
    │   └── postLogin.json
    │
    ├── helpers/
    │   └── autenticacao.js
    │
    ├── tests/
    │   ├── login.test.js
    │   └── transferencias.test.js
    │
    ├── utils/
    │   └── variaveis.js
    │
    └── README.md

------------------------------------------------------------------------

## 🧩 Objetivo de Cada Grupo de Arquivos

### 📂 `config/`

Armazena arquivos de configuração do ambiente local, como: - URL base da
API - Parâmetros que podem variar entre ambientes (dev, homolog, etc.)

Permite desacoplar configurações dos scripts de teste.

------------------------------------------------------------------------

### 📂 `fixtures/`

Contém dados estáticos utilizados nos testes, como: - Payloads de
requisições - Massa de dados simulada

Exemplo: - `postLogin.json` → corpo da requisição de login

Ajuda a manter os testes mais organizados e reutilizáveis, evitando
hardcode nos scripts.

------------------------------------------------------------------------

### 📂 `helpers/`

Responsável por funções auxiliares relacionadas à lógica de negócio dos
testes.

Exemplo: - `autenticacao.js` → funções para login e obtenção de token

Objetivo: - Reutilizar fluxos comuns (ex: autenticação) - Evitar
duplicação de código - Deixar os testes mais limpos e focados no cenário

------------------------------------------------------------------------

### 📂 `tests/`

Contém os scripts principais de testes de performance, organizados por
funcionalidade da API.

Exemplos: - `login.test.js` → testes de carga no endpoint de login -
`transferencias.test.js` → testes de transferência

Objetivo: - Simular cenários reais de uso - Executar testes com
diferentes cargas - Validar comportamento e desempenho da API

------------------------------------------------------------------------

### 📂 `utils/`

Funções utilitárias genéricas usadas em todo o projeto.

Exemplo: - `variaveis.js` → gerenciamento da `BASE_URL` e variáveis de
ambiente

Objetivo: - Centralizar configurações reutilizáveis - Facilitar
manutenção - Padronizar acesso a variáveis globais

------------------------------------------------------------------------

## ⚙️ Instalação

### 1. Clonar o repositório

    git clone https://github.com/Nayrasz/banco-api-performance.git
    cd banco-api-performance

### 2. Instalar o k6

Consulte: https://grafana.com/docs/k6/latest/set-up/install-k6/

------------------------------------------------------------------------

## ▶️ Execução dos Testes

### 🔹 Usando arquivo local (`config.local.json`)

Altere o arquivo:

``` json
{
    "baseUrl": "http://localhost:3000"
}
```

Execute:

``` bash
k6 run tests/login.test.js
```

------------------------------------------------------------------------

### 🔹 Usando variável de ambiente (`BASE_URL`)

``` bash
k6 run tests/login.test.js -e BASE_URL=http://localhost:3000
```

------------------------------------------------------------------------

### 📊 Dashboard em tempo real

``` bash
K6_WEB_DASHBOARD=true k6 run tests/login.test.js -e BASE_URL=http://localhost:3000
```

------------------------------------------------------------------------

### 💾 Exportação do relatório em HTML

``` bash
K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run tests/login.test.js -e BASE_URL=http://localhost:3000
```

Após a execução, o relatório será gerado como `html-report.html`.

------------------------------------------------------------------------

## 🎯 Objetivo do Projeto

-   Validar desempenho da API
-   Identificar gargalos
-   Simular cenários reais
-   Apoiar decisões de escalabilidade
