# 🧩 Lista de Exercícios 7

---

## ✅ Questão 01

Abaixo temos um código para realizar o cálculo da tabuada de soma, subtração, multiplicação e divisão.  
Veja que foi criado um procedimento chamado calcularSomaSubtracao() que recebe dois parametros para realizar o cálculo.

Reescreva este código para implementar um procedimento chamado calcularMultiplicacaoDivisao() para evitarmos de ter que escrever tantos comandos System.out.print do mesmo formato que fizemos no calcularSomaSubtracao().

### 📌 Código (original)

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            int numero;

            System.out.print("Informe o numero para o calculo da tabuada: ");
            numero = teclado.nextInt();

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

            System.out.printf("%d * 0 = %d \t\t %d / 0  = nao existe divisao por 0%n", numero, numero * 0, numero);
            System.out.printf("%d * 1 = %d \t\t %d / 1  = %.2f%n", numero, numero * 1, numero, numero / 1.0);
            System.out.printf("%d * 2 = %d \t\t %d / 2  = %.2f%n", numero, numero * 2, numero, numero / 2.0);
            System.out.printf("%d * 3 = %d \t\t %d / 3  = %.2f%n", numero, numero * 3, numero, numero / 3.0);
            System.out.printf("%d * 4 = %d \t\t %d / 4  = %.2f%n", numero, numero * 4, numero, (float) numero / 4);
            System.out.printf("%d * 5 = %d \t\t %d / 5  = %.2f%n", numero, numero * 5, numero, numero / 5.0);
            System.out.printf("%d * 6 = %d \t\t %d / 6  = %.2f%n", numero, numero * 6, numero, numero / 6.0);
            System.out.printf("%d * 7 = %d \t\t %d / 7  = %.2f%n", numero, numero * 7, numero, numero / 7.0);
            System.out.printf("%d * 8 = %d \t\t %d / 8  = %.2f%n", numero, numero * 8, numero, numero / 8.0);
            System.out.printf("%d * 9 = %d \t\t %d / 9  = %.2f%n", numero, numero * 9, numero, numero / 9.0);

            teclado.close();
        }

        static void calcularSomaSubtracao(int valor1, int valor2) {
            // \t equivale a um TAB
            System.out.printf("%d + 9 = %d \t\t %d - 9 = %d%n", valor1, valor1 + valor2, valor1, Math.abs(valor1 - valor2));
        }
    }

---

### ✅ Solução (com o procedimento `calcularMultiplicacaoDivisao()`)

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            int numero;

            System.out.print("Informe o numero para o calculo da tabuada: ");
            numero = teclado.nextInt();

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

            calcularMultiplicacaoDivisao(numero, 0);
            calcularMultiplicacaoDivisao(numero, 1);
            calcularMultiplicacaoDivisao(numero, 2);
            calcularMultiplicacaoDivisao(numero, 3);
            calcularMultiplicacaoDivisao(numero, 4);
            calcularMultiplicacaoDivisao(numero, 5);
            calcularMultiplicacaoDivisao(numero, 6);
            calcularMultiplicacaoDivisao(numero, 7);
            calcularMultiplicacaoDivisao(numero, 8);
            calcularMultiplicacaoDivisao(numero, 9);

            teclado.close();
        }

        static void calcularSomaSubtracao(int valor1, int valor2) {
            // \t equivale a um TAB
            System.out.printf("%d + %d = %d \t\t %d - %d = %d%n",
                    valor1, valor2, (valor1 + valor2),
                    valor1, valor2, Math.abs(valor1 - valor2));
        }

        static void calcularMultiplicacaoDivisao(int valor1, int valor2) {
            int multiplicacao = valor1 * valor2;

            if (valor2 == 0) {
                System.out.printf("%d * %d = %d \t\t %d / %d = nao existe divisao por 0%n",
                        valor1, valor2, multiplicacao, valor1, valor2);
            } else {
                double divisao = valor1 / (double) valor2;
                System.out.printf("%d * %d = %d \t\t %d / %d = %.2f%n",
                        valor1, valor2, multiplicacao, valor1, valor2, divisao);
            }
        }
    }

---

## ✅ Questão 02

Este algoritmo calcula o aumento do salário de um funcionário em relação a sua faixa salarial.  
Transforme a entrada de dados em uma função obterValorDouble(), a identificação do percentual de aumento em uma funcação obterPercentualAumento() e a exibição do resultado em um procedimento exibirResultado().

### 📌 Código (original)

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            // Entrada de dados
            System.out.print("Informe o salário atual do colaborador: R$ ");
            double salarioAtual = scanner.nextDouble();

            double percentualAumento;
            
            // Determina o percentual de aumento de acordo com o salário
            if (salarioAtual <= 280.00) {
                percentualAumento = 20.0;
            } else if (salarioAtual <= 700.00) {
                percentualAumento = 15.0;
            } else if (salarioAtual <= 1500.00) {
                percentualAumento = 10.0;
            } else {
                percentualAumento = 5.0;
            }

            // Calcula o valor do aumento e o novo salário
            double valorAumento = salarioAtual * (percentualAumento / 100);
            double novoSalario = salarioAtual + valorAumento;

            // Exibe os resultados
            System.out.println("\n--- Resultado do Reajuste ---");
            System.out.printf("Salário antes do reajuste: R$ %.2f%n", salarioAtual);
            System.out.printf("Percentual de aumento aplicado: %.0f%%%n", percentualAumento);
            System.out.printf("Valor do aumento: R$ %.2f%n", valorAumento);
            System.out.printf("Novo salário após o aumento: R$ %.2f%n", novoSalario);

            scanner.close();
        }
    }

---

