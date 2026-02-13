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

<!-- nav_start -->
---
Anterior: [79 Pedra Papel Tesoura](../docs/79_Pedra_Papel_Tesoura.md) | Proximo: [81 Vilao Heroi](../docs/81_Vilao_Heroi.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
