# 📱 Especificação de Telas e Menus da Aplicação Financeira (MVP)

Esta sessão visa descrever as telas, menus e campos do MVP baseado nos requisitos previamente levantados.

---

## 🧭 Menu Principal (Sidebar ou Topbar)

- **Dashboard**
- **Contas Bancárias**
- **Categorias**
- **Lançamentos**
- **Orçamento Mensal**
- **Exportar/Importar**
- **Sair**

---

---

## 🏦 Lista de Contas Bancárias (menu lateral)

**Tabelas agrupadoras em lista (orçar ou não orçar):**
- Nome
- Saldo Atual
- Saldo Previsto (mês atual)

**Ações:**
- Botão “Nova Conta”
- Clique com botão direito em conta existente abre menu suspenso para edição

**Formulário de Conta ao cadastar / editar:**
- Nome (input)
- Tipo (select: Corrente, Poupança, Investimento, Dinheiro, Crédito)
- Saldo do balanço (decimal)
- Data do Balanço (data)
- Participa do orçamento? (checkbox)
- Botão de Excluir ou Salvar


---

## 🧾 Tela de Orçamento (Categorias e Subcategorias)

**Lista agrupada por categoria e subcategoria:**
- Categoria
- Subgategoria
- Barra superior para navegar entre meses e anos
- Coluna de "Orçado", "Realizado" e "Diferença" para cada Categoria e Subcategoria agrupada e cada mês selecionado

**Ações:**
- Botão “Nova Categoria” (na lista acima das categorias)
- Botão "Nova Subcategoria" (abaixo de cada categoria)
- Clique com botão direito em categoria e subcategoria existente abre menu suspenso para edição
- Clicar no campo de orçamento permite editar ou apagar o campo

**Formulário de Categoria/Subcategoria:**
- Nome (input)
- Botão de Excluir ou Salvar

**Formulário de Categoria/Subcategoria:**
- Campo do valor orçado (decimal)

---

## 💵 Tela de Lançamentos (FINALIZAR DEPOIS DAQUI PRA BAIXO)

**Tabela com colunas:**
- Botão de seleção (para edição em massa)
- Data
- Valor
- Tipo
- Conta Origem
- Conta Destino (se transferência)
- Categoria/Subcategoria
- Descrição
- Status (Pendente/Finalizado)
- Ações

**Ações:**
- Botão “Novo Lançamento”
- Filtro por período, tipo, status, conta

**Formulário de Lançamento:**
- Data (input data)
- Valor (input decimal)
- Tipo (select: Entrada, Saída, Transferência)
- Conta Origem (select)
- Conta Destino (select, se tipo = transferência)
- Categoria (select)
- Subcategoria (select)
- Descrição (textarea)
- Status (radio: Pendente/Finalizado)
- Recorrência (select: Nenhuma, Fixa, Parcelada)
- Frequência (se fixa: semanal, quinzenal, mensal)
- Parcelas (se parcelada: número de parcelas)

---

## 📊 Tela de Orçamento Mensal

**Componentes:**
- Filtro por mês/ano
- Lista de categorias com:
  - Limite
  - Valor gasto (bar progressiva)
  - Disponível
  - Alerta se excedido

**Ações:**
- Botão "Editar Limite" por categoria/subcategoria

---

## 🔄 Tela de Exportação / Importação

**Componentes:**
- Botão "Exportar JSON"
- Botão "Importar JSON"
- Input para upload de arquivo

---

## ⚠️ Tela de Erro / Não Autorizado

**Componentes:**
- Mensagem de erro (ex: sessão expirada)

---

## 🧪 Telas Técnicas (Debug ou Ocultas no MVP)

- Tela de Logs / Testes (opcional)
- Tela de Backup Automático (futuro)

---

## 🧹 Layout e Design

- Framework: Angular + Angular Material
- Design responsivo
- Preferência por layout com sidebar
- Cores: tons sóbrios com destaque para alertas

---

## 🗂️ Organização de Rotas (Angular)

- `/dashboard`
- `/contas`
- `/categorias`
- `/lancamentos`
- `/orcamento`
- `/exportar`
- `/erro`

---
