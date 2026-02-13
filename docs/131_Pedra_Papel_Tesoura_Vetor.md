Pedra, papel, tesoura com vetor
Depois que aprendemos à trabalhar com vetores, vamos comparar a implementação do jogo pedra, papel, tesoura feito anteriormente, com uma versão melhorada, utilizando vetores.

Jogo Pedra, Papel e Tesoura

import java.util.Scanner;
// SecureRandom é a biblioteca de sorteio de números
import java.security.SecureRandom;

public class App {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);

        // comando para preparar a variavel para o sorteio
        SecureRandom sorteio = new SecureRandom();
        String escolhaComputador = "";
        String escolhaJogador = "";

        System.out.println("Digite sua escolha (pedra, papel ou tesoura): ");
        escolhaJogador = teclado.nextLine().toLowerCase();

        // sorteia um numero de 0 à 2 (n - 1)
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

        System.out.println("O computador escolheu: " + escolhaComputador);

        // lógica do jogo
        if (escolhaComputador.equals(escolhaJogador)) {
            System.out.printf("Ambos escolheram %s. Deu empate!", escolhaComputador);
        } else if (
            (escolhaJogador.equals("pedra") && escolhaComputador.equals("tesoura")) ||
            (escolhaJogador.equals("papel") && escolhaComputador.equals("pedra")) ||
            (escolhaJogador.equals("tesoura") && escolhaComputador.equals("papel"))) {
            System.out.println("Você venceu!");
        } else if (
            escolhaJogador.equals("pedra") ||
            escolhaJogador.equals("papel") ||
            escolhaJogador.equals("tesoura")) {
            System.out.println("O computador venceu!");
        } else {
            System.out.println("Opção inválida! Use pedra, papel ou tesoura.");
        }

        teclado.close();
    }
}

Compare agora com esta implementação utilizando vetor para determinar o sorteio da escolha do computador.



import java.util.Scanner;
// SecureRandom é a biblioteca de sorteio de números
import java.security.SecureRandom;

public class App { 
    public static void main(String[] args) {

        String[] opcoes = {"pedra", "papel", "tesoura"};
        Scanner teclado = new Scanner(System.in);
        SecureRandom sorteio = new SecureRandom();

        // Escolha do computador usando o array
        int numeroSorteado = sorteio.nextInt(3); 
        String escolhaComputador = opcoes[numeroSorteado];

        // Escolha do jogador
        System.out.print("Digite sua escolha (pedra, papel ou tesoura): ");
        String escolhaJogador = teclado.nextLine().toLowerCase();

        // Validação simples
        if (!escolhaJogador.equals("pedra") &&
            !escolhaJogador.equals("papel") &&
            !escolhaJogador.equals("tesoura")) {
            System.out.println("Opção inválida! Use apenas pedra, papel ou tesoura.");
            teclado.close();
            return;
        }

        System.out.println("O computador escolheu: " + escolhaComputador);

        // Lógica do jogo
        if (escolhaComputador.equals(escolhaJogador)) {
            System.out.println("Empate!");
        } 
        else if (
            (escolhaJogador.equals("pedra")   && escolhaComputador.equals("tesoura")) ||
            (escolhaJogador.equals("papel")   && escolhaComputador.equals("pedra"))   ||
            (escolhaJogador.equals("tesoura") && escolhaComputador.equals("papel"))
        ) {
            System.out.println("Você venceu!");
        } 
        else {
            System.out.println("O computador venceu!");
        }

        teclado.close();
    }
}

---

**Complementos (deixando mais completo e fácil de entender)**

### 1) O que melhora quando usamos vetor (array)?
Quando você usa `switch`, você “amarrra” o sorteio a vários `case`. Funciona, mas:
- fica mais verboso
- se você quiser adicionar novas opções (ex: “lagarto”, “Spock”), você teria que editar vários pontos

Com vetor, a lógica do sorteio vira:
- “tenho uma lista de opções”
- “sorteio um índice”
- “pego a opção desse índice”

Isso é mais **direto**, **limpo** e **escalável**.

Exemplo mental:
- `opcoes[0] = pedra`
- `opcoes[1] = papel`
- `opcoes[2] = tesoura`
Se o sorteio der `2`, o computador escolhe `opcoes[2]` → “tesoura”.

