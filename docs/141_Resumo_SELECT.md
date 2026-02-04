Resumo comando SELECT Banco de Dados


Slides com o resumo dos principais usos do comando SELECT

https://docs.google.com/presentation/d/1F93YdEjUd2INWJ-DU1E9_LeYgz3UPkKi/



Versão Computador:

https://learnsql.com.br/blog/resumo-de-sql-basico/resumo-de-sql-basico-a4.pdf



Versão Celular:

https://learnsql.com.br/blog/resumo-de-sql-basico/resumo-de-sql-basico-mobile.pdf



https://learnsql.com.br/blog/resumo-de-sql-basico/

---

## Opção melhorada

### 📚 Materiais (organizado)
- **Slides (resumo do SELECT):**  
  https://docs.google.com/presentation/d/1F93YdEjUd2INWJ-DU1E9_LeYgz3UPkKi/

- **PDF para computador (A4):**  
  https://learnsql.com.br/blog/resumo-de-sql-basico/resumo-de-sql-basico-a4.pdf

- **PDF para celular (mobile):**  
  https://learnsql.com.br/blog/resumo-de-sql-basico/resumo-de-sql-basico-mobile.pdf

- **Artigo (conteúdo completo + exemplos):**  
  https://learnsql.com.br/blog/resumo-de-sql-basico/

---

## 🧠 Cheat Sheet — Comando SELECT (o essencial)

### ✅ Estrutura base
    SELECT colunas
    FROM tabela
    WHERE condicao
    GROUP BY colunas
    HAVING condicao_agregada
    ORDER BY colunas ASC|DESC;

> Nem todas as cláusulas são obrigatórias. A “espinha dorsal” é: **SELECT + FROM**.

---

## 🔎 Selecionando dados

### Selecionar todas as colunas
    SELECT *
    FROM clientes;

### Selecionar colunas específicas
    SELECT id, nome, email
    FROM clientes;

### Remover duplicados
    SELECT DISTINCT cidade
    FROM clientes;

---

## 🎯 Filtrando resultados (WHERE)

### Operadores mais comuns
- Comparação: `=`, `!=` / `<>`, `>`, `<`, `>=`, `<=`
- Lógicos: `AND`, `OR`, `NOT`
- Faixa: `BETWEEN`
- Lista: `IN`
- Nulos: `IS NULL`, `IS NOT NULL`
- Texto: `LIKE`

### Exemplos práticos
    SELECT nome, salario
    FROM funcionarios
    WHERE salario >= 3000;

    SELECT nome
    FROM clientes
    WHERE cidade IN ('São Paulo', 'Campinas', 'Santos');

    SELECT nome
    FROM produtos
    WHERE nome LIKE 'Café%';

    SELECT nome
    FROM clientes
    WHERE email IS NULL;

---

## 🧾 Ordenação (ORDER BY)

### Crescente (padrão) e decrescente
    SELECT nome, idade
    FROM alunos
    ORDER BY idade ASC;

    SELECT nome, idade
    FROM alunos
    ORDER BY idade DESC;

### Ordenando por mais de uma coluna
    SELECT nome, cidade, idade
    FROM clientes
    ORDER BY cidade ASC, idade DESC;

---

## 📦 Agregação e agrupamento (GROUP BY + funções)

### Funções agregadoras mais usadas
- `COUNT()` → quantidade
- `SUM()` → soma
- `AVG()` → média
- `MIN()` → menor valor
- `MAX()` → maior valor

### Exemplo: média salarial por setor
    SELECT setor, AVG(salario) AS media_salarial
    FROM funcionarios
    GROUP BY setor;

### HAVING (filtro após agrupamento)
> Use **HAVING** quando a condição envolve agregação.

    SELECT setor, AVG(salario) AS media_salarial
    FROM funcionarios
    GROUP BY setor
    HAVING AVG(salario) > 4000;

---

## 🔗 Consultando várias tabelas (JOIN)

### INNER JOIN (somente correspondências)
    SELECT c.nome, p.descricao
    FROM clientes c
    INNER JOIN pedidos p ON p.id_cliente = c.id;

### LEFT JOIN (tudo da esquerda, mesmo sem correspondência)
    SELECT c.nome, p.descricao
    FROM clientes c
    LEFT JOIN pedidos p ON p.id_cliente = c.id;

> Dica prática: **LEFT JOIN** é ótimo pra encontrar “quem não tem relacionamento”.
    SELECT c.nome
    FROM clientes c
    LEFT JOIN pedidos p ON p.id_cliente = c.id
    WHERE p.id IS NULL;

---

## 🧩 Subconsultas (SELECT dentro de SELECT)

### Exemplo: produtos acima da média de preço
    SELECT nome, preco
    FROM produtos
    WHERE preco > (
        SELECT AVG(preco)
        FROM produtos
    );

---

## 🧠 Ordem mental (ajuda a não se perder)
Pense assim (simplificado):
1) FROM / JOIN (de onde vêm os dados)  
2) WHERE (filtra linhas)  
3) GROUP BY (agrupa)  
4) HAVING (filtra grupos)  
5) SELECT (define o que sai)  
6) ORDER BY (ordena)  

---

## ✅ Mini checklist de estudo (rápido e eficiente)
- Montar SELECT simples (colunas + FROM)
- Adicionar WHERE (comparação, AND/OR, IN, BETWEEN, LIKE, NULL)
- ORDER BY (ASC/DESC)
- GROUP BY + agregações (COUNT, AVG, SUM, MIN, MAX)
- HAVING (filtro por agregação)
- JOIN (INNER e LEFT pelo menos)
- Subquery (casos simples)


<!-- nav_start -->
---
Anterior: [InstalaÃ§Ã£o do MySQL Server](../docs/140_Instalacao_MySQL_Server.md) | Próximo: [ExercÃ­cios SQL](../docs/142_Exercicios_SQL.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

