Desafio: Gerenciador de Habitantes
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

**Complementos (versão ajustada com os requisitos do desafio, mantendo o original acima intacto)**

> A ideia é: aproveitar o momento em que já estamos percorrendo os vetores em `imprimirDados(...)` para:
> - somar salários e dependentes (para médias),
> - localizar menor número de dependentes e maior salário,
> - depois imprimir o relatório final,
> - e por fim imprimir a lista de habitantes abaixo da média de dependentes.
>
> Além disso, corrigimos a formatação do nome: se tiver mais de 19 caracteres, corta e coloca `...` no final.

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado;
            teclado = new Scanner(System.in);

            String nomes[] = new String[400];
            int numeroDeps[] = new int[400];
            float salarios[] = new float[400];

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

        static void imprimirDados(String nomes[], float salarios[], int numeroDeps[], int ultimaPosicaoGravada) {

            int qtdeEspacos;

            float somaSalarios = 0f;
            int somaDependentes = 0;
            int totalHabitantes = (ultimaPosicaoGravada + 1);

            int menorDependentes = Integer.MAX_VALUE;
            String nomeMenorDependentes = "";

            float maiorSalario = Float.MIN_VALUE;
            String nomeMaiorSalario = "";

            System.out.println("\nNome                Salario                QtdeDependentes");
            System.out.println("----------------------------------------------------------");

            for (int posicaoVetor = 0; posicaoVetor <= ultimaPosicaoGravada; posicaoVetor++) {

                // ========= Correção de nome para caber em 20 espaços (19 + '...') =========
                String nomeAjustado = ajustarNomeColuna(nomes[posicaoVetor]);

                // imprime o nome do habitante (já ajustado)
                System.out.print(nomeAjustado);

                // calcula quantos espaços são necessários para alinhar
                qtdeEspacos = (20 - nomeAjustado.length());
                System.out.print(geraEspacos(qtdeEspacos));

                // imprime o salário
                System.out.print("R$ " + salarios[posicaoVetor]);

                // alinha a coluna dependentes
                qtdeEspacos = (20 - Float.toString(salarios[posicaoVetor]).length());
                System.out.print(geraEspacos(qtdeEspacos));

                // imprime dependentes
                System.out.println(numeroDeps[posicaoVetor]);

                // ========= Acumuladores para médias =========
                somaSalarios += salarios[posicaoVetor];
                somaDependentes += numeroDeps[posicaoVetor];

                // ========= Menor quantidade de dependentes =========
                if (numeroDeps[posicaoVetor] < menorDependentes) {
                    menorDependentes = numeroDeps[posicaoVetor];
                    nomeMenorDependentes = nomes[posicaoVetor];
                }

                // ========= Maior salário =========
                if (salarios[posicaoVetor] > maiorSalario) {
                    maiorSalario = salarios[posicaoVetor];
                    nomeMaiorSalario = nomes[posicaoVetor];
                }
            }

            // ========= Cálculo das médias =========
            float mediaSalarios = 0f;
            float mediaDependentes = 0f;

            if (totalHabitantes > 0) {
                mediaSalarios = somaSalarios / totalHabitantes;
                mediaDependentes = (float) somaDependentes / totalHabitantes;
            }

            // ========= Impressões finais solicitadas =========
            System.out.println("\n----------------------------------------------------------");
            System.out.printf("Média dos salários: R$ %.2f%n", mediaSalarios);
            System.out.printf("Média de dependentes: %.1f dependentes por habitante.%n", mediaDependentes);

            System.out.println("\nHabitante com a menor quantidade de dependentes: " + nomeMenorDependentes);
            System.out.println("Quantidade de dependentes do " + nomeMenorDependentes + ": " + menorDependentes);

            System.out.println("\nNome do habitante com maior salário: " + nomeMaiorSalario);
            System.out.printf("Valor do salário do %s: R$ %.2f%n", nomeMaiorSalario, maiorSalario);

            // ========= Lista de habitantes abaixo da média de dependentes =========
            System.out.println("\n\nNome                Qtde de Dependentes");
            System.out.println("--------------------------------------");

            for (int posicaoVetor = 0; posicaoVetor <= ultimaPosicaoGravada; posicaoVetor++) {
                if (numeroDeps[posicaoVetor] < mediaDependentes) {

                    String nomeAjustado = ajustarNomeColuna(nomes[posicaoVetor]);

                    System.out.print(nomeAjustado);
                    int espacos = (20 - nomeAjustado.length());
                    System.out.print(geraEspacos(espacos));

                    System.out.println(numeroDeps[posicaoVetor]);
                }
            }
        }

        // Se tiver mais de 19 caracteres, corta para 16 e adiciona "..."
        static String ajustarNomeColuna(String nome) {
            if (nome == null) return "";
            if (nome.length() > 19) {
                return nome.substring(0, 16) + "...";
            }
            return nome;
        }

        static String geraEspacos(int qtde) {
            String espacos = "";

            // garante que não vamos tentar gerar espaços com qtde negativa
            if (qtde < 0) qtde = 0;

            for (int i = 0; i < qtde; i++) {
                espacos += " ";
            }

            return espacos;
        }

        static String[] lerNome(Scanner teclado, String nomes[], int posicaoLivre) {
            System.out.print("Digite o nome do habitante: ");
            nomes[posicaoLivre] = teclado.nextLine();
            return nomes;
        }

        static float[] lerSalario(Scanner teclado, float salarios[], int posicaoLivre) {
            System.out.print("Digite o salario R$: ");
            salarios[posicaoLivre] = teclado.nextFloat();

            teclado.nextLine();
            return salarios;
        }

        static int[] lerDependentes(Scanner teclado, int numeroDeps[], int posicaoLivre) {
            System.out.print("Digite a quantidade de dependentes: ");
            numeroDeps[posicaoLivre] = teclado.nextInt();

            teclado.nextLine();
            return numeroDeps;
        }
    }

---

### Explicação (mais fácil de entender, mantendo o que você pediu)
- **Média de salários**: somamos todos os salários (`somaSalarios`) e dividimos pelo total de habitantes (`totalHabitantes`).
- **Média de dependentes**: somamos todos os dependentes (`somaDependentes`) e dividimos pelo total.
- **Menor dependentes**: guardamos o menor valor encontrado e o nome correspondente.
- **Maior salário**: guardamos o maior salário encontrado e o nome correspondente.
- **Abaixo da média**: depois de saber a média de dependentes, percorremos de novo e imprimimos quem tem `numeroDeps < mediaDependentes`.
- **Nome com mais de 19 caracteres**: cortamos o nome para **16 caracteres** e colocamos `...` para fechar em **19**.

---

<!-- nav_start -->
---
Anterior: [128 Desafio Forca](../docs/128_Desafio_Forca.md) | Proximo: [130 Armazenamento Arquivo](../docs/130_Armazenamento_Arquivo.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
