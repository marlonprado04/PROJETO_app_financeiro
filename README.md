# 💸 Personal Budget App – Clone Simples do YNAB (em desenvolvimento)

Este repositório contém o planejamento e, futuramente, o código-fonte de um sistema pessoal de orçamento financeiro, inspirado no funcionamento do **YNAB (You Need A Budget)**.

---

## 🎯 Objetivos do Projeto

- Desenvolver uma aplicação completa com **Java + Spring Boot (API REST)** e **Angular (SPA Front-end)**.
- Controlar finanças pessoais usando o método de **orçamento por categorias** (envelopes).
- Hospedar o sistema em um **VPS próprio com Docker e HTTPS**.
- Criar uma API reutilizável para integração com um **aplicativo Android (nativo ou híbrido)**, com possibilidade futura de suporte a **iOS**.
- Utilizar o projeto como **ferramenta pessoal** e também como **item de portfólio profissional**.
- Aprender e aplicar conceitos de:
  - Arquitetura backend limpa e modular
  - Consumo de APIs no Angular e em apps mobile
  - Boas práticas de autenticação e segurança
  - Deploy em produção

---

## 🧠 Funcionalidades previstas (MVP)

- [ ] Cadastro de contas bancárias manuais
- [ ] Cadastro de categorias e subcategorias de orçamento
- [ ] Lançamento de receitas, despesas e transferências 
- [ ] Orçamento mensal por categoria / subcategoria

## Funcionalidades futuras 

- [ ] Relatório simples de gastos por mês e categoria
- [ ] Interface web responsiva com Angular
- [ ] Aplicativo Android (primeira versão simples com Flutter ou Angular + Capacitor)
- [ ] Versão iOS (futuramente, após Android)
- [ ] Deploy em VPS com Docker, Nginx e HTTPS

---

## 🛠️ Stack Tecnológica

### Backend
- Java 17+  
- Spring Boot  
- Spring Data JPA (Hibernate)
- Spring Security (JWT) (para versões futuras com autenticação)  
- SQLite (banco local para desktop)  
- PostgreSQL (para backend web/produção remota)  
- Docker (para ambiente e deploy futuros)

### Frontend Web
- Angular 17+  
- Angular Material  
- Consumo de API REST com HttpClient  
- Gráficos com Chart.js (ou similar)  
- **Electron** (empacotamento do Angular para app desktop local)

### Mobile App (futuro)
- Flutter (preferência atual) ou Angular + Capacitor  
- Comunicação com API via HTTP  
- Deploy Google Play e App Store (mais adiante)

### DevOps
- Docker + Docker Compose  
- Nginx (proxy reverso para API e frontend web)  
- Let's Encrypt (certificados SSL/TLS gratuitos)  
- VPS Linux (Ubuntu Server ou similar) para deploy web  

---

## 🗓️ Planejamento Geral

### Etapas de Desenvolvimento (previsão: 12 semanas para versão web)

| Etapa                           | Semanas | Status   |
|----------------------------------|---------|----------|
| Planejamento e wireframes        | 1–2     | 🔜       |
| Backend (API + autenticação)     | 3–5     | 🔜       |
| Frontend Angular (SPA)           | 6–8     | 🔜       |
| Deploy + Docker + HTTPS          | 9       | 🔜       |
| Testes + Documentação + Portfólio| 10–12   | 🔜       |
| Aplicativo Android (início)      | 13+     | 🔜       |

> ⚠️ *O projeto está no estágio de planejamento. As estimativas poderão ser ajustadas conforme evolução.*

---

---

## 📅 Cronograma por Semanas

| Semana | Tarefas Principais                                                                 |
|--------|-------------------------------------------------------------------------------------|
| 1      | Definição de escopo, estudo do YNAB, levantamento de requisitos e funcionalidades  |
| 2      | Wireframes, definição da modelagem inicial e estrutura da base de dados (ERD)      |
| 3      | Criação do projeto Spring Boot, entidades e repositórios base                      |
| 4      | Implementação de autenticação com Spring Security + JWT                            |
| 5      | Endpoints REST para contas, categorias, subcategorias e lançamentos                |
| 6      | Criação do projeto Angular + estrutura básica + tela de login                      |
| 7      | Integração com API (login + dashboard)                                             |
| 8      | CRUD completo no front-end: contas, categorias e lançamentos                       |
| 9      | Dockerização do projeto (backend, banco, frontend) + Nginx e HTTPS                 |
| 10     | Refatorações, ajustes de UX, testes manuais e responsividade                       |
| 11     | Escrita da documentação (README, diagramas, instruções de uso)                     |
| 12     | Finalização do MVP, checklist para portfólio, criação de vídeo/apresentação        |
| 13+    | Início do App Android (com Flutter ou Capacitor)                                   |

> 🧠 *Este cronograma é flexível e poderá ser ajustado conforme evolução e aprendizados ao longo do projeto.*

## 🚀 Plano de Desenvolvimento - Passo a Passo

### 1. Configurar o Ambiente
- [ ] Instalar JDK 17+
- [ ] Instalar Node.js + npm
- [ ] Instalar Angular CLI (`npm install -g @angular/cli`)
- [ ] Instalar Electron (`npm install electron --save-dev`)
- [ ] Configurar IDE para Java (IntelliJ IDEA, VSCode com extensões Java)
- [ ] Configurar IDE para Angular (VSCode ou WebStorm)

### 2. Criar o Backend - Spring Boot (Fase 1)
- [ ] Criar projeto Spring Boot básico com Spring Web e Spring Data JPA
- [ ] Configurar conexão com SQLite
- [ ] Definir modelos básicos: User, Account, Category, Subcategory, Transaction
- [ ] Implementar autenticação básica
- [ ] Implementar CRUD para contas, categorias e versi
- [ ] Testar API com Postman

### 3. Criar o Frontend - Angular (Fase 1)
- [ ] Gerar novo projeto Angular
- [ ] Desenvolver telas básicas: Login, Dashboard, Cadastro e Listagem de Contas, Categorias e Transações
- [ ] Consumir API REST do backend com HttpClient
- [ ] Implementar rotas e navegação básica

### 4. Integrar Desktop com Electron (Fase 2)
- [ ] Configurar projeto Angular para rodar dentro do Electron (servir o build do Angular como app desktop)
- [ ] Configurar comunicação local entre Electron e backend Spring (rodar localmente)
- [ ] Testar funcionamento offline (backend + frontend local)

### 5. Exportar e Importar Dados (Fase 3)
- [ ] Implementar funcionalidade para exportar dados em JSON
- [ ] Implementar importação para restaurar backup local
- [ ] Testar fluxos de backup e restauração

### 6. Sincronizar e Criar API Remota (Fase 4 - opcional)
- [ ] Criar endpoints para sincronização (backup na nuvem, GitHub, etc)
- [ ] Implementar autenticação via JWT para uso remoto (se desejar)
- [ ] Implementar sincronização incremental ou completa

### 7. Melhorar UI/UX e Fazer Deploy
- [ ] Polir interface, responsividade e usabilidade
- [ ] Empacotar app Electron para distribuição (Windows, Linux, Mac)
- [ ] Documentar projeto e publicar no GitHub


## 📄 Licença

Este projeto está licenciado sob a **GNU General Public License (GPL) v3.0**.

- O código é aberto para leitura, modificação, e uso pessoal ou educacional.
- Qualquer software derivado **deve ser liberado sob a mesma licença GPL**.
- Qualquer distribuição ou modificação do código **deve incluir o código-fonte**.

> Para mais detalhes, veja o arquivo [LICENSE](./LICENSE).
