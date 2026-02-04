Desafio: Armazenamento de Dados em Arquivo


Este código possui um problema na entrada de dados da idade e do peso, se o usuário digitar um texto no lugar da idade ou do peso, será gerado uma exceção e o aplicativo fechará. Faça então a tratativa da leitura dos dados garantindo que o usuário insira um valor que seja aceito.



Desenvolva uma nova funcionalidade que conte a quantidade de de pessoas cadastradas.

Dica: Insira um novo item no menu "Exibir a QTDE de Pessoas" e depois no switch faça a exibição da quantidade de linhas no vetor.



Desenvolva uma nova funcionalidade que descubra quem tem a menor idade. Exiba o nome da Pessoa e a idade. 

Dica: Insira um novo item  no menu "Exibir a Pessoa com a Menor Idade".



Desenvolva uma nova funcionalidade que descubra quem tem o maior peso. Exiba o nome da Pessoa e o peso. 

Dica: Insira um novo item  no menu "Exibir a Pessoa com o Maior Peso".



Desenvolva uma nova funcionalidade que descubra a quantidade de pessoas quem tem um peso maior ou igual ao informado pelo usuario. Exiba somente a quantidade. 

Dica: Insira um novo item  no menu "Contar QTDE de Pessoas acima de Peso". Quando o usuário selecionar esta opção pergunte qual o peso que o usuário deseja utilizar como critério de busca, e descubra quantas pessoas tem um peso maior ou igual ao informado pelo usuário. 



import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileNotFoundException;
import java.util.*;

public class App {
    //inicio das variaveis globais
    static Scanner teclado = new Scanner(System.in);

    static String CAMINHO_ARQUIVO = "dados.txt";
    static int TAMANHO_MAXIMO = 50;

    static String[] nomes = new String[TAMANHO_MAXIMO];
    static int[] idades = new int[TAMANHO_MAXIMO];
    static float[] pesos = new float[TAMANHO_MAXIMO];

    //controlar quantas posicoes ja foram gravadas no vetor
    static int contador = 0;
    //variavel para controlar quando se deve ou nao limpar a
    static boolean limparTela = true;

    //fim das variaveis globais
    public static void main(String[] args) {
        //variavel que armazena a resposta do menu
        int opcao;
        
        carregarDados();

        do {
            limparTela();
            opcao = lerOpcaoMenu();
            processarOpcaoMenu(opcao);
        } while(opcao != 3);

        teclado.close();
    }

    static void processarOpcaoMenu(int opcao){
        switch (opcao) {
            case 1:
                adicionarDados();
                break;
            case 2:
                limparTela();
                mostrarDados();
                limparTela = false;
                break;
            case 3:
                limparTela();
                salvarDados();
                System.out.println("Encerrando...");
                break;
            default:
                System.out.println("Opção inválida. Tente novamente.");
        }
    }
    
    static void adicionarDados() {
        limparTela = true;
        limparTela();
        
        //Verifico se tem espaco nos vetores
        if (contador >= TAMANHO_MAXIMO) {
            System.out.println("Limite de dados atingido! Não é possível adicionar mais.");
            //estou usando um retorne para forcar o fim da execucao
            //do metodo adicionarDados quando nao tiver mais posicoes livres 
            //no vetor. 
            return;
        }

        System.out.print("Digite o nome: ");
        nomes[contador] = teclado.nextLine();

        System.out.print("Digite a idade: ");
        idades[contador] = teclado.nextInt();

        System.out.print("Digite o peso (em kg): ");
        pesos[contador] = teclado.nextFloat();
        teclado.nextLine(); // Limpar buffer

        contador++;
    }
    
    static int lerOpcaoMenu(){
        int opcao;
        System.out.println("\n############## Menu ##############\n");
        System.out.println("1. Adicionar dados");
        System.out.println("2. Mostrar dados");
        System.out.println("3. Sair");

        System.out.print("\nEscolha uma opção: ");
        opcao = teclado.nextInt();
        teclado.nextLine(); // Limpar buffer

        return opcao;
    }

