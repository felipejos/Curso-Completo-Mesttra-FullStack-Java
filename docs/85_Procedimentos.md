# Procedimentos

Como visto, em ambos os casos, tanto procedimentos e funções são blocos de códigos que agrupam uma determinada lógica para fornecer uma melhor organização do código. Vamos iniciar pelo entendimento das características dos procedimentos:

---

## Exemplo (antes): menu escrito dentro do `main`

Considere o código abaixo principalmente a parte destacada em azul:

    import java.util.Scanner;
    import java.lang.Math;

    public class App {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            double area;

            String mensagem = "";

            int opcao = 0;

            System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");
            System.out.println("1 - Círculo");
            System.out.println("2 - Retângulo");
            System.out.println("3 - Triângulo\n");

            try {
                System.out.print("Digite o número da opção desejada: ");
                opcao = teclado.nextInt();

                switch (opcao) {
                    case 1:
                        double raio;

                        try {
                            System.out.print("Digite o valor do raio da circunferencia em metros: ");
                            raio = teclado.nextDouble();

                            area =  3.14159 * raio * raio;
                            mensagem = "Área do círculo: " +  Math.round(area)   ;

                        } catch (Exception e) {
                            System.out.println("Valor inválido para o raio.");
                        }

                        break;
                    case 2:
                        double largura, altura;

                        System.out.print("Digite a largura do retangulo: ");
                        largura = teclado.nextDouble();
                        System.out.print("Digite a altura do retangulo: ");
                        altura = teclado.nextDouble();

                        area = largura * altura;

                        mensagem = "Área do retângulo: " + area + " metros";
                        break;
                    case 3:
                        double base;

                        System.out.print("Digite a base do triângulo: ");
                        base = teclado.nextDouble();
                        System.out.print("Digite a altura do triângulo: ");
                        altura = teclado.nextDouble();

                        area = (base * altura) / 2;

                        mensagem = "Área do triângulo: " + area + " metros";
                        break;
                    default:
                        System.out.println("Opção inválida.");
                        break;
                }
            } catch (Exception e) {
                System.out.println("Opção inválida.");
            }

            System.out.println(mensagem);
            teclado.close();
        }
    }

Percebemos que estas linhas tem claramente o objetivo de exibir o menu para o usuário escolher qual figura geométrica ele deseja realizar o cálculo da área.

---

## Exemplo (depois): separando o menu em um procedimento

Podemos separar este techo de código em um bloco específico chamado de `exibirMenu()` conforme destacado pelo parte verde no código abaixo, desta forma, retiramos os detalhes de como imprimir o menu do trecho principal "main" e levamos para uma parte separada do nosso arquivo.

No lugar onde estava as linhas de código responsáveis pela exibição do menu, ficará apenas a referência para o nome do procedimento `exibirMenu` conforme destaco em azul.

    import java.util.Scanner;
    import java.lang.Math;

    public class App {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            double area;

            String mensagem = "";

            int opcao = 0;

            exibirMenu();  // chamada do bloco de código exibirMenu que está definido ao fim deste código

            try {
                System.out.print("Digite o número da opção desejada: ");
                opcao = teclado.nextInt();

                switch (opcao) {
                    case 1:
                        double raio;

                        try {
                            System.out.print("Digite o valor do raio da circunferencia em metros: ");
                            raio = teclado.nextDouble();

                            area =  3.14159 * raio * raio;
                            mensagem = "Área do círculo: " +  Math.round(area)   ;

                        } catch (Exception e) {
                            System.out.println("Valor inválido para o raio.");
                        }

                        break;
                    case 2:
                        double largura, altura;

                        System.out.print("Digite a largura do retangulo: ");
                        largura = teclado.nextDouble();
                        System.out.print("Digite a altura do retangulo: ");
                        altura = teclado.nextDouble();

                        area = largura * altura;

                        mensagem = "Área do retângulo: " + area + " metros";
                        break;
                    case 3:
                        double base;

                        System.out.print("Digite a base do triângulo: ");
                        base = teclado.nextDouble();
                        System.out.print("Digite a altura do triângulo: ");
                        altura = teclado.nextDouble();

                        area = (base * altura) / 2;

                        mensagem = "Área do triângulo: " + area + " metros";
                        break;
                    default:
                        System.out.println("Opção inválida.");
                        break;
                }
            } catch (Exception e) {
                System.out.println("Opção inválida.");
            }

            System.out.println(mensagem);
            teclado.close();
        }

        static void exibirMenu(){ //inicio do bloco de código exibirMenu
            System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");
            System.out.println("1 - Círculo");
            System.out.println("2 - Retângulo");
            System.out.println("3 - Triângulo\n");
        } //fim do bloco de código exibirMenu
    }

Por agora, não se preocupe com o que significa a palavra `static`, apenas vamos sempre adicioná-la. O que faz com que esse bloco de código seja definido como um procedimento, ou em java, um método que não retorna valor, é o fato da existência da palavra `void`.

Sempre que um bloco for escrito com a palavra `void` antes do nome do bloco, que neste caso é `exibirMenu()`, este bloco terá a característica de procedimento, ou seja, o procedimento simplesmente executa o código que está dentro das chaves `{ }` e retorna para o programa principal sem devolver nenhum valor para quem fez a chamada. Por enquanto, este conceito de não devolver um valor, ainda ficará confuso até entendermos qual a diferença para a função.

---

## Fluxo de execução (como o programa “anda”)

Este código terá o seu fluxo de execução da seguinte forma: o programa começa a execução e quando chegar na linha `exibirMenu()` ele continuará a execução do programa no bloco:

    static void exibirMenu(){ //inicio do bloco de código exibirMenu
        System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");
        System.out.println("1 - Círculo");
        System.out.println("2 - Retângulo");
        System.out.println("3 - Triângulo\n");
    } //fim do bloco de código exibirMenu

