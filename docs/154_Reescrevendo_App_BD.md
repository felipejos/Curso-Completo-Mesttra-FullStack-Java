Reescrevendo uma aplicação para banco de dados
Reescrevendo a aplicação abaixo para utilizar um banco de dados ao invés de Matrizes.


import java.util.Scanner;

public class App {

        // ==================== constantes e variáveis definidas no formato global =====================        
        // pesquise sobre "variáveis globais em Java" para mais detalhes

        // Constante que define o tamanho máximo de alunos
        static final int MAX_ALUNOS = 100;

        // Colunas da matriz alunos
        // serão utilizadas para facilitar o acesso aos dados
        // e saber o que cada índice representa
        static final int COL_MATRICULA = 0;
        static final int COL_NOME = 1;
        static final int COL_EMAIL = 2;

        // Colunas da matriz notas
        // serão utilizadas para facilitar o acesso aos dados
        // e saber o que cada índice representa
        static final int NOTA_PROVA1 = 0;
        static final int NOTA_TRABALHO1 = 1;
        static final int NOTA_PROVA2 = 2;
        static final int NOTA_TRABALHO2 = 3;

        static String[][] alunos = new String[MAX_ALUNOS][3];
        static double[][] notas = new double[MAX_ALUNOS][4];

        static int totalAlunos = 0;
        static Scanner sc = new Scanner(System.in);

        // =============================================================================================

        public static void main(String[] args) {

                int opcao;

                do {
                        limparTela();
                        exibirMenu();
                        opcao = sc.nextInt();
                        sc.nextLine();

                        // este switch utiliza a sintaxe do Java 14+
                        // para simplificar o código e melhorar a legibilidade
                        // pesquise sobre "switch expressions" para mais detalhes
                        switch (opcao) {
                                case 1 -> cadastrarAluno();
                                case 2 -> menuConsultaAluno();
                                case 3 -> alterarAluno();
                                case 4 -> excluirAluno();
                                case 5 -> listarAlunos();
                                case 0 -> System.out.println("Encerrando o sistema...");
                                default -> System.out.println("Opção inválida!");
                        }

                        // Pausa para o usuário ler a mensagem antes de continuar
                        if (opcao != 0) {
                                System.out.println("\nPressione ENTER para continuar...");
                                sc.nextLine();
                        }

                // repete enquanto a opção for diferente de 0
                // 0 define que o usuário deseja sair do sistema
                } while (opcao != 0);
        }

        // ================= MENUS =================

        static void exibirMenu() {
                // procedimento responsável por exibir o menu principal
                System.out.println("=================== SISTEMA DE CONTROLE DE ALUNOS ===================\n");
                System.out.println("1 - Cadastrar aluno");
                System.out.println("2 - Consultar aluno");
                System.out.println("3 - Alterar aluno");
                System.out.println("4 - Excluir aluno");
                System.out.println("5 - Listar todos os alunos");
                System.out.println("0 - Sair\n");
                System.out.print("Escolha uma opção: ");
        }

        static void exibirSubmenuConsultaAluno() {
                // procedimento responsável por exibir o submenu de consulta de alunos
                System.out.println("=================== CONSULTAR ALUNO ===================\n");
                System.out.println("1 - Buscar por matrícula");
                System.out.println("2 - Buscar pelo início do nome");
                System.out.println("0 - Voltar\n");
                System.out.print("Escolha uma opção: ");
        }

        
        static void menuConsultaAluno() {
                // este procedimento exibe o submenu de consulta de alunos

                int opcao;

                do {
                        limparTela();
                        exibirSubmenuConsultaAluno();
                        opcao = sc.nextInt();
                        sc.nextLine();

                        switch (opcao) {
                                case 1 -> consultarPorMatricula();
                                case 2 -> consultarPorNome();
                                case 0 -> {
                                }
                                default -> System.out.println("Opção inválida!");
                        }

                        if (opcao != 0) {
                                System.out.println("\nPressione ENTER para continuar...");

                                // este comando é necessário para consumir o ENTER
                                // que ficou no buffer após o nextInt()
                                sc.nextLine();
                        }

                // repete enquanto a opção for diferente de 0
                // 0 define que o usuário deseja sair do sistema
                } while (opcao != 0);
        }