    static void carregarDados() {
        FileReader arquivo = null;
        BufferedReader bufferLeitura = null;

        try {
            //define o arquivo que sera abert
            arquivo = new FileReader(CAMINHO_ARQUIVO);
            bufferLeitura = new BufferedReader(arquivo);
            String linha;

            linha = bufferLeitura.readLine();
            
            while (linha != null) {
                String[] campos = linha.split(";");
                if (campos.length == 3 && contador < TAMANHO_MAXIMO) {
                    nomes[contador] = campos[0];
                    //como o split devolve o resultado como string
                    //é necessario converter a idade do arquivo para int 
                    idades[contador] = Integer.parseInt(campos[1]);
                    //é necessário converter o peso do arquivo para float
                    pesos[contador] = Float.parseFloat(campos[2]);
                    contador++;
                }
                linha = bufferLeitura.readLine();
            }

        } catch (FileNotFoundException e) {
            System.out.println("Arquivo não encontrado. Um novo será criado ao salvar.");
        } catch (IOException e) {
            System.out.println("Erro ao carregar os dados: " + e.getMessage());
        } catch (NumberFormatException e) {
            System.out.println("Erro nos dados do arquivo: formato inválido.");
        } finally {
            // Fechamento do arquivo e do bufferLeitura
            try {
                if (bufferLeitura != null) {
                    bufferLeitura.close();
                }
                if (arquivo != null) {
                    arquivo.close();
                }
            } catch (IOException e) {
                System.out.println("Erro ao fechar o arquivo: " + e.getMessage());
            }
        }
    }

    static void mostrarDados() {
        int qtdeEspacos;

        if (contador == 0) {
            System.out.println("Nenhum dado disponível.");
            return;
        }

        System.out.println("\nNome                Idade               Peso");
        System.out.println("----------------------------------------------------------");
        for (int i = 0; i < contador; i++) {
            qtdeEspacos = 0;

            System.out.print(nomes[i]);
            //calcula quantos espacos sao necessarios para alinhar
            //o valor da idade na posicao da coluna idade
            qtdeEspacos = (20 - nomes[i].length());
            //imprime a quantidade de espacos para alinhar os salarios
            System.out.print(gerarEspacos(qtdeEspacos));

            System.out.print(idades[i]);
            qtdeEspacos = (20 - String.valueOf(idades[i]).length());
            System.out.print(gerarEspacos(qtdeEspacos));

            System.out.println(pesos[i]);
        }
    }

    static void salvarDados() {
        BufferedWriter gravador = null;
    
        try {
            // Inicializa o BufferedWriter para escrever no arquivo
            gravador = new BufferedWriter(new FileWriter(CAMINHO_ARQUIVO));
            
            // Escreve os dados no arquivo
            for (int i = 0; i < contador; i++) {
                //escreve os dados no arquivo
                gravador.write(nomes[i] + ";" + idades[i] + ";" + pesos[i]);
                //cria uma nova linha no arquivo
                gravador.newLine();
            }
    
            System.out.println("Dados salvos no arquivo.");
        } catch (IOException e) {
            System.out.println("Erro ao salvar os dados: " + e.getMessage());
        } finally {
            // Fechamento do BufferedWriter 
            if (gravador != null) {
                try {
                    gravador.close();
                } catch (IOException e) {
                    System.out.println("Erro ao fechar o arquivo: " + e.getMessage());
                }
            }
        }
    }

    static String gerarEspacos(int qtde){
        String espacos = "";

        for (int i = 0; i < qtde; i++) {
            espacos += " ";
        }

        return espacos;
    }

    static void limparTela(){
        if (limparTela){
            try {
                if (System.getProperty("os.name").contains("Windows")) {
                    new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                } else {
                    new ProcessBuilder("clear").inheritIO().start().waitFor();
                }
            } catch (Exception e) {
                System.out.println("Erro ao limpar a tela: " + e.getMessage());
            }
        }
    }
}

---

**Complementos (deixando o desafio completo e mais fácil de entender)**

