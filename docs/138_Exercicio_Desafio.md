Exercício Desafio
O código abaixo realiza a leitura de múltiplos nomes, salarios e qtde de dependentes de uma determinada cidade.



Faça ajustes no código para ao término da impressão dos dados dos habitantes, seja impresso na tela



- A média dos salarios dos habitantes.

Exemplo: 

Média dos salários: R$ 2780,22



- A média de dependentes.

Exemplo:

Média de dependentes: 2,7 dependentes por habitante.



- O nome do habitante que tem a menor quantidade de dependentes. Além do nome imprima também a quantidade de dependentes deste habitante. Não se preocupe se existir empate na quantidade mínima de habitantes. 

Exemplo:

Habitante com a menor quantidade de dependentes: Carlos

Quantidade de dependentes do Carlos: 1



- O nome do habitante que tem o maior salário. Além do nome imprima também o valor do salário deste habitante.

Exemplo: 

Nome do habitante com maior salário: José

Valor do salário do José: R$ 4200,58



- Imprima o nome e a quantidade de dependentes dos habitantes que possuem o número de dependentes menor que a média geral de dependentes por habitante.



Exemplo:

Nome                             Qtde de Dependentes

Mário                              1

Maria                              1

Marcelo                          2

Roberto                          0



- Este código possui um problema, foi estipulado que serão 20 espaços para imprimir a coluna de nome. Se um usuário tiver mais de 20 caracteres no nome a formatação ficará incorreta. Você deve fazer uma correção na impressão do nome da seguinte forma: Se o usuário tiver mais de 19 caracteres você deverá retirar três caracteres no fim do nome e terminar com ... no nome.

Exemplo:

Rogério de Freitas Ribeiro deve ficar

Rogério de Freit...

import java.util.Scanner;

public class App {

    public static void main(String[] args) {
        Scanner teclado;
        teclado = new Scanner(System.in);     

        //declaramos e já inicializamos as 
        //variaveis com 400 posicoes vazias
        String nomes[] = new String[400];
        int numeroDeps[] = new int[400];
        float salarios[] = new float[400];
        
        //variavel utilizada para armazenar a ultima 
        //posicao preenchida do vetor
        int ultimaPosicaoGravada = 0 ;
        
        //variavel para guardar a resposta do 
        //usuario se ele deseja digitar os dados
        //de um novo habitante
        char resposta; 

        //leitura dos habitantes e gravacao na memoria (vetores)
        for (int posicaoVetor = 0; posicaoVetor < 400; posicaoVetor++) {
    
            nomes = lerNome(teclado, nomes, posicaoVetor);
            salarios = lerSalario(teclado, salarios, posicaoVetor);
            numeroDeps = lerDependentes(teclado, numeroDeps, posicaoVetor);

            System.out.print("\nDeseja entrar com dados do próximo habitante [s/n]: ");
            resposta = teclado.nextLine().toLowerCase().charAt(0);
            
            if (resposta == 'n'){
                ultimaPosicaoGravada = posicaoVetor;               
                break;
            }
        }

        imprimirDados(nomes, salarios, numeroDeps, ultimaPosicaoGravada);

        teclado.close();
    }

    static void imprimirDados(String nomes[], float salarios[], int numeroDeps[], int ultimaPosicaoGravada){
        //acessando os dados para imprimir na tela
        int qtdeEspacos;
        System.out.println("\nNome                Salario                QtdeDependentes");
        System.out.println("----------------------------------------------------------");
        
        for (int posicaoVetor = 0; posicaoVetor <= ultimaPosicaoGravada; posicaoVetor++) {
            //imprime o nome do habitante
            System.out.print(nomes[posicaoVetor]);
            
            //calcula quantos espacos sao necessarios para alinhar
            //o valor do salario na posicao da coluna salario
            qtdeEspacos = (20 - nomes[posicaoVetor].length());
            //imprime a quantidade de espacos para alinhar os salarios
            System.out.print(geraEspacos(qtdeEspacos));

            //imprime o salario
            System.out.print("R$ " + salarios[posicaoVetor]);
            //calcula quantos espacos sao necessarios para alinhar
            //a quantidade de dependentes
            qtdeEspacos = (20 - Float.toString(salarios[posicaoVetor]).length());
            //imprime os espacos
            System.out.print(geraEspacos(qtdeEspacos));

            //imprime a quantidade de dependentes
            System.out.println(numeroDeps[posicaoVetor]);
        }
    }

