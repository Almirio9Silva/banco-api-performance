# Banco API Performance

Repositório destinado à implementação de testes de performance utilizando **JavaScript** e **K6**, permitindo validar o comportamento da API sob diferentes cargas de trabalho, identificar gargalos e acompanhar métricas de desempenho.

## 📖 Introdução

Este projeto reúne cenários de testes de performance para a API do Banco, utilizando o **K6** como ferramenta principal de execução.

Os testes foram organizados de forma modular para facilitar a manutenção, reutilização de código e criação de novos cenários.

A URL da API é definida por meio da variável de ambiente `BASE_URL`, permitindo executar os testes contra diferentes ambientes (desenvolvimento, homologação, produção, etc.) sem necessidade de alterar o código.

---

## 🚀 Tecnologias utilizadas

* JavaScript (ES6+)
* K6
* Node.js (opcional, para gerenciamento de dependências caso o projeto utilize bibliotecas externas)

---

## 📂 Estrutura do repositório

```text
.
├── scripts/
├── helpers/
├── payloads/
├── data/
├── utils/
├── package.json
└── README.md
```

> A estrutura acima representa a organização esperada do projeto. Caso novos diretórios sejam adicionados, basta complementar esta documentação.

---

## 📁 Objetivo de cada grupo de arquivos

### `scripts/`

Contém os cenários de testes de performance executados pelo K6.

Cada arquivo representa um teste independente ou um fluxo específico da aplicação.

### `helpers/`

Responsável por armazenar funções auxiliares reutilizadas pelos cenários de teste, evitando duplicação de código.

### `payloads/`

Armazena os corpos (payloads) utilizados nas requisições HTTP.

### `data/`

Contém massas de dados utilizadas durante os testes.

### `utils/`

Reúne funções utilitárias compartilhadas entre os testes, como tratamento de respostas, geração de dados e configurações comuns.

### `package.json`

Arquivo utilizado para gerenciamento das dependências do projeto (quando necessário).

---

## ⚙️ Instalação

### Clone o repositório

```bash
git clone https://github.com/Almirio9Silva/banco-api-performance.git
```

Entre na pasta do projeto:

```bash
cd banco-api-performance
```

Caso existam dependências do Node.js:

```bash
npm install
```

---

## ▶️ Execução dos testes

Antes de executar qualquer teste, é necessário informar a variável de ambiente `BASE_URL`, responsável por definir a URL da API que será testada.

### Linux / macOS

```bash
BASE_URL=https://minha-api.com k6 run scripts/script.js
```

### Windows (PowerShell)

```powershell
$env:BASE_URL="https://minha-api.com"
k6 run scripts/script.js
```

### Windows (CMD)

```cmd
set BASE_URL=https://minha-api.com
k6 run scripts\script.js
```

---

## 📊 Dashboard em tempo real e exportação do relatório

O K6 permite acompanhar a execução dos testes por meio de um dashboard em tempo real e exportar o relatório em HTML ao final da execução.

### Linux / macOS

```bash
BASE_URL=https://minha-api.com \
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run scripts/script.js
```

Ou em uma única linha:

```bash
BASE_URL=https://minha-api.com K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run scripts/script.js
```

### Windows (PowerShell)

```powershell
$env:BASE_URL="https://minha-api.com"
$env:K6_WEB_DASHBOARD="true"
$env:K6_WEB_DASHBOARD_EXPORT="html-report.html"

k6 run scripts/script.js
```

Ao término da execução, será gerado o arquivo:

```text
html-report.html
```

Esse relatório poderá ser aberto diretamente no navegador para análise das métricas coletadas durante o teste.
