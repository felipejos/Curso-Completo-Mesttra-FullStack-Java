# Comandos para leitura de nÃºmeros

Dependendo do tipo de dados que o nosso programa em JAVA for realizar a leitura, Ã© necessÃ¡rio utilizarmos comandos diferentes para cada tipo de dados. Desta forma, se formos ler um texto, um nÃºmero inteiro ou um nÃºmero fracionÃ¡rio, Ã© necessÃ¡rio utilizarmos o comando correto para que seja possÃ­vel armazenarmos este valor corretamente no tipo de variÃ¡vel que escolhemos.

Abaixo temos os mÃ©todos da classe `Scanner` que se encarregam de fazer a leitura e conversÃ£o dos dados para o tipo de dados correto:

- `next()` â€” retorna uma cadeia de caracteres simples, ou seja, que nÃ£o usa o caractere espaÃ§o em branco;
- `nextDouble()` â€” retorna um nÃºmero em notaÃ§Ã£o de ponto flutuante normalizada em precisÃ£o dupla de 64 bits (usado para receber valores reais ou monetÃ¡rios);
- `hasNextDouble()` â€” retorna `true` se o prÃ³ximo dado de entrada pode ser interpretado como um valor `double`;
- `nextInt()` â€” retorna um nÃºmero inteiro de 32 bits;
- `nextLine()` â€” retorna uma cadeia de caracteres;
- `nextLong()` â€” retorna um nÃºmero inteiro de 64 bits.

---

## Exemplo com `Scanner`

```java
import java.util.Scanner;

public class Main{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Lendo uma String
        System.out.print("Digite seu nome: ");
        String nome = scanner.nextLine();

        // Lendo um int
        System.out.print("Digite sua idade: ");
        int idade = scanner.nextInt();

        // Lendo um double
        System.out.print("Digite sua altura (em metros): ");
        double altura = scanner.nextDouble();

        // Lendo um boolean
        System.out.print("VocÃª gosta de Java? (true/false): ");
        boolean gostaDeJava = scanner.nextBoolean();

        // Consumir a quebra de linha restante
        // para entender a funcao deste comando, leia o artigo "Realizando a limpeza de buffer"
        scanner.nextLine(); // evita erro ao ler char depois de nextInt/nextDouble/nextBoolean

        // Lendo um char (ler como String e pegar o primeiro caractere)
        System.out.print("Digite a primeira letra do seu sobrenome: ");
        char inicialSobrenome = scanner.nextLine().charAt(0);

        // Exibindo os dados lidos. Para entender a funÃ§Ã£o do sinal de +, leia o 
        // prÃ³ximo artigo "ConcatenaÃ§Ã£o de Dados"
        System.out.println("\n=== Dados Lidos ===");
        System.out.println("Nome: " + nome);
        System.out.println("Idade: " + idade);
        System.out.println("Altura: " + altura + "m");
        System.out.println("Gosta de Java: " + gostaDeJava);
        System.out.println("Inicial do sobrenome: " + inicialSobrenome);

        scanner.close();
    }
}
```
<!-- nav_start -->
---
Anterior: [AtribuiÃ§Ã£o direta de dados](../docs/17_Atribuicao_Direta.md) | Próximo: [Realizando a limpeza do buffer](../docs/19_Limpeza_Buffer.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

