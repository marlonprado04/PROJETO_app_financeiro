# 💰 App Financeiro

API REST e frontend web para um aplicativo de controle financeiro pessoal, inspirado no app **Organizze**. Desenvolvido com **Spring Boot (Java)** e **Angular**, com foco inicial em uma arquitetura sólida de backend, segurança e escalabilidade. A interface web será implementada em uma fase posterior.

---

## 🧭 Objetivos do Projeto

- Criar uma API REST robusta para controle financeiro pessoal.
- Consolidar conceitos de arquitetura em Spring Boot (DTOs, Services, JWT, versionamento, etc).
- Desenvolver um frontend web moderno com Angular.
- Evoluir por etapas: iniciar com backend, e integrar posteriormente com o frontend web.

---

## 📦 Funcionalidades Previstas

### 🛠️ Backend (fase atual)

- Autenticação via JWT com refresh token  
- Gerenciamento de usuários  
- CRUD de contas bancárias e carteiras  
- Sistema de categorias e subcategorias  
- Registro de transações: entrada, saída, transferência  
- Geração de relatórios (por período, categoria, etc)  
- Log de eventos para futura sincronização  
- API documentada com Swagger/OpenAPI  

### 🌐 Frontend Web (fase futura)

- Interface responsiva para web (Angular)  
- Visualização e edição de transações  
- Relatórios e filtros dinâmicos  
- Gerenciamento de contas e categorias  
- Autenticação e preferências do usuário  
- Operações offline com cache local (PWA)  
- Notificações (metas, lembretes)  

---

## 🧩 Módulos Principais

| Módulo                    | Descrição                                                                |
|---------------------------|---------------------------------------------------------------------------|
| **Auth**                  | Login, registro, autenticação JWT                                        |
| **Usuário**               | Dados pessoais, idioma, fuso horário                                      |
| **Contas**                | Carteiras físicas, contas bancárias e digitais                           |
| **Categorias/Subcategorias** | Organização flexível das transações em hierarquias                  |
| **Transações**            | Entradas, saídas, transferências, agendamentos                           |
| **Relatórios**            | Resumos e análises por período, categoria, tipo                          |
| **Log de Eventos**        | Histórico de ações para sincronização                                    |

---

## ⚙️ Tecnologias e Ferramentas

- **Linguagem Backend:** Java + Spring Boot  
- **Frontend:** Angular (TypeScript)  
- **Banco de Dados:** PostgreSQL  
- **ORM:** Spring Data JPA + Hibernate  
- **Segurança:** JWT (access + refresh token)  
- **Documentação da API:** Swagger / OpenAPI  
- **Build Backend:** Maven ou Gradle (Java DSL)  
- **Build Frontend:** Angular CLI  
- **IDE recomendadas:** IntelliJ IDEA (backend), VSCode ou WebStorm (frontend)  
- **Versionamento:** Git + GitHub  
- **Testes:** JUnit 5 + Mockito (planejado)  

---

## 🧠 Decisões Arquiteturais

| Área                         | Escolha                          | Justificativa                                      |
|------------------------------|----------------------------------|----------------------------------------------------|
| Banco de dados               | PostgreSQL                       | Suporte a queries complexas e alta integridade     |
| Backend                      | Spring Boot (Java)               | Amplo suporte da comunidade e ecossistema maduro   |
| Autenticação                 | JWT (Stateless)                  | Escalabilidade e controle por dispositivo          |
| Comunicação                  | REST + JSON                      | Integração simples com apps/webs                   |
| Estrutura modular            | Controller, Service, Repository, DTO | Padrão de mercado e separação de responsabilidades |
| Frontend Web (futuro)        | Angular                          | Arquitetura robusta e escalável para SPAs          |
| Sincronização (futuro)       | Event-based + cache local (PWA)  | Controle offline e confiável                       |

---

## 📁 Estrutura Inicial do Backend