    static String geraEspacos(int qtde){
        String espacos = "";

        for (int i = 0; i < qtde; i++) {
            espacos += " ";
        }

        return espacos;
    }

    static String[] lerNome(Scanner teclado, String nomes[], int posicaoLivre){
        System.out.print("Digite o nome do habitante: ");
        nomes[posicaoLivre] = teclado.nextLine(); 
        return nomes;
    }

    static float[] lerSalario(Scanner teclado, float salarios[], int posicaoLivre){
        System.out.print("Digite o salario R$: ");
        salarios[posicaoLivre] = teclado.nextFloat(); 
        
        //resolve o problema da limpeza do buffer
        teclado.nextLine();

        return salarios;
    }

    static int[] lerDependentes(Scanner teclado, int numeroDeps[], int posicaoLivre){
        System.out.print("Digite a quantidade de dependentes: ");
        numeroDeps[posicaoLivre] = teclado.nextInt(); 

        //resolve o problema da limpeza do buffer
        teclado.nextLine();
        
        return numeroDeps;
    }
     
}

---

## Opção melhorada

# Exercício Desafio — Gerenciador de Habitantes

## Objetivo
Ajustar o programa para, **além de listar os habitantes**, calcular e exibir estatísticas ao final da impressão.

## Requisitos do desafio
- **Média dos salários** dos habitantes (ex.: `R$ 2780,22`)
- **Média de dependentes** por habitante (ex.: `2,7 dependentes`)
- **Habitante com menor quantidade de dependentes** (nome + quantidade)
- **Habitante com maior salário** (nome + salário)
- Listar **nome e dependentes** de quem tem **dependentes abaixo da média**
- Corrigir a **coluna de nome (20 espaços)**:
  - Se o nome tiver **mais de 19 caracteres**, deve virar: `substring(0, 16) + "..."`  
    - Ex.: `Rogério de Freitas Ribeiro` → `Rogério de Freit...`

---

