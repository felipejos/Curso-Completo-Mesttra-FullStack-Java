Vídeo: Executando comandos SQL pelo Java


Executando o primeiro select

https://www.youtube.com/watch?v=BVjUG4FFE6g


Executando um insert na tabela

https://youtu.be/u_LoZXSIinY

https://youtu.be/GvOop4GYQWA



Executando um update e delete na tabela

https://youtu.be/GvOop4GYQWA

---

## Opção melhorada

# Executando comandos SQL pelo Java (JDBC) — Guia de estudo

## Objetivo
Aprender o fluxo completo de execução de SQL via Java usando JDBC, passando por:

- **SELECT** (ler dados)
- **INSERT** (criar dados)
- **UPDATE** (alterar dados)
- **DELETE** (remover dados)

---

## Roteiro sugerido (ordem de estudo)

### 1) SELECT — primeira consulta
Link:
- https://www.youtube.com/watch?v=BVjUG4FFE6g

O que focar enquanto assiste:
- Conexão com o banco (`DriverManager.getConnection`)
- Execução da consulta (`PreparedStatement` / `Statement`)
- Leitura do resultado (`ResultSet`)
- Laço `while (rs.next())` para percorrer linhas
- Tipos de leitura: `getInt`, `getString`, `getDouble`, etc.

---

### 2) INSERT — inserindo registros
Links:
- https://youtu.be/u_LoZXSIinY
- https://youtu.be/GvOop4GYQWA

O que focar:
- SQL com parâmetros: `INSERT INTO ... VALUES (?, ?)`
- Substituição dos parâmetros com `setString`, `setInt`, etc.
- Uso de `executeUpdate()` (INSERT/UPDATE/DELETE)
- Como obter ID gerado (`RETURN_GENERATED_KEYS` + `getGeneratedKeys`)

---

### 3) UPDATE e DELETE — alterando e removendo
Link:
- https://youtu.be/GvOop4GYQWA

Observação importante:
- Este link aparece também na parte de INSERT. Ele pode estar cobrindo **mais de uma operação** (INSERT e depois UPDATE/DELETE).

O que focar:
- UPDATE com `WHERE` para não atualizar tudo sem querer
- DELETE com `WHERE` para não apagar tudo sem querer
- Conferir o número de linhas afetadas retornado por `executeUpdate()`

---

## Checklist técnico (o que precisa estar “redondo”)

### JDBC (conceitos que devem ficar claros)
- Diferença entre:
  - `executeQuery()` → usado em **SELECT** (retorna `ResultSet`)
  - `executeUpdate()` → usado em **INSERT/UPDATE/DELETE** (retorna linhas afetadas)
- Por que usar `PreparedStatement`:
  - Evita SQL Injection
  - Facilita parâmetros (`?`)
- Fechamento de recursos:
  - `ResultSet`, `PreparedStatement`, `Connection`
  - Preferir `try-with-resources` para reduzir erros

---

## Exercícios rápidos (para fixar)

1) **SELECT filtrado**  
   Faça um SELECT por `id`:
   - `SELECT * FROM usuario WHERE id = ?`

2) **INSERT com 3 usuários**  
   Insira 3 registros diferentes e depois liste todos.

3) **UPDATE por email**  
   Atualize o nome usando `WHERE email = ?`.

4) **DELETE com confirmação lógica**  
   Antes de deletar, faça um SELECT do ID e só depois execute o DELETE.

5) **Contar registros**  
   Faça:
   - `SELECT COUNT(*) AS total FROM usuario`
   E imprima `total` no console.

<!-- nav_start -->
---
Anterior: [152 Esqueleto 4 Operacoes](../docs/152_Esqueleto_4_Operacoes.md) | Proximo: [154 Reescrevendo App BD](../docs/154_Reescrevendo_App_BD.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
