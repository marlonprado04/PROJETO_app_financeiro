## Modelos de Dados

### Account

- id: Long
- name: String
- type: Enum (CASH, DEBIT, SAVINGS, INVESTMENT, CREDIT)  
- currentBalance: BigDecimal       // Atualizado dinamicamente com base em lançamentos finalizados
- isBudgetIncluded: Boolean        // Se faz parte do orçamento
- balanceDate: LocalDate           // Data do balanço
- createdAt: LocalDateTime
- updatedAt: LocalDateTime

### Category

- id: Long
- name: String
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
- account: FK para Account
- toAccount: ID de Account de destino (no caso de transferencia) // nullable caso não seja
- subcategory: FK para Subcategory // (nullable para transferências)
- payee: String (destinatário)
- description: String
- amount: BigDecimal
- date: LocalDateTime // para manter o horário também, dessa forma facilita ordenação de despesas futuras
- operationType: Enum (INCOME, EXPENSE, TRANSFER)  
- transferGroupId: UUID (nullable) // Identificador compartilhado entre transações de transferência
- recurrenceType: Enum (FIXED, INSTALLMENT, NONE) // Tipo de recorrência do lançamento, pode ser none para evitar nullpointerexception
- recurrenceFrequency: Enum (DAILY, WEEKLY, BIWEEKLY, MONTHLY, BIMONHLY, TRYMONTHLY, SIXMONTHLY, YEARLY) (nullable) // Frequência para recorrência fixa
- installmentCount: Integer (nullable) // Número total de parcelas para recorrência parcelada
- groupId: UUID (nullable) // Identificador compartilhado para agrupar lançamentos gerados a partir da mesma recorrência (ex: todas as parcelas de um parcelado)
- manualOverride: Boolean // default false, serve para quando editar somente uma das parcelas ou lançamentos fixos, impedindo edições futuras de afetarem essa transação
- status: Boolean // Indica se o lançamento foi finalizado
- createdAt: LocalDateTime
- updatedAt: LocalDateTime


### Budget

- id: Long
- subcategory: FK para Subcategory
- month: Integer (1-12)
- year: Integer
- plannedAmount: BigDecimal       // Valor orçado
- actualAmount: BigDecimal        // Calculado dinamicamente dos lançamentos finalizados
- createdAt: LocalDateTime
- updatedAt: LocalDateTime

---

### Notas Técnicas

- Autenticação: Spring Security + JWT
- Criptografia de senha: BCrypt
- Middleware no front-end (Angular) para verificar token e redirecionar para login
- Campo `balance` pode ser calculado ou armazenado com atualização via trigger lógica
- Modelos `Category` e `SubCategory` com relação 1:N (uma categoria tem muitas subcategorias)
- Subcategorias são os nós finais da hierarquia — lançamentos e orçamentos usam apenas elas
- Transferências são controladas pelo `transferGroupId`
- O campo `payee` é string simples, sem FK para outra tabela por enquanto