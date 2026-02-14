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

# Complemento da Lição

---

## ✅ O que sua solução já atende muito bem
- Lê as três entradas (**frente**, **lateral**, **valor do metro²**).
- Calcula o valor do terreno: `frente * lateral * valorMetroQuadrado`.
- Aplica a regra:
  - quadrado (`frente == lateral`) → **+10%**
  - retângulo → **-2%**
- Usa `try/catch` para capturar erro de digitação (`InputMismatchException`).

---

## ⚠️ Ponto principal do enunciado (“NÃO seja interrompido por exceções”)
Do jeito que está, se o usuário digitar algo inválido:
- cai no `catch`,
- mostra a mensagem,
- e o programa **termina** (não volta a pedir a entrada).

Para cumprir “não interromper”, o padrão é:
- **repetir a pergunta** até vir um valor válido (**loop + try/catch**)
- e **descartar a entrada inválida** do `Scanner` para não ficar preso no mesmo erro

---

## 🧠 Por que precisa “descartar a entrada inválida”?
Quando o usuário digita letras e você usa `nextInt()`/`nextFloat()`, o `Scanner` não consegue converter e lança `InputMismatchException`.  
Mas aquele texto inválido continua “parado” na entrada. Se você não limpar, vai falhar de novo na próxima tentativa.

Linha típica para limpar:
- `teclado.nextLine();` (descarta o que sobrou na linha)

---

## 🧩 Esqueleto do padrão correto (para você encaixar nas 3 leituras)

### 1) Ler inteiro positivo (frente/lateral)
    int valor = 0;

    while (true) {
        try {
            System.out.print("Digite ...: ");
            valor = teclado.nextInt();

            if (valor <= 0) {
                System.out.println("Erro: informe um número maior que 0.");
                continue;
            }

            break;
        } catch (InputMismatchException e) {
            System.out.println("Erro: digite um número inteiro válido.");
            teclado.nextLine(); // limpa entrada inválida
        }
    }

### 2) Ler float positivo (valor do metro²)
    float valor = 0.0f;

    while (true) {
        try {
            System.out.print("Digite ...: ");
            valor = teclado.nextFloat();

            if (valor <= 0) {
                System.out.println("Erro: informe um valor maior que 0.");
                continue;
            }

            break;
        } catch (InputMismatchException e) {
            System.out.println("Erro: digite um número decimal válido.");
            teclado.nextLine(); // limpa entrada inválida
        }
    }

---

## ✅ Ajustes finos (qualidade)
- `ArithmeticException` aqui tende a não acontecer (não tem divisão). O essencial é `InputMismatchException`.
- Validar valores:
  - `frenteMts > 0`
  - `lateralMts > 0`
  - `valorMetroQuadrado > 0`
- Fechar `Scanner` no final é bom (e pode ir em `finally` quando você migrar para loops e/ou múltiplas leituras).

---

## Exercício rápido (1 passo)
Pegue sua solução e altere **apenas a leitura de `frenteMts`** para o padrão com `while(true)` + `try/catch` + `teclado.nextLine()` no erro.  
Depois teste digitando:
- `abc` (tem que avisar e pedir de novo)
- `-5` (tem que avisar e pedir de novo)
- `10` (tem que aceitar e seguir)

---

<!-- nav_start -->
---
Anterior: [65 Desafio CPF](../docs/65_Desafio_CPF.md) | Proximo: [70 Solucao Teste1 Q05](../docs/70_Solucao_Teste1_Q05.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
