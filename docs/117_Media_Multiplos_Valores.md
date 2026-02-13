# Exemplo: Cálculo de média de múltiplos valores

Realiza a leitura de múltiplos valores e cálcula a média destes valores usando o conceito de variável acumuladora e contadora.

    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            // variaveis contadoras e acumuladoras necessitam 
            // de inicializacao igual a zero normalmente
            double soma = 0;
            int contador = 0;

            char resposta;

            System.out.print(" ========= Cálculo de Média =========  ");

            do {
                System.out.print("Digite um valor: ");
                double valor = teclado.nextDouble();

                // realiza a acumulacao dos valores digitados
                soma += valor;
                // realiza a contagem dos valores digitados
                contador++;

                System.out.print("Deseja digitar outro valor? (s/n): ");
                //obtem o primeiro caractere digitado pelo usuario
                resposta = teclado.nextLine().charAt(0);
                
            // como o usuario pode digitar 's' ou 'S' valida os dois casos
            } while (resposta == 's' || resposta == 'S'); 

            if (contador > 0) {
                double media = soma / contador;
                System.out.println("A média dos valores digitados é: " + media);
            } else {
                System.out.println("Nenhum valor foi digitado.");
            }

            teclado.close();
        }
    }

---

## Complemento: o que são “acumuladora” e “contadora” (do jeito mais fácil)

### Variável acumuladora
É uma variável que **vai juntando (somando)** valores ao longo do tempo.

Neste exemplo:
- `soma` começa com `0`
- a cada número digitado, você faz `soma += valor`
- no final, `soma` contém **a soma de todos os valores digitados**

Exemplo:
- digitou 10, depois 5, depois 3  
- `soma` vira: 0 → 10 → 15 → 18

### Variável contadora
É uma variável que **conta quantas vezes algo aconteceu**.

Neste exemplo:
- `contador` começa com `0`
- a cada número digitado, você faz `contador++`
- no final, `contador` contém **quantos valores foram digitados**

Exemplo:
- digitou 3 valores  
- `contador` vira: 0 → 1 → 2 → 3

---

## Complemento: como a média é calculada
A média é sempre:

- `média = soma / quantidade`

No seu código:
- `media = soma / contador`

Exemplo completo:
- valores: 10, 5, 3
- soma = 18
- contador = 3
- média = 18 / 3 = 6

---

## Complemento: ponto de atenção (bug comum com Scanner)
No seu código, esta linha pode dar erro ou “pular” a leitura:

    resposta = teclado.nextLine().charAt(0);

Motivo:
- você usou `nextDouble()`, que **não consome a quebra de linha**
- aí o `nextLine()` pega a quebra de linha vazia e retorna uma string vazia
- `charAt(0)` em string vazia causa erro (`StringIndexOutOfBoundsException`)

A correção mais simples mantendo sua lógica é consumir o “enter” antes:

- depois do `nextDouble()` e antes do `nextLine()`:

    teclado.nextLine(); // consome o ENTER pendente

Ficaria assim (só o trecho):

    double valor = teclado.nextDouble();
    teclado.nextLine(); // consome a quebra de linha

    System.out.print("Deseja digitar outro valor? (s/n): ");
    resposta = teclado.nextLine().charAt(0);

---

## Complemento: por que o do...while é ideal aqui?
Porque você quer:
- pedir pelo menos **um valor**
- e só depois perguntar se quer continuar

O fluxo fica natural:
1. digita um valor
2. soma e conta
3. pergunta se quer continuar
4. repete se for `s` ou `S`

---

<!-- nav_start -->
---
Anterior: [116 Numeros Primos](../docs/116_Numeros_Primos.md) | Proximo: [118 Contagem Caracteres](../docs/118_Contagem_Caracteres.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
