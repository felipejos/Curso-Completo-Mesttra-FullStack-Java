# Lista de Exercícios 5: Operador Ternário

> Estes exercícios não precisam ser entregues.

## Objetivo
Converter os códigos abaixo para utilizarem **operador ternário** **caso seja possível** e implementar também **try-catch** para tratar erros de entrada (ex.: usuário digitando letras em vez de números).

> Observação importante: o operador ternário é ideal quando você quer **atribuir um valor** baseado em uma condição (`variavel = condicao ? valorSeTrue : valorSeFalse;`).  
> Quando o `if/else` executa **várias ações** (vários `println`, cálculos diferentes, etc.), normalmente **não vale** transformar tudo em ternário. Aí você usa ternário apenas onde faz sentido.

---

## Código 01 — Par ou Ímpar (if → ternário + try-catch)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Ex01_ParOuImpar {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            try {
                System.out.print("Digite um número: ");
                int numero = teclado.nextInt();

                String resultado = (numero % 2 == 0) ? "Par" : "Ímpar";

                System.out.println("O número é " + resultado);

            } catch (InputMismatchException e) {
                System.out.println("Erro: você deve digitar um número inteiro.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                teclado.close();
            }
        }
    }

---

## Código 02 — Desconto (if → ternário + try-catch)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Ex02_DescontoCompra {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            try {
                System.out.print("Digite o valor da compra: ");
                double valorCompra = teclado.nextDouble();

                double desconto = (valorCompra > 300.0) ? (valorCompra * 0.10) : (valorCompra * 0.05);

                System.out.printf("Desconto aplicado: R$ %.2f%n", desconto);

            } catch (InputMismatchException e) {
                System.out.println("Erro: digite um valor numérico válido para a compra.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                teclado.close();
            }
        }
    }

---

## Código 03 — Aprovado/Reprovado (if → ternário + try-catch)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Ex03_StatusAluno {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            try {
                System.out.print("Digite a nota do aluno: ");
                int nota = teclado.nextInt();

                String status = (nota >= 70) ? "Aprovado" : "Reprovado";

                System.out.println("Status do aluno: " + status);

            } catch (InputMismatchException e) {
                System.out.println("Erro: digite um número inteiro para a nota.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                teclado.close();
            }
        }
    }

---

## Código 04 — Maior número (if → ternário + try-catch)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Ex04_MaiorNumero {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            try {
                System.out.print("Digite o primeiro número: ");
                int a = teclado.nextInt();

                System.out.print("Digite o segundo número: ");
                int b = teclado.nextInt();

                int maior = (a > b) ? a : b;

                System.out.println("Maior número: " + maior);

            } catch (InputMismatchException e) {
                System.out.println("Erro: digite apenas números inteiros.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                teclado.close();
            }
        }
    }

---

## Código 05 — Positivo vs Negativo/Zero (ternário: **parcial** + try-catch)

> Aqui o ternário **não substitui bem** o `if/else` inteiro, porque cada lado faz várias ações diferentes.  
> Mesmo assim, podemos usar ternário para decidir uma mensagem e (opcionalmente) uma variável de controle.

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Ex05_PositivoNegativoOuZero {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            try {
                System.out.print("Digite um número: ");
                int numero = teclado.nextInt();

                boolean ehPositivo = (numero > 0);

                String mensagem = ehPositivo
                        ? "O número é positivo."
                        : "O número é negativo ou zero.";

                System.out.println(mensagem);

                if (ehPositivo) {
                    System.out.println("Calculando a raiz quadrada...");
                    double raiz = Math.sqrt(numero);
                    System.out.printf("A raiz quadrada de %d é %.2f%n", numero, raiz);
                } else {
                    System.out.println("Calculando o quadrado do número...");
                    int quadrado = numero * numero;
                    System.out.printf("O quadrado de %d é %d%n", numero, quadrado);
                }

            } catch (InputMismatchException e) {
                System.out.println("Erro: digite um número inteiro válido.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                teclado.close();
            }
        }
    }

<!-- nav_start -->
---
Anterior: [Lista de ExercÃ­cios 4: Switch Case](../docs/72_Lista_Exercicios_04.md) | Próximo: [Lista de ExercÃ­cios 6 - Estruturas de DecisÃ£o](../docs/74_Lista_Exercicios_06.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

