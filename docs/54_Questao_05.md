// QuestÃ£o 05
// Objetivo: Ler peso (kg) e altura (m), calcular o IMC e informar a classificaÃ§Ã£o conforme OMS.
// Requisitos: usar comentÃ¡rios, try/catch e if/else.

import java.util.InputMismatchException;
import java.util.Locale;
import java.util.Scanner;

public class App {

    public static void main(String[] args) {
        // Define Locale.US para aceitar ponto como separador decimal (ex: 1.75).
        // Se vocÃª digitar com vÃ­rgula (1,75), pode dar erro dependendo do seu sistema.
        Locale.setDefault(Locale.US);

        Scanner teclado = new Scanner(System.in);

        try {
            double peso;
            double altura;
            double imc;
            String classificacao;

            System.out.print("Digite o peso (em kg): ");
            peso = teclado.nextDouble();

            System.out.print("Digite a altura (em metros): ");
            altura = teclado.nextDouble();

            // Evita divisÃ£o por zero e valores invÃ¡lidos
            if (peso <= 0 || altura <= 0) {
                System.out.println("Erro: peso e altura devem ser maiores que zero.");
                return;
            }

            // FÃ³rmula do IMC: peso / (altura * altura)
            imc = peso / (altura * altura);

            // ClassificaÃ§Ã£o do IMC segundo a OMS
            if (imc < 18.5) {
                classificacao = "Abaixo do peso";
            } else if (imc < 25.0) {
                classificacao = "Peso normal";
            } else if (imc < 30.0) {
                classificacao = "Sobrepeso";
            } else if (imc < 35.0) {
                classificacao = "Obesidade grau I";
            } else if (imc < 40.0) {
                classificacao = "Obesidade grau II";
            } else {
                classificacao = "Obesidade grau III (obesidade mÃ³rbida)";
            }

            // SaÃ­da
            System.out.printf("%nIMC calculado: %.2f%n", imc);
            System.out.println("ClassificaÃ§Ã£o: " + classificacao);

        } catch (InputMismatchException e) {
            System.out.println("Erro: valor invÃ¡lido. Digite nÃºmeros no formato correto (ex: 70.5 e 1.75).");
        } catch (Exception e) {
            System.out.println("Erro inesperado: ocorreu um problema durante a execuÃ§Ã£o.");
            e.printStackTrace();
        } finally {
            teclado.close();
        }
    }
}

<!-- nav_start -->
---
Anterior: [QuestÃ£o 04](../docs/53_Questao_04.md) | Próximo: [Teoria If Else](../docs/55_Teoria_If_Else.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

