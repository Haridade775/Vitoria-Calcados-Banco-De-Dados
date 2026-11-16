# 👟 Vitória Calçados — Modelagem de Banco de Dados Relacional (Entrega 2)

Projeto acadêmico desenvolvido para a disciplina de **Modelagem de Banco de Dados** do curso de **Ciência da Computação (UNICID)**, sob orientação do **Prof. Cid Rodrigues De Andrade**.

O sistema tem como objetivo informatizar e estruturar a gestão comercial, o controle de estoque e a auditoria de vendas da loja varejista **Vitória Calçados**.

---

## 👥 Equipe Responsável

* **Murillo Kauã Belchior Sanches** — Levantamento de Requisitos e Escopo
* **Lucas Brito Alves** — Modelagem Conceitual, Lógica e Normalização
* **Leonel Achu Quispe** — Implementação SQL (DDL, DML) e Regras de Negócio
* **Ronald Hamachi Vargas** — Consultas Gerenciais (DQL), Auditoria e Validação

---

## 🏪 Caracterização do Cenário (Visita Técnica)

* **Ramo de Atividade:** Comércio varejista de calçados.
* **Volume Operacional:** Média de 180 a 220 vendas semanais (250 a 300 pares comercializados).
* **Portfólio e Equipe:** 10 modelos principais em catálogo e equipe de 4 vendedores sob gestão do gerente Gustavo Henrique.

---

## 🎯 Problemas Operacionais Resolvidos (P1 a P4)

| Código | Problema Identificado | Solução no Banco de Dados |
| :--- | :--- | :--- |
| **P1** | **Descontrole de Estoque e Rupturas** | Restrição `CHECK (qtd_estoque >= 0)` em `PRODUTO`, impedindo saldo negativo e viabilizando alerta de reposição (`< 6 pares`). |
| **P2** | **Perda do Histórico de Preços** | Atributo `preco_unitario_praticado` na tabela associativa `ITEM_VENDA`, preservando o valor exato cobrado no momento da compra. |
| **P3** | **Falta de Rastreabilidade de Vendedores** | Chave estrangeira `cod_funcionario` em `VENDA`, permitindo calcular faturamento, volume de vendas e ticket médio por vendedor. |
| **P4** | **Fragilidade na Auditoria de Caixa** | Domínio controlado para `forma_pagamento` (`Dinheiro`, `PIX`, `Cartão de Débito`, `Cartão de Crédito`) e registro automático de `data_hora`. |

---

## 🗂️ Esquema Lógico Relacional (3FN)

O modelo foi normalizado até a **Terceira Forma Normal (3FN)**:

* **`FUNCIONARIO`** (`cod_funcionario` **[PK]**, `nome`, `cpf` **[UNIQUE]**, `telefone`)
* **`PRODUTO`** (`cod_produto` **[PK]**, `nome`, `categoria`, `preco_catalogo`, `qtd_estoque`)
* **`VENDA`** (`cod_venda` **[PK]**, `data_hora`, `valor_total`, `forma_pagamento`, `cod_funcionario` **[FK]**)
* **`ITEM_VENDA`** (`cod_venda` **[PK, FK]**, `cod_produto` **[PK, FK]**, `quantidade`, `preco_unitario_praticado`)

---

## 🛠️ Tecnologias Utilizadas

* **SGBD:** MySQL 8.0+ (Codificação `utf8mb4`)
* **Linguagem:** SQL (DDL, DML e DQL)
* **Versionamento:** Git & GitHub

---

## 🚀 Como Executar o Projeto

1. Clone este repositório ou baixe o script `.sql`.
2. Abra o **MySQL Workbench** (ou outro cliente MySQL compatível).
3. Execute o script completo para criar o banco `vitoria_calcados`, gerar as tabelas com suas restrições de integridade e popular a base com os dados de teste.
4. Rode as consultas gerenciais (`G01` a `G04`) e de auditoria (`A01`) para visualizar os relatórios.

---

## 📸 Evidência da Visita Técnica

Registro fotográfico realizado durante a visita técnica na **Vitória Calçados**:

![Visita Técnica - Vitória Calçados](./visita-tecnica.jpeg)