```plaintext
PROJETO_app_financeiro/
├── build.gradle / pom.xml
├── settings.gradle
├── src/
│   ├── main/
│   │   ├── java/com/marlonprado/financeiro/
│   │   │   ├── config/         # Configurações (Swagger, Beans, CORS, etc.)
│   │   │   ├── controller/     # Endpoints REST
│   │   │   ├── dto/            # Objetos de transferência de dados
│   │   │   ├── exception/      # Tratamento de exceções customizadas
│   │   │   ├── model/          # Entidades JPA
│   │   │   ├── repository/     # Interfaces JPA
│   │   │   ├── security/       # JWT, filtros e autenticação
│   │   │   └── service/        # Regras de negócio
│   │   └── resources/
│   │       ├── application.yml
│   │       └── static/
└── README.md
```

## ✅ Progresso

- [x] Criar estrutura inicial do projeto
- [ ] Módulo de Autenticação (JWT)
- [ ] CRUD de contas
- [ ] CRUD de categorias
- [ ] CRUD de transações
- [ ] Relatórios simples (por categoria, data e conta)
- [ ] Logs de eventos
- [ ] Testes automatizados
- [ ] Integração com frontend Angular
- [ ] Aplicativo Android (nova etapa)

---

## 💡 Observações Finais

> O projeto está sendo construído com foco em **aprendizado**, **boas práticas** e **escalabilidade**.  
> Todas as etapas serão validadas com testes e documentação.  
> A intenção é entregar não apenas um sistema funcional, mas um sistema limpo, seguro e bem estruturado.

---

## 📈 Milestones

### 🧱 M0 – Setup Inicial

**Objetivo:** Estruturar o ambiente de desenvolvimento e o esqueleto do projeto backend.

- [x] Criar repositório Git e README inicial
- [ ] Inicializar projeto Spring Boot (Java)
- [ ] Configurar PostgreSQL (local)
- [ ] Configurar Swagger/OpenAPI
- [ ] Criar estrutura de pacotes (camadas: controller, service, repository, dto, entity)
- [ ] Configurar versionamento de banco com Flyway
- [ ] Preparar ambiente de desenvolvimento local com Docker

---

### 🔐 M1 – Autenticação e Segurança

**Objetivo:** Implementar login seguro com JWT e controle de acesso por perfis.

- [ ] Criar entidades `User` e `Role`
- [ ] Criar endpoints de login e registro
- [ ] Implementar JWT + filtros de autenticação
- [ ] Middleware para autorização baseada em perfil
- [ ] Implementar auditoria básica (quem criou/alterou)

---

### 💳 M2 – Módulo de Transações

**Objetivo:** Implementar núcleo de controle financeiro.

- [ ] CRUD de contas (bancárias, carteiras etc.)
- [ ] CRUD de categorias e subcategorias
- [ ] CRUD de transações: entrada, saída, transferência
- [ ] Suporte a transações recorrentes e futuras
- [ ] Cálculo automático de saldo por conta
- [ ] Filtragem por data, categoria, tipo e conta

---

### 🔄 M3 – Logs e Sincronização

**Objetivo:** Garantir rastreabilidade de ações e preparar base para futuro app mobile.

- [ ] Estrutura para log de eventos (entidade + serviço)
- [ ] Endpoints para envio e recuperação de logs
- [ ] Estrutura para controle de sincronização (pensando em uso offline no app)
- [ ] Validação de integridade e histórico de alterações

---

### 📊 M4 – Relatórios e Exportações

**Objetivo:** Geração de insights e ferramentas de análise.

- [ ] Relatório de despesas por categoria (mensal/anual)
- [ ] Relatório de saldo por conta
- [ ] Exportação de transações em CSV/Excel
- [ ] Dashboard básico no backend (resumos via endpoints)

---

### 🌐 M5 – Aplicação Web com Angular

**Objetivo:** Interface moderna e responsiva para visualização e gerenciamento de finanças.

- [ ] Setup do projeto Angular
- [ ] Integração com API REST (Spring Boot)
- [ ] Tela de login e registro
- [ ] Tela de dashboard
- [ ] Tela de transações (CRUD)
- [ ] Tela de relatórios
- [ ] Responsividade para uso em mobile

---

### 📱 M6 – Aplicativo Android (versão futura)

**Objetivo:** Criar versão mobile para uso simplificado e sincronizado.

- [ ] Decidir stack mobile (Java, Kotlin, React Native, Flutter...)
- [ ] Login + sincronização com backend
- [ ] Exibir e adicionar transações
- [ ] Acesso offline + sincronização
- [ ] Notificações e lembretes

---