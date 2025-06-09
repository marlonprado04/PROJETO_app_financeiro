# 💸 YNAB Clone – Clone Simples do YNAB

Aplicativo pessoal de orçamento financeiro inspirado no YNAB (You Need A Budget).

## 🎯 Objetivos

- Desenvolver uma aplicação pessoal de finanças com **Spring Boot**, **SQLite**, **Angular (SPA frontend)** e **Electron**.
- Usar o método de orçamento por **envelopes** para controle financeiro.
- Foco em uso pessoal, offline e multiplataforma.
- Portfólio profissional e aprendizado de boas práticas.

### 🥇 Fase 1 – Aplicativo local e offline
- Backend local com **SQLite** via **Prisma ORM**, rodando no próprio computador.
- Frontend React empacotado com **Electron** como app desktop.
- Funcional sem necessidade de internet, ideal para uso pessoal.

### 🌐 Fase 2 – Aplicativo com sincronização remota (opcional)
- APIs web para sincronização em nuvem (autenticação, backup e multi-dispositivo).
- Banco remoto com **PostgreSQL** em **VPS**.
- Integração com futuros apps móveis.

### 📌 Conceitos aplicados
- Arquitetura limpa e modular no backend.
- Boas práticas de autenticação e segurança.
- Deploy em produção com **Docker** e **HTTPS**.
- Desenvolvimento multiplataforma com **React + Electron + Capacitor/Flutter**.

## 🛠️ Stack Tecnológica

- **Backend:** Node.js, Express, TypeScript, Prisma ORM, SQLite (local), PostgreSQL (remoto), Docker.
- **Frontend:** React + Vite, TypeScript, Tailwind CSS, Electron.
- **Mobile:** Flutter (futuro).
- **DevOps:** Docker.

## 🏗️ Arquitetura

- **Fase 1:** App local (Express + SQLite + React/Electron).
- **Fase 2:** Sincronização remota (PostgreSQL, autenticação JWT, deploy em VPS).

## 📚 Planejamento e Tarefas

Veja o planejamento detalhado, cronograma e tarefas em [docs/PLANEJAMENTO.md](docs/PLANEJAMENTO.md).

## 📄 Licença

Distribuído sob a [GPL v3.0](./LICENSE).