# Banco de Dados Agenda Telefônica

---

## Descrição Geral do Sistema
O sistema de Agenda Telefônica tem como objetivo armazenar e organizar informações de contato de pessoas, permitindo que uma mesma pessoa possua vários telefones e e-mails. O sistema diferencia o tipo de contato da pessoa, podendo ser profissional ou pessoal.

---

## Entidades (Tabelas) e Atributos (Colunas)

### Pessoa
Representa o contato principal da agenda.

**Atributos:**
- **id_pessoa (PK):** Identificador único da pessoa
- **nome:** Nome completo da pessoa
- **data_nascimento:** Data de nascimento
- **sexo:** Sexo da pessoa
- **tipo_contato:** Indica se o contato é profissional ou pessoal

---

### Telefone
Armazena os números de telefone associados às pessoas.

**Atributos:**
- **id_telefone (PK):** Identificador único do telefone
- **ddd:** Código do DDD
- **telefone:** Número do telefone
- **id_pessoa (FK):** Referência à pessoa proprietária do telefone

---

### Email
Armazena os endereços de e-mail associados às pessoas.

**Atributos:**
- **id_email (PK):** Identificador único do e-mail
- **email:** Endereço de e-mail
- **id_pessoa (FK):** Referência à pessoa proprietária do e-mail

---

## Relacionamentos

### Pessoa — Telefone
**Tipo:** 1 : N (um para muitos)

**Descrição:**
Uma pessoa pode possuir um ou vários telefones, mas cada telefone pertence a uma única pessoa.

---

### Pessoa — Email
**Tipo:** 1 : N (um para muitos)

**Descrição:**
Uma pessoa pode possuir um ou vários e-mails, mas cada e-mail pertence a uma única pessoa.

---

## Diagrama Entidade Relacionamento (DER)
![OnlineGDB - exemplo](../images/diagrama_DER.png)
---

