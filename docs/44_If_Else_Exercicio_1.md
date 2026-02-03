# ðŸ§© If Else: ExercÃ­cio 1

Exemplo de um exercÃ­cio que envolve o uso de uma estrutura de decisÃ£o **if/else**.

---

## ðŸ“Œ Enunciado do exercÃ­cio

    //Escreva um algoritmo que leia as dimensÃµes de um terreno (frente e lateral). 
    //Leia tambÃ©m o valor do metro quadrado.
    //ApÃ³s as leituras, calcule a area total do terreno e o valor do terreno com base no valor do metro quadrado.
    //Caso o terreno seja um quadrado perfeito, aumente o valor do terreno em 10% pois este terreno Ã© mais valioso.
    //Caso o terreno nÃ£o seja um quadrado perfeito, de um desconto no valor total de 2%.

---

## âœ… SoluÃ§Ã£o em Java

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int frenteMts, lateralMts;
            float valorMetroQuadrado, valorTerreno;

            System.out.print("Digite a metragem da frente do terreno: ");
            frenteMts = teclado.nextInt();

            System.out.print("Digite a metragem da lateral do terreno: ");
            lateralMts = teclado.nextInt();

            System.out.print("Digite o valor do metro quadrado: ");
            valorMetroQuadrado = teclado.nextFloat();

            //calculando o valor do terreno
            valorTerreno = frenteMts * lateralMts * valorMetroQuadrado;

            // estrutura de decisÃ£o composta
            if (frenteMts == lateralMts) { //condicao para ver se Ã© um quadrado
                //este bloco Ã© executado se a condiÃ§Ã£o (frenteMts == lateralMts) for verdadeira 
                //que o valor do terreno seja acrescido em 10%
                //valorTerreno = (valorTerreno * 0.1f) + valorTerreno;
                valorTerreno = (valorTerreno * 1.1f);
            } else {//se nao for quadrado da um desconto
                //este bloco Ã© executado se a condiÃ§Ã£o (frenteMts == lateralMts) for falsa 
                //valorTerreno = (valorTerreno * 0.02f) - valorTerreno;
                valorTerreno = (valorTerreno * 0.98f);
            }

            System.out.printf("O valor do terreno Ã©: R$ %.2f reais", valorTerreno);
            teclado.close();
        }
    }

<!-- nav_start -->
---
Anterior: [Operadores LÃ³gicos](../docs/43_Operadores_Logicos_2.md) | Próximo: [If Else: ExercÃ­cio 2](../docs/45_If_Else_Exercicio_2.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

