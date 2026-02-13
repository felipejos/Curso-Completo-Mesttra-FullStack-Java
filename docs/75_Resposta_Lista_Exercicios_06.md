# Resposta: Lista de Exercícios 6

> Antes de olhar as respostas, tente você mesmo escrever os algoritmos. 🙂

---

## Vídeos com as respostas (por partes)

## Parte 1
Link: https://youtu.be/KyQwtbGtRh8  
[![Parte 1](https://img.youtube.com/vi/KyQwtbGtRh8/hqdefault.jpg)](https://youtu.be/KyQwtbGtRh8)

## Parte 2
Link: https://youtu.be/bYWTAmh3BEw  
[![Parte 2](https://img.youtube.com/vi/bYWTAmh3BEw/hqdefault.jpg)](https://youtu.be/bYWTAmh3BEw)

## Parte 3
Link: https://youtu.be/f6iUXsUsE4U  
[![Parte 3](https://img.youtube.com/vi/f6iUXsUsE4U/hqdefault.jpg)](https://youtu.be/f6iUXsUsE4U)

## Parte 4
Link: https://youtu.be/7cYKvkQu4lU  
[![Parte 4](https://img.youtube.com/vi/7cYKvkQu4lU/hqdefault.jpg)](https://youtu.be/7cYKvkQu4lU)

---

# Soluções (códigos)

## Exercício 10 — Par ou Ímpar

    //10-Faça um algoritmo para receber um número qualquer e 
    //informar na tela se é par ou ímpar.

    import java.util.Scanner;

    public class App {
        public static void main(String[] args)  {
            Scanner teclado;
            int valor;
            boolean ehImpar;

            teclado = new Scanner(System.in);

            System.out.print("Digite um valor qualquer: ");
            valor = teclado.nextInt();

            ehImpar = (valor % 2 != 0);

            if (ehImpar) {
                System.out.println("O número é ímpar.");
            } else {
                System.out.println("O número " + valor + " é par.");
            }

        }
    }

---

## Exercício — Soma de A + B é menor que C?

    import java.util.Scanner;

    public class App {
        public static void main(String[] args)  {
            Scanner teclado;
            int a, b;
            int c;

            teclado = new Scanner(System.in);

            System.out.print("Digite o primeiro valor: ");
            a = teclado.nextInt();

            System.out.print("Digite o segundo valor: ");
            b = teclado.nextInt();

            System.out.print("Digite o terceiro valor: ");
            c = teclado.nextInt();

            if (a + b < c) {
                System.out.println("A soma de A + B é menor C");
            } else {
                System.out.println("A soma de A + B não é menor C");
            }

        }
    }

---

## Exercício 3 — Par ou Ímpar (mesma lógica do exercício 10)

    //3-Faça um algoritmo para receber um número qualquer e 
    //informar na tela se é par ou ímpar.
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {
            Scanner teclado;
            int valor;
            boolean ehImpar;

            teclado = new Scanner(System.in);

            System.out.print("Digite um valor qualquer: ");
            valor = teclado.nextInt();

            ehImpar = (valor % 2 != 0);

            if (ehImpar) {
                System.out.println("O número é ímpar.");
            } else {
                System.out.println("O número " + valor + " é par.");
            }

        }
    }

---

## Exercício 7 — Somar 5 se for par, somar 8 se for ímpar

    //7-Faça um algoritmo que leia uma variável e some 5 
    //caso seja par ou some 8 caso seja ímpar,
    //imprimir o resultado desta operação. 
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {
            Scanner teclado;
            int valor, resultado;
            boolean ehImpar;

            teclado = new Scanner(System.in);

            System.out.print("Digite um valor qualquer: ");
            valor = teclado.nextInt();

            ehImpar = (valor % 2 != 0);

            if (ehImpar) {
                resultado = valor + 8;
            } else {
                resultado = valor + 5;
            }

            System.out.println("Resultado: " + resultado);

        }
    }

---

## Exercício 5 — Dobro se positivo, triplo se negativo

    //5-Encontrar o dobro de um número caso ele seja positivo 
    //e o seu triplo caso seja negativo, imprimindo o resultado. 

    import java.util.Scanner;

    public class App {
        public static void main(String[] args)  {
            Scanner teclado;
            int valor, resultado = 0;

            teclado = new Scanner(System.in);

            System.out.print("Digite um valor qualquer: ");
            valor = teclado.nextInt();

            // negativo
            if (valor < 0) {
                resultado = valor * 3;
                // positivo
            } else if (valor > 0) {
                resultado = valor * 2;
            }

            if (resultado != 0) {
                System.out.println("Resultado: " + resultado);
            }

        }
    }

---

## Exercício 4 — Se A == B soma, senão multiplica (C)

    //4-Faça um algoritmo que leia dois valores inteiros A e B se os 
    //valores forem iguais deverá se somar os dois, caso contrário 
    //multiplique A por B. Ao final de qualquer um dos cálculos 
    //deve-se atribuir o resultado para uma variável C e mostrar 
    //seu conteúdo na tela. 

    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {
            Scanner teclado;
            int a, b, c;

            teclado = new Scanner(System.in);

            System.out.print("Digite o valor de A: ");
            a = teclado.nextInt();

            System.out.print("Digite o valor de B: ");
            b = teclado.nextInt();

            if (a == b) {
                c = (a + b);
            } else {
                c = (a * b);
            }

            System.out.println("O valor de C é: " + c);
        }
    }

---

## Exercício 10 — IMC (classificação simples)

    //10-O IMC – Indice de Massa Corporal é um critério da Organização Mundial de Saúde para dar
    //uma indicação sobre a condição de peso de uma pessoa adulta. A fórmula é IMC = peso / ( altura )2

    //Elabore um algoritmo que leia o peso e a altura de um adulto e mostre sua condição de acordo
    //com a tabela abaixo.
    //IMC em adultos Condição
    //Abaixo de 18,5 Abaixo do peso
    //Entre 18,5 e 25 Peso normal
    //Entre 25 e 30 Acima do peso
    //Acima de 30 obeso 

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            float peso, altura;
            float imc;

            System.out.print("Digite a altura em metros: ");
            altura = teclado.nextFloat();

            System.out.print("Digite o peso em kgs: ");
            peso = teclado.nextFloat();

            imc = peso / (altura * altura);

            // Acima de 30 obeso
            if (imc >= 30) {
                System.out.printf("Seu IMC %.2f lhe classifica como obeso.", imc);
                // Entre 25 e 30 Acima do peso
            } else if (imc >= 25) {
                System.out.printf("Seu IMC %.2f lhe classifica como acima do peso.", imc);
                // Entre 18,5 e 25 Peso normal
            } else if (imc >= 18.5f) {
                System.out.printf("Seu IMC %.2f lhe classifica como peso normal.", imc);
                // Abaixo de 18,5 Abaixo do peso
            } else {
                System.out.printf("Seu IMC %.2f lhe classifica abaixo do peso normal.", imc);
            }

            teclado.close();
        }
    }

---

## Exercício 11 — Pagamento (tabela por opção)

    //11-Elabore um algoritmo que calcule o que deve ser pago por um produto, considerando o preço
    //normal de etiqueta e a escolha da condição de pagamento. Utilize os códigos da tabela a seguir
    //para ler qual a condição de pagamento escolhida e efetuar o cálculo adequado.

    //Código    Condição de pagamento
    //1         À vista em dinheiro ou cheque, recebe 10% de desconto
    //2         À vista no cartão de crédito, recebe 15% de desconto
    //3         Em duas vezes, preço normal de etiqueta sem juros
    //4         Em duas vezes, preço normal de etiqueta mais juros de 10% 

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            float totalCompra;
            float valorFinalCompra;

            int opcaoPagamento;

            System.out.print("Digite o valor total da compra: R$ ");
            totalCompra = teclado.nextFloat();

            System.out.println("\nCódigo  Descrição");
            System.out.println("1       À vista em dinheiro ou cheque, recebe 10% de desconto");
            System.out.println("2       À vista no cartão de crédito, recebe 15% de desconto");
            System.out.println("3       Em duas vezes, preço normal de etiqueta sem juros");
            System.out.println("4       Em três vezes, preço normal de etiqueta mais juros de 10%");
            System.out.println("");
            System.out.print("Digite a opção de pagamento: ");

            opcaoPagamento = teclado.nextInt();

            System.out.println("Valor da compra: R$ " + totalCompra);

            if (opcaoPagamento == 1) {
                System.out.print("Valor à vista com 10% de desconto: R$ ");
                valorFinalCompra = totalCompra * 0.9f;
            } else if (opcaoPagamento == 2) {
                System.out.print("Valor à vista no cartão de crédito com 15% de desconto: R$ ");
                valorFinalCompra = totalCompra * 0.85f;
            } else if (opcaoPagamento == 3) {
                System.out.print("Em 2x sem juros: R$ ");
                valorFinalCompra = totalCompra;
            } else {
                System.out.print("Em 3x com 10% de juros: R$ ");
                valorFinalCompra = totalCompra * 1.1f;
            }

            System.out.println(valorFinalCompra);

            teclado.close();
        }
    }

---

## Exercício 9 — Peso ideal (homem/mulher)

    //9-Tendo como dados de entrada a altura e o sexo de uma pessoa, construa um algoritmo que
    //calcule seu peso ideal, utilizando as seguintes fórmulas:
    // para homens: (72.7 * h) – 58;
    // para mulheres: (62.1 * h) – 44.7

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            float altura;
            int sexo;

            System.out.print("Digite a sua altura em mts: ");
            altura = teclado.nextFloat();

            System.out.println("\nDigite 1 para masculino. ");
            System.out.println("Digite 2 para feminino. ");

            System.out.print("\nDigite o seu sexo: ");
            sexo = teclado.nextInt();

            if (sexo == 1) {
                System.out.printf("Seu peso ideal: %.2f kgs", ((72.7 * altura) - 58));
            } else {
                System.out.printf("Seu peso ideal: %.2f kgs", ((62.1 * altura) - 44.7));
            }

            teclado.close();
        }
    }

