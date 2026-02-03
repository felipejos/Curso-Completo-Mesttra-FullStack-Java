# Exemplo: Lendo valores até um número específico

Realiza a leitura de valores até que uma condição ocorra.

    import java.util.Scanner;

    public class ExemploDoWhile {
        public static void main(String[] args) {
            Scanner teclado= new Scanner(System.in);

            int numero;
            System.out.println("Digite números positivos (negativo encerra):");

            do {
                System.out.print("Número: ");
                numero = teclado.nextInt();
            } while (numero >= 0);

            System.out.println("Encerrado porque foi digitado um número negativo.");
        }
    }

---

## Complemento: entendendo o fluxo desse `do...while` (passo a passo)

### 1) Qual é a regra do jogo?
- O programa **continua pedindo números** enquanto o usuário digitar **0 ou positivo**.
- Quando o usuário digitar **um número negativo**, o laço **para**.

A condição é:
- `numero >= 0`  → continua
- `numero < 0`   → encerra

---

### 2) Por que `do...while` é ideal aqui?
Porque queremos garantir que:
- o usuário **digite pelo menos um número** antes de qualquer verificação.

No `do...while`:
- primeiro o bloco executa (pergunta e lê)
- depois a condição é testada
- se a condição for verdadeira, repete

---

### 3) Visualizando o fluxo de execução
O programa funciona assim:

1. Mostra a mensagem inicial
2. Executa o bloco:
   - pergunta “Número: ”
   - lê o valor
3. Verifica:
   - se `numero >= 0`, volta e pede de novo
   - se `numero < 0`, sai do laço
4. Imprime a mensagem final

---

### 4) O que acontece em cada tipo de entrada?

#### Se o usuário digitar `5`
- `numero = 5`
- `5 >= 0` → verdadeiro → repete

#### Se o usuário digitar `0`
- `numero = 0`
- `0 >= 0` → verdadeiro → repete  
(0 conta como “não negativo”, então continua)

#### Se o usuário digitar `-3`
- `numero = -3`
- `-3 >= 0` → falso → encerra

---

### 5) Ponto importante: cuidado com entradas inválidas
Se o usuário digitar texto (ex: `abc`) em vez de número, o `nextInt()` vai gerar erro (InputMismatchException).

Para deixar o algoritmo mais robusto, você pode:
- envolver a leitura em `try/catch`
- consumir o buffer quando ocorrer erro
- pedir novamente até o usuário digitar um inteiro válido

Isso é comum em programas interativos.

---

### 6) Pequena melhoria de usabilidade (conceito)
Esse exemplo encerra em **qualquer negativo**.
Você pode adaptar facilmente para:
- encerrar apenas quando o usuário digitar um número específico (ex: `-1`)
- ou somar os números até encerrar
- ou contar quantos números foram digitados

A lógica do laço continua a mesma: **executa pelo menos uma vez e para quando a condição ficar falsa**.

---

<!-- nav_start -->
---
Anterior: [Exemplo: IteraÃ§Ã£o sobre caracteres](../docs/114_Iteracao_Caracteres.md) | Próximo: [Exemplo: CÃ¡lculo NÃºmeros Primos](../docs/116_Numeros_Primos.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

