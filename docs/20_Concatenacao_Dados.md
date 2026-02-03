# ConcatenaÃ§Ã£o de Dados

**Prompt no chatgpt:** Explique o conceito de concatenaÃ§Ã£o de dados para um iniciante em programaÃ§Ã£o e dÃª exemplos simples em java.

---

## âœ… O que Ã© concatenaÃ§Ã£o de dados?

**ConcatenaÃ§Ã£o** significa **juntar informaÃ§Ãµes (dados)** para formar uma Ãºnica coisa.

Na programaÃ§Ã£o, geralmente usamos **concatenaÃ§Ã£o de Strings** (textos). Ou seja: juntar dois ou mais textos para formar um novo texto.

---

## Exemplo simples na vida real

Imagine que vocÃª tem duas palavras:

- `"OlÃ¡"`
- `"mundo"`

Se vocÃª concatenar essas palavras, o resultado serÃ¡:

- `"OlÃ¡mundo"`

---

## Exemplo simples em Java

```java
public class Main {
    public static void main(String[] args) {
        String nome = "RogÃ©rio";
        String sobrenome = "Freitas Ribeiro";

        // O resultado impresso serÃ¡ RogÃ©rioFreitas Ribeiro
        // O sÃ­mbolo + quando inserido entre duas palavras "strings", faz com
        // que o conteÃºdo seja concatenado, ou seja, os valores serÃ£o colocados
        // um na frente do outro
        System.out.println(nome + sobrenome);

        // Neste caso o resultado serÃ¡ RogÃ©rio Freitas Ribeiro
        // Note que serÃ¡ juntado um espaÃ§o entre o nome e sobrenome. Este espaÃ§o
        // precisa ser escrito entre aspas
        System.out.println(nome + " " + sobrenome);
    }
}
```
## ExplicaÃ§Ã£o

Criamos duas variÃ¡veis do tipo `String` (texto): `nome` e `sobrenome`.

Usamos o sÃ­mbolo `+` para juntar (concatenar) as variÃ¡veis.

O resultado foi impresso na tela.

### SaÃ­da

```
RogÃ©rioFreitas Ribeiro
RogÃ©rio Freitas Ribeiro
```


**Note:** na primeira impressÃ£o o nome saiu â€œcoladoâ€ no sobrenome. Para inserir um espaÃ§o, foi necessÃ¡rio usar `" "`.

---

## Concatenando texto com nÃºmero

VocÃª tambÃ©m pode concatenar texto com nÃºmeros. O nÃºmero serÃ¡ transformado em texto automaticamente.

```java
public class Main {
    public static void main(String[] args) {
        String nome = "Maria";
        int idade = 30;
        String frase = nome + " tem " + idade + " anos.";

        // SerÃ¡ impresso na tela: Maria tem 30 anos.
        System.out.println(frase);
    }
}
```

âœ… Exemplo direto no System.out.println

```java
public class Main {
    public static void main(String[] args) {
        String nome = "Lucas";
        int idade = 25;

        // O nome Ã© Lucas e a idade Ã© 25 anos.
        System.out.println("O nome Ã© " + nome + " e a idade Ã© " + idade + " anos.");
    }
}
```

## O que acontece aqui

- `"O nome Ã© "` Ã© uma `String`
- `nome` Ã© uma variÃ¡vel do tipo `String`
- `" e a idade Ã© "` Ã© outra `String`
- `idade` Ã© uma variÃ¡vel do tipo `int` (nÃºmero)
- `" anos."` tambÃ©m Ã© uma `String`
- O operador `+` concatena tudo em uma Ãºnica mensagem

---

## â­ Dica para iniciantes

Sempre que vocÃª usar o operador `+` com pelo menos uma `String`, o Java vai tratar tudo como texto.

Para deixar o texto mais legÃ­vel, lembre-se de incluir espaÃ§os quando necessÃ¡rio:

```java
"OlÃ¡, " + nome
"OlÃ¡," + nome
```

<!-- nav_start -->
---
Anterior: [Realizando a limpeza do buffer](../docs/19_Limpeza_Buffer.md) | Próximo: [Caractere de Escape \\](../docs/21_Caractere_de_Escape.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

