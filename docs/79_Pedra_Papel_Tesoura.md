## ✊✋✌️ Exercício: Pedra, Papel e Tesoura (Java)

### 🎯 Objetivo
Completar o jogo para:
- Ler a escolha do jogador
- Comparar com a escolha do computador
- Exibir o resultado (vitória, derrota ou empate)

---

## ✅ Código completo (com validação de entrada)

    import java.util.Scanner;
    // SecureRandom é a biblioteca de sorteio de números
    import java.security.SecureRandom;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            // comando para preparar a variável para o sorteio
            SecureRandom sorteio = new SecureRandom();
            String escolhaComputador = "";
            String escolhaJogador = "";

            System.out.println("=== Jogo Pedra, Papel e Tesoura ===");
            System.out.println("Opções: pedra | papel | tesoura");
            System.out.println("Você também pode digitar: 1 (pedra), 2 (papel), 3 (tesoura)\n");

            // sorteia um número de 0 à 2 (n - 1)
            switch (sorteio.nextInt(3)) {
                case 0:
                    escolhaComputador = "tesoura";
                    break;
                case 1:
                    escolhaComputador = "pedra";
                    break;
                case 2:
                    escolhaComputador = "papel";
                    break;
            }

            // implementar aqui a lógica para ler a escolha do jogador (com validação)
            try {
                System.out.print("Digite sua escolha: ");
                String entrada = teclado.nextLine().trim().toLowerCase();

                switch (entrada) {
                    case "1":
                    case "pedra":
                        escolhaJogador = "pedra";
                        break;
                    case "2":
                    case "papel":
                        escolhaJogador = "papel";
                        break;
                    case "3":
                    case "tesoura":
                        escolhaJogador = "tesoura";
                        break;
                    default:
                        System.out.println("Entrada inválida. Execute o programa novamente e digite pedra, papel ou tesoura (ou 1/2/3).");
                        teclado.close();
                        return;
                }

                System.out.printf("%nComputador escolheu: %s%n", escolhaComputador);
                System.out.printf("Você escolheu: %s%n%n", escolhaJogador);

                // implementar aqui a lógica do jogo para decidir quem foi o vencedor
                if (escolhaComputador.equals(escolhaJogador)) {
                    System.out.printf("Ambos escolheram %s. Deu empate!%n", escolhaComputador);
                } else if (
                        (escolhaJogador.equals("pedra") && escolhaComputador.equals("tesoura")) ||
                        (escolhaJogador.equals("papel") && escolhaComputador.equals("pedra")) ||
                        (escolhaJogador.equals("tesoura") && escolhaComputador.equals("papel"))
                ) {
                    System.out.println("Você venceu! 🎉");
                } else {
                    System.out.println("Você perdeu! 😅");
                }

            } catch (Exception e) {
                System.out.println("Erro: entrada inválida. Execute o programa novamente.");
            }

            teclado.close();
        }
    }

---

## 🧠 Observações importantes
- Para comparar textos (Strings), use **.equals()** (não use `==`).
- A validação evita que o programa quebre caso o usuário digite algo fora do esperado.
- O computador escolhe aleatoriamente usando `SecureRandom`.

--- 

<!-- nav_start -->
---
Anterior: [Calculadora de Ã¡rea de Figuras GeomÃ©tricas](../docs/78_Calculadora_Area.md) | Próximo: [ExercÃ­cio Acerte o NÃºmero](../docs/80_Acerte_Numero.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

