# Banco de Dados

---

## Link
https://roadmap.sh/postgresql-dba

---

## Complemento da Lição

### 🎯 Para que serve esse roadmap
Usar como trilha para dominar **PostgreSQL** (visão DBA + prática de dev) e conseguir:
- modelar tabelas e relacionamentos
- escrever SQL com segurança
- otimizar consultas (índices)
- cuidar de backup/restore e desempenho
- conectar o banco com sua API (Spring Boot)

---

### 🧭 Ordem prática de estudo (sequência recomendada)
1) **Fundamentos de SQL**
   - `SELECT`, `WHERE`, `ORDER BY`, `LIMIT`
   - `INSERT`, `UPDATE`, `DELETE`

2) **Modelagem**
   - entidades/tabelas
   - chaves: `PRIMARY KEY`, `FOREIGN KEY`
   - relacionamentos (1–1, 1–N, N–N)

3) **Consultas intermediárias**
   - `JOIN` (INNER/LEFT)
   - agregações: `COUNT`, `SUM`, `AVG`
   - `GROUP BY` + `HAVING`

4) **Integridade e regras**
   - `NOT NULL`, `UNIQUE`, `CHECK`
   - transações: `BEGIN`, `COMMIT`, `ROLLBACK`

5) **Índices e performance**
   - quando criar índice
   - `EXPLAIN` / `EXPLAIN ANALYZE` (entender plano)

6) **Admin básico (DBA do dia a dia)**
   - usuários/roles e permissões
   - backup/restore
   - logs

7) **Integração com Spring Boot**
   - datasource no `application.properties`
   - JPA/Hibernate (mapeamento)
   - migrations (Flyway/Liquibase)

---

### ✅ Checklist “mínimo dev” para usar PostgreSQL no trabalho
- criar banco e tabelas com PK/FK
- fazer `JOIN` e `GROUP BY` sem travar
- entender por que uma consulta está lenta e quando usar índice
- saber fazer backup/restore básico
- conectar no Spring Boot e rodar migrations

---

### 🧩 Mini-projeto prático para fixar
**Banco para API de Loja**
- tabelas: `clientes`, `produtos`, `pedidos`, `itens_pedido`
- relações:
  - cliente 1–N pedidos
  - pedido 1–N itens
  - item N–1 produto
- consultas:
  - total de pedidos por cliente
  - faturamento por mês
  - top 10 produtos mais vendidos

---

### 🔗 Conexão direta com o seu caminho Full-Stack Java
- Java básico → lógica e POO
- Spring Boot → API
- PostgreSQL → persistência real
- Front-end → consumir e exibir

---

<!-- nav_start -->
---
Anterior: [505 SpringBoot](../docs/505_SpringBoot.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
