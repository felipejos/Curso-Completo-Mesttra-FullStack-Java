# Analogia de uma Repetição no mundo real


História: A busca pelo caderno raro
Maria precisava encontrar um caderno de capa azul com folhas pontilhadas, um modelo que usava para organizar seus estudos. O problema é que esse caderno era difícil de achar. Mesmo assim, ela decidiu que iria procurar loja por loja até encontrar.

Início da busca
Maria saiu de casa bem cedo, determinada.
Ela entrou na primeira papelaria que encontrou e perguntou:

— “Bom dia! Vocês têm o caderno de capa azul com folhas pontilhadas?”

A atendente respondeu:

— “Infelizmente, não temos esse modelo.”

Maria agradeceu, saiu da loja e pensou:

“Tudo bem. Ainda há muitas lojas pela frente. Vou continuar procurando.”

A repetição da ação
Então Maria seguiu para outra papelaria.
E repetiu todo o processo:

Entrou na loja.

Perguntou pelo caderno.

Recebeu a resposta.

Caso a loja não tivesse, continuava a busca.

E assim ela foi:

na segunda loja,

na terceira,

na quarta…

Em todas, ouviu respostas parecidas:

— “Esse modelo acabou.”
— “Não trabalhamos com esse tipo.”
— “Só temos capa vermelha.”

Mas ela não desistiu, porque sua busca continuava enquanto ela não encontrasse o produto desejado.

Até que…
Já quase no fim da tarde, Maria entrou em mais uma papelaria, um pouco cansada, mas ainda esperançosa.

Perguntou ao vendedor:

— “Boa tarde! Vocês têm um caderno de capa azul com folhas pontilhadas?”

O vendedor sorriu e respondeu:

— “Temos sim! Acabou de chegar um lote novo.”

Maria ficou aliviada. Finalmente havia encontrado exatamente o que procurava.

A condição que encerra a repetição
Ao encontrar a loja que possuía o caderno, Maria encerrou sua busca.
Não havia mais necessidade de continuar indo de loja em loja.

Como essa história representa o funcionamento do do…while?
Maria entra pelo menos uma vez em uma loja (assim como o do…while sempre executa o bloco inicial).

Depois dessa primeira visita, ela verifica a resposta do vendedor.

Se não encontrou o que queria, ela repete a ação e vai para outra loja.

Quando finalmente encontra o produto, a repetição é encerrada.

Ou seja:

Maria pergunta → verifica a resposta → continua enquanto não encontrou o produto.

Esta história pode ser representada pela estrutura de repetição abaixo:



FAÇA
    Ir até a próxima loja
    Entrar na loja
    Perguntar ao vendedor se há o caderno de capa azul com folhas pontilhadas
    Receber a resposta do vendedor (tem ou não tem)
ENQUANTO (a resposta for "NÃO TEM O CADERNO")
Explicação:

FAÇA (início)

representa o início do bloco que será executado pelo menos uma vez;

BLOCO DE COMANDOS QUE PODEM SER REPETIDOS

Maria vai até uma loja.

Maria entra na loja e faz a pergunta.

Vendedor da a resposta.

ENQUANTO (condição)

enquanto a condição der resultado verdadeiro, o bloco de comandos continua sendo executado. Neste caso, o código volta novamente para a primeira linha do bloco. No caso deste exemplo, "Ir até a próxima loja".

quando a condição se torna falsa (ou seja, quando uma loja tem o caderno), o laço termina. 

No próximo texto, você verá o funcionamento da estrutura Do While, que é justamente a esturura em java que exemplica na programação este cenário apontado no texto.

---

## Complemento: conectando a história com `do...while` em Java (sem complicar)

### Por que essa história é um `do...while` e não um `while`?
Porque a Maria **precisa entrar em pelo menos uma loja** antes de saber se tem o caderno.

- Se fosse `while`, o programa teria que **verificar a condição antes de executar** (antes de “entrar na loja”).
- No mundo real, ela **entra, pergunta e só depois descobre** a resposta.

Isso é exatamente o comportamento do `do...while`:
- **Executa primeiro**
- **Verifica depois**
- Repete se a condição continuar verdadeira

---

## A mesma história em linguagem de programação (passo a passo)

### 1) Variáveis “do mundo real”
- `resposta` → o que o vendedor disse (ex: "TEM" ou "NÃO TEM")
- `loja` → contador de lojas visitadas (opcional, mas ajuda a entender)

O loop vai continuar **enquanto** a resposta for “NÃO TEM”.

---

## Exemplo em Java (em formato bem iniciante)

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            String resposta;
            int loja = 0;

            do {
                loja++;

                System.out.println("\nMaria entrou na loja #" + loja);
                System.out.print("Vendedor: tem o caderno? (digite TEM ou NAO): ");
                resposta = teclado.nextLine().trim().toUpperCase();

            } while (resposta.equals("NAO"));

            System.out.println("\nAchou! Maria encontrou o caderno na loja #" + loja);

            teclado.close();
        }
    }

### Como ler esse código como se fosse um “roteiro”
1. Maria en

<!-- nav_start -->
---
Anterior: [Estruturas de RepetiÃ§Ã£o](../docs/108_Estruturas_Repeticao_2.md) | Próximo: [Conceito Do While](../docs/110_Do_While.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

