# Documento de Requisitos Funcionais — MVP  
**Projeto**: Aplicativo de Gestão Financeira Pessoal (Clone do YNAB)  

---

## 1. Introdução

Este documento tem como objetivo descrever os requisitos funcionais mínimos (MVP) para o desenvolvimento de um aplicativo de controle financeiro pessoal, com foco em usabilidade offline, controle orçamentário mensal e gestão de contas e transações.

---

## 2. Objetivo do Produto

Desenvolver uma aplicação desktop que permita ao usuário:

- Gerenciar contas bancárias e transações;
- Categorizar receitas, despesas e transferencias;
- Definir e acompanhar limites orçamentários mensais;
- Operar sem necessidade de conexão com a internet (modo offline).

---

## 3. Escopo do MVP

O MVP contemplará funcionalidades essenciais para permitir ao usuário manter o controle de seu orçamento mensal. Funcionalidades mais avançadas, como relatórios detalhados e aplicativos mobile, serão planejadas em etapas futuras.

---

## 4. Requisitos Funcionais

### 4.1. Cadastro de Contas Bancárias

**Descrição**: Permitir o gerenciamento de contas financeiras.

**Funcionalidades**:

- CRUD completo de contas;
- Campos obrigatórios:
  - Nome;
  - Tipo (corrente, poupança, investimento, dinheiro, crédito);
  - Saldo inicial;
  - Participa do orçamento (booleano);
  - Data de balanço inicial;
- Cálculo automático:
  - **Saldo Atual** com base em transações finalizadas;
  - **Saldo Previsto** com base em todas as transações, incluindo futuras;
- Listagem de contas (card visual): nome, saldos
- Listagem de contas (tabela edição): id, nome, saldos, tipo de conta, se participa do orçamento, data de criação, data de modificação 

---

### 4.2. Cadastro de Categorias e Subcategorias

**Descrição**: Permitir a organização de despesas e receitas por categorias hierárquicas.

**Funcionalidades**:

- CRUD completo de categorias e subcategorias;
- Categorias com:
  - Nome;
  - Descrição;
- Subcategorias associadas a categorias, com:
  - Nome;
  - Descrição;
- Listagem de categorias para seleção em lançamentos.

---

### 4.3. Lançamentos de Transações

**Descrição**: Registrar movimentações financeiras.

**Funcionalidades**:

- CRUD de lançamentos do tipo:
  - Receita (entrada);
  - Despesa (saída);
  - Transferência;
- Campos obrigatórios:
  - Data;
  - Valor;
  - Tipo de operação;
  - Conta origem;
  - Conta destino (caso de transferencia);
  - Destino (para identificação de destinatário / relatórios futuros);
  - Categoria/Subcategoria;
  - Descrição;
  - Status (pendente/finalizado);
  - Tipo de recorrência
  - Frequência
  - Numero de parcelas (caso parcelado)

- Lançamentos futuros permitidos (agendamento);
- Atualização automática dos saldos de contas e orçamentos ao finalizar transações;
- Validação de consistência em transferências (afetar ambas as contas corretamente).



#### 4.3.1 Lançamentos Recorrentes

**Descrição**

Permitir o agendamento automático de transações recorrentes (como mensalidades, assinaturas e pagamentos periódicos), com base em uma frequência definida pelo usuário. O sistema deve permitir também a edição ou exclusão de transações individuais em meio a uma sequência de recorrências, além de possibilitar o cancelamento ou modificação da sequência de lançamentos.

**Funcionalidades**

- Marcar uma transação como recorrente no momento do cadastro, do tipo:
  - **FIXA** (`recurrenceType = FIXED`): repetida indefinidamente com base em uma frequência;
  - **PARCELADA** (`recurrenceType = INSTALLMENT`): repetida por um número definido de parcelas;
  - **SEM RECORRÊNCIA** (`recurrenceType = NONE`): transação única.
- Definição dos seguintes parâmetros:
  - **Frequência** (`recurrenceFrequency`): diária, semanal, quinzenal, mensal, bimestral, trimestral, semestral, anual;
  - **Número de parcelas** (`installmentCount`): obrigatório apenas para transações parceladas.
- Geração automática de lançamentos futuros com base na configuração:
  - Para transações FIXAS: lançamentos gerados até **12 meses à frente** (limite configurável futuramente pelo cliente, permitindo até 5 anos no máximo);
  - Para transações PARCELADAS: todas as parcelas são geradas imediatamente;
  - Lançamentos são criados com:
    - Mesmo conteúdo da transação original (exceto data);
    - `status = false` (pendente);
    - `groupId` compartilhado;
    - `manualOverride = false`.
- Transações recorrentes:
  - São listadas normalmente junto às demais transações;
  - Mantêm vínculo com a transação original via `groupId`;
  - Permitem atualização individual (`manualOverride = true`) ou em massa (por grupo);


##### 4.3.1.1 Controle de Edição de Lançamentos Recorrentes

**Edição com Escopo**

Ao editar uma transação pertencente a uma sequência recorrente, o sistema deve perguntar:

- "Deseja aplicar essa alteração em:"
  - Somente esta ocorrência;
  - Esta e as futuras;

**Comportamento**:

- Se **"somente esta"**: define `manualOverride = true`, impedindo que esta transação seja modificada por edições futuras do grupo.
- Se **"esta e futuras"**:
  - Atualiza os lançamentos futuros (baseando-se na data);
  - Remove o `manualOverride` de todos lançamentos futuros do grupo e atualiza todos.

**Campo `manualOverride`**

- Indica que uma transação foi editada manualmente e não deve ser alterada automaticamente.
- Default: `false`.
- Pode ser revertido manualmente sempre que o usuário editar uma ocorrência do grupo ao escolher "esta e futuras".

**Atualização de recorrências**

- Feita localmente (sem dependência de rede).
- Pode ser executada:
  - Automaticamente ao abrir o app;
  - Manualmente, por botão "Atualizar lançamentos recorrentes".

**Validações**

- Transferências geram duas transações com `transferGroupId` compartilhado;
- Apenas transações com `status = false` podem ser alteradas por agendamentos;
- Transações com `manualOverride = true` são protegidas contra alterações em massa, a menos que o usuário confirme a alterção conjunta.


---

### 4.4. Orçamento Mensal por Categoria

**Descrição**: Acompanhar e controlar gastos mensais por categoria.

**Funcionalidades**:

- Permitir CRUD de limites orçamentários mensais por subcategoria cadastrada;
- Visualização do orçamento por mês e agrupado por categoria/subcategoria;
- Cálculo de saldo consumido e saldo disponível (total mês) baseado em todos gastos previstos (finalizados ou não);
- Atualizações em tempo real conforme lançamentos são lançados no sistema;
- Alertas visuais para categorias com orçamento excedido.

---

## 5. Arquitetura Técnica

### 5.1. Backend

- Framework: Spring Boot  
- Banco de Dados: SQLite  
- API RESTful com endpoints para todas as entidades descritas acima  
- Suporte a operação local e offline

### 5.2. Frontend

- Framework: Angular  
- Empacotamento com Electron para aplicativo desktop  
- Telas previstas:
  - Login;
  - Gerenciamento de contas;
  - Gerenciamento de categorias/subcategorias;
  - Cadastro de lançamentos;
  - Visão do orçamento mensal.

---

## 6. Funcionalidades Extras (fase 1)

- Exportação/importação de dados em JSON;
- Validações básicas de dados e tratamento de erros;
- Testes automatizados (mínimos) para API e frontend.

---

## 7. Requisitos Não Funcionais

- Interface responsiva e amigável;
- Operação offline (sem necessidade de rede);
- Desempenho aceitável para operações CRUD em tempo real;
- Persistência local via SQLite.

---

## 8. Exclusões do MVP

- Relatórios detalhados (gráficos, comparações por período);
- Aplicativo mobile;
- Sincronização em nuvem;
- Múltiplos usuários ou contas compartilhadas.

---

## 9. Especificação da API REST (Endpoints)

Esta seção apresenta os endpoints RESTful que serão implementados na API do sistema, de acordo com os requisitos funcionais descritos neste documento. Todos os endpoints seguem convenções REST e utilizam o formato `application/json` para entrada e saída de dados.

---

### 9.1 Contas (Accounts)

- `GET /accounts`  
  Lista todas as contas do usuário.

- `POST /accounts`  
  Cria uma nova conta.

- `GET /accounts/{id}`  
  Retorna os detalhes de uma conta específica.

- `PUT /accounts/{id}`  
  Atualiza os dados de uma conta existente.

- `DELETE /accounts/{id}`  
  Remove uma conta.

---

### 9.2 Categorias

- `GET /categories`  
  Lista todas as categorias disponíveis.

- `POST /categories`  
  Cria uma nova categoria personalizada.

- `GET /categories/{id}`  
  Retorna os detalhes de uma categoria específica.

- `PUT /categories/{id}`  
  Atualiza uma categoria existente.

- `DELETE /categories/{id}`  
  Remove uma categoria.

---

### 9.3 Transações

- `GET /transactions`  
  Lista todas as transações (com filtros opcionais: data, conta, categoria, etc.).

- `POST /transactions`  
  Cria uma nova transação.

- `GET /transactions/{id}`  
  Retorna os detalhes de uma transação específica.

- `PUT /transactions/{id}`  
  Atualiza uma transação existente.

- `DELETE /transactions/{id}`  
  Remove uma transação.

---

### 9.4 Relatórios

- `GET /reports/monthly-summary`  
  Retorna o resumo mensal de entradas e saídas.

- `GET /reports/balance`  
  Retorna o saldo atual por conta ou total consolidado.

---

**Observações**:
- Os recursos estão organizados por usuário autenticado.
- Campos obrigatórios e estrutura dos JSONs serão definidos na documentação da API detalhada.

---

## 10. Considerações Finais

Este documento serve como base para o desenvolvimento e validação do MVP. Mudanças e ajustes poderão ser aplicados conforme a evolução do projeto e os aprendizados obtidos com o uso real da aplicação.

---

