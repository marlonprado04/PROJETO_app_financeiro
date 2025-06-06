# Documento de Requisitos Funcionais — MVP  
**Projeto**: Aplicativo de Gestão Financeira Pessoal (Clone do YNAB)  

---

## 1. Introdução

Este documento tem como objetivo descrever os requisitos funcionais mínimos (MVP) para o desenvolvimento de um aplicativo de controle financeiro pessoal, com foco em usabilidade offline, controle orçamentário mensal e gestão de contas e transações.

---

## 2. Objetivo do Produto

Desenvolver uma aplicação desktop que permita ao usuário:

- Gerenciar contas bancárias e transações;
- Categorizar receitas e despesas;
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
  - Tipo;
  - Conta origem;
  - Destino (para transferência ou identificação / relatórios futuros)
  - Categoria/Subcategoria;
  - Descrição;
  - Status (pendente/finalizado);
- Lançamentos futuros permitidos (agendamento);
- 
- Atualização automática dos saldos de contas e orçamentos ao finalizar transações;
- Validação de consistência em transferências (afetar ambas as contas corretamente).

---

### 4.4. Orçamento Mensal por Categoria

**Descrição**: Acompanhar e controlar gastos mensais por categoria.

**Funcionalidades**:

- Visualização do orçamento por categoria/subcategoria;
- Cálculo de saldo consumido e saldo disponível (total mês);
- Atualizações em tempo real conforme lançamentos são finalizados;
- Alertas visuais para categorias com orçamento excedido;
- Permitir ajuste dos limites orçamentários mensais.

---

### 4.5. Lançamentos Recorrentes

**Descrição**: Permitir o agendamento automático de transações recorrentes (ex: mensalidades, assinaturas, salários), com base em uma frequência definida pelo usuário.

**Funcionalidades**:

- Marcar uma transação como recorrente no momento do cadastro;
- Definição dos seguintes parâmetros de recorrência:
  - Frequência: diária, semanal, quinzenal, mensal;
  - Data da próxima execução;
  - Data final (opcional) para término da recorrência;
- Geração automática de lançamentos com base no agendamento:
  - A nova transação é criada com a mesma estrutura da original, mas com nova data e status pendente;
  - A recorrência atualiza a data da próxima execução automaticamente;
- Edição de recorrência:
  - Permitir pausar, editar ou encerrar recorrências existentes;
- As transações geradas devem:
  - Ser listadas normalmente com as demais transações;
  - Ser associadas à recorrência original (campo de referência);
- Processamento das recorrências:
  - Executado localmente (sem necessidade de rede);
  - Pode ser disparado automaticamente ao iniciar o aplicativo ou manualmente (via botão "Atualizar lançamentos recorrentes").

**Campos adicionais (modelo de dados da transação)**:

- `recorrente` (booleano): indica se é uma transação recorrente;
- `frequencia` (enum): `DIARIA`, `SEMANAL`, `QUINZENAL`, `MENSAL`;
- `proxima_execucao` (data): define a próxima data de geração;
- `fim_recorrencia` (data, opcional): define até quando a transação será repetida;
- `pai_id` (uuid, opcional): identifica a transação-matriz que originou a recorrência.

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

## 9. Considerações Finais

Este documento serve como base para o desenvolvimento e validação do MVP. Mudanças e ajustes poderão ser aplicados conforme a evolução do projeto e os aprendizados obtidos com o uso real da aplicação.

---