---

## Exercício 12 — Conceito pela média (fórmula MA)

    //12) Escreva um algoritmo que leia o número de identificação, as 3 notas obtidas por um aluno nas
    //3 verificações e a média dos exercícios que fazem parte da avaliação, e calcule a média de
    //aproveitamento, usando a fórmula:
    //MA := (((nota1 + nota2) * 2) + (nota3 * 3) + ME)/7
    //A atribuição dos conceitos obedece a tabela abaixo. O algoritmo deve escrever o número do aluno(),
    //suas notas, a média dos exercícios, a média de aproveitamento, o conceito correspondente e a
    //mensagem 'Aprovado' se o conceito for A, B ou C, e 'Reprovado' se o conceito for D ou E.
    //Média de aproveitamento Conceito
    //>= 90 A
    //>= 75 e < 90 B
    //>= 60 e < 75 C
    //>= 40 e < 60 D
    //< 40 E 

    import java.util.Scanner;

    public class App {
        public static void main(String[] args) throws Exception {
            Scanner teclado = new Scanner(System.in);

            float prova1, prova2, prova3, trabalho;
            float notaFinal;

            System.out.print("Digite o valor da prova 1: ");
            prova1 = teclado.nextFloat();

            System.out.print("Digite o valor da prova 2: ");
            prova2 = teclado.nextFloat();

            System.out.print("Digite o valor da prova 3: ");
            prova3 = teclado.nextFloat();

            System.out.print("Digite o valor do trabalho: ");
            trabalho = teclado.nextFloat();

            notaFinal = (((prova1 + prova2) * 2) + (prova3 * 3) + trabalho) / 7;

            if (notaFinal >= 90) {
                System.out.println("Conceito A.");
            } else if (notaFinal >= 75) {
                System.out.println("Conceito B.");
            } else if (notaFinal >= 60) {
                System.out.println("Conceito C.");
            } else if (notaFinal >= 40) {
                System.out.println("Conceito D.");
            } else {
                System.out.println("Conceito E.");
            }

            teclado.close();

        }
    }

