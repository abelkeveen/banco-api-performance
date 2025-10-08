# Testes de Performance da API do Banco com K6

Repositório com testes de performance automatizados desenvolvidos com a ferramenta [Grafana K6](https://k6.io/) e escritos em JavaScript, voltados para a API do sistema bancário.

🔗 Repositório: [github.com/juliodelimas/banco-api-performance](https://github.com/abelkeveen/banco-api-performance)

---

## 📌 Introdução

Este projeto tem como objetivo simular diferentes cargas e cenários de uso para a API do banco, avaliando seu desempenho e identificando possíveis gargalos. Os testes são escritos com foco em modularidade, organização por contexto e reutilização de modelos de dados.

---

## ⚙️ Tecnologias Utilizadas

- [K6](https://k6.io/) – Ferramenta open source de testes de carga e performance.
- JavaScript (ES6)
- [GJSON](https://github.com/tidwall/gjson) – Para extração de dados em respostas JSON.
- Variáveis de ambiente para configuração dinâmica (ex: `BASE_URL`).

---

## 📁 Estrutura do Repositório

```bash
banco-api-performance/
├── config/            # Arquivos de configuração de variaáveis de ambiente
│ └── config.local.json
│
├── fixtures/          # Dados de entrada para os testes (ex: usuários, payloads)
│ └── postLogin.json
│
├── helpers/         # Funções utilitárias para interação com a API
│ └── autenticacao.js      
│
├── tests/           # Casos de teste organizados por módulo da API
│ ├── login.test.js
│ └── transferencias.test.js
│
├── utils/        # Funções utilitárias reutilizáveis
│ └── variaveis.js
│
├── .gitignore
├── html-report.html
└── README.md              
```

---

## 🎯 Objetivo de Cada Grupo de Arquivos

| **fixtures** | Dados de entrada para os testes (ex: usuários, payloads). 
| **helpers** | Funções utilitárias para interação com a API.
| **tests** | Casos de teste organizados por módulo da API
| **utils** | Funções utilitárias reutilizáveis
| **config** | Arquivos de configuração de variaáveis de ambiente

---

## 🛠️ Instalação 

1. **Clone o repositório**
   ```bash
   git clone https://github.com/abelkeveen/banco-api-performance.git
   cd banco-api-performance
   ```

2. **Configure as Variáveis de Ambiente**
   Altere o arqivo `config.local.json` e defina a URL base da API a ser testada:

   ```json
   {
      "baseUrl": "http://localhost:3000"
   }
   ```
   Essas variáveis serão usada dinamicamente nos testes para montar as requisições.

3. **Instale o K6 (caso ainda não tenha instalado)**
   - [Instruções oficiais de instalação](https://k6.io/docs/get-started/installation/)

4. **(Opcional)** Instale dependências auxiliares, se existirem:
   ```bash
   npm install
   ```

---

## 🚀 Execução dos Testes

```bash
k6 run tests/login.test.js
```
Certifique-se de passar a variável de ambiente `BASE_URL`, caso não esteja usando um `config.local.json` ou uma abordagem de carregamento automático:

```bash
k6 run tests/autenticacao/login.test.js -e BASE_URL=http://localhost:3000
```

### 2. Acompanhar o relatório em tempo real via dashboard web

Para acompanhar a execução dos testes com visualização em tempo real e exportar o relatório final em HTML, utilize as variáveis de ambiente do K6:

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=reports/html-report.html \
k6 run tests/autenticacao/login.test.js \
-e BASE_URL=https://localhost:3000
```

Após a execução:
- Um **dashboard interativo** será exibido no navegador.
- O **relatório HTML** será exportado automaticamente para `reports/html-report.html`.


---

## 🧾 Licença

Este projeto é de uso livre para fins de estudo e demonstração de testes de performance.  
Sinta-se à vontade para contribuir ou adaptar os testes conforme suas necessidades.

---

**Autor:** [Abel Keveen](https://github.com/abelkeveen)  
**Projeto:** *Banco API Performance Tests*
