# 🧩 If Else: Exercício 2

---

## 📌 Enunciado

    //Escreva um algoritmo que leia 4 notas de um aluno de 0 a 10.
    //Leia a quantidade de aulas que foram ministradas e a quantidade de aulas que o aluno faltou.
    //Calcule uma media simples entre as 4 notas e também o percentual de faltas do aluno.
    //Ao termino informe o aluno foi:
    //Reprovado por falta. PercentualFaltas >= 25
    //Aprovado. MediaNotas notas >= 6
    //Recuperação. MediaNotas >= 3 e < 6
    //Reprovado por Nota. MediaNotas < 3

---

## ✅ Versão principal (mais eficiente)

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
                //é executado se a condicao (percentualFaltas > 25) for verdadeira
                System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
            }  else if (media >= 6) {
                //é executado se a condicao (media >= 6) for verdadeira
                System.out.printf("Aluno aprovado, a média foi %.2f pontos.", media);
            } else if (media >= 4){
                // é executado se a condicao (media >= 4) for verdadeira
                System.out.printf("Aluno de recuperação, a média foi %.2f pontos.", media);
            } else {
                // é executado se a condicao (media < 4) for verdadeira
                System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
            }  

            teclado.close();
        }
    }

---

## 🔎 Outras versões (menos eficientes) — apenas olhando para o bloco `if/else`

### 1) Versão com condições repetidas

    if (media >= 6 && percentualFaltas < 25) {
        //é executado se a condicao (media >= 6) for verdadeira
        System.out.printf("Aluno aprovado, a média foi %.2f pontos.", media);
    } else if (media >= 4 && percentualFaltas < 25){
        // é executado se a condicao (media >= 4) for verdadeira
        System.out.printf("Aluno de recuperação, a média foi %.2f pontos.", media);
    } else if (media < 4 && percentualFaltas < 25){
        // é executado se a condicao (media < 4) for verdadeira
        System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
    } else if (percentualFaltas > 25 && percentualFaltas < 25){
        //é executado se a condicao (percentualFaltas > 25) for verdadeira
        System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
    }

> ⚠️ Observação: esse último `else if` tem uma condição impossível  
> `percentualFaltas > 25 && percentualFaltas < 25` nunca será verdadeira ao mesmo tempo.

---

### 2) Versão reorganizada

    if (percentualFaltas > 25){
        //é executado se a condicao (percentualFaltas > 25) for verdadeira
        System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
    }  else if (media >= 4 && media < 6) {
        // é executado se a condicao (media >= 4) for verdadeira
        System.out.printf("Aluno de recuperação, a média foi %.2f pontos.", media);
    } else if (media >= 6) {
        //é executado se a condicao (media >= 6) for verdadeira
        System.out.printf("Aluno aprovado, a média foi %.2f pontos.", media);
    } else if (media < 4){
        // é executado se a condicao (media < 4) for verdadeira
        System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
    }

---

### 3) Versão com `if` aninhado (mais verbosa)

    if (percentualFaltas > 25){
        //é executado se a condicao (percentualFaltas > 25) for verdadeira
        System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
    }  else {
        if (media >= 6) {
            //é executado se a condicao (media >= 6) for verdadeira
            System.out.printf("Aluno aprovado, a média foi %.2f pontos.", media);
        } else {
            if (media >= 4) {
                // é executado se a condicao (media >= 4) for verdadeira
                System.out.printf("Aluno de recuperação, a média foi %.2f pontos.", media);
            } else {
                if (media < 4){
                    // é executado se a condicao (media < 4) for verdadeira
                    System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
                }
            }
        }
    }
