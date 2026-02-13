# Exemplo: Identificar o maior e o menor valor

Algoritmo para identificar o maior e o menor valor digitado em uma sequência de valores digitados.

    import java.util.Scanner;

    public class App {
            public static void main(String[] args) {

                    Scanner teclado = new Scanner(System.in);

                    int numero;

                    int maior = Integer.MIN_VALUE;
                    int menor = Integer.MAX_VALUE;

                    do {
                            System.out.println("Digite um número ou 0 para encerrar: ");
                            numero = teclado.nextInt();

                            // não considera o valor definido para a parada
                            if (numero != 0) { 
                                    if (numero > maior) {
                                            maior = numero;
                                    } else if (numero < menor) {
                                            menor = numero;
                                    }
                            }

                    } while (numero != 0);

                    System.out.println("Maior valor: " + maior);
                    System.out.println("Menor valor: " + menor);

                    teclado.close();
            }
    }

---

## Complemento: o que esse algoritmo faz

Esse programa lê vários números digitados pelo usuário e, ao final, mostra:

- **o maior número** digitado
- **o menor número** digitado

A leitura continua **até o usuário digitar 0** (o 0 funciona como “valor de parada”).

---

## Complemento: por que `Integer.MIN_VALUE` e `Integer.MAX_VALUE`?

Você inicializou assim:

- `maior = Integer.MIN_VALUE` (o menor inteiro possível)
- `menor = Integer.MAX_VALUE` (o maior inteiro possível)

Isso é um truque muito usado para garantir que:

- qualquer número digitado (exceto 0) vai conseguir ser maior que `maior` no começo
- qualquer número digitado (exceto 0) vai conseguir ser menor que `menor` no começo

Exemplo rápido:
- `Integer.MIN_VALUE` é um número extremamente negativo
- então o primeiro número digitado (ex.: 7) será maior que isso e vira o novo `maior`

---

## Complemento: como o loop `do...while` funciona aqui

O `do...while` garante que o usuário **digite pelo menos um valor**.

Fluxo:

1. mostra a mensagem
2. lê o número
3. se o número não for 0:
   - compara com o maior
   - compara com o menor
4. repete enquanto o número for diferente de 0

---

## Complemento: detalhe importante na lógica do `menor`

No seu código, você colocou:

    if (numero > maior) {
            maior = numero;
    } else if (numero < menor) {
            menor = numero;
    }

Isso funciona na maioria dos casos, mas tem um detalhe:

- quando o número é maior que o `maior`, ele atualiza o maior,
- **mas não testa se ele também deveria atualizar o menor** (o que normalmente não precisa),
- porém existe um caso especial: **primeiro número digitado**.

### Exemplo do problema (primeiro número)
Suponha que o primeiro número digitado seja `10`:

- `maior` vira `10`
- mas o `menor` não é atualizado porque caiu no `if` e pulou o `else if`
- `menor` continua `Integer.MAX_VALUE`

No final, você pode acabar imprimindo um menor errado caso só tenha digitado um número.

---

## Complemento: como evitar esse caso (ideia de ajuste)

A forma mais segura é testar **independentemente**:

- atualiza maior se for maior
- atualiza menor se for menor

Ou seja, usar dois `if` separados dentro do `if (numero != 0)`:

    if (numero > maior) {
            maior = numero;
    }

    if (numero < menor) {
            menor = numero;
    }

Assim, no primeiro número digitado, ele atualiza os dois corretamente.

---

## Complemento: cuidado extra (e se o usuário digitar 0 logo de cara?)

Se a pessoa digitar `0` na primeira tentativa:
- o loop encerra
- `maior` continua `Integer.MIN_VALUE`
- `menor` continua `Integer.MAX_VALUE`

Nesse caso, faz sentido exibir uma mensagem tipo:
- “Nenhum número válido foi digitado.”

Uma forma simples de resolver é usar um contador ou um boolean para saber se foi digitado algum número válido.

---

<!-- nav_start -->
---
Anterior: [118 Contagem Caracteres](../docs/118_Contagem_Caracteres.md) | Proximo: [120 Exercicio 11](../docs/120_Exercicio_11.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
