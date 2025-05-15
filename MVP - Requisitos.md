# ✅ MVP — Levantamento de Requisitos Funcionais

## Requisitos Funcionais

### 1. 🔐 Cadastro e Login de Usuários (JWT)

- [ ] Usuário pode se cadastrar com email e senha
- [ ] Usuário pode fazer login e receber um token JWT
- [ ] Usuário deve estar autenticado para acessar qualquer recurso do sistema (eventualmente fazer uma versão de teste para uso com armazenamento em variável ou banco de dados em cache, para teste de recrutadores)
- [ ] Logout (invalidação do token no front-end)

__Notas:__

- Spring Security + JWT
- Criptografia de senha (BCrypt)
- Middleware no front (Angular) paara verificar token e redirecionar para login

__Modelo: Usuário__

- id: long
- name: String
- email: String
- password: String (hash via BCrypt)
- createdAt: LocalDateTime
- updatedAt: LocalDateTime

### 2. 🏦 Cadastro de Contas Bancárias Manuais

- [ ] Usuário pode criar, editar e excluir contas bancárias (ex: Carteira, Nubank, Caixa)
- [ ] Cada conta possui: nome, tipo (corrente, poupança / investimento, dinheiro ou crédito) e saldo inicial
- [ ] O saldo da conta é **calculado** automaticamente com base no saldo inicial e nos lançamentos
- [ ] Exibir dois saldos na interface:
  - Saldo Atual: com lançamentos finalizados
  - Saldo Previsto: com todos os lançamentos futuros e não finalizados do mês
- [ ] Nenhum dos saldos é salvo diretamente no banco — são derivados

__Notas__

- Modelo ``Account`` com FK para o ``User``

- Campo ``balance`` pode ser calculado ou armazenado com atualização via trigger lógica

__Model: Account__

- id: Long
- name: String
- type: Enum (CHECKING, SAVINGS, CASH, CREDIT)
- initialBalance: BigDecimal
- user: FK para User
- createdAt: LocalDateTime
- updatedAt: LocalDateTime



### 3. 🧾 Cadastro de Categorias e Subcategorias de Orçamento

- [ ] Usuário pode criar, editar e excluir categorias (ex: Casa, Alimentação, Transporte)
- [ ] Usuário pode criar, editar e excluir subcategorias (ex: Mercado dentro de Casa, delievery dentro de alimentação) 
- [ ] As subcategorias serão utilizadas nos lançamentos e nos orçamentos mensais
- [ ] Cada subcategoria pertence a uma categoria
- [ ] O sistema não permite lançar transações ou orçar diretamente em categorias principais (somente nas subcategorias)
- [ ] Mock de categorias pode ser carregado para novos usuários, mas é totalmente editável



__Notas__ 

- Modelos ``Category`` e ``SubCategory``, com relação 1:N (uma ``Category`` tem muitas ``SubCategory``)
- Subcategorias são os __nós finais__ da hierarquia — os lançamentos e orçamentos usam apenas elas



__Model: Category__

- id: long
- name: String
- user: FK para User
- createdAt: LocalDateTime
- updatedAt: LocalDateTime
- 
__Model: Subcategory__

- id: Long
- name: String
- category: FK para Category
- user: FK para User
- createdAt: LocalDateTime
- updatedAt: LocalDateTime


### 4. 💸 Lançamento de Receitas, Despesas e Transferências

- [ ] Usuário pode criar lançamentos do tipo despesa, receita ou transferência entre contas
- [ ] Cada lançamento tem agrupador (payee), tipo, descrição, valor, data, conta associada, subcategoria (exceto transferencias)
- [ ] Transferências entre conta devem debitar em uma e creditar em outra (sem afetar orçamentos)

__Notas__

- Cada transação é sempre vinculada a uma única conta
- Transferências são controladas pelo transferGroupId
- O campo `payee` (agrupador) é string simples, sem FK para outra tabela por enquanto
- `transferGroupId` serve para vincular os dois lançamentos que formam uma transferência



__Model: Transaction__ 

- id: Long
- user: FK User
- account: FK Account
- subcategory: FK Subcategory
- payee: String
- description: String
- amount: BigDecimal
- date: LocalDate
- type: Enum (INCOME, EXPANSE)
- transferGroupId: UUID
- isPending: boolean
- createdAt: LocalDateTime
- updatedAt: LocalDateTime
