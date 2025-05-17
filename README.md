# 💸 Personal Budget App – Clone Simples do YNAB

Aplicativo pessoal de orçamento financeiro inspirado no YNAB (You Need A Budget).

## 🎯 Objetivos

- Desenvolver uma aplicação pessoal de finanças com **Java + Spring Boot (backend)** e **Angular (frontend SPA)**.
- Usar o método de orçamento por __envelopes__ para controle financeiro.
- Foco em uso pessoal, offline e multiplataforma.
- Portfólio profissional e aprendizado de boas práticas.
- Fase 1 – Aplicativo local e offline:
  - Backend local com SQLite, rodando no próprio computador.
  - Frontend Angular empacotado com Electron como app desktop.
  - Funcional sem necessidade de internet, ideal para uso pessoal.
- Fase 2 – Aplicativo com sincronização remota (opcional):
  - APIs web para sincronização em nuvem (autenticação, backup e multi-dispositivo).
  - Banco remoto com PostgreSQL em VPS.
  - Integração com futuros apps móveis.
- Aplicar conceitos de:
  - Arquitetura limpa e modular no backend.
  - Boas práticas de autenticação e segurança.
  - Deploy em produção com Docker e HTTPS.
  - Desenvolvimento multiplataforma com Angular + Electron + Flutter.


## 🛠️ Stack Tecnológica

- **Backend:** Java 17+, Spring Boot, SQLite (local), PostgreSQL (remoto), Docker.
- **Frontend:** Angular 17+, Angular Material, Electron.
- **Mobile:** Flutter (futuro).
- **DevOps:** Docker, Nginx, Let's Encrypt.

## 🏗️ Arquitetura

- **Fase 1:** App local (Spring Boot + SQLite + Angular/Electron).
- **Fase 2:** Sincronização remota (PostgreSQL, autenticação JWT, deploy em VPS).

## 📚 Planejamento e Tarefas

Veja o planejamento detalhado, cronograma e tarefas em [docs/PLANEJAMENTO.md](docs/PLANEJAMENTO.md).

## 📄 Licença

Distribuído sob a [GPL v3.0](./LICENSE).