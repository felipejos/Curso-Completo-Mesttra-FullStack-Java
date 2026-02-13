# Concatenação de Dados

---

## Conteúdo

**Prompt no chatgpt:** Explique o conceito de concatenação de dados para um iniciante em programação e dê exemplos simples em java.

---

## ✅ O que é concatenação de dados?

**Concatenação** significa **juntar informações (dados)** para formar uma única coisa.

Na programação, geralmente usamos **concatenação de Strings** (textos). Ou seja: juntar dois ou mais textos para formar um novo texto.

---

## Exemplo simples na vida real

Imagine que você tem duas palavras:

- `"Olá"`
- `"mundo"`

Se você concatenar essas palavras, o resultado será:

- `"Olámundo"`

---

## Exemplo simples em Java

    public class Main {
        public static void main(String[] args) {
            String nome = "Rogério";
            String sobrenome = "Freitas Ribeiro";

            // O resultado impresso será RogérioFreitas Ribeiro
            // O símbolo + quando inserido entre duas palavras "strings", faz com
            // que o conteúdo seja concatenado, ou seja, os valores serão colocados
            // um na frente do outro
            System.out.println(nome + sobrenome);

            // Neste caso o resultado será Rogério Freitas Ribeiro
            // Note que será juntado um espaço entre o nome e sobrenome. Este espaço
            // precisa ser escrito entre aspas
            System.out.println(nome + " " + sobrenome);
        }
    }

---

## Explicação

Criamos duas variáveis do tipo `String` (texto): `nome` e `sobrenome`.

Usamos o símbolo `+` para juntar (concatenar) as variáveis.

O resultado foi impresso na tela.

---

## Saída

    RogérioFreitas Ribeiro
    Rogério Freitas Ribeiro

**Note:** na primeira impressão o nome saiu “colado” no sobrenome. Para inserir um espaço, foi necessário usar `" "`.

---

## Concatenando texto com número

Você também pode concatenar texto com números. O número será transformado em texto automaticamente.

    public class Main {
        public static void main(String[] args) {
            String nome = "Maria";
            int idade = 30;
            String frase = nome + " tem " + idade + " anos.";

            // Será impresso na tela: Maria tem 30 anos.
            System.out.println(frase);
        }
    }

---

## ✅ Exemplo direto no System.out.println

    public class Main {
        public static void main(String[] args) {
            String nome = "Lucas";
            int idade = 25;

            // O nome é Lucas e a idade é 25 anos.
            System.out.println("O nome é " + nome + " e a idade é " + idade + " anos.");
        }
    }

---

## O que acontece aqui

- `"O nome é "` é uma `String`
- `nome` é uma variável do tipo `String`
- `" e a idade é "` é outra `String`
- `idade` é uma variável do tipo `int` (número)
- `" anos."` também é uma `String`
- O operador `+` concatena tudo em uma única mensagem

---

## ⭐ Dica para iniciantes

Sempre que você usar o operador `+` com pelo menos uma `String`, o Java vai tratar tudo como texto.

Para deixar o texto mais legível, lembre-se de incluir espaços quando necessário:

    "Olá, " + nome
    "Olá," + nome

---

# Complemento da Lição

## 1) Pegadinha clássica: soma vs concatenação
Quando você usa `+` com **String**, ele concatena.
Quando você usa `+` com **números**, ele soma.

O detalhe é: se **uma parte já virou String**, o resto vira texto também.

Exemplo (pra pensar antes de rodar):
    System.out.println(1 + 2 + "3");
    System.out.println("1" + 2 + 3);

---

## 2) Como controlar a ordem (parênteses)
Se você quer somar antes de virar texto:
    System.out.println("Total: " + (1 + 2));

Sem parênteses:
    System.out.println("Total: " + 1 + 2);

---

## 3) Exercícios rápidos (fixação)

1) Preveja a saída (sem executar):
    System.out.println(10 + 5 + "kg");
2) Preveja a saída (sem executar):
    System.out.println("kg" + 10 + 5);
3) Faça sair exatamente:
   - `Resultado: 15kg`
   usando `10` e `5`.

---

## 4) Pergunta única (para checar que fixou)
O que acontece com `+` quando pelo menos um dos lados é `String`: ele soma ou concatena?

---

---

<!-- nav_start -->
---
Anterior: [19 Limpeza Buffer](../docs/19_Limpeza_Buffer.md) | Proximo: [21 Caractere de Escape](../docs/21_Caractere_de_Escape.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
