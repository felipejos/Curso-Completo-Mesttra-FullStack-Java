# Cálculo de Venda

## Enunciado
Escreva um algoritmo em Java que leia o valor de uma compra e o código de pagamento informado pelo cliente.  
Com base nesse código, o programa deverá calcular e mostrar o valor final a ser pago e, quando for o caso, o valor de cada parcela.

### Códigos de pagamento

Código | Condição de Pagamento | Regra de Cálculo
---|---|---
1 | À vista, com 8% de desconto | valor final = valor - 8%
2 | À vista no cartão, com 4% de desconto | valor final = valor - 4%
3 | Em 2x, preço normal (sem juros) | valor final = valor
4 | Em 4x, com 8% de acréscimo | valor final = valor + 8%
Outro | Código inválido | Exibir mensagem de erro

### O programa deve
- Solicitar ao usuário o valor da compra.
- Solicitar o código da forma de pagamento.
- Calcular o valor final de acordo com a opção escolhida.
- Exibir:
  - O tipo de pagamento escolhido.
  - O valor final da compra.
  - E, se houver parcelamento, o valor de cada parcela.

---

## Código original (sem funções)

    import java.util.Scanner;

    public class PagamentoCompraSemFuncao {
        public static void main(String[] args) {
            Scanner entrada = new Scanner(System.in);

            float valor, valorFinal;
            int codigo;

            System.out.print("Digite o valor da compra: ");
            valor = entrada.nextFloat();

            System.out.println("====================================");
            System.out.println("        FORMAS DE PAGAMENTO");
            System.out.println("====================================");
            System.out.println("1 - À vista, com 8% de desconto");
            System.out.println("2 - À vista no cartão, com 4% de desconto");
            System.out.println("3 - Em 2x, preço normal sem juros");
            System.out.println("4 - Em 4x, preço acrescido de 8%");

            System.out.print("Digite a opção de pagamento: ");
            codigo = entrada.nextInt();

            System.out.println();

            if (codigo == 1) {
                // À vista, 8% de desconto
                valorFinal = valor * ((100 - 8) / 100f);
                System.out.println("À vista, com 8% de desconto.");
                System.out.printf("Valor final: R$ %.2f%n", valorFinal);
            } else if (codigo == 2) {
                // À vista no cartão, 4% de desconto
                valorFinal = valor * ((100 - 4) / 100f);
                System.out.println("À vista no cartão, com 4% de desconto.");
                System.out.printf("Valor final: R$ %.2f%n", valorFinal);
            } else if (codigo == 3) {
                // Em 2x, sem juros
                valorFinal = valor;
                System.out.println("Em 2x, preço normal sem juros.");
                System.out.printf("Cada parcela: R$ %.2f%n", valorFinal / 2);
            } else if (codigo == 4) {
                // Em 4x, com acréscimo de 8%
                valorFinal = valor * ((100 + 8) / 100f);
                System.out.println("Em 4x, preço acrescido de 8%.");
                System.out.printf("Cada parcela: R$ %.2f%n", valorFinal / 4);
            } else {
                System.out.println("Código inválido.");
            }

            entrada.close();
        }
    }

---

> Mantém a mesma lógica do original, mas separa em funções para facilitar manutenção, reutilização e leitura.

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class PagamentoCompraComFuncoes {

        public static void main(String[] args) {
            Scanner entrada = new Scanner(System.in);

            float valorCompra = lerFloat(entrada, "Digite o valor da compra: ");
            int codigo = lerInt(entrada, menuPagamento() + "\nDigite a opção de pagamento: ");

            processarCompra(valorCompra, codigo);

            entrada.close();
        }

        // ==========================
        // 1) ENTRADA DE DADOS
        // ==========================

        static float lerFloat(Scanner entrada, String mensagem) {
            float valor = 0f;

            System.out.print(mensagem);

            try {
                valor = entrada.nextFloat();
            } catch (InputMismatchException e) {
                System.out.println("Erro: digite um número válido (ex: 100.50).");
            } catch (Exception e) {
                System.out.println("Erro inesperado ao ler valor: " + e.getMessage());
            }

            return valor;
        }

        static int lerInt(Scanner entrada, String mensagem) {
            int valor = 0;

            System.out.print(mensagem);

            try {
                valor = entrada.nextInt();
            } catch (InputMismatchException e) {
                System.out.println("Erro: digite um número inteiro válido.");
            } catch (Exception e) {
                System.out.println("Erro inesperado ao ler opção: " + e.getMessage());
            }

            return valor;
        }

        // ==========================
        // 2) MENU
        // ==========================

        static String menuPagamento() {
            return  "\n====================================\n" +
                    "        FORMAS DE PAGAMENTO\n" +
                    "====================================\n" +
                    "1 - À vista, com 8% de desconto\n" +
                    "2 - À vista no cartão, com 4% de desconto\n" +
                    "3 - Em 2x, preço normal sem juros\n" +
                    "4 - Em 4x, preço acrescido de 8%\n";
        }

        // ==========================
        // 3) REGRAS DE CÁLCULO
        // ==========================

        static float aplicarDesconto(float valor, float percentualDesconto) {
            return valor * (1 - (percentualDesconto / 100f));
        }

        static float aplicarAcrescimo(float valor, float percentualAcrescimo) {
            return valor * (1 + (percentualAcrescimo / 100f));
        }

        // ==========================
        // 4) PROCESSAMENTO DA COMPRA
        // ==========================

        static void processarCompra(float valorCompra, int codigoPagamento) {
            float valorFinal = 0f;
            int parcelas = 0;
            String tipoPagamento = "";

            if (codigoPagamento == 1) {
                tipoPagamento = "À vista, com 8% de desconto.";
                valorFinal = aplicarDesconto(valorCompra, 8f);

            } else if (codigoPagamento == 2) {
                tipoPagamento = "À vista no cartão, com 4% de desconto.";
                valorFinal = aplicarDesconto(valorCompra, 4f);

            } else if (codigoPagamento == 3) {
                tipoPagamento = "Em 2x, preço normal sem juros.";
                valorFinal = valorCompra;
                parcelas = 2;

            } else if (codigoPagamento == 4) {
                tipoPagamento = "Em 4x, preço acrescido de 8%.";
                valorFinal = aplicarAcrescimo(valorCompra, 8f);
                parcelas = 4;

            } else {
                exibirErroCodigoInvalido();
                return;
            }

            exibirResultado(tipoPagamento, valorFinal, parcelas);
        }

        // ==========================
        // 5) SAÍDA / EXIBIÇÃO
        // ==========================

        static void exibirResultado(String tipoPagamento, float valorFinal, int parcelas) {
            System.out.println("\n--- RESUMO DA COMPRA ---");
            System.out.println("Tipo de pagamento: " + tipoPagamento);
            System.out.printf("Valor final: R$ %.2f%n", valorFinal);

            if (parcelas > 0) {
                System.out.printf("Parcelas: %dx de R$ %.2f%n", parcelas, (valorFinal / parcelas));
            }
        }

        static void exibirErroCodigoInvalido() {
            System.out.println("\nErro: código inválido.");
            System.out.println("Escolha uma opção válida entre 1 e 4.");
        }
    }

<!-- nav_start -->
---
Anterior: [94 Resposta Lista Exercicios 07](../docs/94_Resposta_Lista_Exercicios_07.md) | Proximo: [96 Calculo Venda Resposta](../docs/96_Calculo_Venda_Resposta.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