        // ================= CONSULTAS =================

        static void consultarPorMatricula() {

                // obtem a matrícula do aluno a ser consultado
                System.out.print("\nDigite a matrícula: ");
                String matricula = sc.nextLine();

                // busca o índice do aluno na matriz
                int index = buscarAlunoPorMatricula(matricula);

                // se o índice for -1, o aluno não foi encontrado
                if (index == -1) {
                        System.out.println("\nAluno não encontrado!");
                        return;
                }

                imprimirCabecalhoTabela();
                imprimirAluno(index);
                imprimirLinhaTabela();
        }

        static void consultarPorNome() {
                // flag para indicar se algum aluno foi encontrado
                // durante a busca, isto auxilia na impressão da mensagem
                // caso nenhum aluno seja encontrado
                boolean encontrou = false;

                // obtem o início do nome a ser consultado
                System.out.print("Digite o início do nome: ");
                String inicioNome = sc.nextLine().toLowerCase();

                imprimirCabecalhoTabela();

                // realiza a busca por todos os alunos cadastrados
                // que tenham o nome iniciando com o texto fornecido
                for (int i = 0; i < totalAlunos; i++) {
                        // startsWith verifica se o nome do aluno armazenado no vetor
                        // e no índice i começa com o texto fornecido
                        if (alunos[i][COL_NOME].toLowerCase().startsWith(inicioNome)) {
                                imprimirAluno(i);
                                // altera a flag para indicar que um aluno foi encontrado
                                encontrou = true;
                        }
                }

                imprimirLinhaTabela();

                // se a flag ainda for false, nenhum aluno foi encontrado
                if (!encontrou) {
                        System.out.println("\nNenhum aluno encontrado com esse critério.");
                }
        }

        static void cadastrarAluno() {

                // verifica se o limite de alunos foi atingido
                if (totalAlunos >= MAX_ALUNOS) {
                        System.out.println("Limite de alunos atingido!");
                        // força o retorno ao menu principal
                        return;
                }

                // obtem os dados do aluno a ser cadastrado
                System.out.print("\nMatrícula: ");
                alunos[totalAlunos][COL_MATRICULA] = sc.nextLine();

                System.out.print("Nome: ");
                alunos[totalAlunos][COL_NOME] = sc.nextLine();

                System.out.print("Email: ");
                alunos[totalAlunos][COL_EMAIL] = sc.nextLine();

                System.out.print("Prova 1: ");
                notas[totalAlunos][NOTA_PROVA1] = sc.nextDouble();

                System.out.print("Trabalho 1: ");
                notas[totalAlunos][NOTA_TRABALHO1] = sc.nextDouble();

                System.out.print("Prova 2: ");
                notas[totalAlunos][NOTA_PROVA2] = sc.nextDouble();

                System.out.print("Trabalho 2: ");
                notas[totalAlunos][NOTA_TRABALHO2] = sc.nextDouble();
                sc.nextLine();

                // ajusta a variável que controla o total de alunos cadastrados
                // esta variavel é utilizada para controlar onde o próximo aluno
                // será cadastrado na matriz
                totalAlunos++;
                System.out.println("\nAluno cadastrado com sucesso!");
        }

