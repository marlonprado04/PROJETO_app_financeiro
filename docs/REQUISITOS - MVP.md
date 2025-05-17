# ✅ MVP — Levantamento de Requisitos Funcionais

## Introdução

Este documento descreve os requisitos funcionais mínimos (MVP) para um aplicativo financeiro pessoal, incluindo autenticação, cadastro de contas, categorias, lançamentos e regras básicas de negócio.

---

## Requisitos Funcionais (MVP)

## 0. 🔐 Autenticação Básica (MVP inicial)

- [ ] Implementar autenticação via login com senha fixa configurada no backend (sem cadastro de usuário no MVP).
- [ ] Frontend deve possuir tela de login solicitando a senha.
- [ ] Toda requisição para API deve exigir token simples ou header customizado que valida a sessão.
- [ ] Sessão expira após tempo configurável, forçando re-login.
- [ ] Redirecionar para login se não autenticado.

---

## 1. 🏦 Cadastro de Contas Bancárias

- [ ] CRUD completo para contas bancárias (ex: Carteira, Nubank, Caixa).
- [ ] Campos: nome, tipo (corrente, poupança/investimento, dinheiro, crédito), saldo inicial, participação no orçamento (bool), data do balanço inicial.
- [ ] Saldo Atual calculado dinamicamente com lançamentos finalizados.
- [ ] Saldo Previsto considera lançamentos futuros e não finalizados no mês.
- [ ] Exibir tabela com: id, nome, tipo (ENUM), saldo atual, saldo previsto, faz parte do orçamento, data do balanço inicial, data de criação e modificação.
- [ ] Atualização automática dos saldos conforme transações forem finalizadas.

---

## 2. 🧾 Cadastro de Categorias e Subcategorias

- [ ] CRUD para categorias e subcategorias.
- [ ] Categorias possuem nome, descrição e limite orçamentário mensal.
- [ ] Subcategorias vinculadas a categorias.
- [ ] Permitir ativar/desativar categorias e subcategorias.
- [ ] Listagem clara para seleção em lançamentos.

---

## 3. 💵 Lançamentos de Transações

- [ ] CRUD para lançamentos financeiros (receitas, despesas e transferências).
- [ ] Campos: data, valor, tipo (receita, despesa, transferência), conta origem, conta destino (se transferência), categoria/subcategoria, descrição, status (pendente/finalizado).
- [ ] Atualizar saldo das contas e orçamento conforme lançamento finalizado.
- [ ] Possibilidade de lançamento futuro (agendamento).
- [ ] Validação para que transferências atualizem corretamente as duas contas.

---

## 4. 📊 Orçamento Mensal por Categoria/Subcategoria

- [ ] Visualizar orçamento mensal com limites por categoria e subcategoria.
- [ ] Mostrar saldo consumido e saldo disponível.
- [ ] Atualizar automaticamente conforme lançamentos finalizados.
- [ ] Alertas visuais quando categoria ou subcategoria ultrapassar o limite.
- [ ] Opção para ajustar limite mensal por categoria.

---

## 5. 🖥️ Frontend + Backend

- [ ] Backend com Spring Boot + SQLite (local/offline).
- [ ] API REST para todos os endpoints.
- [ ] Frontend Angular com telas para:
  - Login
  - Dashboard resumo (contas e orçamento)
  - Cadastro/edição de contas
  - Cadastro/edição de categorias e subcategorias
  - Cadastro/edição de lançamentos
  - Orçamentos mensais
- [ ] Empacotamento do frontend com Electron para app desktop offline.

---

## Extras (fase 1)

- [ ] Exportação e importação de dados em JSON para backup manual.
- [ ] Testes básicos de API e interface.
- [ ] Validação e tratamento de erros no frontend/backend.

---

# Próximos passos após MVP

- Implementar autenticação real com usuários e JWT (Fase 2).
- Sincronização com backend remoto PostgreSQL.
- Relatórios simples de gastos.
- Interface polida com Angular Material.
- Aplicativo mobile com Flutter.

---

## Modelos de Dados

### User

  - id: Long
  - username: String
  - passwordHash: String (armazenar hash da senha fixa)
  - createdAt: LocalDateTime
  - updatedAt: LocalDateTime

### Account

- id: Long
- name: String
- type: Enum (CHECKING, SAVINGS, CASH, CREDIT)
- initialBalance: BigDecimal
- currentBalance: BigDecimal       // Atualizado dinamicamente com base em lançamentos finalizados
- isBudgetIncluded: Boolean        // Se faz parte do orçamento
- balanceDate: LocalDate           // Data do balanço
- user: FK para User
- createdAt: LocalDateTime
- updatedAt: LocalDateTime

### Category

- id: Long
- name: String
- user: FK para User
- createdAt: LocalDateTime
- updatedAt: LocalDateTime


### Subcategory

- id: Long
- name: String
- category: FK para Category
- createdAt: LocalDateTime
- updatedAt: LocalDateTime


### Transaction

- id: Long
- user: FK para User
- account: FK para Account
- subcategory: FK para Subcategory // (nullable para transferências)
- payee: String (destinatário / favorecido)
- description: String
- amount: BigDecimal
- date: LocalDate
- operation: Enum (INCOME, EXPENSE, TRANSFER)
- transferGroupId: UUID (nullable) // Identificador compartilhado entre transações de transferência
- recurrence: Enum (FIXED, INSTALLMENT, NONE) // Tipo de recorrência do lançamento
- recurrenceFrequency: Enum (WEEKLY, BIWEEKLY, MONTHLY) (nullable) // Frequência para recorrência fixa
- installmentCount: Integer (nullable) // Número total de parcelas para recorrência parcelada
- groupId: UUID (nullable) // Identificador compartilhado para agrupar lançamentos gerados a partir da mesma recorrência (ex: todas as parcelas de um parcelado)
- isCleared: Boolean // Indica se o lançamento foi finalizado
- createdAt: LocalDateTime
- updatedAt: LocalDateTime


### Budget

- id: Long
- user: FK para User
- subcategory: FK para Subcategory
- month: Integer (1-12)
- year: Integer
- plannedAmount: BigDecimal       // Valor orçado
- actualAmount: BigDecimal        // Calculado dinamicamente dos lançamentos finalizados
- createdAt: LocalDateTime
- updatedAt: LocalDateTime

---

## Notas Técnicas

- Autenticação: Spring Security + JWT
- Criptografia de senha: BCrypt
- Middleware no front-end (Angular) para verificar token e redirecionar para login
- Modelo `Account` com FK para `User`
- Campo `balance` pode ser calculado ou armazenado com atualização via trigger lógica
- Modelos `Category` e `SubCategory` com relação 1:N (uma categoria tem muitas subcategorias)
- Subcategorias são os nós finais da hierarquia — lançamentos e orçamentos usam apenas elas
- Transferências são controladas pelo `transferGroupId`
- O campo `payee` é string simples, sem FK para outra tabela por enquanto