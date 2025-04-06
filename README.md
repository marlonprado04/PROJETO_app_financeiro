# 💰 App Financeiro

API REST para um aplicativo de controle financeiro pessoal, inspirado no app **Organizze**. Desenvolvido com **Spring Boot (Kotlin)**, com foco inicial em arquitetura sólida de backend, segurança, e escalabilidade. O frontend mobile nativo (Jetpack Compose) será implementado em uma fase posterior.

---

## 🧭 Objetivos do Projeto

- Criar uma API REST robusta para controle financeiro pessoal.
- Consolidar conceitos de arquitetura em Spring Boot (DTOs, Services, JWT, versionamento, etc).
- Preparar a base para uma futura integração com aplicativo Android nativo.
- Evoluir por etapas: iniciar com backend, e integrar posteriormente com o frontend mobile.

---

## 📦 Funcionalidades previstas

### 🛠️ Backend (fase atual)

- Autenticação via JWT com refresh token
- Gerenciamento de usuários
- CRUD de contas bancárias e carteiras
- Sistema de categorias e subcategorias
- Registro de transações: entrada, saída, transferência
- Geração de relatórios (por período, categoria, etc)
- Log de eventos para futura sincronização
- API documentada com Swagger/OpenAPI

### 📱 Mobile (fase futura)

- Registro local de dados usando Room
- Sincronização com backend via WorkManager
- Suporte a múltiplos dispositivos
- Operações offline com sincronização posterior
- Notificações (metas, lembretes)

---

## 🧩 Módulos principais

| Módulo                     | Descrição                                                                |
|----------------------------|---------------------------------------------------------------------------|
| **Auth**                   | Login, registro, autenticação JWT                                        |
| **Usuário**                | Dados pessoais, idioma, fuso horário                                      |
| **Contas**                 | Carteiras físicas, contas bancárias e digitais                           |
| **Categorias/Subcategorias** | Organização flexível das transações em hierarquias                       |
| **Transações**             | Entradas, saídas, transferências, agendamentos                           |
| **Relatórios**             | Resumos e análises por período, categoria, tipo                          |
| **Log de Eventos**         | Histórico de ações para sincronização                                    |

---

## ⚙️ Tecnologias e Ferramentas

- **Linguagem Backend**: Kotlin + Spring Boot
- **Banco de Dados**: PostgreSQL
- **ORM**: Spring Data JPA + Hibernate
- **Segurança**: JWT (access + refresh token)
- **Documentação de API**: Swagger / OpenAPI
- **Gerenciamento de build**: Gradle Kotlin DSL
- **IDE recomendada**: IntelliJ IDEA
- **Versionamento**: Git + GitHub
- **Testes**: JUnit 5 + Mockito (planejado)

---

## 🧠 Decisões Arquiteturais

| Área                         | Escolha                          | Justificativa                                      |
|------------------------------|----------------------------------|----------------------------------------------------|
| Banco de dados               | PostgreSQL                       | Suporte a queries complexas e alta integridade     |
| Backend                      | Spring Boot (Kotlin)             | Foco em aprendizado sólido no ecossistema Spring   |
| Autenticação                 | JWT (Stateless)                  | Escalabilidade e controle por dispositivo          |
| Comunicação                  | REST + JSON                      | Integração simples com apps/webs                   |
| Estrutura modular            | Camadas: Controller, Service, Repository, DTO | Padrão de mercado e separação de responsabilidades |
| Sincronização (futuro)       | Event-based + fila local (Room)  | Controle offline e confiável                      |

---

## 📁 Estrutura inicial do backend

```bash
PROJETO_app_financeiro/
├── build.gradle.kts
├── settings.gradle.kts
├── src/
│   ├── main/
│   │   ├── kotlin/com/marlon-prado/financeiro/
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

## Progresso

- [x] Criar estrutura inicial do projeto
- [ ] Módulo de Autenticação (JWT)
- [ ] CRUD de contas
- [ ] CRUD de categorias
- [ ] CRUD de transações
- [ ] Relatórios simples (lista por categoria, data e conta)
- [ ] Logs de eventos
- [ ] Testes automatizados
- [ ] Integração com app mobile (novas tasks)

## Observações finais

> O projeto está sendo construído com foco em aprendizado e boas práticas. Cada etapa será validada com testes e documentação. O objetivo não é apenas funcionar, mas ser escalável, seguro e bem estruturado.

## 📈 Milestones

Abaixo está a lista de principais etapas (milestones) do projeto, com foco em objetivos incrementais e entregas claras.

---

### M0 – Setup Inicial
**Objetivo:** Estruturar o ambiente de desenvolvimento e projetos base.

- [x] Criar repositório Git e README inicial
- [ ] Criar estrutura de pacotes do backend
- [ ] Iniciar projeto Spring Boot com Kotlin
- [ ] Adicionar Swagger/OpenAPI
- [ ] Configurar PostgreSQL (local)
- [ ] Criar projeto Android com Jetpack Compose
- [ ] Integrar Room para persistência local
- [ ] Configurar Gradle Kotlin DSL

---

### M1 – Autenticação e Segurança
**Objetivo:** Implementar login seguro e autenticação por dispositivo.

- [ ] Criar entidades `User` e `Role`
- [ ] Criar endpoints de login e registro com JWT
- [ ] Middleware de autenticação no backend
- [ ] Autenticação por dispositivo
- [ ] Preferências de usuário (idioma, fuso horário)

---

### M2 – Estrutura de Transações
**Objetivo:** Implementar núcleo de entradas, saídas e transferências.

- [ ] CRUD de contas bancárias/carteiras
- [ ] CRUD de categorias e subcategorias
- [ ] CRUD de transações: entrada, saída, transferência
- [ ] Suporte a transações futuras e recorrentes
- [ ] Cálculo automático de saldos

---

###  M3 – Sincronização e Logs
**Objetivo:** Permitir uso offline e sincronização de dados com backend.

- [ ] Estrutura de log de eventos no mobile
- [ ] Endpoint de sincronização de eventos
- [ ] Lógica de merge e resolução de conflitos
- [ ] WorkManager no Android
- [ ] Testes de sincronização offline/online

---

### M4 – Relatórios e Filtros
**Objetivo:** Geração de insights e análises sobre gastos.

- [ ] Filtro por período, categoria, tipo
- [ ] Resumo mensal e anual
- [ ] Exportação de dados (CSV)

---

### M5 – Notificações e Recursos Extras
**Objetivo:** Adicionar funcionalidades extras e alertas úteis.

- [ ] Notificações de metas e limites
- [ ] Alertas de transações futuras e recorrentes
- [ ] Edição em massa de transações