        static void alterarAluno() {

                // obtem a matrícula do aluno a ser alterado
                System.out.print("Digite a matrícula do aluno: ");
                String matricula = sc.nextLine();

                // busca o índice do aluno na matriz que possui a matrícula fornecida
                int index = buscarAlunoPorMatricula(matricula);

                // se o índice for -1, o aluno não foi encontrado
                if (index == -1) {
                        System.out.println("\nAluno não encontrado!");
                        // força o retorno ao menu principal
                        return;
                }

                // obtem os novos dados do aluno
                System.out.print("Novo nome: ");
                alunos[index][COL_NOME] = sc.nextLine();

                System.out.print("Novo email: ");
                alunos[index][COL_EMAIL] = sc.nextLine();

                System.out.print("Nova Prova 1: ");
                notas[index][NOTA_PROVA1] = sc.nextDouble();

                System.out.print("Novo Trabalho 1: ");
                notas[index][NOTA_TRABALHO1] = sc.nextDouble();

                System.out.print("Nova Prova 2: ");
                notas[index][NOTA_PROVA2] = sc.nextDouble();

                System.out.print("Novo Trabalho 2: ");
                notas[index][NOTA_TRABALHO2] = sc.nextDouble();
                sc.nextLine();

                System.out.println("\nAluno alterado com sucesso!");
        }

        static void excluirAluno() {

                // obtem a matrícula do aluno a ser excluído
                System.out.print("Digite a matrícula do aluno: ");
                String matricula = sc.nextLine();

                // busca o índice do aluno na matriz que possui a matrícula fornecida
                int index = buscarAlunoPorMatricula(matricula);

                // se o índice for -1, o aluno não foi encontrado
                if (index == -1) {
                        System.out.println("\nAluno não encontrado!");
                        return;
                }

                // realiza a exclusão do aluno
                // atraves da sobreposição dos dados
                // dos alunos posteriores ao aluno a ser excluído
                // desta forma, o aluno a ser excluído é "removido"
                // e os dados posteriores são movidos uma posição para trás
                // na matriz de alunos e notas para manter a consistência 
                // e  nao deixar "buracos" na matriz
                for (int i = index; i < totalAlunos - 1; i++) {
                        alunos[i] = alunos[i + 1];
                        notas[i] = notas[i + 1];
                }

                // ajusta a variável que controla o total de alunos cadastrados
                // aponta para o último aluno válido na matriz
                totalAlunos--;
                System.out.println("\nAluno excluído com sucesso!");
        }

        static void listarAlunos() {

                // verifica se há alunos cadastrados
                if (totalAlunos == 0) {
                        System.out.println("\nNenhum aluno cadastrado.");
                        // força o retorno ao menu principal
                        return;
                }

                imprimirCabecalhoTabela();

                // percorre todos os alunos cadastrados e os imprime
                for (int i = 0; i < totalAlunos; i++) {
                        imprimirAluno(i);
                }

                // imprime a linha final da tabela
                imprimirLinhaTabela();
        }


        static void imprimirCabecalhoTabela() {
                // imprime o cabeçalho da tabela de alunos
                imprimirLinhaTabela();
                // pesquise sobre "formatted strings in Java" para mais detalhes
                // foque no padding e alinhamento de texto em Java
                System.out.printf("| %-10s | %-20s | %-24s | %-6s | %-9s | %-6s | %-9s |\n","Matrícula", "Nome", "Email", "P1", "T1", "P2", "T2");
                imprimirLinhaTabela();
        }

        static void imprimirAluno(int i) {
                // imprime os dados do aluno no índice i da matriz
                System.out.printf(
                                "| %-10s | %-20s | %-24s | %6.2f | %9.2f | %6.2f | %9.2f |\n",
                                alunos[i][COL_MATRICULA],
                                alunos[i][COL_NOME],
                                alunos[i][COL_EMAIL],
                                notas[i][NOTA_PROVA1],
                                notas[i][NOTA_TRABALHO1],
                                notas[i][NOTA_PROVA2],
                                notas[i][NOTA_TRABALHO2]);
        }

        static void imprimirLinhaTabela() {
                System.out.println("+------------+----------------------+--------------------------+--------+-----------+--------+-----------+");
        }

