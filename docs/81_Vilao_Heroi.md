## 🎮 Exercício: Jogo Vilão e Herói

### ✅ Objetivo
Você é o **Herói** e o computador é o **Vilão**.  
Ambos escolhem, sem saber a escolha do outro, uma das ações:

- **1 - Atacar**
- **2 - Defender**
- **3 - Fugir**

Depois o programa compara as escolhas e mostra o **resultado da batalha** com base na tabela de regras.

---

## 📌 Tabela de Regras (Herói ↓ / Vilão →)

| Herói \ Vilão | 1 - Atacar | 2 - Defender | 3 - Fugir |
|---|---|---|---|
| **1 - Atacar** | Os dois se ferem! | O vilão bloqueia seu ataque! | Você acerta o vilão pelas costas! |
| **2 - Defender** | Você bloqueia o ataque do vilão! | Ambos ficam na defensiva... ninguém se fere. | O vilão foge enquanto você se protege. |
| **3 - Fugir** | Você escapa por pouco do ataque! | Você foge com sucesso, o vilão nem tenta seguir. | Ambos fogem... ninguém vence. |

---

## 💡 Regras importantes
- O vilão (computador) escolhe aleatoriamente com `SecureRandom`.
- O herói (usuário) escolhe via teclado.
- Use `try-catch` para evitar quebrar caso o usuário digite algo inválido.

---

## ✅ Código completo em Java (com try-catch + switch)

    import java.security.SecureRandom;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            SecureRandom sorteio = new SecureRandom();

            // 1 = atacar, 2 = defender, 3 = fugir
            int escolhaVila = sorteio.nextInt(3) + 1;

            System.out.println("=== Jogo: Herói x Vilão ===\n");
            System.out.println("Escolha sua ação:");
            System.out.println("1 - Atacar");
            System.out.println("2 - Defender");
            System.out.println("3 - Fugir\n");

            int escolhaHeroi = 0;

            try {
                System.out.print("Digite sua escolha (1 a 3): ");
                String entrada = teclado.nextLine().trim();
                escolhaHeroi = Integer.parseInt(entrada);

                if (escolhaHeroi < 1 || escolhaHeroi > 3) {
                    System.out.println("\nErro: escolha inválida. Execute o programa novamente e escolha 1, 2 ou 3.");
                    teclado.close();
                    return;
                }

            } catch (NumberFormatException e) {
                System.out.println("\nErro: valor inválido. Você deve digitar 1, 2 ou 3. Execute o programa novamente.");
                teclado.close();
                return;
            } catch (Exception e) {
                System.out.println("\nErro inesperado. Execute o programa novamente.");
                teclado.close();
                return;
            }

            String acaoHeroi = nomeAcao(escolhaHeroi);
            String acaoVila = nomeAcao(escolhaVila);

            System.out.printf("%nVocê (Herói) escolheu: %s%n", acaoHeroi);
            System.out.printf("Computador (Vilão) escolheu: %s%n%n", acaoVila);

            String resultado = resultadoBatalha(escolhaHeroi, escolhaVila);

            System.out.println("⚔️ Resultado da batalha: " + resultado);

            teclado.close();
        }

        // Converte o número em texto
        public static String nomeAcao(int escolha) {
            switch (escolha) {
                case 1: return "Atacar";
                case 2: return "Defender";
                case 3: return "Fugir";
                default: return "Desconhecido";
            }
        }

        // Aplica as regras do jogo
        public static String resultadoBatalha(int heroi, int vila) {
            // Herói atacou
            if (heroi == 1) {
                switch (vila) {
                    case 1: return "Herói e Vilão foram com tudo... os dois se feriram!";
                    case 2: return "O Vilão levantou o escudo e bloqueou seu ataque!";
                    case 3: return "O Vilão tentou fugir... mas você acertou pelas costas!";
                }
            }

            // Herói defendeu
            if (heroi == 2) {
                switch (vila) {
                    case 1: return "Você defendeu com precisão e bloqueou o ataque do Vilão!";
                    case 2: return "Ambos ficaram em posição defensiva... tensão no ar, ninguém se fere.";
                    case 3: return "Enquanto você se protegia, o Vilão aproveitou e fugiu!";
                }
            }

            // Herói fugiu
            if (heroi == 3) {
                switch (vila) {
                    case 1: return "Você escapou por pouco do ataque! Foi quase!";
                    case 2: return "Você bateu em retirada com sucesso... o Vilão nem tentou seguir.";
                    case 3: return "Os dois fugiram... ninguém venceu essa batalha.";
                }
            }

            return "Algo deu errado nas regras do jogo.";
        }
    }

