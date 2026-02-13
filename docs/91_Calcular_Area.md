## 📐 Calcular Área Figuras Geométricas

Mesmo algoritmo do dia 23/10/2025 (Calculadora de área de Figuras Geométricas) modificado para utilizar funções e procedimentos.

---

## ✅ Código (Java)

    import java.util.InputMismatchException;
    import java.util.Scanner;
    import java.lang.Math;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int opcao = 0;
            String nome;
           
            nome = obterString(teclado, "Digite o seu nome: ");

            exibirMenu(nome); 

            try {
                opcao = obterInt(teclado, "Digite o número da opção desejada: ");

                switch (opcao) {
                    case 1:
                        calcularAreaCirculo(teclado); 
                        break;
                    case 2:
                        calcularAreRetangulo(teclado);
                        break;
                    case 3:
                        calcularAreaTriangulo(teclado);
                        break;
                    default:
                        System.out.println("Opção inválida.");
                        break;
                }
            } catch (Exception e) {
                System.out.println("Opção inválida.");
            }

            teclado.close();
        }

        static void exibirMenu(String xyz) {
            System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");

            System.out.println("Seja bem vindo, " + xyz + "!\n");

            System.out.println("1 - Círculo");
            System.out.println("2 - Retângulo");
            System.out.println("3 - Triângulo\n");
        }

        static int obterInt(Scanner teclado, String mensagem){
            int numero = 0;

            System.out.print(mensagem);

            try {
                numero = teclado.nextInt();
            } catch (InputMismatchException e) {
                System.out.println("Valor digitado é inválido.");
            }

            return numero;     
        }

        static String obterString(Scanner teclado, String mensagem){
            System.out.print(mensagem);
            try {
                return teclado.nextLine();
            } catch (Exception e) {
                System.out.println(e.getMessage());
                return "";
            }
        }

        static void calcularAreaCirculo(Scanner teclado){
            double raio;

            try {
                System.out.print("Digite o valor do raio da circunferencia em metros: ");
                raio = teclado.nextDouble();

                double area =  3.14159 * raio * raio;
                System.out.println("Área do círculo: " +  Math.round(area) + " metros");

            } catch (Exception e) {
                System.out.println("Valor inválido para o raio.");
            }
        }

        static void calcularAreRetangulo(Scanner teclado){
            double largura, altura;
                        
            System.out.print("Digite a largura do retangulo: ");
            largura = teclado.nextDouble();
            System.out.print("Digite a altura do retangulo: ");
            altura = teclado.nextDouble();

        
            System.out.println("Área do retângulo: " + largura * altura + " metros");
        }

        static void calcularAreaTriangulo(Scanner teclado){
             double base;
                        
            System.out.print("Digite a base do triângulo: ");
            base = teclado.nextDouble();
            System.out.print("Digite a altura do triângulo: ");
            double altura = teclado.nextDouble();

            System.out.println("Área do triângulo: " + (base * altura) / 2 + " metros");
        }
    }

---

## 🔎 Checklist rápido do que observar (ao estudar)
- Onde o **procedimento** é usado (ex.: `exibirMenu(...)` e os métodos `calcular...` que apenas imprimem).
- Onde a **função** retorna valor (ex.: `obterInt(...)` e `obterString(...)`).
- Como o `switch` direciona o fluxo para cada cálculo.
- Como o `try/catch` impede o programa de parar quando a entrada é inválida.

<!-- nav_start -->
---
Anterior: [90 Morangos Macas](../docs/90_Morangos_Macas.md) | Proximo: [92 Lista Exercicios 07](../docs/92_Lista_Exercicios_07.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
