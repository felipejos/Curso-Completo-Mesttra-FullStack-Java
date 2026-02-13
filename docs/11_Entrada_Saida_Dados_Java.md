# Comandos de entrada e saída de dados no Java

---

## Visão geral

No Java, para conseguirmos realizar o processo de leitura de dados através do terminal ou console, é necessário introduzirmos uma linha de código no início do arquivo. A estrutura básica de um programa em Java é essa:

    public class Main
    {
            public static void main(String[] args) {
                    System.out.println("Hello World");
            }
    }

---

## Lendo dados do teclado (Scanner)

Como em todo programa de console, provavelmente será necessário realizar a leitura de dados a partir do teclado. Se isto ocorrer, será necessário inserirmos o comando `import java.util.Scanner;` antes da linha que contém a palavra `public` e posteriormente a linha `Scanner teclado = new Scanner(System.in);` ficando assim:

    import java.util.Scanner; // linha de código que permite utilizarmos o comando para a leitura de dados

    public class Main
    {
            public static void main(String[] args) {
                    // a linha de código abaixo prepara o teclado para ler os diversos tipos de dados;
                    Scanner teclado = new Scanner(System.in);
            }
    }

---

## Saída de dados (mensagens para o usuário)

Quando um desenvolvedor está construindo um programa que precisa interagir com o usuário para obter informações, é necessário utilizarmos o comando `System.out.print("Mensagem a ser apresentada para o usuário.")` para informar ao usuário do programa o que ele deve fazer.

Diferentemente do comando de leitura de dados, o comando de saída de dados não precisa de nenhum outro comando de apoio para funcionar. Vamos considerar que o programador precisa escrever um programa que precisa receber do usuário as informações do nome dele, do pai e da mãe.

Neste cenário, o programador deve instruir o computador a exibir em qual ordem ele deseja obter os dados. Assim o programador deve instruir o computador a apresentar uma informação na tela dizendo para o usuário o que ele deve digitar e um outro comando informando que o computador deve obter os dados que o usuário irá digitar.

---

## Exemplo 1: obtendo o nome do usuário

Para obtermos o nome do usuário seria necessário o seguinte bloco de código:

    import java.util.Scanner; // linha de código que permite utilizarmos o comando para a leitura de dados

    public class Main
    {
        public static void main(String[] args) {
            // a linha de código abaixo prepara o teclado para ler os diversos tipos de dados;
            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite o seu nome: ");
            teclado.nextLine();
        }
    }

Após escrever estes comandos e clicar no botão RUN, o seguinte resultado será apresentado:

![OnlineGDB - exemplo](../images/LinguagemDeProgramacao1.png)

Note que o programa não continua a execução enquanto o usuário não digitar um conjunto de dados qualquer e pressionar a tecla ENTER no teclado. Após o usuário pressionar ENTER, como não existe mais nenhum comando após a leitura do nome, o programa será finalizado.

![OnlineGDB - exemplo](../images/LinguagemDeProgramacao2.png)

---

## Exemplo 2: obtendo nome, mãe e pai

Caso o programador agora queira obter o nome do pai e da mãe deste usuário, será necessário incluir mais dois conjuntos de comandos de saída e leitura de dados, para obter o nome do pai e da mãe. Nesta situação, teríamos que escrever o seguinte código.

    import java.util.Scanner; // linha de código que permite utilizarmos o comando para a leitura de dados

    public class Main
    {
        public static void main(String[] args) {
            // a linha de código abaixo prepara o teclado para ler os diversos tipos de dados;
            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite o seu nome: ");
            teclado.nextLine();

            System.out.print("Digite o nome da sua Mãe: ");
            teclado.nextLine();

            System.out.print("Digite o nome do seu Pai: ");
            teclado.nextLine();
        }
    }

O resultado da execução do programa seria:

![OnlineGDB - exemplo](../images/LinguagemDeProgramacao3.png)

---

## Exercício

Tente agora alterar este código para obter o endereço do usuário.

---

# Complemento da Lição

## 1) O que está acontecendo na prática (bem simples)

- `System.out.print(...)` mostra uma mensagem para orientar o usuário.
- `teclado.nextLine()` “pausa” o programa e espera o usuário digitar algo + apertar ENTER.
- Esse “esperar” é normal em console: o programa só continua quando recebe a entrada.

---

## 2) Padrão que você vai repetir sempre (saída → leitura)

A sequência mais comum é:

1) Mostrar o que o usuário deve digitar  
2) Ler o que ele digitou  

Exemplo de “forma padrão” (com variável):

    System.out.print("Digite algo: ");
    String valor = teclado.nextLine();

---

## 3) Exercício guiado (sem entregar pronto)

### Passo 1
Adicione uma nova pergunta para o usuário (saída):

    System.out.print("Digite o seu endereço: ");

### Passo 2
Logo abaixo, faça a leitura (entrada) e guarde em uma variável:

    String endereco = teclado.nextLine();

### Passo 3 (opcional, para testar)
Mostre na tela o que foi digitado:

    System.out.println("Endereço informado: " + endereco);

---

## 4) Pergunta única para você responder (para eu validar)

Qual mensagem você vai colocar no `System.out.print(...)` para pedir o endereço do usuário?

---

<!-- nav_start -->
---
Anterior: [10 onlinegdb](../docs/10_onlinegdb.md) | Proximo: [12 Leitura Dados Scanner](../docs/12_Leitura_Dados_Scanner.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
