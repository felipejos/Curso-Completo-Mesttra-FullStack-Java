DESAFIO PRIMEIRA HACKATHON
O desafio da nossa hackathon será desenvolver o jogo da velha na console em Java.



O funcionamento do jogo pode ser visto no vídeo à seguir:  https://youtu.be/wydUvY_U0NM



Abaixo temos o esqueleto da implementação que todos os grupos devem utilizar para realizar a implementação. É obrigatório a utilização do esqueleto abaixo, ficando a cargo do grupo definir como será a implementação de cada método. Para que o jogo funcione não é necessário a criação de nenhum método adicional além destes que estão descritos no esqueleto abaixo.



Cada um dos métodos estão comentados. Os comentários explicam o raciocínio de funcionamento de cada método. 



Sugestões: 

- Os membros do grupo mais avançados podem ficar no apio ajudando os mais iniciantes no entendimento do que deve ser implementado, e depois posteriormente na junção de todos os códigos em um único programa.

- Utilizem algum mecanismo de comunicação entre o grupo para controlar as demandas que precisam ser implementadas e com qual integrante está esta implementação, além do status de evolução de cada requisito. Uma sugestão é utilizar uma ferramenta parecida com o trello. Mas uma planilha no google sheets compartilhada com todos também resolve, então fica a cargo do grupo definir a melhor estratégia. 

- Definam alguma estratégia de pontos de controle ao longo da semana para acompanharem a evolução da implementação.

- Com relação à implementação, é importante que todos os membros façam a leitura da explicação de todos os métodos para entender como o código será modularizado.

