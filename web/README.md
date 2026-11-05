# 🧪 Testes Automatizados - Webdojo (Cypress)

Este repositório contém a suíte de testes automatizados E2E (End-to-End) desenvolvida em **Cypress** para a aplicação web **Webdojo**.

---

## 📌 Pré-requisitos

Antes de iniciar, certifique-se de ter instalado em sua máquina:

- [Node.js](https://nodejs.org/) (Versão recomendada: LTS)
- Gerenciador de pacotes `npm` ou `yarn`

---

## 🚀 Instalação do Projeto

1. Clone o repositório para a sua máquina local:
   ```bash
   git clone https://github.com/rodrigopbbr/webdojo.git
   ```

2. Acesse a pasta do projeto:
   ```bash
   cd web
   ```

3. Instale as dependências necessárias:
   ```bash
   npm install
   ```

---

## 💻 Executando a Aplicação Localmente

A aplicação Webdojo faz parte deste mesmo repositório. Para poder executar os testes E2E, a aplicação precisa estar em execução no ambiente local.

Para iniciar a aplicação, execute:

```bash
npm run dev
```

> **Nota:** A aplicação estará disponível em `http://localhost:3000`.

---

## 📁 Estrutura do Projeto

A organização de diretórios do Cypress no projeto segue a seguinte estrutura:

```text
web/
└── cypress/
    ├── e2e/                     # Arquivos de especificações de teste (Test Specs)
    ├── fixtures/                # Massas de dados e arquivos de apoio para testes
    │   ├── cep.json             # Dados mockados de CEP
    │   ├── consultancy.json     # Dados mockados de consultoria
    │   └── document.pdf         # Arquivo de exemplo para testes de upload
    └── support/                 # Configurações de suporte e comandos customizados
        ├── actions/             # Ações encapsuladas/reutilizáveis
        │   └── consultancy.actions.js
        ├── commands.js          # Comandos customizados do Cypress (cy.command)
        ├── e2e.js               # Arquivo de suporte global importado antes dos testes
        └── utils.js             # Funções utilitárias auxiliares
```

---

## 🛠️ Scripts de Testes

Os testes podem ser executados tanto em modo *headless* (linha de comando) quanto em modo interativo (via Test Runner), além de executadores específicos para specs e visões mobile.

### 1. Iniciar Aplicação Web
Inicia o servidor local estático na porta 3000.
```bash
npm run dev
```

### 2. Executar Todos os Testes (Headless)
Roda a suíte completa de testes no terminal com a viewport configurada em **1440x900**.
```bash
npm run test
```

### 3. Abrir a Interface do Cypress (Test Runner)
Abre o Cypress no modo interativo (UI) para seleção e acompanhamento visual dos testes.
```bash
npm run test:ui
```

### 4. Executar Testes de Login (Desktop)
Executa apenas a spec `cypress/e2e/login.cy.js` com a resolução desktop (1440x900).
```bash
npm run test:login
```

### 5. Executar Testes de Login (Mobile)
Executa apenas a spec `cypress/e2e/login.cy.js` simulando uma tela mobile (414x896).
```bash
npm run test:login:mobile
```

---

## 📊 Lista de Scripts (`package.json`)

```json
"scripts": {
  "dev": "serve -s dist -p 3000",
  "test": "npx cypress run --config viewportWidth=1440,viewportHeight=900",
  "test:ui": "npx cypress open",
  "test:login": "npx cypress run --spec cypress/e2e/login.cy.js --config viewportWidth=1440,viewportHeight=900",
  "test:login:mobile": "npx cypress run --spec cypress/e2e/login.cy.js --config viewportWidth=414,viewportHeight=896"
}
```