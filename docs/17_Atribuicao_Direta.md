# Atribuição direta de dados

---

## Atribuição direta de dados

A **atribuição direta de dados** é um conceito comum em programação e significa **atribuir um valor diretamente a uma variável**.

Outra forma de atribuir um valor a uma variável é utilizar o **comando de leitura do teclado**. No entanto, o valor que será inserido na variável irá depender do que o usuário irá digitar, enquanto a **atribuição direta** quem define o conteúdo a ser atribuído na variável é o **programador**.

---

## Exemplo com atribuição direta

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

---

**Exemplo sem atribuição direta (fora do arquivo .md):**

Este mesmo exemplo sem utilizar a atribuição direta, seria através da leitura do teclado. Para entender os comandos `nextInt()`, `nextFloat()` leia o próximo artigo **"Comandos para a leitura de números"**.

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

---

# Complemento da Lição

## 1) O que muda entre “atribuição direta” e “leitura do teclado”
- **Atribuição direta**: o valor já está definido no código (controle total do programador).
- **Leitura do teclado (Scanner)**: o valor vem do usuário (o programa precisa lidar com entradas diferentes).

### Exemplo do mundo real
- Atribuição direta: você escreve um bilhete pronto.
- Leitura do teclado: você faz uma pergunta e espera a resposta de alguém.

---

## 2) Quando usar cada um (na prática)
### Use atribuição direta quando:
- estiver **testando** uma lógica rapidamente
- quiser criar **dados de exemplo**
- quiser simular entradas sem depender do usuário

### Use leitura do teclado quando:
- o programa precisa **interagir** com o usuário
- os dados mudam a cada execução

---

## 3) Ponto importante (pegadinha comum do Scanner)
Quando você mistura `nextInt()` / `nextFloat()` com `nextLine()`, pode sobrar uma “quebra de linha” no buffer e o `nextLine()` pode “pular”.

Uma forma simples (iniciante) de evitar confusão é:
- ler tudo com `nextLine()`
- converter quando precisar (ex.: `Integer.parseInt(...)`)

---

## 4) Exercícios rápidos (fixação)

1) Troque os valores da atribuição direta para:
- nome = seu nome
- idade = sua idade
- peso = seu peso (com `f`)

2) Faça o programa imprimir em uma única linha:
- “Nome: X | Sobrenome: Y | Idade: Z | Peso: W”

3) (Desafio curto) Faça primeiro com atribuição direta e depois com teclado.
Compare:
- o que você precisou mudar
- quais linhas foram adicionadas

---

## 5) Pergunta única (para checar se fixou)
Na atribuição direta, quem decide o valor que vai para a variável: o usuário ou o programador?

---

<!-- nav_start -->
---
Anterior: [16 Tipos Dados Intervalos](../docs/16_Tipos_Dados_Intervalos.md) | Proximo: [18 Leitura Numeros](../docs/18_Leitura_Numeros.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