- O que deverá ser entregue: Código do jogo implementado. Será definido também uma data para que cada grupo apresente as lições aprendidas na hackathon, o que deu certo, o que não funcionou tão bem, o que pode ser feito diferente para um próximo desafio como este. 



    import java.util.Random;
    import java.util.Scanner;

    public class App {
        // Estes caracteres são aceitos como caracteres para representarem
        // os jogadores. Utizado para evitar caracteres que não combinem com
        // o desenho do tabuleiro.
        final static String CARACTERES_IDENTIFICADORES_ACEITOS = "XOUC"; //U -> usuário, C -> Computador

        // Tamanho do tabuleiro 3x3. Para o primeiro nivel de dificuldade
        // considere que este valor não será alterado. 
        // Depois que você conseguir implementar o raciocionio para o tabuleiro 3x3
        // tente ajustar o código para funcionar para qualquer tamanho de tabuleiro
        final static int TAMANHO_TABULEIRO = 3;

        static char[][] tabuleiro = new char[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO];
        
        static Scanner teclado = new Scanner(System.in);

        public static void main(String[] args) {

            
            inicializarTabuleiro();

            // Definimos aqui qual é o caractere que cada jogador irá utilizar no jogo.
            //TODO 01: chame as funções obterCaractereUsuario() e obterCaractereComputador
            //para definir quais caracteres da lista de caracteres aceitos que o jogador
            //quer configurar para ele e para o computador.
            char caractereUsuario = ????;
            char caractereComputador = ????;

            // Esta variavel é utilizada para definir se o usuário começa a jogar ou não.
            // Valor true, usuario começa jogando, valor false computador começa.
            //TODO 02: obtenha o valor booleano sorteado
            boolean vezUsuarioJogar = ????;

            boolean jogoContinua;

            do {
                // controla se o jogo terminou
                jogoContinua = true;
                exibirTabuleiro();

                if (vezUsuarioJogar){
                   
                    //TODO 03: Execute a chamada processar vez do usuario

                    // Verifica se o usuario venceu
                    //TODO 04: Este if deve executar apenas se teve ganhador 
                    if ( /*TODO: esreva aqui a chamada para teveGanhador verificar se o usuário ganhou*/ ) {
                        
                        exibirTabuleiro();
                        exibirVitoriaUsuario();
                        jogoContinua = false;
                    }

                    // define que na proxima execucao do laco o jogador nao joga, ou seja, será a vez do computador
                    vezUsuarioJogar = false;
                } else {

                    //TODO 05: Execute a chamada processar vez do computador

                    // Verifica se o computador venceu
                    //TODO 06: Este if deve executar apenas se teve ganhador
                    if ( /*esreva aqui a chamada para teve ganhador*/ ) {

                        //TODO 07: Exiba que o computador ganhou
                        jogoContinua = false;
                    }

                    //TODO 08: defina qual o vaor a variavel abaixo deve possuir para que a proxima execucao do laco seja a vez do usuário
                    vezUsuarioJogar = ????;
                }
            
                //TODO 09: Este if deve executar apenas se o jogo continua E 
                //ocorreu tempate. Utilize o metodo teveEmpate()
                if ( /*escreva aqui a condicao conforme o TODO acima*/ ) {
                    exibirTabuleiro();
                    exibirEmpate();
                    jogoContinua = false;
                }
            } while (jogoContinua);

            teclado.close();
        }


        /*
         * Descrição: Utilizado para iniciar a matriz/tabuleiro com o caractere ' '
         * espaço, no início do jogo. Matrizes de char precisam ter um valor
         * diferente de '' vazio. A idéia é, se tiver ' ' espaço, a posição está
         * livre. Qualquer outro caractere presente na posição, representa o
         * caractere do jogador em questão: usuário ou computador. Um exemplo seria,
         * 'X' para usuário e 'O' para computador. Para o primeiro nível de
         * complexidade considere um tabuleiro apenas de tamanho 3x3, 3 linhas e 3
         * colunas. 
         * Nível de complexidade: 3 de 10
         */
        static void inicializarTabuleiro() {
            //TODO 10: Implementar método conforme explicação

        }

        /*
         * Descrição: Utilizado para obter no início do jogo qual o caractere que o
         * usuário quer utilizar para representar ele próprio. Este método recebe o
         * teclado para permitir que o usuário digite o caractere desejado. Faça a
         * leitura do caractere desejado pelo usuário, através do teclado, realize
         * as validações para não aceitar caracteres que não estejam definidos pela
         * constante CARACTERES_IDENTIFICADORES_ACEITOS, e retorne o caractere lido
         * através do return.
         * Nível de complexidade: 4 de 10
         */
        static char obterCaractereUsuario() {
            //TODO 11: Implementar método conforme explicação

        }

        /*
         * Descrição: Utilizado para obter no início do jogo qual o caractere que o
         * usuário quer utilizar para representar o computador. Este método recebe o
         * teclado e recebe o caractere que foi configurado para o usuário, pois o
         * usuário e o computador não podem jogar com o mesmo caractere. Por exemplo,
         * se o usuário configurou para ele o caractere X ele não pode escolher o X
         * como o caractere também para o computador. Neste método apenas os seguintes
         * caracteres definidos pela constante CARACTERES_IDENTIFICADORES_ACEITOS devem
         * ser aceitos. Lembre-se que o caractere armazenado em caractereUsuario não
         * pode ser aceito. Após realizar a leitura do caractere pelo teclado e
         * validá-lo, faça o return deste caractere.
         * Nível de complexidade: 4 de 10
         */
        static char obterCaractereComputador(char caractereUsuario) {
            //TODO 12: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para validar se a jogada do usuário é uma jogada válida.
         * Uma jogada é considerada válida quando ela está presente dentro da lista de
         * posicoesLivres. Desta forma, o método recebe a string com as posições livres,
         * além da linha e coluna jogada pelo usuário. O método verifica se a linha e
         * coluna está presente dentro da string de posições livres, se estiver retorna
         * true se não retorna false. Para descobrir se a linha e coluna esta presente
         * dentro da lista de posições livres pense em usar método contanis da string.
         * Nível de complexidade: 3 de 10
         */
        static boolean jogadaValida(String posicoesLivres, int linha, int coluna) {
            //TODO 13: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para obter do usuário a linha e a coluna que ele deseja
         * jogar. Para isto o método deve exibir um mensagem informando que o jogador
         * deve digitar a linha e a coluna separados por um espaço. O método deve
         * realizar as validações necessárias para os casos do usuário não digitar
         * dois valores e também para o caso do usuário não digitar números.
         * O método deve garantir que o usuário digite os valores conforme solicitado
         * e devolva os valores lidos somente quando estes atenderam as regras.
         * Após a leitura dos valores de linha e coluna, o método deve retornar os
         * valores já no formato de índice, ou seja, no tabuleiro exibimos para o
         * usuário linha 1, linha 2, linha 3, coluna 1, coluna 2 e coluna 3. O
         * usuário digita os valores neste formato, no entanto o método ao retonar
         * os valores deve ajustar a linha 1 para o índice 0, a linha 2 para o índice
         * 1 e assim sucessivamente, da mesma forma que as colunas.
         * Após a validação e ajuste dos índices, o método deve verificar se a jogada
         * do usuário está presente na lista de posicoesLivres que ele recebeu como
         * parametro. Para isto, o método faz a chamada ao método jogadaValida()
         * para determinar se a jogada é aceita. Se a jogada não for aceita, é exibido
         * uma mensagem informando que a jogada não é permitida e reinicia o processo de
         * leitura de uma nova jogada. Se a jogada for aceita deve devolver os
         * valores no formato de um vetor de inteiro de duas posições. No índice 0 deste
         * vetor, deve ser armazenado o valor da linha jogada pelo usuário e no índice 1
         * do vetor, deve ser armazenado a coluna jogada pelo usuário.
         * Nível de complexidade: 5 de 10
         */
        static int[] obterJogadaUsuario(String posicoesLivres, Scanner teclado) {
            //TODO 14: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para obter do computador a linha e a coluna sorteada.
         * Para isto o método utiliza as posições livres que ele recebeu como parametro.
         * Como as posições livres estão no formato de string, uma sugestão é conveter a
         * lista de pares linhacoluna que estão separados por ; em um vetor de String.
         * Pense em utilizar o método split. A conversão para um vetor de string será
         * útil para o próximo passo que é sortear uma posição livre.
         * Para sortear uma das posições no vetor de posições livres, utilize o método
         * random.nextInt() para sortear um número que esteja no intervalo de 0 até a
         * quantidade de posições no vetor de posições livres. Pesquise pelo método
         * random.nextInt() na internet para entender como ele funciona.
         * Após o random sortear um número, utilize este número como o valor da posição
         * do índice para acessar a jogada dentro do vetor de jogadas livres.
         * Ao realizar este procedimento você terá uma jogada no formato xy onde x é
         * a linha livre e y a coluna livre. Como o método obterJogadaComputador
         * precisa devolver um vetor de inteiro é necessário converter esta string para
         * um vetor de inteiro. Utilize para isto o método
         * converterJogadaStringParaVetorInt(). Após a conversão, devolva o vetor de
         * inteiro através do comando return. Para o nível de complexidade inicial,
         * com esta implementação o computador não terá "inteligência" para se defender
         * e nem para tentar ganhar.
         * Nível de complexidade: 6 de 10
         */
        static int[] obterJogadaComputador(String posicoesLivres, Scanner teclado) {
            //TODO 15: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para converter uma jogada no formato xy (linha/coluna)
         * de string para um vetor de int. Para isto, este método recebe a jogada no
         * formato string e deve colocar o valor de x dentro do índice 0 do vetor de
         * inteiro e deve colocar o valor de y dentro do índice 1 do vetor de inteiro.
         * Após a construção do vetor de inteiro retorne este vetor com o comando
         * return.
         * Nível de complexidade: 4 de 10
         */
        static int[] converterJogadaStringParaVetorInt(String jogada) {
            //TODO 16: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para realizar as ações necessárias para processar a vez
         * do usuário jogar. Este método deve exibir uma mensagem que é a vez do usuário
         * jogar. Este método é encarregado de obter a jogada do usuário através do
         * método obterJogadaUsuario, depois realizar a atualização do tabuleiro através
         * do método atualizaTabuleiro. Lembre-se que para chamar o método obterJogadaUsuario
         * é necessário saber quais posições estão livres
         * Nível de complexidade: 5 de 10
         */
        static void processarVezUsuario(char caractereUsuario) {
            //TODO 17: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para realizar as ações necessárias para processar a vez
         * do computador jogar. Este método é encarregado de obter a jogada do
         * computador através do método obterJogadaComputador, depois realizar a
         * atualização do tabuleiro através do método atualizaTabuleiro. 
         * Lembre-se que para chamar o método obterJogadaUsuario
         * é necessário saber quais posições estão livres 
         * Nível de complexidade: 5 de 10 se o computador for jogar aleatoriamente
         * Nível de complexidade: 8 de 10 se o computador for jogar sempre para se defender
         * Nível de complexidade: 10 de 10 se o computador for jogar para ganhar
         */
        static void processarVezComputador(char caractereComputador) {
            //TODO 18: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para identificar a lista de posições livres no
         * tabuleiro. Esta lista é uma string no formato xy. Onde x é a linha e y a
         * coluna. Se existir mais de uma posição livre, teremos uma lista de valores xy
         * separados por ; exemplo: 00;01;20; Neste exemplo as posições linha 0 e
         * coluna 0; linha 0 e coluna 1; linha 2 e coluna 0 estão livres.
         * Lembre-se que os índices nas matrizes iniciam em 0. Para o primeiro nível
         * de complexidade considere um tabuleiro apenas de tamanho 3x3, 3 linhas e 3
         * colunas. Depois de montar a string retorne a mesma através do comando return
         * Nível de complexidade: 5 de 10
         */
        static String retornarPosicoesLivres() {
            //TODO 19: Implementar método conforme explicação
        }


        /*
         * Descrição: Utilizado para verificar se o jogador identificado por
         * caractereJogador ganhou o jogo. No jogo da velha um usuário ganha
         * quando ele completa uma linha ou uma coluna ou uma diagonal. Assim
         * este método verifica todas as possibilidades. No entanto, este método
         * utiliza outros métodos para auxiliar nesta verificação. Para identificar
         * se o usuário em questão ganhou na linha, é invocado o método
         * teveGanhadorLinha(), para identificar na coluna é invocado o método
         * teveGanhadorColuna(), para identificar na diagonal principal é invocado
         * o método teveGanhadorDiagonalPrincipal() e para identificar na diagonal
         * secundária é utilizado o método teveGanhadorDiagonalSecundaria(). Se
         * o pelo menos um destes métodos retornar verdadeiro, o método teveGanhador
         * retorna true, caso contrário retorna false
         * Nível de complexidade: 4 de 10 se o tabuleiro for fixo 3x3
         * Nível de complexidade: 8 de 10 se o tabuleiro dinâmico 
         */
        static boolean teveGanhador(char caractereJogador) {
            //TODO 20: Implementar método conforme explicação
        }

        /*
         * Descrição: Todos os métodos abaixo, teveGanhador... funcionam da mesma forma.
         * Recebem como parametro o tabuleiro e o caractereJogador. Cada um dos métodos
         * verificam no tabuleiro se o caractere do jogador está presente em todas as
         * posições, ou seja, o método teveGanhadorLinha verifica em todas as posicoes
         * de uma determinada linha se elas estão preenchidas com o caractere informado
         * no caractereJogador. Se estiver presente retorna true, caso contrário retorna
         * false.
         * Nível de complexidade: 4 de 10 se o tabuleiro for fixo 3x3
         * Nível de complexidade: 8 de 10 se o tabuleiro dinâmico 
         */
        static boolean teveGanhadorLinha(char caractereJogador) {
            //TODO 21: Implementar método conforme explicação
        }

        static boolean teveGanhadorColuna(char caractereJogador) {
            //TODO 22: Implementar método conforme explicação
        }

        static boolean teveGanhadorDiagonalPrincipal( char caractereJogador) {
            //TODO 23: Implementar método conforme explicação
        }

        static boolean teveGanhadorDiagonalSecundaria(char caractereJogador) {
            //TODO 24: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para limpar a console, para que seja exibido apenas o
         * conteúdo atual do jogo. Dica: Pesquisa na internet por "Como limpar console
         * no java ProcessBuilder"
         * Nível de complexidade: 3 de 10
         */
        static void limparTela() {
            //TODO 25: Implementar método conforme explicação        
        }

        /*
         * Descrição: Utilizado para imprimir o tabuleiro o conteúdo do tabuleiro na
         * tela. Recebe o tabuleiro como parametro e imprime o conteúdo de cada posição
         * do tabuleiro na tela. Imprimi o conteúdo no formato de uma grade. Para o
         * primeiro nível de complexidade considere um tabuleiro apenas de tamanho 3x3,
         * 3 linhas e 3 colunas.
         * Nível de complexidade: 4 de 10
         */
        static void exibirTabuleiro() {
            //TODO 26: Implementar método conforme explicação
            // execute no início deste método a chamada ao método limparTela
            // para garantir que seja exibido o tabuleiro sem nenhum conteúdo antes dele.
        }

        /*
         * Descrição: Utilizado para atualizar o tabuleiro com o caractere que
         * identifica o jogador. Este método recebe o tabuleiro, um vetor jogada com
         * duas posicoes. jogada[0] representa a linha escolhida pelo jogador. jogada[1]
         * representa a coluna escolhida pelo jogador. Os valores armazenados no vetor
         * já deve estar no formato de índice, ou seja, se jogada[0] contiver o valor
         * 1 e jogada[1] contiver o valor 2, significa que o índice/linha 1 e
         * índice/coluna 2 da matriz devem ser atualizados com o caractere informado na
         * variável caractereJogador. Depois de atualizar o tabuleiro, o mesmo deve ser
         * retornado através do comando return
         * Nível de complexidade: 3 de 10
         */
        static void atualizaTabuleiro(int[] jogada, char caractereJogador) {
            //TODO 27: Implementar método conforme explicação

        }

        /*
         * Descrição: Utilizado para exibir a frase: O computador venceu!, e uma ART
         * ASCII do computador feliz. Este método é utilizado quando é identificado que
         * o computador venceu a partida. Lembre-se que para imprimir uma contrabara \ é
         * necessário duas contra barras \\
         * Nível Complexidade: 2 de 10
         */
        static void exibirVitoriaComputador() {
            //TODO 28: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para exibir a frase: O usuário venceu!, e uma ARTE ASCII
         * do usuário feliz. Este método é utilizado quando é identificado que o usuário
         * venceu a partida. Lembre-se que para imprimir uma contrabara \ é necessário
         * duas contra barras \\
         * Nível Complexidade: 2 de 10
         */
        static void exibirVitoriaUsuario() {
            //TODO 29: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para exibir a frase: Ocorreu empate!, e uma ARTE ASCII
         * do placar 0 X 0. Este método é utilizado quando é identificado que ocorreu
         * empate. Lembre-se que para imprimir uma contrabara \ é necessário duas contra
         * barras \\
         * Nível Complexidade: 2 de 10
         */
        static void exibirEmpate() {
            //TODO 30: Implementar método conforme explicação
        }

        /*
         * Descrição: Utilizado para analisar se ocorreu empate no jogo. Para o primeiro
         * nível de deficuldade, basta verificar se todas as posições do tabuleiro não
         * estão preenchidas com o caractere ' '. Não se preocupe se teve ganhador, não
         * é responsabilidade deste método esta análise. Sugestão: pense em utilizar a
         * função retornarPosicoesLivres. Retorne true se teve empate ou false
         * Nível de complexidade: 3 de 10
         */
        static boolean teveEmpate() {
            //TODO 31: Implementar método conforme explicação

        }

        /*
         * Descrição: Utilizado para realizar o sorteio de um valor booleano. Este
         * método deve sortear um valor entre true ou false. Este valor será
         * utilizado para identificar quem começa a jogar. Dica: pesquise sobre
         * o método random.nextBoolean() na internet. Após ralizar o sorteio o 
         * método deve retornar o valor sorteado.
         * Nível de complexidade: 3 de 10
         */
        static boolean sortearValorBooleano() {
            //TODO 32: Implementar método conforme explicação
        }


    }

---

## Opção melhorada

### Visão geral do que você precisa implementar (sem criar métodos novos)
O esqueleto já está **bem modularizado**. Na prática, seu jogo vai funcionar assim:

1) **Inicializa tabuleiro** com espaços `' '`  
2) **Usuário escolhe um caractere** (ex: X) e **computador escolhe outro** (ex: O)  
3) **Sorteia quem começa** (`true` usuário, `false` computador)  
4) Loop do jogo:
   - mostra tabuleiro
   - jogador da vez faz uma jogada válida
   - atualiza tabuleiro
   - verifica vitória
   - se ninguém ganhou, verifica empate
   - troca a vez

A graça do desafio é: **garantir jogadas válidas** e **detectar vitória/empate**.

---

## Checklist rápido por TODO (o que cada um deve fazer)

### TODO 01 / TODO 02 (main)
- `caractereUsuario = obterCaractereUsuario();`
- `caractereComputador = obterCaractereComputador(caractereUsuario);`
- `vezUsuarioJogar = sortearValorBooleano();`

### TODO 03 e TODO 05 (vez do usuário / vez do computador)
- `processarVezUsuario(caractereUsuario);`
- `processarVezComputador(caractereComputador);`

### TODO 04 e TODO 06 (verificação de vitória)
- usuário ganhou:
  - `if (teveGanhador(caractereUsuario)) { ... }`
- computador ganhou:
  - `if (teveGanhador(caractereComputador)) { ... }`

### TODO 07 (computador venceu)
- `exibirTabuleiro();`
- `exibirVitoriaComputador();`

### TODO 08 (trocar vez pro usuário)
- `vezUsuarioJogar = true;`

### TODO 09 (empate)
- condição típica:
  - `if (jogoContinua && teveEmpate()) { ... }`

---

## Implementações sugeridas (método por método)

### TODO 10 — inicializarTabuleiro()
Objetivo: preencher toda posição com `' '` (espaço).

    static void inicializarTabuleiro() {
        for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
            for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
                tabuleiro[i][j] = ' ';
            }
        }
    }

---

### TODO 11 — obterCaractereUsuario()
Objetivo: ler um caractere do usuário e validar se está em `CARACTERES_IDENTIFICADORES_ACEITOS`.

Regras boas:
- aceitar minúsculo e transformar em maiúsculo
- repetir até ser válido

    static char obterCaractereUsuario() {
        char c;

        do {
            System.out.println("Escolha seu caractere (" + CARACTERES_IDENTIFICADORES_ACEITOS + "): ");
            String entrada = teclado.nextLine().trim().toUpperCase();

            if (entrada.isEmpty()) {
                System.out.println("Digite pelo menos 1 caractere.");
                continue;
            }

            c = entrada.charAt(0);

            if (CARACTERES_IDENTIFICADORES_ACEITOS.indexOf(c) == -1) {
                System.out.println("Caractere inválido. Use apenas: " + CARACTERES_IDENTIFICADORES_ACEITOS);
                continue;
            }

            // impede escolher U e C se vocês quiserem deixar só X e O (opcional)
            // se não for opcional, ignore esse trecho.

            return c;

        } while (true);
    }

---

### TODO 12 — obterCaractereComputador(char caractereUsuario)
Objetivo: mesma validação, porém **não pode ser igual ao do usuário**.

    static char obterCaractereComputador(char caractereUsuario) {
        char c;

        do {
            System.out.println("Escolha o caractere do computador (" + CARACTERES_IDENTIFICADORES_ACEITOS + "): ");
            String entrada = teclado.nextLine().trim().toUpperCase();

            if (entrada.isEmpty()) {
                System.out.println("Digite pelo menos 1 caractere.");
                continue;
            }

            c = entrada.charAt(0);

            if (CARACTERES_IDENTIFICADORES_ACEITOS.indexOf(c) == -1) {
                System.out.println("Caractere inválido. Use apenas: " + CARACTERES_IDENTIFICADORES_ACEITOS);
                continue;
            }

            if (c == caractereUsuario) {
                System.out.println("O computador não pode usar o mesmo caractere do usuário.");
                continue;
            }

            return c;

        } while (true);
    }

---

### TODO 13 — jogadaValida(String posicoesLivres, int linha, int coluna)
A jogada válida se o texto `"" + linha + coluna` existir dentro de `posicoesLivres`.

    static boolean jogadaValida(String posicoesLivres, int linha, int coluna) {
        String jogada = "" + linha + coluna;
        return posicoesLivres.contains(jogada);
    }

---

### TODO 14 — obterJogadaUsuario(String posicoesLivres, Scanner teclado)
Objetivo:
- pedir: "linha coluna"
- validar se são **dois números**
- converter para índice (subtrair 1)
- validar com `jogadaValida()`
- devolver `int[]{linha, coluna}`

    static int[] obterJogadaUsuario(String posicoesLivres, Scanner teclado) {
        while (true) {
            System.out.print("Digite linha e coluna (ex: 1 3): ");
            String entrada = teclado.nextLine().trim();

            String[] partes = entrada.split("\\s+");
            if (partes.length != 2) {
                System.out.println("Entrada inválida. Digite dois valores separados por espaço.");
                continue;
            }

            int linhaDigitada;
            int colunaDigitada;

            try {
                linhaDigitada = Integer.parseInt(partes[0]);
                colunaDigitada = Integer.parseInt(partes[1]);
            } catch (Exception e) {
                System.out.println("Entrada inválida. Use apenas números.");
                continue;
            }

            // converte para índice
            int linha = linhaDigitada - 1;
            int coluna = colunaDigitada - 1;

            // valida limite
            if (linha < 0 || linha >= TAMANHO_TABULEIRO || coluna < 0 || coluna >= TAMANHO_TABULEIRO) {
                System.out.println("Jogada fora do tabuleiro. Use valores de 1 a " + TAMANHO_TABULEIRO);
                continue;
            }

            // valida se está livre
            if (!jogadaValida(posicoesLivres, linha, coluna)) {
                System.out.println("Jogada não permitida. Esta posição já está ocupada.");
                continue;
            }

            return new int[]{linha, coluna};
        }
    }

---

### TODO 15 — obterJogadaComputador(String posicoesLivres, Scanner teclado)
Objetivo: escolher aleatoriamente uma jogada livre.

    static int[] obterJogadaComputador(String posicoesLivres, Scanner teclado) {
        String[] livres = posicoesLivres.split(";");
        Random random = new Random();

        int indiceSorteado = random.nextInt(livres.length);
        String jogada = livres[indiceSorteado];

        return converterJogadaStringParaVetorInt(jogada);
    }

Observação: o parâmetro `Scanner teclado` aqui não é necessário, mas o esqueleto exige a assinatura.

---

### TODO 16 — converterJogadaStringParaVetorInt(String jogada)
Ex: "20" -> linha 2, coluna 0 (índices já são 0-based)

    static int[] converterJogadaStringParaVetorInt(String jogada) {
        int linha = Character.getNumericValue(jogada.charAt(0));
        int coluna = Character.getNumericValue(jogada.charAt(1));
        return new int[]{linha, coluna};
    }

---

### TODO 17 — processarVezUsuario(char caractereUsuario)
Objetivo:
- dizer que é a vez do usuário
- pegar posicoes livres
- obter jogada do usuário
- atualizar tabuleiro

    static void processarVezUsuario(char caractereUsuario) {
        System.out.println("\nSua vez de jogar!");
        String posicoesLivres = retornarPosicoesLivres();
        int[] jogada = obterJogadaUsuario(posicoesLivres, teclado);
        atualizaTabuleiro(jogada, caractereUsuario);
    }

---

### TODO 18 — processarVezComputador(char caractereComputador)
Objetivo:
- pegar posicoes livres
- obter jogada do computador
- atualizar tabuleiro

    static void processarVezComputador(char caractereComputador) {
        System.out.println("\nVez do computador...");
        String posicoesLivres = retornarPosicoesLivres();
        int[] jogada = obterJogadaComputador(posicoesLivres, teclado);
        atualizaTabuleiro(jogada, caractereComputador);
    }

---

### TODO 19 — retornarPosicoesLivres()
Objetivo: varrer tabuleiro e montar "00;01;20;" etc.
Dica: evite ; extra no final? Não é obrigatório, mas ajuda.

    static String retornarPosicoesLivres() {
        String livres = "";

        for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
            for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
                if (tabuleiro[i][j] == ' ') {
                    livres += "" + i + j + ";";
                }
            }
        }

        // remove o último ; se existir
        if (!livres.isEmpty()) {
            livres = livres.substring(0, livres.length() - 1);
        }

        return livres;
    }

---

### TODO 20 — teveGanhador(char caractereJogador)
Objetivo: combinar as verificações.

    static boolean teveGanhador(char caractereJogador) {
        return teveGanhadorLinha(caractereJogador)
            || teveGanhadorColuna(caractereJogador)
            || teveGanhadorDiagonalPrincipal(caractereJogador)
            || teveGanhadorDiagonalSecundaria(caractereJogador);
    }

---

### TODO 21 — teveGanhadorLinha(char caractereJogador)
Para 3x3: basta checar cada linha.

    static boolean teveGanhadorLinha(char caractereJogador) {
        for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
            boolean linhaCompleta = true;

            for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
                if (tabuleiro[i][j] != caractereJogador) {
                    linhaCompleta = false;
                    break;
                }
            }

            if (linhaCompleta) return true;
        }
        return false;
    }

