// QuestÃ£o 04
// Ajuste o cÃ³digo para que ele NÃƒO seja interrompido por exceÃ§Ãµes.
// Use try/catch para tratar valores invÃ¡lidos digitados pelo usuÃ¡rio e quaisquer outras exceÃ§Ãµes.

//Escreva um algoritmo que leia as dimensÃµes de um terreno (frente e lateral). 
//Leia tambÃ©m o valor do metro quadrado.
//ApÃ³s as leituras, calcule a area total do terreno e o valor do terreno com base no valor do metro quadrado.
//Caso o terreno seja um quadrado perfeito, aumente o valor do terreno em 10% pois este terreno Ã© mais valioso.
//Caso o terreno nÃ£o seja um quadrado perfeito, de um desconto no valor total de 2%.

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

            // estrutura de decisÃ£o composta
            if (frenteMts == lateralMts) { // condicao para ver se Ã© um quadrado
                // este bloco Ã© executado se a condiÃ§Ã£o (frenteMts == lateralMts) for verdadeira 
                // que o valor do terreno seja acrescido em 10%
                valorTerreno = (valorTerreno * 1.1f);
            } else { // se nao for quadrado da um desconto
                // este bloco Ã© executado se a condiÃ§Ã£o (frenteMts == lateralMts) for falsa 
                // que o valor do terreno seja reduzido em 2%
                valorTerreno = (valorTerreno * 0.98f);
            }

            System.out.printf("O valor do terreno Ã©: R$ %.2f reais%n", valorTerreno);

        } catch (InputMismatchException e) {
            System.out.println("Erro: vocÃª digitou um valor invÃ¡lido. Digite apenas nÃºmeros (inteiro para metros e decimal para valor).");
        } catch (Exception e) {
            System.out.println("Erro inesperado: ocorreu um problema durante a execuÃ§Ã£o do programa.");
            e.printStackTrace();
        } finally {
            // garante que o Scanner serÃ¡ fechado mesmo se ocorrer exceÃ§Ã£o
            teclado.close();
        }
    }
}

<!-- nav_start -->
---
Anterior: [QuestÃ£o 03](../docs/52_Questao_03.md) | Próximo: [QuestÃ£o 05](../docs/54_Questao_05.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

