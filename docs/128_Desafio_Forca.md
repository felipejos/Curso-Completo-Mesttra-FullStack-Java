Desafio: Jogo da Forca


Abaixo temos um esqueleto do código do jogo da forca. Tente a partir das dicas, implementar o código completo.



Este vídeo mostra a aplicação em funcionamento para auxiliar no entendimento do código.

https://youtu.be/OGoLkleEGys



import java.util.Scanner;

public class App {

    public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int vidasRestantes = 6;
            String letrasCertas = "";
            String letrasTentadas = "";
            char letraChutada;
            
            String palavra = "treme";

            //contagem de vidas
            do {
                System.out.println("\n\nVidas Restantes: " + vidasRestantes);
                System.out.println("Letras já Tentadas: " + letrasTentadas + "\n");

                exibeForca(vidasRestantes);
                exibePalavraTela(palavra, letrasCertas);

                System.out.println("\n\n");
                System.out.print("\nDigite uma letra: "); 
                //TODO 02: caso o usuario digite uma letra ja tentada, peça uma nova letra
                //ate que seja informado uma letra que ainda nao foi tentada

                letraChutada = teclado.nextLine().toLowerCase().charAt(0);
                
                //atualiza a lista de letras tentadas
                letrasTentadas += letraChutada;

                //atualiza a lista de letras certas
                if (acertouLetra(palavra, letraChutada))
                    letrasCertas += letraChutada;
                else 
                    //tira uma vida
                    vidasRestantes--;
                
                exibePalavraTela(palavra, letrasCertas);
     
                //TODO 03: implemente um bloco de código que verifique
                //se o usuario já descobriu todas as letras da palavra.
                //Uma possibilidade seria aproveitar o exibePalavraTela
                //para descobrir isto. Provavelmente tenha que mudar de void
                //para um metodo que retorna o valor


                System.out.println();
            } while (vidasRestantes > 0);


            //TODO 04: implemente aqui neste ponto, um bloco de comandos
            //que informe uma mensagem dizendo se o jogador ganhou ou perdeu
            //se ele perdeu além da mensagem deve ser exibido a forca completa

            teclado.close();
    }
          
    static boolean acertouLetra(String palavra, char letraChutada){
        return palavra.contains(Character.toString(letraChutada));
    }

    static void exibePalavraTela(String palavraSecreta, String letrasCertas){
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

    static void exibeForca(int contagemErro){
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
            //TODO 01: implemente aqui o desenho da forca quando a 
            //qtde de vidas restantes for 5, 4, 3, 2, 1
            default:
                break;
        }
    }

        
        //     +---+
        //     |   |
        //         |
        //         |
        //         |
        //         |
        //   =========
           
        //     +---+
        //     |   |
        //     O   |
        //         |
        //         |
        //         |
        //   =========
           
        //     +---+
        //     |   |
        //     O   |
        //     |   |
        //         |
        //         |
        //   =========
           
        //     +---+
        //     |   |
        //     O   |
        //    /|   |
        //         |
        //         |
        //   =========
           
        //     +---+
        //     |   |
        //     O   |
        //    /|\\  |
        //         |
        //         |
        //   =========
           
        //     +---+
        //     |   |
        //     O   |
        //    /|\\  |
        //    /    |
        //         |
        //   =========
           
        //     +---+
        //     |   |
        //     O   |
        //    /|\\  |
        //    / \\  |
        //         |
        //   ========= 
          
            
}

---

**Complementos (implementação completa seguindo os TODOs, mantendo a ideia do seu esqueleto)**

