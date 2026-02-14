# Solução: Teste1 Questão 04

---

## Enunciado (Teste 1 – Questão 04)
- Escreva um algoritmo que leia as dimensões de um terreno (**frente** e **lateral**).
- Leia também o **valor do metro quadrado**.
- Após as leituras, calcule a **área total** do terreno e o **valor do terreno** com base no valor do metro quadrado.
- Caso o terreno seja um **quadrado perfeito**, aumente o valor do terreno em **10%** (pois este terreno é mais valioso).
- Caso o terreno **não** seja um quadrado perfeito, dê um **desconto de 2%** no valor total.

---

## ✅ Solução (com try/catch + if/else)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int frenteMts = 0, lateralMts = 0;
            float valorMetroQuadrado = 0.0f;
            float valorTerreno = 0.0f;

            try {
                System.out.print("Digite a metragem da frente do terreno: ");
                frenteMts = teclado.nextInt();

                System.out.print("Digite a metragem da lateral do terreno: ");
                lateralMts = teclado.nextInt();

                System.out.print("Digite o valor do metro quadrado: ");
                valorMetroQuadrado = teclado.nextFloat();

                // calculando o valor do terreno
                valorTerreno = frenteMts * lateralMts * valorMetroQuadrado;

                // estrutura de decisão composta
                if (frenteMts == lateralMts) {
                    // terreno quadrado: aumento de 10%
                    valorTerreno *= 1.1f;
                    System.out.println("Terreno quadrado detectado: valor acrescido em 10%.");
                } else {
                    // terreno retangular: desconto de 2%
                    valorTerreno *= 0.98f;
                    System.out.println("Terreno retangular: desconto de 2% aplicado.");
                }

                System.out.printf("O valor do terreno é: R$ %.2f reais%n", valorTerreno);

            } catch (InputMismatchException e) {
                System.out.println("Erro: Você inseriu um valor inválido. Por favor, utilize apenas números.");
            } catch (ArithmeticException e) {
                System.out.println("Erro de cálculo: " + e.getMessage());
            } catch (Exception e) {
                System.out.println("Ocorreu um erro inesperado: " + e.getMessage());
            }

            teclado.close();
        }
    }

---

## Complemento da Lição

### ✅ O que sua solução já atende bem
- Leitura de **frente**, **lateral** e **valor do m²**
- Cálculo do **valor do terreno** pela área
- Regra do **quadrado perfeito (+10%)** e do **não quadrado (-2%)**
- Uso de `try/catch` para impedir “quebra” por entrada inválida

---

### ⚠️ Ajuste importante para “não ser interrompido”
Do jeito que está, se o usuário errar (ex.: digitar `abc`), você mostra a mensagem… mas o programa **termina**.

Para realmente “não interromper”, o padrão é:
- colocar **cada leitura** dentro de um `while (true)`
- no `catch (InputMismatchException)`:
  - imprimir mensagem
  - **limpar o buffer** do Scanner
  - voltar a pedir a entrada

Um lembrete do ponto-chave:
- Se você não limpar, o mesmo valor inválido fica preso e a próxima leitura falha de novo.

---

### ✅ Validações que deixam a regra de negócio mais forte
- `frenteMts` e `lateralMts` devem ser **maiores que 0**
- `valorMetroQuadrado` deve ser **maior que 0**
- (opcional) imprimir também a **área total**:

    float area = frenteMts * lateralMts;
    valorTerreno = area * valorMetroQuadrado;

---

### ✅ Boa prática com `Scanner`
Para garantir fechamento mesmo com erro, o padrão mais seguro é fechar em `finally` (ou usar `try-with-resources`). Aqui você fecha no final do `main`, o que funciona, mas não é o formato mais “à prova de erro”.

---

### 🎯 Checkpoint
Como você faria para o programa **pedir novamente** o valor quando acontecer `InputMismatchException` (sem encerrar o programa)?

<!-- nav_start -->
---
Anterior: [70 Solucao Teste1 Q05](../docs/70_Solucao_Teste1_Q05.md) | Proximo: [73 Lista Exercicios 05](../docs/73_Lista_Exercicios_05.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
