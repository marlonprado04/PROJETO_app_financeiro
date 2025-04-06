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