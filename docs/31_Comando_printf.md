# 🖨️ Comando `printf()`

## ✅ O que é `printf` em Java?

O `printf` é um método usado para imprimir **texto formatado** no console. Ou seja, além de usar `print` ou `println`, o programador ainda tem a opção de utilizar o `printf`, que traz algumas características a mais.

Ele vem da linguagem **C** e significa **"print formatted"** (imprimir formatado).

---

## 🧩 Sintaxe básica

    System.out.printf("texto com formatação desejado", variavel1, variavel2, variavel3);

O `printf` utiliza **caracteres formatadores** (`%s`, `%d`, `%f`...) que definem como os valores das variáveis devem ser exibidos, bem como o seu formato.

---

## 🧪 Exemplo simples

    public class Main {
        public static void main(String[] args) {
            String nome = "Maria";
            int idade = 25;
            float peso = 85.6f;
            System.out.printf("Nome: %s Idade: %d Peso: %f \n", nome, idade, peso);
        }
    }

✅ O resultado impresso será:

    Nome: Maria  Idade: 25

---

## 🎯 Como os formatadores funcionam?

A primeira função do caractere de formatação é marcar a posição dentro do texto a ser formatado: **em qual posição uma variável deverá ter o conteúdo inserido dentro da frase.**

No exemplo acima:

- `%s` (**string**) determina que a variável `nome` será impressa na posição do `%s`.
- `%d` (**inteiro**) determina que a variável `idade` será impressa na posição do `%d`.
- `%f` (**float**) determina que a variável `peso` será impressa na posição do `%f`.

📌 Note que as variáveis são separadas por **vírgulas** e o conteúdo é inserido nas posições dos formatadores, respeitando a ordem:

- 1º formatador → 1ª variável  
- 2º formatador → 2ª variável  
- 3º formatador → 3ª variável  

---

## 🧷 Marcadores de formatação mais comuns

| Marcador | Tipo de dado | Exemplo |
|---------:|--------------|---------|
| `%s`     | `String` (texto) | `"Maria"` |
| `%d`     | `int` (número inteiro) | `25` |
| `%f`     | `float/double` (número decimal) | `3.14` |
| `%.2f`   | decimal com 2 casas | `3.14` (formata para 2 casas decimais) |

---

## 📐 Alinhamento de texto

Exemplo:

    public class Main {
      public static void main(String[] args) {
          System.out.printf("+----------------------+----------+\n");
          System.out.printf("| %-20s | %10s\n", "Produto", "Valor |");
          System.out.printf("+----------------------+----------+\n");
          System.out.printf("| %-20s | %8.2f |\n", "Arroz", 6.78);
          System.out.printf("| %-20s | %8.2f |\n", "Feijao", 9.18);
          System.out.printf("| %-20s | %8.2f |\n", "Açucar", 4.28);
          System.out.printf("| %-20s | %8.2f |\n", "Café", 3.70);
          System.out.printf("+----------------------+----------+\n");
      }
    }

### 📌 O que significa cada formatador?

- `%-20s` → alinha à esquerda e ocupa 20 espaços.
- `%5.2f` → alinha à direita com 5 espaços, e dois caracteres depois da vírgula.

✅ Saída:

    +----------------------+----------+
    | Produto              |    Valor |
    +----------------------+----------+
    | Arroz                |     6.78 |
    | Feijao               |     9.18 |
    | Açucar               |     4.28 |
    | Café                 |     3.70 |
    +----------------------+----------+
