# Conceito Do While


O que é o do…while?
O do…while é uma estrutura de repetição usada para executar um bloco de instruções várias vezes, mas com uma característica muito particular:
o bloco é sempre executado pelo menos uma vez, independentemente da condição de repetição.

Isso acontece porque, no do…while, a condição é verificada somente depois que o bloco de comandos é executado.
Primeiro o programa faz, depois pergunta se deve repetir.

Na programação, existem 3 estruturas para repetir um código: 



- Do While;

- Do;

- For;



Podemos dizer que o Do While, consegue fazer o que o Do e o For, podem fazer. No entanto estes dois últimos (Do e For) podem ser usados em algums casos para escrever menos código do que se fossémos fazer com o Do While. Então dizemos, que se você entender como o Do While funciona, você entenderá os outros dois.



Como funciona o do…while em etapas?
Para entender bem o funcionamento, imagine o seguinte fluxo:

Executa o bloco de ações
O programa entra no bloco do do e executa todas as instruções dali sem verificar nenhuma condição.

Avalia a condição
Somente depois que o bloco termina, o programa verifica a condição do while.

Decide se repete ou não:

Se a condição for verdadeira, o bloco é executado novamente.

Se a condição for falsa, o laço é encerrado e o programa continua sua execução normal.

Essa ordem — executar primeiro, testar depois — é o que torna o do…while especial.

Por que ele sempre executa ao menos uma vez?
A resposta está na própria estrutura lógica:

No momento inicial, antes da primeira execução, nenhuma condição é avaliada.

Como o teste só acontece ao final, o primeiro ciclo ocorre sem qualquer restrição.

Essa característica é extremamente útil quando:

Você precisa garantir que o bloco rodará pelo menos uma vez.

A condição depende de algo que só pode ser obtido depois da primeira execução (por exemplo, ler uma entrada do usuário que será verificada só após ser digitada).

Quando o do…while é a melhor escolha?
O do…while é ideal quando a repetição depende de algo que será conhecido apenas após a primeira execução. Aqui estão alguns casos típicos:

Entrada obrigatória do usuário
Quando você precisa que o usuário forneça pelo menos uma vez um dado, e só depois decide se deve repetir o pedido.

Por exemplo:

pedir uma senha,

solicitar um número válido,

mostrar um menu interativo.

Nesse tipo de situação, você não sabe se a condição inicial será verdadeira ou falsa, então faz sentido executar o bloco pelo menos uma vez.

Processamentos que precisam acontecer antes da checagem
Às vezes você precisa realizar uma ação inicial para então verificar se deve continuar. Por exemplo:

iniciar uma leitura de arquivo,

gerar um valor aleatório que será testado depois,

realizar um cálculo inicial antes de saber se deve repetir.

Situações em que a lógica natural segue o fluxo “primeiro faz, depois verifica”
O do…while combina perfeitamente com operações que naturalmente exigem uma primeira execução obrigatória antes de qualquer decisão.

Características do do…while em comparação com outras estruturas
Sem mencionar diretamente os outros laços, podemos destacar as diferenças gerais:

1. Execução garantida na primeira vez
Essa é a marca registrada do do…while.
Ele sempre roda o bloco inicial, independentemente do estado inicial da condição.

Outros laços podem ou não executar o bloco, dependendo da condição inicial.
O do…while, não: ele faz antes de decidir.

2. Checagem de condição no final
Enquanto a maioria dos laços toma a decisão de executar ou não antes mesmo da primeira iteração, o do…while só avalia a condição depois.

Isso influenciará seu uso: ele é mais adequado quando já há algo concreto para ser analisado apenas após uma primeira execução.

3. Fluxo mais natural para interações
O do…while é especialmente útil em programas interativos — como menus, perguntas ao usuário e validações — porque essas situações geralmente pedem uma primeira execução obrigatória.

4. Mais intuitivo quando se pensa em “processo, e depois verificação”
Enquanto algumas estruturas são pensadas em torno de condições prévias, o do…while reflete processos reais em que você:

realiza uma ação inicial,

observa o resultado,

decide se continua.

Um resumo mental do do…while
“Faça isso pelo menos uma vez, e depois repita enquanto a condição for verdadeira.”

Essa frase resume perfeitamente o comportamento desse laço.

Conclusão
O do…while é uma estrutura de repetição especialmente útil quando:

você precisa garantir uma primeira execução do bloco,

a condição depende do resultado de algo feito internamente,

a repetição faz mais sentido quando ocorre após uma ação inicial,

você está lidando com interações ou verificações que só fazem sentido depois do primeiro passo.

Sua principal marca é o fato de avaliar a condição no final, tornando-o diferente das demais estruturas de repetição, que geralmente decidem antes se continuarão ou não.

---

## Complemento: como “enxergar” o do...while em Java (bem direto)

### Sintaxe (formato padrão)
A estrutura sempre segue este padrão:

    do {
        // bloco que executa pelo menos 1 vez
    } while (condicao);

Repare em 2 detalhes importantes:
- O `while (condicao)` vem **depois** do bloco.
- Existe um `;` (ponto e vírgula) **no final** do `while`.

---

## Complemento: o fluxo real (em português “de computador”)

Pense sempre assim:

1) Executa o bloco dentro do `do { ... }`  
2) Só depois verifica a condição do `while`  
3) Se a condição for `true` → volta e executa de novo  
4) Se a condição for `false` → sai do laço e segue o programa

Frase mental perfeita:
“Executa uma vez e repete se precisar.”

---

## Complemento: exemplo clássico (menu que precisa aparecer ao menos uma vez)

Este é o cenário mais comum do `do...while`: o menu precisa ser exibido, o usuário escolhe, e só então decidimos se repete.

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int opcao;

            do {
                System.out.println("\n=== MENU ===");
                System.out.println("1 - Cadastrar");
                System.out.println("2 - Listar");
                System.out.println("0 - Sair");
                System.out.print("Escolha: ");

                opcao = teclado.nextInt();

                if (opcao == 1) {
                    System.out.println("Cadastrando...");
                } else if (opcao == 2) {
                    System.out.println("Listando...");
                } else if (opcao != 0) {
                    System.out.println("Opção inválida!");
                }

            } while (opcao != 0);

            System.out.println("Programa encerrado.");
            teclado.close();
        }
    }

### Por que aqui é do...while?
Porque o menu **precisa aparecer pelo menos uma vez**.
Se fosse `while`, você teria que já ter uma opção antes de mostrar o menu, o que não faz sentido.

---

## Complemento: cuidado com “loop infinito”
Um loop infinito é quando a condição **nunca fica falsa**.

Exemplo de risco:
- Se você esquecer de atualizar a variável usada na condição.
- Ou se a condição estiver errada.

Dica prática:
Sempre procure responder 2 perguntas:
- “O que faz a repetição continuar?”
- “O que faz a repetição parar?”

Se você não conseguir apontar o “ponto de parada”, tem chance de ficar infinito.

---

## Complemento: quando escolher do...while na prática (regra simples)
Use `do...while` quando:

- Você precisa executar o bloco **pelo menos uma vez**.
- A condição depende de uma informação que só existe **depois** da primeira execução.
- Você está lidando com interação do usuário (menu, validação, repetição de tentativa).

---

<!-- nav_start -->
---
Anterior: [Analogia de uma RepetiÃ§Ã£o no mundo real](../docs/109_Analogia_Repeticao.md) | Próximo: [VÃ­deo: Do While](../docs/111_Video_Do_While.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

