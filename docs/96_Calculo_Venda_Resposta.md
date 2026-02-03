# Cálculo de Venda - Resposta

---

## Versão 01

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            float valorCompra;
            int codigo;
       
            valorCompra = lerValorFloat(teclado, "Digite o valor da compra: ");

            exibirMenuPagamento();

            codigo = lerValorInteiro(teclado,"Digite a opção de pagamento: ");

            System.out.println();

            switch (codigo) {
                case 1: calcPagVista(valorCompra); break;
                case 2: calcPagCreditoDesconto(valorCompra); break;
                case 3: calcPag2xSemJuros(valorCompra); break;
                case 4: calcPag4xComJuros(valorCompra); break;
                default: System.out.println("Código inválido."); break;
            }

            teclado.close();
        }

        static void calcPagVista(Float valor){
            // À vista, 8% de desconto
            float valorFinal = valor * ((100 - 8) / 100f);
            System.out.println("À vista, com 8% de desconto.");
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);
        }

        static void calcPagCreditoDesconto(float valorCompra){
            // À vista no cartão, 4% de desconto
            float valorFinal = valorCompra * ((100 - 4) / 100f);
            System.out.println("À vista no cartão, com 4% de desconto.");
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);
        }

        static void calcPag2xSemJuros(float valorCompra){
            // Em 2x, sem juros
            float valorFinal = valorCompra;
            System.out.println("Em 2x, preço normal sem juros.");
            System.out.printf("Cada parcela: R$ %.2f%n", valorFinal / 2);
        }

        static void calcPag4xComJuros(float valorCompra){
            //  Em 4x, com acréscimo de 8%
            float valorFinal = valorCompra * ((100 + 8) / 100f);
            System.out.println("Em 4x, preço acrescido de 8%.");
            System.out.printf("Cada parcela: R$ %.2f%n", valorFinal / 4);
        }


        static void exibirMenuPagamento(){
            System.out.println("\n====================================");
            System.out.println("        FORMAS DE PAGAMENTO");
            System.out.println("====================================");
            System.out.println("1 - À vista, com 8% de desconto");
            System.out.println("2 - À vista no cartão, com 4% de desconto");
            System.out.println("3 - Em 2x, preço normal sem juros");
            System.out.println("4 - Em 4x, preço acrescido de 8%\n");
        }

        static int lerValorInteiro(Scanner teclado, String mensagem){
            int valor = 0;

            try {
                System.out.print(mensagem);
                valor = teclado.nextInt();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }

            return valor;
        }

        static float lerValorFloat(Scanner teclado, String mensagem){
            float valor = 0;

            try {
                System.out.print(mensagem);
                valor = teclado.nextFloat();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }

            return valor;
        }


        static double lerValorDouble(Scanner teclado, String mensagem){
            double valor = 0;

            try {
                System.out.print(mensagem);
                valor = teclado.nextDouble();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }

            return valor;
        }
    }

---

## Versão 02

> Nesta versão, o processamento das opções de venda foi movido para um procedimento.

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            float valorCompra;
            int codigo;
       
            valorCompra = lerValorFloat(teclado, "Digite o valor da compra: ");

            exibirMenuPagamento();

            codigo = lerValorInteiro(teclado,"Digite a opção de pagamento: ");

            System.out.println();

            processarPagamento(codigo, valorCompra);

            teclado.close();
        }

        static void calcPagVista(Float valor){
            // À vista, 8% de desconto
            float valorFinal = valor * ((100 - 8) / 100f);
            System.out.println("À vista, com 8% de desconto.");
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);
        }

        static void calcPagCreditoDesconto(float valorCompra){
            // À vista no cartão, 4% de desconto
            float valorFinal = valorCompra * ((100 - 4) / 100f);
            System.out.println("À vista no cartão, com 4% de desconto.");
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);
        }

        static void calcPag2xSemJuros(float valorCompra){
            // Em 2x, sem juros
            float valorFinal = valorCompra;
            System.out.println("Em 2x, preço normal sem juros.");
            System.out.printf("Cada parcela: R$ %.2f%n", valorFinal / 2);
        }

        static void calcPag4xComJuros(float valorCompra){
            //  Em 4x, com acréscimo de 8%
            float valorFinal = valorCompra * ((100 + 8) / 100f);
            System.out.println("Em 4x, preço acrescido de 8%.");
            System.out.printf("Cada parcela: R$ %.2f%n", valorFinal / 4);
        }

        static void exibirMenuPagamento(){
            System.out.println("\n====================================");
            System.out.println("        FORMAS DE PAGAMENTO");
            System.out.println("====================================");
            System.out.println("1 - À vista, com 8% de desconto");
            System.out.println("2 - À vista no cartão, com 4% de desconto");
            System.out.println("3 - Em 2x, preço normal sem juros");
            System.out.println("4 - Em 4x, preço acrescido de 8%\n");
        }

        static int lerValorInteiro(Scanner teclado, String mensagem){
            int valor = 0;

            try {
                System.out.print(mensagem);
                valor = teclado.nextInt();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }

            return valor;
        }

        static float lerValorFloat(Scanner teclado, String mensagem){
            float valor = 0;

            try {
                System.out.print(mensagem);
                valor = teclado.nextFloat();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }

            return valor;
        }

        static double lerValorDouble(Scanner teclado, String mensagem){
            double valor = 0;

            try {
                System.out.print(mensagem);
                valor = teclado.nextDouble();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }

            return valor;
        }

        static void processarPagamento(int codigo, float valorCompra){
               switch (codigo) {
                case 1: calcPagVista(valorCompra); break;
                case 2: calcPagCreditoDesconto(valorCompra); break;
                case 3: calcPag2xSemJuros(valorCompra); break;
                case 4: calcPag4xComJuros(valorCompra); break;
                default: System.out.println("Código inválido."); break;
            }
        }
    }

