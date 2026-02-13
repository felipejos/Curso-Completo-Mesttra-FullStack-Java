# Desafio: Refatorar para MVC (Console + MySQL)

---

## Enunciado (conteúdo preservado)

Desafio  
Com base nestes arquivos divida o codigo utilizando o padrão MVC.

---

## Arquivos fornecidos

### arquivo: app\App.java

    package app;

    import dao.PessoaDAO;
    import model.Pessoa;
    import model.Telefone;

    import java.util.List;
    import java.util.Scanner;

    public class App {

        private static Scanner teclado = new Scanner(System.in);
        private static PessoaDAO pessoaDAO = new PessoaDAO();

        public static void main(String[] args) throws Exception {
            int opcao;
            do {
                opcao = menu();
                switch (opcao) {
                    case 1 -> incluirContato();
                    case 2 -> listarContatos();
                    case 3 -> excluirContato();
                    case 4 -> alterarContato();
                    case 5 -> System.out.println("Saindo...");
                }
            } while (opcao != 5);
        }

        private static int menu() {
            System.out.println("============= MENU =============\n");
            System.out.println("1 - Incluir");
            System.out.println("2 - Listar");
            System.out.println("3 - Excluir");
            System.out.println("4 - Alterar");
            System.out.println("5 - Sair");

            System.out.print("\nDigite a opção: ");
            
            int opcao = teclado.nextInt();
            teclado.nextLine(); // consumir a quebra de linha

            return opcao;
        }

        private static void incluirContato() throws Exception {

            System.out.print("Nome: ");
            String nome = teclado.nextLine();

            System.out.print("Email: ");
            String email = teclado.nextLine();

            Pessoa pessoa = new Pessoa(nome, email);

            while (true) {
                System.out.print("Adicionar telefone [s/n]? ");
                if (!teclado.nextLine().equalsIgnoreCase("s"))
                    break;

                System.out.print("DDD: ");
                String ddd = teclado.nextLine();

                System.out.print("Numero: ");
                String numero = teclado.nextLine();

                pessoa.getTelefones().add(new Telefone(ddd, numero));
            }

            pessoaDAO.salvar(pessoa);
        }

        private static void listarContatos() throws Exception {

            List lista = pessoaDAO.listar();

            for (Pessoa p : lista) {
                System.out.println(p);

                for (Telefone t : p.getTelefones())
                    System.out.println("   " + t);
            }
        }

        private static void excluirContato() throws Exception {

            System.out.print("ID: ");
            int id = Integer.parseInt(teclado.nextLine());
        }

        private static void alterarContato() throws Exception {

            System.out.print("ID: ");
            int id = Integer.parseInt(teclado.nextLine());

            Pessoa p = pessoaDAO.buscarPorId(id);

            if (p == null) {
                System.out.println("Não encontrado");
                return;
            }

            System.out.print("Novo nome: ");
            p.setNome(teclado.nextLine());

            System.out.print("Novo email: ");
            p.setEmail(teclado.nextLine());

            pessoaDAO.atualizar(p);
        }
    }

---

### arquivo: dao\PessoaDAO.java

    package dao;

    import model.Pessoa;
    import model.Telefone;

    import java.sql.Connection;
    import java.sql.PreparedStatement;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;
    import java.util.ArrayList;
    import java.util.List;

    import db.ConnectionFactory;

    public class PessoaDAO {

        private TelefoneDAO telefoneDAO = new TelefoneDAO();

        public void salvar(Pessoa pessoa) throws Exception {

            String sql = "INSERT INTO pessoa(nome,email) VALUES(?,?)";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS)) {

                ps.setString(1, pessoa.getNome());
                ps.setString(2, pessoa.getEmail());

                ps.executeUpdate();

                ResultSet rs = ps.getGeneratedKeys();
                if (rs.next())
                    pessoa.setId(rs.getInt(1));

                for (Telefone t : pessoa.getTelefones()) {
                    t.setPessoaId(pessoa.getId());
                    telefoneDAO.salvar(t);
                }
            } catch (SQLException e) {
                                    System.out.println("Erro ao salvar pessoas: " + e.getMessage());
                      }
        }

        public List listar() throws Exception {

            List lista = new ArrayList<>();

            String sql = "SELECT * FROM pessoa";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql);
                 ResultSet rs = ps.executeQuery()) {

                while (rs.next()) {

                    Pessoa p = new Pessoa();
                    p.setId(rs.getInt("id"));
                    p.setNome(rs.getString("nome"));
                    p.setEmail(rs.getString("email"));

                    List tels = telefoneDAO.listarPorPessoa(p.getId());
                    p.getTelefones().addAll(tels);

                    lista.add(p);
                }
            } catch (SQLException e) {
                                    System.out.println("Erro ao listar pessoas: " + e.getMessage());
                      }

            return lista;
        }

        public void atualizar(Pessoa pessoa) throws Exception {

            String sql = "UPDATE pessoa SET nome=?, email=? WHERE id=?";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql)) {

                ps.setString(1, pessoa.getNome());
                ps.setString(2, pessoa.getEmail());
                ps.setInt(3, pessoa.getId());

                ps.executeUpdate();
            } catch (SQLException e) {
                                    System.out.println("Erro ao atualizar pessoas: " + e.getMessage());
                      }
        }

        public void excluir(int id) throws Exception {

            String sql = "DELETE FROM pessoa WHERE id=?";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql)) {

                ps.setInt(1, id);
                ps.executeUpdate();
            } catch (SQLException e) {
                                    System.out.println("Erro ao excluir pessoas: " + e.getMessage());
                      }
        }

        public Pessoa buscarPorId(int id) throws Exception {

            String sql = "SELECT * FROM pessoa WHERE id=?";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql)) {

                ps.setInt(1, id);

                ResultSet rs = ps.executeQuery();

                if (rs.next()) {
                    Pessoa p = new Pessoa();
                    p.setId(id);
                    p.setNome(rs.getString("nome"));
                    p.setEmail(rs.getString("email"));

                    p.getTelefones().addAll(telefoneDAO.listarPorPessoa(id));

                    return p;
                }
            } catch (SQLException e) {
                                    System.out.println("Erro ao consultar pessoas: " + e.getMessage());
                      }

            return null;
        }
    }

