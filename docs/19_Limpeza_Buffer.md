# Realizando a limpeza do buffer

---

## Realizando a limpeza do buffer

Seu código tá certinho e de repente um `teclado.nextLine()` ou `teclado.next()` retorna vazio?  
A classe `Scanner` do Java é uma ferramenta útil para lidar com a entrada do usuário. No entanto, ao usá-la, você pode encontrar problemas se não limpar o buffer de entrada corretamente.

---

## O que é o Buffer?

O **buffer** é uma área de armazenamento temporário na memória do computador que é usada para guardar dados enquanto eles estão sendo transferidos de um lugar para outro. Em Java, quando você usa a classe `Scanner` para ler a entrada do usuário, os dados são primeiro colocados no buffer antes de serem processados.

---

## Por que limpar o Buffer?

Se você não limpar o buffer após ler a entrada do usuário, os dados antigos ainda estarão presentes no buffer na próxima vez que você tentar ler a entrada. Isso pode causar problemas, pois você pode acabar lendo dados antigos em vez dos novos dados que o usuário acabou de inserir.

---

## Como limpar o Buffer?

Em Java, você pode limpar o buffer executando o comando `teclado.nextLine()` da classe `Scanner` após cada chamada de `nextInt()`, `nextDouble()`, etc.

---

## Exemplo

    import java.util.Scanner;

    public class Main {
      public static void main(String[] args) {
          Scanner teclado = new Scanner(System.in);

          System.out.println("Digite um número: ");
          int number = teclado.nextInt();

          teclado.nextLine();  // Limpa o buffer

          System.out.println("Digite uma linha de texto: ");
          String text = teclado.nextLine();

          System.out.println("Número: " + number);
          System.out.println("Texto: " + text);
      }
    }

Neste exemplo, após ler um número inteiro do usuário com `nextInt()`, chamamos `nextLine()` para limpar o buffer antes de ler uma linha de texto com `nextLine()`. Isso garante que a linha de texto não seja contaminada por qualquer dado residual no buffer após a chamada para `nextInt()`.

---

## Vídeo complementar

https://www.youtube.com/watch?v=GVhqeZcVGTk

[![Assistir no YouTube](https://img.youtube.com/vi/GVhqeZcVGTk/hqdefault.jpg)](https://www.youtube.com/watch?v=GVhqeZcVGTk)

---

# Complemento da Lição

## 1) O que realmente “sobra” no buffer (bem direto)
Quando você digita no console e aperta ENTER, você envia:
- o valor (ex.: `10`)
- **e o ENTER** (quebra de linha `\n`)

Métodos como `nextInt()` leem o **número**, mas podem deixar o ENTER “sobrando”.  
Aí quando você chama `nextLine()`, ele lê essa quebra de linha e retorna **vazio**.

---

## 2) Regra de ouro (para não errar)
Se você usar:
- `nextInt()`, `nextDouble()`, `nextBoolean()`, `nextLong()`

e depois precisar ler texto com:
- `nextLine()`

então faça antes:
- `nextLine()` **uma vez** para “consumir” o ENTER que ficou.

---

## 3) Estratégia alternativa (iniciante, menos bug)
Leia **tudo com `nextLine()`** e converta:

    String idadeTexto = teclado.nextLine();
    int idade = Integer.parseInt(idadeTexto);

Isso evita quase todas as confusões do buffer no começo.

---

## 4) Exercício rápido (fixação)
Monte um programa que peça:
1) idade (número)
2) nome completo (texto com espaço)

E garanta que o nome não venha vazio.

---

## 5) Pergunta única (para checar que fixou)
O que fica “sobrando” no buffer depois que você usa `nextInt()` e aperta ENTER?

---


<!-- nav_start -->
---
Anterior: [Comandos para leitura de nÃºmeros](../docs/18_Leitura_Numeros.md) | Próximo: [ConcatenaÃ§Ã£o de Dados](../docs/20_Concatenacao_Dados.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

