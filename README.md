# 💸 Personal Budget App – Clone Simples do YNAB (em desenvolvimento)

Este repositório contém o planejamento e, futuramente, o código-fonte de um sistema pessoal de orçamento financeiro, inspirado no funcionamento do **YNAB (You Need A Budget)**.


## 📚 Sumário

- [💸 Personal Budget App – Clone Simples do YNAB (em desenvolvimento)](#-personal-budget-app--clone-simples-do-ynab-em-desenvolvimento)
  - [📚 Sumário](#-sumário)
  - [🎯 Objetivos do Projeto](#-objetivos-do-projeto)
  - [🧠 Funcionalidades previstas (MVP – Fase 1)](#-funcionalidades-previstas-mvp--fase-1)
  - [Funcionalidades futuras (Fase 2+)](#funcionalidades-futuras-fase-2)
  - [🛠️ Stack Tecnológica](#️-stack-tecnológica)
    - [Backend](#backend)
    - [Frontend Web/Desktop](#frontend-webdesktop)
    - [Mobile App (futuro)](#mobile-app-futuro)
    - [DevOps](#devops)
  - [🏗️ Etapas de Arquitetura](#️-etapas-de-arquitetura)
    - [🔹 Fase 1 – Aplicação Local (Offline)](#-fase-1--aplicação-local-offline)
    - [🔹 Fase 2 – Aplicação com Sincronização (Online)](#-fase-2--aplicação-com-sincronização-online)
  - [🗓️ Planejamento Geral](#️-planejamento-geral)
  - [📅 Cronograma por Semanas](#-cronograma-por-semanas)
  - [🚀 Plano de Desenvolvimento - Passo a Passo](#-plano-de-desenvolvimento---passo-a-passo)
    - [0. Definir Escopo e protótipos](#0-definir-escopo-e-protótipos)
    - [1. Configurar Ambiente de Desenvolvimento](#1-configurar-ambiente-de-desenvolvimento)
    - [2. Fase 1 – Aplicativo Local com Electron](#2-fase-1--aplicativo-local-com-electron)
      - [Backend](#backend-1)
      - [Frontend](#frontend)
      - [Extras (fase 1)](#extras-fase-1)
    - [3. Fase 2 – Sincronização com Backend Remoto](#3-fase-2--sincronização-com-backend-remoto)
    - [4. Mobile App (futuro)](#4-mobile-app-futuro)
  - [📄 Licença](#-licença)
---

## 🎯 Objetivos do Projeto

- Desenvolver uma aplicação pessoal de finanças com **Java + Spring Boot (backend)** e **Angular (frontend SPA)**.
- Usar o método de **orçamento por categorias/envelopes** para controle financeiro.
- **Fase 1 – Aplicativo local e offline:**
  - Backend local com SQLite, rodando no próprio computador.
  - Frontend Angular empacotado com **Electron** como app desktop.
  - Funcional sem necessidade de internet, ideal para uso pessoal.
- **Fase 2 – Aplicativo com sincronização remota (opcional):**
  - APIs web para sincronização em nuvem (autenticação, backup e multi-dispositivo).
  - Banco remoto com PostgreSQL em VPS.
  - Integração com futuros apps móveis.
- Usar o projeto como **ferramenta de uso pessoal** e **portfólio profissional**.
- Aplicar conceitos de:
  - Arquitetura limpa e modular no backend.
  - Boas práticas de autenticação e segurança.
  - Deploy em produção com Docker e HTTPS.
  - Desenvolvimento multiplataforma com Angular + Electron + Flutter.

---

## 🧠 Funcionalidades previstas (MVP – Fase 1)

- [ ] Cadastro de contas bancárias manuais.
- [ ] Cadastro de categorias e subcategorias de orçamento.
- [ ] Lançamento de receitas, despesas e transferências.
- [ ] Orçamento mensal por categoria/subcategoria.

## Funcionalidades futuras (Fase 2+)

- [ ] Relatórios simples de gastos por mês e categoria.
- [ ] Interface responsiva e polida com Angular Material.
- [ ] Aplicativo Android (primeira versão com Flutter ou Capacitor).
- [ ] Versão iOS (futuramente).
- [ ] Deploy remoto com Docker, Nginx e HTTPS.
- [ ] Sincronização e backup em nuvem via API REST.

---

## 🛠️ Stack Tecnológica

### Backend
- Java 17+
- Spring Boot
- Spring Data JPA (Hibernate)
- Spring Security com JWT (fase 2)
- SQLite (backend local para uso offline)
- PostgreSQL (backend remoto para sincronização)
- Docker (para deploy futuro)

### Frontend Web/Desktop
- Angular 17+
- Angular Material
- Electron (para empacotar app desktop offline)
- HttpClient para consumir APIs
- Chart.js (ou similar) para gráficos

### Mobile App (futuro)
- Flutter (preferência) ou Angular + Capacitor
- Comunicação com API remota
- Deploy nas lojas (Google Play e App Store)

### DevOps
- Docker + Docker Compose
- Nginx (proxy reverso)
- Let's Encrypt (HTTPS)
- VPS Linux para backend remoto

---

## 🏗️ Etapas de Arquitetura

### 🔹 Fase 1 – Aplicação Local (Offline)

- API local (Spring Boot + SQLite).
- Frontend Angular empacotado com Electron.
- Rodando totalmente no computador do usuário.
- Sem necessidade de internet ou login.
- Foco em funcionalidade mínima e usabilidade.

### 🔹 Fase 2 – Aplicação com Sincronização (Online)

- Backend remoto com PostgreSQL.
- Autenticação com JWT.
- Endpoints para sincronizar dados entre dispositivos.
- Deploy com Docker em VPS (uso web ou mobile).

---

## 🗓️ Planejamento Geral

| Etapa                               | Semanas | Status |
|------------------------------------|---------|--------|
| Planejamento e wireframes          | 1–2     | 🔜     |
| Backend local (API + SQLite)       | 3–4     | 🔜     |
| Frontend Angular (SPA)             | 5–6     | 🔜     |
| Integração Angular + Electron      | 7       | 🔜     |
| Testes e exportação de dados       | 8       | 🔜     |
| Backend remoto (API + PostgreSQL)  | 9       | 🔜     |
| Deploy remoto com Docker + HTTPS   | 10      | 🔜     |
| Testes + Documentação + Portfólio  | 11–12   | 🔜     |
| Aplicativo Android (início)        | 13+     | 🔜     |

> ⚠️ *O cronograma é flexível e poderá ser ajustado conforme evolução e aprendizados.*

---

## 📅 Cronograma por Semanas

| Semana | Tarefas Principais                                                                  |
|--------|--------------------------------------------------------------------------------------|
| 1      | Definir escopo, estudar o YNAB, levantar requisitos e funcionalidades               |
| 2      | Criar wireframes e modelagem inicial do banco (ERD)                                 |
| 3      | Iniciar backend com Spring Boot + SQLite                                            |
| 4      | Implementar CRUD e autenticação básica (usuário fixo admin/admin)                   |
| 5      | Criar frontend Angular e telas iniciais (login, dashboard)                          |
| 6      | Conectar frontend ao backend local                                                  |
| 7      | Empacotar Angular com Electron para app desktop                                     |
| 8      | Implementar exportação/importação de dados locais (JSON)                            |
| 9      | Substituir SQLite por PostgreSQL e configurar backend remoto                        |
| 10     | Deploy remoto com Docker, Nginx, HTTPS e autenticação com JWT                       |
| 11     | Ajustes de usabilidade, testes e refinamento visual                                 |
| 12     | Finalizar documentação, README, e preparar material de portfólio                    |
| 13+    | Começar desenvolvimento do aplicativo mobile com Flutter ou Capacitor               |

---

## 🚀 Plano de Desenvolvimento - Passo a Passo

### 0. Definir Escopo e protótipos
- [x] Definir escopo MVP de requisitos do projeto
- [ ] Criar wireframes do MVP
- [ ] Criar diagrama de banco do MVP
- [ ] Criar diagrama UML do MVP

### 1. Configurar Ambiente de Desenvolvimento
- [ ] Instalar JDK 17+
- [ ] Instalar Node.js + npm
- [ ] Instalar Angular CLI (`npm install -g @angular/cli`)
- [ ] Instalar Electron (`npm install electron --save-dev`)
- [ ] Configurar IDEs para Java e Angular (IntelliJ, VSCode, etc)

---

### 2. Fase 1 – Aplicativo Local com Electron
#### Backend
- [ ] Criar projeto Spring Boot com Web + Data JPA
- [ ] Configurar SQLite para persistência local
- [ ] Criar modelos: User (fixo), Account, Category, Transaction
- [ ] CRUD para contas, categorias, lançamentos
- [ ] API REST testável com Postman

#### Frontend
- [ ] Criar projeto Angular básico
- [ ] Implementar telas: Login (fixo), Dashboard, Contas, Categorias, Lançamentos
- [ ] Consumir API local com HttpClient
- [ ] Empacotar com Electron para uso como app desktop

#### Extras (fase 1)
- [ ] Exportação/Importação de dados (JSON local)

---

### 3. Fase 2 – Sincronização com Backend Remoto
- [ ] Criar versão com PostgreSQL
- [ ] Adicionar autenticação JWT (login real)
- [ ] Criar endpoints de sincronização
- [ ] Dockerizar app backend
- [ ] Configurar Nginx + HTTPS com Let's Encrypt
- [ ] Deploy em VPS Linux

---

### 4. Mobile App (futuro)
- [ ] Criar app com Flutter ou Capacitor
- [ ] Login, dashboard, CRUD básico
- [ ] Comunicação com API remota
- [ ] Publicação nas lojas

---

## 📄 Licença

Este projeto está licenciado sob a **GNU General Public License (GPL) v3.0**.

- O código é aberto para leitura, modificação e uso pessoal ou educacional.
- Qualquer software derivado **deve ser liberado sob a mesma licença GPL**.
- Qualquer distribuição ou modificação do código **deve incluir o código-fonte**.

> Para mais detalhes, veja o arquivo [LICENSE](./LICENSE).
