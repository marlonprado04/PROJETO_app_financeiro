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

- [ ] CRUD para lançamentos financeiros (entradas, saídas e transferências).
- [ ] Campos: data, valor, tipo (entrada, saída, transferência), conta origem, conta destino (se transferência), categoria/subcategoria, descrição, status (pendente/finalizado).
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
  - Login (tela inicial)
  - Cadastro/edição de contas (tela de orçamentos ou lançamentos)
  - Cadastro/edição de categorias e subcategorias (tela de orçamentos)
  - Cadastro/edição de lançamentos (tela de lançamentos)
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