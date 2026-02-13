Aplicativo Gerenciamento de Alunos
O sistema apresentado é um Sistema de Controle de Alunos que funciona em modo console. Ele permite gerenciar informações básicas de alunos de forma simples e organizada, utilizando apenas estruturas de dados em memória, posteriormente substituiremos o armazenamento em memória por um banco de dados,

De maneira geral, o sistema possibilita o cadastro, consulta, alteração, exclusão e listagem de alunos. Para cada aluno, são armazenados dados como matrícula, nome, e-mail, além das notas de avaliações (duas provas e dois trabalhos). Essas informações são mantidas em matrizes, respeitando um limite máximo de alunos definido no sistema.

A interação com o usuário ocorre por meio de menus no formato de texto, nos quais o usuário escolhe as operações desejadas. O sistema conta com um menu principal e um submenu de consulta, permitindo buscar alunos tanto pela matrícula quanto pelo início do nome. Os dados são exibidos em formato de tabela textual, facilitando a leitura e a visualização das informações.

O sistema também realiza validações básicas, como verificar se o aluno existe antes de consultar, alterar ou excluir, e se o limite máximo de alunos foi atingido antes de permitir novos cadastros. Além disso, mantém a consistência dos dados ao reorganizar as matrizes quando um aluno é removido, evitando espaços vazios.

Este sistema pode ser evoluido para acrescentar novas funcionalidades como cálculo da nota média, se o aluno foi aprovado ou reprovado, além de outras funcionalidades.

Analise o código para entender o funcionamento do mesmo,

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

**Complementos (mais completo e fácil de entender)**

### 1) O que esse sistema “é” na prática (uma frase bem direta)
É um **CRUD em console** (Create, Read, Update, Delete) de alunos, usando **matrizes em memória** para guardar os dados.

- **Create**: `cadastrarAluno()`
- **Read**: `consultarPorMatricula()`, `consultarPorNome()`, `listarAlunos()`
- **Update**: `alterarAluno()`
- **Delete**: `excluirAluno()`

Isso é um modelo perfeito para treinar: **menu + vetores/matrizes + busca + validações + impressão formatada**.

---

### 2) Como os dados estão guardados (entenda antes de ler o resto)
Você usa duas matrizes paralelas (elas “andam juntas” pelo mesmo índice):

- `alunos[i][...]` guarda **texto** do aluno (matrícula, nome, email)
- `notas[i][...]` guarda **números** do aluno (P1, T1, P2, T2)

**Exemplo mental:**
Se o aluno está no índice `i = 3`:

- `alunos[3][COL_NOME]`  → nome do aluno 3
- `notas[3][NOTA_PROVA1]` → nota P1 do aluno 3

A “cola” entre essas duas matrizes é o índice `i`.

---

### 3) Por que você criou constantes como COL_NOME e NOTA_PROVA1?
Porque isso evita “número mágico” no código.

Em vez de escrever:

- `alunos[i][1]`
- `notas[i][2]`

Você escreve:

- `alunos[i][COL_NOME]`
- `notas[i][NOTA_PROVA2]`

Isso deixa o código:
- mais legível
- mais seguro (menos chance de errar o índice)
- mais fácil de manter (se a ordem mudar, você altera a constante, não o sistema todo)

---

### 4) Fluxo do programa (como o usuário “navega”)
**Menu principal (loop do main):**
1. limpa a tela
2. mostra o menu
3. lê a opção
4. executa a ação (switch)
5. pausa no ENTER
6. repete até o usuário digitar 0

**Submenu de consulta (menuConsultaAluno):**
1. mostra opções de busca
2. lê a opção
3. chama `consultarPorMatricula()` ou `consultarPorNome()`
4. volta até o usuário escolher 0

Esse padrão é muito usado em sistemas de console: **menu em loop + switch**.

---

### 5) Como a busca por matrícula funciona (conceito de busca linear)
O método:

- `buscarAlunoPorMatricula(String matricula)`

faz uma **busca linear** (varre do início até `totalAlunos`):

- se achar, retorna o índice do aluno
- se não achar, retorna `-1`

Isso é importante porque o índice retornado vira “chave” para:
- consultar
- alterar
- excluir

---

### 6) Como a exclusão funciona (por que não fica “buraco”)
Quando você remove um aluno, você não deixa a posição vazia.

Você faz:

- sobrescreve `alunos[index]` com `alunos[index + 1]`
- e assim por diante (shift para a esquerda)

Depois:

- `totalAlunos--`

Resultado:
- o “fim válido” da lista diminui
- o sistema continua compacto
- nenhuma função precisa lidar com posições vazias no meio

**Isso é o comportamento típico de “remoção em array”**.

---

### 7) Como a listagem em tabela funciona (por que fica alinhado)
Você usa `printf` com formatação:

- `%-20s` → texto alinhado à esquerda com largura 20
- `%6.2f` → número com 2 casas decimais, ocupando largura mínima 6

Esse é um padrão excelente para console porque gera saída “profissional” e fácil de ler.

---

### 8) Validações que o sistema já faz (e o motivo delas existir)
- **Limite máximo**: `if (totalAlunos >= MAX_ALUNOS)` impede estourar o vetor
- **Aluno existe?**: `if (index == -1)` evita alterar/excluir algo que não existe
- **Sem alunos cadastrados**: `if (totalAlunos == 0)` evita listar tabela vazia

Essas validações são “regras de proteção” para manter o sistema estável.

---

### 9) Melhorias comuns para deixar esse sistema ainda mais “redondo”
Você pode evoluir esse projeto em camadas, sem “pular etapas”:

**A) Regras de dados (validação)**
- matrícula não pode ser vazia
- matrícula deve ser única (não permitir cadastrar duas iguais)
- email deve ter formato básico (ex: conter `@` e `.`)
- notas devem ficar em um intervalo (ex: 0 a 10)

**B) Robustez na entrada**
Hoje, se o usuário digitar texto onde era número, pode estourar exceção.
A evolução natural é criar funções de leitura segura (como a sua classe `Leitura` com repetição no erro).

**C) Funcionalidades acadêmicas**
- calcular **média do aluno**
- mostrar **situação** (aprovado / reprovado / recuperação)
- listar alunos por **maior média**
- relatório: **média geral da turma**

**D) Organização de código (arquitetura simples)**
Separar responsabilidades:
- `Menu` (exibir/ler opções)
- `AlunoService` (regras e processamento)
- `AlunoRepository` (armazenamento: hoje matriz, amanhã banco)

Assim, quando você trocar “matriz” por “banco”, o sistema muda menos.

---

### 10) Um “mapa mental” rápido do que cada método faz
- `main()` → loop do menu principal
- `menuConsultaAluno()` → loop do submenu de busca
- `cadastrarAluno()` → grava dados na posição `totalAlunos`
- `alterarAluno()` → acha índice pela matrícula e sobrescreve dados
- `excluirAluno()` → acha índice e “puxa” os próximos para não deixar buraco
- `listarAlunos()` → imprime todos os índices válidos (0 até totalAlunos-1)
- `buscarAlunoPorMatricula()` → devolve o índice (ou -1)
- `imprimirCabecalhoTabela()/imprimirAluno()` → saída formatada
- `limparTela()` → estética do console

Se você entender isso, você entendeu 90% do sistema.

<!-- nav_start -->
---
Anterior: [133 Sorteio Unico](../docs/133_Sorteio_Unico.md) | Proximo: [135 Primeira Hackathon](../docs/135_Primeira_Hackathon.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
