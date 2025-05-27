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

- API local (Spring Boot + SQLite).
- Frontend Angular empacotado com Electron.
- Sem necessidade de internet ou login.

### Fase 2 – Aplicação com Sincronização (Online)

- Backend remoto com PostgreSQL.
- Autenticação com JWT.
- Endpoints para sincronizar dados entre dispositivos.

---

## Planejamento Geral

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

---

## Cronograma por Semanas

| Semana | Tarefas Principais                                                                  |
|--------|--------------------------------------------------------------------------------------|
| 1      | Definir escopo, estudar o YNAB, levantar requisitos e funcionalidades               |
| 2      | Criar wireframes e modelagem inicial do banco (ERD)                                 |
| 3      | Iniciar backend com Spring Boot + SQLite                                            |
| 4      | Implementar CRUD e autenticação básica (usuário fixo admin/admin)                   |
| 5      | Criar frontend Angular e telas iniciais (login, telas)                          |
| 6      | Conectar frontend ao backend local                                                  |
| 7      | Empacotar Angular com Electron para app desktop                                     |
| 8      | Implementar exportação/importação de dados locais (JSON)                            |
| 9      | Substituir SQLite por PostgreSQL e configurar backend remoto                        |
| 10     | Deploy remoto com Docker, Nginx, HTTPS e autenticação com JWT                       |
| 11     | Ajustes de usabilidade, testes e refinamento visual                                 |
| 12     | Finalizar documentação, README, e preparar material de portfólio                    |
| 13+    | Começar desenvolvimento do aplicativo mobile com Flutter ou Capacitor               |

---

## Plano de Desenvolvimento - Passo a Passo

### 0. Definir Escopo e protótipos (semana 1 e 2)
- [x] Definir escopo MVP de requisitos do projeto
- [x] Criar wireframes do MVP (figma no [link](https://www.figma.com/design/jVGa1laO8WMWhzxlJKT7TF/PROJETO--APP-FINANCEIRO?node-id=0-1&t=qTswms0Jup1cTlM1-1))
- [ ] Criar diagrama de banco do MVP
- [ ] Criar diagrama UML do MVP

### 1. Configurar Ambiente de Desenvolvimento (semana 3)
- [ ] Instalar JDK 17+
- [ ] Instalar Node.js + npm
- [ ] Instalar Angular CLI (`npm install -g @angular/cli`)
- [ ] Instalar Electron (`npm install electron --save-dev`)
- [ ] Configurar IDEs para Java e Angular (IntelliJ, VSCode, etc)

### 2. Fase 1 – Aplicativo Local com Electron (semana 4, 5, 6, 7 e 8)
#### Backend
- [ ] Criar projeto Spring Boot com Web + Data JPA
- [ ] Configurar SQLite para persistência local
- [ ] Criar modelos: Account, Category, Transaction
- [ ] CRUD para contas, categorias, lançamentos
- [ ] API REST testável com Postman

#### Frontend
- [ ] Criar projeto Angular básico
- [ ] Implementar telas: Login (fixo), Dashboard, Contas, Categorias, Lançamentos
- [ ] Consumir API local com HttpClient
- [ ] Empacotar com Electron para uso como app desktop

#### Extras (fase 1)
- [ ] Exportação/Importação de dados (JSON local)

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
