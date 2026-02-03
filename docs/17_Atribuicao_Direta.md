# AtribuiÃ§Ã£o direta de dados

A **atribuiÃ§Ã£o direta de dados** Ã© um conceito comum em programaÃ§Ã£o e significa **atribuir um valor diretamente a uma variÃ¡vel**.

Outra forma de atribuir um valor a uma variÃ¡vel Ã© utilizar o **comando de leitura do teclado**. No entanto, o valor que serÃ¡ inserido na variÃ¡vel irÃ¡ depender do que o usuÃ¡rio irÃ¡ digitar, enquanto a **atribuiÃ§Ã£o direta** quem define o conteÃºdo a ser atribuÃ­do na variÃ¡vel Ã© o **programador**.

---

## Exemplo com atribuiÃ§Ã£o direta

```java
public class Main {
    public static void main(String[] args) {
        String nome;
        String sobrenome;
        int idade;
        float peso;

        nome = "RogÃ©rio";
        sobrenome = "de Freitas Ribeiro";
        idade = 42;
        peso = 88.5f;

        System.out.println(nome);
        System.out.println(sobrenome);
        System.out.println(idade);
        System.out.println(peso);
    }
}
```

---

**Exemplo sem atribuiÃ§Ã£o direta (fora do arquivo .md):**

Este mesmo exemplo sem utilizar a atribuiÃ§Ã£o direta, seria atravÃ©s da leitura do teclado. Para entender os comandos `nextInt()`, `nextFloat()` leia o prÃ³ximo artigo **"Comandos para a leitura de nÃºmeros"**.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner teclado;
        String nome;
        String sobrenome;
        int idade;
        float peso;

        teclado = new Scanner(System.in);

        System.out.print("Digite o seu nome: ");
        nome = teclado.nextLine();

        System.out.print("Digite o seu sobrenome: ");
        sobrenome = teclado.nextLine();

        System.out.print("Digite a sua idade: ");
        idade = teclado.nextInt();

        System.out.print("Digite o seu peso: ");
        peso = teclado.nextFloat();

        System.out.println("Dados armazenados na memÃ³ria:");
        System.out.println(nome);
        System.out.println(sobrenome);
        System.out.println(idade);
        System.out.println(peso);
    }
}

<!-- nav_start -->
---
Anterior: [Tipos de Dados e Intervalos de Valores](../docs/16_Tipos_Dados_Intervalos.md) | Próximo: [Comandos para leitura de nÃºmeros](../docs/18_Leitura_Numeros.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

