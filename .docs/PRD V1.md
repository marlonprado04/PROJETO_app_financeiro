# 📚 PRD 
[PRD no Notion](https://marlonprado04.notion.site/Product-Requirements-Document-PRD-20cb296b2792800cbd4ecc9bbc57d0e6?source=copy_link)


# Product Requirements Document (PRD)

## 📌 Projeto: **YNAB Clone - Gerenciador Financeiro Pessoal Offline**

### 🧠 Visão Geral

Criar uma aplicação desktop que auxilie na organização financeira pessoal com base no modelo de orçamento por categorias e controle contínuo de fluxo de caixa, inspirado no YNAB (You Need A Budget). O sistema deverá funcionar **100% offline**, mas com estrutura escalável para possível sincronização futura com nuvem.

---

## 🎯 Objetivos do Produto

- Prover uma ferramenta de orçamento pessoal offline
- Implementar um sistema baseado nos princípios do YNAB
- Permitir que o usuário controle receitas, despesas, contas e metas
- Manter separação entre frontend e backend para facilitar manutenção
- Garantir portabilidade e usabilidade em Windows e Linux via Electron

---

## 🧱 Arquitetura Técnica

### 1. **Frontend**

- **Framework:** Angular
- **UI:** Angular Material
- **State Management:** Componente 
- **API calls:** HTTP client para comunicação com backend local
- **Build:** Produzido com `ng build` e servido no Electron

### 2. **Backend**

- **Framework:** Spring Boot
- **Banco de Dados:** SQLite (modo local em disco)
- **ORM:** Hibernate / JPA
- **Exposição de dados:** RESTful API
- **Execução:** Iniciado como processo filho dentro do Electron

### 3. **Desktop App Container**

- **Plataforma:** Electron
- **Modo de operação:**
    - `main.js` inicia backend Spring Boot via `child_process.spawn()`
    - Servidor acessado em `http://localhost:8080`
    - Angular é carregado na WebView

---

## 🧮 Funcionalidades Essenciais (v1 MVP)

### 🎛️ Tela Principal

- Visão geral das contas, saldo atual e orçamento disponível

### 🧾 Transações

- CRUD de transações (data, descrição, valor, categoria, conta)

### 💰 Contas

- CRUD de contas (nome, saldo inicial, tipo)

### 🧩 Categorias de orçamento

- Criar categorias e definir metas mensais

### 🔄 Realocação de verbas

- Mover orçamento entre categorias

---

## 🔐 Considerações Técnicas

### Offline First

- Toda persistência via SQLite local
- Angular deve operar com dados sincronizados via REST

### Futuro Online

- Possibilidade de acoplar camada de sincronização remota via API externa
- Arquitetura REST do backend já prepara esse caminho

---

## 📦 Empacotamento

- **Build Final:** Electron embala frontend Angular e inicia backend Spring Boot
- **Distribuição:** App desktop para Linux e Windows (.exe e .AppImage)

---

## 🧪 Testes

### Frontend

- Testes unitários 

### Backend

- Testes unitários com JUnit + Mockito
- Testes de integração com TestContainers (SQLite)

---

## 🛣️ Roadmap de Entregas

### 🟩 Fase 1 – MVP Local

- [ ]  Estrutura do projeto Angular + Spring Boot
- [ ]  Integração Angular ↔ Spring REST
- [ ]  Persistência local via SQLite
- [ ]  CRUD de contas, categorias, transações
- [ ]  Interface mínima funcional

### 🟦 Fase 2 – Empacotamento Electron

- [ ]  Setup inicial do Electron
- [ ]  Servir Angular e iniciar backend local via Electron
- [ ]  Script de build multiplataforma

### 🟨 Fase 3 – Refino e usabilidade

- [ ]  Feedbacks visuais
- [ ]  Validações e UX
- [ ]  Sistema de backup local

---

## 🛠️ Tecnologias Envolvidas

| Camada | Stack Principal |
| --- | --- |
| Frontend | Angular, Angular Material |
| Backend | Spring Boot, JPA, REST, SQLite |
| Desktop App | Electron, Node.js |
| Build Tool | Maven (Spring), Angular CLI |
| Testes | JUnit, Karma, Jasmine, etc |
