# ✅ Questão 05 — IMC (Java) com `try/catch` e `if/else`

---

## 🎯 Objetivo
- Ler **peso (kg)** e **altura (m)**
- Calcular o **IMC**
- Informar a **classificação** conforme OMS
- Usar **comentários**, **try/catch** e **if/else**

---

## ✅ Código (UTF-8 normalizado)

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

---

## Complemento da Lição

### ✅ O que ficou bem feito no seu código
- Você validou **peso e altura > 0** antes de calcular (evita erro e resultado sem sentido).
- Você usou `if/else if` do jeito certo: **faixas** (intervalos) sem sobreposição.
- Você tratou `InputMismatchException`, que é o erro mais comum do `Scanner` quando o usuário digita letras.

---

### ⚠️ Pontos que ainda podem “interromper” o fluxo do jogo/programa
Mesmo com `try/catch`, se o usuário digitar errado:
- Você mostra a mensagem…
- E o programa **termina** (porque não pede de novo).

O padrão para “não parar” é: **repetir a pergunta até vir um valor válido** (loop + tratamento).

---

### 🧠 Detalhe importante do `Locale`
Você definiu `Locale.setDefault(Locale.US)` para aceitar **ponto** (1.75).
- Se o usuário digitar com **vírgula** (1,75), pode dar `InputMismatchException`.

---

### 🧩 Exercício prático (fixação)
1) Faça o programa **repetir** a leitura do peso até o usuário digitar um número válido.
2) Depois faça o mesmo para a altura.
3) Regra: se digitar texto (ex.: `abc`) ou número inválido (≤ 0), o programa **não encerra**.

---

### ✅ Checkpoint (para você responder)
Você está digitando a altura/peso com **vírgula** (`1,75`) ou com **ponto** (`1.75`)?

<!-- nav_start -->
---
Anterior: [53 Questao 04](../docs/53_Questao_04.md) | Proximo: [55 Teoria If Else](../docs/55_Teoria_If_Else.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