        static int buscarAlunoPorMatricula(String matricula) {
                // percorre todos os alunos cadastrados
                // e verifica se a matrícula fornecida pertence ao aluno
                for (int i = 0; i < totalAlunos; i++) {
                        if (alunos[i][COL_MATRICULA].equals(matricula)) {
                                // se encontrar, retorna o índice do aluno na matriz
                                return i;
                        }
                }

                // se nenhum aluno for encontrado, retorna -1
                return -1;
        }

        static void limparTela() {
                try {
                        if (System.getProperty("os.name").toLowerCase().contains("win")) {
                                new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                        } else {
                                new ProcessBuilder("clear").inheritIO().start().waitFor();
                        }
                } catch (Exception e) {
                        for (int i = 0; i < 50; i++) {
                                System.out.println();
                        }
                }
        }
}

---

## Opção melhorada

# Reescrita do Sistema para Banco de Dados (MySQL + JDBC)

## 1) Modelo de Dados (tabela única para simplificar)
Este modelo guarda **dados do aluno + notas** na mesma tabela (mais simples para começar).

    -- Banco
    CREATE DATABASE IF NOT EXISTS controle_alunos
      DEFAULT CHARACTER SET utf8mb4
      COLLATE utf8mb4_unicode_ci;

    USE controle_alunos;

    -- Tabela
    CREATE TABLE IF NOT EXISTS aluno (
        matricula   VARCHAR(20) PRIMARY KEY,
        nome        VARCHAR(150) NOT NULL,
        email       VARCHAR(150) NOT NULL,
        prova1      DOUBLE NOT NULL,
        trabalho1   DOUBLE NOT NULL,
        prova2      DOUBLE NOT NULL,
        trabalho2   DOUBLE NOT NULL,
        data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    );

    -- Índices úteis para consultas por nome (LIKE)
    CREATE INDEX idx_aluno_nome ON aluno (nome);

---

## 2) Dependência (MySQL Connector/J no VS Code)
Para o Java conseguir falar com MySQL via JDBC, o projeto precisa do driver:

- Arquivo: `mysql-connector-j-8.x.x.jar`

Estrutura comum do projeto (VS Code):

    seu_projeto/
      lib/
        mysql-connector-j-8.x.x.jar
      src/
        App.java

---