### 1) Como corrigir o problema de exceção na idade e no peso
O problema acontece porque `nextInt()` e `nextFloat()` quebram o programa se o usuário digitar texto (ex: “dez”, “abc”).

A solução mais simples e robusta é:
- ler sempre como **String** (`nextLine()`)
- tentar converter com `Integer.parseInt(...)` e `Float.parseFloat(...)`
- se der erro, mostrar mensagem e **pedir de novo** (loop)

Isso garante que o usuário só avança quando digita um valor válido.

### 2) Novas opções do menu (funcionalidades do desafio)
Você vai adicionar novos itens no menu e novos `case` no `switch`:

- **4. Exibir a QTDE de Pessoas** → mostrar o valor do `contador`
- **5. Exibir a Pessoa com a Menor Idade** → percorrer o vetor e achar o menor
- **6. Exibir a Pessoa com o Maior Peso** → percorrer o vetor e achar o maior
- **7. Contar QTDE de Pessoas acima de Peso** → ler um peso limite e contar quantos `>=`

> Observação importante: o seu `contador` já representa “quantas pessoas existem”, porque ele vai aumentando a cada cadastro e também aumenta quando carrega do arquivo.

---

**Complemento (código com as alterações do desafio implementadas, mantendo o original acima intacto)**

    import java.io.FileReader;
    import java.io.FileWriter;
    import java.io.IOException;
    import java.io.BufferedReader;
    import java.io.BufferedWriter;
    import java.io.FileNotFoundException;
    import java.util.*;

    public class App {
        static Scanner teclado = new Scanner(System.in);

        static String CAMINHO_ARQUIVO = "dados.txt";
        static int TAMANHO_MAXIMO = 50;

        static String[] nomes = new String[TAMANHO_MAXIMO];
        static int[] idades = new int[TAMANHO_MAXIMO];
        static float[] pesos = new float[TAMANHO_MAXIMO];

        static int contador = 0;
        static boolean limparTela = true;

        public static void main(String[] args) {
            int opcao;

            carregarDados();

            do {
                limparTela();
                opcao = lerOpcaoMenu();
                processarOpcaoMenu(opcao);
            } while (opcao != 3);

            teclado.close();
        }

        static void processarOpcaoMenu(int opcao) {
            switch (opcao) {
                case 1:
                    adicionarDados();
                    break;

                case 2:
                    limparTela();
                    mostrarDados();
                    limparTela = false;
                    break;

                case 3:
                    limparTela();
                    salvarDados();
                    System.out.println("Encerrando...");
                    break;

                case 4:
                    limparTela();
                    exibirQtdePessoas();
                    limparTela = false;
                    break;

                case 5:
                    limparTela();
                    exibirPessoaMenorIdade();
                    limparTela = false;
                    break;

                case 6:
                    limparTela();
                    exibirPessoaMaiorPeso();
                    limparTela = false;
                    break;

                case 7:
                    limparTela();
                    contarPessoasAcimaDePeso();
                    limparTela = false;
                    break;

                default:
                    System.out.println("Opção inválida. Tente novamente.");
            }
        }

        static void adicionarDados() {
            limparTela = true;
            limparTela();

            if (contador >= TAMANHO_MAXIMO) {
                System.out.println("Limite de dados atingido! Não é possível adicionar mais.");
                return;
            }

            System.out.print("Digite o nome: ");
            nomes[contador] = teclado.nextLine();

            // Leitura segura (não fecha o app se o usuário digitar texto)
            idades[contador] = lerInteiroSeguro("Digite a idade: ");
            pesos[contador] = lerFloatSeguro("Digite o peso (em kg): ");

            contador++;
        }

        static int lerOpcaoMenu() {
            System.out.println("\n############## Menu ##############\n");
            System.out.println("1. Adicionar dados");
            System.out.println("2. Mostrar dados");
            System.out.println("3. Sair");
            System.out.println("4. Exibir a QTDE de Pessoas");
            System.out.println("5. Exibir a Pessoa com a Menor Idade");
            System.out.println("6. Exibir a Pessoa com o Maior Peso");
            System.out.println("7. Contar QTDE de Pessoas acima de Peso");

            return lerInteiroSeguro("\nEscolha uma opção: ");
        }

        // ========= NOVAS FUNÇÕES DO DESAFIO =========

        static void exibirQtdePessoas() {
            System.out.println("\nQTDE de pessoas cadastradas: " + contador);
        }

        static void exibirPessoaMenorIdade() {
            if (contador == 0) {
                System.out.println("Nenhum dado disponível.");
                return;
            }

            int menorIdade = Integer.MAX_VALUE;
            String nomeMenorIdade = "";

            for (int i = 0; i < contador; i++) {
                if (idades[i] < menorIdade) {
                    menorIdade = idades[i];
                    nomeMenorIdade = nomes[i];
                }
            }

            System.out.println("\nPessoa com a menor idade: " + nomeMenorIdade);
            System.out.println("Idade: " + menorIdade);
        }

        static void exibirPessoaMaiorPeso() {
            if (contador == 0) {
                System.out.println("Nenhum dado disponível.");
                return;
            }

            float maiorPeso = Float.MIN_VALUE;
            String nomeMaiorPeso = "";

            for (int i = 0; i < contador; i++) {
                if (pesos[i] > maiorPeso) {
                    maiorPeso = pesos[i];
                    nomeMaiorPeso = nomes[i];
                }
            }

            System.out.println("\nPessoa com o maior peso: " + nomeMaiorPeso);
            System.out.printf("Peso: %.2f kg%n", maiorPeso);
        }

        static void contarPessoasAcimaDePeso() {
            if (contador == 0) {
                System.out.println("Nenhum dado disponível.");
                return;
            }

            float pesoMinimo = lerFloatSeguro("Informe o peso mínimo (kg) para busca: ");

            int qtde = 0;
            for (int i = 0; i < contador; i++) {
                if (pesos[i] >= pesoMinimo) {
                    qtde++;
                }
            }

            System.out.println("\nQTDE de pessoas com peso maior ou igual a " + pesoMinimo + " kg: " + qtde);
        }

        // ========= LEITURAS SEGURAS (EVITAM FECHAR O PROGRAMA) =========

        static int lerInteiroSeguro(String mensagem) {
            int valor = 0;
            boolean leituraComProblema = true;

            do {
                try {
                    System.out.print(mensagem);
                    String entrada = teclado.nextLine().trim();
                    valor = Integer.parseInt(entrada);
                    leituraComProblema = false;
                } catch (Exception e) {
                    System.out.println("Valor inválido. Digite um número inteiro (ex: 10).");
                }
            } while (leituraComProblema);

            return valor;
        }

        static float lerFloatSeguro(String mensagem) {
            float valor = 0f;
            boolean leituraComProblema = true;

            do {
                try {
                    System.out.print(mensagem);
                    String entrada = teclado.nextLine().trim();

                    // permite digitar 70,5 ou 70.5
                    entrada = entrada.replace(",", ".");

                    valor = Float.parseFloat(entrada);
                    leituraComProblema = false;
                } catch (Exception e) {
                    System.out.println("Valor inválido. Digite um número (ex: 70,5).");
                }
            } while (leituraComProblema);

            return valor;
        }

        // ========= RESTO DO CÓDIGO (ARQUIVO / IMPRESSÃO / TELA) =========

        static void carregarDados() {
            FileReader arquivo = null;
            BufferedReader bufferLeitura = null;

            try {
                arquivo = new FileReader(CAMINHO_ARQUIVO);
                bufferLeitura = new BufferedReader(arquivo);
                String linha;

                linha = bufferLeitura.readLine();

                while (linha != null) {
                    String[] campos = linha.split(";");
                    if (campos.length == 3 && contador < TAMANHO_MAXIMO) {
                        nomes[contador] = campos[0];
                        idades[contador] = Integer.parseInt(campos[1]);
                        pesos[contador] = Float.parseFloat(campos[2]);
                        contador++;
                    }
                    linha = bufferLeitura.readLine();
                }

            } catch (FileNotFoundException e) {
                System.out.println("Arquivo não encontrado. Um novo será criado ao salvar.");
            } catch (IOException e) {
                System.out.println("Erro ao carregar os dados: " + e.getMessage());
            } catch (NumberFormatException e) {
                System.out.println("Erro nos dados do arquivo: formato inválido.");
            } finally {
                try {
                    if (bufferLeitura != null) bufferLeitura.close();
                    if (arquivo != null) arquivo.close();
                } catch (IOException e) {
                    System.out.println("Erro ao fechar o arquivo: " + e.getMessage());
                }
            }
        }

        static void mostrarDados() {
            int qtdeEspacos;

            if (contador == 0) {
                System.out.println("Nenhum dado disponível.");
                return;
            }

            System.out.println("\nNome                Idade               Peso");
            System.out.println("----------------------------------------------------------");

            for (int i = 0; i < contador; i++) {

                // (extra) nome ajustado para manter a coluna alinhada
                String nomeAjustado = ajustarNomeColuna(nomes[i]);

                System.out.print(nomeAjustado);
                qtdeEspacos = (20 - nomeAjustado.length());
                System.out.print(gerarEspacos(qtdeEspacos));

                System.out.print(idades[i]);
                qtdeEspacos = (20 - String.valueOf(idades[i]).length());
                System.out.print(gerarEspacos(qtdeEspacos));

                System.out.println(pesos[i]);
            }
        }

        static void salvarDados() {
            BufferedWriter gravador = null;

            try {
                gravador = new BufferedWriter(new FileWriter(CAMINHO_ARQUIVO));

                for (int i = 0; i < contador; i++) {
                    gravador.write(nomes[i] + ";" + idades[i] + ";" + pesos[i]);
                    gravador.newLine();
                }

                System.out.println("Dados salvos no arquivo.");
            } catch (IOException e) {
                System.out.println("Erro ao salvar os dados: " + e.getMessage());
            } finally {
                if (gravador != null) {
                    try {
                        gravador.close();
                    } catch (IOException e) {
                        System.out.println("Erro ao fechar o arquivo: " + e.getMessage());
                    }
                }
            }
        }

        static String gerarEspacos(int qtde) {
            String espacos = "";

            if (qtde < 0) qtde = 0;

            for (int i = 0; i < qtde; i++) {
                espacos += " ";
            }

            return espacos;
        }

        // (extra) se o nome tiver mais de 19 caracteres, corta e coloca "..."
        static String ajustarNomeColuna(String nome) {
            if (nome == null) return "";
            if (nome.length() > 19) {
                return nome.substring(0, 16) + "...";
            }
            return nome;
        }

        static void limparTela() {
            if (limparTela) {
                try {
                    if (System.getProperty("os.name").contains("Windows")) {
                        new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                    } else {
                        new ProcessBuilder("clear").inheritIO().start().waitFor();
                    }
                } catch (Exception e) {
                    System.out.println("Erro ao limpar a tela: " + e.getMessage());
                }
            }
        }
    }

---

### Explicação rápida do que você treinou com esse desafio
- **Tratamento de exceção + repetição**: você garante a leitura correta usando `do...while` e `try/catch`.
- **Vetores paralelos**: `nomes[i]`, `idades[i]`, `pesos[i]` representam a mesma pessoa no mesmo índice.
- **Algoritmos de varredura (for)**:
  - achar menor/maior (comparando e guardando “o melhor até agora”)
  - contar ocorrências por critério (`>= pesoMinimo`)
- **Persistência em arquivo**:
  - `salvarDados()` grava em formato “nome;idade;peso”
  - `carregarDados()` lê linha por linha, dá `split(";")` e converte tipos

<!-- nav_start -->
---
Anterior: [Desafio: Gerenciador de Habitantes](../docs/129_Gerenciador_Habitantes.md) | Próximo: [Pedra, papel, tesoura com vetor](../docs/131_Pedra_Papel_Tesoura_Vetor.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