---

> Mantive as duas versões originais acima **exatamente como você mandou**.  
> Abaixo vai uma **opção melhorada** com pequenos ajustes para deixar mais robusto e reaproveitável, sem mudar a lógica.

### Melhorias aplicadas (sem mudar o comportamento)

- **Remove o método `lerValorDouble()`** (não é usado nas versões).
- **Evita repetição**: cria uma função única `calcularValorFinal(...)` para desconto/acréscimo.
- **Trata erro de entrada** de forma mais segura: limpa buffer e repete a pergunta até receber valor válido.
- **Mostra valor final em todas as opções** e, quando parcelado, mostra parcelas também (organiza saída).

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            float valorCompra = lerFloatAteValido(teclado, "Digite o valor da compra: ");
            exibirMenuPagamento();
            int codigo = lerIntAteValido(teclado, "Digite a opção de pagamento: ");

            System.out.println();

            processarPagamento(codigo, valorCompra);

            teclado.close();
        }

        static void exibirMenuPagamento(){
            System.out.println("\n====================================");
            System.out.println("        FORMAS DE PAGAMENTO");
            System.out.println("====================================");
            System.out.println("1 - À vista, com 8% de desconto");
            System.out.println("2 - À vista no cartão, com 4% de desconto");
            System.out.println("3 - Em 2x, preço normal sem juros");
            System.out.println("4 - Em 4x, preço acrescido de 8%\n");
        }

        static void processarPagamento(int codigo, float valorCompra){
            switch (codigo) {
                case 1:
                    exibirPagamentoAvista(valorCompra, 0.08f, "À vista, com 8% de desconto.");
                    break;
                case 2:
                    exibirPagamentoAvista(valorCompra, 0.04f, "À vista no cartão, com 4% de desconto.");
                    break;
                case 3:
                    exibirPagamentoParcelado(valorCompra, 2, "Em 2x, preço normal sem juros.");
                    break;
                case 4:
                    exibirPagamentoParceladoComAcrescimo(valorCompra, 4, 0.08f, "Em 4x, preço acrescido de 8%.");
                    break;
                default:
                    System.out.println("Código inválido.");
                    break;
            }
        }

        // ---------- Regras de cálculo (funções) ----------

        static float aplicarDesconto(float valor, float percentualDesconto){
            return valor * (1 - percentualDesconto);
        }

        static float aplicarAcrescimo(float valor, float percentualAcrescimo){
            return valor * (1 + percentualAcrescimo);
        }

        // ---------- Exibição (procedimentos) ----------

        static void exibirPagamentoAvista(float valorCompra, float percentualDesconto, String descricao){
            float valorFinal = aplicarDesconto(valorCompra, percentualDesconto);
            System.out.println(descricao);
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);
        }

        static void exibirPagamentoParcelado(float valorCompra, int parcelas, String descricao){
            float valorFinal = valorCompra;
            System.out.println(descricao);
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);
            System.out.printf("Cada parcela (%dx): R$ %.2f%n", parcelas, (valorFinal / parcelas));
        }

        static void exibirPagamentoParceladoComAcrescimo(float valorCompra, int parcelas, float percentualAcrescimo, String descricao){
            float valorFinal = aplicarAcrescimo(valorCompra, percentualAcrescimo);
            System.out.println(descricao);
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);
            System.out.printf("Cada parcela (%dx): R$ %.2f%n", parcelas, (valorFinal / parcelas));
        }

        // ---------- Leitura robusta (funções) ----------

        static int lerIntAteValido(Scanner teclado, String mensagem){
            while (true) {
                try {
                    System.out.print(mensagem);
                    int valor = teclado.nextInt();
                    teclado.nextLine(); // limpa o \n
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Valor digitado é incorreto. Digite um número inteiro.");
                    teclado.nextLine(); // descarta entrada inválida
                } catch (Exception e) {
                    System.out.println("Erro inesperado: " + e.getMessage());
                    teclado.nextLine();
                }
            }
        }

        static float lerFloatAteValido(Scanner teclado, String mensagem){
            while (true) {
                try {
                    System.out.print(mensagem);
                    float valor = teclado.nextFloat();
                    teclado.nextLine(); // limpa o \n
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Valor digitado é incorreto. Digite um número (ex: 10.50).");
                    teclado.nextLine(); // descarta entrada inválida
                } catch (Exception e) {
                    System.out.println("Erro inesperado: " + e.getMessage());
                    teclado.nextLine();
                }
            }
        }
    }

<!-- nav_start -->
---
Anterior: [CÃ¡lculo de Venda](../docs/95_Calculo_Venda.md) | Próximo: [Lista de ExercÃ­cios](../docs/98_Lista_08.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->


