Esqueleto básico das 4 Operações
Executar o script abaixo no banco de dados MySQL para criar a tabela usuário;
-- Cria o banco de dados
CREATE DATABASE IF NOT EXISTS teste_db;

-- Seleciona o banco
USE teste_db;

-- Cria a tabela usuario
CREATE TABLE IF NOT EXISTS usuario (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(150) NOT NULL,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Copiar esta versão da aplicação JAVA para o VsCode e testar a sua execução.
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class App {

    public static void main(String[] args) {

        //string    Conexao com o banco
        //mysql     Definicação do SGBD utilizado
        //localhost O endereço do Servidor onde o banco de dados está hospedado
        //3306      A porta tcp do banco de dados
        //teste_db  Nome do banco de dados
        final String STR_CONNECTION = "jdbc:mysql://localhost:3306/teste_db";
        
        //Usuario para conectar no banco de dados
        final String USER = "root";

        //Senha para conectar no banco de dados
        final String PASSWORD = "12345678";

        //Variavel para armazenar a conexao estabelecida com o banco de dados
        Connection conn = null;

        //Comandos preparados para evitar SQL Injection
        PreparedStatement psInsert = null;
        PreparedStatement psSelect = null;
        PreparedStatement psUpdate = null;
        PreparedStatement psDelete = null;

        //Variavel para armazenar as respostas do banco de dados
        ResultSet rs = null;

        //Variavel para armazenar o id gerado no bando de dados
        int idGerado = 0;

        try {

            String nome = "Pedro Paulo";
            String email = "pedro@email.com";

            //Cria a conexão com o banco de dados e armazena em conn
            conn = DriverManager.getConnection(STR_CONNECTION, USER, PASSWORD);
            System.out.println("Conexão ao banco de dados realizada com sucesso!");

            // 1. INSERT 
            String insertSql = "INSERT INTO usuario (nome, email) VALUES (?, ?)";

            // Montar a consulta preparada para evitar SQL Injection
            // Statement.RETURN_GENERATED_KEYS para que diz para o banco de dados devolver o id gerado na inserção (chave primária)
            psInsert = conn.prepareStatement(insertSql, Statement.RETURN_GENERATED_KEYS);

            //Substitui o primeiro ? por pedro
            psInsert.setString(1, nome);
            //Substitui o segundo ? por pedro@email.com
            psInsert.setString(2, email);

            //Envia o SQL gerado para o banco de dados realizar o insert
            psInsert.executeUpdate();

            //Obter o id gerado como chave primaria na tabela de usuario
            rs = psInsert.getGeneratedKeys();

            //Verifica se existe um id e armazena na variavel
            if (rs.next()) 
                idGerado = rs.getInt(1);
            
            System.out.println("INSERT realizado com sucesso!");
            System.out.println("O(a) " + nome + " foi inserido no banco com ID: " + idGerado);

            // 2. SELECT
            String selectSql = "SELECT * FROM usuario";

            //Executa a consulta no banco de dados
            psSelect = conn.prepareStatement(selectSql);
            
            //Guarda em rs o resultado da consulta realizado no banco de dados (linhas e colunas)
            rs = psSelect.executeQuery();

            System.out.println("Resultado da consulta:");
            
            //Existe alguma linha que foi retornada do banco de dados
            while (rs.next()) {
                //rs.getInt("id") obtem a coluna id que tem valor inteiro retornada do banco de dados
                //rs.getString("nome") obtem a coluna nome que tem valor string retornada do banco de dados
                System.out.println(
                        "ID: " + rs.getInt("id") +
                        ", Nome: " + rs.getString("nome") +
                        ", Email: " + rs.getString("email") +
                        ", Data Cadastro: " + rs.getString("data_criacao")
                );
            }

            // 3. UPDATE usando ID
            String novoEmail = "pedrof@email.com";
            String updateSql = "UPDATE usuario SET email = ? WHERE id = ?";

            //Prepara o SQL para receber as substiticoes evitando sql injection
            psUpdate = conn.prepareStatement(updateSql);

            //Realiza as substituicoes das ? pelo valor correto
            psUpdate.setString(1, novoEmail);
            psUpdate.setInt(2, idGerado);

            //Executa o update no banco de dados
            psUpdate.executeUpdate();

            System.out.println("UPDATE realizado!");

            // 4. DELETE usando ID
            String deleteSql = "DELETE FROM usuario WHERE id = ?";

            //Prepara o SQL para receber as substituicoes evitando sql injection
            psDelete = conn.prepareStatement(deleteSql);

            //Faz a substituicacao da ? pelo idGerado
            psDelete.setInt(1, idGerado);

            //Executa a operação de delete no banco de dados
            psDelete.executeUpdate();

            System.out.println("DELETE realizado!");

        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            //encerrar as conexões criadas e demais recursos
            try {
                if (rs != null) rs.close();
                if (psInsert != null) psInsert.close();
                if (psSelect != null) psSelect.close();
                if (psUpdate != null) psUpdate.close();
                if (psDelete != null) psDelete.close();
                if (conn != null) conn.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
---

## Opção melhorada

# CRUD básico (MySQL + Java JDBC) — Esqueleto + Complementos

## 1) Script SQL (criar banco e tabela)

> Dica: rode no MySQL Workbench / DBeaver / terminal `mysql`.

    -- Cria o banco de dados
    CREATE DATABASE IF NOT EXISTS teste_db;

    -- Seleciona o banco
    USE teste_db;

    -- Cria a tabela usuario
    CREATE TABLE IF NOT EXISTS usuario (
        id INT AUTO_INCREMENT PRIMARY KEY,
        nome VARCHAR(100) NOT NULL,
        email VARCHAR(150) NOT NULL,
        data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    );

---

## 2) Como rodar no VS Code (passo a passo)

### 2.1) Pré-requisitos
- JDK instalado (recomendado: 17+)
- Extensão **Extension Pack for Java** no VS Code
- MySQL Server rodando localmente (porta `3306`)

### 2.2) Adicionar o driver JDBC do MySQL
Você precisa do **MySQL Connector/J** (arquivo `.jar`).

Estrutura recomendada do projeto:

    seu-projeto/
    ├─ lib/
    │  └─ mysql-connector-j-8.x.x.jar
    └─ src/
       └─ App.java

No VS Code:
- Crie a pasta `lib/`
- Coloque o `.jar` lá dentro
- Pressione `Ctrl+Shift+P` → **Java: Configure Classpath**
- Adicione o `.jar` da pasta `lib`

### 2.3) Ajustar string de conexão
Se seu MySQL exigir timezone/SSL, use uma string mais “completa”:

    final String STR_CONNECTION =
        "jdbc:mysql://localhost:3306/teste_db?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true";

---

## 3) Melhorias práticas no código (sem mudar a ideia do esqueleto)

### 3.1) Fechamento automático com try-with-resources
Evita esquecer `.close()` e reduz código no `finally`.

### 3.2) Separar prints e usar format
Melhora leitura do console.

### 3.3) Validação de conexão e mensagens claras
Facilita debug quando o banco não conecta.

---

## 4) Versão com pequenas melhorias (mesma lógica do seu código)

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.PreparedStatement;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    public class App {

        public static void main(String[] args) {

            final String STR_CONNECTION =
                "jdbc:mysql://localhost:3306/teste_db?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true";

            final String USER = "root";
            final String PASSWORD = "12345678";

            String nome = "Pedro Paulo";
            String email = "pedro@email.com";

            String insertSql = "INSERT INTO usuario (nome, email) VALUES (?, ?)";
            String selectSql = "SELECT * FROM usuario";
            String updateSql = "UPDATE usuario SET email = ? WHERE id = ?";
            String deleteSql = "DELETE FROM usuario WHERE id = ?";

            int idGerado = 0;

            try (Connection conn = DriverManager.getConnection(STR_CONNECTION, USER, PASSWORD)) {

                System.out.println("Conexão ao banco de dados realizada com sucesso!");

                // 1) INSERT
                try (PreparedStatement psInsert =
                        conn.prepareStatement(insertSql, Statement.RETURN_GENERATED_KEYS)) {

                    psInsert.setString(1, nome);
                    psInsert.setString(2, email);
                    psInsert.executeUpdate();

                    try (ResultSet rsKeys = psInsert.getGeneratedKeys()) {
                        if (rsKeys.next()) {
                            idGerado = rsKeys.getInt(1);
                        }
                    }
                }

                System.out.println("INSERT realizado com sucesso!");
                System.out.println("Usuário inserido: " + nome + " | ID: " + idGerado);

                // 2) SELECT
                System.out.println("\nResultado da consulta:");
                try (PreparedStatement psSelect = conn.prepareStatement(selectSql);
                     ResultSet rs = psSelect.executeQuery()) {

                    while (rs.next()) {
                        System.out.printf(
                            "ID: %d, Nome: %s, Email: %s, Data Cadastro: %s%n",
                            rs.getInt("id"),
                            rs.getString("nome"),
                            rs.getString("email"),
                            rs.getString("data_criacao")
                        );
                    }
                }

                // 3) UPDATE
                String novoEmail = "pedrof@email.com";
                try (PreparedStatement psUpdate = conn.prepareStatement(updateSql)) {
                    psUpdate.setString(1, novoEmail);
                    psUpdate.setInt(2, idGerado);
                    psUpdate.executeUpdate();
                }

                System.out.println("\nUPDATE realizado! Email atualizado para: " + novoEmail);

                // 4) DELETE
                try (PreparedStatement psDelete = conn.prepareStatement(deleteSql)) {
                    psDelete.setInt(1, idGerado);
                    psDelete.executeUpdate();
                }

                System.out.println("DELETE realizado! ID removido: " + idGerado);

            } catch (SQLException e) {
                System.out.println("Erro SQL: " + e.getMessage());
                e.printStackTrace();
            }
        }
    }

---

## Exercícios (para praticar com este CRUD)

1) Altere o `SELECT * FROM usuario` para listar **apenas** `id` e `nome`, ordenando por `id` desc.
2) Faça um `SELECT` com `WHERE email = ?` recebendo o email por variável.
3) No `UPDATE`, também altere o `nome` além do email.
4) No `DELETE`, peça o ID para o usuário via `Scanner` e apague o registro digitado.
<!-- nav_start -->
---
Anterior: [Criando o seu prÃ³prio pacote](../docs/151_Criando_Pacote.md) | Próximo: [VÃ­deo: Executando comandos SQL pelo Java](../docs/153_Video_SQL_no_Java.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