### ✅ Solução (com `obterValorDouble`, `obterPercentualAumento`, `exibirResultado`)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            double salarioAtual = obterValorDouble(scanner, "Informe o salário atual do colaborador: R$ ");

            double percentualAumento = obterPercentualAumento(salarioAtual);

            double valorAumento = salarioAtual * (percentualAumento / 100.0);
            double novoSalario = salarioAtual + valorAumento;

            exibirResultado(salarioAtual, percentualAumento, valorAumento, novoSalario);

            scanner.close();
        }

        static double obterValorDouble(Scanner scanner, String mensagem) {
            double valor = 0.0;

            System.out.print(mensagem);

            try {
                valor = scanner.nextDouble();
            } catch (InputMismatchException e) {
                System.out.println("Entrada inválida. Digite um número válido.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            }

            return valor;
        }

        static double obterPercentualAumento(double salarioAtual) {
            double percentualAumento;

            if (salarioAtual <= 280.00) {
                percentualAumento = 20.0;
            } else if (salarioAtual <= 700.00) {
                percentualAumento = 15.0;
            } else if (salarioAtual <= 1500.00) {
                percentualAumento = 10.0;
            } else {
                percentualAumento = 5.0;
            }

            return percentualAumento;
        }

        static void exibirResultado(double salarioAtual, double percentualAumento, double valorAumento, double novoSalario) {
            System.out.println("\n--- Resultado do Reajuste ---");
            System.out.printf("Salário antes do reajuste: R$ %.2f%n", salarioAtual);
            System.out.printf("Percentual de aumento aplicado: %.0f%%%n", percentualAumento);
            System.out.printf("Valor do aumento: R$ %.2f%n", valorAumento);
            System.out.printf("Novo salário após o aumento: R$ %.2f%n", novoSalario);
        }
    }

---

## ✅ Questão 03

Este algoritmo calcula a média final de um aluno com base nos pesos e notas de 3 provas e mais a média simples das notas dos trabalhos.  
As provas possuem os seguintes pesos respectivos: 1, 2 e 3.

Faça os ajustes necessários neste código para obter os valores inteiro e double a partir de funções lerInteiro() e lerDouble().  
Escreva uma função que retorne as strings: Aprovado, Recuperação e Reprovado.  

Regras:
- >= 6 está Aprovado.
- Abaixo de 4 pontos o aluno está reprovado
- Caso contrário o aluno está de recuperação.

Escreva a exibição dos dados como um procedimento exibirResultados() que além de exibir as atuais informações, exiba também o status do Aluno, se ele está Aparovado, Reprovado ou de Recuperação.

### 📌 Código (original)

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            // Entrada de dados
            System.out.print("Informe o código de matrícula do aluno: ");
            int numIdentificacao = scanner.nextInt();

            System.out.print("Informe a 1ª nota: ");
            double nota1 = scanner.nextDouble();

            System.out.print("Informe a 2ª nota: ");
            double nota2 = scanner.nextDouble();

            System.out.print("Informe a 3ª nota: ");
            double nota3 = scanner.nextDouble();

            System.out.print("Informe a média dos exercícios (ME): ");
            double ME = scanner.nextDouble();

            // Cálculo da média de aproveitamento
            double MA = (nota1 + (nota2 * 2) + (nota3 * 3) + ME) / 7;

            // Exibição dos resultados
            System.out.println("\n--- Resultado ---");
            System.out.println("Número de identificação: " + numIdentificacao);
            System.out.printf("Média de aproveitamento: %.2f%n", MA);

            scanner.close();
        }
    }

---

### ✅ Solução (com `lerInteiro`, `lerDouble`, `obterStatusAluno`, `exibirResultados`)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            int numIdentificacao = lerInteiro(scanner, "Informe o código de matrícula do aluno: ");

            double nota1 = lerDouble(scanner, "Informe a 1ª nota: ");
            double nota2 = lerDouble(scanner, "Informe a 2ª nota: ");
            double nota3 = lerDouble(scanner, "Informe a 3ª nota: ");
            double ME = lerDouble(scanner, "Informe a média dos exercícios (ME): ");

            double MA = (nota1 + (nota2 * 2) + (nota3 * 3) + ME) / 7.0;

            String status = obterStatusAluno(MA);

            exibirResultados(numIdentificacao, MA, status);

            scanner.close();
        }

        static int lerInteiro(Scanner scanner, String mensagem) {
            int valor = 0;

            System.out.print(mensagem);

            try {
                valor = scanner.nextInt();
            } catch (InputMismatchException e) {
                System.out.println("Entrada inválida. Digite um número inteiro.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            }

            return valor;
        }

        static double lerDouble(Scanner scanner, String mensagem) {
            double valor = 0.0;

            System.out.print(mensagem);

            try {
                valor = scanner.nextDouble();
            } catch (InputMismatchException e) {
                System.out.println("Entrada inválida. Digite um número válido (ex: 7.5).");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            }

            return valor;
        }

        static String obterStatusAluno(double mediaFinal) {
            if (mediaFinal >= 6.0) {
                return "Aprovado";
            } else if (mediaFinal < 4.0) {
                return "Reprovado";
            } else {
                return "Recuperação";
            }
        }

        static void exibirResultados(int numIdentificacao, double mediaAproveitamento, String status) {
            System.out.println("\n--- Resultado ---");
            System.out.println("Número de identificação: " + numIdentificacao);
            System.out.printf("Média de aproveitamento: %.2f%n", mediaAproveitamento);
            System.out.println("Status do aluno: " + status);
        }
    }

<!-- nav_start -->
---
Anterior: [91 Calcular Area](../docs/91_Calcular_Area.md) | Proximo: [93 CPF com Funcoes](../docs/93_CPF_com_Funcoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
