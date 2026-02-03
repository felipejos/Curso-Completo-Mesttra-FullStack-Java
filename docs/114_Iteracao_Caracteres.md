# Exemplo: Iteração sobre caracteres

Uso do Do While em tarefas que envolvem uma contagem.

    public class IterarString {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite uma palavra: ");
            String texto = teclado.nextLine();

            int i = 0;

            // pega cada caractere individual da palavra e exibe na tela
            do {
                char c = texto.charAt(i);        // pega o caractere na posição i
                System.out.println("Caractere: " + c);
                i++;
            } while (i < texto.length());        // condição: ainda dentro do tamanho da string
        }
    }

---

## Complemento: o que esse exemplo ensina na prática

### 1) O que significa “iterar” uma String
Iterar é **percorrer item por item**.  
No caso da String, é **percorrer caractere por caractere** usando um índice (`i`).

- `i` começa em `0` porque **String em Java é indexada a partir do zero**
- `texto.length()` retorna a **quantidade total de caracteres**
- O último índice válido sempre é: `texto.length() - 1`

---

### 2) Por que o `do...while` funciona bem aqui
O `do...while` garante que o bloco rode **pelo menos uma vez**.

Isso faz sentido quando:
- você **tem certeza** que existe algo para processar (por exemplo, uma palavra não vazia)
- ou você quer “rodar uma vez e depois validar”

Mas aqui existe um detalhe importante…

---

### 3) Atenção: se o usuário digitar vazio, dá erro
Se o usuário apenas apertar Enter, `texto` vira `""` (string vazia).

- `texto.length()` será `0`
- o `do` executa **mesmo assim**
- e logo na primeira linha: `texto.charAt(0)` vai falhar

O erro seria:
- `StringIndexOutOfBoundsException`

Isso acontece porque você tentou acessar uma posição que não existe.

---

### 4) Melhorando a segurança sem mudar seu código original
Você pode manter esse exemplo e apenas **adicionar uma validação antes do do...while**:

Ideia:
- Se `texto.length() == 0`, mostrar mensagem e encerrar

Ou garantir que o usuário digite algo até ficar válido (aí sim o `do...while` faz ainda mais sentido).

---

### 5) Alternativa comum: usar `while` ou `for` nesse caso
Esse tipo de contagem (de 0 até o tamanho) costuma ficar bem natural com `for`:

- porque você já tem:
  - início: `i = 0`
  - condição: `i < texto.length()`
  - passo: `i++`

Mas o objetivo do seu exemplo é mostrar que **o do...while também serve para contagem**, desde que você cuide do caso de string vazia.

---

### 6) Resumo rápido do fluxo do seu código
- Lê uma palavra
- Cria contador `i = 0`
- Executa:
  - pega caractere na posição `i`
  - imprime
  - incrementa `i`
- Repete enquanto `i` ainda for menor que o tamanho da string

---

<!-- nav_start -->
---
Anterior: [Estruturas de RepetiÃ§Ã£o Do e For](../docs/113_Do_e_For.md) | Próximo: [Exemplo: Lendo valores atÃ© um nÃºmero especÃ­fico](../docs/115_Lendo_Valores.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

