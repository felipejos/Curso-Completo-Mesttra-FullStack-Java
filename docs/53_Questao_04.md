// Questão 04
// Ajuste o código para que ele NÃO seja interrompido por exceções.
// Use try/catch para tratar valores inválidos digitados pelo usuário e quaisquer outras exceções.

//Escreva um algoritmo que leia as dimensões de um terreno (frente e lateral). 
//Leia também o valor do metro quadrado.
//Após as leituras, calcule a area total do terreno e o valor do terreno com base no valor do metro quadrado.
//Caso o terreno seja um quadrado perfeito, aumente o valor do terreno em 10% pois este terreno é mais valioso.
//Caso o terreno não seja um quadrado perfeito, de um desconto no valor total de 2%.

import java.util.InputMismatchException;
import java.util.Scanner;

public class App {

    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);

        try {
            int frenteMts, lateralMts;
            float valorMetroQuadrado, valorTerreno;

            System.out.print("Digite a metragem da frente do terreno: ");
            frenteMts = teclado.nextInt();

            System.out.print("Digite a metragem da lateral do terreno: ");
            lateralMts = teclado.nextInt();

            System.out.print("Digite o valor do metro quadrado: ");
            valorMetroQuadrado = teclado.nextFloat();

            // calculando o valor do terreno
            valorTerreno = frenteMts * lateralMts * valorMetroQuadrado;

            // estrutura de decisão composta
            if (frenteMts == lateralMts) { // condicao para ver se é um quadrado
                // este bloco é executado se a condição (frenteMts == lateralMts) for verdadeira 
                // que o valor do terreno seja acrescido em 10%
                valorTerreno = (valorTerreno * 1.1f);
            } else { // se nao for quadrado da um desconto
                // este bloco é executado se a condição (frenteMts == lateralMts) for falsa 
                // que o valor do terreno seja reduzido em 2%
                valorTerreno = (valorTerreno * 0.98f);
            }

            System.out.printf("O valor do terreno é: R$ %.2f reais%n", valorTerreno);

        } catch (InputMismatchException e) {
            System.out.println("Erro: você digitou um valor inválido. Digite apenas números (inteiro para metros e decimal para valor).");
        } catch (Exception e) {
            System.out.println("Erro inesperado: ocorreu um problema durante a execução do programa.");
            e.printStackTrace();
        } finally {
            // garante que o Scanner será fechado mesmo se ocorrer exceção
            teclado.close();
        }
    }
}
