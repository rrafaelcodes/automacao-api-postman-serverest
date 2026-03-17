# 🚀 Automação de API REST - ServeRest (Postman)

## 💻 Sobre o Projeto
Este repositório contém uma suíte de testes automatizados E2E (Ponta a Ponta) desenvolvida para a API do [ServeRest](https://serverest.dev/), um simulador de loja virtual para estudos de Quality Assurance. O objetivo deste projeto é validar o fluxo completo de cadastro de usuário, autenticação, injeção de token e manipulação de produtos, garantindo o funcionamento integrado do back-end.

## 🛠️ Tecnologias Utilizadas
* **Postman:** Criação, execução das requisições e configuração do Collection Runner.
* **JavaScript:** Escrita dos scripts de validação (Tests) e manipulação de variáveis (Pre-request/Post-response Scripts).
* **API REST:** Padrão de arquitetura validado (Verbos HTTP, Status Codes, Query Parameters).

## ⚙️ Funcionalidades e Técnicas Aplicadas
* **Variáveis Dinâmicas de Ambiente:** Uso de `{{$randomEmail}}` e `{{$randomProductName}}` para evitar conflitos de duplicidade de dados (Status 400) em execuções sucessivas.
* **Manipulação de Token (Bearer):** Script automatizado para capturar o token JWT no endpoint de login, limpá-lo e injetá-lo no Header das requisições autenticadas subsequentes de forma 100% autônoma.
* **Testes Automatizados (Asserts):** Validação de Status Code (ex: `200 OK`, `201 Created`) utilizando o framework integrado do Postman (`pm.response.to.have.status()`).

## 🔄 Fluxo de Teste E2E Realizado
A Collection executa automaticamente as seguintes requisições em cadeia:
1. `POST /usuarios`: Cadastra um novo usuário administrador com e-mail gerado dinamicamente.
2. `POST /login`: Realiza a autenticação com as credenciais do usuário recém-criado e salva o Token em uma variável de coleção.
3. `POST /produtos`: Utiliza o Token de autorização para cadastrar um novo produto no banco de dados.
4. `GET /produtos`: Realiza uma busca filtrada via *Query Parameter* para garantir que o recurso foi persistido corretamente no servidor.

## 🚀 Como Executar
1. Clone este repositório em sua máquina.
2. Abra o Postman e importe o arquivo `.json` da Collection.
3. Clique nos três pontos ao lado da Collection e selecione **Run Collection**.
4. Observe a execução em cascata e os testes passando na aba do *Runner*.

---
*Projeto desenvolvido por Rafael, estudante de Ciência da Computação construindo soluções e portfólio prático para atuar na área de Quality Assurance (QA).*