Ao terminar de executar todos os comandos presentes entre as `{ }` "chaves", o fluxo de execução volta para a próxima linha depois da chamada `exibirMenu()`, que neste caso é:

    try {
        System.out.print("Digite o número da opção desejada: ");
        opcao = teclado.nextInt();

        .
        .
        .

---

## Procedimentos que você já usa desde o começo

Note que o comando utilizado para invocar/executar o procedimento `exibirMenu` foi `exibirMenu()`.

Isto provavelmente se parece com outros comandos já utilizados anteriormente, como:

- `System.out.print();`
- `System.out.println();`
- `System.out.printf();`

Note que já estávamos utilizando o conceito de procedimento deste o início da nossa academia, pois todos os comandos `System....` são na verdade procedimentos, ou seja, em algum lugar dentro do computador, existe um conjunto de linhas de código que são executadas quando invocamos o `System.out.printf()` e os demais comandos `System`.

A única diferença entre os procedimentos/comandos System e o nosso procedimento/comando `exibirMenu()` é que nós fomos os desenvolvedores que descreveu o código que deveria ser executado ao ser executado `exibirMenu()`.

---

## Benefícios (o “porquê” disso)

Agora compare o código antes e depois do uso do procedimento e pense quais foram os benefícios foram obtidos ao usar procedimento.

Caso você não consiga identificar os benefícios, volte no artigo anterior e releia o item **Vantagens de utilizar Funções e Procedimentos**. É fundamental que você consiga entender o benefício do uso de procedimentos e funções.

---

## Como chamar um procedimento (e o que NÃO faz sentido fazer)

Note que a execução/chamada do bloco de comandos do procedimento é realizada da seguinte forma:

**Exemplo 01:**

    exibirMenu();

Veja que não colocamos algo assim no nosso código:

**Exemplo 02:**

    String resultado = exibirMenu();

Não colocamos isto porque o comportamento do bloco de comandos `exibirMenu()` é executar um conjunto de código e **não retornar nenhum valor** para quem fez a invocação do procedimento.

Então isto é o que define um procedimento: um bloco de comandos que executa algo e não devolve nenhum resultado para ser armazenado em uma variável ou utilizado em alguma operação lógica, aritmética ou de comparação.

O exemplo 01 é o comportamento padrão de execução de um procedimento, ou seja, não esperamos nenhum resultado da exeução para armazenar em uma variável.

No exemplo 02 seria o exemplo de sintaxe de como executar uma função, obviamente no nosso caso isto irá produzir um erro pois o bloco de comandos foi escrito utilizando o termo `void`.

---

# Complemento da Lição

---

## 🧠 Módulo 1 — O que “procedimento” significa no Java (sem complicar)

No Java, “procedimento” é um nome didático para um **método `void`**.

- `void` significa: **não devolve valor**
- Ele **executa** e volta para quem chamou

Exemplo do mundo real:
- Um procedimento é como “tocar o alarme”:
  - você manda tocar
  - ele toca
  - não existe um “resultado” para você guardar em uma variável

---

## 🧩 Módulo 2 — Como identificar um procedimento no código (check rápido)

Um método é procedimento quando tem:

- `static`
- `void`
- um nome + parênteses
- um bloco `{ ... }`

Exemplo:

    static void exibirMenu() {
        // comandos
    }

O ponto-chave é: **`void`**.

---

## 🔁 Módulo 3 — Passo a passo do fluxo (com setinhas)

Trecho do `main`:

    exibirMenu();
    try {
        // ...
    }

Fluxo:
1) Executa `exibirMenu();`
2) Entra no método `exibirMenu()`
3) Executa os `System.out.println(...)`
4) Termina o método
5) Volta para a próxima linha no `main` (o `try`)

---

## ✅ Módulo 4 — Benefícios reais que você ganha (na prática)

### 1) `main` fica mais “limpo”
Em vez de um monte de `println`, fica:

    exibirMenu();

Isso melhora a leitura:
- você olha e já entende “aqui exibe o menu”.

### 2) Você pode reutilizar
Se amanhã você precisar exibir o menu de novo (ex.: repetir o menu em um loop),
basta chamar:

    exibirMenu();

Sem copiar e colar.

### 3) Você muda o menu em um só lugar
Se quiser adicionar “4 - Quadrado”, você altera **apenas dentro** do método.

---

## ⚠️ Módulo 5 — Erros comuns ao criar procedimentos

1) Esquecer o `void`
- Aí vira função (método com retorno) e o Java exige `return`.

2) Tentar guardar o retorno do procedimento
- Isso não faz sentido:

    String resultado = exibirMenu();

Porque `exibirMenu()` não devolve nada.

3) Criar o método fora da classe
- No Java, métodos precisam estar **dentro da classe**.

---

## 🧪 Exercícios (para fixar com prática)

1) Crie um procedimento `exibirTitulo()` que imprime:
- “=== Calculadora ===”

2) Crie um procedimento `exibirMenuOperacoes()` que imprime:
- “1 - Somar”
- “2 - Subtrair”
- “3 - Sair”

3) No `main`, chame os dois procedimentos antes de pedir a opção.

4) Crie um procedimento `mostrarErroOpcao()` que imprime:
- “Opção inválida.”

E use ele no `default` do `switch`.

---


<!-- nav_start -->
---
Anterior: [84 Conceito Geral Funcoes](../docs/84_Conceito_Geral_Funcoes.md) | Proximo: [86 Procedimentos Parametros](../docs/86_Procedimentos_Parametros.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
