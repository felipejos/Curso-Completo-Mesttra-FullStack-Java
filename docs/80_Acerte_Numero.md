## 🎯 Exercício: Acerte o Número (0 a 10)

### ✅ Regras do jogo
- O computador sorteia **um número entre 0 e 10**.
- O jogador tem **3 tentativas** para acertar.
- Se errar, o programa informa se o chute foi **abaixo** ou **acima** do número sorteado.
- Pontuação:
  - Acertou na **1ª tentativa** → **5 pontos**
  - Acertou na **2ª tentativa** → **4 pontos**
  - Acertou na **3ª tentativa** → **2 pontos**
- Se não acertar em 3 tentativas → **perde o jogo**.

---

## 🧠 Dica rápida
- Use `SecureRandom` para sortear.
- Use `try-catch` para evitar travar se o usuário digitar algo inválido.

---

## ✅ Código completo em Java

    import java.security.SecureRandom;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            SecureRandom sorteio = new SecureRandom();

            // Sorteia um número entre 0 e 10 (inclusive)
            int numeroSecreto = sorteio.nextInt(11);

            int tentativas = 3;
            int tentativaAtual = 1;
            boolean acertou = false;

            System.out.println("=== Jogo: Acerte o Número ===");
            System.out.println("O computador escolheu um número entre 0 e 10.");
            System.out.println("Você tem 3 tentativas!\n");

            while (tentativaAtual <= tentativas && !acertou) {
                try {
                    System.out.printf("Tentativa %d de %d - Digite seu chute (0 a 10): ", tentativaAtual, tentativas);
                    String entrada = teclado.nextLine().trim();

                    int chute = Integer.parseInt(entrada);

                    // (Opcional) validação simples do intervalo, para evitar dicas fora do jogo
                    if (chute < 0 || chute > 10) {
                        System.out.println("Erro: o chute deve estar entre 0 e 10. Execute o programa novamente.\n");
                        teclado.close();
                        return;
                    }

                    if (chute == numeroSecreto) {
                        acertou = true;

                        int pontos;
                        if (tentativaAtual == 1) {
                            pontos = 5;
                        } else if (tentativaAtual == 2) {
                            pontos = 4;
                        } else {
                            pontos = 2;
                        }

                        System.out.printf("\n✅ Você acertou! O número era %d.%n", numeroSecreto);
                        System.out.printf("🏆 Pontuação: %d pontos.%n", pontos);
                    } else {
                        // Se ainda houver tentativa disponível, dá dica e continua
                        if (chute < numeroSecreto) {
                            System.out.println("❌ Errou! Seu chute está ABAIXO do número.\n");
                        } else {
                            System.out.println("❌ Errou! Seu chute está ACIMA do número.\n");
                        }
                    }

                    tentativaAtual++;

                } catch (NumberFormatException e) {
                    System.out.println("Erro: valor inválido. Por favor, digite um NÚMERO inteiro. Execute o programa novamente.\n");
                    teclado.close();
                    return;
                } catch (Exception e) {
                    System.out.println("Ocorreu um erro inesperado. Execute o programa novamente.\n");
                    teclado.close();
                    return;
                }
            }

            if (!acertou) {
                System.out.printf("😢 Você perdeu! O número era %d.%n", numeroSecreto);
            }

            teclado.close();
        }
    }

---

# Complemento da Lição

---

## 🧩 Módulo 1 — “Arquitetura” do jogo (bem simples)

Pense em 4 partes:

1) **Sorteio**
- O computador escolhe um número com `sorteio.nextInt(11)`.

2) **Controle de tentativas**
- Você tem `3` tentativas.
- A variável `tentativaAtual` começa em `1` e vai até `3`.

3) **Leitura segura da entrada**
- Lê texto com `nextLine()`.
- Converte para número com `Integer.parseInt()`.
- Se não for número, cai no `catch (NumberFormatException)`.

4) **Regras (dicas + pontuação)**
- Se acertar → calcula pontos.
- Se errar → dá dica “acima” ou “abaixo”.
- Se acabar tentativas → perde.

---

## 🧠 Módulo 2 — Entendendo o sorteio (passo a passo)

    int numeroSecreto = sorteio.nextInt(11);

- `nextInt(11)` gera um número de `0` até `10`:
  - porque ele vai de `0` até `n - 1`
  - aqui `n = 11`
  - então `0` a `10`

Exemplo do mundo real:
- É como ter 11 papeizinhos numerados de 0 a 10 em uma caixa e tirar 1.

---

## 🔁 Módulo 3 — Por que o `while` funciona (controle real do jogo)

    while (tentativaAtual <= tentativas && !acertou)

O loop continua enquanto:
- ainda tem tentativa (`tentativaAtual <= 3`)
- e o jogador ainda não acertou (`!acertou`)

Isso evita:
- continuar jogando depois de acertar
- passar de 3 tentativas

---

## ✅ Módulo 4 — Pontuação (raciocínio direto)

A pontuação depende da tentativa:

- tentativa 1 → 5 pontos
- tentativa 2 → 4 pontos
- tentativa 3 → 2 pontos

O seu código faz isso com:

    if (tentativaAtual == 1) { ... }
    else if (tentativaAtual == 2) { ... }
    else { ... }

Exemplo do mundo real:
- Quanto mais rápido você acerta, mais “recompensa” você ganha.

---

## 🛡️ Módulo 5 — Por que usar `Integer.parseInt()` e não `nextInt()`

Você leu assim:

    String entrada = teclado.nextLine().trim();
    int chute = Integer.parseInt(entrada);

Vantagens (bem práticas):
- Você controla melhor erros (ex.: texto inválido).
- Evita problemas comuns de `Scanner` quando mistura `nextInt()` com `nextLine()`.

---

## ⚠️ Módulo 6 — Pontos de atenção do seu código (comportamento real)

### 1) Você encerra o programa ao digitar fora de 0..10
Aqui:

    if (chute < 0 || chute > 10) {
        System.out.println("Erro: o chute deve estar entre 0 e 10. Execute o programa novamente.\n");
        teclado.close();
        return;
    }

Isso é “válido”, mas significa:
- o jogador perde a chance de tentar de novo no mesmo jogo

### 2) Em erro de texto, você também encerra
No `NumberFormatException`, você encerra com `return`.
Isso garante que não “quebra”, mas interrompe o jogo.

---

## 🧪 Exercícios (fixação + prática)

1) Em vez de encerrar quando o chute for fora de 0..10, faça:
- mostrar mensagem de erro
- **não contar tentativa**
- pedir novamente

2) Em vez de encerrar ao digitar texto inválido, faça:
- mostrar mensagem
- **não contar tentativa**
- pedir novamente

3) Mostre no final o histórico de chutes:
- tentativa 1: X
- tentativa 2: Y
- tentativa 3: Z

4) Adicione dificuldade:
- fácil (0..10, 3 tentativas)
- médio (0..50, 5 tentativas)
- difícil (0..100, 7 tentativas)

---


---

<!-- nav_start -->
---
Anterior: [79 Pedra Papel Tesoura](../docs/79_Pedra_Papel_Tesoura.md) | Proximo: [81 Vilao Heroi](../docs/81_Vilao_Heroi.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
