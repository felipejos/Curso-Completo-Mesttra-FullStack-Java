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

# Complemento da Lição

---

## 🧩 Módulo 1 — Entendendo a “arquitetura” do programa (bem simples)

Pense no programa como 3 blocos principais:

1) **Sorteio do computador**
- O computador escolhe aleatoriamente `pedra`, `papel` ou `tesoura`.

2) **Leitura + validação do jogador**
- O jogador digita texto (`"pedra"`) ou número (`"1"`).
- O programa transforma isso em uma escolha padronizada: `pedra | papel | tesoura`.

3) **Regra do jogo (decidir vencedor)**
- Empate se as escolhas forem iguais.
- Vitória se o jogador estiver em uma das combinações vencedoras.
- Senão, derrota.

---

## 🧠 Módulo 2 — Passo a passo do raciocínio do sorteio do computador

O computador faz:

    sorteio.nextInt(3)

Isso devolve um número **aleatório** entre:
- `0`, `1` ou `2`

Aí o `switch` transforma número em palavra:

- `0` → `"tesoura"`
- `1` → `"pedra"`
- `2` → `"papel"`

Exemplo do mundo real:
- É como jogar um dado que só tem 3 lados numerados 0, 1 e 2.
- Depois você traduz o número para uma opção do jogo.

---

## ✅ Módulo 3 — Validação do jogador (por que `.trim().toLowerCase()`?)

O programa usa:

    String entrada = teclado.nextLine().trim().toLowerCase();

Isso faz 2 “limpezas”:

- `.trim()` remove espaços extras:
  - `"  Pedra  "` vira `"Pedra"`
- `.toLowerCase()` deixa tudo minúsculo:
  - `"Pedra"` vira `"pedra"`

Assim, o usuário pode digitar:
- `PEDRA`, `Pedra`, ` pedra `, `PeDrA`
e o código entende do mesmo jeito.

---

## 🥊 Módulo 4 — Regras do jogo (mapa mental rápido)

### ✅ Empate
- `pedra` x `pedra`
- `papel` x `papel`
- `tesoura` x `tesoura`

### ✅ Jogador vence quando:
- `pedra` ganha de `tesoura`
- `papel` ganha de `pedra`
- `tesoura` ganha de `papel`

Tudo isso está neste bloco:

    (pedra vs tesoura) OU (papel vs pedra) OU (tesoura vs papel)

---

## ⚠️ Módulo 5 — Erros comuns (e por que seu código evitou)

### 1) Usar `==` para comparar String
Errado:

    if (escolhaComputador == escolhaJogador)

Certo (como você fez):

    if (escolhaComputador.equals(escolhaJogador))

Explicação simples:
- `==` compara “se é o mesmo objeto”
- `.equals()` compara “se o texto é igual”

Exemplo do mundo real:
- Duas folhas diferentes podem ter a mesma palavra escrita (“pedra”).
- `.equals()` olha a palavra escrita, não a folha.

---

## 🧪 Exercícios (para fixar, sem complicar)

1) **Conte placar**
- Crie duas variáveis `vitorias` e `derrotas`.
- Se ganhar, soma 1 em `vitorias`.
- Se perder, soma 1 em `derrotas`.
- No final, mostre o placar.

2) **Rodadas**
- Faça o jogo repetir 3 vezes (3 rodadas) e depois mostrar:
  - vitórias, derrotas e empates.

3) **Mensagem mais detalhada**
- Quando o jogador vencer, mostre a regra usada:
  - Ex.: `"Pedra quebra Tesoura. Você venceu!"`

---


---

<!-- nav_start -->
---
Anterior: [78 Calculadora Area](../docs/78_Calculadora_Area.md) | Proximo: [80 Acerte Numero](../docs/80_Acerte_Numero.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