---

### arquivo: dao\TelefoneDAO.java

    package dao;

    import model.Telefone;

    import java.sql.*;
    import java.util.ArrayList;
    import java.util.List;

    import db.ConnectionFactory;

    public class TelefoneDAO {

        public void salvar(Telefone t) throws Exception {

            String sql = "INSERT INTO telefone(ddd,numero,pessoa_id) VALUES(?,?,?)";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS)) {

                ps.setString(1, t.getDdd());
                ps.setString(2, t.getNumero());
                ps.setInt(3, t.getPessoaId());

                ps.executeUpdate();

                ResultSet rs = ps.getGeneratedKeys();
                if (rs.next())
                    t.setId(rs.getInt(1));
            } catch (SQLException e) {
                                    System.out.println("Erro ao salvar telefones: " + e.getMessage());
                      }
        }

        public List listarPorPessoa(int pessoaId) throws Exception {

            List lista = new ArrayList<>();

            String sql = "SELECT * FROM telefone WHERE id_pessoa = ?";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql)) {

                ps.setInt(1, pessoaId);

                ResultSet rs = ps.executeQuery();

                while (rs.next()) {
                    Telefone t = new Telefone(
                            rs.getString("ddd"),
                            rs.getString("numero")
                    );
                    t.setId(rs.getInt("id"));
                    t.setPessoaId(pessoaId);

                    lista.add(t);
                }
            } catch (SQLException e) {
                                    System.out.println("Erro ao consultar telefones: " + e.getMessage());
                      }

            return lista;
        }

        public void excluir(int id) throws Exception {

            String sql = "DELETE FROM telefone WHERE id=?";

            try (Connection con = ConnectionFactory.getConnection();
                 PreparedStatement ps = con.prepareStatement(sql)) {

                ps.setInt(1, id);
                ps.executeUpdate();
          } catch (SQLException e) {
                                    System.out.println("Erro ao excluir telefones: " + e.getMessage());
               }
        }
    }

---

### arquivo: db\ConnectionFactory.java

    package db;

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.SQLException;

    public class ConnectionFactory {

        private static final String URL = "jdbc:mysql://localhost:3306/agenda_telefonica";

        private static final String USER = "root";
        private static final String PASSWORD = "12345678";

        public static Connection getConnection() throws SQLException {
            return DriverManager.getConnection(URL, USER, PASSWORD);
        }
    }

---

### arquivo: model\Pessoa.java

    package model;

    import java.util.ArrayList;
    import java.util.List;

    public class Pessoa {

        private int id;
        private String nome;
        private String email;
        private List telefones = new ArrayList<>();

        public Pessoa() {}

        public Pessoa(String nome, String email) {
            this.nome = nome;
            this.email = email;
        }

        public int getId() {
            return id;
        }

        public void setId(int id) {
            this.id = id;
        }

        public String getNome() {
            return nome;
        }

        public void setNome(String nome) {
            this.nome = nome;
        }

        public String getEmail() {
            return email;
        }

        public void setEmail(String email) {
            this.email = email;
        }

        public List getTelefones() {
            return telefones;
        }

        @Override
        public String toString() {
            return "ID: " + id + ", Nome: " + nome + ", Email: " + email;
        }
    }

---

### arquivo: model\Telefone.java

    package model;

    public class Telefone {

        private int id;
        private String ddd;
        private String numero;
        private int pessoaId;

        public Telefone(String ddd, String numero) {
            this.ddd = ddd;
            this.numero = numero;
        }

        public int getId() {
            return id;
        }

        public void setId(int id) {
            this.id = id;
        }

        public String getDdd() {
            return ddd;
        }

        public String getNumero() {
            return numero;
        }

        public int getPessoaId() {
            return pessoaId;
        }

        public void setPessoaId(int pessoaId) {
            this.pessoaId = pessoaId;
        }

        @Override
        public String toString() {
            return "ID: " + id + " (" + ddd + ") " + numero;
        }
    }