---

# Complemento da Lição

---

## 🧩 Módulo 1 — Visão geral (passo a passo do raciocínio)

1) **O vilão escolhe primeiro (em segredo)**
- `sorteio.nextInt(3) + 1` gera `1`, `2` ou `3`.

2) **O herói escolhe pelo teclado**
- Lê como texto (`nextLine`)
- Converte para número (`Integer.parseInt`)
- Valida se está entre `1` e `3`

3) **O programa traduz números em ações**
- `1` → Atacar
- `2` → Defender
- `3` → Fugir

4) **O programa aplica as regras**
- Usa `resultadoBatalha(heroi, vila)` para retornar uma frase pronta.

---

## 🎲 Módulo 2 — Entendendo o sorteio do vilão

    int escolhaVila = sorteio.nextInt(3) + 1;

- `nextInt(3)` gera: `0`, `1` ou `2`
- Somando `+1`, vira: `1`, `2` ou `3`

Exemplo do mundo real:
- É como girar uma roleta com 3 resultados e depois “renomear” para 1, 2 e 3.

---

## 🛡️ Módulo 3 — Validação (por que isso evita quebrar)

O problema que pode acontecer:
- usuário digita `abc`
- `Integer.parseInt("abc")` gera `NumberFormatException`

Seu `try-catch`:
- captura o erro
- mostra mensagem clara
- encerra com segurança (sem travar o programa)

Além disso, você validou o intervalo:
- se não for 1..3, também encerra com mensagem.

---

## 🧠 Módulo 4 — Como a função `resultadoBatalha()` “lê” a tabela

A tabela de regras é como “linha e coluna”:

- Linha = escolha do **Herói**
- Coluna = escolha do **Vilão**

Seu método faz exatamente isso:

1) Primeiro escolhe o “bloco” pela linha (Herói):
- se `heroi == 1` (Atacar)
- se `heroi == 2` (Defender)
- se `heroi == 3` (Fugir)

2) Dentro de cada bloco, usa `switch (vila)` para escolher a coluna.

Exemplo:
- Herói = `2` (Defender)
- Vilão = `1` (Atacar)
- Cai em:
  - bloco do herói `2`
  - `case 1` do vilão
  - retorna: “Você defendeu...”

---

## ✅ Módulo 5 — Mapeamento completo (para conferir rapidamente)

- Herói Atacar (1):
  - Vilão Atacar (1) → ambos se ferem
  - Vilão Defender (2) → vilão bloqueia
  - Vilão Fugir (3) → herói acerta pelas costas

- Herói Defender (2):
  - Vilão Atacar (1) → herói bloqueia
  - Vilão Defender (2) → ninguém se fere
  - Vilão Fugir (3) → vilão foge

- Herói Fugir (3):
  - Vilão Atacar (1) → herói escapa por pouco
  - Vilão Defender (2) → herói foge, vilão não segue
  - Vilão Fugir (3) → ambos fogem

---

## ⚠️ Erros comuns (que seu código já evita)

- Digitar texto e quebrar o programa → evitado com `try-catch`
- Digitar `0` ou `4` e cair em regra inexistente → evitado com validação 1..3
- Mostrar número sem significado → evitado com `nomeAcao()`

---

## 🧪 Exercícios (evolução do mesmo jogo)

1) Faça o programa mostrar também os números escolhidos:
- “Herói: 2 (Defender)”
- “Vilão: 1 (Atacar)”

2) Faça o jogo ter 3 rodadas:
- no final mostre quantas vitórias/derrotas/empates do herói

3) Crie um placar de “dano”:
- ataque bem-sucedido tira 2 pontos de vida
- ambos se ferem tira 1 de cada
- defender não perde vida
- fugir não perde vida
- fim quando alguém chegar a 0

---


---

<!-- nav_start -->
---
Anterior: [80 Acerte Numero](../docs/80_Acerte_Numero.md) | Proximo: [82 Conceito Bibliotecas](../docs/82_Conceito_Bibliotecas.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
