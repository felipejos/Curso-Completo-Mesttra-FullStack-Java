# ðŸ§© If Else: ExercÃ­cio 2

---

## ðŸ“Œ Enunciado

    //Escreva um algoritmo que leia 4 notas de um aluno de 0 a 10.
    //Leia a quantidade de aulas que foram ministradas e a quantidade de aulas que o aluno faltou.
    //Calcule uma media simples entre as 4 notas e tambÃ©m o percentual de faltas do aluno.
    //Ao termino informe o aluno foi:
    //Reprovado por falta. PercentualFaltas >= 25
    //Aprovado. MediaNotas notas >= 6
    //RecuperaÃ§Ã£o. MediaNotas >= 3 e < 6
    //Reprovado por Nota. MediaNotas < 3

---

## âœ… VersÃ£o principal (mais eficiente)

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {      
            Scanner teclado = new Scanner(System.in);  

            float nota1, nota2, nota3, nota4;
            float media, percentualFaltas;
            int qtdeAulasDadas, qtdeFaltas;

            System.out.print("Digite a nota 1: ");
            nota1 = teclado.nextFloat();

            System.out.print("Digite a nota 2: ");
            nota2 = teclado.nextFloat();

            System.out.print("Digite a nota 3: ");
            nota3 = teclado.nextFloat();

            System.out.print("Digite a nota 4: ");
            nota4 = teclado.nextFloat();

            System.out.print("Digite a quantidade de aulas dadas: ");
            qtdeAulasDadas = teclado.nextInt();

            System.out.print("Digite a quantidade de faltas do aluno: ");
            qtdeFaltas = teclado.nextInt();

            media = (nota1 + nota2 + nota3 + nota4) / 4;

            percentualFaltas = (qtdeFaltas * 100) / qtdeAulasDadas;

            if (percentualFaltas > 25){
                //Ã© executado se a condicao (percentualFaltas > 25) for verdadeira
                System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
            }  else if (media >= 6) {
                //Ã© executado se a condicao (media >= 6) for verdadeira
                System.out.printf("Aluno aprovado, a mÃ©dia foi %.2f pontos.", media);
            } else if (media >= 4){
                // Ã© executado se a condicao (media >= 4) for verdadeira
                System.out.printf("Aluno de recuperaÃ§Ã£o, a mÃ©dia foi %.2f pontos.", media);
            } else {
                // Ã© executado se a condicao (media < 4) for verdadeira
                System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
            }  

            teclado.close();
        }
    }

---

## ðŸ”Ž Outras versÃµes (menos eficientes) â€” apenas olhando para o bloco `if/else`

### 1) VersÃ£o com condiÃ§Ãµes repetidas

    if (media >= 6 && percentualFaltas < 25) {
        //Ã© executado se a condicao (media >= 6) for verdadeira
        System.out.printf("Aluno aprovado, a mÃ©dia foi %.2f pontos.", media);
    } else if (media >= 4 && percentualFaltas < 25){
        // Ã© executado se a condicao (media >= 4) for verdadeira
        System.out.printf("Aluno de recuperaÃ§Ã£o, a mÃ©dia foi %.2f pontos.", media);
    } else if (media < 4 && percentualFaltas < 25){
        // Ã© executado se a condicao (media < 4) for verdadeira
        System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
    } else if (percentualFaltas > 25 && percentualFaltas < 25){
        //Ã© executado se a condicao (percentualFaltas > 25) for verdadeira
        System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
    }

> âš ï¸ ObservaÃ§Ã£o: esse Ãºltimo `else if` tem uma condiÃ§Ã£o impossÃ­vel  
> `percentualFaltas > 25 && percentualFaltas < 25` nunca serÃ¡ verdadeira ao mesmo tempo.

---

### 2) VersÃ£o reorganizada

    if (percentualFaltas > 25){
        //Ã© executado se a condicao (percentualFaltas > 25) for verdadeira
        System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
    }  else if (media >= 4 && media < 6) {
        // Ã© executado se a condicao (media >= 4) for verdadeira
        System.out.printf("Aluno de recuperaÃ§Ã£o, a mÃ©dia foi %.2f pontos.", media);
    } else if (media >= 6) {
        //Ã© executado se a condicao (media >= 6) for verdadeira
        System.out.printf("Aluno aprovado, a mÃ©dia foi %.2f pontos.", media);
    } else if (media < 4){
        // Ã© executado se a condicao (media < 4) for verdadeira
        System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
    }

---

### 3) VersÃ£o com `if` aninhado (mais verbosa)

    if (percentualFaltas > 25){
        //Ã© executado se a condicao (percentualFaltas > 25) for verdadeira
        System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
    }  else {
        if (media >= 6) {
            //Ã© executado se a condicao (media >= 6) for verdadeira
            System.out.printf("Aluno aprovado, a mÃ©dia foi %.2f pontos.", media);
        } else {
            if (media >= 4) {
                // Ã© executado se a condicao (media >= 4) for verdadeira
                System.out.printf("Aluno de recuperaÃ§Ã£o, a mÃ©dia foi %.2f pontos.", media);
            } else {
                if (media < 4){
                    // Ã© executado se a condicao (media < 4) for verdadeira
                    System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
                }
            }
        }
    }

<!-- nav_start -->
---
Anterior: [If Else: ExercÃ­cio 1](../docs/44_If_Else_Exercicio_1.md) | Próximo: [Desafio Jogo da Forca](../docs/46_Desafio_Jogo_Forca.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