---

### TODO 22 — teveGanhadorColuna(char caractereJogador)

    static boolean teveGanhadorColuna(char caractereJogador) {
        for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
            boolean colunaCompleta = true;

            for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
                if (tabuleiro[i][j] != caractereJogador) {
                    colunaCompleta = false;
                    break;
                }
            }

            if (colunaCompleta) return true;
        }
        return false;
    }

---

### TODO 23 — teveGanhadorDiagonalPrincipal(char caractereJogador)
Diagonal: (0,0) (1,1) (2,2)

    static boolean teveGanhadorDiagonalPrincipal(char caractereJogador) {
        for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
            if (tabuleiro[i][i] != caractereJogador) return false;
        }
        return true;
    }

---

### TODO 24 — teveGanhadorDiagonalSecundaria(char caractereJogador)
Diagonal: (0,2) (1,1) (2,0)

    static boolean teveGanhadorDiagonalSecundaria(char caractereJogador) {
        int j = TAMANHO_TABULEIRO - 1;

        for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
            if (tabuleiro[i][j] != caractereJogador) return false;
            j--;
        }
        return true;
    }

---

### TODO 25 — limparTela()
(igual ao que você já fez na forca)

    static void limparTela() {
        try {
            if (System.getProperty("os.name").toLowerCase().contains("win")) {
                new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
            } else {
                System.out.print("\033[H\033[2J");
                System.out.flush();
            }
        } catch (Exception e) {
            for (int i = 0; i < 50; i++) System.out.println();
        }
    }