## Solução (código ajustado e com impressão mais alinhada)

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            String[] nomes = new String[400];
            int[] numeroDeps = new int[400];
            float[] salarios = new float[400];

            int ultimaPosicaoGravada = 0;
            char resposta;

            for (int posicaoVetor = 0; posicaoVetor < 400; posicaoVetor++) {

                nomes = lerNome(teclado, nomes, posicaoVetor);
                salarios = lerSalario(teclado, salarios, posicaoVetor);
                numeroDeps = lerDependentes(teclado, numeroDeps, posicaoVetor);

                System.out.print("\nDeseja entrar com dados do próximo habitante [s/n]: ");
                resposta = teclado.nextLine().toLowerCase().charAt(0);

                if (resposta == 'n') {
                    ultimaPosicaoGravada = posicaoVetor;
                    break;
                }
            }

            imprimirDados(nomes, salarios, numeroDeps, ultimaPosicaoGravada);

            teclado.close();
        }

        static void imprimirDados(String[] nomes, float[] salarios, int[] numeroDeps, int ultimaPosicaoGravada) {

            // -----------------------------
            // 1) Cabeçalho da tabela
            // -----------------------------
            System.out.println();
            System.out.printf("%-20s%-20s%-20s%n", "Nome", "Salario", "QtdeDependentes");
            System.out.println("------------------------------------------------------------");

            // -----------------------------
            // 2) Acumuladores / controles
            // -----------------------------
            float somaSalarios = 0f;
            int somaDeps = 0;

            int menorDeps = Integer.MAX_VALUE;
            String nomeMenorDeps = "";

            float maiorSalario = Float.MIN_VALUE;
            String nomeMaiorSalario = "";

            int totalHabitantes = ultimaPosicaoGravada + 1;

            // -----------------------------
            // 3) Impressão + cálculo em 1ª passada
            // -----------------------------
            for (int i = 0; i <= ultimaPosicaoGravada; i++) {

                String nomeOriginal = nomes[i];
                String nomeColuna = formatarNomeColuna(nomeOriginal);

                // imprime linha (alinhada por colunas fixas)
                System.out.printf("%-20sR$ %-17.2f%-20d%n", nomeColuna, salarios[i], numeroDeps[i]);

                // acumuladores
                somaSalarios += salarios[i];
                somaDeps += numeroDeps[i];

                // menor dependentes
                if (numeroDeps[i] < menorDeps) {
                    menorDeps = numeroDeps[i];
                    nomeMenorDeps = nomeOriginal;
                }

                // maior salário
                if (salarios[i] > maiorSalario) {
                    maiorSalario = salarios[i];
                    nomeMaiorSalario = nomeOriginal;
                }
            }

            // evita divisão por zero
            if (totalHabitantes <= 0) {
                System.out.println("\nNenhum habitante foi cadastrado.");
                return;
            }

            float mediaSalarios = somaSalarios / totalHabitantes;
            float mediaDeps = (float) somaDeps / totalHabitantes;

            // -----------------------------
            // 4) Resultados finais
            // -----------------------------
            System.out.println("\n==================== RESULTADOS ====================");
            System.out.printf("Média dos salários: R$ %.2f%n", mediaSalarios);
            System.out.printf("Média de dependentes: %.1f dependentes por habitante.%n", mediaDeps);

            System.out.println("\nHabitante com a menor quantidade de dependentes: " + nomeMenorDeps);
            System.out.println("Quantidade de dependentes do " + nomeMenorDeps + ": " + menorDeps);

            System.out.println("\nNome do habitante com maior salário: " + nomeMaiorSalario);
            System.out.printf("Valor do salário do %s: R$ %.2f%n", nomeMaiorSalario, maiorSalario);

            // -----------------------------
            // 5) Abaixo da média de dependentes (2ª passada)
            // -----------------------------
            System.out.println("\nHabitantes com dependentes menor que a média:");
            System.out.printf("%-20s%s%n", "Nome", "Qtde de Dependentes");
            System.out.println("------------------------------------------");

            boolean encontrou = false;

            for (int i = 0; i <= ultimaPosicaoGravada; i++) {
                if (numeroDeps[i] < mediaDeps) {
                    encontrou = true;
                    System.out.printf("%-20s%d%n", formatarNomeColuna(nomes[i]), numeroDeps[i]);
                }
            }

            if (!encontrou) {
                System.out.println("Nenhum habitante possui dependentes abaixo da média.");
            }
        }

        // Regra do desafio:
        // - coluna "Nome" tem 20 espaços
        // - se tiver mais de 19 caracteres, vira 16 + "..." (total 19)
        static String formatarNomeColuna(String nome) {
            if (nome.length() > 19) {
                return nome.substring(0, 16) + "...";
            }
            return nome;
        }

        static String[] lerNome(Scanner teclado, String[] nomes, int posicaoLivre) {
            System.out.print("Digite o nome do habitante: ");
            nomes[posicaoLivre] = teclado.nextLine();
            return nomes;
        }

        static float[] lerSalario(Scanner teclado, float[] salarios, int posicaoLivre) {
            System.out.print("Digite o salario R$: ");
            salarios[posicaoLivre] = teclado.nextFloat();
            teclado.nextLine(); // limpar buffer
            return salarios;
        }

        static int[] lerDependentes(Scanner teclado, int[] numeroDeps, int posicaoLivre) {
            System.out.print("Digite a quantidade de dependentes: ");
            numeroDeps[posicaoLivre] = teclado.nextInt();
            teclado.nextLine(); // limpar buffer
            return numeroDeps;
        }
    }

---

<!-- nav_start -->
---
Anterior: [137 Salvando TXT](../docs/137_Salvando_TXT.md) | Proximo: [139 Introducao Banco de Dados](../docs/139_Introducao_Banco_de_Dados.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