---

# Complemento da Lição

## Arquitetura alvo (MVC para console)

### Model (dados + acesso a dados)
- `model.Pessoa`, `model.Telefone`
- `dao.PessoaDAO`, `dao.TelefoneDAO`
- `db.ConnectionFactory`

### View (console)
- Uma classe responsável por:
  - mostrar menus e mensagens (`System.out.println`)
  - ler entradas (`Scanner`)
- Exemplo de pacote: `view.ConsoleView`

### Controller (coordena ações)
- Uma classe responsável por:
  - executar o loop do menu
  - chamar DAO (Model)
  - pedir/mostrar informações na View
- Exemplo de pacote: `controller.PessoaController`

---

## Passo a passo (sem pular etapas)

### Passo 1 — Criar o “Main” mínimo (App não faz mais tudo)
Crie um `app.Main` que só instancia controller + view e chama `start()`.

Estrutura sugerida:
- `app/Main.java`
- `controller/PessoaController.java`
- `view/ConsoleView.java`

Exemplo de esqueleto (preencher por você):
    package app;

    import controller.PessoaController;
    import view.ConsoleView;
    import dao.PessoaDAO;

    public class Main {
        public static void main(String[] args) throws Exception {
            ConsoleView view = new ConsoleView();
            PessoaDAO dao = new PessoaDAO();
            PessoaController controller = new PessoaController(view, dao);
            controller.start();
        }
    }

---

### Passo 2 — Mover menu e leitura de dados para a View
Objetivo: **tirar Scanner e prints do Controller/DAO**.

Esqueleto de `ConsoleView` (preencher por você):
    package view;

    import java.util.Scanner;
    import model.Pessoa;

    public class ConsoleView {

        private final Scanner teclado = new Scanner(System.in);

        public int menuPrincipal() {
            // imprimir opções e ler número
            // retornar opção
            return 0; // TODO
        }

        public String lerTexto(String rotulo) {
            // imprimir "rotulo: " e retornar texto
            return ""; // TODO
        }

        public int lerInt(String rotulo) {
            // ler int com segurança e consumir quebra de linha
            return 0; // TODO
        }

        public void mostrar(String msg) {
            // System.out.println
        }

        public void mostrarPessoa(Pessoa p) {
            // imprime a pessoa
        }
    }

---

### Passo 3 — Controller vira o “cérebro do fluxo”
Objetivo: o Controller decide “o que fazer” com cada opção, mas não faz I/O direto (isso é View).

Esqueleto de `PessoaController` (preencher por você):
    package controller;

    import dao.PessoaDAO;
    import view.ConsoleView;
    import model.Pessoa;
    import model.Telefone;

    import java.util.List;

    public class PessoaController {

        private final ConsoleView view;
        private final PessoaDAO dao;

        public PessoaController(ConsoleView view, PessoaDAO dao) {
            this.view = view;
            this.dao = dao;
        }

        public void start() throws Exception {
            int opcao;
            do {
                opcao = view.menuPrincipal();
                switch (opcao) {
                    case 1:
                        incluir();
                        break;
                    case 2:
                        listar();
                        break;
                    case 3:
                        excluir();
                        break;
                    case 4:
                        alterar();
                        break;
                    case 5:
                        view.mostrar("Saindo...");
                        break;
                    default:
                        view.mostrar("Opção inválida.");
                }
            } while (opcao != 5);
        }

        private void incluir() throws Exception {
            // ler nome/email na view
            // montar Pessoa e Telefones
            // dao.salvar(pessoa)
        }

        private void listar() throws Exception {
            // dao.listar()
            // view.mostrarPessoa + telefones
        }

        private void excluir() throws Exception {
            // ler id na view
            // dao.excluir(id)
        }

        private void alterar() throws Exception {
            // ler id na view
            // dao.buscarPorId(id)
            // se null: view.mostrar("Não encontrado")
            // senão: ler novo nome/email e dao.atualizar(p)
        }
    }

---

## Checagem rápida (para você validar que fez MVC de verdade)
- A classe `Main` não tem regra de menu.
- A `ConsoleView` concentra Scanner + prints.
- O `PessoaController` concentra o switch do menu e chama DAO.
- DAO não imprime menus nem lê teclado.

---

## Exercício (o próximo passo prático)
Implemente primeiro **apenas**:
1) `menuPrincipal()` na `ConsoleView`  
2) `start()` no `PessoaController` chamando os métodos vazios  
3) Só depois implemente `incluir()` (o resto vem em sequência)

---

## 1 pergunta (para eu guiar o próximo passo)
Você quer que a **View** trate entradas inválidas (ex.: letra em vez de número no menu) com repetição até acertar, ou pode encerrar com mensagem de erro?

<!-- nav_start -->
---
Anterior: [166 Padrão Arquitetural MVC](../docs/166_Padrão_Arquitetural_MVC.md) | Proximo: [168 Preparação para aplicação backend no formato de API HTTP](../docs/168_Preparação_para_aplicação_backend_no_formato_de_API_HTTP.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
