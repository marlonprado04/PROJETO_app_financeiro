# 📚 Planejamento e Tarefas – Personal Budget App

## Funcionalidades previstas (MVP – Fase 1)

- [ ] Cadastro de contas bancárias manuais.
- [ ] Cadastro de categorias e subcategorias de orçamento.
- [ ] Lançamento de entradas, saídas e transferências.
- [ ] Orçamento mensal por categoria/subcategoria.

## Funcionalidades futuras (Fase 2+)

- [ ] Relatórios simples de gastos por mês e categoria.
- [ ] Interface responsiva e polida com Angular Material.
- [ ] Aplicativo Android/iOS.
- [ ] Deploy remoto com Docker, Nginx e HTTPS.
- [ ] Sincronização e backup em nuvem via API REST.

---

## Etapas de Arquitetura

### Fase 1 – Aplicação Local (Offline)

- API local (Node.js + Express + TypeScript + SQLite com Prisma).
- Frontend React (com Vite + Tailwind) empacotado com Electron.
- Sem necessidade de internet ou login.

### Fase 2 – Aplicação com Sincronização (Online)

- Backend remoto (Node.js + PostgreSQL).
- Autenticação com JWT.
- Endpoints para sincronizar dados entre dispositivos.

---

## Planejamento Geral

| Etapa                               | Semanas | Status |
|------------------------------------|---------|--------|
| Planejamento e wireframes          | 1–2     | 🔜     |
| Backend local (Node + SQLite via Prisma) | 3–4 | 🔜   |
| Frontend Angular (SPA com Vite + Tailwind) | 5–6 | 🔜 |
| Integração React + Electron        | 7       | 🔜     |
| Testes e exportação de dados       | 8       | 🔜     |
| Backend remoto (API + PostgreSQL)  | 9       | 🔜     |
| Deploy remoto com Docker + HTTPS   | 10      | 🔜     |
| Testes + Documentação + Portfólio  | 11–12   | 🔜     |
| Aplicativo Android (início)        | 13+     | 🔜     |

---

## Plano de Desenvolvimento - Passo a Passo

### 0. Definir Escopo e protótipos (semana 1 e 2)
- [x] Definir escopo MVP de requisitos do projeto
- [x] Criar wireframes do MVP (figma no [link](https://www.figma.com/design/jVGa1laO8WMWhzxlJKT7TF/PROJETO--APP-FINANCEIRO?node-id=0-1&t=qTswms0Jup1cTlM1-1))
- [x] Criar diagrama de banco do MVP (diagrama no [link](https://dbdiagram.io/d/YNAB-Clone-6837b82fc07db17e77a1936b))
- [x] Criar diagrama UML do MVP (diagrama na pasta [./diagrams](./diagrams/class-diagram.puml))

### 1. Configurar Ambiente de Desenvolvimento (semana 3)
- [x] Instalar Node.js + npm
- [ ] Instalar TypeScript (`npm install -g typescript`)
- [ ] Instalar Vite (npm create vite@latest)
- [ ] Instalar Tailwind CSS no projeto React
- [x] Instalar Electron (`npm install electron --save-dev`)
- [ ] Instalar Prisma (`npm install prisma --save-dev && npx prisma init`)
- [ ] Configurar IDEs para Node, React e TypeScript


### 2. Fase 1 – Aplicativo Local com Electron (semana 4, 5, 6, 7 e 8)
#### Backend
- [ ] Criar projeto Node.js com Express e TypeScript  
- [ ] Configurar SQLite via Prisma ORM  
- [ ] Criar modelos: Account, Category, Subcategory, Transaction, Budget  
- [ ] CRUD para contas, categorias, subcategorias, lançamentos, orçamento 
- [ ] API REST testável com Postman

#### Frontend
- [ ] Criar projeto React com Vite + TypeScript + Tailwind CSS  
- [ ] Implementar telas: Dashboard de lançamentos, Dashboard de orçamentos, Contas, Categorias, Subcategorias  
- [ ] Consumir API local com fetch ou axios  
- [ ] Empacotar React com Electron para uso como app desktop  

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

### 4. Mobile App (futuro)
- [ ] Criar app com Flutter ou Capacitor
- [ ] Login, dashboard, CRUD básico
- [ ] Comunicação com API remota
- [ ] Publicação nas lojas