---

### 2) Como o sorteio funciona exatamente?
`nextInt(3)` sempre retorna um número **inteiro** entre:
- `0` e `2` (nunca chega no 3)

Então:
- `0` pega `"pedra"`
- `1` pega `"papel"`
- `2` pega `"tesoura"`

Isso combina perfeitamente com um vetor de tamanho 3.

---

### 3) Por que validar a entrada do jogador é importante?
Sem validação, o usuário pode digitar:
- “pedraaa”
- “papel ” (com espaço)
- “tesoura,”
- “banana”

E aí o programa não se comporta como esperado.

A validação evita isso e faz o programa:
- aceitar somente o conjunto permitido
- encerrar com uma mensagem clara se for inválido

---

### 4) Um jeito mais “esperto” de validar e decidir vencedor usando índices (conceito)
Em vez de comparar strings o tempo todo, dá pra transformar tudo em **número** (índice no vetor):

- pedra → 0
- papel → 1
- tesoura → 2

A partir disso, existe uma regra clássica:
- se for empate: índices iguais
- senão, o jogador vence quando:
  - `(jogador - computador + 3) % 3 == 1`

Exemplos rápidos:
- jogador pedra(0), pc tesoura(2):
  - (0 - 2 + 3) % 3 = 1 → jogador vence ✅
- jogador papel(1), pc pedra(0):
  - (1 - 0 + 3) % 3 = 1 → jogador vence ✅
- jogador tesoura(2), pc papel(1):
  - (2 - 1 + 3) % 3 = 1 → jogador vence ✅

Ou seja, com índices você reduz bastante o “if gigante”.

---

### 5) Complemento (versão alternativa usando vetor + índice para validar e decidir vencedor)
Mantém a ideia do vetor e deixa a lógica mais compacta, porque compara números (índices) ao invés de comparar textos o tempo todo.

    import java.util.Scanner;
    import java.security.SecureRandom;

    public class App {
        public static void main(String[] args) {
            String[] opcoes = { "pedra", "papel", "tesoura" };

            Scanner teclado = new Scanner(System.in);
            SecureRandom sorteio = new SecureRandom();

            System.out.print("Digite sua escolha (pedra, papel ou tesoura): ");
            String escolhaJogador = teclado.nextLine().toLowerCase().trim();

            int indiceJogador = indexOfSimples(opcoes, escolhaJogador);
            if (indiceJogador == -1) {
                System.out.println("Opção inválida! Use apenas pedra, papel ou tesoura.");
                teclado.close();
                return;
            }

            int indiceComputador = sorteio.nextInt(opcoes.length);
            String escolhaComputador = opcoes[indiceComputador];

            System.out.println("O computador escolheu: " + escolhaComputador);

            if (indiceJogador == indiceComputador) {
                System.out.println("Empate!");
            } else {
                int resultado = (indiceJogador - indiceComputador + 3) % 3;
                if (resultado == 1) {
                    System.out.println("Você venceu!");
                } else {
                    System.out.println("O computador venceu!");
                }
            }

            teclado.close();
        }

        // Faz o papel de um indexOf simples, procurando a string dentro do vetor
        static int indexOfSimples(String[] vetor, String procurado) {
            for (int i = 0; i < vetor.length; i++) {
                if (vetor[i].equals(procurado)) {
                    return i;
                }
            }
            return -1;
        }
    }

---

### 6) Onde esse exemplo conecta com vetores de verdade?
Esse exercício é ótimo porque te faz treinar 3 pontos fundamentais de vetor:

- **Armazenar um conjunto de valores relacionados** (as opções do jogo)
- **Acessar por índice** (resultado do sorteio)
- **Percorrer para buscar um valor** (o `indexOfSimples`)

Isso é a base de muita coisa:
menus, tabelas, rankings, listas de nomes, notas, produtos etc.

<!-- nav_start -->
---
Anterior: [130 Armazenamento Arquivo](../docs/130_Armazenamento_Arquivo.md) | Proximo: [132 Codigo Final Forca](../docs/132_Codigo_Final_Forca.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