---

### TODO 26 — exibirTabuleiro()
Regras:
- chamar `limparTela()` no começo
- desenhar grade 3x3
- opcional: mostrar numeração 1..3 para ajudar o usuário

    static void exibirTabuleiro() {
        limparTela();

        System.out.println("    1   2   3");
        for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
            System.out.print((i + 1) + " ");

            for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
                System.out.print(" " + tabuleiro[i][j] + " ");
                if (j < TAMANHO_TABULEIRO - 1) System.out.print("|");
            }
            System.out.println();

            if (i < TAMANHO_TABULEIRO - 1) {
                System.out.println("   ---+---+---");
            }
        }
    }

---

### TODO 27 — atualizaTabuleiro(int[] jogada, char caractereJogador)

    static void atualizaTabuleiro(int[] jogada, char caractereJogador) {
        int linha = jogada[0];
        int coluna = jogada[1];
        tabuleiro[linha][coluna] = caractereJogador;
    }

---

### TODO 28 / TODO 29 / TODO 30 — artes + mensagens
Aqui é estilo, mas o mínimo é imprimir a frase.

    static void exibirVitoriaComputador() {
        System.out.println("\nO computador venceu!");
        System.out.println("   (⌐■_■)  ");
    }

    static void exibirVitoriaUsuario() {
        System.out.println("\nO usuário venceu!");
        System.out.println("   \\o/  ");
        System.out.println("    |   ");
        System.out.println("   / \\  ");
    }

    static void exibirEmpate() {
        System.out.println("\nOcorreu empate!");
        System.out.println("  0  X  0 ");
    }

