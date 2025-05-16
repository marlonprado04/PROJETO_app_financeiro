# 💸 Personal Budget App – Clone Simples do YNAB (em desenvolvimento)

Este repositório contém o planejamento e, futuramente, o código-fonte de um sistema pessoal de orçamento financeiro, inspirado no funcionamento do **YNAB (You Need A Budget)**.

---

## 🎯 Objetivos do Projeto

- Desenvolver uma aplicação web completa com **Java + Spring Boot (API REST)** e **Angular (SPA Front-end)**.
- Controlar finanças pessoais usando o método de **orçamento por categorias** (envelopes).
- Hospedar o sistema em um **VPS próprio com Docker, Nginx e HTTPS**.
- Utilizar o projeto como **ferramenta pessoal** e também como **item de portfólio profissional**.
- Aprender e aplicar conceitos de:
  - Arquitetura backend limpa e modular
  - Consumo de APIs REST no Angular
  - Boas práticas de autenticação e segurança
  - Deploy em produção com Docker e HTTPS

---

## 🧠 Funcionalidades previstas (MVP)

- [ ] Cadastro de contas bancárias manuais
- [ ] Cadastro de categorias e subcategorias de orçamento
- [ ] Lançamento de receitas, despesas e transferências 
- [ ] Orçamento mensal por categoria/subcategoria
- [ ] Interface web responsiva com Angular

## Funcionalidades futuras 

- [ ] Relatório simples de gastos por mês e categoria
- [ ] Exportação e importação de dados (backup)
- [ ] Autenticação com JWT
- [ ] Sincronização com servidor remoto (opcional)

---

## 🛠️ Stack Tecnológica

### Backend
- Java 17+  
- Spring Boot  
- Spring Data JPA (Hibernate)
- Spring Security (JWT) — para versão futura com autenticação  
- SQLite (ambiente local)  
- PostgreSQL (produção)  
- Docker (para ambiente e deploy)  

### Frontend Web
- Angular 17+  
- Angular Material  
- Consumo de API REST com HttpClient  
- Gráficos com Chart.js (ou similar)

### DevOps
- Docker + Docker Compose  
- Nginx (proxy reverso)  
- Let's Encrypt (certificados SSL gratuitos)  
- VPS Linux (Ubuntu Server ou similar)  

---

## 🗓️ Planejamento Geral

### Etapas de Desenvolvimento (previsão: 10 semanas para versão web)

| Etapa                           | Semanas | Status   |
|----------------------------------|---------|----------|
| Planejamento e wireframes        | 1–2     | 🔜       |
| Backend (API + autenticação)     | 3–5     | 🔜       |
| Frontend Angular (SPA)           | 6–8     | 🔜       |
| Deploy + Docker + HTTPS          | 9       | 🔜       |
| Testes + Documentação + Portfólio| 10      | 🔜       |

> ⚠️ *O projeto está no estágio de planejamento. As estimativas poderão ser ajustadas conforme evolução.*

---

## 📅 Cronograma por Semanas

| Semana | Tarefas Principais                                                                 |
|--------|-------------------------------------------------------------------------------------|
| 1      | Definição de escopo, estudo do YNAB, levantamento de requisitos e funcionalidades  |
| 2      | Wireframes e modelagem inicial da base de dados (ERD)                              |
| 3      | Criação do projeto Spring Boot, entidades e repositórios base                      |
| 4      | Implementação de autenticação com Spring Security + JWT                            |
| 5      | Endpoints REST para contas, categorias, subcategorias e lançamentos                |
| 6      | Criação do projeto Angular + tela de login                                         |
| 7      | Integração com API (login + dashboard)                                             |
| 8      | CRUD completo no front-end: contas, categorias e lançamentos                       |
| 9      | Dockerização do backend + frontend + configuração com Nginx e HTTPS                |
| 10     | Refatorações, testes manuais, responsividade e documentação final                  |

> 🧠 *Este cronograma é flexível e será ajustado conforme a evolução e aprendizados.*

---

## 🚀 Passo a Passo de Desenvolvimento

### 1. Configurar o Ambiente
- [ ] Instalar JDK 17+
- [ ] Instalar Node.js + npm
- [ ] Instalar Angular CLI (`npm install -g @angular/cli`)
- [ ] Configurar IDE para Java (IntelliJ IDEA ou VSCode com extensões Java)
- [ ] Configurar IDE para Angular (VSCode ou WebStorm)

### 2. Criar o Backend - Spring Boot
- [ ] Criar projeto com Spring Web e Spring Data JPA
- [ ] Configurar conexão com SQLite (dev) e PostgreSQL (prod)
- [ ] Definir modelos: User, Account, Category, Subcategory, Transaction
- [ ] Implementar autenticação básica (JWT)
- [ ] Criar endpoints REST
- [ ] Testar API com Postman

### 3. Criar o Frontend - Angular
- [ ] Gerar novo projeto Angular
- [ ] Desenvolver telas: Login, Dashboard, Contas, Categorias, Transações
- [ ] Consumir API com HttpClient
- [ ] Implementar rotas, navegação e componentes visuais

### 4. Deploy e Produção
- [ ] Criar arquivos Dockerfile e docker-compose
- [ ] Configurar Nginx como proxy reverso
- [ ] Adicionar HTTPS com Let's Encrypt
- [ ] Publicar em VPS e realizar testes de produção

---

## 📄 Licença

Este projeto está licenciado sob a **GNU General Public License (GPL) v3.0**.

- O código é aberto para leitura, modificação e uso pessoal ou educacional.
- Qualquer software derivado **deve ser liberado sob a mesma licença GPL**.
- Qualquer distribuição ou modificação do código **deve incluir o código-fonte**.

> Para mais detalhes, veja o arquivo [LICENSE](./LICENSE).

Se quiser, posso exportar isso como .md para você baixar. Deseja?

