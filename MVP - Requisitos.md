# ✅ MVP — Levantamento de Requisitos Funcionais

## Introdução

Este documento descreve os requisitos funcionais mínimos (MVP) para um aplicativo financeiro pessoal, incluindo autenticação, cadastro de contas, categorias, lançamentos e regras básicas de negócio.

---

## Requisitos Funcionais (MVP)


### 1. 🏦 Cadastro de Contas Bancárias

- [ ] Usuário deve poder criar, editar e excluir (CRUD) contas bancárias (ex: Carteira, Nubank, Caixa)
- [ ] Na criação cada conta deve possuir um nome, tipo (corrente, poupança/investimento, dinheiro ou crédito), saldo, se faz parte ou não do orçamento e data do balanço inicial
- [ ] O saldo da conta (saldo inicial) deve ser calculado dinâmicamente de acordo com transações finalizadas
- [ ] A lista de contas deve exibir dois saldos na interface:
  - Saldo Atual: com lançamentos finalizados
  - Saldo Previsto: com lançamentos futuros e ainda não finalizados no mês
- [ ] O saldo da conta deve ser atualizado dinamicamente no banco de dados conforme transações forem finalizadas
- [ ] O saldo previso deve ser demonstrado com o calculo do saldo atual somado às transações previstas no mês e não finalizadas ainda
- [ ] Conta deve constar em uma tabela com id, nome, tipo (ENUM), saldo, se faz parte do orçamento (bool), data do balanço, data de criação e data de modificação

### 2. 🧾 Cadastro de Categorias e Subcategorias de Orçamento

- [ ] O usuário deve poder criar, editar e excluir (CRUD) categorias (ex: Casa, Alimentação, Transporte)
- [ ] O usuário deve poder criar, editar e excluir (CRUD) subcategorias (ex: Mercado dentro de Casa, delivery dentro de Alimentação)
- [ ] As subcategorias devem ser utilizadas nos lançamentos e nos orçamentos mensais
- [ ] As subcategorias devem pertencem a uma categoria
- [ ] O sistema não deve permitir lançar transações ou orçar diretamente em categorias principais (somente nas subcategorias)
- [ ] O sistema deve ter um mock de categorias padrão ao acessar o sistema que deve ser carregado para novos usuários
- [ ] O mock de categorias e subcategorias do sistema deve ser totalmente editável / removível pelos usuários
- [ ] Cada categoria deve constar em uma tabela com  um id, nome, fk de usuario, data de criação e data de modificação
- [ ] Cada subcategoria deve constar em uma tabela com id, nome, fk de categoria, data de criação e data de modificação

### 3. 💸 Lançamento de Receitas, Despesas e Transferências

- [ ] O usuário deve poder criar, editar e excluir (CRUD) lançamentos 
- [ ] O sistema deve comportar 3 tipos de operação (ENUM) de lançamentos, sendo de, receita ou transferência entre contas
- [ ] Lançamentos ao ser criado devem ter um tipo de operação, valor, data, conta associada e subcategoria 
- [ ] Lançamentos do tipo de operação transferência devem gerar um lançamento clone vinculado por UUID ao original na conta de destino (destinatário)
- [ ] Lançamentos do tipo de operação transferência devem permitir criação sem que seja adicionada uma subcategoria
- [ ] Tabela tem que ter recorrencia (fixo, parcelado ou em branco)
- [ ] Lançamentos com recorrência fixa devem permitir o período semanal, quinzenal e mensal (inicialmente)
- [ ] Lançamentos com recorrência parcelada devem permitir a seleção de parcelas para registro
- [ ] Lançamentos com recorrência devem ser gerados nos respectivos meses de seus orçamentos
- [ ] Cada lançamento deve constar em uma tabela com id, operation, destinatário, descrição, valor, data, conta associada, pk de categoria, recorrencia (ENUM), 


### 4. 📊 Orçamento Mensal por Subcategoria

- [ ] O usuário deve poder definir um valor mensal planejado por subcategoria
- [ ] O sistema deve calcular quanto já foi gasto na subcategoria no mês
- [ ] O sistema deve exibir a diferença entre o valor planejado e o gasto
- [ ] Orçamentos devem poder ser criados, editados e excluídos (CRUD)
- [ ] Cada orçamento deve estar vinculado ao usuário, mês/ano e subcategoria



## Requisitos Futuros


### 1. 🔐 Cadastro e Login de Usuários (JWT)

- [ ] Usuário deve poder se cadastrar usando um nome, email e senha
- [ ] Usuário deve fazer login e receber um token JWT para sua sessão
- [ ] Usuário deve estar autenticado para acessar qualquer recurso do sistema
- [ ] Usuário deve poder realizar logout (invalidar token)
- [ ] Usuário deve ser uma tabela com id, nome, email, senha, data de criação e data de modificação 

### Outros

- Integração automática com bancos via Open Finance
- Dashboard com gráficos e relatórios avançados
- Orçamento mensal por subcategoria
- Notificações e lembretes de vencimento
- Multiusuário e compartilhamento de contas

---

## Modelos de Dados

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
- payee: String                     // Destinatário / favorecido
- description: String
- amount: BigDecimal
- date: LocalDate
- operation: Enum (INCOME, EXPENSE, TRANSFER)
- transferGroupId: UUID (nullable) // Identificador compartilhado entre transações de transferência
- isCleared: Boolean               // Se foi finalizado
- recurrence: Enum (FIXED, INSTALLMENT, NONE)
- recurrenceFrequency: Enum (WEEKLY, BIWEEKLY, MONTHLY) // para FIXED
- installmentCount: Integer (nullable)     // para INSTALLMENT
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