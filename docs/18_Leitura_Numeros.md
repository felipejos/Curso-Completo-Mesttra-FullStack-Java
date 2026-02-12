# Comandos para leitura de números

---

## Comandos para leitura de números

Dependendo do tipo de dados que o nosso programa em Java for realizar a leitura, é necessário utilizarmos comandos diferentes para cada tipo de dados. Desta forma, se formos ler um texto, um número inteiro ou um número fracionário, é necessário utilizarmos o comando correto para que seja possível armazenarmos este valor corretamente no tipo de variável que escolhemos.

Abaixo temos os métodos da classe `Scanner` que se encarregam de fazer a leitura e conversão dos dados para o tipo de dados correto:

- `next()` — retorna uma cadeia de caracteres simples, ou seja, que não usa o caractere espaço em branco;
- `nextDouble()` — retorna um número em notação de ponto flutuante normalizada em precisão dupla de 64 bits (usado para receber valores reais ou monetários);
- `hasNextDouble()` — retorna `true` se o próximo dado de entrada pode ser interpretado como um valor `double`;
- `nextInt()` — retorna um número inteiro de 32 bits;
- `nextLine()` — retorna uma cadeia de caracteres;
- `nextLong()` — retorna um número inteiro de 64 bits.

---

## Exemplo com `Scanner`

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

---

# Complemento da Lição

## 1) Termos técnicos rápidos (simples + exemplo)

### Conversão
**O que é:** transformar um tipo em outro.  
**Exemplo do mundo real:** transformar “2 horas” em “120 minutos”.

No Scanner, quando você usa `nextInt()`, ele já tenta converter o que foi digitado para inteiro.

---

## 2) O problema mais comum: “quebra de linha” (buffer)
Quando você usa:
- `nextInt()` / `nextDouble()` / `nextBoolean()`

o ENTER que você digitou pode ficar “sobrando”, e o próximo `nextLine()` pode ler uma linha vazia.

Por isso aparece este padrão:

    scanner.nextLine(); // limpa o buffer antes de ler texto com nextLine()

---

## 3) Regra prática de iniciante (para evitar travar)
Se você estiver começando e quer menos dor:
- leia tudo com `nextLine()`
- converta manualmente quando precisar

Exemplo:

    String idadeTexto = scanner.nextLine();
    int idade = Integer.parseInt(idadeTexto);

---

## 4) Exercícios rápidos (fixação)

1) Faça um programa que leia:
- quantidade (int)
- preço (double)
E imprima o total (quantidade * preço).

2) Faça um programa que leia:
- idade (int)
E imprima se é maior de idade (>= 18).

3) Faça um programa que leia:
- nome (String)
- letra inicial (char)
Sem “pular” a leitura (use a limpeza de buffer quando necessário).

---

## 5) Pergunta única (para checar que fixou)
Por que o código usa `scanner.nextLine();` depois de ler com `nextInt()`/`nextDouble()`?

---

<!-- nav_start -->
---
Anterior: [AtribuiÃ§Ã£o direta de dados](../docs/17_Atribuicao_Direta.md) | Próximo: [Realizando a limpeza do buffer](../docs/19_Limpeza_Buffer.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

