## 🧮 Calculadora de Área de Figuras Geométricas

### ✅ O que esse programa faz?
Este programa exibe um menu com 3 figuras geométricas e calcula a **área** da figura escolhida pelo usuário:

- **1 — Círculo**
- **2 — Retângulo**
- **3 — Triângulo**

Ele usa `switch case` para decidir qual cálculo executar e `try-catch` para evitar que o programa quebre caso o usuário digite algo inválido.

---

### 💻 Código (Java)

    // Calculadora de área de Figuras Geométricas

    import java.util.Scanner;
    import java.lang.Math;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            double area;

            String mensagem = "";

            int opcao = 0;

            System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");
            System.out.println("1 - Círculo");
            System.out.println("2 - Retângulo");
            System.out.println("3 - Triângulo\n");

            try {
                System.out.print("Digite o número da opção desejada: ");
                opcao = teclado.nextInt();

                switch (opcao) {
                    case 1:
                        double raio;

                        try {
                            System.out.print("Digite o valor do raio da circunferencia em metros: ");
                            raio = teclado.nextDouble();

                            area = 3.14159 * raio * raio;
                            mensagem = "Área do círculo: " + Math.round(area);

                        } catch (Exception e) {
                            System.out.println("Valor inválido para o raio.");
                        }

                        break;

                    case 2:
                        double largura, altura;

                        System.out.print("Digite a largura do retangulo: ");
                        largura = teclado.nextDouble();
                        System.out.print("Digite a altura do retangulo: ");
                        altura = teclado.nextDouble();

                        area = largura * altura;

                        mensagem = "Área do retângulo: " + area + " metros";
                        break;

                    case 3:
                        double base;

                        System.out.print("Digite a base do triângulo: ");
                        base = teclado.nextDouble();
                        System.out.print("Digite a altura do triângulo: ");
                        altura = teclado.nextDouble();

                        area = (base * altura) / 2;

                        mensagem = "Área do triângulo: " + area + " metros";
                        break;

                    default:
                        System.out.println("Opção inválida.");
                        break;
                }
            } catch (Exception e) {
                System.out.println("Opção inválida.");
            }

            System.out.println(mensagem);
            teclado.close();

<!-- nav_start -->
---
Anterior: [Exemplo de usando do charAt()](../docs/77_Exemplo_charAt.md) | Próximo: [ExcercÃ­cio Pedra Papel e Tesoura](../docs/79_Pedra_Papel_Tesoura.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

