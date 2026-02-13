Código Final Jogo da Forca
import java.util.Scanner;

public class App {

        public static void main(String[] args) {
                Scanner teclado = new Scanner(System.in);

                int vidasRestantes = 6;
                String letrasCertas = "";
                String letrasTentadas = "";
                char letraChutada;

                String palavra = "treme";

                boolean ganhou = false;

                // contagem de vidas
                do {
                        limparTela();

                        System.out.println("\n\nVidas Restantes: " + vidasRestantes);
                        System.out.println("Letras já Tentadas: " + letrasTentadas + "\n");

                        exibeForca(vidasRestantes);
                        exibePalavraTela(palavra, letrasCertas);

                        System.out.println("\n\n");

                        // impedir letras já tentadas
                        while (true) {
                                System.out.print("Digite uma letra: ");
                                String entrada = teclado.nextLine().toLowerCase();

                                // evita vazio
                                if (entrada.isEmpty())
                                        continue;

                                letraChutada = entrada.charAt(0);

                                if (letrasTentadas.contains(Character.toString(letraChutada))) {
                                        System.out.println("Você já tentou essa letra. Digite outra!");
                                } else {
                                        break;
                                }
                        }

                        // atualiza letras tentadas
                        letrasTentadas += letraChutada;

                        // verifica acerto
                        if (acertouLetra(palavra, letraChutada))
                                letrasCertas += letraChutada;
                        else
                                vidasRestantes--;

                        // verificar se a palavra foi descoberta
                        if (palavraCompleta(palavra, letrasCertas)) {
                                ganhou = true;
                                break;
                        }

                } while (vidasRestantes > 0);

                // mensagem final
                System.out.println("\n======================================");

                if (ganhou) {
                        System.out.println("PARABÉNS! Você ganhou!");
                } else {
                        limparTela();
                        System.out.println("Você perdeu!");
                        System.out.println("\nA palavra era: " + palavra + "\n");
                        exibeForca(0);
                }

                System.out.println("");

                teclado.close();
        }

        static boolean acertouLetra(String palavra, char letraChutada) {
                return palavra.contains(Character.toString(letraChutada));
        }

        static void exibePalavraTela(String palavraSecreta, String letrasCertas) {
                char letra;
                System.out.println("\n\n");

                for (int posicaoLetra = 0; posicaoLetra < palavraSecreta.length(); posicaoLetra++) {
                        letra = palavraSecreta.charAt(posicaoLetra);

                        if (letrasCertas.contains(Character.toString(letra))) {
                                System.out.print("  _" + letra + "_  ");
                        } else {
                                System.out.print("  ____  ");
                        }
                }
        }

        // verifica se todas as letras foram descobertas
        static boolean palavraCompleta(String palavra, String letrasCertas) {
                for (int i = 0; i < palavra.length(); i++) {
                        char letra = palavra.charAt(i);
                        if (!letrasCertas.contains(Character.toString(letra))) {
                                return false;
                        }
                }
                return true;
        }
        
        // limpa a tela do console
        static void limparTela() {
                try {
                        // Para Windows
                        if (System.getProperty("os.name").toLowerCase().contains("win")) {
                                new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                        } else {
                                // Linux / Mac
                                System.out.print("\033[H\033[2J");
                                System.out.flush();
                        }
                } catch (Exception e) {
                        // Se não funcionar, imprime várias linhas para "simular" limpeza
                        for (int i = 0; i < 50; i++)
                                System.out.println();
                }
        }

        static void exibeForca(int contagemErro) {
                switch (contagemErro) {
                        case 6:
                                System.out.println("""
                                                    +---+
                                                    |   |

                                                        |
                                                        |
                                                        |
                                                        |
                                                ========= """);
                                break;

                        case 5:
                                System.out.println("""
                                                    +---+
                                                    |   |
                                                    O   |
                                                        |
                                                        |
                                                        |
                                                ========= """);
                                break;

                        case 4:
                                System.out.println("""
                                                    +---+
                                                    |   |
                                                    O   |
                                                    |   |
                                                        |
                                                        |
                                                ========= """);
                                break;

                        case 3:
                                System.out.println("""
                                                    +---+
                                                    |   |
                                                    O   |
                                                   /|   |
                                                        |
                                                        |
                                                ========= """);
                                break;

                        case 2:
                                System.out.println("""
                                                    +---+
                                                    |   |
                                                    O   |
                                                   /|\\  |
                                                        |
                                                        |
                                                ========= """);
                                break;

                        case 1:
                                System.out.println("""
                                                    +---+
                                                    |   |
                                                    O   |
                                                   /|\\  |
                                                   /    |
                                                        |
                                                ========= """);
                                break;

                        case 0:
                                System.out.println("""
                                                    +---+
                                                    |   |
                                                    O   |
                                                   /|\\  |
                                                   / \\  |
                                                        |
                                                ========= """);
                                break;

                        default:
                                break;
                }
        }

}

---

**Complementos (mais completo e fácil de entender)**

### 1) Visão geral do seu jogo (o “ciclo” principal)
Seu jogo funciona como um **loop principal** (o `do { ... } while (vidasRestantes > 0);`) que repete:

1. Limpa a tela e mostra o estado atual do jogo (vidas + letras tentadas)
2. Desenha a forca (de acordo com as vidas)
3. Mostra a palavra “escondida” com as letras já descobertas
4. Pede uma letra do usuário (com validação)
5. Atualiza o estado (acertou? adiciona em letrasCertas / errou? perde vida)
6. Verifica se o jogador ganhou (palavra completa) e pode encerrar o loop

