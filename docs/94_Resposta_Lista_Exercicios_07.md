# Resposta Lista de Exercícios 7

---

## Exercício 01

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            int numero = 0;

            numero = obterNumeroInteiro(teclado, "Informe o numero para o calculo da tabuada: ");
            
            System.out.println("\nTabuada do + e - para o numero " + numero);
            calcularSomaSubtracao(numero, 0);
            calcularSomaSubtracao(numero, 1);
            calcularSomaSubtracao(numero, 2);
            calcularSomaSubtracao(numero, 3);
            calcularSomaSubtracao(numero, 4);
            calcularSomaSubtracao(numero, 5);
            calcularSomaSubtracao(numero, 6);
            calcularSomaSubtracao(numero, 7);
            calcularSomaSubtracao(numero, 8);
            calcularSomaSubtracao(numero, 9);

            System.out.println("\nTabuada do * e / para o numero " + numero);
            calcularDivisaoMultiplicacao(numero, 0);
            calcularDivisaoMultiplicacao(numero, 1);
            calcularDivisaoMultiplicacao(numero, 2);
            calcularDivisaoMultiplicacao(numero, 3);
            calcularDivisaoMultiplicacao(numero, 4);
            calcularDivisaoMultiplicacao(numero, 5);
            calcularDivisaoMultiplicacao(numero, 6);
            calcularDivisaoMultiplicacao(numero, 7);
            calcularDivisaoMultiplicacao(numero, 8);
            calcularDivisaoMultiplicacao(numero, 9);

            teclado.close();
        }

        static void calcularSomaSubtracao(int valor1, int valor2) {
            // \t equivale a um TAB
            System.out.printf("%d + %d = %d \t\t %d - %d = %d%n", valor1, valor2, (valor1 + valor2), valor1, Math.abs(valor1 - valor2), valor2);
        }


        static void calcularDivisaoMultiplicacao(int valor1, int valor2){
            System.out.printf("%d * %d = %d",  valor1, valor2, (valor1 * valor2));
            System.out.printf("\t\t %d / %d = ", valor1, valor2);
            
            // quando o valor2 for 0 como nao existe divisao por 0 damos uma mensagem especifica
            if (valor2 != 0) 
                System.out.printf("%.2f \n", (valor1 / (float)valor2) );
            else 
                System.out.printf("não existe divisao por 0!\n");
        }

        static int obterNumeroInteiro(Scanner teclado, String mensagem){
            int numero = 0;
            System.out.print(mensagem);

            try {
                numero = teclado.nextInt();
            } catch (InputMismatchException e) {
                System.out.println("É necessário digitar um valor inteiro.");
            }

            return numero;
        }
    }

---

## Exercício 2

    // Este algoritmo calcula o aumento do salário de um funcionário em relação a sua faixa salarial. 
    // Transforme a entrada de dados em uma função obterValorFloat(), a identificação do percentual de aumento
    // em uma funcação obterPercentualAumento() e a exibição do resultado em um procedimento exibirResultado(),  
    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            // Entrada de dados

            double salarioAtual = obterValorDouble(teclado, "Informe o salário atual do colaborador: R$ ");

            double percentualAumento = obterPercentualAumento(salarioAtual);

            // Calcula o valor do aumento e o novo salário
            double valorAumento = (salarioAtual * percentualAumento);
            double salarioDepoisAumento = (salarioAtual + valorAumento);

            exibirResultado(salarioAtual, percentualAumento, valorAumento, salarioDepoisAumento);

            teclado.close();
        }

        static void exibirResultado(double salarioAtual, double percentualAumento, double valorAumento, double novoSalario){
            // Exibe os resultados
            System.out.println("\n--- Resultado do Reajuste ---");
            System.out.printf("Salário antes do reajuste: R$ %.2f%n", salarioAtual);
            System.out.printf("Percentual de aumento aplicado: %.0f%%%n", percentualAumento);
            System.out.printf("Valor do aumento: R$ %.2f%n", valorAumento);
            System.out.printf("Novo salário após o aumento: R$ %.2f%n", novoSalario);
        }

        static double obterValorDouble(Scanner teclado, String mensagem){
            double numero = 0;

            System.out.print(mensagem);

            try {
                numero = teclado.nextDouble();
            } catch (InputMismatchException e) {
                System.out.println("O valor digitado é incorreto!");
            } catch (Exception e){
                e.printStackTrace();
            }

            return numero;
        }
        
        static double obterPercentualAumento(Double salario){
            double percentualAumento;

            // Determina o percentual de aumento de acordo com o salário
            if (salario <= 280.00) {
                percentualAumento = 0.20;
            } else if (salario <= 700.00) {
                percentualAumento = 0.15;
            } else if (salario <= 1500.00) {
                percentualAumento = 0.10;
            } else {
                percentualAumento = 0.05;
            }

            return percentualAumento;
        }
    }

<!-- nav_start -->
---
Anterior: [93 CPF com Funcoes](../docs/93_CPF_com_Funcoes.md) | Proximo: [95 Calculo Venda](../docs/95_Calculo_Venda.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
