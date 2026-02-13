Conceito de ENUM
Um enum no Java é uma maneira de criar um conjunto de valores fixos e predefinidos que representam um conceito específico no seu programa. Ele é usado quando você sabe que algo pode ter apenas algumas opções possíveis.

Por exemplo, imagine que você está criando um sistema de pedidos de comida e quer representar os tamanhos possíveis de uma pizza: pequeno, médio e grande. Em vez de usar strings ou números, você pode usar um enum para garantir que só esses valores sejam usados.

Como funciona
Um enum é um tipo especial de classe que define constantes (valores fixos). Esses valores são chamados de elementos ou constantes do enum.

Arquivo: TamanhoPizza.java

// Definindo o enum
public enum TamanhoPizza {
    PEQUENO,
    MEDIO,
    GRANDE
}

Com isso, você pode usar o TamanhoPizza no seu código para representar os tamanhos possíveis:

Arquivo: App.java

public class App {
    public static void main(String[] args) {
        TamanhoPizza tamanho = TamanhoPizza.GRANDE;

        // Verificar o tamanho
        switch (tamanho) {
            case PEQUENO:
                System.out.println("Você escolheu uma pizza pequena.");
                break;
            case MEDIO:
                System.out.println("Você escolheu uma pizza média.");
                break;
            case GRANDE:
                System.out.println("Você escolheu uma pizza grande.");
                break;
        }
    }
}

Por que usar enum?

Legibilidade: O código fica mais claro, porque você usa nomes significativos em vez de números ou strings.

Segurança: Como os valores são fixos, você evita erros como digitar "grande" errado (ex.: "grnade").

Organização: Facilita agrupar valores relacionados em um único lugar.

Facilidade de manutenção: Se precisar adicionar ou alterar um valor, basta ajustar o enum.

Para fazer a leitura do tamanho da pizza pelo teclado em Java, você pode usar a classe Scanner para capturar a entrada do usuário. A ideia é ler a entrada como uma string e depois verificar qual valor foi digitado, convertendo para um valor do tipo enum.

import java.util.Scanner;

public class PedidoPizza {
    // Definindo o enum como uma inner class
    public enum TamanhoPizza {
        PEQUENO,
        MEDIO,
        GRANDE
    }

    public static void main(String[] args) {
        // Criando o Scanner para ler a entrada do usuário
        Scanner scanner = new Scanner(System.in);

        // Pedindo ao usuário para informar o tamanho da pizza
        System.out.println("Digite o tamanho da pizza (PEQUENO, MEDIO, GRANDE):");
        String entrada = scanner.nextLine().toUpperCase();  // Lê a entrada e converte para maiúsculo

        // Tentando converter a entrada para um valor do enum
        try {
            TamanhoPizza tamanho = TamanhoPizza.valueOf(entrada);  // Converte a string para o enum
            System.out.println("Você escolheu uma pizza de tamanho: " + tamanho);
        } catch (IllegalArgumentException e) {
            System.out.println("Tamanho inválido. Por favor, escolha entre PEQUENO, MEDIO ou GRANDE.");
        }

        scanner.close();  // Fecha o scanner
    }
}
No exemplo acima o enum foi definido como uma inner class (classe interna). Uma classe interna é uma classe declarada dentro de outra classe. Ela serve para organizar melhor o código e para representar algo que só faz sentido existir junto da classe externa. Uma inner class não pode ser utilizada por outra classe que não seja a própria classe que a definiu.

---

## Opção melhorada

# ENUM em Java (versão bem “redondinha”)

## 1) O que é `enum` (na prática)
- `enum` é um **tipo** (como `int` e `String`), só que feito para representar **opções fechadas**.
- Ele evita “texto solto” no código (ex.: `"GRANDE"`, `"Grande"`, `"grnade"`).

---

## 2) Enum com “dados” e comportamento (bem comum em projeto real)
Você pode colocar atributos e métodos dentro do enum, por exemplo: tamanho + preço base.

    public enum TamanhoPizza {
        PEQUENO(25),
        MEDIO(35),
        GRANDE(45);

        private final double precoBase;

        TamanhoPizza(double precoBase) {
            this.precoBase = precoBase;
        }

        public double getPrecoBase() {
            return precoBase;
        }
    }

Uso:

    public class App {
        public static void main(String[] args) {
            TamanhoPizza t = TamanhoPizza.MEDIO;
            System.out.println("Preço base: R$ " + t.getPrecoBase());
        }
    }

---

## 3) Leitura segura pelo teclado (sem estourar exceção e com repetição)
Em vez de tentar uma vez e parar, você pode **repetir até o usuário digitar certo**.

    import java.util.Scanner;

    public class PedidoPizza {

        public enum TamanhoPizza {
            PEQUENO, MEDIO, GRANDE
        }

        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            TamanhoPizza tamanho = lerTamanhoPizza(scanner);

            System.out.println("Você escolheu: " + tamanho);

            scanner.close();
        }

        static TamanhoPizza lerTamanhoPizza(Scanner scanner) {
            while (true) {
                System.out.print("Digite o tamanho (PEQUENO, MEDIO, GRANDE): ");
                String entrada = scanner.nextLine().trim().toUpperCase();

                try {
                    return TamanhoPizza.valueOf(entrada);
                } catch (IllegalArgumentException e) {
                    System.out.println("Valor inválido. Use: PEQUENO, MEDIO ou GRANDE.");
                }
            }
        }
    }

---

## 4) Inner class vs arquivo separado (quando usar)
- **Inner enum**: faz sentido quando o enum **só existe naquele contexto** (ex.: só dentro de `PedidoPizza`).
- **Arquivo separado**: melhor quando o enum é reutilizado em várias classes (ex.: `TamanhoPizza` usado em pedido, carrinho, relatório, etc).

---

## Exercícios

1) Crie um enum `StatusPedido` com: `ABERTO`, `PAGO`, `ENVIADO`, `CANCELADO`.  
   - No `switch`, imprima uma mensagem diferente para cada status.

2) Crie um enum `NivelAcesso` com: `ADMIN`, `GERENTE`, `USUARIO`.  
   - Faça um método `podeExcluir()` que retorne `true` só para `ADMIN`.

3) Faça uma leitura de `StatusPedido` no console:
   - Aceite também entradas como `pago`, `Pago`, `PAGO` (ou seja, normalize com `trim().toUpperCase()`).

4) (Desafio) Crie um enum `DiaSemana` e um método `ehFimDeSemana()` retornando `true` para `SABADO` e `DOMINGO`.

<!-- nav_start -->
---
Anterior: [156 Validador](../docs/156_Validador.md) | Proximo: [158 ArrayList](../docs/158_ArrayList.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