> **Observação importante:** aqui eu não apago nem altero o seu código acima. Abaixo está uma **versão completa** (com os TODOs resolvidos) para você comparar e copiar se quiser.

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

            do {
                System.out.println("\n\nVidas Restantes: " + vidasRestantes);
                System.out.println("Letras já Tentadas: " + letrasTentadas + "\n");

                exibeForca(vidasRestantes);
                exibePalavraTela(palavra, letrasCertas);

                System.out.println("\n\n");
                System.out.print("\nDigite uma letra: ");

                // TODO 02: se a letra já foi tentada, pede outra até ser inédita
                do {
                    String entrada = teclado.nextLine().toLowerCase();

                    // garante que o usuário digitou pelo menos 1 caractere
                    if (entrada.length() == 0) {
                        System.out.print("Você não digitou nada. Digite uma letra: ");
                        continue;
                    }

                    letraChutada = entrada.charAt(0);

                    // verifica se já foi tentada
                    if (letrasTentadas.contains(Character.toString(letraChutada))) {
                        System.out.print("Você já tentou essa letra. Digite outra: ");
                    } else {
                        break; // letra válida e inédita
                    }

                } while (true);

                // atualiza a lista de letras tentadas
                letrasTentadas += letraChutada;

                // atualiza a lista de letras certas ou perde vida
                if (acertouLetra(palavra, letraChutada)) {
                    letrasCertas += letraChutada;
                } else {
                    vidasRestantes--;
                }

                // TODO 03: descobrir se já acertou a palavra inteira
                // solução: criar uma função que verifica se todas as letras da palavra estão em letrasCertas
                ganhou = descobriuPalavra(palavra, letrasCertas);

                System.out.println();
            } while (vidasRestantes > 0 && !ganhou);

            // TODO 04: mensagem final e forca completa se perdeu
            if (ganhou) {
                System.out.println("\n🎉 Parabéns! Você ganhou! A palavra era: " + palavra);
            } else {
                System.out.println("\n💀 Você perdeu! A palavra era: " + palavra);
                exibeForca(0); // forca completa
            }

            teclado.close();
        }

        static boolean acertouLetra(String palavra, char letraChutada) {
            return palavra.contains(Character.toString(letraChutada));
        }

        // Função do TODO 03
        static boolean descobriuPalavra(String palavra, String letrasCertas) {
            for (int i = 0; i < palavra.length(); i++) {
                char letra = palavra.charAt(i);
                if (!letrasCertas.contains(Character.toString(letra))) {
                    return false;
                }
            }
            return true;
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

        // TODO 01 completo (desenho por vidas restantes)
        static void exibeForca(int vidasRestantes) {
            switch (vidasRestantes) {
                case 6:
                    System.out.println("""
                            +---+
                            |   |
                                |
                                |
                                |
                                |
                        =========""");
                    break;
                case 5:
                    System.out.println("""
                            +---+
                            |   |
                            O   |
                                |
                                |
                                |
                        =========""");
                    break;
                case 4:
                    System.out.println("""
                            +---+
                            |   |
                            O   |
                            |   |
                                |
                                |
                        =========""");
                    break;
                case 3:
                    System.out.println("""
                            +---+
                            |   |
                            O   |
                           /|   |
                                |
                                |
                        =========""");
                    break;
                case 2:
                    System.out.println("""
                            +---+
                            |   |
                            O   |
                           /|\\  |
                                |
                                |
                        =========""");
                    break;
                case 1:
                    System.out.println("""
                            +---+
                            |   |
                            O   |
                           /|\\  |
                           /    |
                                |
                        =========""");
                    break;
                default: // 0 ou menos -> enforcado completo
                    System.out.println("""
                            +---+
                            |   |
                            O   |
                           /|\\  |
                           / \\  |
                                |
                        =========""");
                    break;
            }
        }
    }

---

### 1) Como cada TODO foi resolvido (bem direto)
- **TODO 01:** completar o `switch` da forca com os desenhos para 5,4,3,2,1 e o final (0).
- **TODO 02:** criar um `do { ... } while(true)` só para ler a letra, repetindo enquanto:
  - o usuário não digitou nada, ou
  - digitou uma letra que já está em `letrasTentadas`
- **TODO 03:** criar a função `descobriuPalavra(palavra, letrasCertas)` que percorre a palavra e verifica se cada letra já foi descoberta.
- **TODO 04:** após sair do laço, se `ganhou == true` mostra vitória, senão mostra derrota e imprime a forca completa.

---

### 2) Dicas práticas (o que mais costuma dar errado nesse desafio)
- **Entrada vazia:** `nextLine()` pode vir vazio, então trate `entrada.length() == 0`.
- **Repetição de letras:** usar `letrasTentadas.contains(...)` resolve de forma simples.
- **Ganho sem precisar “montar string”:** a verificação “letra por letra” é a forma mais fácil de saber se venceu.
- **Forca final:** chamar `exibeForca(0)` é um truque simples para sempre mostrar a última fase.

---

<!-- nav_start -->
---
Anterior: [AplicaÃ§Ã£o com Menu de Escolha](../docs/127_Menu_de_Escolha.md) | Próximo: [Desafio: Gerenciador de Habitantes](../docs/129_Gerenciador_Habitantes.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

