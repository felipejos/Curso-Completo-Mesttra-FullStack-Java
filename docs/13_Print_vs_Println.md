# Diferença entre `print` e `println` em Java ☕

---

## Conteúdo

# Diferença entre `print` e `println` em Java ☕

Diferença entre print e println

Em Java, System.out.print e System.out.println são usados para imprimir texto no console, mas há uma diferença fundamental entre eles.

### Diferença Principal

- System.out.print: Imprime o texto, mas não adiciona uma nova linha na exibição dos dados na console. Isso significa que o próximo texto impresso será mostrado na mesma linha na console.
- System.out.println: Imprime o texto e, em seguida, adiciona uma nova linha na console. Isso significa que o próximo texto impresso será mostrado na linha seguinte.

### Exemplos

#### Usando System.out.print:

    public class Main {
        public static void main(String[] args) {
            System.out.print("Hello, ");
            System.out.print("World!");
        }
    }

Saída na console:

Hello, World!

Explicação: Ambos os textos foram impressos na mesma linha porque System.out.print não adiciona uma nova linha ao término da impressão dos dados.

#### Usando System.out.println:

    public class Main {
        public static void main(String[] args) {
            System.out.println("Hello, ");
            System.out.println("World!");
        }
    }

Saída na console:

Hello,
World!

Explicação: Cada chamada de System.out.println adiciona uma nova linha após imprimir o texto, então "World!" é impresso na linha seguinte.

#### Combinando System.out.print e System.out.println:

    public class Main {
        public static void main(String[] args) {
           System.out.print("Hello, ");
           System.out.println("World!");
           System.out.print("Welcome to Java Programming.");
        }
    }

Saída:

Hello, World!
Welcome to Java Programming.

Explicação: O primeiro System.out.print imprime "Hello, " sem adicionar uma nova linha, então "World!" aparece na mesma linha. O segundo System.out.println adiciona uma nova linha após "World!", então "Welcome to Java Programming." aparece na linha seguinte.

### Resumo

- Use System.out.print quando quiser que o texto seja impresso na mesma linha.
- Use System.out.println quando quiser que o texto seja impresso e movido para a próxima linha.
- Isso é essencial para controlar a formatação da saída no console, dependendo do que você deseja que o usuário veja.

<!-- nav_start -->

---

# Complemento da Lição

## 1) Regra mental rápida (para não esquecer)
- `print` = **imprime e fica na mesma linha**
- `println` = **imprime e pula para a próxima linha**

Uma forma de lembrar:
- `println` tem **ln** de **line** (linha).

---

## 2) Onde isso aparece muito (na prática)
### 2.1 Perguntas no console (entrada de dados)
Você normalmente faz:
- `print` para **perguntar** (o cursor fica na mesma linha para o usuário digitar)
- `nextLine()` para **ler**
- `println` para **confirmar** ou mostrar resultado

Exemplo de padrão (ideia):

    System.out.print("Digite seu nome: ");
    String nome = teclado.nextLine();
    System.out.println("Nome recebido: " + nome);

---

## 3) Exercícios rápidos (fixação)
### Exercício 1
Sem executar, tente prever a saída:

    System.out.print("A");
    System.out.print("B");
    System.out.println("C");
    System.out.print("D");

### Exercício 2
Transforme para que a saída fique em 3 linhas:
- Linha 1: `Hello,`
- Linha 2: `World!`
- Linha 3: `Fim`

---

## 4) Pergunta única (para eu checar que fixou)
Se você quiser que o usuário digite na mesma linha da pergunta, você usa `print` ou `println`?
---
Anterior: [Leitura de Dados com a Classe Scanner](../docs/12_Leitura_Dados_Scanner.md) | Próximo: [VariÃ¡veis](../docs/14_Variaveis.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