Esse padrão (mostrar estado → ler entrada → processar → checar fim) é o padrão clássico de jogos e menus em console.

---

### 2) O que cada variável “representa” na prática
- `vidasRestantes`: quantas tentativas ainda existem (começa em 6 e vai até 0)
- `letrasTentadas`: um “histórico” das letras que o jogador já chutou
- `letrasCertas`: as letras que o jogador acertou (usadas para revelar a palavra)
- `ganhou`: uma “flag” (variável de controle) que guarda se o jogador venceu
- `palavra`: a palavra secreta (no seu caso fixada como `"treme"`)

**Por que usar `ganhou`?**  
Porque o loop pode terminar de dois jeitos:
- ganhou (descobriu a palavra) → você dá `break`
- perdeu (vidas chegaram a 0) → condição do `while` encerra

A flag deixa claro qual foi o motivo do término.

---

### 3) Entrada do usuário (por que seu `while(true)` é uma boa ideia)
Você fez algo muito usado em programas reais:

- Um loop “infinito” (`while (true)`)
- Que só sai quando a entrada é válida (`break`)
- E repete quando a entrada é inválida (`continue` ou só não dá `break`)

O que você validou muito bem:
- não aceitar string vazia
- não aceitar letra repetida (já tentada)

**Dica extra de validação (conceito):**
- garantir que o caractere digitado seja uma letra (e não número/símbolo)
- aceitar apenas 1 caractere (ou pelo menos avisar o usuário)

Exemplo de regra simples (conceito):
- se o usuário digitar “ab”, você pega só o `a`. Isso funciona, mas pode confundir.
- você pode avisar “Digite apenas uma letra”.

---

### 4) Como a palavra aparece na tela (por que esse método é importante)
O método `exibePalavraTela(palavra, letrasCertas)` varre cada caractere da palavra e decide:

- se a letra está em `letrasCertas` → imprime `_letra_`
- senão → imprime `____`

Ou seja, ele é o “renderizador” do jogo: ele transforma o estado (`letrasCertas`) em uma visualização.

**Observação importante (comportamento):**
No seu loop, você exibe a palavra **antes** do chute.
Depois que o jogador chuta uma letra, você não exibe novamente a palavra atualizada antes de ganhar/perder.

Isso não quebra o jogo, mas:
- o usuário pode não “ver” imediatamente a atualização no momento do acerto
- na vitória, você mostra “PARABÉNS!” mas não mostra a palavra completa

Uma forma simples (conceito) de deixar mais claro é exibir a palavra novamente após atualizar `letrasCertas` / `vidasRestantes`.

---

### 5) Como você detecta vitória (muito bem feito)
O método `palavraCompleta(palavra, letrasCertas)` faz:

- percorre cada letra da palavra
- se existir alguma letra que não esteja em `letrasCertas` → retorna `false`
- se passou por todas → retorna `true`

Isso é perfeito porque:
- funciona mesmo se a palavra tiver letras repetidas (ex: “arara”)
- independe da ordem dos chutes

---

### 6) Como a forca funciona (e por que o switch é ideal aqui)
Você usou `switch (contagemErro)` para desenhar cada estágio.

Ponto forte:
- fica super visual e fácil de manter
- cada “vida” tem um desenho

Dica de leitura:
- Repare que você está usando `vidasRestantes` para decidir o desenho.
- Ou seja: “quanto menos vidas, mais completa fica a forca”.

---

### 7) Melhorias “naturais” para deixar o jogo mais completo (idéias)
Sem mudar seu estilo, aqui vão melhorias bem comuns e fáceis de justificar:

- **Lista de palavras com sorteio**:
  - em vez de `String palavra = "treme";`
  - ter um vetor `String[] palavras = {...}` e sortear uma delas
- **Exibir mensagem ao acertar/errar**:
  - “Você acertou!” / “Você errou!”
- **Impedir que o usuário chute a palavra toda** (se quiser manter só letra)
- **Reiniciar jogo (jogar novamente)**:
  - ao final perguntar “Deseja jogar novamente? (s/n)”
- **Melhorar o armazenamento de letras tentadas**:
  - hoje você usa `String` e `contains`
  - dá pra evoluir depois para estruturas como `Set<Character>` (mais eficiente e mais “sem repetição” por natureza)
- **Evitar concatenação excessiva de String** (conceito):
  - `letrasTentadas += letraChutada;` é ok para pequeno
  - mas em programas grandes é comum usar `StringBuilder`

Essas melhorias são ótimas para você evoluir o projeto sem complicar demais.

---

### 8) Resumo do que você aplicou de conceitos (bem completo)
No seu código você treinou, na prática:

- **laço `do...while`** (loop principal do jogo)
- **laço `while(true)`** (validação de entrada até ser válida)
- **condicionais** (`if/else` para acerto/erro e para fim do jogo)
- **funções (métodos)** com retorno (`acertouLetra`, `palavraCompleta`)
- **procedimentos (void)** para exibir (`exibeForca`, `exibePalavraTela`, `limparTela`)
- **uso de String** (`contains`, `charAt`, `toLowerCase`)

Isso é exatamente o que torna esse desafio bom: ele junta vários fundamentos num único programa.

<!-- nav_start -->
---
Anterior: [131 Pedra Papel Tesoura Vetor](../docs/131_Pedra_Papel_Tesoura_Vetor.md) | Proximo: [133 Sorteio Unico](../docs/133_Sorteio_Unico.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
