Exercícios SQL


Link para os exercícios:

https://docs.google.com/document/d/1KBr6QXwDUudAlQoZse9NdCJHiB0Lculq/edit

---

## Opção melhorada

### 📌 Acesso rápido
- **Documento com os exercícios (Google Docs):**  
  https://docs.google.com/document/d/1KBr6QXwDUudAlQoZse9NdCJHiB0Lculq/edit

---

## ✅ Como aproveitar esses exercícios do jeito certo (passo a passo)

### 1) Antes de começar (2 min)
Garanta que você sabe:
- Qual banco está usando (ex.: **MySQL**)
- Como executar um `SELECT` e ver o resultado
- Como criar um banco/tabela (se o material pedir)

### 2) Faça em “camadas” (mais fácil)
Resolva na ordem:
1. **SELECT básico** (FROM, SELECT *)
2. **Filtros** (WHERE: =, >, <, LIKE, IN, BETWEEN, IS NULL)
3. **Ordenação** (ORDER BY)
4. **Agrupamento** (GROUP BY + COUNT/SUM/AVG)
5. **HAVING** (filtro de agregação)
6. **JOIN** (INNER / LEFT)
7. **Subquery** (quando pedirem “acima da média”, “maior que…”, etc.)

---

## 🧠 Dicas práticas para não travar
- **Leia o enunciado e marque palavras-chave**, por exemplo:
  - “apenas” → provavelmente `WHERE`
  - “ordenado por” → `ORDER BY`
  - “quantidade / total” → `COUNT()` / `SUM()`
  - “média” → `AVG()`
  - “por categoria / por cidade” → `GROUP BY`
  - “somente grupos com…” → `HAVING`
  - “traga dados de duas tabelas” → `JOIN`

---

## 🧩 Modelo pronto (use como “esqueleto mental”)
    SELECT colunas
    FROM tabela
    WHERE condicao
    GROUP BY colunas
    HAVING condicao_agregada
    ORDER BY colunas ASC;

---

## ✅ Checklist de validação (pra conferir se sua resposta faz sentido)
- Minha query **traz só o que o enunciado pediu** (nem mais, nem menos)?
- O filtro está no lugar certo?
  - Linha a linha → `WHERE`
  - Resultado de agregação (ex.: AVG/COUNT) → `HAVING`
- Se usei `GROUP BY`, eu só selecionei:
  - colunas agrupadas **ou**
  - funções agregadas (`COUNT`, `AVG`, etc.)
- Se usei `JOIN`, a ligação `ON` faz sentido (chave/relacionamento)?

<!-- nav_start -->
---
Anterior: [141 Resumo SELECT](../docs/141_Resumo_SELECT.md) | Proximo: [143 Agenda Telefonica](../docs/143_Agenda_Telefonica.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