## Script de Criação do Banco de Dados

    -- Criação do banco de dados
    DROP DATABASE IF EXISTS agenda_telefonica;
    CREATE DATABASE agenda_telefonica
      DEFAULT CHARACTER SET utf8mb4
      COLLATE utf8mb4_unicode_ci;

    USE agenda_telefonica;

    -- =========================
    -- Tabela: pessoa
    -- =========================
    CREATE TABLE pessoa (
        id_pessoa INT AUTO_INCREMENT PRIMARY KEY,
        nome VARCHAR(150) NOT NULL,
        data_nascimento DATE,
        sexo ENUM('M', 'F', 'O') NOT NULL,
        tipo_contato ENUM('profissional', 'pessoal') NOT NULL
    );

    -- =========================
    -- Tabela: telefone
    -- =========================
    CREATE TABLE telefone (
        id_telefone INT AUTO_INCREMENT PRIMARY KEY,
        ddd VARCHAR(3) NOT NULL,
        telefone VARCHAR(10) NOT NULL,
        id_pessoa INT NOT NULL,

        CONSTRAINT fk_telefone_pessoa
            FOREIGN KEY (id_pessoa)
            REFERENCES pessoa(id_pessoa)
            ON DELETE CASCADE
            ON UPDATE CASCADE
    );

    -- =========================
    -- Tabela: email
    -- =========================
    CREATE TABLE email (
        id_email INT AUTO_INCREMENT PRIMARY KEY,
        email VARCHAR(150) NOT NULL,
        id_pessoa INT NOT NULL,

        CONSTRAINT fk_email_pessoa
            FOREIGN KEY (id_pessoa)
            REFERENCES pessoa(id_pessoa)
            ON DELETE CASCADE
            ON UPDATE CASCADE
    );

    -- =========================
    -- Inserção de Pessoas
    -- =========================
    INSERT INTO pessoa (nome, data_nascimento, sexo, tipo_contato) VALUES
    ('Ana Silva', '1990-05-12', 'F', 'pessoal'),
    ('Bruno Costa', '1985-08-22', 'M', 'profissional'),
    ('Carla Mendes', '1993-01-10', 'F', 'pessoal'),
    ('Daniel Rocha', '1988-11-03', 'M', 'profissional'),
    ('Eduarda Lima', '1995-07-19', 'F', 'pessoal'),
    ('Felipe Araujo', '1982-04-27', 'M', 'profissional'),
    ('Gabriela Nunes', '1991-09-14', 'F', 'pessoal'),
    ('Henrique Alves', '1987-12-02', 'M', 'profissional'),
    ('Isabela Torres', '1996-06-30', 'F', 'pessoal'),
    ('João Pereira', '1980-03-18', 'M', 'profissional'),
    ('Karen Ribeiro', '1994-10-09', 'F', 'pessoal'),
    ('Lucas Martins', '1989-02-21', 'M', 'profissional'),
    ('Mariana Freitas', '1992-08-05', 'F', 'pessoal'),
    ('Nelson Barros', '1978-01-16', 'M', 'profissional'),
    ('Olivia Pacheco', '1997-11-28', 'F', 'pessoal'),
    ('Paulo Rangel', '1984-09-07', 'M', 'profissional'),
    ('Renata Farias', '1990-12-12', 'F', 'pessoal'),
    ('Sergio Batista', '1986-06-25', 'M', 'profissional'),
    ('Tatiana Lopes', '1993-04-01', 'F', 'pessoal'),
    ('Victor Guedes', '1981-07-08', 'M', 'profissional');

    -- =========================
    -- Inserção de Telefones
    -- =========================
    INSERT INTO telefone (ddd, telefone, id_pessoa) VALUES
    ('11', '988111001', 1),
    ('11', '977221002', 2),
    ('21', '988331003', 3),
    ('21', '977441004', 4),
    ('31', '988551005', 5),
    ('31', '977661006', 6),
    ('41', '988771007', 7),
    ('21', '977946743', 4),
    ('41', '977881008', 8),
    ('51', '988991009', 9),
    ('51', '977001010', 10),
    ('61', '988111011', 11),
    ('61', '977221012', 12),
    ('61', '977221012', 12),
    ('11', '977945543', 1),
    ('71', '988331013', 13),
    ('71', '977441014', 14),
    ('81', '988551015', 15),
    ('81', '977661016', 16),
    ('91', '988771017', 17),
    ('91', '997772019', 17),
    ('11', '977001020', 20);

    -- =========================
    -- Inserção de E-mails
    -- =========================
    INSERT INTO email (email, id_pessoa) VALUES
    ('ana.silva@email.com', 1),
    ('bruno.costa@empresa.com', 2),
    ('carla.mendes@email.com', 3),
    ('daniel.rocha@empresa.com', 4),
    ('eduarda.lima@email.com', 5),
    ('felipe.araujo@empresa.com', 6),
    ('gabriela.nunes@email.com', 7),
    ('henrique.alves@empresa.com', 8),
    ('isabela.torres@email.com', 9),
    ('joao.pereira@empresa.com', 10),
    ('karen.ribeiro@email.com', 11),
    ('lucas.martins@empresa.com', 12),
    ('olivia.pacheco@email.com', 15),
    ('paulo.rangel@empresa.com', 16),
    ('renata.farias@email.com', 17),
    ('sergio.batista@empresa.com', 18),
    ('tatiana.lopes@email.com', 19),
    ('victor.guedes@empresa.com', 20);

---

## Exercícios Básicos – Consultas SQL

### Nível 1 – SELECT Simples
- Liste todas as pessoas cadastradas na agenda.
- Mostre apenas os nomes e tipos de contato das pessoas.
- Liste todas as pessoas cujo tipo de contato seja “profissional”.
- Liste todas as pessoas do sexo feminino.
- Exiba os nomes das pessoas ordenados em ordem alfabética.
- Liste os nomes e datas de nascimento ordenados da pessoa mais velha para a mais nova.

---

### Nível 2 – WHERE, ORDER BY e LIMIT
- Liste as pessoas nascidas após o ano de 1990.
- Exiba os contatos do tipo pessoal, ordenados pelo nome.
- Liste as 5 primeiras pessoas cadastradas na tabela pessoa.
- Liste as pessoas cujo nome comece com a letra “A”.
- Liste as pessoas cujo nome contenha a palavra “Silva”.
- Liste as pessoas do sexo masculino ordenadas pela data de nascimento.

---

### Nível 3 – JOIN (Relacionamentos)
- Liste o nome da pessoa e seu telefone.
- Liste o nome da pessoa e seu e-mail.
- Liste o nome, telefone e e-mail de todas as pessoas.
- Liste apenas os contatos profissionais, exibindo nome e telefone.
- Liste os contatos pessoais, exibindo nome e e-mail.
- Liste os dados completos de uma pessoa específica (nome, telefone e e-mail) informando o ID da pessoa.

---

### Nível 4 – Funções e Agregações
- Conte quantas pessoas existem cadastradas.
- Conte quantos contatos são do tipo profissional.
- Conte quantas pessoas existem por sexo.
- Mostre a pessoa mais velha cadastrada.
- Mostre a pessoa mais nova cadastrada.

