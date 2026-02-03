# Comandos para leitura de números

Dependendo do tipo de dados que o nosso programa em JAVA for realizar a leitura, é necessário utilizarmos comandos diferentes para cada tipo de dados. Desta forma, se formos ler um texto, um número inteiro ou um número fracionário, é necessário utilizarmos o comando correto para que seja possível armazenarmos este valor corretamente no tipo de variável que escolhemos.

Abaixo temos os métodos da classe `Scanner` que se encarregam de fazer a leitura e conversão dos dados para o tipo de dados correto:

- `next()` — retorna uma cadeia de caracteres simples, ou seja, que não usa o caractere espaço em branco;
- `nextDouble()` — retorna um número em notação de ponto flutuante normalizada em precisão dupla de 64 bits (usado para receber valores reais ou monetários);
- `hasNextDouble()` — retorna `true` se o próximo dado de entrada pode ser interpretado como um valor `double`;
- `nextInt()` — retorna um número inteiro de 32 bits;
- `nextLine()` — retorna uma cadeia de caracteres;
- `nextLong()` — retorna um número inteiro de 64 bits.

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
        System.out.print("Você gosta de Java? (true/false): ");
        boolean gostaDeJava = scanner.nextBoolean();

        // Consumir a quebra de linha restante
        // para entender a funcao deste comando, leia o artigo "Realizando a limpeza de buffer"
        scanner.nextLine(); // evita erro ao ler char depois de nextInt/nextDouble/nextBoolean

        // Lendo um char (ler como String e pegar o primeiro caractere)
        System.out.print("Digite a primeira letra do seu sobrenome: ");
        char inicialSobrenome = scanner.nextLine().charAt(0);

        // Exibindo os dados lidos. Para entender a função do sinal de +, leia o 
        // próximo artigo "Concatenação de Dados"
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