# 🧩 If/Else — Exercício 2 (Notas + Faltas)

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

---

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

---

# Complemento da Lição

---

## 1) Ordem correta das regras (por prioridade)
Quando existe regra de **falta** e regra de **nota**, a falta costuma ter prioridade, porque reprova mesmo que a média seja alta.

Ordem típica:
1. **Reprovado por falta** (percentualFaltas >= 25)
2. Se não reprovou por falta:
   - **Aprovado** (média >= 6)
   - **Recuperação** (média >= 3 e < 6)
   - **Reprovado por nota** (média < 3)

---

## 2) Ponto importante: cálculo do percentual com divisão inteira
No seu código:

    percentualFaltas = (qtdeFaltas * 100) / qtdeAulasDadas;

`qtdeFaltas`, `100` e `qtdeAulasDadas` são `int`.  
Isso faz o Java calcular como **divisão inteira** e só depois jogar o resultado no `float`.

Exemplo:
- 1 falta em 3 aulas → (1 * 100) / 3 = 33 (ok)
- 1 falta em 200 aulas → (1 * 100) / 200 = 0 (vira 0.0 no float, perdendo a parte decimal)

Forma mais segura:
- forçar pelo menos um lado para `float`:

    percentualFaltas = (qtdeFaltas * 100.0f) / qtdeAulasDadas;

---

## 3) Ajuste dos limites do enunciado vs código
O enunciado diz:
- Falta: **PercentualFaltas >= 25**
- Recuperação: **média >= 3 e < 6**
- Reprovado por nota: **média < 3**

Na “versão principal”, aparecem dois desvios:
- usa `percentualFaltas > 25` (em vez de `>= 25`)
- usa `media >= 4` para recuperação (enunciado pede `>= 3`)

---

## 4) Versão “corrigida” (seguindo exatamente o enunciado)
Abaixo, apenas o trecho principal (cálculo + decisão), mantendo o estilo do exercício:

    media = (nota1 + nota2 + nota3 + nota4) / 4;

    percentualFaltas = (qtdeFaltas * 100.0f) / qtdeAulasDadas;

    if (percentualFaltas >= 25) {
        System.out.printf("Aluno reprovado por faltas (%.1f%%) faltas.", percentualFaltas);
    } else if (media >= 6) {
        System.out.printf("Aluno aprovado, a média foi %.2f pontos.", media);
    } else if (media >= 3) {
        System.out.printf("Aluno de recuperação, a média foi %.2f pontos.", media);
    } else {
        System.out.printf("Aluno reprovado por nota. Nota final %.2f pontos.", media);
    }

---

## 5) Testes rápidos (para validar a lógica)
Use entradas simples para confirmar a saída:

- **Caso A (reprovado por falta)**  
  aulas=20, faltas=5 → 25% → deve reprovar por falta

- **Caso B (aprovado)**  
  faltas baixas, média 6.0 ou mais → aprovado

- **Caso C (recuperação)**  
  faltas baixas, média entre 3.0 e 5.99 → recuperação

- **Caso D (reprovado por nota)**  
  faltas baixas, média menor que 3.0 → reprovado por nota

<!-- nav_start -->
---
Anterior: [If Else: ExercÃ­cio 1](../docs/44_If_Else_Exercicio_1.md) | Próximo: [Desafio Jogo da Forca](../docs/46_Desafio_Jogo_Forca.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