---

## Exercício 6 — Dois booleanos (ambos iguais?)

    //6-Escreva um algoritmo que lê dois valores booleanos (lógicos) 
    //e então determina se ambos são VERDADEIROS ou FALSOS.
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) throws Exception {
            Scanner teclado = new Scanner(System.in);
            boolean a, b;

            System.out.print("Digite o primeiro valor booleano: ");
            a = teclado.nextBoolean();

            System.out.print("Digite o segundo valor booleano: ");
            b = teclado.nextBoolean();

            if (a == b) {
                System.out.println("Valores igual.");
            } else {
                System.out.println("Valores diferentes.");
            }
            teclado.close();

        }
    }

---

## Exercício 8 — Ordem decrescente (versão com trocas)

    import java.util.Scanner;

    //8-Escreva um algoritmo que leia três valores inteiros e 
    //diferentes e mostre-os em ordem decrescente. 
    public class App {
        public static void main(String[] args) throws Exception {
            Scanner scanner = new Scanner(System.in);
            int a, b, c, temp;

            // Lendo os três valores
            System.out.print("Digite o primeiro valor: ");
            a = scanner.nextInt();

            System.out.print("Digite o segundo valor: ");
            b = scanner.nextInt();

            System.out.print("Digite o terceiro valor: ");
            c = scanner.nextInt();

            if (a < b) {
                temp = a;
                a = b;
                b = temp;
            }

            if (a < c) {
                temp = a;
                a = c;
                c = temp;
            }

            if (b < c) {
                temp = b;
                b = c;
                c = temp;
            }

            System.out.println("Ordem decrescente: " + a + " " + b + " " + c);

            scanner.close();

        }
    }