## 3) Aplicação Console usando JDBC (App.java)
Abaixo está a versão reescrita para banco de dados, mantendo a ideia do menu e das operações (CRUD) sem usar matrizes.

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.PreparedStatement;
    import java.sql.ResultSet;
    import java.sql.SQLException;

    import java.util.Locale;
    import java.util.Scanner;

    public class App {

        // ======== Configurações do Banco ========
        // Ajuste usuário/senha conforme seu MySQL
        private static final String STR_CONNECTION =
                "jdbc:mysql://localhost:3306/controle_alunos?useUnicode=true&characterEncoding=utf8&serverTimezone=UTC";
        private static final String USER = "root";
        private static final String PASSWORD = "12345678";

        // ======== Scanner ========
        private static final Scanner sc = new Scanner(System.in);

        // ======== SQL ========
        private static final String SQL_INSERT =
                "INSERT INTO aluno (matricula, nome, email, prova1, trabalho1, prova2, trabalho2) VALUES (?, ?, ?, ?, ?, ?, ?)";

        private static final String SQL_SELECT_ALL =
                "SELECT matricula, nome, email, prova1, trabalho1, prova2, trabalho2 FROM aluno ORDER BY nome";

        private static final String SQL_SELECT_BY_MATRICULA =
                "SELECT matricula, nome, email, prova1, trabalho1, prova2, trabalho2 FROM aluno WHERE matricula = ?";

        private static final String SQL_SELECT_BY_NOME_PREFIX =
                "SELECT matricula, nome, email, prova1, trabalho1, prova2, trabalho2 " +
                "FROM aluno WHERE LOWER(nome) LIKE ? ORDER BY nome";

        private static final String SQL_UPDATE =
                "UPDATE aluno SET nome = ?, email = ?, prova1 = ?, trabalho1 = ?, prova2 = ?, trabalho2 = ? WHERE matricula = ?";

        private static final String SQL_DELETE =
                "DELETE FROM aluno WHERE matricula = ?";

        public static void main(String[] args) {
            Locale.setDefault(new Locale("pt", "BR"));

            int opcao;

            do {
                limparTela();
                exibirMenu();
                opcao = lerInt("Escolha uma opção: ");

                switch (opcao) {
                    case 1 -> cadastrarAluno();
                    case 2 -> menuConsultaAluno();
                    case 3 -> alterarAluno();
                    case 4 -> excluirAluno();
                    case 5 -> listarAlunos();
                    case 0 -> System.out.println("Encerrando o sistema...");
                    default -> System.out.println("Opção inválida!");
                }

                if (opcao != 0) {
                    System.out.println("\nPressione ENTER para continuar...");
                    sc.nextLine();
                }

            } while (opcao != 0);

            sc.close();
        }

        // ================= MENUS =================

        static void exibirMenu() {
            System.out.println("=================== SISTEMA DE CONTROLE DE ALUNOS (DB) ===================\n");
            System.out.println("1 - Cadastrar aluno");
            System.out.println("2 - Consultar aluno");
            System.out.println("3 - Alterar aluno");
            System.out.println("4 - Excluir aluno");
            System.out.println("5 - Listar todos os alunos");
            System.out.println("0 - Sair\n");
        }

        static void exibirSubmenuConsultaAluno() {
            System.out.println("=================== CONSULTAR ALUNO ===================\n");
            System.out.println("1 - Buscar por matrícula");
            System.out.println("2 - Buscar pelo início do nome");
            System.out.println("0 - Voltar\n");
        }

        static void menuConsultaAluno() {
            int opcao;

            do {
                limparTela();
                exibirSubmenuConsultaAluno();
                opcao = lerInt("Escolha uma opção: ");

                switch (opcao) {
                    case 1 -> consultarPorMatricula();
                    case 2 -> consultarPorNome();
                    case 0 -> { }
                    default -> System.out.println("Opção inválida!");
                }

                if (opcao != 0) {
                    System.out.println("\nPressione ENTER para continuar...");
                    sc.nextLine();
                }

            } while (opcao != 0);
        }

        // ================= CRUD (DB) =================

        static void cadastrarAluno() {
            limparTela();

            String matricula = lerString("\nMatrícula: ");
            String nome = lerString("Nome: ");
            String email = lerString("Email: ");

            double prova1 = lerDouble("Prova 1: ");
            double trabalho1 = lerDouble("Trabalho 1: ");
            double prova2 = lerDouble("Prova 2: ");
            double trabalho2 = lerDouble("Trabalho 2: ");

            try (Connection conn = getConnection();
                 PreparedStatement ps = conn.prepareStatement(SQL_INSERT)) {

                ps.setString(1, matricula);
                ps.setString(2, nome);
                ps.setString(3, email);
                ps.setDouble(4, prova1);
                ps.setDouble(5, trabalho1);
                ps.setDouble(6, prova2);
                ps.setDouble(7, trabalho2);

                int linhas = ps.executeUpdate();

                if (linhas > 0) {
                    System.out.println("\nAluno cadastrado com sucesso!");
                } else {
                    System.out.println("\nNenhum aluno foi cadastrado.");
                }

            } catch (SQLException e) {
                System.out.println("\nErro ao cadastrar aluno: " + e.getMessage());
            }
        }

        static void consultarPorMatricula() {
            String matricula = lerString("\nDigite a matrícula: ");

            try (Connection conn = getConnection();
                 PreparedStatement ps = conn.prepareStatement(SQL_SELECT_BY_MATRICULA)) {

                ps.setString(1, matricula);

                try (ResultSet rs = ps.executeQuery()) {
                    if (!rs.next()) {
                        System.out.println("\nAluno não encontrado!");
                        return;
                    }

                    imprimirCabecalhoTabela();
                    imprimirAluno(rs);
                    imprimirLinhaTabela();
                }

            } catch (SQLException e) {
                System.out.println("\nErro ao consultar: " + e.getMessage());
            }
        }

        static void consultarPorNome() {
            String inicioNome = lerString("Digite o início do nome: ").toLowerCase();

            boolean encontrou = false;

            try (Connection conn = getConnection();
                 PreparedStatement ps = conn.prepareStatement(SQL_SELECT_BY_NOME_PREFIX)) {

                ps.setString(1, inicioNome + "%");

                try (ResultSet rs = ps.executeQuery()) {
                    imprimirCabecalhoTabela();

                    while (rs.next()) {
                        imprimirAluno(rs);
                        encontrou = true;
                    }

                    imprimirLinhaTabela();
                }

                if (!encontrou) {
                    System.out.println("\nNenhum aluno encontrado com esse critério.");
                }

            } catch (SQLException e) {
                System.out.println("\nErro ao consultar: " + e.getMessage());
            }
        }

        static void alterarAluno() {
            String matricula = lerString("Digite a matrícula do aluno: ");

            if (!existeAluno(matricula)) {
                System.out.println("\nAluno não encontrado!");
                return;
            }

            String novoNome = lerString("Novo nome: ");
            String novoEmail = lerString("Novo email: ");

            double prova1 = lerDouble("Nova Prova 1: ");
            double trabalho1 = lerDouble("Novo Trabalho 1: ");
            double prova2 = lerDouble("Nova Prova 2: ");
            double trabalho2 = lerDouble("Novo Trabalho 2: ");

            try (Connection conn = getConnection();
                 PreparedStatement ps = conn.prepareStatement(SQL_UPDATE)) {

                ps.setString(1, novoNome);
                ps.setString(2, novoEmail);
                ps.setDouble(3, prova1);
                ps.setDouble(4, trabalho1);
                ps.setDouble(5, prova2);
                ps.setDouble(6, trabalho2);
                ps.setString(7, matricula);

                int linhas = ps.executeUpdate();

                if (linhas > 0) {
                    System.out.println("\nAluno alterado com sucesso!");
                } else {
                    System.out.println("\nNenhuma alteração realizada.");
                }

            } catch (SQLException e) {
                System.out.println("\nErro ao alterar aluno: " + e.getMessage());
            }
        }

        static void excluirAluno() {
            String matricula = lerString("Digite a matrícula do aluno: ");

            if (!existeAluno(matricula)) {
                System.out.println("\nAluno não encontrado!");
                return;
            }

            try (Connection conn = getConnection();
                 PreparedStatement ps = conn.prepareStatement(SQL_DELETE)) {

                ps.setString(1, matricula);

                int linhas = ps.executeUpdate();

                if (linhas > 0) {
                    System.out.println("\nAluno excluído com sucesso!");
                } else {
                    System.out.println("\nNenhuma exclusão realizada.");
                }

            } catch (SQLException e) {
                System.out.println("\nErro ao excluir aluno: " + e.getMessage());
            }
        }

        static void listarAlunos() {
            try (Connection conn = getConnection();
                 PreparedStatement ps = conn.prepareStatement(SQL_SELECT_ALL);
                 ResultSet rs = ps.executeQuery()) {

                if (!rs.isBeforeFirst()) {
                    System.out.println("\nNenhum aluno cadastrado.");
                    return;
                }

                imprimirCabecalhoTabela();

                while (rs.next()) {
                    imprimirAluno(rs);
                }

                imprimirLinhaTabela();

            } catch (SQLException e) {
                System.out.println("\nErro ao listar alunos: " + e.getMessage());
            }
        }

        // ================= Impressão em Tabela =================

        static void imprimirCabecalhoTabela() {
            imprimirLinhaTabela();
            System.out.printf(
                    "| %-10s | %-20s | %-24s | %6s | %9s | %6s | %9s |\n",
                    "Matrícula", "Nome", "Email", "P1", "T1", "P2", "T2"
            );
            imprimirLinhaTabela();
        }

        static void imprimirAluno(ResultSet rs) throws SQLException {
            System.out.printf(
                    "| %-10s | %-20s | %-24s | %6.2f | %9.2f | %6.2f | %9.2f |\n",
                    rs.getString("matricula"),
                    limitarTexto(rs.getString("nome"), 20),
                    limitarTexto(rs.getString("email"), 24),
                    rs.getDouble("prova1"),
                    rs.getDouble("trabalho1"),
                    rs.getDouble("prova2"),
                    rs.getDouble("trabalho2")
            );
        }

        static String limitarTexto(String texto, int limite) {
            if (texto == null) return "";
            if (texto.length() <= limite) return texto;

            if (limite <= 3) return texto.substring(0, limite);
            return texto.substring(0, limite - 3) + "...";
        }

        static void imprimirLinhaTabela() {
            System.out.println("+------------+----------------------+--------------------------+--------+-----------+--------+-----------+");
        }

        // ================= Helpers (DB / Input) =================

        static Connection getConnection() throws SQLException {
            return DriverManager.getConnection(STR_CONNECTION, USER, PASSWORD);
        }

        static boolean existeAluno(String matricula) {
            try (Connection conn = getConnection();
                 PreparedStatement ps = conn.prepareStatement(SQL_SELECT_BY_MATRICULA)) {

                ps.setString(1, matricula);

                try (ResultSet rs = ps.executeQuery()) {
                    return rs.next();
                }

            } catch (SQLException e) {
                System.out.println("\nErro ao verificar aluno: " + e.getMessage());
                return false;
            }
        }

        static String lerString(String mensagem) {
            System.out.print(mensagem);
            return sc.nextLine().trim();
        }

        static int lerInt(String mensagem) {
            while (true) {
                System.out.print(mensagem);
                String entrada = sc.nextLine().trim();

                try {
                    return Integer.parseInt(entrada);
                } catch (NumberFormatException e) {
                    System.out.println("Valor inválido. Digite um número inteiro.");
                }
            }
        }

        static double lerDouble(String mensagem) {
            while (true) {
                System.out.print(mensagem);
                String entrada = sc.nextLine().trim().replace(",", ".");

                try {
                    return Double.parseDouble(entrada);
                } catch (NumberFormatException e) {
                    System.out.println("Valor inválido. Digite um número (ex: 7.5).");
                }
            }
        }

        static void limparTela() {
            try {
                if (System.getProperty("os.name").toLowerCase().contains("win")) {
                    new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                } else {
                    new ProcessBuilder("clear").inheritIO().start().waitFor();
                }
            } catch (Exception e) {
                for (int i = 0; i < 50; i++) {
                    System.out.println();
                }
            }
        }
    }

---

## Exercícios (fixação)

1) (SQL) Crie uma consulta que liste apenas alunos com média (P1+T1+P2+T2)/4 >= 7.0.  
2) (SQL) Crie uma consulta que liste os 5 alunos com maior nota de Prova 1.  
3) (Java) Adicione uma opção “6 - Exibir aluno com maior média” (SELECT + cálculo).  
4) (Java) Adicione validação de e-mail (precisa conter `@` e `.`) antes de salvar.  
5) (DB) Crie uma coluna `status` (`ATIVO/INATIVO`) e mude o “excluir” para marcar `INATIVO` ao invés de apagar.

<!-- nav_start -->
---
Anterior: [153 Video SQL no Java](../docs/153_Video_SQL_no_Java.md) | Proximo: [155 Resumo Classes Objetos](../docs/155_Resumo_Classes_Objetos.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