---

### Nível 5 – Desafios Iniciais
- Liste as pessoas que não possuem telefone cadastrado.
- Liste as pessoas que não possuem e-mail cadastrado.
- Exiba a quantidade de telefones por pessoa.
- Exiba apenas as pessoas que possuem mais de um telefone.
- Liste os contatos ordenados pelo domínio do e-mail.
- Exiba a idade aproximada das pessoas (considerando o ano atual).
- Liste os contatos profissionais com e-mail corporativo (ex: que contenha @empresa.com).

---

# Opção melhorada

---

## Complementos essenciais para deixar o banco mais consistente (sem mudar sua ideia)

### 1) Restrições de unicidade
Como e-mail e telefone costumam ser únicos (ou pelo menos não deveriam repetir para a mesma pessoa), você pode reforçar com `UNIQUE`:

- Evitar duplicidade exata de e-mails
- Evitar duplicidade do mesmo telefone para a mesma pessoa (DDD + telefone + pessoa)

**Exemplo (adição de constraints):**
    ALTER TABLE email
      ADD CONSTRAINT uq_email UNIQUE (email);

    ALTER TABLE telefone
      ADD CONSTRAINT uq_tel_pessoa UNIQUE (id_pessoa, ddd, telefone);

---

### 2) Padronização de DDD e telefone
Hoje você está usando `VARCHAR(3)` para DDD e `VARCHAR(10)` para telefone, o que é correto para manter zeros e formatação. Como complemento, pode garantir que só tenha números usando `CHECK` (em versões modernas do MySQL).

**Exemplo:**
    ALTER TABLE telefone
      ADD CONSTRAINT chk_ddd_num CHECK (ddd REGEXP '^[0-9]{2,3}$');

    ALTER TABLE telefone
      ADD CONSTRAINT chk_tel_num CHECK (telefone REGEXP '^[0-9]{8,10}$');

---

### 3) Índices para acelerar JOIN e buscas
Como `telefone` e `email` sempre fazem JOIN por `id_pessoa`, índices ajudam bastante.

**Exemplo:**
    CREATE INDEX idx_telefone_id_pessoa ON telefone (id_pessoa);
    CREATE INDEX idx_email_id_pessoa ON email (id_pessoa);

---

## Gabarito prático (consultas-modelo) para cada nível

### Nível 1 – SELECT simples
    -- 1) Todas as pessoas
    SELECT * FROM pessoa;

    -- 2) Nome e tipo de contato
    SELECT nome, tipo_contato FROM pessoa;

    -- 3) Apenas profissionais
    SELECT * FROM pessoa
    WHERE tipo_contato = 'profissional';

    -- 4) Sexo feminino
    SELECT * FROM pessoa
    WHERE sexo = 'F';

    -- 5) Nomes em ordem alfabética
    SELECT nome FROM pessoa
    ORDER BY nome;

    -- 6) Mais velha para mais nova (data mais antiga primeiro)
    SELECT nome, data_nascimento FROM pessoa
    ORDER BY data_nascimento ASC;

---

### Nível 2 – WHERE, ORDER BY e LIMIT
    -- 1) Nascidas após 1990 (>= 1991-01-01)
    SELECT * FROM pessoa
    WHERE data_nascimento >= '1991-01-01';

    -- 2) Pessoal ordenado por nome
    SELECT * FROM pessoa
    WHERE tipo_contato = 'pessoal'
    ORDER BY nome;

    -- 3) 5 primeiras pessoas (pela PK)
    SELECT * FROM pessoa
    ORDER BY id_pessoa
    LIMIT 5;

    -- 4) Nome começa com A
    SELECT * FROM pessoa
    WHERE nome LIKE 'A%';

    -- 5) Nome contém Silva
    SELECT * FROM pessoa
    WHERE nome LIKE '%Silva%';

    -- 6) Sexo masculino por data de nascimento
    SELECT * FROM pessoa
    WHERE sexo = 'M'
    ORDER BY data_nascimento;

---