---

## Exercício 8 — Ordem decrescente (versão por comparações)

    import java.util.Scanner;

    //8-Escreva um algoritmo que leia três valores inteiros e 
    //diferentes e mostre-os em ordem decrescente. 
    public class App {
        public static void main(String[] args) throws Exception {
            Scanner scanner = new Scanner(System.in);
            int a, b, c;

            // Lendo os três valores
            System.out.print("Digite o primeiro valor: ");
            a = scanner.nextInt();

            System.out.print("Digite o segundo valor: ");
            b = scanner.nextInt();

            System.out.print("Digite o terceiro valor: ");
            c = scanner.nextInt();

            if (a > b && a > c && b > c) {
                System.out.println("\nOrdem decrescente: " + a + " " + b + " " + c);
            } else if (a > b && a > c && c > b) {
                System.out.println("\nOrdem decrescente: " + a + " " + c + " " + b);
            } else if (b > a && b > c && a > c) {
                System.out.println("\nOrdem decrescente: " + b + " " + a + " " + c);
            } else if (b > a && b > c && c > a) {
                System.out.println("\nOrdem decrescente: " + b + " " + c + " " + a);
            } else if (c > a && c > b && a > b) {
                System.out.println("\nOrdem decrescente: " + c + " " + a + " " + b);
            } else if (c > a && c > b && b > a) {
                System.out.println("\nOrdem decrescente: " + c + " " + b + " " + a);
            }

            scanner.close();

        }
    }

<!-- nav_start -->
---
Anterior: [74 Lista Exercicios 06](../docs/74_Lista_Exercicios_06.md) | Proximo: [76 charAt](../docs/76_charAt.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