---

### TODO 31 — teveEmpate()
Empate: não existe mais posição livre.

Sugestão bem alinhada com o texto:
- se `retornarPosicoesLivres()` vier vazio, então deu empate.

    static boolean teveEmpate() {
        String livres = retornarPosicoesLivres();
        return livres.isEmpty();
    }

---

### TODO 32 — sortearValorBooleano()
Usar `Random.nextBoolean()`.

    static boolean sortearValorBooleano() {
        Random random = new Random();
        return random.nextBoolean();
    }

---

## “Onde o pessoal mais erra” nesse desafio (pra você ficar atento)
1) **Não limpar buffer**: aqui você já está usando `nextLine()` quase sempre, então ok.
2) **Converter para índice**: usuário digita 1..3, você precisa transformar em 0..2.
3) **Validar jogada livre**: se não fizer isso, o usuário sobrescreve a jogada do outro.
4) **Empate antes de vitória**: no loop, primeiro verifica vitória, depois empate (o esqueleto já sugere isso).
5) **Posições livres vazias**: se não tratar, `split(";")` pode quebrar (por isso é importante empate antes, ou garantir que só chama quando ainda tem livre).

---

## Extra (nível 2): computador “um pouco mais esperto” sem criar método novo
Mesmo sem criar métodos novos, você pode melhorar o `obterJogadaComputador()`:
- priorizar o centro (11)
- depois cantos (00, 02, 20, 22)
- depois aleatório

Mas primeiro, faça a versão aleatória funcionar 100%.

---

<!-- nav_start -->
---
Anterior: [134 Gerenciamento Alunos](../docs/134_Gerenciamento_Alunos.md) | Proximo: [136 Exercicios Funcoes Procedimentos](../docs/136_Exercicios_Funcoes_Procedimentos.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
