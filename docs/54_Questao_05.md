// Questão 05
// Objetivo: Ler peso (kg) e altura (m), calcular o IMC e informar a classificação conforme OMS.
// Requisitos: usar comentários, try/catch e if/else.

import java.util.InputMismatchException;
import java.util.Locale;
import java.util.Scanner;

public class App {

    public static void main(String[] args) {
        // Define Locale.US para aceitar ponto como separador decimal (ex: 1.75).
        // Se você digitar com vírgula (1,75), pode dar erro dependendo do seu sistema.
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

            // Evita divisão por zero e valores inválidos
            if (peso <= 0 || altura <= 0) {
                System.out.println("Erro: peso e altura devem ser maiores que zero.");
                return;
            }

            // Fórmula do IMC: peso / (altura * altura)
            imc = peso / (altura * altura);

            // Classificação do IMC segundo a OMS
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
                classificacao = "Obesidade grau III (obesidade mórbida)";
            }

            // Saída
            System.out.printf("%nIMC calculado: %.2f%n", imc);
            System.out.println("Classificação: " + classificacao);

        } catch (InputMismatchException e) {
            System.out.println("Erro: valor inválido. Digite números no formato correto (ex: 70.5 e 1.75).");
        } catch (Exception e) {
            System.out.println("Erro inesperado: ocorreu um problema durante a execução.");
            e.printStackTrace();
        } finally {
            teclado.close();
        }
    }
}
