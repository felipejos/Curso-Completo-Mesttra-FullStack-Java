# Exemplo: Cálculo Números Primos

Cálculo de números primos.

    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite um número: ");
            int limite = teclado.nextInt();

            int num = 2; // primeiro número primo

            do {
                if (ehPrimo(num)) {
                    System.out.println(num);
                }
                num++;
            } while (num <= limite);
        }

        // Função que verifica se um número é primo
        public static boolean ehPrimo(int n) {
            if (n < 2) return true;

            // testa se existe algum número primo entre 2 e a raiz quadrada do número testado
            // se até a raiz quadrada não foi encontrado um número primo, depois da raiz quadrada
            // nunca existirá um número primo com base nas caractéristicas de números múltiplos
            for (int i = 2; i <= Math.sqrt(n); i++) {
                if (n % i == 0) {
                    return false;
                }
            }
            return true;
        }
    }

---

## Complemento: como esse algoritmo funciona (bem explicado)

### 1) O objetivo do programa
Você digita um número `limite` e o programa **imprime todos os números primos de 2 até `limite`**.

Exemplo:
- Entrada: `10`
- Saída esperada: `2 3 5 7`

---

### 2) O papel do `do...while` aqui
O programa começa com:

- `num = 2` (primeiro candidato a primo)
- Enquanto `num <= limite`:
  - verifica se `num` é primo
  - se for, imprime
  - incrementa `num`

Isso garante que o programa:
- testa todos os números de 2 até o limite
- **executa pelo menos uma vez** (mesmo se o limite for pequeno)

---

### 3) O que significa “ser primo”?
Um número é primo quando:
- é maior ou igual a 2
- e **só pode ser dividido por 1 e por ele mesmo**
- ou seja, não pode ter nenhum divisor inteiro entre 2 e `n-1`

Exemplos:
- 2 (primo)
- 3 (primo)
- 4 (não é primo, pois 4 % 2 == 0)
- 9 (não é primo, pois 9 % 3 == 0)

---

### 4) Por que testar apenas até a raiz quadrada?
Se um número `n` **não tem divisores até** `sqrt(n)`, então ele não terá divisores maiores que isso também.

Por quê?
- Todo divisor de `n` vem em par: `a * b = n`
- Se `a` é pequeno, `b` é grande
- Quando `a` passa de `sqrt(n)`, o `b` obrigatoriamente fica menor que `sqrt(n)`
- Então, se existisse divisor, ele teria aparecido antes da raiz

Por isso o laço faz:
- `i = 2` até `i <= sqrt(n)`

Isso deixa o algoritmo bem mais rápido.

---

### 5) Observação importante: existe um erro lógico na função `ehPrimo`
No seu código está assim:

    if (n < 2) return true;

Mas para números menores que 2 (0, 1 e negativos), o correto é:
- eles **não são primos**

Então o correto seria:

    if (n < 2) return false;

Esse detalhe muda bastante a lógica, especialmente se o código for reutilizado em outros contextos.

---

### 6) Cenários para você visualizar

#### Se o limite for 2
- `num = 2`
- `ehPrimo(2)` → true
- imprime 2
- incrementa para 3
- 3 <= 2 → falso → para

#### Se o limite for 1
- `num = 2`
- executa o bloco uma vez por ser `do...while`
- imprime nada (pois 2 não está <= 1 na condição final, mas só é testado depois)
- quando chega na condição: 3 <= 1 → falso → encerra

Isso mostra a característica do `do...while`: **executa primeiro, verifica depois**.

---

### 7) Dica para deixar mais seguro (conceito)
Se o usuário digitar um valor inválido (texto), `nextInt()` vai gerar erro.
E também, se o usuário digitar um limite menor que 2, você pode:
- exibir uma mensagem dizendo que não existe primo naquele intervalo

Isso deixa o programa mais “amigável” para quem está usando.

---

<!-- nav_start -->
---
Anterior: [Exemplo: Lendo valores atÃ© um nÃºmero especÃ­fico](../docs/115_Lendo_Valores.md) | Próximo: [Exemplo: CÃ¡lculo de mÃ©dia de mÃºltiplos valores](../docs/117_Media_Multiplos_Valores.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

