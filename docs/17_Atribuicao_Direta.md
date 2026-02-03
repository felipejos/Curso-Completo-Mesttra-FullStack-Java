# Atribuição direta de dados

A **atribuição direta de dados** é um conceito comum em programação e significa **atribuir um valor diretamente a uma variável**.

Outra forma de atribuir um valor a uma variável é utilizar o **comando de leitura do teclado**. No entanto, o valor que será inserido na variável irá depender do que o usuário irá digitar, enquanto a **atribuição direta** quem define o conteúdo a ser atribuído na variável é o **programador**.

---

## Exemplo com atribuição direta

```java
public class Main {
    public static void main(String[] args) {
        String nome;
        String sobrenome;
        int idade;
        float peso;

        nome = "Rogério";
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

**Exemplo sem atribuição direta (fora do arquivo .md):**

Este mesmo exemplo sem utilizar a atribuição direta, seria através da leitura do teclado. Para entender os comandos `nextInt()`, `nextFloat()` leia o próximo artigo **"Comandos para a leitura de números"**.

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

        System.out.println("Dados armazenados na memória:");
        System.out.println(nome);
        System.out.println(sobrenome);
        System.out.println(idade);
        System.out.println(peso);
    }
}
