# Realizando a limpeza do buffer

Seu cÃ³digo tÃ¡ certinho e de repente um `teclado.nextLine()` ou `teclado.next()` retorna vazio?  
A classe `Scanner` do Java Ã© uma ferramenta Ãºtil para lidar com a entrada do usuÃ¡rio. No entanto, ao usÃ¡-la, vocÃª pode encontrar problemas se nÃ£o limpar o buffer de entrada corretamente.

## O que Ã© o Buffer?

O **buffer** Ã© uma Ã¡rea de armazenamento temporÃ¡rio na memÃ³ria do computador que Ã© usada para guardar dados enquanto eles estÃ£o sendo transferidos de um lugar para outro. Em Java, quando vocÃª usa a classe `Scanner` para ler a entrada do usuÃ¡rio, os dados sÃ£o primeiro colocados no buffer antes de serem processados.

## Por que limpar o Buffer?

Se vocÃª nÃ£o limpar o buffer apÃ³s ler a entrada do usuÃ¡rio, os dados antigos ainda estarÃ£o presentes no buffer na prÃ³xima vez que vocÃª tentar ler a entrada. Isso pode causar problemas, pois vocÃª pode acabar lendo dados antigos em vez dos novos dados que o usuÃ¡rio acabou de inserir.

## Como limpar o Buffer?

Em Java, vocÃª pode limpar o buffer executando o comando `teclado.nextLine()` da classe `Scanner` apÃ³s cada chamada de `nextInt()`, `nextDouble()`, etc.

### Exemplo

```java
import java.util.Scanner;

public class Main {
  public static void main(String[] args) {
      Scanner teclado = new Scanner(System.in);

      System.out.println("Digite um nÃºmero: ");
      int number = teclado.nextInt();

      teclado.nextLine();  // Limpa o buffer

      System.out.println("Digite uma linha de texto: ");
      String text = teclado.nextLine();

      System.out.println("NÃºmero: " + number);
      System.out.println("Texto: " + text);
  }
}
```
Neste exemplo, apÃ³s ler um nÃºmero inteiro do usuÃ¡rio com `nextInt()`, chamamos `nextLine()` para limpar o buffer antes de ler uma linha de texto com `nextLine()`. Isso garante que a linha de texto nÃ£o seja contaminada por qualquer dado residual no buffer apÃ³s a chamada para `nextInt()`.

## VÃ­deo complementar
https://www.youtube.com/watch?v=GVhqeZcVGTk

[![Assistir no YouTube](https://img.youtube.com/vi/GVhqeZcVGTk/hqdefault.jpg)](https://www.youtube.com/watch?v=GVhqeZcVGTk)


<!-- nav_start -->
---
Anterior: [Comandos para leitura de nÃºmeros](../docs/18_Leitura_Numeros.md) | Próximo: [ConcatenaÃ§Ã£o de Dados](../docs/20_Concatenacao_Dados.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