### Nível 3 – JOIN
    -- 1) Nome e telefone
    SELECT p.nome, t.ddd, t.telefone
    FROM pessoa p
    JOIN telefone t ON t.id_pessoa = p.id_pessoa;

    -- 2) Nome e e-mail
    SELECT p.nome, e.email
    FROM pessoa p
    JOIN email e ON e.id_pessoa = p.id_pessoa;

    -- 3) Nome + telefone + e-mail (gera repetição por combinação)
    SELECT p.nome, t.ddd, t.telefone, e.email
    FROM pessoa p
    LEFT JOIN telefone t ON t.id_pessoa = p.id_pessoa
    LEFT JOIN email e ON e.id_pessoa = p.id_pessoa
    ORDER BY p.id_pessoa;

    -- 4) Profissionais com telefone
    SELECT p.nome, t.ddd, t.telefone
    FROM pessoa p
    JOIN telefone t ON t.id_pessoa = p.id_pessoa
    WHERE p.tipo_contato = 'profissional';

    -- 5) Pessoais com e-mail
    SELECT p.nome, e.email
    FROM pessoa p
    JOIN email e ON e.id_pessoa = p.id_pessoa
    WHERE p.tipo_contato = 'pessoal';

    -- 6) Dados completos por ID (exemplo: id_pessoa = 4)
    SELECT p.nome, t.ddd, t.telefone, e.email
    FROM pessoa p
    LEFT JOIN telefone t ON t.id_pessoa = p.id_pessoa
    LEFT JOIN email e ON e.id_pessoa = p.id_pessoa
    WHERE p.id_pessoa = 4;

---

### Nível 4 – Agregações
    -- 1) Total de pessoas
    SELECT COUNT(*) AS total_pessoas
    FROM pessoa;

    -- 2) Total de profissionais
    SELECT COUNT(*) AS total_profissionais
    FROM pessoa
    WHERE tipo_contato = 'profissional';

    -- 3) Total por sexo
    SELECT sexo, COUNT(*) AS total
    FROM pessoa
    GROUP BY sexo;

    -- 4) Pessoa mais velha (menor data_nascimento)
    SELECT nome, data_nascimento
    FROM pessoa
    WHERE data_nascimento IS NOT NULL
    ORDER BY data_nascimento ASC
    LIMIT 1;

    -- 5) Pessoa mais nova (maior data_nascimento)
    SELECT nome, data_nascimento
    FROM pessoa
    WHERE data_nascimento IS NOT NULL
    ORDER BY data_nascimento DESC
    LIMIT 1;

---

### Nível 5 – Desafios iniciais
    -- 1) Pessoas sem telefone
    SELECT p.*
    FROM pessoa p
    LEFT JOIN telefone t ON t.id_pessoa = p.id_pessoa
    WHERE t.id_telefone IS NULL;

    -- 2) Pessoas sem e-mail
    SELECT p.*
    FROM pessoa p
    LEFT JOIN email e ON e.id_pessoa = p.id_pessoa
    WHERE e.id_email IS NULL;

    -- 3) Quantidade de telefones por pessoa
    SELECT p.id_pessoa, p.nome, COUNT(t.id_telefone) AS qtde_telefones
    FROM pessoa p
    LEFT JOIN telefone t ON t.id_pessoa = p.id_pessoa
    GROUP BY p.id_pessoa, p.nome
    ORDER BY qtde_telefones DESC;

    -- 4) Pessoas com mais de um telefone
    SELECT p.id_pessoa, p.nome, COUNT(t.id_telefone) AS qtde_telefones
    FROM pessoa p
    JOIN telefone t ON t.id_pessoa = p.id_pessoa
    GROUP BY p.id_pessoa, p.nome
    HAVING COUNT(t.id_telefone) > 1;

    -- 5) Contatos ordenados pelo domínio do e-mail
    SELECT p.nome, e.email,
           SUBSTRING_INDEX(e.email, '@', -1) AS dominio
    FROM pessoa p
    JOIN email e ON e.id_pessoa = p.id_pessoa
    ORDER BY dominio, p.nome;

    -- 6) Idade aproximada (em anos)
    SELECT nome,
           TIMESTAMPDIFF(YEAR, data_nascimento, CURDATE()) AS idade_aprox
    FROM pessoa
    WHERE data_nascimento IS NOT NULL
    ORDER BY idade_aprox DESC;

    -- 7) Profissionais com e-mail corporativo
    SELECT p.nome, e.email
    FROM pessoa p
    JOIN email e ON e.id_pessoa = p.id_pessoa
    WHERE p.tipo_contato = 'profissional'
      AND e.email LIKE '%@empresa.com%';

<!-- nav_start -->
---
Anterior: [142 Exercicios SQL](../docs/142_Exercicios_SQL.md) | Proximo: [144 Loja Virtual](../docs/144_Loja_Virtual.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
